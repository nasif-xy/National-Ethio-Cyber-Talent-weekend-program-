##ARD AND IRDP

🌐 ARP vs IRDP (Networking Basics)
🔹 ARP (Address Resolution Protocol)
Purpose: Resolve IP address → MAC address
How it works:
Device checks ARP cache
If not found → sends broadcast request
Target replies with its MAC address
Entry is stored in ARP table
Example:
Bash
Copy code
IP: 192.168.1.10 → MAC: AA:BB:CC:DD:EE:FF
Key Points:
Works in IPv4 networks
Uses broadcast communication
Operates within a LAN
Essential for device-to-device communication
🔹 IRDP (ICMP Router Discovery Protocol)
Purpose: Discover default gateway (router) automatically
How it works:
Router sends advertisement (ICMP)
OR host sends solicitation
Router responds with its IP
Example:
Bash
Copy code
Default Gateway: 192.168.1.1
Key Points:
Based on ICMP messages
Helps find routers dynamically
Mostly replaced by DHCP today

⚡ Key Differences
-Function
ARP-IP → MAC mapping
IRDP-Find default gateway
-Protocol
ARP-ARP
IRDP-ICMP
-Scope
ARP-Local network
IRDP-Network routing
-Usage
ARP-Widely used
IRDP-Rare (DHCP preferred)
-Quick Analogy
ARP → "What's your MAC address?"
IRDP → "Who is the router?"
