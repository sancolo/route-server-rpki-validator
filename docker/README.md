### Docker

La instalación de Docker en Debian 9 requiere la ejecución de los siguientes comandos como super usuario:
```sh
# apt install apt-transport-https ca-certificates curl gnupg2 softw0are-properties-common

# curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg | apt-key add -

# sudo apt-key fingerprint 0EBFCD88

# add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") $(lsb_release -cs) stable"

# apt update

# apt list --upgradable
 
# apt install docker-ce
```
Para chequear que Docker funciona es bueno correr el contenedor "hello-world":
```sh
# docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

```
Es buena practica agregar al grupo docker el usuario habilitado a correr Docker
 
```sh
# usermod -aG docker $USER
```
Finalmente agregamos el servicio Docker para que se ejecute cada vez que se re-inicie Debian.
```sh
# systemctl enable docker
```

