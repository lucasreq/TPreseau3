# TPreseau3
Lucas Requena Gabriel Fougerol

## I. Creation et utilisation simples d'une VM CentOS
### 4. Configuration reseau d'une machine CentOS 

1. ```nslookup``` ==> google.com
2. ```ping``` ip 
3. ```ip route```

### 5. Faire joujou avec quelques commandes

```ping``` windows ==> 192.168.127.10

```ping``` centOS ==> 192.168.127.1

Trace route windows ```route print -4```
Trace route CentOS ```traceroute``` ou ```ip route```

```curl``` ==> google.com :charge le code html de la page google.com  
```curl -o http://lakanal.net/ressources/poesies/bonjourA4_lak.pdf``` telecharge le code html de ce magnifique poème nommé [bonjour](http://lakanal.net/ressources/poesies/bonjourA4_lak.pdf)

```dig``` ==> google.com
```dig``` ==> ynov.com

## II. Notion de ports et SSH
### 1. Exploration des ports locaux

### 2. SSH
```shell
ssh root@192.168.127.10
root@192.168.127.10's password:
Last login: Tue Jan 21 17:08:00 2019 from 192.168.127.1
C:\Users\lucas> ssh root@192.168.127.10
root@192.168.127.10's password:
Permission denied, please try again.
[root@localhost ~]# pwd
```

### 3. Firewall
```shell
[root@localhost ~]# firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3
  sources:
  services: ssh dhcpv6-client
  ports:
  protocols:
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
 ```
 
Ouvrir le port 2222

```shell
[root@localhost ~]# firewall-cmd --add-port=2222/tcp --permanent
success
[root@localhost ~]# firewall-cmd --remove-port=2222/tcp --permanent
success
[root@localhost ~]# firewall-cmd --reload
success
```

#### SHH

Modification fichier ```shell /etc/ssh/sshd_config ```
```shell
[root@localhost ~]# cd /etc/ssh/ 
[root@localhost ssh]# nano sshd_config
```
verification
```shell
[root@localhost ssh]# systemctl restart sshd
[root@localhost ssh]# ss -4 -ntpl
State      Recv-Q Send-Q Local Address:Port               Peer Address:Port     
LISTEN     0      128          *:2222                     *:*                   users:(("sshd",pid=3890,fd=3))
LISTEN     0      100    127.0.0.1:25                       *:*                   users:(("master",pid=3659,fd=13))
```

ouverture du port 2222
```shell
firewall-cmd --add-port=2222/tcp --permanent
``` 

connection sur le serveur ssh

## III. Routage statique

### 1. Preparation des hôtes (vos PCs)


### 2. Configuration du routage

