### Chapter 15: IP Routing - Summary with Example Commands

---

#### **15.1 Packet Forwarding: A Closer Look**
- **Next-Hop Routing**:
  - Only the next destination (router or host) is determined during forwarding.
  - Source routing (complete path pre-determined) is mostly unused due to security issues.
- **Routing Tables**:
  - Store rules for directing packets based on their destination.
  - Use commands like `netstat -rn` or `ip route show` to examine.

Example:
```bash
# Display the routing table
ip route show
```

---

#### **15.2 Routing Daemons and Routing Protocols**
- **Routing Daemons**:
  - Collect route information dynamically.
  - Examples include Quagga and Bird.
- **Protocol Types**:
  - Distance-Vector: Advertise routes as "hops" (e.g., RIP).
  - Link-State: Share network topology to compute routes (e.g., OSPF).

Example:
```bash
# Start a Quagga daemon
sudo systemctl start zebra
```

---

#### **15.3 Protocols on Parade**
- **RIP and RIPng**:
  - Simplicity but limited to small networks.
- **OSPF**:
  - Preferred for large and complex networks.
  ```bash
  # OSPF configuration in Quagga
  router ospf
  network 192.168.1.0/24 area 0
  ```
- **BGP**:
  - Standard for Internet-wide routing, manages traffic between autonomous systems.

---

#### **15.4 Routing Protocol Multicast Coordination**
- Routing protocols often use multicast to communicate efficiently.
- Each protocol has specific multicast addresses.

Example:
```bash
# View multicast groups
ip maddr
```

---

#### **15.5 Routing Strategy Selection Criteria**
- **Static Routing**:
  - Best for small, unchanging networks.
  - Example:
    ```bash
    ip route add 192.168.2.0/24 via 192.168.1.1
    ```
- **Dynamic Routing**:
  - Necessary for large or frequently changing topologies.

---

#### **15.6 Routing Daemons**
- **routed**:
  - Obsolete; limited support for RIP.
- **Quagga**:
  - Supports multiple protocols (RIP, OSPF, BGP).
- **Bird**:
  - Lightweight and configurable for dynamic routing.

Example:
```bash
# Install Quagga on Linux
sudo apt install quagga
```

---

#### **15.7 Cisco Routers**
- Cisco uses proprietary protocols like EIGRP, as well as standard ones (OSPF, BGP).
- CLI Example:
  ```bash
  # Configure a default route
  config terminal
  ip route 0.0.0.0 0.0.0.0 192.168.1.1
  exit
  ```

---

#### **15.8 Recommended Reading**
- Suggested resources cover advanced routing concepts and protocol-specific strategies.

This summary combines foundational concepts and practical examples for managing IP routing. Let me know if further elaboration is needed!