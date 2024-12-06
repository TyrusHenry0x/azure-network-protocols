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
