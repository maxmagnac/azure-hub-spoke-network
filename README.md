# Azure Hub-and-Spoke Network Topology

A hands-on Azure networking project demonstrating a hub-and-spoke virtual network architecture using Azure VNet Peering. This project establishes a central hub VNet connected to two spoke VNets, enabling controlled and scalable network segmentation in the cloud.

> 🔧 **Terraform Automation:** The infrastructure-as-code version of this project lives here → [azure-hub-spoke-terraform](https://github.com/maxmagnac/azure-hub-spoke-terraform)

## Network Topology

```mermaid
graph TD
 HUB["hub-vnet"]
 S1["spoke1-vnet"]
 S2["spoke2-vnet"]

 HUB -- "spoke1-to-hub | Connected | Fully Synchronized" --- S1
 HUB -- "spoke2-to-hub | Connected | Fully Synchronized" --- S2
```

## Architecture Overview

| Component | Type | Role |
|---|---|---|
| hub-vnet | Azure Virtual Network | Central connectivity hub |
| spoke1-vnet | Azure Virtual Network | Workload segment 1 |
| spoke2-vnet | Azure Virtual Network | Workload segment 2 |
| spoke1-to-hub | VNet Peering | Spoke 1 to Hub peering link |
| hub-to-spoke1 | VNet Peering | Hub to Spoke 1 peering link |
| spoke2-to-hub | VNet Peering | Spoke 2 to Hub peering link |
| hub-to-spoke2 | VNet Peering | Hub to Spoke 2 peering link |

## Peering Configuration

Azure VNet Peering requires two peering links per connection - one from each side. This project configures all four links with the following settings:

**Hub to Spoke 1**
- Allow hub-vnet to access spoke1-vnet ✅
- Forward traffic from spoke1-vnet to hub-vnet ⬜
- Gateway or route server forwarding ⬜
- Remote gateway or route server ⬜

**Hub to Spoke 2**
- Allow hub-vnet to access spoke2-vnet ✅
- Forward traffic from spoke2-vnet to hub-vnet ⬜
- Gateway or route server forwarding ⬜
- Remote gateway or route server ⬜

## Screenshot Walkthrough

### 01 - Hub VNet
![01-hub-vnet](https://github.com/user-attachments/assets/6c354471-3a6d-4229-9976-644fe83327d9)

### 02 - Spoke 1 VNet
![02-spoke1-vnet](https://github.com/user-attachments/assets/47902d88-168f-4af1-827d-13001303f61e)

### 03 - Spoke 2 VNet
![03-spoke2-vnet](https://github.com/user-attachments/assets/278360e2-462d-4b9f-be90-34fc24f166f3)

### 04 - Hub VNet Peerings Overview
![04-hub-vnet-peerings](https://github.com/user-attachments/assets/517862e5-bb84-477d-b429-c4d733f16d16)

### 04a - Hub to Spoke 1 Peering (Remote Settings)
![04a-hub-to-spoke1-peering-remote](https://github.com/user-attachments/assets/06e94467-6d61-4641-ab7c-e3bc800d9c90)

### 04b - Hub to Spoke 1 Peering (Local Settings)
![04b-hub-to-spoke1-peering-local](https://github.com/user-attachments/assets/ec404861-87aa-4a0e-adce-7afeffdd7055)

### 05 - Spoke 1 VNet Peerings
![05-spoke1-vnet-peerings](https://github.com/user-attachments/assets/e04b811a-6daa-45a4-8806-2ce309abe2b1)

### 06 - Hub to Spoke 2 Peering (Remote Settings)
![06-hub-to-spoke2-peering-remote](https://github.com/user-attachments/assets/67f161a4-eaf1-4445-a726-b17c7e3633d0)

### 07 - Hub to Spoke 2 Peering (Local Settings)
![07-hub-to-spoke2-peering-local](https://github.com/user-attachments/assets/366ab061-9c74-4a6c-a380-b35aaecc356e)

### 08 - Hub VNet Spoke 2 Peering Connected
![08-hub-vnet-spoke2-peering-connected](https://github.com/user-attachments/assets/702c9a1c-45f0-4dc9-9221-5d3e84da82e7)

### 09 - Spoke 2 VNet Peerings
![09-spoke2-vnet-peerings](https://github.com/user-attachments/assets/5e84e518-8cf9-487d-9837-31b19a21e43f)

## Key Concepts

**Hub-and-Spoke Topology**
A hub-and-spoke architecture places a central hub VNet as the shared services and connectivity layer. Each spoke VNet connects to the hub, allowing controlled communication across workload segments without direct spoke-to-spoke peering.

**Azure VNet Peering**
VNet Peering connects two Azure virtual networks, making them function as a single network for connectivity purposes. Peering operates at low latency over the Microsoft backbone network without requiring gateways or encrypted tunnels.

**Bidirectional Peering Links**
Each peered connection requires two peering links - one initiated from each VNet. Both links must reach a Connected and Fully Synchronized state for traffic to flow correctly.

## Technologies Used
- Microsoft Azure
- Azure Virtual Networks (VNet)
- Azure VNet Peering
- Azure Portal

## Related Projects

| Project | Description |
|---|---|
| [azure-hub-spoke-terraform](https://github.com/maxmagnac/azure-hub-spoke-terraform) | Terraform automation of this exact architecture |

## Author
**Maurrin Carter** — [GitHub](https://github.com/maxmagnac)
