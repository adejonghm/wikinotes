# Uncomplicated Istio

## Table of Content

- [Day1: Concepts, Install & Integration](#day-1)
  - [Prepare the environment](Istio/install.md)
  - [Deploy the first Sample App](deploy.md)
- [Day2: VirtualService & DestinationRule](day-2.md)
- [Day3: Security](day-3.md)
- [Day4: ----](day-4.md)
- [Documentation](#documentation)

## Day 1

### Services mesh

A service mesh is a dedicated infrastructure layer that you can add to the App. This infrastructure layer can document how well (or not) different parts of an App interact, so it becomes easier to optimize communication and avoid downtime as an App grows. It allows you to transparently add capabilities like ***observability***, ***traffic management***, ***security*** and ***policies***, without adding them to your own code. The term service mesh describes both the type of software you use to implement this pattern and the security or network domain that is created when you use that software.

### Istio

Istio is an open-source service mesh that layers transparently onto existing distributed Apps. Istio's robust features provide a consistent and more efficient way to secure, connect, and monitor services. Its powerful control plane brings vital features.

### Data plane

The *data plane* is composed of a set of intelligent proxies (**Envoy**) deployed as sidecars in each service. These proxies mediate and control all network communication between microservices. They also collect and report telemetry on all mesh traffic.

### Control plane

The *control plane* (**istiod**) provides service discovery, configuration and certificate management.

**Istiod** converts high level routing rules that control traffic behavior into Envoy-specific configurations, and propagates them to the sidecars at runtime.

**Pilot** abstracts platform-specific service discovery mechanisms and synthesizes them into a standard format that any sidecar conforming with the Envoy API can consume.

![Istio Architecture](../files/istio/arch.svg)

### Integration

1. **Kiali** is an observability console for Istio with service mesh configuration and validation capabilities. It helps you understand the structure and health of your service mesh by monitoring *traffic flow in real time* to infer the topology and report errors. Kiali provides detailed metrics and a basic **Grafana** integration, which can be used for advanced queries. Distributed tracing is provided by integration with **Jaeger**.

2. When you install Istio on a Kubernetes cluster, an *istio system namespace* is created, where Istio runs.

3. **Grafana**  is an open source monitoring solution that can be used to configure *dashboards* for Istio. You can use Grafana to monitor the health of Istio and of applications within the service mesh.

4. To enable Istio in a certain namespace within the kubernetes cluster, it is necessary to create an "*istio-injection*" label for that namespace with value "*enabled*". `istio-injection=enable`

5. *istiod* is the name of the Istio daemon and it is inside the Control Plane.

6. When istio is installed, three *profile* types can be defined (*demo, default, minimal*).

## Documentation

1. <https://kind.sigs.k8s.io>
2. <https://istio.io/latest/docs>
3. <https://kubernetes.io/docs/tasks/tools>
4. <https://istio.io/latest/docs/setup/getting-started/>
5. <https://istio.io/latest/docs/setup/additional-setup/config-profiles>
6. <https://istio.io/latest/docs/ops/integrations/>
7. <https://istio.io/latest/docs/tasks/traffic-management/>

---
[TOP](#table-of-content) | [INSTALL ISTIO](install.md)
