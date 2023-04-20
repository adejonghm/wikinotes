# Comandos

## Crear un Pod

### Create

```sh
kubectl create ??????
```

### Apply

```sh
kubectl apply -f pod-file.yaml
```

Existe una diferencia entre las dos opciones si se usa `create` crea el *Pod* si no existe. Si se usa la opcion `apply` crea el *Pod* si no existe, pero si exite, actualiza el *Pod* existente con las nuevas configuraciones encontradas en el manifiesto YAML. Existen algunas configuraciones que no son posible actualizarlas como es el caso de adicionar o remover un *container* dentro del *Pod*, en ese caso hay que eliminar el *Pod* y crearlo nuevamente.

## Analizar un Pod

```sh
kubectl logs <nombre_pod> -c <nombre_container>
```

```sh
kubectl logs <nombre_pod> -f
```

## Ejecutar un Pod

```sh
kubectl run <nombre_pod> --image <imagen_docker> --port <>
```

La opcion `-t -i` es para ??????
Existe la opcion `--dry-run=<none | server | client>`. Si la estrategia es *client*, solo imprime el objeto que se enviaría, sin enviarlo. Si es *server*, envíe una solicitud del lado del servidor sin conservar el recurso. Si se usa la estrategia *client* combinado con la opcion `-o yaml` y comandos de Linux se puede salvar la configuración del *Pod* en un manifiesto YAML.

## Acceder a un Container específico dentro de un Pod

```sh
kubectl attach <nombre_pod> -c <nombre_container> -ti

kubectl exec -ti <nombre_container> -- bash [lista ....]
```

## Listar todos los Pods

```sh
kubectl get pods -A

kubectl get deployment <nombre_deployment> -o wide
```

La opcion `-L <nombre_label>` lista los *Pods* que tienen esa label en su definicion. La opcion `--watch` ??

## Listar todos los Services

```sh
kubectl get services
```

## Descripcion de un recurso

```sh
kubectl describe pods <name_pod>

kubectl describe deployment <nombre_deployment>

kubectl describe node <nombre_node>
```

## Eliminar un Pod

```sh
kubectl delete pods <name_pod>

kubectl delete -f <file.yaml>

kubectl delete deployment <nombre_deployment>
```

## Crear un deployment

```sh
kubectl create deployment --image nginx --repĺicas 3 <nombre_deployment>
```

## Analizar actualizacion en tiempo real

```sh
# Muestra el estado de las actualizaciones
kubectl rollout status deployment <nombre_deployment> -n <nombre_namespace>

# Pausa el rollout y ejecuta ninguna actualizacion
kubectl rollout pause deployment <nombre_deployment> -n <nombre_namespace>

# Reanuda el rollout y ejecuta las actualizaciones pendientes
kubectl rollout resume deployment <nombre_deployment> -n <nombre_namespace>

# Reinicia todo el rollout
kubectl rollout restart deployment <nombre_deployment> -n <nombre_namespace>
```

## Rollback

```sh
# Regresa a la version anterior que estaba en ejecución
kubectl rollout undo deployment <nombre_deployment> -n <nombre_namespace>

# Para regresar a una revision específica
kubectl rollout undo --revision <int>

# Muestra el histórico de los cambios/actualizaciones hechas
kubectl rollout history deployment <nombre_deployment> -n <nombre_namespace>

# Para ver una revision específica
kubectl rollout history --revision <int>
```
