📡 Wireshark CTF Writeup — Network Forensics Challenges

🛠 Tools Used

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

👉 Shows flag inside HTTP response body


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

FLAG_hidden_data.example.com

-Result

Extract hidden string from domain name.

-Key Learning

> DNS queries can be used for data exfiltration.

![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge2.png)



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

![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge3.png)


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

![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge4a.png)

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

### Follow HTTP Stream Output

![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fla-challenge5a.png)
### Follow HTTP Stream Output

![HTTP Stream](https://github.com/nasif-xy/National-Ethio-Cyber-Talent-weekend-program-/blob/main/INSA-CYBER_WEEKEND-main/Challenge/wireshark%20challenges/FL-challenge/fl-challenge5b.png)
