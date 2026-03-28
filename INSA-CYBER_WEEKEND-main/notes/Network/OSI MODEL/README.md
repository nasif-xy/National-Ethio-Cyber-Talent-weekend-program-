## 7Layers of the OSI Model (Top → Bottom)

The OSI Model (Open Systems Interconnection Model) is a conceptual framework used to understand how data travels across a network. It divides networking into 7 layers, each with a specific function.

7. Application Layer
Closest to the user
Provides network services to applications
PDU name : data
Examples: Web browsers, email apps
Protocols: HTTP, FTP, SMTP, DNS

6. Presentation Layer
Translates data formats
Handles encryption and compression
PDU name: data
Example: Converting data into readable format

5. Session Layer
Manages connections between devices
Starts, maintains, and ends sessions
PDU name: data
Example: Keeping you logged into a website

4. Transport Layer
Ensures reliable data delivery
Breaks data into segments
Handles error checking and flow control
PDU name: segment
Protocols: TCP (reliable), UDP (faster but less reliable)

3. Network Layer
Determines the best path for data
Uses IP addresses
Devices: Routers
PDU name : packet
Protocol: IP (Internet Protocol)

2. Data Link Layer
Transfers data between devices on the same network
Uses MAC addresses
Devices: Switches
PDU name : frame
Error detection at this level

1. Physical Layer
Sends raw bits (0s and 1s)
Deals with cables, signals, hardware
PDU name : bits
Examples: Ethernet cables, voltage si

