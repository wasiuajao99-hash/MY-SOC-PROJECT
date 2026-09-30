A cybersecurity lab project demonstrating **network monitoring, attack simulation, intrusion detection, and firewall response** using pfSense, Ubuntu, Kali Linux, Wireshark, Snort, and Wazuh. The project investigates reconnaissance, port scanning, brute-force authentication, and Shellshock activity, then applies firewall rules to restrict malicious traffic. 

## Project Overview

The project focuses on building and testing a segmented cybersecurity network using **pfSense** as the firewall, with Ubuntu as the protected LAN host, Kali Linux as the testing/attack host, and Wazuh as the SIEM. The project demonstrates how network attacks can be detected using **Wireshark, Snort, and Wazuh**, followed by firewall rule implementation to block malicious traffic. 

## Network Topology

* **pfSense WAN:** `10.0.2.15`
* **pfSense LAN:** `192.168.1.1`
* **pfSense DMZ:** `192.168.2.1`
* **Ubuntu LAN host:** `192.168.1.101`
* **Kali Linux DMZ host:** `192.168.2.100`
* **Wazuh SIEM:** `192.168.1.102`
* Ubuntu and Kali were tested for connectivity using ICMP.
* Kali was used to generate reconnaissance and attack traffic against Ubuntu. 

## Tools and Technologies

* **pfSense** firewall
* **Ubuntu Linux**
* **Kali Linux**
* **Wazuh SIEM**
* **Wireshark** network protocol analyser
* **Snort IDS**
* **SSH**
* **FTP**
* **HTTP**
* **Nmap** for network reconnaissance and port scanning
* **Hydra** for password-guessing attacks
* **Nikto** for web application scanning
* **MITRE ATT&CK** techniques for attack classification 

## Configuration Steps

1. Configure the **pfSense WAN, LAN, and DMZ interfaces** with the required IP addresses.
2. Configure Ubuntu with IP address `192.168.1.101`.
3. Configure Kali Linux with IP address `192.168.2.100`.
4. Configure Wazuh with IP address `192.168.1.102`.
5. Verify connectivity between Ubuntu and Kali using `ping`.
6. Confirm that SSH port `22` is listening on Ubuntu.
7. Monitor network traffic between Kali and Ubuntu using **Wireshark**.
8. Apply Wireshark filters such as `tcp.port == 22` and `tcp.flags.syn == 1 && tcp.flags.ack == 0` to identify SSH and SYN-scan activity.
9. Perform **port scanning** from Kali against Ubuntu.
10. Simulate **Hydra password-guessing** activity against authentication services.
11. Use **Nikto** to perform web application reconnaissance.
12. Monitor the generated activity using **Snort IDS** on pfSense.
13. Review security events and attack alerts in **Wazuh SIEM**.
14. Analyse alerts involving SSH authentication, brute-force activity, and Shellshock.
15. Create pfSense rules to allow required LAN traffic while blocking the malicious Kali IP from the LAN.
16. Verify that Kali can no longer reach Ubuntu after the firewall rules are applied. 

## Results and Findings

* Successful connectivity between the Ubuntu LAN host and Kali DMZ host was initially established.
* Wireshark identified **TCP SYN-based port scanning** from `192.168.2.100` against `192.168.1.101`.
* Snort detected suspicious activity involving **HTTP port 80 and SSH port 22**, including possible Nmap scanning, web enumeration, and directory guessing.  
* Wazuh detected multiple authentication events consistent with a **brute-force attack**.
* Wazuh identified a **Level 15 Shellshock alert** originating from Kali against Ubuntu and mapped the activity to MITRE ATT&CK techniques **T1068** and **T1190**. 
* Firewall rules were successfully applied to prevent the Kali DMZ host from reaching the Ubuntu LAN host.
* Ubuntu could still reach the DMZ after the rules were applied, demonstrating controlled network segmentation and traffic filtering. 

## Author

* **Name:*Wasiu Ajao
* **Contact:** [wasiuajao99@gmail.com]
