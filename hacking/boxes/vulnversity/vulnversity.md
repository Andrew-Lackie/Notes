# Vulnversity

IP Address: 10.10.154.152

## Flags

1.
2.
3.

## What do we know?

1. 
2.
3.

## Enumeration/Scanning

### Nmap:


	 sudo nmap -A -sC -p1-3500 -oN vulnversity.nmap 10.10.73.128
	 Starting Nmap 7.92 ( https://nmap.org ) at 2022-09-17 20:35 PDT
	Nmap scan report for 10.10.73.128
	Host is up (0.17s latency).
	Not shown: 3494 closed tcp ports (reset)
	PORT     STATE SERVICE     VERSION
	21/tcp   open  ftp         vsftpd 3.0.3
	22/tcp   open  ssh         OpenSSH 7.2p2 Ubuntu 4ubuntu2.7 (Ubuntu Linux; protocol 2.0)
	| ssh-hostkey: 
	|   2048 5a:4f:fc:b8:c8:76:1c:b5:85:1c:ac:b2:86:41:1c:5a (RSA)
	|   256 ac:9d:ec:44:61:0c:28:85:00:88:e9:68:e9:d0:cb:3d (ECDSA)
	|_  256 30:50:cb:70:5a:86:57:22:cb:52:d9:36:34:dc:a5:58 (ED25519)
	139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
	445/tcp  open  netbios-ssn Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)
	3128/tcp open  http-proxy  Squid http proxy 3.5.12
	|_http-server-header: squid/3.5.12
		1 # Nmap 7.92 scan initiated Sat Sep 17 20:35:44 2022 as: nmap -A -sC -p1-3500 -oN vulnversity.nmap 10.10.73.128
		2 Nmap scan report for 10.10.73.128
		3 Host is up (0.17s latency).
		4 Not shown: 3494 closed tcp ports (reset)
		5 PORT     STATE SERVICE     VERSION
		6 21/tcp   open  ftp         vsftpd 3.0.3
		7 22/tcp   open  ssh         OpenSSH 7.2p2 Ubuntu 4ubuntu2.7 (Ubuntu Linux; protocol 2.0)
		8 | ssh-hostkey:
		9 |   2048 5a:4f:fc:b8:c8:76:1c:b5:85:1c:ac:b2:86:41:1c:5a (RSA)
	|_http-title: ERROR: The requested URL could not be retrieved
	3333/tcp open  http        Apache httpd 2.4.18 ((Ubuntu))
	|_http-title: Vuln University
	|_http-server-header: Apache/2.4.18 (Ubuntu)
	No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
	TCP/IP fingerprint:
	OS:SCAN(V=7.92%E=4%D=9/17%OT=21%CT=1%CU=41748%PV=Y%DS=2%DC=T%G=Y%TM=632692A
	OS:D%P=x86_64-pc-linux-gnu)SEQ(SP=FE%GCD=1%ISR=102%TI=Z%CI=I%II=I%TS=8)SEQ(
	OS:SP=FE%GCD=1%ISR=102%TI=Z%CI=RD%TS=8)OPS(O1=M506ST11NW7%O2=M506ST11NW7%O3
	OS:=M506NNT11NW7%O4=M506ST11NW7%O5=M506ST11NW7%O6=M506ST11)WIN(W1=68DF%W2=6
	OS:8DF%W3=68DF%W4=68DF%W5=68DF%W6=68DF)ECN(R=Y%DF=Y%T=40%W=6903%O=M506NNSNW
	OS:7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF
	OS:=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=
	OS:%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=
	OS:0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RI
	OS:PCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

	Network Distance: 2 hops
	Service Info: Host: VULNUNIVERSITY; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

	Host script results:
	|_clock-skew: mean: 1h20m00s, deviation: 2h18m34s, median: 0s
	| smb-os-discovery: 
	|   OS: Windows 6.1 (Samba 4.3.11-Ubuntu)
	|   Computer name: vulnuniversity
	|   NetBIOS computer name: VULNUNIVERSITY\x00
	|   Domain name: \x00
	|   FQDN: vulnuniversity
	|_  System time: 2022-09-17T23:38:14-04:00
	| smb-security-mode: 
	|   account_used: guest
	|   authentication_level: user
	|   challenge_response: supported
	|_  message_signing: disabled (dangerous, but default)
	| smb2-time: 
	|   date: 2022-09-18T03:38:14
	|_  start_date: N/A
	| smb2-security-mode: 
	|   3.1.1: 
	|_    Message signing enabled but not required
	|_nbstat: NetBIOS name: VULNUNIVERSITY, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)

	TRACEROUTE (using port 111/tcp)
	HOP RTT       ADDRESS
	1   237.02 ms 10.18.0.1
	2   237.01 ms 10.10.73.128

	OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
	Nmap done: 1 IP address (1 host up) scanned in 157.37 seconds
		 
	
### HTTP Headers:

#### Port 3333

	curl http://10.10.73.128:3333 -v > curl.txt
	> GET / HTTP/1.1
	> Host: 10.10.73.128:3333
	> User-Agent: curl/7.84.0
	> Accept: */*
	> 
	* Mark bundle as not supporting multiuse
	< HTTP/1.1 200 OK
	< Date: Sun, 18 Sep 2022 03:51:59 GMT
	< Server: Apache/2.4.18 (Ubuntu)
	< Last-Modified: Wed, 31 Jul 2019 22:44:06 GMT
	< ETag: "80f6-58f01dcd2b575"
	< Accept-Ranges: bytes
	< Content-Length: 33014
	< Vary: Accept-Encoding
	< Content-Type: text/html
	< 
	{ [1019 bytes data]
	100 33014  100 33014    0     0  55192      0 --:--:-- --:--:-- --:--:-- 55207
	* Connection #0 to host 10.10.73.128 left intact
	
[curl.md](files/curl.md)



### Web Server Requests:

#### Port 3128

![http://10.10.72.128:3128](img/10.10.73.128:3128.png)

#### Port 3333

![http://10.10.73.128:3333](img/10.10.73.128:3333.png)

### robot.txt:

**N/a**

### sitemap.xml:

**N/a**

## Automated Discovery

### Gobuster/DirBuster:

	gobuster dir -u http://10.10.73.128:3333 -w /usr/share/wordlists/dirbuster/directory-list-1.0.txt
	===============================================================
	Gobuster v3.1.0
	by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
	===============================================================
	[+] Url:                     http://10.10.73.128:3333
	[+] Method:                  GET
	[+] Threads:                 10
	[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-1.0.txt
	[+] Negative Status codes:   404
	[+] User Agent:              gobuster/3.1.0
	[+] Timeout:                 10s
	===============================================================
	2022/09/17 21:50:57 Starting gobuster in directory enumeration mode
	===============================================================
	/images               (Status: 301) [Size: 320] [--> http://10.10.73.128:3333/images/]
	/css                  (Status: 301) [Size: 317] [--> http://10.10.73.128:3333/css/]   
	/js                   (Status: 301) [Size: 316] [--> http://10.10.73.128:3333/js/]    
	/internal             (Status: 301) [Size: 322] [--> http://10.10.73.128:3333/internal/]

### Burp Suite:



## Exploitation

### Step 1: Vulnerability

- What is the vulnerability? How can it be exploited?

### Step 2: Exploitation

- What is the exploit? How will it be executed?

## Privilege Escalation

### Do you have sudo? 

```
sudo -l
```

#### What SUID/GUID is available?

```
find / -perm -u=s -type f 2>/dev/null
```


- What directories are available?

- What files can you read?

- Run autoscript Linpeas

