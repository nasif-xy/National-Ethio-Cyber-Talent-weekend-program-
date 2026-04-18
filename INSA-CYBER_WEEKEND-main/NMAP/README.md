# Nmap Basics Guide (Detailed Notes for Future Reference)

---

## 🔍 What is Nmap?

Nmap (Network Mapper) is a powerful open-source tool used for:

* Network discovery (finding live hosts)
* Port scanning (checking open ports)
* Service enumeration (identifying running services)
* Security auditing (detecting weaknesses)

👉 In simple terms:
Nmap helps you understand **what is running on a target system and how it can be accessed**.

---

## 🌐 OSI Layers Used in Nmap

Nmap operates across multiple layers of the OSI model:

### Layer 3 (Network Layer)

* Protocols: IP, ICMP
* Used for host discovery (ping scan)
* Example: `-sn`

### Layer 4 (Transport Layer)

* Protocols: TCP, UDP
* Used for port scanning
* Example: SYN scan (`-sS`), TCP scan (`-sT`), UDP scan (`-sU`)

### Layer 7 (Application Layer)

* Service detection and scripting
* Example: `-sV`, `--script`

👉 Key Idea:
Lower layers = connectivity
Higher layers = service intelligence

---

## 🔎 Scan Types (Deep Understanding)

### 1. TCP Connect Scan (`-sT`)

* Completes full 3-way handshake
* Easy to detect (logged by system)
* Does NOT require root privileges

### 2. SYN Scan (`-sS`) (Stealth Scan)

* Sends SYN but does NOT complete handshake
* Faster and stealthier
* Requires root privileges

👉 If SYN/ACK is received → port is OPEN

### 3. UDP Scan (`-sU`)

* Used to scan UDP services (DNS, SNMP)
* Slow because UDP has no handshake
* Often shows "open|filtered"

### 4. Ping Scan (`-sn`)

* Checks if host is alive
* Does NOT scan ports

### 5. Version Detection (`-sV`)

* Identifies software and versions
* Example: Apache 2.4, OpenSSH 8.2

### 6. OS Detection (`-O`)

* Uses TCP/IP fingerprinting
* Compares responses with known OS signatures

### 7. Aggressive Scan (`-A`)

Includes:

* OS detection
* Version detection
* Script scanning
* Traceroute

---

## ⚡ Timing (Speed vs Stealth)

Nmap provides timing templates:

* `-T0` → Paranoid (very slow, maximum stealth)
* `-T1` → Sneaky (IDS evasion)
* `-T2` → Polite (low bandwidth usage)
* `-T3` → Normal (default)
* `-T4` → Aggressive (faster)
* `-T5` → Insane (very fast, very noisy)

👉 Important:

* Slower scans = harder to detect
* Faster scans = easier to detect but quicker results

---

## 🧠 Nmap Scripting Engine (NSE)

NSE allows automation of advanced scanning tasks.

### Categories:

* `auth` → authentication checks
* `vuln` → vulnerability detection
* `exploit` → exploitation scripts
* `discovery` → service discovery

### Example:

```
nmap --script=vuln target.com
```

👉 NSE can:

* Detect CVEs
* Identify misconfigurations
* Automate penetration testing tasks

---

## 🛠 Common Flags Explained

### Target Discovery

* `-sn` → Ping scan only

### Port Selection

* `-p 80` → scan specific port
* `-p 1-1000` → scan range
* `-p-` → scan all ports (1–65535)

### Scan Types

* `-sT` → TCP Connect
* `-sS` → SYN scan
* `-sU` → UDP scan

### Detection

* `-sV` → version detection
* `-O` → OS detection
* `-A` → aggressive scan

### Speed Control

* `-T0` to `-T5`

### Output Formats

* `-oN` → normal text
* `-oX` → XML
* `-oG` → grepable
* `-oA` → all formats

### Scripts

* `--script=default`
* `--script=vuln`

---

## 📊 Understanding Nmap Output

Example:

```
PORT   STATE    SERVICE VERSION
80/tcp open     http    Apache 2.4
22/tcp closed   ssh
53/udp open     domain
```

### Output Fields:

* PORT → port number
* STATE → open, closed, filtered
* SERVICE → service name
* VERSION → software version

### States Meaning:

* **Open** → service is actively running
* **Closed** → host reachable but no service
* **Filtered** → blocked by firewall or IDS

👉 Key Insight:
Filtered = something is hiding the port (firewall/security device)

---

## 🔐 Firewall Evasion Techniques (Important)

These techniques help reduce detection:

### 1. Packet Fragmentation

```
nmap -f target
```

* Breaks packets into smaller fragments
* Can bypass simple firewalls

### 2. Decoy Scanning

```
nmap -D RND:10 target
```

* Adds fake IP addresses
* Makes logs confusing

### 3. Source IP Spoofing

```
nmap -S fake_ip target
```

* Pretends scan comes from another IP

### 4. Slow Scanning

```
nmap -T1 target
```

* Reduces detection by IDS

### 5. Source Port Manipulation

```
nmap --source-port 53 target
```

* Uses trusted ports (like DNS)

### 6. Skip Host Discovery

```
nmap -Pn target
```

* Avoids ping detection

---

## ⚔️ Red Team Strategy

* Use stealth scans (`-sS`)
* Slow down scans (`-T1` or `-T2`)
* Use decoys and fragmentation
* Avoid scanning all ports at once

👉 Goal: Stay undetected

---

## 🛡 Blue Team Strategy

* Monitor unusual traffic patterns
* Detect repeated SYN requests
* Use IDS/IPS systems
* Analyze logs for scanning behavior

👉 Goal: Detect and block attackers

---

## 🚀 Example Commands

### Basic Scan

```
nmap target.com
```

### Stealth Scan with Version Detection

```
nmap -sS -sV target.com
```

### Full Advanced Scan

```
nmap -sS -sV -O -A -T4 target.com
```

---

##  Final Notes

* Nmap is one of the most important tools in cybersecurity
* Mastering it is essential for both Red Team and Blue Team roles
* Always practice in legal environments (labs, CTFs, or your own systems)

---

