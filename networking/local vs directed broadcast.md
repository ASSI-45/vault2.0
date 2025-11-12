# Local and Directed Broadcast in Networking

In networking, **broadcasting** refers to sending a packet to **all hosts** on a network (as opposed to unicast, which targets one host, or multicast, which targets a group).

There are **two main types** of IPv4 broadcasts:
- **Local Broadcast**
- **Directed Broadcast**

---

## 🌐 1. Local Broadcast

**Definition:**  
A **local broadcast** is sent to **all hosts on the same local network (LAN)**. It **never leaves** that network — routers do **not forward** local broadcast packets.

**Address used:**  
`255.255.255.255`

**Example:**  
If your IP is `192.168.1.10/24`, a packet sent to `255.255.255.255` will be received by all devices in the `192.168.1.0/24` network.

**Use case examples:**
- DHCP Discover messages (when a client doesn’t yet know the DHCP server’s address)
- ARP requests (for mapping IP to MAC addresses)

**Key point:**  
Local broadcast packets **stay within the local subnet**.

---

## 🌍 2. Directed Broadcast

**Definition:**  
A **directed broadcast** is sent to **all hosts on a specific remote network**.  
It’s “directed” because it targets a **different subnet**, but once it reaches that subnet, it is broadcast locally there.

**Address format:**  
The **host portion** of the target subnet is **all 1s**.

**Example:**  
For the network `192.168.2.0/24`, the **directed broadcast address** is `192.168.2.255`.

**Use case example:**  
A host in `192.168.1.0/24` sends a packet to `192.168.2.255` — routers can (in theory) forward it to the `192.168.2.0/24` network, where it’s delivered to all hosts.

**Important note:**  
Routers **usually block directed broadcasts by default** (to prevent **smurf attacks** and other DDoS abuses).

---

## 🔑 Summary Table

| Type | Address Example | Scope | Routed? | Common Use |
|------|------------------|--------|----------|-------------|
| **Local Broadcast** | 255.255.255.255 | Local network only | ❌ No | DHCP, ARP |
| **Directed Broadcast** | e.g. 192.168.2.255 | Target remote subnet | ⚠️ Usually blocked | Rare (legacy testing, wake-on-LAN) |

---

## 🧭 Diagram: Local vs Directed Broadcast


