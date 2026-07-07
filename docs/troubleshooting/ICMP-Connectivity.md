Troubleshooting: Restoring ICMP Connectivity Between Windows Server and Windows 10 Client
Objective: Identify and resolve why the Windows Server and Windows 10 client could not communicate using ICMP (ping) in the pfSense home lab.
Issue
During validation of network connectivity, the Windows Server (192.168.1.10/24) and the Windows 10 client (DHCP address 192.168.1.100/24) were unable to ping one another despite being on the same subnet and using the same default gateway (192.168.1.1). Ping requests timed out.
Environment
•	Firewall/Router: pfSense
•	Server: Windows Server (Static IP: 192.168.1.10/24)
•	Client: Windows 10 (DHCP: 192.168.1.100/24)
Troubleshooting Process
1.	Verified IP addressing, subnet mask (/24), and default gateway on both systems.
2.	Reviewed pfSense firewall logs for blocked traffic.
3.	Verified the default LAN allow rule in pfSense and confirmed LAN traffic was permitted.
4.	Investigated Windows Defender Firewall on the Windows systems.
5.	Located the inbound rule 'File and Printer Sharing (Echo Request - ICMPv4-In)'.
6.	Enabled the ICMPv4 Echo Request rule.
7.	Retested connectivity and confirmed successful ping responses.
Root Cause
The Windows Defender Firewall was blocking inbound ICMP Echo Requests. Although pfSense was routing traffic correctly, Windows would not respond to ping requests until the ICMPv4 inbound firewall rule was enabled.
Resolution
After enabling the 'File and Printer Sharing (Echo Request - ICMPv4-In)' inbound rule, the Windows Server and Windows 10 client were able to successfully ping each other.
Evidence

<img width="624" height="509" alt="windows_user_firewall_rules" src="https://github.com/user-attachments/assets/c80b802d-c365-45f4-ac51-789f1c67c17a" />

Windows Server Command Prompt showing failed ping followed by successful ping.

<img width="624" height="469" alt="Windows_server_cmd_ping" src="https://github.com/user-attachments/assets/e5dacb41-eea2-47ac-9de1-b518024b40f3" />

Windows Defender Firewall Advanced Security showing the enabled 'File and Printer Sharing (Echo Request - ICMPv4-In)' rule.

<img width="624" height="477" alt="pFsense_allow_rule" src="https://github.com/user-attachments/assets/32b6093b-c3e7-4129-a191-ad0b57c64c13" />

pfSense Firewall → Rules → LAN showing the default Allow LAN rule.
Lessons Learned
Successful routing through pfSense does not guarantee end-to-end connectivity. Host-based firewalls must also permit the desired traffic. Verifying IP configuration, router rules, and host firewall settings in a logical order provides an efficient troubleshooting workflow.
