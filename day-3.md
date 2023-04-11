# Security

1. Tenemos mutual TLS para dejar todo el trafico encriptado.

2. Pilot es quien distribuye las politicas de autenticacion, ademas es el responsable por pasar las informaciones del Secure Naming para el Proxy.

3. Citadel é o responsable por tener los certificados y llaves de comunicacion.

4. Mixer es el responsable por administrar las autenticaciones y realizar toda la auditoria, todo el monitoreo a travez de plugins.

## Habilitando Mutual TLS

Primeramente creamos varios namespaces en el cluster, en este caso vamos a crear 3 namespaces.

```sh
kubectl create namespaces
```

Luego settear el istio-injection label para dos de ellos. Una vez hecho todo, deployed el ejemplo httpbin y sleep en todos los namespaces.

Para validar todo se puede usar el siguiente comando:

```sh
kubectl exec -ti -n strigus sleep-78ff5975c6-sjhdg -- curl http://httpbin.giropops:8000/ip -s -o /dev/null -w "%{http_code}\n"
```

En este comando está validando desde un namespace (strigus) para otro namespace (giropops), si todo está bien, recibirá 200 (http error code: ok) como output de ese comando.

## Documentation

1. <https://istio.io/latest/docs/concepts/security/>

---
[BACK](day-2.md) | [START](main.md) | [TOP](#security) | [NEXT](day-4.md)
