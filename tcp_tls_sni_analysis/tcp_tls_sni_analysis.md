# TCP Handshake & TLS/SNI Analysis — krewlworld.com

## Objective
Capture and analyze a full TCP 3-way handshake and TLS Client Hello to identify key metadata, including Server Name Indication (SNI), for the domain `krewlworld.com`.

---

## Tools Used
- **Wireshark** — for packet capture and protocol analysis
- **Browser (Chrome)** — to initiate HTTPS connection
- **Terminal (`nslookup`)** — for DNS resolution

---

## Step-by-Step Breakdown

### 1. Triggering the Traffic
- Opened Wireshark and selected the correct network interface (Wi-Fi).
- Closed all browser windows before capture.
- Started capture and visited: `https://krewlworld.com`.

---

### 2. Identifying the TCP Handshake
Applied the following Wireshark display filter to isolate TCP connection setup:

```wireshark
tcp.flags.syn == 1
```

Found a packet with:
- **Destination Port:** 443 (HTTPS)
- **Destination IP:** Matched IP returned from:
  ```bash
  nslookup krewlworld.com
  ```

#### TCP 3-Way Handshake Observed:
- `[SYN]` — Client initiates connection
- `[SYN, ACK]` — Server acknowledges
- `[ACK]` — Client completes handshake

---

### 3. Verifying TLS & SNI (Server Name Indication)

Used this Wireshark filter to locate TLS handshake metadata:

```wireshark
ssl.handshake.extensions_server_name
```

Located a `Client Hello` packet with:
```
Extension: server_name
  Server Name: krewlworld.com
```

This confirms the TLS session is for the correct domain, even though the content is encrypted.

---

## Key Observations

- Although HTTPS encrypts application data, metadata such as **SNI** remains visible during the handshake.
- Destination IP may vary due to Shopify’s use of CDN edge servers, but matching DNS and port confirmed the traffic source.
- Wireshark’s **Follow TCP Stream** feature helped visualize the handshake (SYN → SYN/ACK → ACK).

---

## Optional Screenshots
If adding screenshots later, consider:
- TCP handshake packet view
- TLS `Client Hello` with highlighted Server Name: `krewlworld.com`

---

## Conclusion

Successfully captured and analyzed the TCP 3-way handshake and TLS Client Hello for `krewlworld.com`, including confirmation of the Server Name Indication. This fulfills a core requirement in Phase 1 of the Cybersecurity Networking Foundations roadmap.
