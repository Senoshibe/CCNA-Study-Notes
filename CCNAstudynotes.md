## 10/19/26 Neil Anderson Cisco CCNA 200-301 v 1.1 - The Complete Guide to Getting Certified Section 5: Mind Dump
#Revision of what I've learnt from video to see if I understand....
# TCP/UDP and the Transport Layer
TCP and UDP live in the transport layer. 
TCP is best effort, meaning there's flow control and sometimes checks for errors. 
Whereas UDP is for best effort. 

UDP is mainly for video and voice as they can't afford the overhead in the headers that are typically found in TCP. TCP is usually for every other service that relies on the data reaching from source to destination. 

Data sent via TCP is in sequence and any dropped packets are sent again, whereas with UDP, dropped packets are left dropped and an effort isn't made for the data to be sent in sequence. 

# Multiplex Sessions
Multiplex sessions are when a sender can have multiple sessions and send data via different protocols to different receivers at the same time. 

# 3 Way Handshake
When a sender and receiver establishes a connection, the handshake is in the followin sequence: SYN > SYN-ACK > ACK 
Whereby, the sender attempt to sync with the receiver, the receiver acknowledges the sync, and the sender finally acknowledges (?) the connection. 

# Source and Destination Ports and Protocols
For example when the sender sends data through a web server to receiver, the source to destination ports would be from port 80 HTTP to receiver's port e.g. port 2500, and back from 2500 to 80. 

Firewalls can determine whether the transfer of data is bi-direcitonal or not. For example, it can set a rule where it allows the sender to send data to the receiver on their respective ports, however, the receiver cannot send data to sender. Or it can allow the sending of data from receiver to sender, under the condition that the sender has sent data to receiver in the same session.

# Port Numbers and their Protocols
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

# Review of Mind Dump:
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
