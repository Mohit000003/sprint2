#  SonarQube High Availability (HA)

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------------|-------------|----------------|-----|-------------|-------------|
| Mohit Kumar|   03-03-2025        | V1   | Mohit Kumar |03-03-2025    |  Internal Reviewer | Komal Jaiswal |



## Table of Contents

1. [Introduction](#introduction)
2. [Why High Availability?](#why-high-availability)
3. [SonarQube Editions and HA](#sonarqube-editions-and-ha)
4. [Architecture Overview](#architecture-overview)
5. [Traffic Flow](#traffic-flow)
6. [High Availability Setup for SonarQube in AWS](#high-availability-setup-for-sonarqube-in-aws)
7. [Conclusion](#conclusion)
8. [Contact Information](#contact-information)
9. [References](#references)

## Introduction
This documentation provides a detailed guide to implementing High Availability (HA) for SonarQube, ensuring uninterrupted code quality and security analysis. High Availability is essential for organizations where code analysis is critical to the software development lifecycle, minimizing downtime and maintaining consistent service availability.

## Why High Availability?
High Availability (HA) ensures that SonarQube remains operational even if individual components fail. The key benefits include:

- **Minimal Downtime:** Ensures uninterrupted access to code analysis.
- **No Single Point of Failure:** Distributes workloads across multiple nodes.
- **Scalability:** Improves performance by balancing traffic efficiently.
___
  ## SonarQube Editions and HA
> [!NOTE]
> ### Why Can't We Set Up HA in the Free Edition?

>The Community Edition of SonarQube does not support clustering or distributed setups. It is designed for single-instance deployments, making it unsuitable for High Availability configurations. If the instance crashes, all services become unavailable until it is restarted manually.

### Why is HA Only Available in the Data Center Edition?

SonarQube’s **Data Center Edition** is the only version that supports High Availability. It includes:

- **Clustered Deployment:** Multiple instances work together to handle traffic.
- **Built-in Load Balancing:** Distributes requests across multiple nodes.
- **Elasticsearch Clustering:** Ensures efficient data indexing and redundancy.
- **Database Replication:** Supports failover mechanisms for continuous operation.

To implement HA, enterprises must use the **Data Center Edition**, as the required components (e.g., clustering, multi-node architecture) are not available in lower editions.
 ___
## **Architecture Overview**

![image](https://github.com/user-attachments/assets/e500e8ab-6821-45b4-ac79-9c4c1bb2b374)

### **Components and Their Roles**

| **Component**                          | **Description**                                                              |
|----------------------------------------|------------------------------------------------------------------------------|
| **VPC (10.0.0.0/22)**                  | Virtual Private Cloud providing network isolation and security.              |
| **Public Subnet (10.0.0.0/25)**         | Hosts OpenVPN and NAT Gateway for secure access to private subnets.         |
| **Internet Gateway**                    | Allows internet access for resources in the public subnet.                   |
| **NAT Gateway**                         | Enables private subnet instances to access the internet securely.            |
| **Application Load Balancer (ALB)**     | Distributes incoming traffic across SonarQube servers for load balancing.    |
| **Private Route Table**                 | Manages routing for private subnet traffic.                                  |
| **Auto Scaling Group**                  | Dynamically scales SonarQube instances based on demand.                      |
| **SonarQube Servers (10.0.1.0/25 & 10.0.2.0/25)** | Hosts SonarQube instances in private subnets.                        |
| **RDS for PostgreSQL (Primary & Secondary)** | Manages SonarQube data with replication for high availability.      |
| **Database Subnets (10.0.3.0/25 & 10.0.4.0/25)** | Houses the RDS database instances.                               |
| **Security Groups**                     | Controls access to instances based on defined rules.                          |
| **VPC Endpoint**                        | Enables secure communication with AWS services like S3.                       |
| **S3 Bucket (SonarQube Backup)**        | Stores SonarQube backups securely.                                           |




---
## **Traffic Flow**

1. **Users** access SonarQube via the ALB.
2. The ALB forwards requests to **SonarQube instances** in private subnets.
3. SonarQube stores data in **RDS PostgreSQL**, which replicates data between primary and secondary databases.
4. **NAT Gateway** enables outbound access for SonarQube servers when needed.
5. **Backups** are stored securely in an **S3 bucket** via a VPC Endpoint.

---


## **High Availability Setup for SonarQube in AWS**

This guide outlines the steps to configure a **highly available** and **fault-tolerant** SonarQube deployment in AWS.

## **1. Create the Infrastructure**

| **Step**                            | **Description**                                                           |
|--------------------------------------|---------------------------------------------------------------------------|
| **Provision EC2 Instances**          | Deploy SonarQube servers in private subnets across multiple AZs.         |
| **Configure Subnets and Route Tables** | Define public and private subnets with correct routing rules.           |
| **Set Up an Application Load Balancer (ALB)** | Distribute traffic to healthy SonarQube instances.                        |

---

## **2. Configure Database for High Availability**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Deploy PostgreSQL (Multi-AZ RDS)** | Set up a managed database with automatic failover.                         |
| **Enable Read Replicas (Optional)** | Improve read performance by distributing queries across replicas.           |
| **Optimize Database Performance**  | Use connection pooling and indexing for efficient queries.                  |

---

## **3. Configure Elasticsearch for Scaling**

| **Step**                           | **Description**                                                                |
|-------------------------------------|--------------------------------------------------------------------------------|
| **Deploy an Elasticsearch Cluster** | Run multiple nodes across AZs for redundancy and fault tolerance.             |
| **Configure Data Sharding and Replication** | Ensure even distribution of data and failover protection.                   |

---

## **4. Enable Auto Scaling and Fault Tolerance**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Set Up an Auto Scaling Group**   | Automatically scale SonarQube instances based on load.                      |
| **Define Scaling Policies**        | Use CPU/memory thresholds to add/remove instances dynamically.               |
| **Implement Health Checks**        | Ensure unhealthy instances are terminated and replaced.                      |

---

## **5. Secure the Infrastructure**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Enforce Security Group Rules**   | Restrict access to SonarQube and database instances.                         |
| **Apply Network ACLs**             | Control inbound and outbound traffic at the subnet level.                    |
| **Set Up OpenVPN for Secure Access** | Enable VPN access for administrators instead of public SSH access.          |

---

## **6. Monitor and Test the HA Setup**

| **Step**                          | **Description**                                                              |
|------------------------------------|------------------------------------------------------------------------------|
| **Simulate Failover Scenarios**    | Test instance, database, and AZ failures to verify HA mechanisms.           |
| **Implement Monitoring Solutions** | Use AWS CloudWatch, Prometheus, and Grafana for real-time observability.    |
| **Enable Logging and Alerts**      | Configure AWS CloudTrail, ELK stack, or S3 for log storage.                 |



This setup ensures **high availability, fault tolerance, and security** for SonarQube in AWS.
___
## Conclusion
This guide has shown how to set up SonarQube for High Availability (HA). By using a distributed setup with multiple servers and proper configurations, you can ensure that SonarQube runs smoothly without interruptions, keeping your code quality analysis always available for your team.
___

## Contact Information

| **Name**        | **Email address**            |
|-----------------|------------------------------|
| Mohit Kumar     | mohit.kumar@mygurukulam.co    |

## References

| **Link** | **Description** |
|----------------------------------------------------|--------------------|
| [SonarQube Installation](https://docs.sonarsource.com/sonarqube-server/latest/setup-and-upgrade/install-the-server-as-a-cluster/) | SonarQube Installation Guide |
| [SonarQube Community Discussion](https://community.sonarsource.com/t/sonarqube-community-edition-high-availability/117618) | SonarQube HA Discussion |
