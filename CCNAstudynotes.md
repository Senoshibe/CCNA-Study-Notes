# 10/19/26 Neil Anderson Cisco CCNA 200-301 v 1.1 - The Complete Guide to Getting Certified Section 5: Mind Dump
#Revision of what I've learnt from video to see if I understand....
## TCP/UDP and the Transport Layer
TCP and UDP live in the transport layer. 
TCP is best effort, meaning there's flow control and sometimes checks for errors. 
Whereas UDP is for best effort. 

UDP is mainly for video and voice as they can't afford the overhead in the headers that are typically found in TCP. TCP is usually for every other service that relies on the data reaching from source to destination. 

Data sent via TCP is in sequence and any dropped packets are sent again, whereas with UDP, dropped packets are left dropped and an effort isn't made for the data to be sent in sequence. 

## Multiplex Sessions
Multiplex sessions are when a sender can have multiple sessions and send data via different protocols to different receivers at the same time. 

## 3 Way Handshake
When a sender and receiver establishes a connection, the handshake is in the followin sequence: SYN > SYN-ACK > ACK 
Whereby, the sender attempt to sync with the receiver, the receiver acknowledges the sync, and the sender finally acknowledges (?) the connection. 

## Source and Destination Ports and Protocols
For example when the sender sends data through a web server to receiver, the source to destination ports would be from port 80 HTTP to receiver's port e.g. port 2500, and back from 2500 to 80. 

Firewalls can determine whether the transfer of data is bi-direcitonal or not. For example, it can set a rule where it allows the sender to send data to the receiver on their respective ports, however, the receiver cannot send data to sender. Or it can allow the sending of data from receiver to sender, under the condition that the sender has sent data to receiver in the same session.

## Port Numbers and their Protocols
TCP: 
    FTP: port 21
    SSH: port 22
    Telnet: port 23
    HTTP: port 80
    HTTPS: 443 

UDP: 
    TFTP: port 69

TCP & UDP: 
    DNS: ?

## Review of Mind Dump:
## ✅ What I got right
* TCP and UDP are both Layer 4 (Transport Layer) protocols.
* TCP retransmits lost data and delivers it in order; UDP does neither.
* Voice/video typically use UDP.
* 3-way handshake order: SYN > SYN-ACK > ACK.
* Port numbers for FTP (21), SSH (22), Telnet (23), HTTP (80), HTTPS (443), TFTP (69, UDP).
* Good instinct on firewalls only allowing return traffic for sessions started from inside.

## ❌ Corrections
**1. TCP is NOT best effort. TCP = reliable, connection-oriented. UDP = best effort, connectionless.**

* TCP always does error recovery (ACKs + retransmission), not "sometimes".
* TCP features: connection setup (handshake), sequencing, acknowledgements, retransmission, flow control (windowing).
* UDP: no handshake, no ACKs, no sequencing, no flow control. Any reliability is left to the application.

**2. Why voice/video use UDP**

* The main reason is timing, not just header size. A retransmitted voice packet arrives too late to be useful, so it's better to drop it and keep going.
* Header size: TCP = 20 bytes minimum, UDP = 8 bytes.
* Other UDP users: DNS queries, DHCP, TFTP, SNMP, Syslog, NTP.

**3. Terminology**

* TCP unit of data = **segment**. UDP unit of data = **datagram**. ("Packet" is the Layer 3 term.)

**4. Multiplexing (better definition)**

* Port numbers let one host run many conversations/applications at the same time over a single IP address.
* Each session is uniquely identified by: source IP, source port, destination IP, destination port, protocol.
* IP address + port = a **socket**.

**5. 3-way handshake (filling in my "?")**

* SYN: client asks to open a connection and sends its starting sequence number.
* SYN-ACK: server acknowledges the client's SYN and sends its own sequence number.
* ACK: client acknowledges the server's SYN. Connection is now established. ✅
* Teardown uses FIN/ACK (FIN > ACK > FIN > ACK).

**6. Source/Destination ports. I had these backwards.**

* The **client** picks a random high **ephemeral (source) port**, and the **server** listens on the **well-known (destination) port**.
* Example: PC → web server = src 50000 → dst 80. Reply: web server → PC = src 80 → dst 50000.
* Port ranges: Well-known 0–1023 | Registered 1024–49151 | Dynamic/Ephemeral 49152–65535.

**7. Firewalls**

* What I described is a **stateful firewall**: it tracks sessions and automatically allows return traffic for connections started from inside.
* A basic ACL / packet filter is **stateless** and checks each packet on its own. (Covered properly in Section 32.)

**8. Ports: answering my "?" and adding missing exam ports**
| Protocol | Port | Transport |
|---|---|---|
| FTP | 20 (data), 21 (control) | TCP |
| SSH | 22 | TCP |
| Telnet | 23 | TCP |
| SMTP | 25 | TCP |
| DNS | 53 | **UDP** for normal queries, **TCP** for zone transfers/large replies |
| DHCP | 67 (server), 68 (client) | UDP |
| TFTP | 69 | UDP |
| HTTP | 80 | TCP |
| POP3 | 110 | TCP |
| NTP | 123 | UDP |
| SNMP | 161 (agent), 162 (traps) | UDP |
| HTTPS | 443 | TCP |
| Syslog | 514 | UDP |

## 📌 Weak areas → add to revisionareas.md
* TCP vs UDP: which one is "reliable" vs "best effort" (I mixed these up)
* Client vs server ports (ephemeral vs well-known)
* DNS / DHCP / SNMP / Syslog / NTP port numbers

# 10/19/26 Neil Anderson Cisco CCNA 200-301 v 1.1 - The Complete Guide to Getting Certified Section 6: Mind Dump
#Revision of what I've learnt from video to see if I understand....

## Binary
Calculated 179 in binary to be 010110011, moving on.

## IPv4 Addresses
Format is always 4 Octects. Octets because there are 8 bits in each octet. 
For example: 192.168.10.15 > 11000000.10101000.00001010.00001111

## Subnet Mask

With the example of the IP address: 192.168.10.15 with the subnet mask 255.255.255.0 i.e. 192.168.10.15/255.255.255.0

in binary, 255.255.255.0 can be represented as 11111111.11111111.11111111.00000000

The bits of the IPv4 address that correspond to the 1s of the subnet mask represent the first portion of the network address. And the rest you fill with zeros. In other words, 192.168.10.15 is a part of the subnet with network address 192.168.10.0 due to the subnet mask being 255.255.255.0.
If the subnet mask was 255.255.0.0, the network address would be 192.168.0.0

Same rule applies with the broadcast address, whereby instead the 2nd part of the broadcast address of the subnet is replaced with 255. i.e. 192.168.10.15 is a part of the subnet with broadcast address 192.168.10.255 due to the subnet mask being 255.255.255.0. 
If the subnet mask was 255.255.0.0, the broadcast address is 192.168.255.255

Any IPv4 address prepended with the network address is a part of the same network address. For example 192.168.10.1, 192.168.10.2.... 192.168.10.254 - Except of course the addresses 192.168.10.0 and 192.168.10.255 addresses, as they are the network address and broadcast address respectively.
i.e. Any endpoint (e.g. printer, switch etc) will have an IP address between 192.168.10.1 and 192.168.10.254 if the subnet mask is 255.255.255.0

The network address is just so you can identify the IP address to its subnet group, whereas the broadcast address is necessary so that you can send data through the network to all IP addresses in the same subnet group.\

# 10/22/26 Neil Anderson Cisco CCNA 200-301 v 1.1 - The Complete Guide to Getting Certified Section 6: Mind Dump

## Slash Notation

Simply count the number of ones in the subnet mask.

For example if subnet mask is 255.255.255.0, the binary conversion is 11111111.11111111.11111111.0, which has 24 ones and therefore the subnet mask can be represented as /24.

i.e. With the example of the IP address: 192.168.10.15 with the subnet mask 255.255.255.0
It is equivalent to 192.168.10.15/24

## Host Portion
The host portion is where the 0s of a binary conversion of the subnet mask correspond with the IP address. e.g. if the subnet mask is 255.255.0.0, and there's a host with IP address 192.168.10.15, the host portion would be where the digits 10 and 15 are. This portion is unique per host. Meaning the hosts in this subnet have IP addresses ranging from 192.168.0.1, 192.168.0.2, 192.168.0.3 ... 192.168.255.254

## Network Portion
The network portion is where the 1s of a binary conversion of the subnet mask correspond with the IP address.

Here's a table with another example of **Network Portion** and **Host Portion** of an **IP Address**

## Example: 192.168.10.15 /255.255.255.0 (/24)

| | Octet 1 | Octet 2 | Octet 3 | Octet 4 |
|---|---|---|---|---|
| IP address | 192 | 168 | 10 | 15 |
| Mask | 255 | 255 | 255 | 0 |
| Mask in binary | 11111111 | 11111111 | 11111111 | 00000000 |
| Portion | Network | Network | Network | Host |

- **Network portion:** 192.168.10 (24 bits)
- **Host portion:** 15 (8 bits)

## Dotted Decimal Notation vs Binary Notation vs Slash Notation
255.255.255.0 vs 11111111.11111111.11111111.00000000 vs /24

## Loopback Addresses (Class A)
This address is used for testing the local computer. For example, pinging 127.0.0.1 tests whether the TCP/IP Protocol works from your endpoint. 

127.0.0.0/8 is reserved for the loopback address.
127.0.0.0 is the network address
127.255.255.255 is the broadcast address
127.0.0.1 is the primary host address hence why it's used for testing. 

| Address | Use case |
|---|---|
| **127.0.0.0** (network address) | **No practical use.** It identifies the 127.0.0.0/8 block in routing tables. It is not assigned to the device and you cannot send traffic to it. |
| **127.255.255.255** (broadcast address) | **No practical use.** It is a valid broadcast address under the standard /8 calculation, but loopback has only one device (your own), so there is nothing else to broadcast to. On Linux it appears in the local routing table as a broadcast entry. |
| **127.0.0.1** | The standard loopback address, also called **localhost**. It is used for testing the TCP/IP stack and for local services, such as the Duo Endpoint Health service on your Mac. |
| **Other 127.x.x.x** | On Linux, the whole range works by default. For example, Ubuntu maps the hostname to 127.0.1.1, and systemd-resolved uses 127.0.0.53. On macOS, only 127.0.0.1 is configured by default. Other addresses must be added manually, for example with `sudo ifconfig lo0 alias 127.0.0.2`. |

## 'This Network' Address
0.0.0.0/8 is reserved for 'this network' 

**Official names in the IANA special-purpose address registry:**

- **0.0.0.0/8** is called **"This network"**

**Common informal names for 0.0.0.0:**

- **Unspecified address**
- **Wildcard address** (in programming it is called `INADDR_ANY`)

**Rule:** 0.0.0.0 can be used as a **source** address only. It must never be used as a **destination**.

| Use | How 0.0.0.0 is used |
|---|---|
| **DHCP** | A device with no IP address sends a DHCP Discover from source **0.0.0.0** to destination **255.255.255.255**. |
| **Server listening** | A service bound to **0.0.0.0** listens on every IPv4 address on the device. A service bound to **127.0.0.1** listens only locally. |
| **Default route** | **0.0.0.0/0** matches all destinations. It is configured on Cisco IOS as `ip route 0.0.0.0 0.0.0.0 <next-hop>`. This is a /0 prefix, not the /32 address. |
| **Cisco ACL wildcard** | `0.0.0.0 255.255.255.255` means "any address". |
| **Hosts file blocking** | Mapping a domain to 0.0.0.0 makes connections to it fail immediately. |
| **0.x.x.x (other than 0.0.0.0)** | Originally defined as "a specific host on this network". It is not used today. |