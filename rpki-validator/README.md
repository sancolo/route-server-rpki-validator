# rpki-validator

Como validador de ROAs utilizamos el RIPE NCC RPKI Validator version 2.24 

1. Creamos una imagen para docker a partir del archivo [Dockerfile](Dockerfile) definido para el rpki-validator
```sh
$ mkdir mydockerbuild_rpki-validator
$ cd mydockerbuild_rpki-validator
$ wget https://github.com/sancolo/route-server-rpki-validator/blob/master/rpki-validator/Dockerfile 
$ sudo docker build -t rpki-validator .
```
Verificamos la imagen creada ejecutando:
```sh
$ docker images
rpki-validator              latest              478ef5603551        2 months ago        647MB
```
3. Ejecutamos el contenedor teniendo en cuenta que los puertos 8080 y 8282 son mapeados en el host para su acceso externo. En el puerto 8080 se ejecuta la interfaz web del validador y en el puerto 8282 se accede al repositorio de ROAs. 
```sh
$ sudo docker run --name rpki-validator -dit --restart unless-stopped -h rpki -p 8080:8080 -p 8282:8282 rpki-validator
```
La opción *--restart unless-stopped* asegura que al reinicio del demonio docker se ejecute el contenedor rpki-validator.

5. Para conectarnos al contenedor rpki-validator ejecutamos: 
```sh
$ sudo docker exec -it rpki-validator /bin/bash
root@rpki:/rpki-validator-app-2.24#
```
6. Verificamos que el validador este escuchsndo en los puertos 8080 y 8282.
```sh
root@rpki:/rpki-validator-app-2.24# lsof -nPi | grep LISTEN
java       63 root   87u  IPv6     62992      0t0  TCP *:8282 (LISTEN)
java       63 root   93u  IPv6     62999      0t0  TCP *:8080 (LISTEN)
```
7. Verificamos el estado y funcionamiento del rpki-validador ingresando a la pagina web https://ip_route_server:8080.
