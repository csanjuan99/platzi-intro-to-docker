# platzi-intro-to-docker

## 01

```sh

docker run hello-world
docker run --name <custom_name>

```

## 02

Listando contenedores

```sh

docker ps -a

```

Inspeccionando un contenedor

```sh

docker inspect <container_id>

```

Renombrando un contenedor

```sh

docker rename <current_name> <new_name>

```

Removiendo un contenedor

```sh

docker rm <container_id>

```

Removiendo todos los contenedores

```sh

docker container prune

```

## 03

Ciclo de vida de un contenedor

-- Corre un contenedor con ubuntu cambiando el proceso
-- principal para evitar su cierre

```sh

docker run --name <container_name> -d ubuntu tail -f /dev/null 

```

Comando para entrar al bash del contenedor

```sh

docker exec -it <container_name> bash

```

Comando para encontrar el process id de nuestro contenedor

```sh

docker inspect --format '{{.State.Pid}}' <container_name>


```

Matando el contenedor desde fuera del mismo

```sh

Kill  2474


```

## 04

Exponiendo contenedores

-- Para correr un contenedor y exponerlo 
-- es neceario usar un servidor web o proxy

-- Cada contenedor tiene su propia interfaz de red,
-- con lo cual el puerto del contenedor no es el mismo
-- de la maquina

```sh

docker run --detach --name proxy 9000:80  nginx

```

Comando para ver la llegada de eventos que llegan al contenedor
con un limite

```sh

docker logs --tail <n> -f <container_name>

```
