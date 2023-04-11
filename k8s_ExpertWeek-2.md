# Expert Week Day 2

## Conceptos

**kube-system** es el *namespace* administrativo de Kubernetes.

### Pod

Es la menor unidade en Kubernetes, permite ejecutar varios *containers* dentro de un mismo *Pod* pero no es recomendado. Cuando son ejecutados varios *containers* en el mismo *Pod*, este encapsula todos los *containers* haciendo que compartan los mismo recursos dentro del *Pod*, como direccion IP, puertos y todos los demas recursos del *Pod*. Ejemplo: si se ejecutan dos *containers* y los usan el mismo puerto para publicar servicios diferentes, el segundo *container* no será iniciado por estar el puerto ya en uso por el primer *container*.

### Deployment

Es el objeto encargado de controlar los *Pods* que se ejecutan dentro de un clúster, en el se definen el número de réplicas en que será distribuida la app para ejecuturse en el cluster (Garantizar *High Availability*). Permite además definir la estrategia de despliegue, permitiendo actualizar los *Pods* sin tener indisponibilidad (Garantizar Zero Downtime). Al aplicar o crear un Deployment se crea automaticamente una ReplciaSet, que es quien controla la salud los *Pods*.

## Limitando recursos de un Pod

Para limitar de "cpu", "memoria" y "IO" de un *Pod*, se usa la especificación `resources:` y dentro se definen los `limits:` para especificar el maximo de recursos que puede llegar a usar el *Pod* y `requests:` para definir los recursos con que será iniciado. El valor declarado en "cpu" se puede usar valores decimales para representar %, donde 1 representa 1 core del cpu (ejemplo: 1.5 = 1CPU 1/2, 0.3 = 30% de 1CPU), o puede ser expresado em millicpu, (1.5 = 1500m = 1500 millicpu = 50% = 1CPU 1/2). El valor de memoria debe ser definido en bytes, combinado con los sufijos conocidos K, M, G.

```yaml
resources:
  limits:
    cpu: "500m"
    memory: "128Mi"
  requests:
    cpu: "0.3"
    memory: "64Mi"
```

## Volume

Para definir un volumen, primero se define el punto de montaje que usará dentro del *container* con la siguiente especificación `volumeMounts:` y dentro se define la ruta `mountPath:` y el nombre `name:`. Posteriomente se define el tipo de volumen a ser utilizado y se usa el mismo nombre, definido dentro del *container*, fuera del *container* con la especificación `volume:`.

```yaml
spec:
  containers:
  - image: nginx
    name: my-nginx
    volumeMounts:
    - mountPath: /cache
      name: cache-volume
  volume:
  - name: cache-volume
    emptyDir:
      sizeLimit: 256Mi
```
