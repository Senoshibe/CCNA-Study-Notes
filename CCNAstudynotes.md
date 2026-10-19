## 10/10/26 Neil Anderson Cisco CCNA 200-301 v 1.1 - The Complete Guide to Getting Certified Section 5: Mind Dump
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
