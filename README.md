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




Information for configuration container
https://linuxcontainers.org/lxc/manpages/man5/lxc.container.conf.5.html
https://www.kernel.org/doc/Documentation/cgroup-v1/cpusets.txt


