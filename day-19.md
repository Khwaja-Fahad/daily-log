# Day 19 - 2026-10-28

## Data Representation (TryHackMe)
Room completed: 100% (all 4 tasks)

## How it felt
This room was easy for me because I have already studied number systems
and conversions many times, and I am comfortable with maths. No
confusion. The new part was seeing where these ideas show up in security.

## What I learned

### Why computers use binary
Computers work with electrical signals that are either on or off, so
all data is stored as **binary**: only 0 and 1. Text, images, music
and programs are all long strings of bits underneath.
- 1 bit = one 0 or 1
- 1 byte = 8 bits (values 0 to 255)

### Representing Colors
Screens mix **red, green and blue (RGB)**. Each colour channel is one
byte, from 0 (none) to 255 (full).
- Example: (255, 0, 0) is pure red, (0, 0, 0) is black,
  (255, 255, 255) is white.
- Colours are often written in **hex** as `#RRGGBB`, two hex digits
  per channel. Example: `#FF0000` is red.
- One byte can be written as exactly two hex digits, which is why hex
  is so common.

### Numbers: From Decimal to Hexadecimal
| System | Base | Digits used |
|--------|------|-------------|
| Decimal | 10 | 0-9 |
| Binary | 2 | 0-1 |
| Hexadecimal | 16 | 0-9 and A-F |

- Hex A to F means 10 to 15.
- Binary to hex: group the bits in **fours** (a nibble), and each group
  becomes one hex digit. Example: `1111 1111` = `FF` = 255.
- Hex is a shorter, easier way for humans to read binary.

## Connection to earlier days
- Day 11: a **MAC address** is written in hex (for example
  `AA:BB:CC:DD:EE:FF`). Each pair is one byte.
- Day 12: an **IPv4 address** is four bytes (four numbers from 0 to
  255). A **subnet mask** like `255.255.255.0` is really 24 ones
  followed by 8 zeros in binary, which is why it is written `/24`.
- Day 6: `exiftool` and file analysis work on raw bytes.
- Day 16: **hashes** are usually shown as hex strings.
- Day 5: the `file` command identifies files by looking at their first
  bytes, not their name.

## Why this matters for security
- Analysts read **hex** in packet captures (Wireshark), memory dumps
  and malware analysis, so being fluent in it is a real advantage.
- Subnetting and firewall rules are much easier if I can convert
  between decimal and binary quickly.
- **Encoding is not encryption.** Writing something in binary, hex or
  base64 only changes how it looks and anyone can reverse it. Encryption
  needs a key.
- Special byte values and encodings are used in attacks and in hiding
  data, so defenders need to recognise them.

## Time and completion
- Time spent: 45 minutes
- Room completed: 100%
