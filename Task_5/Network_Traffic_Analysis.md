# Wireshark Traffic Analysis Documentation
### 1. Install Wireshark

Download and install Wireshark from the official website:

👉 https://www.wireshark.org/download.html

Follow the installation instructions for your operating system (Windows/Linux/macOS).

### 2. Start Capturing Traffic

Launch Wireshark.

Select your active network interface (e.g., eth0, wlan0, or similar).

Click the "Start capturing packets" button (shark fin icon).

### 3. Generate Network Traffic

To generate analyzable traffic:

Open a terminal or Command Prompt.

Run the following command to ping a public DNS server:
```
ping 8.8.8.8
```

Let it run for a few seconds to ensure multiple packets are captured.

### 4. Filter Captured Packets by Protocol

Use the Wireshark display filter bar to isolate protocols:

`icmp` → To view ping (Internet Control Message Protocol) packets.

`dns` → To view DNS queries/responses.

`tcp` or `http` → To view TCP or web traffic.

Example filters:
```
icmp
dns
tcp
```

### 5. Protocols Identified

Based on the .pcapng file and the capture shown:

Protocol	Description
| Protocol    | Description                                                                            |
| ----------- | -------------------------------------------------------------------------------------- |
| **ICMP**    | Ping requests and replies to/from `8.8.8.8`.                                           |
| **DNS**     | Queries to `plugins.nessus.org` and Cloudflare DNS resolution.                         |
| **TCP/TLS** | Secure TCP handshakes and TLS 1.3 communication to `172.64.150.5` (likely HTTPS site). |

### 6. Export Capture as .pcap

In Wireshark, go to File → Save As.

Save the capture with .pcapng or .pcap extension (you used .pcapng).

### 7. Summary of Findings

ICMP (Ping)
Request from `192.168.75.128` to `8.8.8.8`.

Reply received from `8.8.8.8`.

ID, sequence numbers, and TTL values show normal ping behavior.

➤ DNS

DNS query for plugins.nessus.org.cdn.cloudflare.net.

Resolution returned both IPv4 (A) and IPv6 (AAAA) records.

➤ TCP/TLS

TCP handshake initiated by your system to `172.64.150.5:443`.

TLS 1.3 session established securely.

Session later reset (RST flag seen) indicating either a closed or failed connection.

🖧 Internal IPs Observed:

`192.168.75.128` → Likely your system.

`192.168.75.2` → Likely default gateway or DNS resolver.

### Files Included
✅ [.pcapng capture file: Traffic_Analysis_with Ping.pcapng]

✅ [Screenshot: showing filtered ICMP, DNS, and TCP traffic.]
