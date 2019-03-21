# Buenas prácticas para construir contenedores
* Una sola aplicación por contenedor. Por ejemplo, PHP y Mysql en dos contenedores.
* Agregar el código fuente de la aplición lo más tarde posible. Las capas y dependencias se pueden cachear y acelerar las builds posteriores
* Eliminar todo lo que no sea necesario, o utilizar una imagen scratch o distroless.
* Hacer las imágenes lo más pequeñas posibles. Reduce downtimes, tiempo de arranque y espacio en disco.
* Etiquetar las imágenes
* Utiliza volúmenes para manejar guardar la configuración y los datos fuera de los contenedores

# Docker
Diferentes configuraciones de Docker

## Dockerfiles
Permiten automatizar la construcción de una imagen, a través de un fichero que contiene instrucciones para fabricar una imagen, a través de una serie de pasos.

Formato del Dockerfile, que se creará dentro de la carpeta donde tengamos el proyecto
```
FROM ubuntu:14.04
ENTRYPOINT ["/bin/echo"]
```
Si en lugar de utilizar entrypoints queremos pasar parámetros, podemos utilizar CMD
```
CMD ["/bin/echo" , "Hi Docker !"]
```
Construimos la imagen
```
docker build .
```
Al no definir repositorios ni tags, se asigna a la imagen una ID hexadecimal. Podemos especificar un nombre y una etiqueta al vonstruir la imagen:
```
docker build -t cookbook:hello .
```
Consultar las imágenes disponibles:
```
docker images
```
A partir de una imagen podemos crear y ejecutar un contenedor, especificando el ID de la imagen:

```
docker run e778362ca7cf
```

## Docker compose

Pruebas con docker-compose. Nos permite configurar varios servicios en un solo archivo de configuración
Para ello definimos la configuración de los servicios mediante un archivo en formato YAML, que llamaremos docker-compose.
De este modo, con un solo comando podemos poner en marcha varios contenedores al mismo tiempo.

Para ejecutar docker-compose:
```
docker-compose up
```
También podemos ejecutar los contenedores en segundo plano, utilizando
```
docker-compose up -d
```
Si queremos visualizar los contenedores que se están ejecutando:
```
docker ps
```
Eliminar todos los contenedores existentes (subshell):
```
docker stop $(docker ps -q)
docker rm -v $(docker ps -aq)
```
## Monitorizar contenedores ##

* Comprobar recursos que utiliza un contenedor: docker stats xxx
Comprobar los logs de un contenedor: docker logs
Comprobar todos los eventos que han ocurrido a un contenedor: docker events 
Listar procesos de un contenedor: docker top xxx

