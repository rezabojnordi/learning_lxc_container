# learning_lxc_container
importan command in lxc container
## command

image
Which lxc
launch
Wich lxd
stop
Dpkg -i |grep lxd
delete
Systemctl status lxd
list
Lxd init [btfs,dir,lvm]
exec
Lxc version



Lxc --help |less

## Lxc help storage
create
edit
delete
get
set
info
list
show

Lxc storage list

## How to show repository lxc
Lxc remote list

Show to show image my system
Lxc image list

Lxc image list images:cent |less

Lxc launch ubuntu:18.04 ubuntu


How to remove start and stop container

Lxc list

Lxc delete container name

Lxc stop myubuntu

Lxc delete --force containername

Lxc move myubuntu myvm 

#### ===== error

Lxc stop myubuntu 

Lxc move myubuntu myvm

Lxc start myvm

How to connect to container
Lxc exec my vm

## You access other container why?but just to bridge 

Lxc info myvm |less

####   Pstree -p pid

## Show information config container for example cpu and memory limitation

Lxc config show myvm |less

## profile

Lxc profile list

Lxc profile show default

Lxc profile copy default custom

Lxc profile list

Lxc profile edit custome

Lxc launch ubuntu:18.04 myvm --profile custom

Lxc exec myvm bash

Lxc config set myvm limit.memory 512MB

Lxc config show myvm |less

Lxc config set myvm limit.cpu 1

Lxc delete --force myvm 


## How to add and get file in container

echo hello there > myfile

Lxc file push myfile myvm:/root  

#### -----> for send file to container

Lxc file pull myvm/root/myfile .  

#### ------->for get or download container to my local server


## How to snapshot

### You run for in myvm for create 5 directory

### For i in $(seq 5);do mkdir $i;done


Lxc snapshot myvm snap1

Lxc image list

And remove directory in vm for test restore snapshot

Lxc help snapshot

Lxc help restore |less

Lxc restore myvm snap1

Lxc exec myvm bash


### Note :how add lxc container nested

## Make configuration

Lxc stop myvm

Lxc config set myvm limits.memory 512MB

Lxc config set myvm limits.cpu 1

Lxc config set myvm security.privileged true

Lxc config set myvm security.nesting true

### Lxc profile edit custom
       Config:
             Limits.memory: 512MB
             Limits.cpu: 1


## how to run apache2 fin lx container
  
## Apache Web Server with LXDPermalink
## This section will create a container, install the Apache web server, and add ## the appropriate iptables rules in order to expose post 80.

### 1. Launch a new container:

lxc launch ubuntu:18.04 web

### 2. Update the package list in the container.

lxc exec web -- apt update

### 3. Install the Apache in the LXD container.

lxc exec web -- apt install apache2

### 4. Get a shell in the LXD container.

lxc exec web -- sudo --user ubuntu --login

### 5. Edit the default web page for Apache to make a reference that it runs inside a LXD container.

sudo nano /var/www/html/index.html

#### Change the line It works! (line number 224) to It works inside a LXD container!. Then, save and exit.
### 6. Exit back to the host. We have made all the necessary changes to the container.

exit

### 7. Add a LXD proxy device to redirect connections from the internet to port 80 (HTTP) on the server to port 80 at this container.

sudo lxc config device add web myport80 proxy listen=tcp:0.0.0.0:80 connect=tcp:127.0.0.1:80

```
Note
In recent versions of LXD, you need to specify an IP address (such as 127.0.0.1) instead of a hostname (such as localhost). If your container already has a proxy device that uses hostnames, you can edit the container configuration to replace with IP addresses by running lxc config edit web.
Information for configuration container
```

### 8. From your local computer, navigate to your Linode’s public IP address in a web browser. You should see the default Apache page:


### how to update and upgrade container

lxc exec mycontainer -- apt update
lxc exec mycontainer -- apt upgrade

#### Open a shell session within mycontainer:

lxc exec mycontainer -- sudo --login --user ubuntu

### how to show log

### View the container logs:

lxc info mycontainer --show-log



https://linuxcontainers.org/lxc/manpages/man5/lxc.container.conf.5.html
https://www.kernel.org/doc/Documentation/cgroup-v1/cpusets.txt


