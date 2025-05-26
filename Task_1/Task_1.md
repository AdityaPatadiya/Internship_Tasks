### Total IP scan: 4 (192.168.75.1, 192.168.75.2, 192.168.75.128, 192.168.75.254)
### Total Open ports: 1 (53 in 192.168.75.2)

### Services about the port 53:
Port 53 is used by the Domain Name System (DNS) protocol — which is like the phonebook of the internet.
When you type a website like www.google.com, your computer doesn’t understand domain names directly — it needs to convert that into an IP address (like 142.250.195.36) so it can connect to Google's servers.

This conversion process is done via DNS, which runs over port 53.


| Protocol     | Transport Layer | Usage                                                                           |
| ------------ | --------------- | ------------------------------------------------------------------------------- |
| DNS over UDP | UDP 53          | Used for fast, small requests like resolving `www.example.com`                  |
| DNS over TCP | TCP 53          | Used for large queries (e.g., zone transfers, DNSSEC), or fallback if UDP fails |


Typical DNS Tasks Using Port 53
- Name resolution (most common)
  - Convert domain names into IP addresses (A, AAAA records).

- Reverse DNS lookup
  - Convert IP address to domain name (PTR records).

- Mail server lookups
  - Find mail servers for a domain (MX records).

- Service discovery
  - Find services for a domain (SRV records).

- Zone transfers (AXFR)
  - Used between DNS servers to replicate records (done over TCP 53).


## Important Notes:
DNS was not designed with security in mind, so DNSSEC (DNS Security Extensions) and DoH/DoT (DNS over HTTPS/TLS) were later introduced.
These more secure versions still rely on DNS, but not directly on traditional port 53 (e.g., DoH uses port 443).


## Potential Security Risk for the port 53:
1. DNS Cache Poisoning / Spoofing
What happens: An attacker tricks a DNS server into caching a malicious mapping between domain names and IP addresses.

Impact: Redirects users to malicious websites (e.g., phishing, malware delivery).

Tools: dnsspoof, ettercap, responder

2. DNS Amplification Attacks (DDoS)
What happens: Attackers send small DNS queries with a spoofed source IP (victim’s) and get large responses.

Impact: Overwhelms the target with huge amounts of traffic.

Exploited Service: Open recursive DNS servers (those that answer DNS queries from any IP).

3. Zone Transfer (AXFR) Information Disclosure
What happens: A misconfigured DNS server allows unauthorized zone transfers (AXFR).

Impact: An attacker can download all DNS records (internal hosts, subdomains, IPs).

How to test:

`dig axfr @<dns-server-ip> domain.com`

4. DNS Tunneling
What happens: Attackers exfiltrate data or create backdoors using DNS queries/responses.

Use case: Bypasses firewalls and proxies since DNS traffic is usually allowed.

Tools: iodine, dnscat2

5. Buffer Overflow / Remote Code Execution (RCE)
DNS servers (like BIND, dnsmasq, Windows DNS Server) have had past vulnerabilities leading to:

Buffer overflows

Denial of Service (DoS)

Remote Code Execution

Examples:

CVE-2020-1350 (Windows DNS RCE)

CVE-2015-5477 (BIND DoS)

6. Misconfigured DNSSEC
DNSSEC is meant to secure DNS, but incorrect configuration can lead to:

Zones being unreachable

Validation failures, opening the door to spoofing

7. DNS Rebinding Attacks

What happens: Malicious websites trick a browser into communicating with internal IPs via DNS tricks.

Impact: Attacker can access internal web apps or APIs from a victim's browser.
