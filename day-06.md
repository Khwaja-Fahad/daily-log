# Day 6 - 2026-10-12

## Windows system (TryHackMe room)
I learned about the main parts of Windows and the tools used to manage it:
- **Task Manager:** shows running programs and processes and how much
  CPU and memory they use. Useful for spotting something suspicious
  running on a machine.
- **Control Panel:** where system settings are managed (users, programs,
  network and so on).

## Most interesting thing: Windows Security
I already knew Windows Security scans for viruses, but I didn't think it
was worth much. In the room there was a malicious file, and when I ran a
scan it actually found it and flagged it as a virus.

What I learned: built-in antivirus does a real job. It is not perfect,
and no single tool catches everything, but it is a solid first layer of
defence and should stay turned on.

## New commands and tools

1. **`nmap -sn IP_address`** discovers which hosts are live (online)
   without scanning their ports. `-sn` means "ping scan only".
   Example: `nmap -sn 10.10.10.0/24`

2. **`nslookup domain`** resolves a domain name to its IP address,
   like looking up a phone number from a name.
   Example: `nslookup example.com`

3. **`exiftool imagename.extension`** reads the metadata of a file,
   for example an image. Metadata is hidden information such as the
   date, the camera or phone used, and sometimes the GPS location.
   Example: `exiftool photo.jpg`

## Why these matter for security
- `nmap -sn` helps a defender see which devices are really on a network.
- `nslookup` helps check where a suspicious domain points.
- `exiftool` shows that a photo can leak private details like location,
  so it's worth thinking before sharing original images online.

