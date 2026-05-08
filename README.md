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
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="2560" height="1280" alt="image" src="https://github.com/user-attachments/assets/8f3d6b70-8bb8-40d3-85f6-3ac6527f0be9" />
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-LXFIREWALLRULE2" src="https://github.com/user-attachments/assets/53ee801c-aa94-4d1f-a44e-dc65564e7d30" />
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-SSH1" src="https://github.com/user-attachments/assets/1512ec24-3325-4fa8-ae37-4cc776cafa41" />
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-DHCPTRAFFIC" src="https://github.com/user-attachments/assets/bdcd6074-c261-4cb0-9a76-d79d2780664b" />
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-DNSTRAFFIC" src="https://github.com/user-attachments/assets/02a91bf9-30b9-4f5a-aca0-0499f2502a93" />
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1856" height="993" alt="LAB1-RDPTRAFFIC" src="https://github.com/user-attachments/assets/beaef697-8fa3-4dd6-9361-b77ea5da2b86" />
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
