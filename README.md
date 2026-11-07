# 🌐 NAT Types Interactive Visualizer & Packet Simulator

[![Live Demo](https://img.shields.io/badge/Live_Demo-Online-10b981?style=for-the-badge&logo=googlechrome)](https://clonotril.github.io/NAT-Types-Interactive-Visualizer-Packet-Simulator/)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github)](https://github.com/Clonotril/NAT-Types-Interactive-Visualizer-Packet-Simulator)
[![RFC 3489](https://img.shields.io/badge/Standards-RFC_3489_%2F_4787-6366f1?style=for-the-badge)](https://datatracker.ietf.org/doc/html/rfc3489)
[![Tech Stack](https://img.shields.io/badge/Built_With-HTML5_Canvas_%7C_Tailwind-38bdf8?style=for-the-badge)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)

> **Live Interactive Simulator:** [https://clonotril.github.io/NAT-Types-Interactive-Visualizer-Packet-Simulator/](https://clonotril.github.io/NAT-Types-Interactive-Visualizer-Packet-Simulator/)  
> ⭐ **Give it a Star on GitHub:** [Clonotril/NAT-Types-Interactive-Visualizer-Packet-Simulator](https://github.com/Clonotril/NAT-Types-Interactive-Visualizer-Packet-Simulator)

---

## 🎬 Demo Video

https://github.com/user-attachments/assets/a228f693-e669-4160-a6c4-fe1d3f24e4b3






---

## 💡 Overview

An interactive, real-time networking engine that visualizes NAT (Network Address Translation) endpoint mapping and inbound firewall filtering policies. It demonstrates how UDP packets traverse gateways across the four classic RFC NAT classifications: **Full Cone**, **Restricted (Address-Restricted)**, **Port-Restricted**, and **Symmetric NAT**.

Understanding NAT traversal behavior is crucial for real-time systems, peer-to-peer protocols, WebRTC media channels, VoIP (SIP), and multiplayer game netcodes.

---

## 🔗 Live Deployment

The application is hosted and accessible in the browser:

👉 **[Launch Live Simulator](https://clonotril.github.io/NAT-Types-Interactive-Visualizer-Packet-Simulator/)**

📦 **GitHub Repository:** [https://github.com/Clonotril/NAT-Types-Interactive-Visualizer-Packet-Simulator](https://github.com/Clonotril/NAT-Types-Interactive-Visualizer-Packet-Simulator)

*(Tested across all modern desktop and mobile browsers on Chrome, Edge, Safari, and Firefox).*

---

## 🧠 Architectural Overview & RFC 4787 Mechanics

Modern NAT analysis separates behavior into two decoupled dimensions: **Mapping Behavior** and **Firewall Inbound Filtering**.

```
+-----------------------------------------------------------------------------------+
|                            NAT BEHAVIOR TAXONOMY                                  |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  [ Endpoint-Independent Mapping (Cone NATs) ]     [ Address & Port-Dependent ]    |
|   • Same local IP:Port maps to SAME public port    • Creates NEW public port for  |
|     regardless of destination server                 EVERY distinct remote host   |
|   • Supported: Full, Restricted, Port-Restricted   • Symmetric NAT (Blocks STUN)  |
|                                                                                   |
+-----------------------------------------------------------------------------------+
                                        │
                                        ▼
+-----------------------------------------------------------------------------------+
|                        INBOUND PACKET FILTERING RULES                             |
+----------------------+--------------------+---------------------+-----------------+
|      Full Cone       |  Restricted (IP)   |   Port-Restricted   |    Symmetric    |
+----------------------+--------------------+---------------------+-----------------+
| • No filtering       | • Filters by IP    | • Filters IP + Port | • 1:1 Session   |
| • Anyone can send to | • Must have sent   | • Must match remote | • Only specific |
|   open public port   |   packet to IP     |   IP and exact port |   server/port   |
| • STUN: Perfect      | • STUN: High       | • STUN: Moderate    | • STUN: Fails   |
| • TURN: Not needed   | • TURN: Not needed | • TURN: Rarely      | • TURN: Mandated|
+----------------------+--------------------+---------------------+-----------------+
```

---

## 🚀 Key Features

* **Real-time 60 FPS Packet Flight:** Animated particle physics and packet flight rendering over custom HTML5 Canvas.
* **Kernel-Style State Table Flushing:** Switching NAT architecture automatically resets the virtual `conntrack` session table and triggers an automatic outbound handshake to establish mappings.
* **Slow-Motion Inspection:** Step-down playback options (`0.3x`, `0.5x`, `1.0x`, `2.0x`) for frame-by-frame packet inspection.
* **Dynamic Role Tracking:** Dynamically identifies whether Server A or Server B is contacted first and rebinds active session tables accordingly.
* **Firewall Dropped Packet Diagnostics:** Visual spark/break effects and explanatory reason logs when packets fail firewall criteria.
* **Zero Dependencies:** Pure vanilla JavaScript, CSS Canvas rendering, and CDN Tailwind styling with zero package overhead.

---

## 📊 Summary Reference Matrix

| Sender Condition | Full Cone | Restricted (IP) | Port-Restricted | Symmetric |
| :--- | :---: | :---: | :---: | :---: |
| **Known IP, same port** *(e.g., replying server)* | ✅ Allowed | ✅ Allowed | ✅ Allowed | ✅ Allowed |
| **Known IP, different port** *(e.g., port 9999)* | ✅ Allowed | ✅ Allowed | ❌ Blocked | ❌ Blocked |
| **Unknown IP** *(Host C / unsolicited peer)* | ✅ Allowed | ❌ Blocked | ❌ Blocked | ❌ Blocked |
| **Peer sends to active mapping** | ✅ Allowed | ⚠️ *Only if sent to peer* | ⚠️ *Only if sent to peer* | ❌ Blocked |

---

## 🛠 Tech Stack

* **Rendering Engine:** HTML5 Canvas API (High-DPI / 2x Retina ready)
* **Logic & Networking Simulation:** Vanilla JavaScript (ES6+)
* **Styling & UI:** Tailwind CSS & Font Awesome Icons
* **Hosting:** GitHub Pages

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
