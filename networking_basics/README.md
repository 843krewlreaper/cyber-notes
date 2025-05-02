# Networking Basics for Cybersecurity

This document contains summarized notes of essential networking concepts every cybersecurity learner should understand. These fundamentals form the foundation for understanding how data travels across networks and how attackers and defenders interact with them.

---

## 1. IP Address
An IP address is a unique indentifier assigned to every device on a network. It allows devices to locate and communicate with each other.

- **IPv4**: Example - '192.168.1.1' (most common)
- **IPv4**: Example - '2001:0db8:85a3::8a2e0370:7334' (used for modern scalability)

---

## 2. MAC Address
A Media Access Control (MAC) address is a unique hardware ID assigned to a device's network interface card (NIC). It workds at the Data Link Layer (Layer 2 of the OSI model).

- Format: '00:1A:2B:3C:4D:5E'

---

## 3. DNS (Domain Name System)
DNS is the internet's phonebook. It converts human-readable domain names (like 'krewlworld.com' into machine-readable IP addresses. 

---

## 4. Ports & Protocols
Ports are logical connection points for sending and receiving data. Protocols define rules for communication.

- Common Protocols & Their Default Ports:
  - **HTTP**: 80
  - **HTTPS**: 443
  - **SSH**: 22
  - **FTP**: 21
  - **DNS**: 53
 
---

## 5. TCP vs. UDP

| Feature  | TCP (Transmission Control Protocol) | UDP (User Datagram Protocol) |
|----------|-------------------------------------|-------------------------------|
| Speed    | Slower                              | Faster                        |
| Reliability  | Guanranteed delivery              | No guarantee                 |
| Use Case | Web browsing, email, file transfers | Video, games, VoIP            |

---

## 6. Firewalls, Routers, Switches

- **Firewall**: A security barrier that filters traffic based on rules.
- **Router**: Connects different networks and directs data packets.
- **Switch**: Connects devices within the same local network (LAN).

---

## 7. OSI Model (7 Layers)

The OSI Model explains how data travels through a network, layer by layer:

1. **Physical** - Cables, signals
2. **Data Link** - MAC addresses, switches
3. **Network** - IP addresses, routers
4. **Transport** - TCP/UDP, ports
5. **Session** - Maintains sessions between devices
6. **Presentation** - Data formatting and encryption
7. **Application** - Interfaces like browsers, apps

---

## Summary

Understanding these networking basics is a crucial first step in becoming a cybersecurity professional. These concepts will help you diagnose issues, interpret attacks, and build a strong foundation for tools like Wireshark, nmap, and firewalls.
Stay tunned for more updates as I progress through my cybersecurity learning journey.
