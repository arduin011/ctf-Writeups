# Nmap: The Basics
> TryHackMe Room: Nmap: The Basics
> Status: ✅ Completed

---

## 📌 Quick Summary

| Feature | Description |
|---------|-------------|
| Tool | Nmap (Network Mapper) |
| Purpose | Discover live hosts, open ports, and service versions |
| Use case | Network reconnaissance, penetration testing |

---

## 📖 Detailed Notes

### 1. Host Discovery: Who Is Online
- Used to find **which hosts are alive** on a network
- Nmap sends probes and checks for responses

| Command | Description |
|---------|-------------|
| `nmap -sn 10.10.10.0/24` | Ping scan — find live hosts (no port scan) |
| `nmap -PR 10.10.10.1` | ARP scan — best for local network |
| `nmap -PE 10.10.10.1` | ICMP Echo scan |
| `nmap -Pn 10.10.10.1` | Skip host discovery — assume host is up |

---

### 2. Port Scanning: Who Is Listening
- After finding live hosts, scan for **open ports**

| Command | Description |
|---------|-------------|
| `nmap 10.10.10.1` | Default scan (top 1000 ports) |
| `nmap -p 80 10.10.10.1` | Scan specific port |
| `nmap -p 1-1000 10.10.10.1` | Scan port range |
| `nmap -p- 10.10.10.1` | Scan ALL 65535 ports |
| `nmap -sS 10.10.10.1` | SYN scan (stealth scan) — requires sudo |
| `nmap -sT 10.10.10.1` | TCP connect scan |
| `nmap -sU 10.10.10.1` | UDP scan |

**Port States:**
| State | Meaning |
|-------|---------|
| Open | Port is accepting connections |
| Closed | Port is accessible but no service running |
| Filtered | Firewall is blocking the port |

---

### 3. Version Detection: Extract More Information
- Finds out **what service and version** is running on open ports

| Command | Description |
|---------|-------------|
| `nmap -sV 10.10.10.1` | Service/version detection |
| `nmap -O 10.10.10.1` | OS detection |
| `nmap -A 10.10.10.1` | Aggressive scan (OS + version + scripts + traceroute) |

---

### 4. Timing: How Fast is Fast
- Controls **speed vs stealth** of the scan

| Flag | Name | Description |
|------|------|-------------|
| `-T0` | Paranoid | Extremely slow — IDS evasion |
| `-T1` | Sneaky | Very slow — IDS evasion |
| `-T2` | Polite | Slow — less bandwidth |
| `-T3` | Normal | Default speed |
| `-T4` | Aggressive | Fast — good for reliable networks |
| `-T5` | Insane | Very fast — may miss results |

> 💡 `-T4` and `--T4 Aggressive` are equivalent — same thing!

---

### 5. Output: Controlling What You See
- Control how results are **displayed and saved**

| Command | Description |
|---------|-------------|
| `nmap -v 10.10.10.1` | Verbose — more details |
| `nmap -vv 10.10.10.1` | Very verbose |
| `nmap -oN output.txt 10.10.10.1` | Save as normal text |
| `nmap -oX output.xml 10.10.10.1` | Save as XML |
| `nmap -oG output.gnmap 10.10.10.1` | Save as grepable format |
| `nmap -oA output 10.10.10.1` | Save in all formats |

---

## 🛠️ Cheat Sheet

### Common Nmap Commands
```bash
# Basic scan
nmap 10.10.10.1

# Scan all ports
nmap -p- 10.10.10.1

# Service version detection
nmap -sV 10.10.10.1

# OS detection
nmap -O 10.10.10.1

# Aggressive scan
nmap -A 10.10.10.1

# Stealth SYN scan
sudo nmap -sS 10.10.10.1

# Fast scan with version
sudo nmap -sS -sV -T4 10.10.10.1

# Skip ping, scan all ports
nmap -Pn -p- 10.10.10.1

# Scan entire subnet
nmap -sn 10.10.10.0/24

# Save output
nmap -oN results.txt 10.10.10.1
```

### Timing Templates
```
-T0 = Paranoid
-T1 = Sneaky
-T2 = Polite
-T3 = Normal (default)
-T4 = Aggressive
-T5 = Insane
```

### Most Used Flags
```
-sS  = SYN/Stealth scan
-sT  = TCP connect scan
-sU  = UDP scan
-sV  = Version detection
-sn  = Ping scan only
-O   = OS detection
-A   = Aggressive (all)
-Pn  = Skip ping
-p-  = All ports
-T4  = Fast timing
-v   = Verbose
-oN  = Output to file
```

---

## 💡 Key Takeaways

- **Nmap** = most essential recon tool in pentesting
- **Host Discovery** (`-sn`) = find live hosts first before port scanning
- **SYN scan** (`-sS`) = stealthier than TCP connect scan — needs sudo
- **-A flag** = all-in-one but noisy — use carefully in real engagements
- **Timing** = balance between speed and stealth — `-T4` for CTFs, `-T1/-T2` for real stealth
- **-Pn** = use when target blocks ICMP/ping — assumes host is up
- **Always save output** (`-oN`) = para hindi mo na ulit i-scan yung same target
- **Version detection** (`-sV`) = important para malaman kung may vulnerable na version ng service

---

## 🔍 Pentesting Workflow with Nmap

```
1. Host Discovery
   nmap -sn 10.10.10.0/24

2. Port Scan
   nmap -p- 10.10.10.1

3. Version + OS Detection
   sudo nmap -sS -sV -O 10.10.10.1

4. Aggressive Scan
   sudo nmap -A -T4 10.10.10.1

5. Save Results
   nmap -oN results.txt 10.10.10.1
```

---

*Notes by: sean.orzales13*
*Platform: TryHackMe*
