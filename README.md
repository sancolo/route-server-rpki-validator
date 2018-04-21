# route-server-rpki-validator

BIRD Route Server + RIPE NCC RPKI Validator

# Descripción

Este repositorio es una implementación de un route server con validación del origen de rutas. 
Se utiliza Docker para virtualizar y ejecutar las instancias que cada demonio, para los cuales se utilizan los paquetes BIRD y RIPE NCC RPKI Validator.

La construcción, instalación, configuración y detalles de la ejecución de cada contenedor se describen en el README.md de cada directorio. Es importante seguir el siguiente orden en la instalación:

1. Debian 

> Es necesario disponer de una distribución de Linux para comenzar la implementación. En nuestro caso instalamos Debian 9 server básico en una máquina física o virtual. 

2. [Docker](docker/README.md)

3. [RPKI Validator](rpki-validator/README.md)  

4. [BIRD](bird/README.md) 

