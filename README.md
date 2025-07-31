# pfsense-openvpn-lab
Project: Secure Remote Access VPN with pfSense & OpenVPN
Objective::
To design, deploy, and verify a secure remote access VPN solution for a simulated corporate network. This project demonstrates core competencies in network administration, security protocols, and troubleshooting methodologies. A remote user will securely connect to the "corporate" network over a simulated internet connection, gaining access to internal resources as if they were physically in the office.

Technologies Used:

Virtualization: Oracle VirtualBox

Network Simulation: GNS3

Firewall/VPN Gateway: pfSense (Open-source firewall distribution)

VPN Protocol: OpenVPN

Network Analysis: Wireshark

Network Topology Diagram::
"Export from GNS3"

Configuration Summary::
Phase 1: Setup the Virtual Environment
- Download pfSense: Go to the pfSense website and download the latest Community Edition ISO (select AMD64 architecture).
- Download a Client OS: Download an ISO for a lightweight client machine. Lubuntu is a great, lightweight Linux choice. You will use this for both your "Internal Server" and your "Remote Client."
- Create Virtual Machines in VirtualBox:
    o Create a VM for pfSense. (Assign it at least 1GB RAM, 2 network adapters). Don't start it yet.
        # 2 network adapters, both "not attached" and "Intel PRO/1000 MT Desktop (82540EM)" type.
    o Create a VM for your "Internal-Server" using the Lubuntu ISO.
        # 1 network adapter, "not attached" and "Intel PRO/1000 MT Desktop (82540EM)" type.
    o Create a VM for your "Remote-Client" using the Lubuntu ISO.
        # 1 network adapter, "not attached" and "Intel PRO/1000 MT Desktop (82540EM)" type.
- Integrate VMs: Configure GNS3 to use your VirtualBox VMs.
Phase 2: Build the Network Topology in GNS3
Phase 3: Configure the pfSense Firewall & VPN Server
Phase 4: Configure the Remote Client
Phase 5: Verification & Troubleshooting

Results::