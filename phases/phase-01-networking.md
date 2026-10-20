# Phase 1: Networking Fundamentals

Welcome to your first week. Every attack, every defense, and every packet you will ever analyze lives on a network, so this is where it all starts. You will learn how devices find each other, how data moves between them, and how to watch it happen with real tools on your own machines.

## Day 1: What a network is
- **Learn:** A network is two or more devices that can talk to each other. A LAN connects devices in one place (your home), a WAN connects LANs across distance (the internet), a switch moves data between devices on the same network, and a router connects different networks together.
- **Do:** List every device on your home network right now (your laptop, phone, TV, smart devices) and draw a simple map on paper showing how they connect to your router.
- [ ] Done: My home network map shows my router and every device connected to it.

## Day 2: The OSI model and the TCP/IP model
- **Learn:** The OSI model splits networking into 7 layers (physical, data link, network, transport, session, presentation, application), while the TCP/IP model uses 4 layers that match how the internet really works. Each layer only talks to the layer above and below it, which is why a problem at one layer looks different from a problem at another.
- **Do:** Pick three things you do online today (send a message, load a website, stream a video) and write down which layer each one lives at, then check your answers against a TCP/IP layer reference.
- [ ] Done: I can name all 7 OSI layers and match three everyday activities to their TCP/IP layers.

## Day 3: IP addresses and subnetting basics
- **Learn:** An IP address is the unique label every device needs to send and receive data. IPv4 uses 32 bits (like 192.168.1.10) and is running out, while IPv6 uses 128 bits (like 2001:db8::1) and has room to spare. Subnetting splits one network into smaller ones by borrowing bits from the host part of the address.
- **Do:** Open a terminal and run `ip addr` (Linux) or `ipconfig` (Windows), then write down your IPv4 address, your subnet mask, and whether you have an IPv6 address too.
- [ ] Done: I recorded my own IPv4 address, subnet mask, and IPv6 status from a real command.

## Day 4: TCP vs UDP and the 20 most common ports
- **Learn:** TCP is reliable and connection based (it checks that every packet arrives, used by web browsing and email), while UDP is fast and connectionless (it just sends and hopes, used by video calls and gaming). Ports are the numbered doors on a device that decide which program gets the traffic.
- **Do:** Write the 20 most common ports on flashcards or paper, quiz yourself until you know them cold: 20/21 FTP, 22 SSH, 23 Telnet, 25 SMTP, 53 DNS, 67/68 DHCP, 69 TFTP, 80 HTTP, 110 POP3, 123 NTP, 143 IMAP, 161/162 SNMP, 389 LDAP, 443 HTTPS, 445 SMB, 587 SMTP (submission), 993 IMAPS, 995 POP3S, 3389 RDP, 8080 HTTP alt.
- [ ] Done: I can recite all 20 ports and their services from memory without looking.

## Day 5: DNS and DHCP
- **Learn:** DNS is the internet phone book: it turns names like example.com into IP addresses your computer can actually reach. DHCP is the automatic desk clerk: it hands your device an IP address, subnet mask, gateway, and DNS server when it joins a network, so you never configure them by hand.
- **Do:** Run `nslookup example.com` (Windows) or `dig example.com` (Linux) and note the IP address it returns, then run `ipconfig /all` (Windows) or check your DHCP lease with `nmcli` (Linux) to find the DHCP server that gave you your address.
- [ ] Done: I resolved a domain name to an IP and found which DHCP server gave me my address.

## Day 6: Wireshark basics
- **Learn:** Wireshark captures the actual packets moving across your network interface and lets you read them layer by layer, which makes abstract ideas like DNS queries suddenly visible and concrete. A filter like `dns` or `http` narrows the capture to only the traffic you care about.
- **Do:** Install Wireshark from https://www.wireshark.org, start a capture on your Wi-Fi or Ethernet interface, browse to a plain website like http://neverssl.com in your browser, then stop the capture and find one DNS query (filter: `dns`) and one HTTP request (filter: `http`) in the packet list.
- [ ] Done: My capture contains a visible DNS query and an HTTP request, and I can explain what each packet shows.

## Day 7: Nmap and week review
- **Learn:** Nmap is a network scanner: it sends probes to devices and reads the answers to tell you which hosts are alive, which ports are open, and which services are running. Scanning your own home network is the safest legal way to practice, because every device you find belongs to you.
- **Do:** Install nmap from https://nmap.org, find your network range (for example 192.168.1.0/24 from Day 3), run `nmap -sn 192.168.1.0/24` to list live hosts (replace with your real range), then pick one host and run `nmap -sV <host-IP>` to identify its open ports and services, and match each one to the devices on your Day 1 map.
- [ ] Done: I scanned my home network, identified my devices and their open ports, and can name one concept I learned each day this week.
