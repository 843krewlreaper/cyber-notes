# ICMP & Ping Behavior Lab — Phase 1 (Networking Foundations)

## Objective
Analyze ICMP traffic in a live environment to understand echo requests/replies, TTL behavior, and unreachable network responses.

---

## Tools Used
- **Wireshark** — for packet capture and protocol analysis
- **Terminal** — for running `ping` and `traceroute`

---

## Step-by-Step Breakdown

### 1. Basic Ping Test

Command:
```bash
ping -c 4 8.8.8.8
```

**Wireshark Filter Used:**
```wireshark
icmp
```

**Observed Packet Types:**
- `Type: 8` — Echo Request (sent from our machine)
- `Type: 0` — Echo Reply (received from 8.8.8.8)

This confirms basic ICMP echo functionality — target is reachable and responds.

---

### 2. Traceroute Analysis

Command:
```bash
traceroute google.com
```

**Observed ICMP Responses:**
- `Type: 11` — Time Exceeded (TTL expired in transit)

Each TTL-exceeded response indicates a router hop along the path. This is how traceroute maps the route from source to destination.

---

### 3. Pinging a Non-Existent Network

Command:
```bash
ping -c 4 10.255.255.1
```

**Observed ICMP Response:**
- `Type: 3` — Destination Unreachable  
- `Code: 0` — Network Unreachable

This indicates that no route exists to the network `10.255.255.0/24`.

---

## ICMP Types Summary

| Type | Code | Meaning                        |
|------|------|--------------------------------|
| 0    | —    | Echo Reply                     |
| 3    | 0    | Destination Network Unreachable|
| 3    | 3    | Destination Port Unreachable   |
| 8    | —    | Echo Request                   |
| 11   | 0    | TTL Expired in Transit         |

---

## Conclusion

Captured and analyzed various ICMP message types using `ping` and `traceroute`. This lab demonstrated how ICMP supports network diagnostics, hop-by-hop routing insights, and unreachable host detection — key skills in packet-level network analysis.
