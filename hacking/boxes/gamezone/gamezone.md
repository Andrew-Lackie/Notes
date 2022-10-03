# Game Zone

IP Address: 10.10.107.166

## Description

Learn to hack into this machine. Understand how to use SQLMap, crack some passwords, reveal services using a reverse SSH tunnel and escalate your privileges to root!

## Flags

1. 
2.

## Enumeration/Scanning

### Nmap

Run nmap to determine open ports. 

```sh
$ sudo nmap -sV -vv -sC -oN gamezone.nmap 10.10.107.166

# Nmap 7.92 scan initiated Sun Oct  2 21:29:01 2022 as: nmap -sV -vv -sC -oN gamezone.nmap 10.10.107.166
Nmap scan report for 10.10.107.166
Host is up, received echo-reply ttl 63 (0.19s latency).
Scanned at 2022-10-02 21:29:01 PDT for 19s
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE REASON         VERSION
22/tcp open  ssh     syn-ack ttl 63 OpenSSH 7.2p2 Ubuntu 4ubuntu2.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 61:ea:89:f1:d4:a7:dc:a5:50:f7:6d:89:c3:af:0b:03 (RSA)
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDFJTi0lKi0G+v4eFQU+P+CBodBOruOQC+3C/nXv0JVeR7yDWH6iRsFsevDofWcq05MZBr/CDPCnluhZzM1psx+5bp1Eiv3ecO0PF1QjhAzsPwUcmFSG1zAg+S757M+RFeRs0Jw0WMev8N6aR3uBZQSDPwBHGps+mZZZRcsssckJGQCZ4Qg/6PVFIwNGx9UoftdMFyfNMU/TDZmoatzo/FNEJOhbR38dF/xw9s/HRhugrUsLdNHyBxYShcY3B0Y2eLjnnuUWhYPmLZqgHuHr+eKnb1Ae3MB5lJTfZf3OmWaqcDVI3wpvQK7ACC9S8nxL3vYLyzxlvucEZHM9ILBI7Ov
|   256 b3:7d:72:46:1e:d3:41:b6:6a:91:15:16:c9:4a:a5:fa (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKAU0Orx0zOb8C4AtiV+Q1z2yj1DKw5Z2TA2UTS9Ee1AYJcMtM62+f7vGCgoTNN3eFj3lTvktOt+nMYsipuCxdY=
|   256 53:67:09:dc:ff:fb:3a:3e:fb:fe:cf:d8:6d:41:27:ab (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIL6LScmHgHeP2OMerYFiDsNPqgqFbsL+GsyehB76kldy
80/tcp open  http    syn-ack ttl 63 Apache httpd 2.4.18 ((Ubuntu))
| http-cookie-flags: 
|   /: 
|     PHPSESSID: 
|_      httponly flag not set
|_http-title: Game Zone
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun Oct  2 21:29:20 2022 -- 1 IP address (1 host up) scanned in 19.81 seconds
```

### Web Servers

#### Port 80

`http://http://10.10.107.166/`

![Gamezone](img/gamezone-server.png)

## Exploitation
### Inital SQL Injection

To log in to this, we can inject SQL into the login form.

![SQL Injection](img/sql-inj.png)

#### SQLMap

We're going to use SQLMap to dump the entire database for GameZone. It can be installed [here](https://github.com/sqlmapproject/sqlmap), though it does come preinstalled on Kali.

Now we need to use Burpsuite to intercept a request made to the server. Navigate to the proxy tab and enable incept, then type a request into the "search for gave review" bar and submit.

![Burpsuite](img/burpsuite.png)

Now we have to save this request to a file and run `sqlmap`.

```sh
$ sqlmap -r burpsuite_request.txt --dbms=mysql --dump
```

## Privilege Escalation


