### Docker commands and tips
- Listado de imagenes disponibles en el host
```sh
$ docker images
```
- Ver procesos contenedores corriendo en el host
```sh
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                            NAMES
1611c3c34128        bird-2.0.1          "/bin/sh -c 'bird -c…"   7 days ago          Up 7 days           179/tcp                                          rbird1
c9f391a27ed9        bird-2.0.1          "/bin/sh -c 'bird -c…"   7 days ago          Up 7 days           179/tcp                                          rbird2
d19077c0d04e        rpki-validator      "/rpki-validator-app…"   3 weeks ago         Up 12 days          0.0.0.0:8080->8080/tcp, 0.0.0.0:8282->8282/tcp   rpki-validator
```
- Listado de drivers de red
```sh
$ docker network list
NETWORK ID          NAME                DRIVER              SCOPE
b998edd187a9        bridge              bridge              local
b027bfad4f40        host                host                local
faa9cfb38174        none                null                local
```
- Detalle de un dispositivo de red (Ej: bridge)
```sh
$ docker network inspect bridge
```
- Logs de un contenedor (Ej: rbird1)
```sh
$ docker logs --tail 20 rbird1
. . . . . 
bird: Reconfiguring
bird: Reloading channel bgp1.ipv4
bird: Reconfigured
bird: Accept unknown ROA 0.0.0.0/0 for ASN 65002
bird: Accept unknown ROA 192.168.0.0/16 for ASN 65002
bird: Ignore invalid ROA 86.49.0.0/17 for ASN 65002
bird: Accept unknown ROA 10.0.0.0/8 for ASN 65002
bird: Ignore invalid ROA 200.3.12.0/22 for ASN 65002
bird: Reconfiguring
bird: Reloading channel bgp1.ipv6
bird: Reconfigured
bird: Accept unknown ROA ::/0 for ASN 65002
bird: Accept unknown ROA 2001:db8:4000::/48 for ASN 65002
bird: Accept unknown ROA 2001:db8::/32 for ASN 65002
bird: Ignore invalid ROA 2001:13c7:7002::/48 for ASN 65002
bird: Accept unknown ROA 2000::/4 for ASN 65002
bird: Ignore invalid ROA 2001:13c7:7012::/49 for ASN 65002
. . . . .
```
- Parar un contenedor
```sh
$ docker stop rbird1
```
- Remover un contenedor
```
$ docker rm rbird1
```




