# Day 24 - 2026-11-05

## Cisco Networking Basics, Module 3: Wireless and Mobile Networks
Sections: 3.0 Introduction, 3.1 Wireless Networks, 3.2 Mobile Device
Connectivity, 3.3 Summary
Module completed: 100%

## What I learned

### 3.1 Wireless Networks
- A **WLAN** (Wireless Local Area Network) is a LAN where devices
  connect with radio signals instead of cables. It follows the
  **IEEE 802.11** standards (IEEE = Institute of Electrical and
  Electronics Engineers). **Wi-Fi** is the brand name for these.
- **Access point (AP):** the device that connects wireless devices to
  the wired network (Day 8). A home **wireless router** combines a
  router, a switch and an access point in one box.
- **SSID** (Service Set Identifier): the name of the Wi-Fi network I
  see in the list.
- **Frequency bands:**
  | Band | Range | Speed | Notes |
  |------|-------|-------|-------|
  | 2.4 GHz | Longer, passes walls better | Slower | More interference (microwaves, Bluetooth) |
  | 5 GHz | Shorter | Faster | Less crowded |
  GHz = gigahertz. Newer standards also use 6 GHz.
- **Channels:** each band is split into channels. Neighbouring networks
  on the same channel interfere, so changing the channel can help.
- Wireless is shared. Everyone in range can receive the signal, unlike
  a cable that goes to one device.
- **Wireless security:**
  - **WEP** (Wired Equivalent Privacy): old and broken, never use it
  - **WPA2** / **WPA3** (Wi-Fi Protected Access): the current choices,
    and WPA3 is the strongest
  - Use a strong passphrase, and change the default router password
  - **Open networks** (no password) leave traffic readable by others

### 3.2 Mobile Device Connectivity
- Phones and tablets connect in several ways:
  - **Wi-Fi:** uses a WLAN (local, usually free or cheaper)
  - **Cellular:** the mobile network (4G, 5G) through cell towers,
    works over a wide area
  - **Bluetooth:** short range (a few metres), for headphones, watches,
    keyboards. Devices must **pair** first.
  - **NFC** (Near Field Communication): very short range (a few
    centimetres), used for contactless payments
  - **Hotspot / tethering:** my phone shares its cellular connection
    with other devices
- Example: at home my phone uses Wi-Fi, on the street it switches to
  cellular, and my earbuds use Bluetooth.

### 3.3 Summary
Wireless and mobile technologies let devices connect without cables,
each with its own range, speed and security needs.

## Connection to earlier days
- Day 8: the access point and router are the devices that carry this
  traffic.
- Day 12: my phone gets its IP settings from **DHCP** when it joins Wi-Fi.
- Day 15: Wi-Fi works at **Layer 1** (Physical, radio signals) and
  **Layer 2** (Data Link, MAC addresses). IP is still Layer 3.
- Day 11: every wireless card has a **MAC address**.

## Why this matters for security
- Because wireless signals travel through the air, anyone nearby could
  try to listen, so encryption (WPA2 or WPA3) is essential.
- **Public Wi-Fi** is risky. Use **HTTPS** (Day 18) so the content stays
  hidden, and avoid sensitive logins on open networks. Plain HTTP and
  Telnet (Day 15) could be read in the air.
- **Evil twin:** an attacker creates a fake access point with the same
  SSID as a real one, so people connect to it by mistake.
- **Rogue access point:** an unauthorised AP plugged into a company
  network, creating a back door. Defenders scan for them.
- **MAC filtering** (allowing only certain MAC addresses) is weak,
  because MAC addresses can be faked (Day 11).
- Bluetooth and NFC can also be attacked, so turn them off when not
  needed and keep devices updated.
- Only test wireless networks I own or have written permission to test.

## Full forms from today
- **WLAN:** Wireless Local Area Network
- **IEEE:** Institute of Electrical and Electronics Engineers
- **AP:** Access Point
- **SSID:** Service Set Identifier
- **GHz:** Gigahertz
- **WEP:** Wired Equivalent Privacy
- **WPA:** Wi-Fi Protected Access
- **NFC:** Near Field Communication

## Time and completion
- Time spent: 1 hour
