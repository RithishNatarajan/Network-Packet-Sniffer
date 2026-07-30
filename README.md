INTERNID : CITS4274
# Python Packet Sniffer

A simple packet sniffer written in Python using raw sockets. This project captures and analyzes network packets directly from the network interface and displays information about Ethernet, IPv4, ICMP, TCP, and UDP packets.

> **Note:** This project is intended for educational purposes to demonstrate how network packets are structured and processed.

---

## Features

- Captures raw Ethernet frames
- Parses Ethernet headers
- Detects IPv4 packets
- Extracts IPv4 header information
- Decodes ICMP packets
- Decodes TCP segments
- Decodes UDP segments
- Displays packet payload in hexadecimal format
- Continuously monitors incoming and outgoing network traffic

---

## Technologies Used

- Python 3
- `socket`
- `struct`
- `textwrap`

No external libraries are required.

---

## Project Structure

```
packet-sniffer/
│
├── packet_sniffer.py
└── README.md
```

---

## Requirements

- Python 3.x
- Linux operating system
- Root (administrator) privileges

This project uses:

```python
socket.AF_PACKET
```

which is only available on Linux.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/packet-sniffer.git
```

Navigate to the project:

```bash
cd packet-sniffer
```

---

## Running the Program

Since raw sockets require administrator privileges, run the program using:

```bash
sudo python3 packet_sniffer.py
```

---

## Sample Output

```
Ethernet Frame:
    Destination: FF:FF:FF:FF:FF:FF
    Source: 3C:52:82:11:22:33
    Protocol: 8

IPv4 Packet:
    Version: 4
    Header Length: 20
    TTL: 64
    Protocol: 6
    Source: 192.168.1.10
    Target: 142.250.182.206

TCP Segment:
    Source Port: 51423
    Destination Port: 443
    Sequence: 23849231
    Acknowledgment: 9238492
    Flags:
        URG: 0
        ACK: 1
        PSH: 1
        RST: 0
        SYN: 0
        FIN: 0
```

---

## Supported Protocols

### Ethernet

Extracts:

- Destination MAC Address
- Source MAC Address
- Ethernet Protocol

---

### IPv4

Extracts:

- Version
- Header Length
- TTL
- Protocol
- Source Address
- Destination Address

---

### ICMP

Extracts:

- Type
- Code
- Checksum

---

### TCP

Extracts:

- Source Port
- Destination Port
- Sequence Number
- Acknowledgment Number
- Flags
  - URG
  - ACK
  - PSH
  - RST
  - SYN
  - FIN

---

### UDP

Extracts:

- Source Port
- Destination Port
- Packet Length

---

## How It Works

1. Creates a raw socket to capture all Ethernet frames.
2. Reads packets from the network interface.
3. Parses the Ethernet header.
4. Checks whether the packet contains IPv4 data.
5. Decodes the IPv4 header.
6. Determines the transport protocol (ICMP, TCP, or UDP).
7. Parses the corresponding protocol header.
8. Displays packet details and payload.

---

## Limitations

- Linux only (`AF_PACKET` is not supported on Windows).
- Requires root/administrator privileges.
- Does not capture packets in promiscuous mode unless the network interface is configured accordingly.
- Supports only Ethernet and IPv4 packets.
- Does not parse application-layer protocols such as HTTP, HTTPS, DNS, or FTP.

---

## Possible Improvements

- Add IPv6 support
- Parse ARP packets
- Decode HTTP requests and responses
- Decode DNS packets
- Save captured packets to a `.pcap` file
- Add packet filtering by IP, port, or protocol
- Display timestamps
- Export packet information to CSV or JSON
- Build a graphical interface using Tkinter or PyQt

---

## Learning Objectives

This project demonstrates:

- Raw socket programming
- Network packet capture
- Ethernet frame structure
- IPv4 packet structure
- TCP, UDP, and ICMP header parsing
- Binary data manipulation using Python's `struct` module
- Bitwise operations for decoding protocol flags

---

## License

This project is provided for educational purposes. Feel free to modify and use it for learning and experimentation.

