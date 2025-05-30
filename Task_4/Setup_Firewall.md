# Linux Firewall Configuration using UFW

This document outlines the steps taken to configure the Linux firewall using **UFW (Uncomplicated Firewall)** to manage traffic filtering rules.

---

## ✅ Task Steps


### 1. Open Firewall Configuration Tool

Check UFW status:

Command: `sudo ufw status`

Output:
```
aditya@HP:~$ sudo ufw status
Status: inactive
```

Enable if inactive

Command: `sudo ufw enable`

Output:
```
aditya@HP:~$ sudo ufw status
Status: active
```

### 2. List Current Firewall Rules:

`sudo ufw status numbered`


### 3. Block Inbound Traffic on Port 23 (Telnet):

Command: `sudo ufw deny 23`

Output:
```
aditya@HP:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 23                         DENY IN     Anywhere
[ 2] 22                         ALLOW IN    Anywhere
[ 3] 23 (v6)                    DENY IN     Anywhere (v6)
[ 4] 22 (v6)                    ALLOW IN    Anywhere (v6)
```


### 4. Test the Rules (locally):

`sudo apt install telnet`

Attempt connection:

Command: `telnet localhost 23`

Output:
```
aditya@HP:~$ telnet localhost 23
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```


### 5. Allow SSH (Port 22)

To ensure remote access reoains open:

Command: `sudo ufw allow 22`

Output:
```
aditya@HP:~$ sudo ufw allow 22
Rule added
Rule added (v6)
```


### 6 Remove the Telnet Block Rule:

Command: `sudo ufw delete 1`

Output: 
```
aditya@HP:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 23                         DENY IN     Anywhere
[ 2] 22                         ALLOW IN    Anywhere
[ 3] 23 (v6)                    DENY IN     Anywhere (v6)
[ 4] 22 (v6)                    ALLOW IN    Anywhere (v6)
```

📜 Summary: How UFW Filters Traffic

- UFW is a frontend for iptables, providing an easy way to manage firewall rules.

- It filters traffic based on IP addresses, ports, and protocols.

- Default policy: deny incoming traffic and allow outgoing unless specified.

- Allows adding allow, deny, and limit rules to define how traffic flows.

- Rules are applied in order and logged (if logging is enabled).


### Command Used (Summery Table)
| Purpose                    | Command                         |
| -------------------------- | ------------------------------- |
| Enable UFW                 | `sudo ufw enable`               |
| Check firewall status      | `sudo ufw status numbered`      |
| Block port 23 (Telnet)     | `sudo ufw deny 23`              |
| Test connection to port 23 | `telnet localhost 23`           |
| Allow SSH port 22          | `sudo ufw allow 22`             |
| Delete rule by number      | `sudo ufw delete <rule-number>` |


### Environment Info

OS: Linux (Ubuntu-based)

Firewall Tool: UFW

User Privilege: Root (sudo)
