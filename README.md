# Hosting a Static Website on AWS

## Overview:
This project entails the deployment of a static HTML web application on Amazon Web Services (AWS). It utilizes various AWS services to ensure reliability, security, scalability, and fault tolerance.

## Project Components:
1. **Virtual Private Cloud (VPC)**:
   - Configured a VPC with both public and private subnets across two different availability zones.

2. **Internet Gateway**:
   - Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Groups**:
   - Established Security Groups as a network firewall mechanism.

4. **Availability Zones**:
   - Leveraged two Availability Zones to enhance system reliability and fault tolerance.

5. **Subnets**:
   - Utilized Public Subnets for infrastructure components like the NAT Gateway and Application Load Balancer.
   - Positioned web servers (EC2 instances) within Private Subnets for enhanced security.

6. **EC2 Instance Connect Endpoint**:
   - Implemented EC2 Instance Connect Endpoint for secure connections to assets within both public and private subnets.

7. **NAT Gateway**:
   - Enabled instances in both private Application and Data subnets to access the Internet via the NAT Gateway.

8. **Web Hosting**:
   - Hosted the website on EC2 Instances.

9. **Application Load Balancer (ALB)**:
   - Employed an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.

10. **Auto Scaling Group (ASG)**:
    - Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

11. **Version Control**:
    - Stored web files on GitHub for version control and collaboration.

12. **Certificate Manager**:
    - Secured application communications using a Certificate Manager.

13. **Simple Notification Service (SNS)**:
    - Configured Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.

14. **Domain Name**:
    - Registered the domain name and set up a DNS record using Route 53.

## Deployment Script (Bash):
```bash
#!/bin/bash

# Switch to the root user to gain full administrative privileges
sudo su

# Update all installed packages to their latest versions
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change the current working directory to the Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project GitHub repository to the current directory
git clone https://github.com/dsenazah/Host-a-static-website-on-aws.git

# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
rm -rf Host-a-static-website-on-aws

# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd

# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

## GitHub Repository:
The project is available on GitHub: [**_Host a static website on AWS_**](https://github.com/dsenazah/Host-a-static-website-on-aws.git)

## Conclusion:
This project demonstrates the implementation of a robust infrastructure on AWS for hosting a static website. By leveraging various AWS services such as VPC, EC2, ALB, and Route 53, the deployment ensures high availability, security, and scalability of the web application. The provided deployment script simplifies the setup process, enabling easy replication of the environment. Feel free to explore the GitHub repository for further details and contributions.
