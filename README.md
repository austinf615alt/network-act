<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Configuring Network Security Groups and Inspecting Network Traffic Between Azure Virtual Machines</h1>
In this project, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups (NSG). <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DHCP, DNS, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows Server 2025 Datacenter X64 Gen2
- Ubuntu Server 24.04 LTS X64 Gen2

<h2>High-Level Steps</h2>

- Step 1: Deploy Azure Virtual Machines and Configure Network Infrastructure 
- Step 2: Capture and Analyze ICMP Network Traffic with Wireshark
- Step 3: Configure Network Security Group Rules and Validate Connectivity Changes
- Step 4: Analyze Common Network Protocol Traffic (SSH, DHCP, DNS, RDP)

<h2>Actions and Observations</h2>

---

## Step 1: Deploy Azure Virtual Machines and Configure Network Infrastructure 

---

<p>
<img width="1624" height="971" alt="RG-Creation" src="https://github.com/user-attachments/assets/87b42123-b342-4048-9a39-8d5883df50fa" />
</p>
<p>

- Created an Azure resource group named Network-Activities-RG to organize the virtual machines, networking resources, and supporting infrastructure used throughout the lab.

</p>
<br />

<p>
<img width="1624" height="971" alt="Win-Server VM Creation 1" src="https://github.com/user-attachments/assets/d6f005b2-5157-4602-aa5b-80137f4b5812" />
</p>
<p>

- Began deployment of the Windows-Server virtual machine, assigning it to the previously created resource group and deploying it in the US East region.

</p>
<br />

<p>
<img width="1624" height="971" alt="Win-Server VM Creation 2" src="https://github.com/user-attachments/assets/1f5ed991-4f34-463d-abbe-1ae4d1973532" />
</p>
<p>

- Configured the Windows virtual machine using the Windows Server 2025 Datacenter x64 Gen 2 image, allocating 2 vCPUs and 16 GiB of memory, and created a local administrator account for remote management.

</p>
<br />

<p>
<img width="1624" height="976" alt="Win-Server VM Creation VNet" src="https://github.com/user-attachments/assets/2f8caea3-6de3-41b6-a079-3fc47dbcbfc2" />
</p>
<p>

- Created a new Azure virtual network named Network-Activities-VNet, which would provide internal communication between both virtual machines.

</p>
<br />

<p>
<img width="1912" height="1152" alt="Win-Server VM Creation End" src="https://github.com/user-attachments/assets/e2a349cc-2f53-467f-93d5-21c4472458ae" />
</p>
<p>

- Reviewed the Windows virtual machine deployment settings to verify correct infrastructure configuration before provisioning.

</p>
<br />

<p>
<img width="1624" height="976" alt="Linux-Server VM Creation 1" src="https://github.com/user-attachments/assets/38b99ee0-b3af-4897-955d-e8156be8619b" />
</p>
<p>

- Began deployment of the Linux-Server virtual machine, assigning it to the same Azure resource group and region as the Windows virtual machine.

</p>
<br />

<p>
<img width="1624" height="976" alt="Linux-Server VM Creation 2" src="https://github.com/user-attachments/assets/ac818382-d999-4ce5-90bf-f568aec255cf" />
</p>
<p>

- Configured the Linux virtual machine using the Ubuntu Server 24.04 LTS x64 Gen 2 image, allocating 2 vCPUs and 16 GiB of memory, and configured local credentials for SSH-based administration.

</p>
<br />

<p>
<img width="1624" height="976" alt="Linux-Server VM Creation VNet" src="https://github.com/user-attachments/assets/fc41e36c-a0e9-4500-86b1-244ee464cdc5" />
</p>
<p>

- Connected the Linux virtual machine to the previously created Network-Activities-VNet, ensuring both systems shared the same internal network for communication testing.

</p>
<br />

<p>
<img width="1624" height="976" alt="Linux-Server VM Creation End" src="https://github.com/user-attachments/assets/796cc040-cbd0-483c-996c-8e22189e0943" />
</p>
<p>

- Reviewed and verified the Linux virtual machine deployment settings prior to provisioning.

</p>
<br />

<p>
<img width="1624" height="976" alt="VM Verify" src="https://github.com/user-attachments/assets/1c572497-cec2-4ad9-ac19-4920e94af855" />

</p>
<p>

- Confirmed that both the Windows and Linux virtual machines were successfully deployed within the same Azure environment, establishing the infrastructure required for protocol analysis and network testing.

</p>
<br />

---

## Step 2: Capture and Analyze ICMP Network Traffic with Wireshark

---

<p>
<img width="1624" height="976" alt="VM RDC Info" src="https://github.com/user-attachments/assets/c038e508-fdf5-48c9-bc00-9f22ebaf2099" />
</p>
<p>

- Recorded the public IP address of the Windows virtual machine to establish a Remote Desktop connection for protocol analysis.

</p>
<br />

<p>
<img width="1624" height="987" alt="RD-Windows-Server" src="https://github.com/user-attachments/assets/8449dfcf-7fbb-46b0-8857-6e85e1fcc47d" />
</p>
<p>

- Connected to the Windows virtual machine using Remote Desktop Protocol (RDP) to perform network traffic observation and testing from within the Azure environment.

</p>
<br />

<p>
<img width="1624" height="983" alt="Installed Wireshark" src="https://github.com/user-attachments/assets/dc9ef7b1-e73b-490d-ac1e-99f63be21e55" />
</p>
<p>

- Downloaded and installed Wireshark, a packet analysis tool used to capture and inspect live network traffic between systems.

</p>
<br />

<p>
<img width="1624" height="983" alt="Wireshark Main" src="https://github.com/user-attachments/assets/227301e8-d613-46d8-b3b4-1e3cd597ab32" />
</p>
<p>

- Opened Wireshark and selected the active Ethernet interface to begin monitoring unfiltered network traffic.

</p>
<br />

<p>
<img width="1624" height="981" alt="Linux-Server Private IP" src="https://github.com/user-attachments/assets/78596610-dd93-46a4-9a3f-18adc5cfff96" />
</p>
<p>

- Retrieved the Linux virtual machine’s private IP address (10.0.0.5) from Azure networking settings to use for internal connectivity testing.

</p>
<br />

<p>
<img width="1624" height="981" alt="ICMP Empty" src="https://github.com/user-attachments/assets/686486e5-fb5a-4e27-ae8f-738976fa2398" />
</p>
<p>

- Applied an ICMP filter in Wireshark to isolate ping traffic, then initiated a ping from the Windows virtual machine to the Linux virtual machine to generate test traffic.

- Why ICMP matters: ICMP is commonly used for connectivity testing and troubleshooting to verify whether systems can successfully communicate across a network.

</p>
<br />

<p>
<img width="1624" height="981" alt="ICMP Active" src="https://github.com/user-attachments/assets/894ce173-a1ab-4e61-8bc5-d03d79257b71" />
</p>
<p>

- Observed ICMP request and reply packets in Wireshark after initiating the ping, confirming successful internal communication between the two Azure virtual machines.

</p>
<br />

<p>
<img width="1624" height="981" alt="ICMP Observe" src="https://github.com/user-attachments/assets/f234aaa8-7e08-4a2b-9078-c9e39cf39cf2" />
</p>
<p>

- Used ipconfig /all to confirm the Windows virtual machine’s private IP address, validating the packet source shown in the Wireshark capture.

</p>
<br />

---

## Step 3: Configure Network Security Group Rules and Validate Connectivity Changes

---

<p>
<img width="1624" height="985" alt="Perpetual Ping" src="https://github.com/user-attachments/assets/3dad1405-4c66-40d5-8048-42ebdb0f6096" />
</p>
<p>

- Started a continuous ping (ping -t) from the Windows virtual machine to continuously monitor connectivity while testing network security rule behavior.

</p>
<br />

<p>
<img width="1624" height="983" alt="NSG Nav" src="https://github.com/user-attachments/assets/6fe4ef7c-b0fd-4b01-ab33-097e5ac546f2" />
</p>
<p>

- Navigated to the Linux virtual machine’s Network Security Group (NSG) settings in Azure to configure inbound traffic restrictions.

</p>
<br />

<p>
<img width="1624" height="983" alt="NSG Create" src="https://github.com/user-attachments/assets/3e499ffe-5f96-49c4-9c03-55fe0ff22a42" />
</p>
<p>

- Created a custom inbound NSG rule to deny ICMPv4 traffic, using rule priority to ensure the deny action took precedence over default allow rules.

- Why this matters: Network Security Groups act as Azure cloud firewalls, controlling inbound and outbound traffic to virtual machines.

</p>
<br />

<p>
<img width="1624" height="983" alt="NSG Create 2" src="https://github.com/user-attachments/assets/50c5676d-e4d3-4678-8482-bc0118117bf2" />
</p>
<p>

- Successfully applied the inbound ICMP deny rule to restrict connectivity to the Linux virtual machine.

</p>
<br />

<p>
<img width="1624" height="983" alt="ICMP Block" src="https://github.com/user-attachments/assets/66da8eca-700a-4570-a2b5-a8fac5c34c05" />
</p>
<p>

- Observed ping timeouts in PowerShell and missing ICMP reply traffic in Wireshark, confirming that the NSG rule successfully blocked inbound traffic.

</p>
<br />

<p>
<img width="1624" height="983" alt="Delete NSG" src="https://github.com/user-attachments/assets/ff92174e-9a75-4b9d-bad4-7a9e0f171ceb" />
</p>
<p>

- Removed the custom ICMP deny rule from the Network Security Group to restore normal network connectivity.

</p>
<br />

<p>
<img width="1624" height="983" alt="ICMP Allowed Again" src="https://github.com/user-attachments/assets/0f2c7cca-fbd8-4ac1-8f4c-01a1708f13d8" />
</p>
<p>

- Observed successful ping replies resume in both PowerShell and Wireshark, confirming restored connectivity after removing the firewall restriction.

</p>
<br />

---

## Step 4: Analyze Common Network Protocol Traffic (SSH, DHCP, DNS, RDP)

---

<p>
<img width="1624" height="987" alt="SSH Empty" src="https://github.com/user-attachments/assets/ebd28d57-5f98-43fa-80fb-3b3eef1343c8" />
</p>
<p>

- Cleared the previous Wireshark capture, applied an SSH traffic filter, and prepared an SSH connection from the Windows virtual machine to the Linux virtual machine.

- Why SSH matters: SSH (Secure Shell) provides encrypted remote command-line access to Linux systems and is commonly used for server administration.

</p>
<br />

<p>
<img width="1624" height="988" alt="SSH Active" src="https://github.com/user-attachments/assets/e00a348e-0c90-42ac-bc21-9c56cc960534" />
</p>
<p>

- Established an SSH session to the Linux virtual machine using PowerShell, observing encrypted SSH traffic in Wireshark generated by authentication and command execution activity.

</p>
<br />

<p>
<img width="1624" height="990" alt="DHCP Empty" src="https://github.com/user-attachments/assets/e4a2bac1-3851-44b7-b9ea-ca38f2600a98" />
</p>
<p>

- Cleared the Wireshark capture, applied a DHCP filter, and prepared to renew the Windows virtual machine’s IP configuration.

- Why DHCP matters: DHCP automatically assigns IP configuration details such as IP addresses, subnet masks, gateways, and DNS servers.

</p>
<br />

<p>
<img width="1624" height="990" alt="DHCP Active" src="https://github.com/user-attachments/assets/55b4f2e3-8c60-4319-ac7b-a60e6c50b0cf" />
</p>
<p>

- Executed ipconfig /renew to request updated network configuration from the DHCP server, observing DHCP request and acknowledgment traffic in Wireshark.

</p>
<br />

<p>
<img width="1624" height="990" alt="DNS Empty" src="https://github.com/user-attachments/assets/88d5bec8-4c08-40de-80f3-c7075cd701e5" />
</p>
<p>

- Cleared the Wireshark capture, applied a DNS filter, and prepared to generate DNS lookup traffic using PowerShell.

- Why DNS matters: DNS translates domain names (such as google.com) into IP addresses so systems can locate network resources.

</p>
<br />

<p>
<img width="1624" height="988" alt="DNS Active" src="https://github.com/user-attachments/assets/967344f1-27f8-4342-9248-cf874eeca857" />
</p>
<p>

- Executed nslookup queries to generate DNS traffic, observing query and response packets in Wireshark as the system resolved domain names to IP addresses.

</p>
<br />

<p>
<img width="1624" height="996" alt="RDP Always" src="https://github.com/user-attachments/assets/cc1c540e-d3f0-4b80-9047-7fcd312d2c90" />
</p>
<p>

- Applied an RDP traffic filter (tcp.port == 3389) and observed continuous traffic generated by the active Remote Desktop session.

- Why RDP appears continuous: Remote Desktop continuously transmits display updates, keyboard input, mouse movement, and session data between systems, resulting in constant network activity.

</p>
<br />

---

## Skills Developed

### Microsoft Azure Infrastructure Deployment

Gained hands-on experience deploying and managing Azure virtual machines, resource groups, virtual networks, and network security groups (NSGs) within a cloud environment.

### Virtual Networking Fundamentals

Configured Azure virtual networking components to allow secure internal communication between Windows and Linux virtual machines on the same subnet.

### Network Traffic Analysis

Used Wireshark to capture, filter, and analyze live network traffic between systems, developing practical packet analysis and troubleshooting skills.

### ICMP Connectivity Testing

Used ICMP (ping) to test internal network communication between systems and validate connectivity before and after security policy changes.

### Network Security Group (NSG) Administration

Configured Azure Network Security Group inbound rules to allow and deny specific traffic types, demonstrating cloud firewall management and access control concepts.

### Firewall Troubleshooting

Validated the impact of firewall rule changes by observing connectivity failures and successful reconnection after security rule removal.

### SSH Remote Administration

Established encrypted SSH connections from a Windows system to a Linux server, demonstrating secure command-line remote administration fundamentals.

### DHCP Analysis

Observed DHCP traffic and IP lease renewal behavior using command-line tools and packet analysis to better understand dynamic network configuration processes.

### DNS Troubleshooting and Name Resolution

Generated and analyzed DNS queries using nslookup, developing familiarity with hostname-to-IP resolution and DNS traffic behavior.

### Remote Desktop Administration

Used Remote Desktop Protocol (RDP) to remotely access and manage cloud-hosted Windows systems.

### Command-Line Networking Tools

Used networking command-line tools including ping, ipconfig /renew, nslookup, and ssh to generate and troubleshoot network traffic.

### Cross-Platform System Administration

Worked across both Windows Server and Ubuntu Linux environments, demonstrating basic multi-platform administration familiarity.

### Network Troubleshooting Methodology

Practiced structured troubleshooting by generating traffic, isolating protocols, applying security changes, and validating results through observation and testing.

### Technical Documentation

Documented infrastructure deployment, network testing, protocol analysis, and security behavior using structured technical documentation and screenshots.
