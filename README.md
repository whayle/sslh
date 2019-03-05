# whalye/sslh
container for sslh, a ssl/ssh multiplexer : https://www.rutschle.net/tech/sslh/README.html

USE AT YOUR OWN RISK

use case is for sharing an SSL connection with SSH and VPN

typically;
```bash
$ sudo docker run -d --name sslh --net=host -p 443:443 -p 127.0.0.1::22 whayle/sslh
```

*__Note:__ This image is based on [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker) which has SSH listening on 22 by default.*

## Requirements
docker >= 0.11

## Configuration
Theses options can be passed to the container using docker
```-e <variable>```.

Variable         | Function
---------------- | -----------------------------------------------------------------------------------------------------------------------------------
LISTEN_ADDR      | Address to listen on waiting for new connections. The format is ```<ip>:<port>```. Defaults to: ```0.0.0.0:443```
HTTP_TARGET_ADDR | Address to relay when a new HTTP connection is detected. The format is ```<ip>:<port>```. Defaults to: ```$HOST_ADDR:80```
XMPP_TARGET_ADDR | Address to relay when a new XMPP connection is detected. The format is ```<ip>:<port>```. Defaults to: ```$HOST_ADDR:5222```
SSL_TARGET_ADDR  | Address to relay when a new SSL (HTTPS) connection is detected. The format is ```<ip>:<port>```. Defaults to: ```$HOST_ADDR:8443```
SSH_TARGET_ADDR  | Address to relay when a new SSH connection is detected. The format is ```<ip>:<port>```. Defaults to: ```$HOST_ADDR:22```
VPN_TARGET_ADDR  | Address to relay when a new Open VPN connection is detected. The format is ```<ip>:<port>```. Defaults to: ```$HOST_ADDR:1194```
TRANSPARENT      | use the transparent option if set to true
VERBOSE          | set verbose if true
