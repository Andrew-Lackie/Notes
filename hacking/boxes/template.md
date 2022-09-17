# Title of Box

IP Address: <Address_Here>

## Questions

1.
2.
3.

## What do we know?

1. 
2.
3.

## Enumeration/Scanning

### Step 1: Visit IP Address In Browser With Burp Suite Running


### Step 2: Nmap IP Address

#### Default nmap
nmap -nv -Pn -sC -sV -O -T4 -oA <IP_Address>


#### Fast nmap


#### Long nmap


### Step 3: See if there is a robot.txt file 


### Step 4: Gobuster or DirBuster


### Step 5: Review services on Nmap. Can you use automated scripts?

Example: Enum4Linux
Example: Hydra bruteforce if notice statements of weak passwords

### Step 6: Burp Suite

-Map out site

-Determine if there are any fields that could possibly be exploited

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

