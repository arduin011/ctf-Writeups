# Wireshark: The Basics
> TryHackMe Room: Wireshark: The Basics
> Status: ✅ Completed

---

## 📌 Quick Summary

| Feature | Description |
|---------|-------------|
| Tool | Wireshark |
| Purpose | Network packet analyzer / traffic analysis |
| File format | `.pcap` / `.pcapng` |
| Use case | Network troubleshooting, security analysis, CTF forensics |

---

## 📖 Detailed Notes

### 1. Tool Overview
- Wireshark is a **free, open-source packet analyzer**
- Used to **capture and inspect network traffic** in real time
- Can also open **pre-captured PCAP files** for analysis
- Used by network engineers, security analysts, and pentesters

**Main Interface Sections:**
| Section | Purpose |
|---------|---------|
| Packet List | Shows all captured packets |
| Packet Details | Shows breakdown of selected packet |
| Packet Bytes | Shows raw hex/ASCII data of packet |

---

### 2. Packet Dissection
- Wireshark breaks down each packet into **protocol layers**
- Based on the **OSI Model**:

```
Layer 7 - Application  (HTTP, DNS, FTP, SMTP)
Layer 4 - Transport    (TCP, UDP)
Layer 3 - Network      (IP)
Layer 2 - Data Link    (Ethernet, MAC)
Layer 1 - Physical     (bits)
```

- Clicking a packet shows all its layers in **Packet Details pane**
- Each layer can be **expanded** to see its fields

---

### 3. Packet Navigation
Useful ways to navigate packets:

| Action | How |
|--------|-----|
| Go to specific packet | `Ctrl + G` |
| Find packet | `Ctrl + F` |
| Mark packet | `Ctrl + M` |
| Next marked packet | `Shift + Ctrl + N` |
| Follow TCP Stream | Right-click → Follow → TCP Stream |
| Follow HTTP Stream | Right-click → Follow → HTTP Stream |

**Follow Stream** — very useful for:
- Seeing full HTTP conversations
- Finding **credentials/passwords** in plaintext traffic
- Reading email content captured in PCAP

---

### 4. Packet Filtering
Wireshark has two types of filters:

#### Capture Filters (before capturing)
- Applied **before** capture starts
- Uses BPF (Berkeley Packet Filter) syntax

```
host 192.168.1.1        # filter by IP
port 80                 # filter by port
tcp                     # TCP only
udp                     # UDP only
```

#### Display Filters (after capturing)
- Applied **after** capture — most commonly used
- More powerful and flexible

```bash
# Filter by protocol
http
dns
tcp
udp
ftp
ssh

# Filter by IP
ip.addr == 10.10.10.10
ip.src == 192.168.1.1
ip.dst == 192.168.1.1

# Filter by port
tcp.port == 80
tcp.port == 443
udp.port == 53

# Filter by HTTP method
http.request.method == "GET"
http.request.method == "POST"

# Filter by keyword in packet
frame contains "password"
http contains "flag"

# Combine filters
ip.addr == 10.10.10.10 && tcp.port == 80
http || dns
```

---

## 🛠️ Cheat Sheet

### Common Display Filters
```
http                          # all HTTP traffic
https / tls                   # all HTTPS/TLS traffic
dns                           # all DNS queries
ftp                           # FTP traffic
ssh                           # SSH traffic
tcp                           # all TCP
udp                           # all UDP
icmp                          # ping traffic

ip.addr == x.x.x.x           # filter specific IP
ip.src == x.x.x.x            # filter source IP
ip.dst == x.x.x.x            # filter destination IP

tcp.port == 80                # filter port 80
frame contains "picoCTF"      # find keyword in packets
http.request.method == "POST" # find POST requests
```

### Key Shortcuts
```
Ctrl + G    → Go to packet number
Ctrl + F    → Find packet
Ctrl + M    → Mark packet
Ctrl + E    → Export objects (files, images)
```

### Follow Stream (Right-click on packet)
```
Follow → TCP Stream     # see full TCP conversation
Follow → HTTP Stream    # see HTTP request/response
Follow → TLS Stream     # see TLS (need key to decrypt)
```

---

## 💡 Key Takeaways

- **Wireshark** = powerful tool for seeing exactly what's happening on a network
- **Packet Dissection** = breaks packets into layers — helps understand protocols deeply
- **Display Filters** = essential skill — learn the syntax para mabilis mahanap ang importante
- **Follow Stream** = pinaka-useful feature — shows full conversation including **credentials!**
- **HTTP traffic is dangerous** = passwords visible in plaintext if not using HTTPS
- **TLS/HTTPS** = encrypted — need `ssl-key.log` file to decrypt in Wireshark
- **PCAP files** = evidence in forensics — always check for credentials, flags, and suspicious traffic
- **POST requests** = where login credentials usually hide — always filter `http.request.method == "POST"`

---

## 🔍 CTF Tips with Wireshark

1. **Filter HTTP POST** → find login credentials
2. **Follow HTTP Stream** → read full web conversations
3. **Filter `frame contains "flag"`** → find CTF flags
4. **Export Objects** (File → Export Objects → HTTP) → extract downloaded files
5. **Check DNS queries** → find what domains were visited
6. **Filter FTP** → FTP sends credentials in plaintext!

---

*Notes by: sean.orzales13*
*Platform: TryHackMe*
