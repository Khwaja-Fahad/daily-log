# Day 11 - 2026-10-20

## What is Networking? (TryHackMe)
Room completed: 100%

## What I learned

### What is Networking?
A network is two or more devices connected so they can share data and
resources. Networks exist everywhere: at home, in schools, in offices.
Example: a group chat. Every phone is a device, and the network is what
carries the messages between them.

### What is the Internet?
The internet is a huge network made of many smaller networks connected
together (a "network of networks"). Routers connect these networks and
pass data between them, so my laptop can reach a server far away.
This links to Cisco Module 2, where the internet was the biggest WAN.

### Identifying Devices on a Network
Every device needs a way to be identified, so data reaches the right place.
- **IP address:** a logical address given to a device on a network.
  Example: a street address. It can change when I move to a different
  network. IPv4 looks like four numbers separated by dots (like
  `192.168.1.10`).
- **MAC address:** the unique hardware ID of the network card. Example:
  the serial number of the card. It is written in hexadecimal and is
  meant to stay with the device, unlike an IP address.
- Easy way to remember: **IP = where I am now, MAC = who I am (my card).**

### Ping (ICMP)
`ping` checks whether another device can be reached and how long the
round trip takes. It works by sending a small message (an ICMP echo
request) and waiting for a reply. The time is measured in milliseconds,
and lower is faster.
[example from the room ping 8.8.8.8]

## Connection to earlier days
- Day 10: `ipconfig /all` showed my IPv4 address (IP) and Physical Address
  (MAC), which is exactly what this room explained.
- Day 10: `ping` to my router uses ICMP, and I now know why it is useful.
- Day 8: switches and routers are the devices that carry this traffic.
- Day 6: `nmap -sn` finds live hosts, similar to ping but for many
  devices at once.

## Why this matters for security
- Defenders read logs full of IP and MAC addresses, so I need to know
  what each one means. (Day 2: my incident report included the
  attacker's IP address.)
- Ping is a quick way to check whether a device is alive, but
  attackers also use it to find targets, which is why it is only used
  on systems I own or have permission to test.
- A MAC address can be faked, so it is useful but not proof of identity.

## Time and completion
- Time spent: [1 hour]
- Room completed: 100%
- Next room offered: Intro to LAN
