# Cybersecurity Learning Repository

This repository documents my hands-on journey into the world of cybersecurity — breaking down complex topics into digestible, real-world examples and packet-level analysis.

---

## Table of Contents

### Phase 1 – Networking Foundations & Protocol Analysis

1. **[Networking Basics](./networking_basics/README.md)**  
   Overview of fundamental networking concepts including IP addressing, ports, protocols, OSI model, and interfaces.

2. **[DNS Traffic Analysis](./dns_traffic/README.md)**  
   Hands-on analysis of DNS query/response flow using Wireshark. Includes inspection of query types, response codes, and SNI resolution.

3. **[HTTP Traffic Analysis](./http_traffic/README.md)**  
   Deep dive into unencrypted HTTP requests and responses, including GET/POST methods, status codes, and headers.

4. **[TLS 1.2 Handshake](./tls_handshake/tls12_handshake.md)**  
   Full breakdown of a secure TLS 1.2 handshake, observed in Wireshark. Highlights each stage of negotiation and transition to encrypted communication.

---

## Tools Used

- **Wireshark** – for packet capture and protocol analysis  
- **VirtualBox + Kali Linux** – testing environment  
- **curl & browser** – traffic generation  
- **GitHub** – version control and documentation

---

## Notes

Each folder includes:
- A `.md` file summarizing what was learned
- Screenshots (optional)
- Packet-level explanations using real-world websites and tools

This repo is being actively built as part of my cybersecurity foundation — focusing on hands-on skill development from the ground up.
