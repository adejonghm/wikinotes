# GitOps Fundamentals with Argo CD and Argo Rollouts

## GitOps

GitOps is a set of best practices where the entire code delivery process is controlled via Git, including infrastructure and application definition as code and automation to complete updates and rollbacks. GitOps is not only for Kubernetes applications.

GitOps is the best thing since configuration as code. Git changed how we collaborate, but declarative configuration is the key to dealing with infrastructure at scale, and sets the stage for the next generation of management tools.

### GitOps Principles

1. Declarative: A system managed by GitOps must have its desired state expressed declaratively.
2. Versioned and Immutable: Desired state is stored in a way that enforces immutability, versioning and retains a complete version history.
3. Pulled Automatically: Software agents automatically pull the desired state declarations from the source.
4. Continuously Reconciled: Software agents continuously observe actual system state and attempt to apply the desired state.

### In the case of Kubernetes, GitOps deployments happen in the following manner

1. A GitOps agent is deployed on the cluster.
2. The GitOps agent is monitoring one or more Git repositories that define applications and contain Kubernetes manifests (or Helm charts or Kustomize files).
3. Once a Git commit happens the GitOps agent is instructing the cluster to reach the same state as what is described in Git.
4. Developers, operators. and other stakeholders perform all changes via Git operations and never directly touch the cluster (or perform manual kubectl commands).

### The key points here are

1. The state of the cluster is always described in Git. Git holds everything for the application and not just the source code.
2. There is no external deployment system with full access to the cluster. The cluster itself is pulling changes and deployment information.
3. The GitOps controller is running in a constant loop and always matches the Git state with the cluster state.

### Some Pros of GitOps

- Eliminating configuration drift (the most important)
- Faster deployments
- Safer deployments
- Easier rollbacks
- Straightforward auditing
- Better traceability

## Argo CD

### Argo CD implements all GitOps principles that we described in the following way

- Install Argo CD as a controller in the Kubernetes cluster. Usually install Argo CD on the same cluster that it manages.
- Store your manifests in Git. Argo CD is agnostic on the type of manifests you can use. It supports plain Kubernetes manifests, Helm charts, Kustomize definitions, and other templating mechanisms.
- Create an Argo CD application by defining which Git repository to monitor and to which cluster/namespace this application should be installed.
- From now on, Argo CD monitors the Git repository, and when there is a change, it automatically brings the cluster to the same state.
- Optionally Argo CD can deploy applications to other clusters (and not just the one on which it is installed).  It is also possible to manage external clusters with ArgoCD.

### Install ArgoCD

There are many ways to install it on a Kubernetes cluster. For quick demos and labs, you can deploy ArgoCD using the **Manifests**:

```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

For a production setup we suggest you use **Autopilot**. Other way to install is a community Helm chart that is also available at: <https://github.com/argoproj/argo-helm/tree/master/charts/argo-cd>

### Installing ArgoCD CLI

```sh
curl -sSL -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/v2.1.5/argocd-linux-amd64

chmod +x /usr/local/bin/argocd

argocd help
```

### Login to ArgoCD via CLI

```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d > admin-pass.txt

argocd login localhost:30443 --insecure
```

### The essentials to customize ArgoCD

- Decide how to expose Argo CD API/UI to your users.
- Decide how users are going to authenticate to Argo CD.

### There are mainly two approaches for external URL to access the ArgoCD

- Use a small number of local users. Authentication is handled by Argo CD itself. Best for very small companies (e.g. 2-5 people).
- Use an SSO provider. Authentication is handled by the provider. Ideal for companies and large organizations

### Creating an Argo CD application with the argocd CLI

```sh
argocd app create {APP NAME} \
--project {PROJECT} \
--repo {GIT REPO} \
--path {APP FOLDER} \
--dest-namespace {NAMESPACE} \
--dest-server {SERVER URL}
```

#### Description

{APP NAME} -> *is the name you want to give the application*

{PROJECT} -> *is the name of the project created or "default"*

{GIT REPO} -> *is the url of the git repository where the gitops config is located*

{APP FOLDER} -> *is the path to the configuration for the application in the gitops repo*

{DEST NAMESPACE} -> *is the target namespace in the cluster where the application will be deployed*

{SERVER URL} -> *is the url of the cluster where the application will be deployed. Use <https://kubernetes.default.svc> to reference the same cluster where Argo CD has been deployed*

### See the status and configuration of the application

```sh
argocd app list
argocd app get {APP NAME}
argocd app history {APP NAME}
```

### Synchronizing an Argo CD application with the argocd CLI

- By default the app is in "OutOfSync" status because it hasn’t been deployed yet, sync the app with the command.
    argocd app sync {APP NAME}
- To confirm it's running, execute a kubectl command. The Application (Pod) will have a status "Running" if synchronized successfully.
    kubectl -n {NAMESPACE} get all

### Parameters that you can change when defining the sync strategy

- **Manual or automatic sync:** If set to automatic, Argo CD will apply the changes then update/create new resources in the cluster. If set to manual, Argo CD will detect the change but will not change anything in the cluster.
- **Auto-pruning of resources - this is only applicable for automatic sync:** (remove/delete) If it is enabled, Argo CD will also remove the respective resources in the cluster as well. If disabled, Argo CD will never delete anything from the cluster.
- **Self-Heal of cluster - this is only applicable for automatic sync:** (make changes directly (kubectl) to the cluster) If enabled, then Argo CD will discard the extra changes and bring the cluster back to the state described in Git.

## Encryptation

By default, secrets in Kubernetes are not encrypted in any way and the base64 encoding used should be never seen as a security feature. Secrets can be encrypted inside and outside the cluster itself. To encrypt them outside of the cluster, you can use the Bitnami Sealed secrets controller, and this way you can store them in Git as required by one of the fundamental principles of GitOps. The controller comes with the associated "kubeseal" executable that is created for this purpose.

### The full process is the following

- You create a plain Kubernetes secret locally. You should never commit this anywhere.
- You use kubeseal to encrypt the secret in a SealedSecret.
- You delete the original secret from your workstation and apply the sealed secret to the cluster.
- You can optionally commit the Sealed secret to Git.
- You deploy your application that expects normal Kubernetes secrets to function. (The application needs no modifications of any kind.)
- The controller decrypts the Sealed secrets and passes them to your application as plain secrets.
- The application works as usual.

### Encrypt commands

This creates a SealedSecret which is a custom Kubernetes resource specific to the controller:

```sh
kubeseal -n my-namespace <.db-creds.yml> db-creds.json
```

Apply the secret on the cluster:

```sh
kubectl apply -f db-creds.json -n my-namespace
```

## Declarative Setup

In all scenarios, it is much better to fully adopt GitOps and work exclusively via Kubernetes resources and git commits instead of GUI actions. The GUI of Argo CD is best used for verifying and inspecting resources instead of changing them by hand.

### Helm with ArgoCD

Hence if you execute the helm list command, you should no longer be able to view your helm release because the Helm metadata no longer exists.

### Kustomize

Kustomize is a CLI configuration manager for Kubernetes objects with a kustomization.yaml file. It is integrated with kubectl and allows you to customize raw, template-free YAML files for multiple purposes declaratively. It is based on the following configuration layers to allow reuse:

- **Base Layer:** This layer specifies the most common resources.
- **Overlays:** This layer specifies use-case specific resources by utilizing patches to override other kustomization files and Kubernetes manifests.

### There are some powerful commands

Generate a customized YAML file:

```sh
kustomize build name_of_application
```

This file/resources can then be applied to a cluster:

```sh
kustomize build name_of_application | kubectl apply -k or --kustomize
```

This then creates all resources previously mentioned

## Progressive Delivery

### Argo Rollouts

Argo Rollouts is a progressive delivery controller created for Kubernetes. It allows you to deploy your application with minimal/zero downtime and easy rollbacks by adopting a gradual way of deploying instead of taking an “all at once” approach. There are several forms of progressive delivery such as blue/green, canary, a/b and feature flags.

Argo Rollouts offers the powerful capability to look at application metrics and decide automatically if the deployment should continue or not. The idea behind this approach is to completely automate canary deployments. Instead of having a human running manual smoke tests, or looking at graphs, you can set different thresholds that define if a deployment is "successful" or not. Argo Rollouts is an independent project that can work on its own and it also works great with Argo CD.

- **Blue Green**: When a new version is deployed, the old version is kept. Who makes the change to the new version is the Load-Balancer.

- **Canary**: It's similar to blue/green, but instead of switching 100% of live traffic all at once to the new version, you can instead move only a subset of users.

### Commands

Change the container image of the rollout to the next version with, in command line live:

```sh
kubectl argo rollouts set image {POD NAME} webserver-simple=docker.io/kostiscodefresh/gitops-canary-app:v2.0
```

See what Argo Rollouts is doing behind the scenes:

```sh
kubectl argo rollouts get rollout {POD NAME}
```

Manually promote the deployment and switch all traffic to the new version enter:

```sh
kubectl argo rollouts promote {POD NAME}
```

Monitor again the rollout with:

```sh
kubectl argo rollouts get rollout {POD NAME} --watch 
```

Argo Rollouts offers the powerful capability to look at application metrics and decide automatically if the deployment should continue or not. The idea behind this approach is to completely automate canary deployments. Instead of having a human running manual smoke tests, or looking at graphs, you can set different thresholds that define if a deployment is “successful” or not.

## Example Lab

- <https://github.com/codefresh-contrib/gitops-certification-examples/tree/main/simple-app>

## References

- <https://kubectl.docs.kubernetes.io/references/kustomize/>

- <https://argo-cd.readthedocs.io/en/stable/operator-manual/>

- <https://argoproj.github.io/argo-rollouts/>

- <https://dev.to/stack-labs/store-your-kubernetes-secrets-in-git-thanks-to-kubeseal-hello-sealedsecret-2i6h>
