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

## 06

Bind Mounts -> herramienta para montar directorios y guardar espejos de la informacion

-- Comando para crear un contenedor en background de MongoDB con un custom name

```sh

docker run -d --name db <custom_name>

```

-- Comando para ver los contenedores activos

```sh

docker ps

```

-- Comando para entrar al bash del contenedor
-- la flag -it hace referencia al modo interactivo

```sh

docker exec -it <container_name> bash
```

-- Comando en el bash del contenedor para correrlo

```sh

mongosh

```

-- Comando en eliminar un contenedor corriendo

```sh

docker rm -f <container_name>

```

## 07

Asociando volumenes a los contenedores

-- Comando para crear un volumen de Docker

```sh

docker volume create --name <volume_name>

```

-- Comando para montar el volumen sea que tenga informacion o no a un contenedor

```sh

docker run -d --name db -v <volume_name>:<internal_container_path_data> <image>

```

## 08

-- Comando para copiar un archivo de la maquina anfitriona
-- a un folder del contenedor

```sh
docker cp <file_name> <container_name>:<internal_container_path>
```

-- Comando para copiar un archivo desde el contenedor
-- a la maquina anfitriona

```sh
docker cp <container_name>:<internal_container_path> <file_name_path>
```

## 09

-- Comando para descargar una imagen de Docker Hub

```sh
docker pull <image_name>:<tag>
```

-- Comando para construir una imagen de Docker a
-- partir de un Dockerfile que esta en la misma carpeta de ejecucion
-- del comando

```sh
docker build -t <name_image>:<tag> .
```

-- Dockefile para crear una imagen a partir de Ubuntu
-- que crea un archivo hello-world.txt en built time

hint: Cada ejecucion de un comando crea una capa en la imagen

```dockerfile
FROM ubuntu:latest

RUN touch /usr/src/hello-word.txt

```

-- Comando para entrar en modo interactivo de un contenedor
-- en tiempo de ejecucion

```sh
docker run -it <image_name>:<tag>
```

-- Comando para ver el historial de capaz de una imagen y la ultima
-- capa obedece a la ultima linea de ejucion de la imagen lo que es lo
-- mismo que un tag

```sh
docker history <image_name>
```

-- Comando para retaggear una imagen

```sh
docker tag  <image_name>:<tag> <user_repository>/<image_name>:<tag>

```

-- Comando para subir una imagen al repositorio publico

```sh
docker push <user_repository>/<image_name>:<tag> 
```

### hint: USAR DIVE PARA INSPECCIONAR A PROFUNDIDAD UNA IMAGEN