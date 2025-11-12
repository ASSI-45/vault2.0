
## layer 2 - packet in and from the the END to END layer

At **Layer 3 (Network layer)**, the data unit is a **packet**.
The most common example is an **IPv4 packet**.

Here’s how an **IPv4 packet** looks in a clear Markdown table:

---

### 🌐 IPv4 Packet Structure (Layer 3)

| **Field**                                     | **Size (bits)**       | **Description**                                                              |
| --------------------------------------------- | --------------------- | ---------------------------------------------------------------------------- |
| **Version**                                   | 4                     | IP version number (always `4` for IPv4).                                     |
| **IHL (Internet Header Length)**              | 4                     | Length of the header in 32-bit words. Minimum is 5 (20 bytes).               |
| **DSCP (Differentiated Services Code Point)** | 6                     | Used for packet priority and QoS.                                            |
| **ECN (Explicit Congestion Notification)**    | 2                     | Used for congestion control signaling.                                       |
| **Total Length**                              | 16                    | Total packet length (header + data) in bytes.                                |
| **Identification**                            | 16                    | Unique ID for fragment reassembly.                                           |
| **Flags**                                     | 3                     | Control flags (e.g., DF = Don’t Fragment, MF = More Fragments).              |
| **Fragment Offset**                           | 13                    | Indicates the position of this fragment in the original datagram.            |
| **Time To Live (TTL)**                        | 8                     | Limits packet lifetime (decremented by each router).                         |
| **Protocol**                                  | 8                     | Indicates encapsulated Layer 4 protocol (e.g., TCP = 6, UDP = 17, ICMP = 1). |
| **Header Checksum**                           | 16                    | Error-checking for the header.                                               |
| **Source IP Address**                         | 32                    | Sender’s IPv4 address.                                                       |
| **Destination IP Address**                    | 32                    | Receiver’s IPv4 address.                                                     |
| **Options (optional)**                        | Variable (0–40 bytes) | Used for testing, routing, or timestamps.                                    |
| **Padding**                                   | Variable              | Ensures the header is a multiple of 32 bits.                                 |
| **Data (Payload)**                            | Variable              | Contains the Layer 4 segment (e.g., TCP, UDP, ICMP data).                    |

---

### 📦 Example IPv4 Packet (simplified)

| **Field**       | **Example Value** | **Notes**               |
| --------------- | ----------------- | ----------------------- |
| Version         | 4                 | IPv4                    |
| IHL             | 5                 | 20-byte header          |
| DSCP / ECN      | 0                 | Default                 |
| Total Length    | 60 bytes          | Header + Data           |
| Identification  | 0x1C46            | Packet ID               |
| Flags / Offset  | DF set            | Don’t Fragment          |
| TTL             | 64                | Typical initial value   |
| Protocol        | 6                 | TCP                     |
| Header Checksum | 0xB1E6            | Calculated from header  |
| Source IP       | 192.168.1.10      | Sender                  |
| Destination IP  | 8.8.8.8           | Receiver                |
| Data            | (TCP segment)     | Transport layer content |


There is also the the **IPv6 structure**.

---

## layer 3 - frames in and from the data link layer

It is a wrapper for layer 2 Ip packets.

Here’s how a **Layer 2 (Data Link layer) frame** typically looks, using **Ethernet II** as an example:

| **Field**                       | **Size (bytes)** | **Description**                                                                                         |
| ------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------- |
| **Preamble**                    | 7                | Synchronization pattern used by the receiver to establish bit timing.                                   |
| **Start Frame Delimiter (SFD)** | 1                | Indicates the start of the frame (`10101011` pattern).                                                  |
| **Destination MAC Address**     | 6                | MAC address of the destination device.                                                                  |
| **Source MAC Address**          | 6                | MAC address of the source device.                                                                       |
| **EtherType / Length**          | 2                | Indicates either the protocol type (e.g., IPv4 = `0x0800`) or payload length.                           |
| **Payload (Data)**              | 46–1500          | Encapsulated Layer 3 data (e.g., IP packet). Must be at least 46 bytes for Ethernet minimum frame size. |
| **Frame Check Sequence (FCS)**  | 4                | CRC used for error detection.                                                                           |

✅ **Minimum frame size:** 64 bytes
✅ **Maximum frame size (standard Ethernet):** 1518 bytes (without VLAN tag)

If a VLAN tag (IEEE 802.1Q) is present, an extra **4 bytes** are added:

| **Field**                          | **Size (bytes)** | **Description**                                               |
| ---------------------------------- | ---------------- | ------------------------------------------------------------- |
| **Tag Protocol Identifier (TPID)** | 2                | Indicates VLAN tagging (`0x8100`).                            |
| **Tag Control Information (TCI)**  | 2                | Contains VLAN ID (12 bits), priority, and other control bits. |

There is also the **Bit level Diagram**.

---

## layer 4 - Segments and Datagrams in and from the trasnsport layer (_Service to Service_)

At **Layer 4 (Transport layer)**, the data unit is called a **segment** (for TCP) or a **datagram** (for UDP). 


## 🧩 TCP Segment (L4)

| **Field**                 | **Size (bits)** | **Description**                                                 |
| ------------------------- | --------------- | --------------------------------------------------------------- |
| **Source Port**           | 16              | Port of the sender.                                             |
| **Destination Port**      | 16              | Port of the receiver.                                           |
| **Sequence Number**       | 32              | Number of the first byte in this segment.                       |
| **Acknowledgment Number** | 32              | If ACK flag is set, the next expected byte from the other side. |
| **Data Offset**           | 4               | Header length in 32-bit words.                                  |
| **Reserved**              | 3               | Reserved, must be 0.                                            |
| **Flags**                 | 9               | Control bits: URG, ACK, PSH, RST, SYN, FIN, ECE, CWR, NS.       |
| **Window Size**           | 16              | Size of the sender’s receive window (flow control).             |
| **Checksum**              | 16              | Error-checking for header + data.                               |
| **Urgent Pointer**        | 16              | Points to urgent data if URG flag is set.                       |
| **Options**               | Variable        | Optional (e.g., Maximum Segment Size, Timestamps).              |
| **Padding**               | Variable        | Ensures header is multiple of 32 bits.                          |
| **Data (Payload)**        | Variable        | Encapsulated Layer 5 (application) data.                        |

---

### 📦 Example TCP Segment (simplified)

| **Field**             | **Example Value** | **Notes**                     |
| --------------------- | ----------------- | ----------------------------- |
| Source Port           | 443               | HTTPS server                  |
| Destination Port      | 56789             | Client port                   |
| Sequence Number       | 0x1A2B3C4D        | First byte of segment         |
| Acknowledgment Number | 0x0               | Not set for SYN               |
| Data Offset           | 5                 | 20-byte header                |
| Flags                 | SYN               | Initial connection request    |
| Window Size           | 65535             | Max window                    |
| Checksum              | 0xABCD            | Calculated from header + data |
| Urgent Pointer        | 0                 | Not used                      |
| Data                  | —                 | No payload for SYN            |

---

## 🧩 UDP Datagram (L4)

| **Field**            | **Size (bits)** | **Description**                          |
| -------------------- | --------------- | ---------------------------------------- |
| **Source Port**      | 16              | Port of the sender.                      |
| **Destination Port** | 16              | Port of the receiver.                    |
| **Length**           | 16              | Length of header + data in bytes.        |
| **Checksum**         | 16              | Error-checking for header + data.        |
| **Data (Payload)**   | Variable        | Encapsulated Layer 5 (application) data. |

---

### 📦 Example UDP Datagram

| **Field**        | **Example Value** | **Notes**                     |
| ---------------- | ----------------- | ----------------------------- |
| Source Port      | 53                | DNS server                    |
| Destination Port | 34567             | Client port                   |
| Length           | 32 bytes          | Header + payload              |
| Checksum         | 0x1F2E            | Calculated from header + data |
| Data             | DNS response      | Application data              |

---


