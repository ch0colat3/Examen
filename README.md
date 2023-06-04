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
docker run -p 80:80 -t prueba
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