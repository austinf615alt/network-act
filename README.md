<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Configuring Network Security Groups and Inspecting Network Traffic Between Azure Virtual Machines</h1>
In this project, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups (NSG). <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows Server 2025 Datacenter X64 Gen2
- Ubuntu Server 24.04 LTS X64 Gen2

<h2>High-Level Steps</h2>

- Step 1: Created Virtual Machines within Azure
- Step 2: Observed ICMP Traffic within Wireshark
- Step 3: Configured Linux Network Security Group Rule
- Step 4: Observed ICMP Traffic with NSG Rule enabled
- Step 5: Observed SSH Traffic
- Step 6: Observed DHCP Traffic
- Step 7: Observed DNS Traffic
- Step 8: Observed RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img width="2560" height="1280" alt="image" src="https://github.com/user-attachments/assets/b19b1588-2b22-486c-8851-26063bf13920" />
</p>
<p>

- In Azure, created a resource group wherein a Windows Server 2025 Virtual Machine and an Ubuntu Linux Virtual Machine were configured and deployed, taking care to make sure both virtual machines were on the same virtual network and subnet to enable internal communication between systems.

</p>
<br />

<p>
<img width="2560" height="1327" alt="image" src="https://github.com/user-attachments/assets/3a86af82-2717-463a-a195-e133808e01cb" />
</p>
<p>

- Connected to the Windows 10 virtual machine using Remote Desktop and installed Wireshark to analyze network traffic. Configured and filtered Wireshark to only see ICMP traffic.

- Using the private IP address of the Ubuntu Linux Virtual Machine, performed ICMP ping tests within Powershell to verify internal network connectivity, observing the request and reply packets within Wireshark. Note that 10.0.0.5 is the private IP address of the Ubuntu Linux Virtual Machine and 10.0.0.4 is the source of the requests which is the Windows Virtual Machine. Also pinged "www.google.com" within Powershell to observe the ICMP traffic and verify internet connectivity.

</p>
<br />

<p>
<img width="2560" height="1280" alt="image" src="https://github.com/user-attachments/assets/8f3d6b70-8bb8-40d3-85f6-3ac6527f0be9" />
</p>
<p>

- Ran a non-stop ping from Windows Virtual Machine to Ubuntu Linux Virtual Machine using Powershell and the command "ping 10.0.0.5 -t" to monitor real time connectivity within the network. Configured and modified the Network Security Group within Azure from the Ubunut Linux Virtual Machine to block inbound ICMP traffic, resulting in failed ping responses observed in both Powershell and Wireshark.

</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-LXFIREWALLRULE2" src="https://github.com/user-attachments/assets/53ee801c-aa94-4d1f-a44e-dc65564e7d30" />
</p>
<p>

- Note that the requests timed out within Powershell and no response found within Wireshark due to the Network Security Group configuration.
- Re-enabled inbound ICMP traffic on the Network Security Group for the Ubuntu Linux Virtual Machine, observing that the Ping and Wireshark activity starts again.

</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-SSH1" src="https://github.com/user-attachments/assets/1512ec24-3325-4fa8-ae37-4cc776cafa41" />
</p>
<p>

- Reconnected to Windows Virtual Machine and initiated packet capture within Wireshark, filtering for SSH traffic. From Powershell, established an SSH connection to the Ubuntu Linux Virtual Machine using its private IP address (ssh labuser@10.0.0.5), initiating secure remote shell access. Executed basic Linux commands within the session and observed encrypted SSH packet exchanges in Wireshark. 

</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-DHCPTRAFFIC" src="https://github.com/user-attachments/assets/bdcd6074-c261-4cb0-9a76-d79d2780664b" />
</p>
<p>

- Configured Wireshark to filter for DHCP traffic to analyze IP address assignment behavior. Using Powershell as administrator, ran the "ipconfig /renew" to request a new IP address from the DHCP server. Observed DHCP reqest and response packets in Wireshark, confirming lease renewal and communication between the Windows VM and the DHCP server.

</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-DNSTRAFFIC" src="https://github.com/user-attachments/assets/02a91bf9-30b9-4f5a-aca0-0499f2502a93" />
</p>
<p>

- Configured Wireshark to filter for DNS traffic to analyze domain name resolution behavior. From Powershell, ran the "nslookup" command with google.com and apple.com after it to observe their respective IP addresses. Observed DNS query and query response packets within Wireshark , confirming successful name resolution and visibility of DNS communication between the Windows VM and the DNS servers.

</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-RDPTRAFFIC" src="https://github.com/user-attachments/assets/beaef697-8fa3-4dd6-9361-b77ea5da2b86" />
</p>
<p>

- Configured Wireshark to filter for RDP traffic typing in "tcp.port == 3389" in the filter bar. Observed continuous and high traffic between host PC and Windows VM due to the Remote Desktop Protocol maintaining the active connection. RDP Port 3389 transmits a live feed including inputs, visuals, and session data between the host computer and the remote computer.

</p>
<br />
