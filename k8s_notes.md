# Notes

## Scaling Kubernetes Apps

Which blade in the Azure Kubernetes service resource includes the list of all deployed pods?

> *Answer:* In AKS, is **Workloads** in the **Kubernetes resources** menu. Here you can see all Deployments, Pods, Replica Sets, etc... In this **Kubernetes resources** menu, you can also see **Services and Ingresses** and other aspects related to the cluster.

Which are configurations that can be performed while deploying a Kubernetes service in Azure?

> *Answer:* (1) Creating and associating a node pool. (2) Creating or referencing a container registry.

### ConfigMaps

Is an API object used to store non-confidential data in key-value pairs for use by other objects. Pods can consume **ConfigMaps** as environment variables, command-line arguments, or as configuration files in a volume. A ConfigMap allows you to decouple environment-specific configuration from your container images without compiling these configurations inside the container images, so that your applications are easily portable.

### Readiness, Liveness and Startup

- **Liveness Probe** indicates if the container is operating. If so, no action is taken. If not, the *kubelet* kills and restarts the container.
- **Readiness Probe** indicates whether the application running in the container is ready to accept requests. If so, **Services** matching the pod are allowed to send traffic to it. If not, the endpoints controller removes the pod from all matching Kubernetes **Services**.
- **Startup Probe** indicates whether the application running in the container has started. If so, other **probes** start functioning. If not, the *kubelet* kills and restarts the container.

How many times will a liveness probe restart a container before giving up?

> *Answer:* Kubernetes will restart a container in a pod after failureThreshold times. By default it is 3 times - so after 3 failed probes.

### Taints and Tolerations

They are a mechanism that allows you to ensure that pods are not placed on inappropriate nodes. **Taints** are added to nodes, while **Tolerations** are defined in the pod specification. When you **taint** a node, it will repel all the pods except those that have a **toleration** for that **taint**. **Tolerations** allow the *kubescheduler* to schedule pods with matching **taints**. **Taints** and **Tolerations** work together to ensure that pods are not scheduled onto inappropriate nodes. One or more **taints** are applied to a node; this marks that the node should not accept any pods that do not tolerate the taints.

A **Taint** can produce three possible effects:

- **NoSchedule**: The Kubernetes scheduler will only allow scheduling pods that have tolerations for the tainted nodes.
- **PreferNoSchedule**: The Kubernetes scheduler will try to avoid scheduling pods that don’t have tolerations for the tainted nodes.
- **NoExecute**: Kubernetes will evict the running pods from the nodes if the pods don’t have tolerations for the tainted nodes.

Which best describes a Taint?

> *Answer:* A description of a node that can be used for filtering and selection

Which Kubernetes utility is used to select a node for a pod?

> *Answer:* kubescheduler

### Autoscaling

Which best describes vertical scaling?

> *Answer:* Adding additional computer power (e.g. memory, CPU, etc.) to a single node

What is the minimum number of nodes that can be configured with autoscaling enabled?

> *Answer:* In AKS minimum: Zero; maximum: 1000
