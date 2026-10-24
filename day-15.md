# Day 15 - 2026-10-24

## Networking Concepts (TryHackMe)
Room completed: 100% (all 8 tasks)

## What I learned

### The OSI Model
The OSI model splits network communication into 7 layers. Each layer has
one job and talks to the layers next to it.

| Layer | Name | Job (simple version) |
|-------|------|----------------------|
| 7 | Application | The apps I use (web, email) |
| 6 | Presentation | Formatting, encryption, compression |
| 5 | Session | Starting and keeping a conversation open |
| 4 | Transport | Delivering data reliably (TCP) or quickly (UDP) |
| 3 | Network | IP addresses and routing between networks |
| 2 | Data Link | MAC addresses, delivery inside one local network |
| 1 | Physical | Cables, Wi-Fi signals, the actual bits |

Memory trick (top to bottom): **All People Seem To Need Data Processing.**
Why layers help: when something breaks, I can ask "which layer is the
problem?" and troubleshoot step by step.

### The TCP/IP Model
A simpler, 4-layer model that the real internet is based on:
Application, Transport, Internet, Network Access.
It covers the same ground as OSI with fewer layers. OSI is mostly used
for learning and talking about problems, TCP/IP is what is actually used.

### IP Addresses and Subnets
- An IP address identifies a device on a network (Day 11).
- A subnet splits a big network into smaller ones, and the subnet mask
  shows which part of the address is the network and which is the
  device (Day 12).
- Example: a street (network) and house numbers (devices).

### UDP and TCP
Both are Transport layer protocols, and they work differently.
- **TCP:** reliable. It sets up a connection first (the three-way
  handshake: SYN, SYN-ACK, ACK), checks that data arrived, and resends
  anything lost. Used for web pages, email, file downloads.
- **UDP:** fast but no guarantees. It just sends the data with no
  handshake and no checking. Used for video calls, streaming, games.
- Example: TCP is a registered letter with a signature. UDP is a
  postcard, quick, but you don't know if it arrived.

### Encapsulation
As data goes down the layers to be sent, each layer wraps it with its
own header (extra information, like addresses). The receiving device
unwraps it layer by layer in reverse.
- Example: putting a letter in an envelope, then putting that envelope
  into a bigger package. The receiver opens the package, then the
  envelope.
- Data moves down the layers when sending (encapsulation) and up the
  layers when receiving (de-encapsulation).

### Telnet
Telnet is an old protocol that lets me control another computer through
a text terminal over a network. It sends everything, including
passwords, in **plain text**, so anyone watching the traffic can read
it. It has been replaced by **SSH**, which is encrypted.

## Connection to earlier days
- Day 8: switches and routers sit at the Data Link and Network layers.
- Day 11: IP address = Network layer, MAC address = Data Link layer.
- Day 12: ARP links the two layers, and DHCP hands out IP settings.
- Day 14: `ping` and `tracert` test the Network layer.

## Why this matters for security
- Defenders and attackers both think in layers. An attack or a
  firewall rule can happen at different layers, so knowing the layer
  tells me where to look.
- **Telnet** is a good example of insecure design: passwords sent in
  plain text can be stolen. Use SSH instead.
- TCP vs UDP matters when reading logs and scans. Tools like `nmap`
  check TCP and UDP ports differently.
- Encapsulation explains why one packet contains many headers, which
  analysts read in tools like Wireshark.
- I only use these tools on lab machines or networks I own.

## Time and completion
- Time spent: 1 hour
- Room completed: 100%
