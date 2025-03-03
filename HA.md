#  SonarQube High Availability (HA)

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------------|-------------|----------------|-----|-------------|-------------|
| Mohit Kumar|   03-03-2025        | V1   | Mohit Kumar |03-03-2025    |  Internal Reviewer | Komal Jaiswal |



## Table of Contents

1. [Introduction](#introduction)
2. [Why High Availability?](#why-high-availability)
3. [SonarQube Editions and HA](#sonarqube-editions-and-ha)
3. [Architecture Overview](#architecture-overview)
4. [High Availability Setup Steps](#high-availability-setup-steps-for-sonarqube)
5. [Conclusion](#conclusion)
6. [Contact Information](#contact-information)
7. [References](#references)

## Introduction
This documentation provides a detailed guide to implementing High Availability (HA) for SonarQube, ensuring uninterrupted code quality and security analysis. High Availability is essential for organizations where code analysis is critical to the software development lifecycle, minimizing downtime and maintaining consistent service availability.

## Why High Availability?
High Availability (HA) ensures that SonarQube remains operational even if individual components fail. The key benefits include:

- **Minimal Downtime:** Ensures uninterrupted access to code analysis.
- **No Single Point of Failure:** Distributes workloads across multiple nodes.
- **Scalability:** Improves performance by balancing traffic efficiently.
___
  ## SonarQube Editions and HA

### Why Can't We Set Up HA in the Free Edition?

The Community Edition of SonarQube does not support clustering or distributed setups. It is designed for single-instance deployments, making it unsuitable for High Availability configurations. If the instance crashes, all services become unavailable until it is restarted manually.

### Why is HA Only Available in the Data Center Edition?

SonarQube’s **Data Center Edition** is the only version that supports High Availability. It includes:

- **Clustered Deployment:** Multiple instances work together to handle traffic.
- **Built-in Load Balancing:** Distributes requests across multiple nodes.
- **Elasticsearch Clustering:** Ensures efficient data indexing and redundancy.
- **Database Replication:** Supports failover mechanisms for continuous operation.

To implement HA, enterprises must use the **Data Center Edition**, as the required components (e.g., clustering, multi-node architecture) are not available in lower editions.
 ___
## **Architecture Overview**

### **Components and Their Roles**

| **Component**               | **Description**                                                                                       |
|-----------------------------|-------------------------------------------------------------------------------------------------------|
| **VPC (10.0.0.0/22)**       | Virtual Private Cloud for network isolation and security.                                            |
| **Public Subnet (10.0.0.0/25)** | Hosts the OpenVPN and NAT Gateway for secure access to private subnets.                           |
| **Private Subnets**         | Dedicated subnets for SonarQube servers and EFS storage.                                            |
| **Internet Gateway**        | Enables internet access for resources in the public subnet.                                        |
| **NAT Gateway**             | Allows instances in private subnets to access the internet securely.                               |
| **Application Load Balancer (ALB)** | Distributes incoming traffic across SonarQube server instances.                         |
| **Auto Scaling Group**      | Ensures high availability by dynamically adjusting the number of SonarQube servers.                |
| **SonarQube Servers (10.0.1.0/25 & 10.0.2.0/25)** | Hosts SonarQube instances behind ALB, ensuring redundancy.                  |
| **EFS (Elastic File System)** | Provides a shared storage solution for SonarQube data across multiple instances.                  |
| **Private NACL (Network ACL)** | Controls inbound and outbound traffic for security within the private subnets.            |

![image](https://github.com/user-attachments/assets/598a7bcb-03d6-4d32-b05a-ad0cb6a935cd)

---

## **High Availability Setup Steps**

### **1. Create the Infrastructure**

| **Step**                          | **Description**                                                           |
|------------------------------------|---------------------------------------------------------------------------|
| **Provision Virtual Machines**     | Set up EC2 instances for SonarQube servers in private subnets.             |
| **Configure Public & Private Subnets** | Define routing rules to allow controlled communication.                  |
| **Set Up Load Balancer (ALB)**     | Route incoming traffic to healthy SonarQube instances.                     |

---

### **2. Configure Database for High Availability**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Deploy PostgreSQL in HA Mode**   | Set up a managed database (e.g., RDS Multi-AZ) for redundancy and failover.  |
| **Optimize Database Connections**  | Tune connection pooling and query optimization for high performance.         |

---

### **3. Configure Elasticsearch for Scaling**

| **Step**                           | **Description**                                                                |
|-------------------------------------|--------------------------------------------------------------------------------|
| **Deploy Elasticsearch Cluster**   | Run multiple Elasticsearch nodes for fault tolerance.                         |
| **Distribute Load Across Nodes**   | Ensure balanced data indexing and retrieval across cluster nodes.             |

---

### **4. Enable Auto Scaling and Fault Tolerance**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Configure Auto Scaling Group**   | Scale SonarQube instances based on CPU and memory usage.                     |
| **Set Up Health Checks**           | Ensure unhealthy instances are replaced automatically.                        |

---

### **5. Secure the Infrastructure**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Implement Security Groups**      | Restrict access to SonarQube instances to only necessary ports.              |
| **Configure Network ACLs**         | Control inbound and outbound traffic at the subnet level.                    |
| **Use OpenVPN for Admin Access**   | Provide secure remote access to the private infrastructure.                  |

---

### **6. Configure Shared Storage with EFS**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Deploy AWS EFS**                 | Ensure multiple SonarQube instances share configuration and logs.             |
| **Mount EFS on SonarQube Instances** | Configure instances to use EFS for persistent data storage.                 |

---

### **7. Monitor and Test the HA Setup**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Test Failover Scenarios**        | Simulate failures to ensure high availability mechanisms work as expected.   |
| **Use Monitoring Tools**           | Set up AWS CloudWatch, Prometheus, or Grafana for real-time observability.   |

---
## Conclusion
This guide has shown how to set up SonarQube for High Availability (HA). By using a distributed setup with multiple servers and proper configurations, you can ensure that SonarQube runs smoothly without interruptions, keeping your code quality analysis always available for your team.

## Contact Information
## Contact Information

| **Name**        | **Email address**            |
|-----------------|------------------------------|
| Mohit Kumar     | mohit.kumar@mygurukulam.co    |

## References

| **Link** | **Description** |
|----------------------------------------------------|--------------------|
| [SonarQube Installation](https://docs.sonarsource.com/sonarqube-server/latest/setup-and-upgrade/install-the-server-as-a-cluster/) | SonarQube Installation Guide |
| [SonarQube Community Discussion](https://community.sonarsource.com/t/sonarqube-community-edition-high-availability/117618) | SonarQube HA Discussion |
