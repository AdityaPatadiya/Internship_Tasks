## Wireshark results:
![image](https://github.com/user-attachments/assets/01cfffd4-a816-43a8-87eb-f0db4939dc98)

![image](https://github.com/user-attachments/assets/8a3bec92-07d5-453f-8b9c-aa74f0de9832)

above two images shown the result of the wireshark tool that scaned the `eth0` for my device.

### TCP portocol:

It contains mostly `TCP` protocol. TCP is used to establish reliable communication between devices.
`192.168.75.128 ↔ 172.64.150.5 (port 443 - HTTPS)`
- It shows:
  - Multiple TCP segments being sent (many are part of a reassembled PDU).
  - One packet (Frame 326124) has a [RST, ACK] flag:
    - RST (Reset): This means one side is abruptly terminating the TCP connection.
    - Possible reasons: an error, a rejected connection, or an unsupported request.
- This communication is likely part of an HTTPS request to a server at IP 172.64.150.5, which is associated with plugins.nessus.org.

### DNS Protocol:

DNS resolves domain names to IP addresses. In this capture:
`plugins.nessus.org`

- The DNS responses map the domain to:
  - IPv4: 104.18.37.251, 172.64.150.5
  - IPv6: 2606:4700:4400::ac40:9605 (in the AAAA response)
- This DNS activity precedes the HTTPS (TCP port 443) communication — as expected:
  - First, the domain name is resolved.
  - Then the client establishes a TCP connection to the resolved IP (e.g., 172.64.150.5).
