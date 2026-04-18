# Nmap Basics Guide

## 🔍 What is Nmap?

Nmap (Network Mapper) is an open-source tool used for network discovery, port scanning, and security auditing.

---

##  OSI Layers Used

* Layer 3: IP, ICMP
* Layer 4: TCP/UDP
* Layer 7: Service detection, scripting

---

##  Scan Types

* `-sT` → TCP Connect Scan
* `-sS` → SYN (Stealth Scan)
* `-sU` → UDP Scan
* `-sn` → Ping Scan
* `-sV` → Version Detection
* `-O` → OS Detection
* `-A` → Aggressive Scan

---

##  Timing (Speed vs Stealth)

* `-T0` → Paranoid (slowest)
* `-T3` → Default
* `-T5` → Insane (fastest)

---

##  Nmap Scripting Engine (NSE)

* Automates vulnerability scanning
* Example:
  nmap --script=vuln target.com

---

##  Common Flags

* `-p` → Specify ports
* `-p-` → All ports
* `-oN` → Normal output
* `-oX` → XML output
* `-oA` → All formats
* `--script` → Run scripts

---

##  Output States

* Open → Service is running
* Closed → No service
* Filtered → Blocked by firewall

---

## 🔐 Firewall Evasion Techniques

* Fragmentation: `-f`
* Decoys: `-D RND:10`
* Spoof IP: `-S`
* Slow scan: `-T1`
* Source port: `--source-port 53`
* Skip ping: `-Pn`

---

## Red Team Tips

* Use stealth scans (`-sS`)
* Reduce speed (`-T1`)
* Use decoys and fragmentation

---

## Blue Team Tips

* Monitor logs
* Detect abnormal scanning patterns
* Use IDS/IPS systems

---

##  Example Command

nmap -sS -sV -O -T4 target.com

---

