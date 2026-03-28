🌐 File Transfer

PORT 20 (FTP Data)
Used for actual file transfer
Works with port 21 (control)
- Not secure (data sent in plaintext)

PORT 21 (FTP Control)
Sends commands (login, list files)
Uses username/password
- Easily sniffed → attackers capture credentials
🔐 Remote Access

PORT 22 (SSH)
Secure remote login (encrypted)
Used by admins to control servers
🔥 Attack: brute-force login attempts

PORT23 (Telnet)
Old remote login method
- No encryption
- Completely insecure (avoid in real systems)

📧 Email Services
PORT 25 (SMTP)
Sends emails between servers
Used in mail delivery
⚠️ Spam & spoofing attacks common

PORT 110 (POP3)
Downloads emails to your device
Deletes from server (by default)
Used in basic email clients

PORT 143 (IMAP)
Syncs emails with server
Allows access from multiple devices
More modern than POP3

PORT 465 (SMTPS)
Secure SMTP (encrypted)
Older but still used
587 (SMTP Secure Submission)
Modern secure email sending
Preferred over port 25

🌍 Networking Core
PORT 53 (DNS)
Converts domain → IP (e.g., google.com → IP)
Uses UDP (fast) & TCP (reliable)
🔥 Attack: DNS spoofing / poisoning
PORT 67 (DHCP Server)
Assigns IP addresses automatically
PORT 68 (DHCP Client)
Receives IP from DHCP server
📁 Simple Transfer
PORT 69 (TFTP)
Lightweight file transfer (no authentication)
Used in routers/booting systems
⚠️ Highly insecure
🌐 Web Traffic

PORT 80 (HTTP)
Loads websites (non-secure)
Data visible to attackers

PORT 443 (HTTPS)
Secure web traffic (SSL/TLS encryption)
🔒 Used everywhere today
📰 Communication & Time

PORT 119 (NNTP)
Used for Usenet discussions
Rare today

PORT 123 (NTP)
Syncs system time
⚠️ Can be used in DDoS attacks
🖥️ Windows Networking (NetBIOS)

PORT 137 (NetBIOS Name Service)
Resolves computer names

PORT 138 (NetBIOS Datagram)
Sends network messages

PORT 139 (NetBIOS Session)
File sharing & communication
⚠️ Vulnerable in old systems
🧠 Directory & Management

PORT 161 (SNMP)
Monitors network devices
Used by admins

PORT 162 (SNMP Trap)
Sends alerts from devices

PORT 179 (BGP)
Controls routing between ISPs
🔥 Critical internet backbone protocol

PORT 389 (LDAP)
Directory services (user authentication)
Used in Active Directory
📂 File Sharing

PORT 445 (SMB)
Windows file sharing
Used in networks for shared folders
🔥 Attack: ransomware (e.g., WannaCry)
🔐 VPN & Security

PORT 500 (ISAKMP / IKE)
Used to establish VPN tunnels
Helps secure communication
📜 Logging & Services

PORT 514 (Syslog)
Sends logs to server
Used in monitoring systems

PORT 515 (LPD)
Printer service (old)
Sends print jobs
🌍 Routing

PORT 520 (RIP)
Routing protocol (old)
Shares network paths
🗄️ Database

PORT 3306 (MySQL)
Database communication
Used by web apps
⚠️ If exposed → data breach risk
