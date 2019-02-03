# docker-pruebas
Pruebas con docker-compose. Nos permite configurar varios servicios en un solo archivo de configuración
Para ello definimos la configuración de los servicios mediante un archivo en formato YAML, que llamaremos docker-compose.
De este modo, con un solo comando podemos poner en marcha varios contenedores al mismo tiempo.

## Ejecución
Una vez extraída la carpeta, ejecutar: 
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
