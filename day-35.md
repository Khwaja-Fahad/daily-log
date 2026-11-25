# Day 35 - 2026-11-25

## OSI Model (TryHackMe)
Room completed: 100% (all 8 tasks)

## The idea
The **OSI model** (Open Systems Interconnection) is a framework that describes how data is sent, received and understood on a network. It has **seven layers**, each with its own job. Because every device follows the same model, devices with different designs can still communicate.

As data moves down the layers to be sent, each layer adds its own information to it. This is called **encapsulation**. The receiving device removes the added information layer by layer in reverse.

## The seven layers

| Layer | Name | Main job | Examples |
|-------|------|----------|----------|
| 7 | Application | Rules for how the user interacts with data | Browsers, email clients, DNS, FileZilla |
| 6 | Presentation | Translating and standardising data, encryption | Data formats, HTTPS encryption |
| 5 | Session | Creating, maintaining and closing connections | Sessions and checkpoints |
| 4 | Transport | Delivering data between devices | TCP, UDP |
| 3 | Network | Routing data using IP addresses | Routers, OSPF, RIP |
| 2 | Data Link | Physical addressing on the local network | MAC addresses, NIC, switches |
| 1 | Physical | Sending the actual signals | Ethernet cables, electrical signals |

Memory tricks:
- Top to bottom (7 to 1): **All People Seem To Need Data Processing**
- Bottom to top (1 to 7): **Please Do Not Throw Sausage Pizza Away**

## What I learned about each layer

### Layer 1: Physical
- The lowest layer: the physical hardware used for networking.
- Devices send data as electrical signals in **binary** (0s and 1s).
- Example: **Ethernet cables** connecting devices.

### Layer 2: Data Link
- Handles **physical addressing**. It takes a packet from the network layer and adds the **MAC** address of the receiving device.
- Every network-enabled computer has a **NIC** (Network Interface Card) with a unique **MAC address** (Media Access Control).
- A MAC address is set by the manufacturer, but it can be **spoofed** (faked).
- On a local network, the MAC address is what is actually used to deliver the data.
- Also prepares data in a form suitable for transmission.

### Layer 3: Network
- **Routing** and re-assembly of data. Routing chooses the best path for the data to travel.
- Everything here uses **IP addresses** (for example 192.168.1.100). Devices that work with IP addresses, like routers, are **Layer 3 devices**.
- Routing protocols: **OSPF** (Open Shortest Path First) and **RIP** (Routing Information Protocol).
- The path is chosen by: shortest (fewest devices), most reliable (fewer lost packets), and fastest physical link (fibre is faster than copper).
- The data does not always take the single best path.

### Layer 4: Transport
Two protocols, with different strengths:
| | **TCP** (Transmission Control Protocol) | **UDP** (User Datagram Protocol) |
|---|---|---|
| Reliability | Guarantees accurate, complete, ordered data | No guarantee, data is sent whether it arrives or not |
| Connection | Keeps a connection between the two devices | No continuous connection |
| Speed | Slower, because it does more work | Much faster |
| Error checking | Yes | No (the application can add its own) |
| Used for | Web browsing, email, file sharing and downloads | Video streaming, small quick messages, device discovery protocols |
- TCP is like a registered letter, and UDP is like a postcard.
- TCP breaks data into pieces (**packets**) and reassembles them in the correct order. If one piece is missing, the whole thing cannot be used.
- With UDP, if some packets are lost, part of the picture may be missing, but for a video call a few lost pixels do not matter.

### Layer 5: Session
- Creates and maintains the connection to the other computer. An active connection means an active **session**.
- Closes the connection if it is unused for a while or lost.
- Sessions can have **checkpoints**: if data is lost, only the newest data has to be resent, which saves bandwidth.
- Sessions are unique, and data cannot travel across different sessions.

### Layer 6: Presentation
- The layer where **standardisation** happens. It acts as a **translator** between the application layer and the network, so data looks the same even when the software differs (for example two different email programs).
- The room places **encryption** here (like HTTPS on a secure site).

### Layer 7: Application
- The layer I know best: the protocols and rules that decide how users interact with data.
- Everyday software with a **GUI** (graphical user interface): browsers, email clients and file transfer programs.
- Includes protocols like **DNS** (Domain Name System), which turns website names into IP addresses.

## Added by me: how the data is named at each stage (PDU)
| Layer | Data unit (PDU) |
|-------|-----------------|
| 7, 6, 5 | Data |
| 4 | Segment (TCP) or datagram (UDP) |
| 3 | Packet |
| 2 | Frame |
| 1 | Bits |
- **PDU** = Protocol Data Unit.

## Added by me: where common devices and tools fit
| Device or tool | Layer |
|----------------|-------|
| Cable, hub, Wi-Fi radio signal | 1 |
| Switch, NIC | 2 |
| Router | 3 |
| Firewall | Layers 3 and 4 (newer ones also check layer 7) |
| Wireshark (packet analyser) | Can show all layers |

## Why this matters for security

### Attacks by layer
| Layer | Example attack or weakness |
|-------|----------------------------|
| 1 | Physical access, cable tapping, unplugging or stealing equipment |
| 2 | **MAC spoofing**, ARP spoofing, rogue devices on the local network |
| 3 | **IP spoofing**, routing attacks, ping floods |
| 4 | Port scans, SYN floods (abusing the TCP handshake) |
| 5 | **Session hijacking** (taking over an active session, for example by stealing a cookie) |
| 6 | Weak or missing encryption, downgrade attacks |
| 7 | Phishing, SQL injection, cross-site scripting, malicious DNS use |

### Troubleshooting by layer
- Work from the bottom up: is the cable or Wi-Fi connected (layer 1), is there a MAC and local link (layer 2), can I ping the IP (layer 3), is the port open (layer 4), does the application respond (layer 7).
- Example: pinging an IP address works, but a website name does not, so the fault is at the application layer (DNS), not the network.

### For a SOC analyst
- When an alert arrives, asking "at which layer is this happening?" shows where to look and which tool or log to check.
- Defence in depth means protecting several layers, because an attacker only needs a weakness in one.
- Only test these ideas in labs or on networks I own or am authorised to test.

## Connection to what I already know
- **MAC and IP addresses, ARP, and switches vs routers:** layers 2 and 3.
- **TCP and UDP, ports and the three-way handshake:** layer 4.
- **DNS, HTTP and HTTPS, and encoding:** layers 7 and 6.
- **Encapsulation:** the same wrapping idea as the TCP/IP model.
- **Troubleshooting commands** (`ping`, `ipconfig`, `nslookup`, `tracert`) each test a different layer.
- **Wireless networks** operate at the first two layers.

## Full forms
- **OSI:** Open Systems Interconnection
- **NIC:** Network Interface Card
- **MAC:** Media Access Control
- **IP:** Internet Protocol
- **OSPF:** Open Shortest Path First
- **RIP:** Routing Information Protocol
- **TCP:** Transmission Control Protocol
- **UDP:** User Datagram Protocol
- **DNS:** Domain Name System
- **GUI:** Graphical User Interface
- **HTTPS:** HyperText Transfer Protocol Secure
- **ARP:** Address Resolution Protocol
- **PDU:** Protocol Data Unit
- **SYN:** Synchronize (the first step of the TCP handshake)

## Practice (from memory, out loud)
1. Say the seven layers from 7 down to 1, then from 1 up to 7.
2. Say one job and one example for each layer.
3. Explain TCP vs UDP with an everyday comparison.
4. Say which layer a switch, a router and a browser work at.
5. Pick any security alert idea (for example a port scan) and say which layer it belongs to.

## Time and completion
- Time spent: 30 minutes
- Room completed: 100%
