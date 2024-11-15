# Static Website Deployment on AWS

## Overview

This project demonstrates how to deploy a static website with a WordPress application hosted on AWS. It leverages AWS services for high availability, fault tolerance, and scalability. The architecture ensures secure, reliable, and scalable hosting of a static website using EC2 instances, Auto Scaling Groups (ASGs), and Elastic File System (EFS).

## Architecture

The deployment utilizes the following AWS resources:

- **VPC**: Configured with public and private subnets across two Availability Zones (AZs) for high availability and fault tolerance.
- **Internet Gateway (IGW)**: Enables communication between VPC resources and the internet.
- **Security Groups**: Acts as a virtual firewall to control inbound and outbound traffic.
- **NAT Gateway**: Allows instances in private subnets to access the internet while keeping them inaccessible from the outside.
- **Application Load Balancer (ALB)**: Distributes incoming traffic across multiple EC2 instances in multiple AZs.
- **EC2 Instances**: Used to host WordPress and other website services. Instances are dynamically managed using an ASG.
- **EC2 Instance Connect Endpoint**: Provides secure access to public and private subnets.
- **Elastic File System (EFS)**: Mounted on EC2 instances for persistent storage.
- **Route 53 (R53)**: Manages custom domain registration and DNS routing.

## Features

1. **High Availability and Fault Tolerance**: 
   - Subnets in multiple AZs.
   - Auto Scaling Group dynamically adjusts the number of EC2 instances based on demand.

2. **Security**:
   - Instances hosting the WordPress application are in private subnets.
   - Security Groups ensure only necessary ports are open.

3. **Scalability and Elasticity**:
   - ASG ensures the website scales dynamically with traffic.
   - Load balancing for efficient traffic distribution.

4. **Persistent Storage**:
   - EFS provides shared, scalable storage for web content.

5. **Custom Domain**:
   - Route 53 is used for managing a custom domain name for the website.

## Prerequisites

- An AWS account with required permissions.
- A registered domain (optional, for Route 53 configuration).
- Basic knowledge of AWS and Linux commands.

## Deployment Steps

### 1. Set Up the Environment

1. **Create VPC and Subnets**:
   - Configure public and private subnets across two AZs.
   - Attach an Internet Gateway to the VPC.

2. **Create Security Groups**:
   - Allow HTTP (port 80) and HTTPS (port 443) traffic for the ALB.
   - Restrict access to private EC2 instances.

3. **Launch EC2 Instance**:
   - Use the provided script to configure the instance and install WordPress.

### 2. Configure WordPress

- Follow the script to:
  - Install Apache, PHP, and MySQL.
  - Download and set up WordPress.
  - Configure permissions and mount EFS for shared storage.

### 3. Implement Load Balancing and Auto Scaling

- **Create an ASG Launch Template** using the provided script.
- Configure the ALB to distribute traffic across multiple instances.

### 4. Configure Route 53

- Register your domain name with Route 53.
- Map the ALB’s DNS name to your custom domain.

## Deployment Scripts

### WordPress Installation Script

```bash
# WordPress setup script
# Please refer to install-wordpress.sh

```

### ASG Launch Template Script

```bash
# Auto Scaling Group setup script
# Please refer to launch-template-script-install-wordpress.sh
```

## Diagram

![Alt text](Reference Architecture.png)

## Additional Notes

- Scripts to deploy the application are included in this repository.
- Ensure proper IAM roles and permissions for the resources.

## Conclusion

This project demonstrates an end-to-end deployment of a static WordPress website on AWS with a robust and scalable architecture. By leveraging AWS services, the setup ensures high availability, fault tolerance, and security.
