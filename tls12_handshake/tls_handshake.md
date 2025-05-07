# TLS Handshake Analysis: TLS 1.2 vs TLS 1.3

**Transport Layer Security (TLS)** is the cryptographic protocol used to secure communications over the internet. This file provides a side-by-side breakdown of TLS 1.2 and TLS 1.3 handshakes based on packet capture observations using Wireshark.

---

## TLS 1.2 Handshake Breakdown

A typical TLS 1.2 handshake includes these steps:

1. **Client Hello**
   - Starts the TLS handshake
   - Contains supported TLS versions, cipher suites, extensions (like SNI)

2. **Server Hello**
   - Server selects protocol version, cipher suite

3. **Certificate**
   - Server sends its digital certificate (visible in plaintext)

4. **Server Hello Done**

5. **Client Key Exchange**
   - Client sends pre-master secret encrypted with server’s public key

6. **Change Cipher Spec**
   - Client and server switch to encrypted communication

7. **Encrypted Handshake Message**
   - Final step confirming encrypted session

8. **Application Data**
   - Encrypted HTTPS or other traffic begins

---

## TLS 1.3 Handshake Breakdown

TLS 1.3 reduces latency and improves security by simplifying the handshake:

1. **Client Hello**
   - Contains all necessary parameters to begin encryption
   - Includes extensions, key shares, and cipher suites

2. **Server Hello**
   - Server agrees to parameters and immediately transitions to encrypted messages

3. **Encrypted Handshake Message**
   - Certificate and key exchange are encrypted (not visible in Wireshark)

4. **Application Data**
   - Encrypted communication starts faster

---

## Key Differences Between TLS 1.2 and TLS 1.3

| Feature                     | TLS 1.2                         | TLS 1.3                          |
|-----------------------------|----------------------------------|----------------------------------|
| Certificate visibility      | Visible in plaintext            | Encrypted                        |
| Round trips                 | Multiple                        | One (or 1.5)                     |
| Forward secrecy             | Optional                        | Required                         |
| Performance                 | Slower                          | Faster                           |
| Security                    | Moderate                        | Stronger                         |

---

## Tools Used

- **Wireshark**: Captured TLS packets
- **Firefox with SSLKEYLOGFILE**: Logged secrets to allow TLS decryption
- **cURL**: Used to generate TLS traffic on demand

---

## Notes

- TLS 1.3 encrypts most of the handshake, so tools like Wireshark won’t show certificates unless decryption is set up.
- For decryption, set the `SSLKEYLOGFILE` environment variable before launching Firefox or Chrome.
- QUIC and HTTP/3 traffic often bypasses traditional TLS capture methods and uses UDP.

---

This documentation is part of the `cyber-notes` repo for studying core network protocols and traffic analysis techniques.
