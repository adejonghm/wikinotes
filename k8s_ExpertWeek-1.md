# Expert Week Day 1

## Install kind

```sh
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.17.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

### Crear un clúster

Para crear un clúster simples, lo ideal es definir 1 *Control Plane* y 3 *Workers*, como se muestra en el siguiente manifiesto [YAML](../files/cluster-kind.yaml).

```sh
kind create cluster --config cluster.yaml --name my-cluster
```

`--name <string>` --> cluster name, overrides KIND_CLUSTER_NAME, config (default kind)

`--config <string>` --> path to a kind config file

### Listar clústers

```sh
kind get clusters
```

### Eliminar un clúster

```sh
kind delete <nombre_clúster>
```

If the flag `--name` is not specified, kind will use the default cluster context name "kind" and delete that cluster.

Para leer la documentación clique [aqui](https://kind.sigs.k8s.io/).

## Install kubectl

```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo chmod +x ./kubectl
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client --output=yaml
```

### Interactuar con un clúster específico

```sh
kubectl cluster-info --context kind-<nombre_clúster>
```

## Concepos

- **Container**: revisar para ver sobre namespaces

- **Container Engine**: Responsavel por fazer a criação do container(validar saude, criar volumes, network e tudo mais q precisa o container para existir), uma visão do container como produto, como um todo pensando em o ambiente q completo que precisa para executar. O container engine no conversa diretamente com o Kernel, para isso usa container runtime.

- **Container Runtime**: Responsavel pela executar os containers.

  - **Low Level**: Son aquellos que son ejecutados directamente por el *kernel* de Linux. Ej: (runC, crun)

  - **Hight Level**: Son aquellos que no son ejecutados directamente por el *kernel* de Linux, son ejecutados por un *Container Engine*. Ej: (Containerd)

- **Open Container Iniciative (OCI)**: Es un proyecto de gobernanza abierta, formado bajo los auspicios de la *Linux Foundation*, con el propósito expreso de crear estándares abiertos en la industria en torno a *containers* y *runtimes*. Fue lanzado el 22 de junio de 2015 por Docker, CoreOS y otros líderes en la industria de *containers*.

- **Kubernetes**: Es un orquestador de *containers* desarrollado por Google en 2014 y donado a la *Cloud Native Computing Foundation*.
  - **Control Plane**: Es el nodo o conjunto de nodos responsables por mantener el clúster. De forma predeterminada, es posible, pero no se recomienda, ejecutar aplicaciones dentro de él, solo se ejecutarán los componentes de K8 necesarios para mantener y administrar el clúster.
    - **etcd**: Puertos 2379 - 2390. Responsable de almacenar toda la información del clúster (clave, estado actual, etc.)

    - **kube API Server**: Puerto 6443. Es el único componente que puede comunicarse con "etcd". Es la pasarela de comunicasión entre "etcd" y el resto de los componentes en el *Control Plane*.

    - **kube Scheduler**: Puerto 10251. Responsable de programar la ejecución de los *Pods*, es decir, administrará dónde y cuándo deben ejecutarse cada uno de los *Pods*.

    - **kube Controller Manager**: Puerto 10252. Administrador de todos los controladores del clúster, lo cual garantiza un rendimiento óptimo.

  - **Workers**: Son los nodos donde se ejecutan todas las aplicaciones de usuario que se ejecutan en un clúster.
    - **kubelet**: Puerto 10250. *Agent* que está presente en todos los nodos (*Workers*) y es quien siempre se comunica con el *Control Plane*.

    - **kubeproxy**: Puerta zzz.Es el proxy dentro de cada nodo (*Workers*) para administrar todo lo que es tráfico de red.

    - **Servicios en los Workers**
      - *Node Port* 30000 - 32767

- **Deployment**: Es el *Controller* que define todos los parametros/informaciones (Ej: número de Pods, imagen, recursos, etc...) para desplegar *Pod* donde se ejecutará la app en el cluster.

- **ReplicaSet**: Es el *Controller* responsable por garantizar que todas las replicas de un *Pod* esten saludables, si fuera necesario él reubica de un node para otro.

- **Service**: Es el *Controller* responsable por garantizar q las app estaran disponibles para acceder desde fuera del *Pods/Nodes*, o sea, es el responsable de exponer los puertos/servicios de las aplicaciones en ejecución.

- **Namespaces**
  - **kube-system**: namespace donde se ejecutan los componentes del K8s-cluster

## Links

<https://www.linuxtips.io/course/kubernetesexpertweek>

<https://play.instruqt.com/study-room>
  
usuario: gmail | password: el de linuxtips
