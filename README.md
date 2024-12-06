<p align="center">
  <img src="https://github.com/user-attachments/assets/196ada7d-e9dc-4417-a53a-ac259cd04b07"/>
</p>

# Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines

In this lab, I explored how to observe and manipulate network traffic between Azure Virtual Machines using Wireshark and Network Security Groups (NSGs). I used real-world tools to analyze network protocols and configure security rules.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command-Line Tools
- Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

## Operating Systems Used

- Windows 10 (21H2)
- Linux Ubuntu Server 20.04

## High-Level Steps

1. Create Resources
2. Install Wireshark
3. Observe Network Protocols and Configure NSGs

---

## Actions and Observations

<details>
<summary> 
  
### Step 1 Install Resources
  
</summary>  
  
  I started by creating a Resource Group in Azure to house all necessary components. Using Azure's search feature, I selected `Create a Resource` and defined a resource group called `RG-Network-Activities`. I set the region closest to me to optimize performance and minimize cost.

<p align="center">
  <img width="955" src="https://github.com/user-attachments/assets/ead818e7-3629-441b-985f-31d85577e70a"/>
</p>

Next, I manually created a virtual network named `Lab-Vnet` to contain my virtual machines (VMs).

<p align="center">
  <img width="850" src="https://github.com/user-attachments/assets/1aa562ed-c763-4e20-bf97-f9c8c00e86be"/>
</p>

I created two VMs: one running Windows 10 Pro and the other running Linux Ubuntu Server. Both were placed in the same resource group and virtual network.

<p align="center">
  <img width="757" src="https://github.com/user-attachments/assets/f54db579-2423-49a5-a0b8-198c9dc25e7b"/>
</p>
</details>

---

<details>
  <summary>  
  
  ### Step 2 Install Wireshark

  </summary>  
  I accessed the Windows VM via Remote Desktop using its public IP address. After logging in, I installed Wireshark with its default settings. The installation also included Npcap, which was required for packet capturing.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e4ca35ab-2354-4ebc-9ba8-719c30b2ffea"/>
</p>

Once installed, I launched Wireshark, selected the Ethernet interface, and began capturing packets. Immediately, I observed a stream of network activity taking place in the background.

<p align="center">
  <img src="https://github.com/user-attachments/assets/b88df9e0-45f4-418e-8f30-54c1fb1e21a4"/>
</p>
</details>

---

<details>
  <summary>

  ### Step 3 Observe Differing Network Protocols
  
  </summary> 

#### Testing ICMP (Ping) Traffic
I retrieved the private IP address of the Linux VM and pinged it from the Windows VM using the command `ping [private IP address]`. I filtered ICMP traffic in Wireshark to observe the requests and replies.

<p align="center">
  <img src="https://github.com/user-attachments/assets/4d3bab6b-732c-4519-bd16-1c0891256a5e"/>
</p>

To block ICMP traffic, I added a deny rule in the Network Security Group associated with the Linux VM. After applying the rule, ping requests timed out, and Wireshark displayed only outbound requests.

<p align="center">
  <img src="https://github.com/user-attachments/assets/f0ce4c21-3f6d-4818-8984-468173074a9b"/>
</p>

#### Observing SSH Traffic
I used SSH to connect to the Linux VM from the Windows VM (`ssh username@private IP`). By performing basic commands like `ls` and `pwd`, I captured SSH traffic in Wireshark.

<p align="center">
  <img src="https://github.com/user-attachments/assets/16accf8d-5251-4c07-8af3-89abb5a00ece"/>
</p>

#### Filtering DHCP and DNS Traffic
I renewed the IP address on the Windows VM (`ipconfig /renew`) to observe DHCP traffic in Wireshark. Similarly, I filtered for DNS traffic by using the `nslookup` command to resolve domain names, like `www.disney.com`.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e130fee1-9097-46a1-ad2b-bfdf1741e076"/>
</p>

#### Capturing RDP Traffic
I filtered for RDP traffic (`tcp.port == 3389`) to observe the continuous stream of data sent during my Remote Desktop session.

<p align="center">
  <img src="https://github.com/user-attachments/assets/37169e06-9e49-4a32-8fa0-a968d1517cd2"/>
</p>
</details>

---

## Summary

In this lab, I gained hands-on experience in observing and manipulating network traffic in Azure. I used Wireshark to analyze ICMP, SSH, DHCP, DNS, and RDP traffic and experimented with Network Security Groups to control access between virtual machines. This exercise improved my understanding of network protocols, traffic flows, and how to implement security measures in a cloud environment. It also emphasized the importance of using diagnostic tools for troubleshooting and security analysis.
