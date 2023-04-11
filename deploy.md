# Deploy the first Sample App (Bookinfo)

## Deploying

This app is one of the examples app that **Istio** brings when you download the installer. In order to perform all the steps and execute all the commands, it must be placed inside the downloaded folder, with the name `istio-<version>`.

To get started, run the following command, as each pod becomes ready, the Istio sidecar will be deployed along with it.

```sh
kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
```

To verify if everything is ok, you can view the services that are running on you kubernetes cluster, as shown below. As a result you will be able to see the three services (*productpage, ratings, reviews*) deployed with their respective details. You can also see all running pods, related to the application.

```sh
kubectl get services 
kubectl get pods
```

### Verify everything is working correctly

Run this command to see if the app is running inside the cluster and serving HTML pages by checking for the page title in the response. In the output it should display the following text `<title>Simple Bookstore App</title>` in the terminal.

```sh
kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"
```

### Open the application to outside traffic

At this point, the app is deployed but not accessible from the outside. To make it accessible, you must create an Istio Ingress Gateway, which maps a path to a route at the edge of your mesh.

```sh
kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
```

Make sure there are no problems with your configuration with the following istio command, which is a diagnostic tool that can detect potential problems with your Istio configuration:

```sh
istioctl analyze
```

### Determining the ingress IP and ports

Execute the following command to determine if your Kubernetes cluster is running in an environment that supports external load balancers:

```sh
kubectl get svc -n istio-system istio-ingressgateway
```

If the **EXTERNAL-IP** value is set, your environment has an external load balancer that you can use for the ingress gateway. If the **EXTERNAL-IP** value is ***none*** (or perpetually ***pending***), your environment does not provide an external load balancer for the ingress gateway. In this case, you can access the gateway using the service’s [node port](https://kubernetes.io/docs/concepts/services-networking/service/#type-nodeport). For that, follow these commands to set the ingress ports:

```sh
export INGRESS_PORT=$(kubectl get svc -n istio-system istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')

export SECURE_INGRESS_PORT=$(kubectl get svc -n istio-system istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].nodePort}')

export INGRESS_HOST=$(kubectl get po -l istio=ingressgateway -n istio-system -o jsonpath='{.items[0].status.hostIP}')
```

Setting the gateway url:

```sh
export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT
```

In all the above cases, you can verify the information using the `echo` command to print the values of the variables. In the same way, we will check the external access `echo "http://$GATEWAY_URL/productpage"` and as a result, we will have the URL `http://ip_address:port/productpage`.

## View the dashboard

Istio integrates with [several](https://istio.io/latest/docs/ops/integrations) different telemetry applications. Follow these instructions to deploy the Kiali dashboard, along with Prometheus, Grafana, and Jaeger.

### Install Kiali and the other addons

To run Kiali successfully, you need to also install Prometheus.

```sh
kubectl apply -f samples/addons/<service_name.yaml>
```

#### Monitor the deployment

```sh
kubectl rollout status -n istio-system deployment <deployment-name>
```

All the installed plugins/add-ons will be placed in the Kubernetes namespace where Istio was installed/running. By default "**istio-system**".

### Access the Kiali dashboard

```sh
istioctl dashboard kiali
```

## Uninstall

To delete the **Bookinfo** sample application and its configuration, run the cleanup script located in the `/bookinfo/platform/kube/cleanup.sh`. For more information see [Bookinfo cleanup](https://istio.io/latest/docs/examples/bookinfo/#cleanup).

---
[BACK](install.md) | [START](main.md) | [TOP](#deploy-the-first-sample-app-bookinfo) | [NEXT](day-2.md)
