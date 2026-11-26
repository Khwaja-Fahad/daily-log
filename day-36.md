# Day 36 - 2026-11-26

## Packets & Frames (TryHackMe)
Room completed: 100% (all 5 tasks)

## The idea
Data is not sent as one big piece. It is split into many small pieces, sent across the network and put back together by the receiver. Small pieces are efficient, because a single huge message cannot block the whole network. Example: a picture on a web page arrives as many packets and is rebuilt on my computer.

## What I learned

### Packets and frames
| | Packet | Frame |
|---|---|---|
| OSI layer | Layer 3 (Network) | Layer 2 (Data Link) |
| Holds | IP header and the data (payload) | The packet, plus extra information such as MAC addresses |
| Addressing | IP addresses | MAC addresses |
- Analogy: the **envelope is the frame** and the **letter inside is the packet**. The envelope carries the letter to the next place, and once it is opened, the receiver knows how to forward the letter.
- Wrapping data in headers as it goes down the layers is **encapsulation**. Removing them on the receiving side is **decapsulation**.
- If a piece of data has IP addressing information, I am talking about a packet. If the encapsulating layer is stripped away, I am talking about the contents.

### Important IP packet headers
| Header | What it does |
|--------|--------------|
| **TTL** (Time To Live) | An expiry counter, so a packet that never arrives does not circle the network forever |
| **Checksum** | A calculated value used to check that the data was not changed. If it differs on arrival, the data is corrupt |
| **Source address** | The IP address of the sender |
| **Destination address** | The IP address of the receiver |
- Note: this **TTL** counts how many hops a packet may travel and is reduced by each router. The DNS **TTL** is a different thing: how long an answer may be cached.

### TCP (Transmission Control Protocol) in detail
- **TCP/IP model:** four layers: Application, Transport, Internet and Network Interface. It is a shorter version of the OSI model.
- TCP is **connection-based**: a connection is set up before any data is sent. It guarantees that data arrives complete and in order, but it is slower and needs a reliable connection.
- **TCP header fields:**
  | Field | Meaning |
  |-------|---------|
  | Source port | Port the sender opens, chosen randomly from those not in use |
  | Destination port | Port of the service on the receiver (for example a web server), not random |
  | Source / destination IP | Sender and receiver addresses |
  | Sequence number | Numbers data so it can be rebuilt in the right order |
  | Acknowledgement number | Tells the sender which data arrived |
  | Checksum | Gives TCP its integrity check |
  | Data | The actual content |
  | Flag | Tells the devices how to treat the packet |

### The three-way handshake
| Step | Message | Meaning |
|------|---------|---------|
| 1 | **SYN** | Client: "I want to connect, here is my starting number" |
| 2 | **SYN/ACK** | Server: "Agreed, here is mine, and I received yours" |
| 3 | **ACK** | Client: "Received, let's start" |
| 4 | **DATA** | The actual data is sent |
- **Closing:** one side sends **FIN**, the other acknowledges it and sends its own FIN, and the first side acknowledges that. This ends the connection cleanly and frees resources.
- **RST** (reset): ends everything abruptly. It is a last resort when something goes wrong, for example a service is not working or a port is closed.
- **Sequence numbers:** each side picks a starting number (the Initial Sequence Number, ISN), and the numbers count up so data can be put in order. The room's example uses small numbers and adds 1 each time to keep it simple. In real TCP, the starting number is random and the count goes up by the number of bytes sent.
- **Practical:** I put the handshake messages in the correct order in a simulation.

### UDP (User Datagram Protocol)
- **Stateless:** no connection set up, no handshake, no acknowledgements and no guarantee of arrival.
- Much faster and simpler, with fewer headers. The application decides how to handle speed and lost data.
- Good for video calls, streaming and voice chat, where a few lost pieces are acceptable. TCP is for file transfers, email and web pages.
- UDP headers: TTL, source and destination address, source and destination port, and data.

### Ports
- A **port** is a number from **0 to 65535** that identifies which application or service on a device receives the data. Analogy: a harbour, where each ship needs a port that fits it.
- The IP address finds the **device**, and the port finds the **service** on it.
- Ports in the low range (up to 1023, which the room rounds to 1024) are the common, standard ones. Applications follow the standard so that, for example, every browser knows web data uses port 80.
- **Common ports:**
  | Service | Port | Job |
  |---------|------|-----|
  | **FTP** (File Transfer Protocol) | 21 | File sharing from a central server |
  | **SSH** (Secure Shell) | 22 | Secure text-based remote login |
  | **HTTP** | 80 | Web pages |
  | **HTTPS** | 443 | Encrypted web pages |
  | **SMB** (Server Message Block) | 445 | Sharing files and printers |
  | **RDP** (Remote Desktop Protocol) | 3389 | Remote login with a visual desktop |
- Services can run on **non-standard ports** (for example a web server on 8080). Then the port has to be written after a colon, for example `address:8080`.
- **Practical:** I connected to a given address and port in a simulation and saw that a port is where a connection actually happens.

### Added by me (not in the room)
| Service | Port |
|---------|------|
| Telnet | 23 |
| SMTP (email sending) | 25 |
| DNS | 53 |
- A short way to remember: 21 FTP, 22 SSH, 23 Telnet, 25 SMTP, 53 DNS, 80 HTTP, 443 HTTPS, 445 SMB, 3389 RDP.

## Connection to what I already know
- **OSI model:** packets sit at the Network layer, frames at the Data Link layer, and TCP and UDP at the Transport layer.
- **IP and MAC addresses:** the packet uses IP and the frame uses MAC.
- **ARP and DHCP:** these local network protocols are small messages that suit UDP.
- **HTTP, HTTPS and DNS:** web traffic runs on top of TCP with ports 80 and 443, and DNS uses port 53.
- **SSH vs Telnet:** SSH on port 22 is the secure remote login, while Telnet sends everything readable.
- **Ping and traceroute:** the TTL field is what makes traceroute work.
- **Linux and Windows commands:** tools like `ss`, `netstat` and `nmap` show or scan ports.

## Why this matters for security
- **Open ports are the doors of a system.** Every listening service is a possible entry point, so defenders keep only the needed ports open and close the rest.
- **Port scanning** is how attackers (and defenders) find open services. Many connection attempts to different ports from one address is a classic sign of scanning.
- **The handshake can be abused:** a **SYN flood** sends huge numbers of SYN packets without finishing the handshake, filling the server's resources (a denial of service attack).
- **RST packets** in logs can mean closed ports or interference, so analysts notice them.
- **Firewall rules** are written in terms of IP addresses, ports and protocol (TCP or UDP), so I need to understand them to read and write rules.
- **Standard ports hint at the service:** unusual traffic on a port (for example SSH on a strange port, or an unexpected connection to port 3389 or 445) is worth investigating. Attackers also hide services on non-standard ports, so the port number alone is not proof.
- **Unencrypted protocols** (FTP, Telnet, plain HTTP) send data readable, so their secure versions (SFTP, SSH, HTTPS) are preferred.
- **Packet analysers** such as Wireshark let an analyst look at headers, flags and ports in real traffic.
- I only scan or connect to systems I own, lab machines, or systems I am authorised to test.

## Full forms
- **TCP:** Transmission Control Protocol
- **UDP:** User Datagram Protocol
- **IP:** Internet Protocol
- **MAC:** Media Access Control
- **TTL:** Time To Live
- **SYN / ACK / FIN / RST:** synchronise / acknowledge / finish / reset
- **ISN:** Initial Sequence Number
- **FTP:** File Transfer Protocol
- **SSH:** Secure Shell
- **HTTP / HTTPS:** HyperText Transfer Protocol / Secure
- **SMB:** Server Message Block
- **RDP:** Remote Desktop Protocol
- **DNS:** Domain Name System
- **SMTP:** Simple Mail Transfer Protocol
- **DoS:** Denial of Service

## Practice (from memory, out loud)
1. Explain a packet vs a frame with the envelope and letter.
2. Say the three steps of the handshake, then how a connection is closed.
3. Explain TCP vs UDP and give two uses for each.
4. Say the standard ports for SSH, HTTP, HTTPS, SMB and RDP.
5. Explain why many connection attempts to different ports from one address is suspicious.
6. Say the difference between the TTL in a packet and the TTL in DNS.

## Time and completion
- Time spent: 30 minutes
- Room completed: 100%
