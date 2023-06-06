# Diseño de Soluciones de Infraestructura

<p align="left" style="text-align:left;">
  <a href="https://www.duoc.cl/">
    <img alt="Github Universe" src="img/logo.png" width="1040"/>
  </a>
</p>

## Pre-requisitos

Ingresar al sitio de [play-with-docker](https://www.docker.com/play-with-docker/), para ello deben tener una cuenta en docker, si no la tienen, pueden crearla [aqui](https://hub.docker.com/signup)

## Implementación Docker

1.- Clonamos el repositorio git

```
git clone https://github.com/jveraduran/hello-world-container
```

2.- Ingresamos a la carpeta del proyecto

```
cd hello-world-container
```

3.- Compilamos la imagen mediante ```docker build```

```
docker build -t imagen-custom .
```

4.- Ejecutamos de manera local el contenedor con ```docker run```

```
docker run -p 80:80 -t imagen-custom
```

## Implementación Docker Swarm

1.- Iniciamos Docker Swarm

```
docker swarm init --advertise-addr 127.0.0.1
```

2.- Deployamos el Stack de PHP

```
docker stack deploy -c stack.yml image-custom
```

## Implementación Kubernetes

Ingresar al sitio de [play-with-k8s](https://labs.play-with-k8s.com), para ello deben tener una cuenta en GitHub, si no la tienen, pueden crearla [aqui](https://github.com/join)



1.- Iniciamos nodo maestro cluster

```
kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16
```

2.- Iniciamos red en el cluster

```
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```

3.- Parchamos temporalmente el Cluster, para permitir pods en el ControlPlane

```
kubectl taint nodes --all node-role.kubernetes.io/control-plane-
```

4.- Creamos un despliegue de prueba

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/website/master/content/en/examples/application/nginx-app.yaml
```
