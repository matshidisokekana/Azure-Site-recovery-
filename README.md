
## **Azure Site Recovery**
Azure Site Recovery provides comprehensive solutions that enable organizations to protect their critical applications and data in the event of an outage. In this project, I have explored the key features and functionality of Azure Site Recovery, including setting up protection for virtual machines and implementing failover mechanisms.
![](imageazure.png)
# **Azure Site Recovery (ASR) Architecture**

## **Overview**
This repository contains an Azure Site Recovery (ASR) architecture diagram demonstrating disaster recovery and high availability between **East US (Primary)** and **West US (Disaster Recovery Site)** using **Azure Traffic Manager** and **ASR replication**.


## **Architecture Diagram**
![Azure Site Recovery Diagram](recovery.avif)

## **Replication Setup**
- **East US (Primary Site)**
  - Web, App, and Database tiers hosted on **Azure VMs** with **Availability Sets**.
  - **Public IP & Load Balancer** manage traffic.
- **West US (Disaster Recovery Site)**
  - Mirrors the **primary site** with continuous **disk replication** via **Azure Site Recovery (ASR)**.
  - Becomes active during failover.

## **Failover Process**
1. **Primary site failure detected.**
2. **ASR** triggers failover to **West US**.
3. **Traffic Manager** redirects user traffic seamlessly.

## **Key Components**
- **Azure Traffic Manager** – Routes global traffic.
- **Azure Site Recovery (ASR)** – Ensures replication and failover.
- **Azure Load Balancer** – Distributes traffic across VMs.

This architecture provides a robust **disaster recovery solution** with automatic **failover** to maintain business continuity across Azure regions.
