# Linux commands 

to access something as root on ubuntu you can use sudo

while in debian you have su / su -l(for actions like dhclient or for changing/adding users and groups)

## get system information

### kernel vesion

> uname -r

see more info about kernel

> uname -a

See active processes 

default installed on debian

>top

not installed by default 

>htop

traceroute - see all routers your packets will travel through in effort to ping that Server

>traceroute ${-4 || -6} ${link || or ip}

that -4 or -6 means is it ipv4 or ipv6



## TIMEZONE

see all timezones

>timedatectl list-timezones

set timezone

>timedatectl set-timezone ${timezone}

## user managment

add user

> adduser ${name} $[group_name]

delete user

>userdel ${name} 

all data about users is stored in `/etc/passwd`

change password of user

>passwd ${name}

## Group managment

add group

>groupadd ${name}

delete group

>groupdel ${name}

### all data about groups is stored in `/etc/group



## premissions 

4=read

2=write

1=execute

7=read+write+execute

764

7 stands for autor of that file(owner)

6 stands for other users in same group as autor(owner)

4 stands for everyone else (every other user that is not in same group as owner)


changing premission of file

>chmod ${3 numbers of premission} ${file_path} -R

that -R stands for every file in that folder 

>ls -l

that lists files and display premissions and owners 


change owner 

>chown -R ${new user} ${file}


## Networking

show hostname

>hostname

rename your computer 

>hostname ${new name}

show ip information

>ip a || ip addr

turn network card up on some network card

>ip link set ${nameofnethworkcard} up

set ip of network card

>ip address add ${ip}/${subnet} dev ${nameofnetworkrcard}

>ip addr add ${ip}/${subnet} broadcast ${final IP of subnet} dev enp3s0
//ip addr add 192.168.0.77/24 broadcast 192.168.0.255 dev enp3s0

speaking of subnetmask

`inet 192.168.1.2/24`

that 24 means 255.255.255.0

8 means 255.0.0.0

get router ip address

>ip route

release IP

>dhclient -r

renew

>dhclient

save changes on networking configuration `/etc/init.d/networking restart`

setting up ip address is here /etc/network/interfaces

change from 
```sh
iface enp3s0 inet dhcp

```

to

```sh
iface eth0 inet static

address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254

```

DNS configuration is in `/etc/resolv.conf`


firewall UFW(Ubuntu has it installed by default while debian doesnt )

status

>ufw status 

setting default settings 

block all trafic by defualt 

>ufw default deny

allow all trafic by defualt

>ufw default allow

turn on ufw

>ufw enable

turn off ufw

>ufw disable

rules 

open/close some port

>ufw allow/deny ${port number}

ban/allow traffic from some ip

>ufw allow/deny from ${ip || 243.213.* . *}

ban/allow traffic from some ip but only on specific port for them to access 

>ufw allow/deny from ${ip || 243.213.*.*} to ${port}


---

## Sudo

sudo is command for running files with root privilages 

install sudo (if you dont have it installed already)

`User privilege specification`

or under 

` Allows root to run any commands anywhere `

copy and paste configuration for root just replace root with username


## redirecting

> /etc/hosts

thats the file you want to edit 
