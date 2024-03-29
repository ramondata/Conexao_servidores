![banner_server](https://raw.githubusercontent.com/ramondata/Conexao_servidores/master/server-status-check-maintenance-report-with-modern-flat-style-minimalist-green-color-theme_65709-88.avif)
Criação de dois servers linux com conexão de acesso remoto
==============

###### Comandos `docker` para criação de duas máquinas linux ubuntu como container

> Criando volume persistente de dados para o container
```
docker volume create volume2servers 
```
> Criando a própria rede do tipo bridge para a conexão dos servidores
```
docker network create --drive bridge net2servers 
```
## Executando as `imagens` para serem `containers` de ubuntu

```
docker run -it --name server-1 --mount source=volume2servers,target=/data --network net2servers ubuntu bash

docker run -it --name server-2 --mount source=volume2servers,target=/data --network net2servers ubuntu bash
```

## Executar esses comandos dentro de cada server
```
$ apt-get update -y

$ apt install iputils-ping -y

$ apt install openssh-server -y

$ apt install openssh-client -y

$ service ssh start

$ apt install net-tools -y

$ apt-get install ufw -y

$ ufw enable

$ ufw allow 2244/tcp

$ ifconfig -> obter o ip do server

$ apt-get install iptables sudo -y

$ adduser user1 -> cadastre uma senha para o novo user

## Testando conexão

$ ping < ip >

$ ssh < user >@< ip > -> ssh user1@172.0.1.1
```
