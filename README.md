Task 1: Scan Your Local Network for Open Ports


Objective
To learn how to use port scanning tools like Nmap to detect open ports on devices in a 
local network and understand how exposed services can lead to potential security risks.


Tools Used
[Nmap](https://nmap.org/)


What I Did
1. Identified my local IP range using the `ipconfig` (Windows) or `ifconfig` (Linux/macOS) command.
2. Ran a TCP SYN scan using Nmap:
   {nmap -sS 192.168.245.128/24 -oN scan_results.txt}
3. Analyzed the output to identify devices and open ports.
4. (Optional) Captured packets in Wireshark to observe SYN requests.
5. Researched what services run on the open ports and whether they are necessary or risky.



Scan Result Summary

| Port | State | Service         | Explanation 
|------|-------|-----------------|
| 902  | Open  | iss-realsecure  | Used by VMware for remote VM management. Risky if unused. 
| 912  | Open  | apex-mesh       | Unknown or custom service. Needs further investigation. 
| 5357 | Open  | wsdapi          | Windows device discovery protocol (printer/scanner). Safe on local networks.


What I Learned

- How to find my IP range and scan the entire local network.
- How to use Nmap to discover open ports and understand their services.
- How to assess security risks based on open ports.
- How tools like Wireshark help observe what's happening behind the scenes.


Commands Used

# Find local IP
ifconfig       # (Linux)
ipconfig       # (Windows)

# Run Nmap SYN scan
nmap -sS 192.168.128.245/24 -oN scan_results.txt

# Convert to HTML (optional)
nmap -sS 192.168.245.128/24 -oX scan.xml
xsltproc scan.xml -o scan_results.html


Recommendations

- Close unnecessary ports using a firewall or by disabling unused services.
- Regularly scan your network to stay informed about what's exposed.
- Understand what services are running and who needs access to them.
