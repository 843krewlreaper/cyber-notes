# TCP 3-Way Handshake Packet Analysis

## Objective
To capture and analyze a **TCP 3-way handshake** using Wireshark. This is the process used to establish a reliable connection between two devices before any data is exchanged - critical for understanding how secure and stable communications begin over the internet.

---

## What Is a TCP 3-Way Handshake?

It's a **three-step process** that initiates a connection between a client and a server over TCP: 

| Step | Direction | Purpose|
|------|-----------|--------|
| 1. SYN | Client -> Server | Requests to start a connection |
| 2. SYN-ACK | Server -> Client | Acknowledges the request, and agrees |
| 3. ACK | Client -> Server | Confirms and estblishes the connection |

---

## How to Capture It In Wireshark

### Step 1: Start Wireshark
- Open **Wireshark**
- Choose your network interface (e.g., 'en0' for Wi-Fi)
- Click the **blue shark fin** to start capture

---

### Step 2: Trigger TCP Handshake
- Open your terminal and run:
    '''bash
  curl http://example.com

This sends a basic HTTP request - which begins with a TCP handshake.

---

### Step 3: Stop the Capture
Click the **red square** in **Wireshark** to start capturing packets.

---

### Step 4: Filter for SYN Packets
- In the top filter bar, type: 'tcp.flags.syn == 1 && tcp.flags.ack == 0'
- This shows only initial SYN packets - the start of any TCP handshake.

---

### Step 5: Locate the 3-Way Handshake
Find 3 consecutive packets between the same two IPs and ports:
- **Packet 1 (SYN)**: Your machine -> Server
- **Packet 2 (SYN-ACK)**: Server -> Your machine
- **Packet 3 (ACK)**: Your machine -> Server

You can follow the stream by:
- Right clicking the SYN packet
- Selecting **Follow > TCP Stream**

---

## What to Look For
**Packet 1: SYN**
- **Flags**: SYN = 1, ACK = 0
- **Sequence Number**: Random starting value

**Packet 2: SYN-ACK**
- **Flags**: SYN = 1, ACK = 1
- **Acknowledgment Number**: Your initial sequence + 1

**Packet 3: ACK**
**Flags**: ACK = 1
**Sequence Number**: Matches expected value

---

## Why This Matter in Cybersecurity
Understanding TCP handshakes is key to:
- **Detecting scans** (e.g., SYN floods, half-open connections)
- **Identifying suspicious activity** (abnormal connection patterns)
- **Recognizing man-in-the-middle attacks**
- **Analyzing malwar behavior**

---

##Next Steps
- Practice spotting abnormal handshakes (e.g., missing ACKs)
- Analyze HTTPS handshakes (after TCP is established)
- Study TCP teardown (FIN and RST flags)

---

**File Number**: tcp_handshake.md
**Author**: 843krewlreaper
**Date**: 05-02-2025
