# DNS Packet Analysis: Query and Response for krewlworld.com

## Objective
To capture and analyze a DNS query and response for the domain `krewlworld.com` using Wireshark. This exercise helps understand how DNS lookups work at a packet level — a vital skill in network-based cybersecurity analysis.

---

## Step-by-Step Process

### 1. Start Capture
- Open **Wireshark** and select your active network interface (e.g., `en0` for Wi-Fi).
- Click the blue shark fin icon to begin capturing.

### 2. Generate Traffic
- In a browser, visit:  

'http://krewlworld.com'

### 3. Stop Capture
- Click the red stop square in Wireshark to freeze the packet capture for analysis.

### 4. Filter for DNS Packets
- In the top filter bar, type:  

(dns && frame contains “krewlworld”)

- This shows only DNS packets that reference the domain `krewlworld.com`.

---

## Packet Breakdown

### DNS Query
- **Source IP**: Your local machine
- **Destination IP**: A DNS server (e.g., 8.8.8.8)
- **Protocol**: UDP port 53
- **Query Type**: A (IPv4 address)
- **Domain Requested**: `krewlworld.com`

### DNS Response
- **Response Code**: No error
- **Answers Section**: IP address resolved for `krewlworld.com` (e.g., `76.223.105.230`)
- **Matched Transaction ID**: This links the response to the original query.
- **TTL (Time to Live)**: How long the response can be cached by the client.

---

## Raw Bytes View
- The bottom pane in Wireshark shows the raw **hexadecimal** and **ASCII** representation of the packet.
- When clicking `[Response In: ####]`, Wireshark highlights the bytes that contain the DNS answer.
- This is useful when analyzing DNS-based attacks, spoofed replies, or covert data channels.

---

## Why This Matters in Cybersecurity
- DNS is one of the first things attackers abuse or manipulate (e.g., redirecting traffic, hiding C2 servers).
- Understanding how to trace and decode DNS traffic is critical for:
- Detecting **suspicious domains**
- Catching **DNS tunneling**
- Investigating **malware communications**
- Identifying **misconfigurations**

---

## Next Steps
- Analyze DNS responses for suspicious domains.
- Try viewing DNS over TCP (port 53) or encrypted DNS (DoH/DoT).
- Compare responses from different DNS servers.

---

**File Name:** `dns_analysis.md`  
**Author:** 843krewlreaper
**Date:** 05-02-2025
