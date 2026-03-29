📡 Wireshark CTF Writeup — Network Forensics Challenges

 What is Wireshark?

Wireshark is a network protocol analyzer — a tool used to capture and inspect data traveling across a network in real time or from saved files.

1.  Capture network traffic

It records packets (small units of data) sent between devices.

Example:

your browser → website
your PC → router
your system → DNS server
2. Analyze packets

Each packet contains:

source IP
destination IP
protocol (HTTP, DNS, TCP, etc.)
actual data (payload)

Wireshark breaks all of this down for you.

3. Filter specific traffic

You can focus on exactly what you want:

http → web traffic
dns → domain queries
tcp → connections
icmp → ping packets

-This is critical in CTFs and real investigations.

4. Reconstruct conversations

Using features like:

Follow HTTP Stream
Follow TCP Stream

-It rebuilds full communication from many small packets.

5.  Detect problems & attacks

Wireshark helps identify:

slow networks
packet loss
suspicious traffic
hacking attempts

## tools Used

Wireshark

Base64 decoder (Linux terminal)

xxd (hex decoding tool)

-Overview

This challenges demonstrates how to analyze network traffic using Wireshark and extract hidden flags from different protocols.

Each challenge is solved by:

> Identifying the protocol → Filtering traffic → Inspecting payload → Extracting hidden data


🚩 Challenge 1 — HTTP (Unencrypted Traffic)

-Concept

HTTP traffic is not encrypted, meaning all requests and responses are visible in plain text.

- Approach

Filter:

http

Steps:

Identify GET/POST requests

Right-click packet

Select Follow → HTTP Stream

Inspect full request/response


-Result

Flag is directly visible inside:

URL parameters

POST body

Server response


-Key Learning

> HTTP exposes readable data because it has no encryption.

### Follow HTTP Stream Output

![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fl-challenge1.png)


🚩 Challenge 2 — DNS (Data in Domain Names)

-Concept

DNS is used to resolve domain names, but attackers can hide data inside subdomains.

-Approach

Filter:

dns

Steps:

Inspect DNS queries

Look at dns.qry.name

Identify suspicious subdomains


Example:

FLAG_dns_exfiltration_.example.com

-Result

Extract hidden string from domain name.

-Key Learning

> DNS queries can be used for data exfiltration.

![UDP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge2.png)



🚩 Challenge 3 — TCP Stream Reassembly

-Concept

TCP splits data into multiple packets but Wireshark can reconstruct full conversations.

-Approach

Filter:

tcp

Steps:

Identify suspicious packets

Right-click → Follow → TCP Stream

View full reconstructed message


-Result

Flag appears only after full stream reconstruction.

-Key Learning

> TCP stream grouping allows full message recovery from fragmented packets.

![TCP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge3.png)


🚩 Challenge 4 — SMTP + Base64 Encoding

-Concept

Email traffic (SMTP) often carries encoded content such as Base64.

-Approach

Filter:

tcp.stream eq 12

Steps:

Identify SMTP traffic

Open full stream

Locate encoded string


Example:

RkxBR3tzbXRwX2Jhc2U2NH0=

Decode:

echo "RkxBR3tzbXRwX2Jhc2U2NH0=" | base64 -d

-Result

FLAG{smtp_base64}

-Key Learning

> SMTP messages often hide data using Base64 encoding.

![SMTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge4a.png)

![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge4b.png)


🚩 Challenge 5 — ICMP Hidden Data (Ping Payload)

-Concept

ICMP (ping) packets can carry hidden data inside their payload section.

-Approach

Filter:

icmp

Steps:

Inspect ICMP echo requests/replies

View packet payload (data section)

Extract raw hex fragments


Observed data:

G(1c_icmp)FLAG
C_icmp FLAG

Reconstruction:

Combine fragmented payload parts

Extract raw hex values


Decode:

echo "<hex_data>" | xxd -r -p

Result

Flag successfully reconstructed from ICMP payload.

Key Learning

> ICMP can be used as a convert channel to transmit hidden data.


![ICMP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge5a.png)


![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fl-challenge5b.png)
