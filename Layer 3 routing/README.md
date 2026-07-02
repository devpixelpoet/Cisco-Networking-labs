# Corporate Multi-Layer Routing & Switching Lab (With Real-World Hardware & Packet Tracer)

This repository showcases an advanced enterprise-level network engineering project. The architecture transition spans from conceptual design in **Cisco Packet Tracer** to production implementation on physical **Cisco Routers (2811 series)** and **Multilayer Switches (3560 series)**.

The project highlights core competencies in **Layer 3 routing, Inter-VLAN configuration, static route optimization, and rigorous network troubleshooting**.

---

## 🌐 Network Architecture & Topology

The design consists of a multi-segment enterprise infrastructure engineered for redundancy and scalability:

1. **Core / Distribution Layer:** Implemented using **Cisco 3560 Multilayer Switches**, operating at Layer 3 to provide fast inter-VLAN routing and reliable backbone transport.
2. **Edge / Routing Layer:** Driven by **Cisco 2811 Integrated Services Routers**, handling inter-site connectivity and routing table convergence.
3. **Access Layer:** Provides localized endpoint connections for end-user workstations (PCs) isolated across distinct subnets.

### Topology Overview (Packet Tracer Blueprint)
* **Left Segment:** Multilayer Switch managing a local cluster of end-devices (`192.168.10.0/24` subnet mapped to `Vlan1`).
* **Transit Segments:** Dual-homed router networks operating over point-to-point subnets (`192.168.2.0/30` and `192.168.3.0/30`).
* **Right Segment:** Secondary Layer 3 Switch cluster supporting separate departments.

---

## 🛠️ Implementation & Technical Specifications

### 1. Layer 3 Routing & Subnetting
* Designed and deployed a strict IPv4 subnetting scheme utilizing classless inter-domain routing (**CIDR**).
* Configured point-to-point `/30` WAN links between routers to optimize IP address allocation.
* Implemented **Static Routing** across the enterprise fabric to dictate deterministic next-hop pathways.

### 2. Multi-Layer Switch Configuration (L3 Switching)
* Transformed traditional Layer 2 interfaces into routed ports using the `no switchport` command to allow direct IP assignments on switch boundaries.
* Configured Switched Virtual Interfaces (**SVIs**) for efficient, hardware-accelerated Inter-VLAN routing.

---

## 🔍 Troubleshooting & Verification (CLI Analysis)

A substantial part of this project involved dynamic troubleshooting, tracking routing tables, and validating interface conditions via Cisco IOS CLI using terminal emulators (MobaXterm).

### Real-time Routing Table Verification (`show ip route`)
As shown in the deployment screenshots, the routing tables were verified to ensure accurate path generation:
* **Directly Connected Routes (`C`):** Validated active interfaces (e.g., `192.168.2.0/30` on `FastEthernet0/1`).
* **Static Routes (`S`):** Confirmed successful next-hop resolution (e.g., routing traffic to remote networks like `192.168.4.0/24` via `192.168.2.2`).

### Solved Troubleshooting Scenarios:
1. **Interface State Issues:** Diagnosed and corrected administratively downed ports by applying systematic `no shutdown` sequences on critical Layer 3 interfaces.
2. **IOS Command Syntax Errors:** Troubleshooted configuration edge-cases (e.g., catching syntax errors like inputting invalid commands within incorrect prompt modes, fixing them through proper global/interface context validation).
3. **Next-Hop Reachability:** Resolved asymmetric routing patterns by ensuring mutual static route entries on both `R1`, `R2`, and the Multilayer Switches.

---

## 📸 Project Gallery

### Physical Lab Setup & Hardware Deployment
*Hands-on configuration using console cables, real Cisco 2811 routers, 3560 switches, and dual-screen monitoring environments.*

### Cisco IOS CLI Proof of Execution
*Live terminal captures verifying configuration parameters, interface activations, and successful route tables.*

---

## ⚙️ Technologies & Tools Used
* **Hardware:** Cisco 2811 Routers, Cisco 3560 Multilayer Switches
* **Software:** Cisco Packet Tracer, MobaXterm Terminal Emulator
* **Protocols & Concepts:** IPv4 Subnetting (CIDR / VLSM), Layer 3 Switching (`no switchport`), Inter-VLAN Routing (SVI), Static Routing, Cisco IOS CLI, Network Troubleshooting.
