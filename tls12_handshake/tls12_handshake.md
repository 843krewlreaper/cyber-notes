# TLS 1.2 Handshake Analysis – www.krewlworld.com

This analysis captures a full TLS 1.2 handshake between a client and `www.krewlworld.com` using Wireshark.

## Observed Packet Flow

1. **Client Hello**  
   - Starts the handshake.  
   - Contains supported cipher suites and SNI (`www.krewlworld.com`).

2. **Server Hello**  
   - Server selects a cipher suite and responds.

3. **Certificate**  
   - Server sends its SSL certificate for authentication.  
   - Details (expandable in Wireshark):
     - Common Name / SAN
     - Issuer
     - Validity

4. **Server Hello Done**

5. **Client Key Exchange**

6. **Change Cipher Spec**  
   - Client signals it will now use encrypted messages.

7. **Encrypted Handshake Message**  
   - Final handshake steps are now encrypted.

8. **Application Data**  
   - Encrypted traffic begins (e.g., page content).

## Notes
- Protocol version: **TLSv1.2**
- Server Name: **www.krewlworld.com**
- Traffic captured using Wireshark on macOS
- Initiated via browser and validated with `curl`

---

This handshake confirms that secure HTTPS communication was successfully established with the server.
