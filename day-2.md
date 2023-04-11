# Virtual-Services & Destination-Rules

[VirtualService](https://istio.io/latest/docs/concepts/traffic-management/#virtual-services): lets you configure how requests are routed to a service within an Istio service mesh, building on the basic connectivity and discovery provided by Istio and your platform. Each one consists of a set of routing rules that are evaluated in order, letting **Istio** match each given request to a specific real destination (or *subset*/version of it) within the mesh.

Example:

```YAML
spec:
  hosts:
  - reviews
  http:
  - route:
    - destination:
        host: reviews
        subset: v2
      weight: 50
    - destination:
        host: reviews
        subset: v3
      weight: 50
```

Along with **Virtual Services**, [DestinationRules](https://istio.io/latest/docs/concepts/traffic-management/#destination-rules) are a key part of Istio’s traffic routing functionality. You can think of virtual services as how you route your traffic to a given destination, and then you use destination rules to configure what happens to traffic for that destination. Destination rules are applied after virtual service routing rules are evaluated, so they apply to the traffic’s “real” destination.

In particular, you use destination rules to specify named service subsets, such as grouping all a given service’s instances by version. You can then use these service subsets in the routing rules of virtual services to control the traffic to different instances of your services.

Example:

```YAML
spec:
  host: my-svc
  trafficPolicy:
    loadBalancer:
      simple: RANDOM
  subsets:
  - name: v1
    labels:
      version: v1
  - name: v2
    labels:
      version: v2
  - name: v3
    labels:
      version: v3
```

To have more than one version of a running service, in the *route* section of the **Virtual Service** file, define a new *destination* with the new version, like the first example. It is also necessary to define the load distribution with the *weight* parameter, where the sum of that load distribution between the versions must be equal to 100.

In the **VirtualService** you can also define other types of forwarding, not just load balancing. For example, it can be possible to define that specific users or users with a specific geo-location are redirected to a new version and the other users to the old version.

These are three of the various types of traffic management:

- [Traffic Shifting](https://istio.io/latest/docs/tasks/traffic-management/traffic-shifting/):
  > This routing feature allows you to switch traffic from one microservice version to another. A common case is to gradually migrate traffic from an older version to a newer version. In **Istio**, you accomplish this goal by configuring a sequence of routing rules (*weight* parameter) that redirect a percentage of traffic from one destination to another. Like the first example.

- [Request Routing](https://istio.io/latest/docs/tasks/traffic-management/request-routing/):
  > This routing feature allows you to route requests dynamically to multiple versions of a microservice. A common case is to change the route configuration so that all traffic from a specific user is routed to a specific service version. This example is enabled by the fact that the main microservice adds a custom end-user header to all outgoing HTTP requests to the reviews service.

- [Request Timeouts](https://istio.io/latest/docs/tasks/traffic-management/request-timeouts/):
  > This feature allows you to configure request timeouts in Envoy using **Istio**. A timeout request can be specified using the timeout field of the *route* rule. By default, the request timeout is disabled, but you can override the service timeout to X seconds. This feature can be used to perform some tests on the application, so you can see the behavior of one service in the face of a delay in the response of another.

Every time a **Virtual Service** is defined, it is necessary to define a **Destination Rule**.

## Tips

Whenever the version of Istio is updated, it will be reflected in the **apiVersion** line of the YAML files, that line is the one that can give errors or problems. Therefore, it is necessary to be aware of the version of Istio in the documentation.

---
[BACK](deploy.md) | [START](main.md) | [TOP](#virtual-services--destination-rules) | [NEXT](day-3.md)
