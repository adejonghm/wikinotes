# Notes

## Scaling Kubernetes Apps

How many times will a liveness probe restart a container before giving up?

> *Answer:* Kubernetes will restart a container in a pod after failureThreshold times. By default it is 3 times - so after 3 failed probes.

What is the minimum number of nodes that can be configured with autoscaling enabled?

> *Answer:* Zero

Which blade in the Azure Kubernetes service resource includes the list of all deployed pods?

> *Answer:* In the Azure Portal, is **Workloads** in the **Kubernetes resources** menu. Here you can see all Deployments, Pods, Replica Sets, etc... In this **Kubernetes resources** menu, you can also see **Services and Ingresses** and other aspects related to the cluster.

Which Kubernetes utility is used to select a node for a pod?

> *Answer:* kube scheduler

Which are configurations that can be performed while deploying a Kubernetes service in Azure?

> *Answer:* (1) Creating and associating a node pool. (2) Creating or referencing a container registry.

Which best describes vertical scaling?

> *Answer:* Adding additional computer power (e.g. memory, CPU, etc.) to a single node

Which best describes a taint?

> *Answer:* A description of a node that can be used for filtering and selection

### ConfigMaps

Is an API object used to store non-confidential data in key-value pairs, and configuration for other objects to use. Pods can consume **ConfigMaps** as environment variables, command-line arguments, or as configuration files in a volume. A ConfigMap allows you to decouple environment-specific configuration from your container images without compiling these configurations inside the container images, so that your applications are easily portable.
