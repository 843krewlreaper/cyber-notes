# HTTP Traffic Packet Analysis

## Objective 
To capture and analyze basic **HTTP traffic** using Wireshark. This reveals how web browsers and servers communicate in clear text over the internet using the Hypertext Transfer Protocol (HTTP).

---

## What Is HTTP?

HTTP (Hypertext Transfer Protocol) is the foundation of datat communication for the web. It's a **text-based protocol** used to request and deliver web pages and resources. HTTP is **unencrypted**, making it easy to inspect in Wireshark.

> Note: Most modern websites use **HTTPS**, which encrypts traffic and hides content. For training, we use a site that still supports plain HTTP.

---

## Step-by-Step Capture

### Step 1: Start Wireshark
- Open **Wireshark**
- Select your interface ('en0' for Wi-Fi)
- Click the **blue shark fin** to start capturing

---

### Step 2: Trigger HTTP Traffic
In your terminal or browser, visit:
'''bash
http://neverssl.com

This site uses plain HTTP and allows you to view traffic clearly.

---

### Step 3: Stop the Capture
Click the red square in Wireshark to stop the packet capture

---

### Step 4: Apply HTTP Filter
Use this display filter:
- 'http'

This isolates all HTTP-related packets.

---

## Step-by-Step Analysis

### 1. Find the HTTP GET Request
- Look for a line like: 'GET / HTTP/ 1.1'
- Click to inspect:
  **Request Method**: GET
  **Host**: e.g., neverssl.com
  **User-Agent**: e.g., curl or your browser

---

### 2. Find the HTTP Screen
- Look for: 'HTTP/1.1 200 OK'
- Inspect for:
  **Status Code**: 200 (Success)
  **Content-Type**: e.g., text/html
  **Response Body**: HTML content returned by the server

---

## Why This Matters in Cybersecurity
Understanding HTTP traffic helps with:
- Spotting exposed login credentials or cookies (in HTTP, not HTTPS)
- Identifying insecure endpoints
- Tracing malware command-and-control traffic
- Creating custom intrusion detection rules

---

## Next Steps
- Analyze POST requests (used for logins/forms)
- Compare HTTP vs HTTPS in Wireshark
- Explore HTTP headers and cookies

---

**File Name**: http_analysis.md
**Author**: 843krewlreaper
**Date**: 05-02-2025
