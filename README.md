
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
# Azure Site Recovery (ASR) - Business Continuity and Disaster Recovery

## Overview
Azure Site Recovery (ASR) provides a **Business Continuity and Disaster Recovery (BCDR)** solution within the Azure environment. It ensures that applications and workloads remain **available** during planned and unplanned outages by replicating them to a secondary location. 

I have set up ASR to ensure **business continuity** by keeping workload data available in case of a **significant failure** or **website shutdown**. If an outage occurs in **East US**, users might lose access to services. To prevent this, I implemented a **replication strategy** with a **secondary site in West US** to maintain accessibility and minimize downtime.

For redundancy, I have configured **two resource groups**, one in **East US** and another in **West US**. This setup ensures that even if one region fails, services will continue running from the other region without disruption.

## Why Use Azure Site Recovery?
ASR offers several advantages that make it an essential disaster recovery solution:

- **Minimizes Downtime** – Enables seamless failover and failback.
- **Automated Replication** – Continuously replicates Azure VMs, on-premises VMs, and physical servers.
- **Orchestrated Disaster Recovery** – Automates recovery plans with failover sequencing.
- **Cost-Effective DR Solution** – Eliminates the need for a dedicated secondary data center.
- **Security & Compliance** – Supports encryption, role-based access control (RBAC), and geo-redundant storage (GRS).

---

## My Azure Site Recovery Setup  

### **1. Environment Preparation**
- **Primary site (East US) and Disaster Recovery site (West US)** are identified.
- An **Azure Recovery Services Vault** is set up in **West US** for replication.
- **Two resource groups** are created, one for each region.

### **2. Replication Configuration**
- ASR is enabled via **Azure Portal > Recovery Services Vault > Site Recovery > Replicate**.
- The **source region (East US)** and **target region (West US)** are selected.
- **Replication policies** are defined:
  - Retention: **24 hours**
  - Storage Type: **Geo-Redundant Storage (GRS)**
  - Application-consistent snapshots enabled for databases.

### **3. Initial Synchronization & Testing**
- The **initial sync** of VMs and disks between East and West US is completed.
- **Test failovers** are performed to verify the setup.

---

## Failover and Failback Configuration

### **Failover Process**
Failover is the process of switching operations from the primary site to the disaster recovery site. I have configured two types:

1. **Planned Failover** *(For maintenance/testing, zero data loss)*  
   - Activated via **Recovery Services Vault > Select VM > Click Failover > Choose Planned Failover**

2. **Unplanned Failover** *(For unexpected disasters, latest recovery point used)*  
   - Triggered via **Recovery Services Vault > Select VM > Click Failover > Choose Unplanned Failover**  
   - Azure **Traffic Manager** automatically redirects users to the DR site.

### **Failback Process**
Once the primary site is restored:

1. **Replication is re-enabled** to sync data back to the primary region.
2. **Failback is initiated** via **Recovery Services Vault > Select VM > Click Failback**.
3. Services are restored in **East US**, and normal operations resume.

---

## Best Practices for Azure Site Recovery

### **1. High Availability & Redundancy**
- **Geo-Redundant Storage (GRS)** ensures multiple copies of data are stored.
- **Azure Load Balancer & Traffic Manager** handle failover routing.

### **2. Regular Disaster Recovery (DR) Testing**
- **Quarterly test failovers** verify the DR plan is functional.
- **Azure Runbooks** automate recovery steps for efficiency.

### **3. Cost & Performance Optimization**
- **Reserved Instances & Auto-scaling** help manage costs.
- **Replication policies** are fine-tuned based on workload priority.

### **4. Security & Compliance**
- Data is **encrypted** using **Azure Disk Encryption & Azure Key Vault**.
- **Role-Based Access Control (RBAC)** restricts unauthorized actions.

### **5. Monitoring & Alerting for Failover Readiness**
- **Azure Monitor** tracks replication health.
- **Alerts** notify about failures or required actions.

---

## Conclusion  
By implementing **Azure Site Recovery**, I have ensured **business continuity** with minimal downtime. My **failover and failback strategy** guarantees that applications remain operational even during outages. Regular testing, monitoring, and compliance measures further enhance disaster recovery readiness.  


