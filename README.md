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
    o Navigate to GNS3 Preferences > VirtualBox > VirtualBox VMs
    o Create a new VM Template for pfSense, Internal Server, and Remote Client.
    o Edit the templates for optimal settings
        # pfSense-Firewall : 
            ## Change this from "End Devices" to "Security Devices"
            ## Ensure the network adapters are set to "2", just like you set in VirtualBox.
            ## Change the first port name to "WAN"
            ## Change the port name format to LAN{0} (Port 2 will be LAN1)
        # Internal-Server :
            ## Ensure the category remains as "End Devices".
            ## Ensure the network adapter is set to "1", just like you set in VirtualBox.
        # Remote-Client :
            ## Ensure the category remains as "End Devices".
            ## Ensure the network adapter is set to "1", just like you set in VirtualBox.
    o Verify Integration by observing your tools palette in GNS3. You should see the pfSense-Firewall, Internal-Server, and Remote-Client icons available for use.
Phase 2: Build the Network Topology in GNS3
- Create a new GNS3 project.
- Create 3 major sections in your GNS3 workspace (Corporate Network, Internet, Remote Network).
    o Corporate Network
        # Drag and drop the pfSense-Firewall and Internal-Server icons into this section.
        # Add a switch to connect the pfSense-Firewall and Internal-Server. This will be your LAN.
        # Internal-Server (eth0) --> switch (eth0)
        # switch (eth1) --> pfSense-Firewall (LAN0)
    o Internet
        # Drag and drop a cloud icon to represent the Internet.
            ## Configure the cloud to use your host's network interface (Ethernet Interfaces -> Select current network adapter [e.g., Wi-Fi or Ethernet] -> Add).
        # Connect the cloud to the pfSense-Firewall
        # pfSense-Firewall (WAN) --> cloud (ethernet)
    o Remote Network
        # Drag and drop the Remote-Client icon into this section.
        # Connect the Remote-Client to the cloud.
        # Remote-Client (eth0) --> cloud (ethernet 2)
Phase 3: Configure the pfSense Firewall & VPN Server
Phase 4: Configure the Remote Client
Phase 5: Verification & Troubleshooting

Results::