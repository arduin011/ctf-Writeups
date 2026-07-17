# Networking Core Protocols
> TryHackMe Room: Networking Core Protocols
> Status: ✅ Completed

---

## 📌 Quick Summary

| Protocol | Purpose | Port |
|----------|---------|------|
| DNS | Translates domain names to IP addresses | 53 |
| WHOIS | Looks up domain registration info | 43 |
| HTTP | Accessing web pages (unencrypted) | 80 |
| HTTPS | Accessing web pages (encrypted) | 443 |
| FTP | Transferring files | 21 |
| SMTP | Sending emails | 25 |
| POP3 | Receiving emails (downloads) | 110 |
| IMAP | Receiving emails (syncs) | 143 |

---

## 📖 Detailed Notes

### 1. DNS (Domain Name System)
- Acts like a **phonebook of the internet**
- Translates human-readable domain names (google.com) into IP addresses (142.250.x.x)
- Without DNS, you would need to memorize IP addresses instead of domain names
- **Command:**
```bash
nslookup google.com
dig google.com
```

---

### 2. WHOIS
- A protocol used to **look up registration information** of a domain
- Shows: owner, registrar, creation date, expiration date, name servers
- Useful in **reconnaissance** during penetration testing
- **Command:**
```bash
whois google.com
```

---

### 3. HTTP/S (HyperText Transfer Protocol)
- Used for **accessing web pages**
- HTTP = unencrypted (port 80)
- HTTPS = encrypted via SSL/TLS (port 443)
- Uses request methods: `GET`, `POST`, `PUT`, `DELETE`
- **Manual testing via Telnet:**
```bash
telnet 10.10.x.x 80
GET /page.html HTTP/1.1
Host: 10.10.x.x
# Press Enter twice
```

---

### 4. FTP (File Transfer Protocol)
- Used for **transferring files** between client and server
- Requires authentication (username + password)
- **Commands:**
```bash
ftp 10.10.x.x        # connect
ls                    # list files
get filename          # download file
put filename          # upload file
bye                   # disconnect
```

---

### 5. SMTP (Simple Mail Transfer Protocol)
- Used for **sending emails**
- Works between mail servers and email clients
- **Manual testing via Telnet:**
```bash
telnet 10.10.x.x 25
HELO client.example.com
MAIL FROM: <sender@example.com>
RCPT TO: <recipient@example.com>
DATA
Subject: Test Email
Hello!
.
QUIT
```

---

### 6. POP3 (Post Office Protocol v3)
- Used for **receiving/downloading emails**
- Downloads emails from server to local device
- Emails are usually **deleted from server** after download
- **Manual testing via Telnet:**
```bash
telnet 10.10.x.x 110
USER username
PASS password
STAT          # check number of emails
LIST          # list emails
RETR 1        # read email #1
QUIT
```

---

### 7. IMAP (Internet Message Access Protocol)
- Used for **receiving/syncing emails**
- Unlike POP3, emails **stay on the server**
- Allows access from **multiple devices** (phone, laptop, etc.)
- **Manual testing via Telnet:**
```bash
telnet 10.10.x.x 143
a LOGIN username password
a SELECT INBOX
a FETCH 1 BODY[]     # read email #1
a LOGOUT
```

---

## 🛠️ Cheat Sheet

### Common Ports
```
DNS    = Port 53
WHOIS  = Port 43
HTTP   = Port 80
HTTPS  = Port 443
FTP    = Port 21
SMTP   = Port 25
POP3   = Port 110
IMAP   = Port 143
```

### Key Commands
```bash
# DNS
nslookup <domain>
dig <domain>

# WHOIS
whois <domain>

# HTTP via Telnet
telnet <IP> 80
GET / HTTP/1.1
Host: <IP>

# FTP
ftp <IP>

# SMTP via Telnet
telnet <IP> 25

# POP3 via Telnet
telnet <IP> 110

# IMAP via Telnet
telnet <IP> 143
```

---

## 💡 Key Takeaways

- **DNS** = phonebook ng internet — converts domain → IP
- **WHOIS** = useful sa recon para malaman kung sino may-ari ng domain
- **HTTP/S** = basis ng web browsing — HTTPS is encrypted, HTTP is not
- **FTP** = file transfer — insecure kaya may SFTP/FTPS na ngayon
- **SMTP** = para sa pagpapadala ng email
- **POP3 vs IMAP** = POP3 downloads at deletes, IMAP syncs across devices
- **Telnet** = pwedeng gamitin para manually test at interact with these protocols

---

*Notes by: sean.orzales13*
*Platform: TryHackMe*
