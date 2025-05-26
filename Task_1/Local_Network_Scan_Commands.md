Command: `ifconfig`:
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.75.128  netmask 255.255.255.0  broadcast 192.168.75.255
        inet6 fe80::20c:29ff:fee5:a15  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:e5:0a:15  txqueuelen 1000  (Ethernet)
        RX packets 300977  bytes 453865019 (432.8 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 238554  bytes 14340419 (13.6 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2028  bytes 85480 (83.4 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2028  bytes 85480 (83.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

Command: `nmap -sS 192.168.75.0/24`:
```
Starting Nmap 7.95 ( https://nmap.org ) at 2025-05-26 10:22 IST
Nmap scan report for 192.168.75.1
Host is up (0.00040s latency).
All 1000 scanned ports on 192.168.75.1 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 00:50:56:C0:00:08 (VMware)

Nmap scan report for 192.168.75.2
Host is up (0.00032s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
53/tcp open  domain
MAC Address: 00:50:56:F7:FB:48 (VMware)

Nmap scan report for 192.168.75.254
Host is up (0.00033s latency).
All 1000 scanned ports on 192.168.75.254 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 00:50:56:E6:45:D7 (VMware)

Nmap scan report for 192.168.75.128
Host is up (0.000012s latency).
All 1000 scanned ports on 192.168.75.128 are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 256 IP addresses (4 hosts up) scanned in 8.57 seconds
```
