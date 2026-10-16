# Day 8 - 2026-10-16

## Cisco Networking Basics, Module 2: Network Components, Types, and Connections
Module completed: 100% (all 4 sections finished)

## What I learned

### Clients and Servers
- A **client** is a device that asks for something, such as my laptop
  or phone opening a website.
- A **server** is a computer that provides data or services, such as a
  web server sending a page.
- Example: a restaurant. I (the client) order, and the kitchen (the
  server) prepares and sends the food.
- In a **peer-to-peer** network, devices share files directly with each
  other, and each can act as both client and server.

### Network Components
- **End devices:** computers, phones, printers, anything that sends or
  receives data.
- **Intermediary devices:** devices that move data between end devices:
  - **Switch:** connects devices inside one local network
  - **Router:** connects different networks, such as my home network
    to the internet
  - **Wireless access point:** lets devices connect over Wi-Fi
  - **Firewall:** filters traffic and blocks what is not allowed
- **Media:** how the data travels: cables (copper, fibre) or wireless.

### Network types
- **LAN:** a small area, such as a home, school or office
- **WAN:** a large area, connecting LANs across cities or countries.
  The internet is the biggest WAN.

### ISP Connectivity Options
An ISP (Internet Service Provider) gives me access to the internet.
Common ways to connect:
- **Cable**
- **DSL** (through telephone lines)
- **Fibre optic** (the fastest, uses light)
- **Cellular** (mobile data)
- **Satellite** (useful in remote areas, slower)
- [Add any other option the module listed, such as dial-up]

## Why this matters for security
- The router and firewall are the front door of a network, so if they
  are set up badly, attackers can walk in.
- Knowing clients, servers and devices helps me understand what a SOC
  analyst sees in logs: which device talked to which server.
- When I use `nmap -sn`, I am looking for end devices on a network.
  This connects what I learned on Day 6 with today's topic.
