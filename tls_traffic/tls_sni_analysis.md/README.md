# TLS & SNI Analysis: www.krewlworld.com

## Overview
This analysis captures and explains how TLS 1.3 handshakes work and how to locate the Server Name Indication (SNI) in Wireshark when visiting a domain like `www.krewlworld.com`.

## Tools Used
- Wireshark (packet capture)
- cURL (command-line request)
- Kali Linux & macOS
- VirtualBox

---

## Key Concepts

### TLS 1.3 Handshake
- **Client Hello**: Sent from the browser or terminal to initiate the handshake.
- **Server Hello**: Response that confirms the TLS version and cipher suite.
- **Certificates**: Encrypted in TLS 1.3, no longer visible in plaintext.

---

### SNI (Server Name Indication)
- Found inside the `Client Hello`.
- Tells the server which domain the client wants to connect to.
- Critical for servers hosting multiple domains (SNI-based virtual hosting).

---

## How to Find the Domain in Wireshark

1. Apply the filter: ‘tcp.port == 443’
2. Find the packet labeled `Client Hello`.
3. Expand: ‘Transport Layer Security > TLSv1.3 Record Layer > Handshake Protocol: Client Hello > Extensions > server_name’
4. You should see: ‘Hostname: www.krewlworld.com’

---

## Troubleshooting

### Issue: Seeing a different server name like `automate-analytics.com`?
**Cause**: Your browser redirected you or connected to a third-party domain used by your site (like Shopify analytics or CDNs).

### Fix: Use curl to initiate a clean TLS handshake:
```bash
curl -vk https://www.krewlworld.com

This forces a new connection directly to your domain, making it easy to capture the SNI.

Final Notes
	•	TLS 1.3 encrypts certificate data; use TLS 1.2 test sites to inspect certs.
	•	SNI is sent unencrypted and is the most reliable way to identify requested domains in encrypted traffic.
