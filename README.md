# Home IoT Network Design & Simulation

A scalable Smart Home IoT network designed and simulated in **Cisco Packet Tracer**. This project demonstrates end-to-end communication between smart home appliances, local control interfaces, a dedicated gateway, and a centralized remote IoT Registration Server operating across routed subnets.

---

## Architecture Overview


The network is segregated into two primary subnets interconnected by an enterprise-grade router (Cisco 2901):

1. **Home Local Area Network (LAN):** 
   - Subnet: `10.1.1.0/24`
   - Managed by a Home Wireless Router providing local Wi-Fi (`IOT5G1`) and internal DHCP routing.
   - End-user control terminals: PC0 (Ethernet), Laptop0 (Wireless), Smartphone0 (Wireless).
2. **IoT Server Infrastructure (DMZ / Data Center Zone):**
   - Subnet: `10.1.2.0/24`
   - Connected via Cisco Catalyst 2960 Switch.
   - Hosts the centralized **IoT Registration Server** (`10.1.2.2`) that facilitates monitoring and HTTP-based remote control (`http://10.1.2.2/home.html`).

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f6b88997-283f-490a-8e0e-6f9e99e5f5d9" />


## Network Topology & Addressing Scheme

| Device | Interface | IP Address | Subnet Mask | Connection Type |
|---|---|---|---|---|
| **Router0 (Cisco 2901)** | Gig0/0 (Home LAN) | `10.1.1.1` | `255.255.255.0` | Copper Straight-Through |
| **Router0 (Cisco 2901)** | Gig0/1 (Server LAN)| `10.1.2.1` | `255.255.255.0` | Copper Straight-Through |
| **Home Wireless Router** | Internet (0/0) | `10.1.1.2` | `255.255.255.0` | Copper Straight-Through |
| **IoT Server** | FastEthernet0 | `10.1.2.2` | `255.255.255.0` | Copper Straight-Through |
| **PC0** | FastEthernet0 | DHCP Assigned | `255.255.255.0` | Copper Straight-Through |
| **Laptop0 / Smartphone0**| Wireless0 | DHCP Assigned | `255.255.255.0` | Wireless (802.11n) |
| **Smart IoT Devices** | Wireless0 | DHCP Assigned | `255.255.255.0` | Wireless (WPA2-PSK) |

---

## Connected IoT Smart Devices

All smart appliances communicate through the dedicated Wi-Fi network and register with the IoT Server:

- **Ceiling Fan (`FAN`):** Multi-state control (`Off`, `Low`, `High`).
- **Air Conditioner (`AC`):** Remote power toggle for climate management.
- **Smart Door (`IoT2`):** Dual-state security mechanism (`Lock` / `Unlock`, `Open` / `Close`).
- **Humidity Monitor (`IoT5`):** Environmental monitoring sensor delivering real-time telemetry.
- **Garage Door (`IoT3`):** Automated toggle entry mechanism.
- **Smart Lamp (`IoT4`):** Remote ambient illumination control.

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0d4265ed-fc30-408b-b6f2-f8cca496f95d" />


## Wireless & Security Configuration

- **SSID:** `IOT5G1`
- **Authentication:** WPA2-PSK
- **Encryption:** AES
- **Bandwidth:** 300 Mbps (802.11n standard)

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2077bf38-2230-4945-bccb-beefea01687f" />


## Web-Based IoT Monitoring & Control

The smart appliances are monitored via HTTP using the centralized IoT monitor dashboard:

- **URL:** `http://10.1.2.2/home.html`
- **Control Channels:** Real-time state toggling, live humidity telemetry, and lock/unlock safety commands from any client PC, laptop, or smartphone terminal across the network.

---

## How to Run the Simulation

1. Clone or download this repository:
   ```bash
   git clone https://github.com/Asmeer12/Home-IoT-Network-design.git

   Open Cisco Packet Tracer (v8.0 or higher recommended).

2. Open the file: Home-IoT-Network-Design.pkt.

3. Click on PC0, Laptop0, or Smartphone0.

4. Navigate to Desktop > Web Browser.

5. Type http://10.1.2.2/home.html and hit Go.

6. Log in with the IoT Server credentials:

7. Username: HomeIOT

8. Password: CISCO
