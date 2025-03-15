# Azure VPN Implementation with ProtonVPN

## Project Overview
This project demonstrates how to use Azure virtual machines and ProtonVPN to understand VPN concepts, geo-location spoofing, and the impact of VPN connections on web browsing. It shows how different geographical server locations affect web content and IP address identification.

## Environments and Technologies Used
- Microsoft Azure (Virtual Machines)
- Windows 10
- ProtonVPN (Free Tier)
- Web Browsers
- IP Geolocation Services

## Prerequisites
- Azure subscription
- Basic understanding of virtual machines
- Remote Desktop capability

## Implementation Steps

### Part 1: Identifying Base IP Address

#### 1. Check Original IP Location
- On local physical machine, visited https://whatismyipaddress.com/
- Recorded the IP address and location information
- Saved this information in a text file for comparison

![Initial IP Check](https://i.imgur.com/BQwxfqt.png)

### Part 2: Setting Up Azure Resources

#### 1. Create Resource Group
- Logged into Azure Portal
- Created a new Resource Group named "RG-VPN-Demo"

![Resource Group Creation](https://i.imgur.com/J6h3fY2.png)

#### 2. Virtual Machine Deployment
- Created a Windows 10 Virtual Machine with the following settings:
  - Name: vpn-demo-vm
  - Region: Selected a region different from my physical location (e.g., East Asia)
  - Size: Standard_D2s_v3 (2 vCPUs, 8 GB memory)
  - Authentication: Username and password
  - Inbound ports: Allowed RDP (3389)
- Verified successful VM deployment

![VM Creation](https://i.imgur.com/UgD6Skv.png)

### Part 3: Remote Desktop Connection

#### 1. Connect to VM
- Retrieved the public IP address of the VM
- Connected to the VM using Remote Desktop Connection
- For Mac users: Used Microsoft Remote Desktop application
- Successfully logged into the Windows 10 VM

![RDP Connection](https://i.imgur.com/nHMcj5j.png)

#### 2. Check VM IP Location
- Within the VM, visited https://whatismyipaddress.com/
- Noted the IP address and location (should match the Azure region)
- Saved this information in a text file for comparison
- Confirmed the IP location differed from my physical location

![VM IP Check](https://i.imgur.com/YPFLrxR.png)

### Part 4: ProtonVPN Setup

#### 1. ProtonVPN Account Creation
- On physical machine, signed up for free ProtonVPN account
- Used the URL: https://account.protonvpn.com/signup?plan=free&language=en
- Completed registration process with email verification

![ProtonVPN Signup](https://i.imgur.com/gKV5g37.png)

#### 2. ProtonVPN Client Installation
- Within the VM, downloaded the ProtonVPN client
- Located download link at https://protonvpn.com/download
- Installed the application in the Windows 10 VM
- Logged in with ProtonVPN credentials

![ProtonVPN Installation](https://i.imgur.com/CZnfdj9.png)

### Part 5: VPN Connection Testing

#### 1. VPN Server Selection
- Opened ProtonVPN client in the VM
- Selected a VPN server in a third location (different from both physical location and VM region)
- Chose a server in Japan for this demonstration
- Connected to the selected VPN server

![VPN Connection](https://i.imgur.com/d3L9rBM.png)

#### 2. IP Verification
- With VPN connected, visited https://whatismyipaddress.com/
- Noted the new IP address and location (should show Japan)
- Saved this information in a text file
- Now had three different IP locations for comparison:
  1. Physical machine's real location
  2. Azure VM's location
  3. ProtonVPN Japan server location

![VPN IP Check](https://i.imgur.com/KJyWVEr.png)

### Part 6: Observing Geo-Location Effects

#### 1. Website Localization Testing
- Visited major websites to observe regional differences:
  - Opened Google.com (may redirect to google.co.jp)
  - Checked if search results had Japanese content
  - Visited Disney.com (may redirect to disney.co.jp)
  - Noted language changes, regional content, and URL differences

![Regional Website](https://i.imgur.com/nR2vsrP.png)

#### 2. Additional Testing
- Tried accessing region-restricted content
- Noted advertising differences based on perceived location
- Observed how websites adapted to the detected location

![Location-Based Content](https://i.imgur.com/H17ZK9Q.png)

### Part 7: Resource Cleanup

#### 1. Disconnect VPN
- Closed the VPN connection in ProtonVPN client
- Logged out of the ProtonVPN application

#### 2. Close Remote Desktop
- Logged out of the Windows 10 VM
- Closed the Remote Desktop connection

#### 3. Delete Azure Resources
- Returned to Azure Portal
- Located the "RG-VPN-Demo" resource group
- Selected and deleted the resource group
- Confirmed deletion by typing the resource group name
- Verified all resources were properly removed

![Resource Cleanup](https://i.imgur.com/9TBmHgE.png)

## Results Analysis

| Location Source | IP Address | Geographic Location | Notes |
|-----------------|------------|---------------------|-------|
| Physical Machine | x.x.x.x | Chicago, USA | Original location |
| Azure VM | y.y.y.y | Tokyo, Japan | Azure datacenter location |
| ProtonVPN | z.z.z.z | Osaka, Japan | VPN server location |

## Lessons Learned
- How IP addresses serve as geographic identifiers on the internet
- The relationship between IP addresses and content
- How IP addresses serve as geographic identifiers on the internet
- The relationship between IP addresses and content localization
- How VPNs can modify apparent user location for various purposes
- The layered approach to location masking (physical → VM → VPN)
- Practical implementation of VPN technology for privacy and geo-restriction bypass
- Resource management best practices in Azure to prevent unwanted charges
