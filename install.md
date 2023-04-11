# Prepare the environment

## Install Kind

In order to run **Istio**, **Kind** will be used to create a Kubernetes Cluster quickly and locally. You must have *Docker* and *Kubernetes* installed for **Kind** to run properly. To install Kind, follow the steps below:

```sh
curl -LO ./kind https://kind.sigs.k8s.io/dl/v0.16.0/kind-linux-amd64
sudo chmod +x ./kind
sudo cp ./kind /usr/local/bin/kind
```

To check if the installation finished successfully, run the following command:

```sh
kind version
```

### Create the cluster

We are going to define the characteristics of the cluster through a configuration file, you can use this [file](./files/cluster-kind.yaml) as a template. Once the cluster parameters are defined, run the following command to start the cluster:

```sh
kind create cluster --config <config_file>.yaml
```

## Download and Install Istio

### Download istioctl

```sh
curl -L https://istio.io/downloadIstio | sh -
sudo cp ~/istio-1.16.1/bin/istioctl /usr/bin/istioctl 
istioctl version
```

### Install and configure the profile

For this installation, we use the **demo** [configuration profile](https://istio.io/latest/docs/setup/additional-setup/config-profiles/). It’s selected to have a good set of defaults for testing, but there are other profiles for production or performance testing.

```sh
istioctl install --set profile=demo -y
```

Add the tag "**istio-injection=enabled**" to the namespace where apps will be deployed to tell Istio to automatically inject **Envoy sidecar** proxies when you deploy your app later. This means that Istio will now take care of that namespace. By default you can use the "**default**" namespace.

```sh
kubectl label namespace <namespace> istio-injection=enabled
```

## Uninstall

If you want to remove installed addons, just run the following command:

```sh
kubectl delete -f samples/addons
```

The **istio-system** namespace is not removed by default. If no longer needed, use the following command to remove it:

```sh
kubectl delete namespace istio-system
```

The label to instruct Istio to automatically inject Envoy sidecar proxies is not removed by default. If no longer needed, use the following command to remove it:

```sh
kubectl label namespace default istio-injection-
```

---
[BACK](main.md) | [TOP](#prepare-the-environment) | [DEPLOY FIRST APP](deploy.md)
