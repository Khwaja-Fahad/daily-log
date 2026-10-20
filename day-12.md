# Day 12 - 2026-10-21

## Intro to LAN (TryHackMe)
Room completed: 100%

## What I learned

### LAN Topologies
A topology is the layout of how devices in a network are connected.
- **Star:** every device connects to one central device (a switch).
  The most common today. Easy to manage, and one broken cable only
  affects one device, but if the central device fails, everything fails.
- **Bus:** all devices share one main cable. Cheap, but one fault can
  break the whole network.
- **Ring:** devices connect in a circle, and data travels around it.
- Example: a star is like a bus station where every route passes through
  one hub.

### A Primer on Subnetting
Subnetting means dividing a big network into smaller networks (subnets).
- It keeps traffic organised and can improve security, because
  different groups (for example staff and guests) can be separated.
- The **subnet mask** (like `255.255.255.0`) shows which part of an IP
  address is the network and which part is the device. I saw this line
  in `ipconfig /all` on Day 10.
- Example: a big office building split into floors. The building is the
  network, and each floor is a subnet.

### ARP (Address Resolution Protocol)
ARP connects the two kinds of address I learned yesterday. A device
knows the IP address it wants to reach, but needs the MAC address to
deliver the data on the local network. ARP asks "who has this IP
address?" and the owner replies with its MAC address.
- Example: shouting "Is there an Alex here?" in a room, and Alex
  answers "Yes, it's me, I'm over here."
- Devices remember the answers in an **ARP table (cache)**.

### DHCP (Dynamic Host Configuration Protocol)
DHCP automatically gives devices their network settings (IP address,
subnet mask, gateway, DNS) when they join. Without it, I would have to
type these in by hand on every device.
- Example: a hotel reception giving every guest a room number when they
  arrive.
- On Day 10, `ipconfig /all` showed "DHCP Enabled" and the DHCP server,
  which is usually the router.
- The four steps are often remembered as **DORA**: Discover, Offer,
  Request, Acknowledge.

## Connection to earlier days
- Day 8: switches and routers carry LAN traffic, and the star topology
  uses a switch.
- Day 10: `ipconfig /all` showed the subnet mask, gateway, and DHCP info.
- Day 11: IP address vs MAC address. ARP is the link between them.

## Why this matters for security
- **ARP spoofing:** ARP has no built-in way to verify answers, so an
  attacker on the same network can send fake replies and redirect
  traffic through their own device. Defenders watch for this.
- **Rogue DHCP server:** a fake DHCP server could give devices wrong
  settings and send their traffic to the attacker.
- **Subnetting** limits how far an attacker can move if one device is
  compromised.
- I only test these ideas in lab environments or on my own network.

## Time and completion
- Time spent: 30 minutes
- Room completed: 100%
