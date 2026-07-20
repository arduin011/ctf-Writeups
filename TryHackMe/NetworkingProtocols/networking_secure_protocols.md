# Networking Secure Protocols
> TryHackMe Room: Networking Secure Protocols
> Status: ✅ Completed

---

## 📌 Quick Summary

| Protocol | Secure Version Of | Purpose | Port |
|----------|------------------|---------|------|
| TLS | SSL | Encrypts network traffic | N/A (used by others) |
| HTTPS | HTTP | Secure web browsing | 443 |
| SMTPS | SMTP | Secure email sending | 465 / 587 |
| POP3S | POP3 | Secure email receiving (download) | 995 |
| IMAPS | IMAP | Secure email receiving (sync) | 993 |
| SSH | Telnet | Secure remote access | 22 |
| SFTP | FTP | Secure file transfer (via SSH) | 22 |
| FTPS | FTP | Secure file transfer (via TLS) | 990 |
| VPN | N/A | Secure private network tunnel | Various |

---

## 📖 Detailed Notes

### 1. TLS (Transport Layer Security)
- **Successor to SSL** — SSL is outdated and insecure
- Provides **encryption, authentication, and integrity** for network traffic
- Used by HTTPS, SMTPS, IMAPS, POP3S, and more
- How it works:
  1. Client connects to server
  2. Server sends its **certificate**
  3. Both agree on **encryption keys**
  4. Encrypted communication begins
- **Wireshark Tip:** Use `ssl-key.log` file to decrypt TLS traffic for analysis

---

### 2. HTTPS (HTTP Secure)
- HTTP + TLS = HTTPS
- All data is **encrypted** — cannot be read by attackers via packet sniffing
- Uses **port 443**
- Certificate issued by **Certificate Authority (CA)**
- **Wireshark:** Even if you capture HTTPS traffic, it appears as encrypted gibberish without the key

---

### 3. SMTPS, POP3S, and IMAPS
- Secure versions of email protocols using **TLS encryption**

| Protocol | Port | Purpose |
|----------|------|---------|
| SMTPS | 465 / 587 | Send emails securely |
| POP3S | 995 | Download emails securely |
| IMAPS | 993 | Sync emails securely |

- Without these — emails sent via plain SMTP/POP3/IMAP can be **intercepted and read**!

---

### 4. SSH (Secure Shell)
- **Secure replacement for Telnet**
- Encrypts all communication between client and server
- Used for **remote server access**
- Uses **port 22**
- **Commands:**
```bash
# Basic SSH login
ssh username@IP_ADDRESS

# SSH with specific port
ssh username@IP_ADDRESS -p 2222

# SSH with key file
ssh -i keyfile.pem username@IP_ADDRESS
```
- **Why not Telnet?** Telnet sends everything in **plaintext** — passwords visible in Wireshark!

---

### 5. SFTP and FTPS
Both are secure alternatives to FTP:

| | SFTP | FTPS |
|-|------|------|
| Stands for | SSH File Transfer Protocol | FTP Secure |
| Based on | SSH | TLS/SSL |
| Port | 22 | 990 |
| Encryption | SSH encryption | TLS encryption |

- **SFTP Commands:**
```bash
sftp username@IP_ADDRESS
ls          # list files
get file    # download
put file    # upload
bye         # disconnect
```

---

### 6. VPN (Virtual Private Network)
- Creates an **encrypted tunnel** between your device and a server
- Makes it appear as if you're in a **different location**
- Protects traffic on **public networks**
- Common VPN protocols:
  - **OpenVPN** — open source, widely used
  - **WireGuard** — modern, fast, lightweight
  - **IPSec** — commonly used in enterprise
- **TryHackMe uses OpenVPN** to connect you to their lab network!

---

## 🛠️ Cheat Sheet

### Secure Protocol Ports
```
HTTPS  = 443
SMTPS  = 465 / 587
POP3S  = 995
IMAPS  = 993
SSH    = 22
SFTP   = 22
FTPS   = 990
```

### Key Commands
```bash
# SSH
ssh username@IP
ssh -i key.pem username@IP

# SFTP
sftp username@IP

# Check TLS certificate
openssl s_client -connect example.com:443

# Wireshark — filter HTTPS
tls
tcp.port == 443
```

---

## 💡 Key Takeaways

- **TLS** = the backbone of internet security — encrypts almost everything
- **HTTPS** = always use it! HTTP is readable by anyone on the network
- **SSH > Telnet** — never use Telnet for real systems, passwords are visible!
- **SFTP/FTPS > FTP** — plain FTP sends credentials in cleartext
- **VPN** = creates encrypted tunnel — useful for privacy and accessing private networks
- **Wireshark lesson** — even encrypted traffic can be decrypted if you have the key file (`ssl-key.log`)
- **URL Encoding** — `%7B` = `{`, `%7D` = `}` — useful when reading captured credentials

---

## 🔐 Insecure vs Secure Comparison

| Insecure | Secure | What it protects |
|----------|--------|-----------------|
| HTTP | HTTPS | Web browsing |
| FTP | SFTP / FTPS | File transfer |
| Telnet | SSH | Remote access |
| SMTP | SMTPS | Sending email |
| POP3 | POP3S | Receiving email |
| IMAP | IMAPS | Syncing email |

---

*Notes by: sean.orzales13*
*Platform: TryHackMe*
