# Greenheys Centre — Network Design, Implementation & Security
Cisco Packet Tracer | Networking & Cybersecurity Portfolio Project
Project overview
I designed, configured and tested a simulated network for Greenheys Centre using Cisco Packet Tracer as part of my Level 3 Networking and Cybersecurity studies. The project developed from a working multi-department network into a more secure design with traffic separation, firewall protection and access-control rules.
The goal was to provide network services to different user groups while restricting access to sensitive systems and resources.
Network design and implementation
The simulated network included a router, core switch and additional switches, PCs, printers, wireless access points, a web server and a database server. I worked through practical labs covering:
- IP addressing and subnetting, including static addresses and DHCP-assigned addresses
- VLAN creation and switch-port configuration to separate departments and student labs
- Inter-VLAN routing using router subinterfaces
- DHCP and DNS services
- Printer, server and wireless connectivity
- Connectivity checks and troubleshooting using Packet Tracer and ping tests
User groups in the design included Teachers, Administration, Managers, IT, Marketing, Lab 1, Lab 2 and wireless users. The earlier working design allowed connectivity between VLANs for testing; the later security work applied tighter access controls.
Security improvements
1. ASA firewall at the network boundary
I added a Cisco ASA firewall between an external test PC and the internal Greenheys network:
Outside PC → ASA Firewall → Router → Core Switch → Internal VLANs
Configuration recorded in my original assignment:
Device/interface	Address
Outside test PC	10.0.0.10/24, gateway 10.0.0.1
ASA outside (VLAN 2)	10.0.0.1
ASA inside (VLAN 1)	172.16.0.1
Router G0/1	172.16.0.2


Documented test: The outside PC could ping the ASA outside interface but could not ping the internal router. This is a limited connectivity test, not proof of comprehensive firewall security.
2. Separate VLAN for the database server
I separated the web and database servers because the database handles more sensitive information.
Component	Configuration
Web Server	VLAN 60, core switch Fa0/6
Database Server	VLAN 70, core switch Fa0/7
Database server IP	192.168.70.2/24
VLAN 70 gateway	192.168.70.1, router G0/0.70


Documented test: The database server successfully pinged its gateway.
3. Router access control lists (ACLs)
I created named ACLs to control movement between VLANs and protect the database:
- DATABASE-PROTECTION — restricted Marketing, Lab 1, Lab 2, Guest Wi-Fi and Staff Wi-Fi access to the database while allowing designated Teachers, Administration, Managers and IT access.
- LAB1-STUDENT-ISOLATION and LAB2-STUDENT-ISOLATION — designed to prevent student labs from accessing each other or sensitive internal departments, while preserving access to relevant learning services and lab printers.
- GUEST-WIFI-ISOLATION — restricted the guest/central Wi-Fi network (VLAN 40) from internal departmental networks, the database, printers and IT systems, while allowing the web server.
The original assignment described successful guest access to the web server and blocked guest access to the database and internal VLANs. The saved text documents those outcomes; CLI outputs and the original Packet Tracer file should be included as supporting evidence when available.
4. Security policy
I also produced a security policy covering least privilege, role-based permissions, strong passwords, staff awareness, software updates, HTTPS/certificates, file permissions and layered physical/software safeguards. I reviewed common attack types, likely sources and motives, and ways to reduce security risks.
Testing and evidence
My assignment documented DHCP address allocation, working network connectivity/ping tests, firewall boundary testing, database gateway connectivity, and segmentation/access restrictions. The evidence section below can be populated with screenshots exported from the original .pkt file or the assessed assignment; screenshots are not embedded here because the original image files have not yet been recovered.
Suggested evidence folder:
screenshots/
  network-topology.png
  vlans-and-trunks.png
  dhcp-addresses.png
  database-vlan70.png
  firewall-test.png
  acl-tests.png
Skills demonstrated
Cisco Packet Tracer · Network design · Switching and VLANs · IP addressing and subnetting · Inter-VLAN routing · DHCP · DNS · Cisco ASA firewall · ACLs · Network testing and troubleshooting · Network security documentation
What I learned
This project helped me move from basic connectivity and device configuration to thinking about who should be allowed to access each part of a network. I practised building a working network, testing connectivity, identifying security risks and applying segmentation and access controls while maintaining essential services.
Project files
- README.md — project overview and technical summary (this file)
- Greenheys_Network_Project_Report.pdf — portfolio report
- Greenheys.pkt — original Packet Tracer file (add when available)
- screenshots/ — original topology/configuration/test screenshots (add when available)
Evidence note: This README was reconstructed from the saved written assignment, including its network-security demonstrations. Configuration descriptions reflect that record, not a fresh independent audit of the .pkt file.
