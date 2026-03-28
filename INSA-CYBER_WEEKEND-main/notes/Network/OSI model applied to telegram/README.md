##OSI MODEL applied on Telegram

📡 OSI Model Explained Using Telegram (Full Cybersecurity View)

This project explains the OSI (Open Systems Interconnection) model using a real-world example: sending a message on Telegram, plus how each layer can be viewed from a cybersecurity perspective.
📱 Example Scenario
You send:
“Meet me at 5 PM”
to your friend on Telegram.

Now let’s trace it through all 7 OSI layers 👇

7. Application Layer

-What it does:
Where user interacts with the app
Provides services like messaging, calls, file sharing

-Example:
You open Telegram and send:
“Meet me at 5 PM”
-Cyber View:
Attacker sees only app traffic (Telegram)
Cannot directly see message content

6. Presentation Layer

-What it does:
Encrypts/decrypts data
Compresses media
Converts data format

-Example:
Message becomes:
encrypted data like X9k@2!encrypted
-Cyber View:
Encryption blocks packet sniffers
Without keys → data is useless

5. Session Layer

-What it does:
Maintains login session
Keeps connection between devices
Controls start/end of communication

-Example:
You stay logged into Telegram on:
Phone 📱
Laptop 💻

-Cyber View:
Session hijacking risk exists if token stolen

4. Transport Layer

-What it does:
Splits message into packets
Ensures delivery and order
Handles retransmission if lost

-Example:
Message split:
Packet 1: “Meet me”
Packet 2: “at 5 PM”

-Cyber View:
DoS attacks can target this layer (flooding packets)

3. Network Layer

-What it does:
Routes packets using IP addresses
Finds best path across internet

-Example:
Route:
Ethiopia → ISP → Telegram server → Friend

-Cyber View:
IP tracking is possible
MITM attacks can target routing

2. Data Link Layer

-What it does:
Local delivery over Wi-Fi or mobile data
Uses MAC addresses
Handles frame transmission

-Example:
Phone sends data to:
Wi-Fi router 📡
Mobile tower 📶

-Cyber View:
ARP spoofing attacks happen here

1. Physical Layer

-What it does:
Sends raw bits as signals
Uses cables, fiber optics, radio waves

-Example:
Message becomes:
electrical signals + radio waves

-Cyber View:
Physical tapping possible (rare but real)
🔁 FULL FLOW (Simple Diagram)
Copy code

User Message
    ↓
Application Layer (Telegram UI)
    ↓
Presentation Layer (Encryption)
    ↓
Session Layer (Login/Connection)
    ↓
Transport Layer (Packet Split)
    ↓
Network Layer (IP Routing)
    ↓
Data Link Layer (Wi-Fi/Mobile)
    ↓
Physical Layer (Signals)
    ↓
Friend receives message
🔐 CYBERSECURITY SUMMARY
  Layer                                  Risk
Application                         App misuse, phishing
Presentation                        Weak encryption (if any)
Session                             Session hijacking
Transport                           DoS attacks
Network                             IP tracking, MITM
Data Link                           ARP spoofing
Physical                            Physical interception
