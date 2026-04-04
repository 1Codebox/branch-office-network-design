# branch-office-network-design
Cisco Packet Tracer VLAN &amp; Inter-VLAN Routing Lab
🖧 Branch Office Network Design (Cisco Packet Tracer Lab)

**📌 Project Overview**

This project demonstrates the design and implementation of a branch office network for a growing company. The network is built using Cisco devices in Packet Tracer and follows real-world networking practices such as VLAN segmentation, DHCP configuration, and inter-VLAN communication.

The goal of this lab is to simulate how a small enterprise network is structured to support multiple departments while ensuring scalability, security, and efficient communication.

**🏢 Scenario**

XYZ Company is expanding and opening a new branch office. The network must:

Support 3 departments:
Admin/IT
Finance/HR
Customer Service / Reception
Use 1 Router + 1 Switch (Cisco devices)
Separate departments using VLANs
Provide wireless access for users
Assign IP addresses automatically (DHCP)
Allow communication between departments (Inter-VLAN Routing)

**🧩 Network Design**

**🔹 VLAN Structure**
Department	VLAN ID	Subnet
Admin / IT	VLAN 10	192.168.1.0 /26
Finance / HR	VLAN 20	192.168.1.64 /26
Customer Service	VLAN 30	192.168.1.128 /26


**🔹 Topology Overview**
1 Router (ISR4331) → Handles routing between VLANs
1 Switch (Layer 2) → VLAN segmentation
Access Points → Wireless connectivity for each department
End Devices:
PCs
Laptops
Smartphones
Printers


**⚙️ Key Features Implemented**

✅ VLAN Configuration

Each department is isolated using VLANs to improve security and reduce broadcast traffic.

✅ Inter-VLAN Routing (Router-on-a-Stick)

The router enables communication between VLANs using subinterfaces.

✅ DHCP Configuration

Devices automatically receive IP addresses from the router.

✅ Wireless Network

Each department has its own wireless access point connected to the VLAN.

✅ Full Connectivity

All departments can communicate with each other as required.


**🛠️ Configuration Summary**

Base Network: 192.168.1.0

No. of subnets = 3

No. of subnets = 2^n

2^n = 3 ==> n=2

Class C = 255.255.255.0 ==> 11111111.11111111.11111111.00000000

After borrowing 2 bits

New Binary = 11111111.11111111.11111111.11000000

New Subnet mask: 255.255.255.192

Block size = 64


**1st Subset** 

Network ID: 192.168.1.0

Broadcasr ID: 192.168.1.63

Host Range: 192.168.1.1 - 192.168.1.62


**2nd Subset**

Network ID: 192.168.1.64

Broadcasr ID: 192.168.1.127

Host Range: 192.168.1.65 - 192.168.1.126


**3rd Subset**

Network ID: 192.168.1.128

Broadcasr ID: 192.168.1.191

Host Range: 192.168.1.129 - 192.168.1.190


**🔹 Switch Configuration**

VLAN creation:

VLAN 10
VLAN 20
VLAN 30
Assign ports to VLANs
Configure trunk port to router


**🔹 Router Configuration**

Subinterfaces for each VLAN:

interface g0/0/0.10

encapsulation dot1Q 10

ip address 192.168.1.1 255.255.255.192

interface g0/0/0.20

encapsulation dot1Q 20

ip address 192.168.1.65 255.255.255.192

interface g0/0/0.30

encapsulation dot1Q 30

ip address 192.168.1.129 255.255.255.192

do write

**DHCP pools:**

service dhcp

ip dhcp pool VLAN10 (Admin-pool)

network 192.168.1.0 255.255.255.192

default-router 192.168.1.1

dns-server 192.168.1.1

domain-name Admin.com

exit


ip dhcp pool VLAN20 (Finance-pool)

network 192.168.1.64 255.255.255.192

default-router 192.168.1.65

dns-server 192.168.1.65

domain-name Finance.com

exit


ip dhcp pool VLAN30 (CS-pool)

network 192.168.1.128 255.255.255.192

default-router 192.168.1.129

dns-server 192.168.1.129

domain-name CS.com

exit

do wr


**📡 Wireless Setup**
Each department uses an Access Point
Connected to respective VLAN
Allows laptops and smartphones to connect wirelessly

**🧪 Testing & Verification**

✔ Devices successfully receive IP addresses via DHCP

✔ Devices within VLAN can communicate

✔ Inter-VLAN communication works (ping between departments)

✔ Wireless devices connect and communicate properly

**🎯 Learning Outcomes**

From this lab, I learned:

VLAN design and segmentation
Router-on-a-stick configuration
DHCP setup on Cisco router
Wireless network integration
Real-world enterprise network planning

**📂 Tools Used**
Cisco Packet Tracer
Basic networking concepts (TCP/IP, VLANs, DHCP)

**🙌 Conclusion**
This project simulates a real-world branch office network and demonstrates how multiple departments can securely and efficiently share network resources using VLANs and routing.
