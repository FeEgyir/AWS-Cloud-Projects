# CloudFormation Capstone Project - Group 8

## Project Description
This project implements a **secure, scalable, and highly available two-tier architecture** on AWS for a Node.js-based Inventory Management Application. The infrastructure leverages core AWS services to ensure fault tolerance, automated scaling, and robust security.

### Key Objectives:
- **High Availability**: Deploy resources across multiple Availability Zones (AZs).
- **Security**: Restrict access using Security Groups, NACLs, and a Bastion Host.
- **Scalability**: Use Auto Scaling Groups (ASGs) and Load Balancers to handle traffic fluctuations.
- **Monitoring**: Track performance via Amazon CloudWatch alarms.

### Technologies Used:
| Category       | AWS Services/Tools                                                                 |
|----------------|------------------------------------------------------------------------------------|
| Compute        | EC2 (Amazon Linux), Auto Scaling Groups                                           |
| Database       | PostgreSQL (RDS/Aurora)                                                            |
| Networking     | VPC, Public/Private Subnets, Internet Gateway, NAT Gateway, Application Load Balancer |
| Security       | Security Groups, NACLs, IAM                                                        |
| Monitoring     | Amazon CloudWatch                                                                  |

---

## Architecture Overview
![Architecture Diagram](https://via.placeholder.com/800x500.png?text=Architecture+Diagram+Placeholder)  
*Replace with your architecture diagram link.*

### Components:
1. **VPC**: 
   - CIDR: `10.0.0.0/16`
   - Public Subnets: `10.0.1.0/24` and `10.0.3.0/24` (for Bastion Host, ALB, NAT Gateway).
   - Private Subnets: `10.0.2.0/24` and `10.0.4.0/24` (for EC2 instances, RDS).

2. **Internet Gateway**: Attached to the VPC for public subnet internet access.

3. **NAT Gateway**: Deployed in the public subnet to allow private subnet instances to access the internet.

4. **Security Groups**:
   - **ALB**: Allows HTTP/HTTPS traffic from the internet.
   - **Bastion Host**: Restricts SSH access to trusted IPs.
   - **Private EC2 Instances**: Allows HTTP/HTTPS from ALB and SSH from Bastion Host.
   - **RDS**: Permits PostgreSQL traffic (port 5432) only from private EC2 instances.

5. **Auto Scaling Group (ASG)**:
   - **Launch Template**: Uses a pre-configured AMI from a private EC2 instance.
   - **Scaling Policies**: 
     - Scale out: Add 2 instances when CPU > 60%.
     - Scale in: Reduce to 1 instance when CPU < 30%.

6. **Application Load Balancer (ALB)**: Distributes traffic to instances in private subnets.

7. **PostgreSQL Database**: Hosted on RDS in private subnets.

---

## Deployment Instructions

### Prerequisites:
- AWS CLI configured with appropriate IAM permissions.
- SSH key pair for EC2 instance access.

### Steps:
1. **VPC Setup**:
   - Create a VPC with CIDR `10.0.0.0/16`.
   - Create public and private subnets across two AZs.
   - Attach an Internet Gateway to the VPC.
   - Configure route tables:
     - Public route table directs traffic to the Internet Gateway.
     - Private route table directs traffic to the NAT Gateway.

2. **Security Configurations**:
   - Create Security Groups for ALB, Bastion Host, EC2 instances, and RDS as described above.
   - Set up NACLs to allow inbound/outbound traffic in public subnets.

3. **Launch EC2 Instances**:
   - **Bastion Host**: Deploy in a public subnet with SSH access.
   - **Private EC2 Instance**: Deploy in a private subnet; install Node.js app and connect to RDS.

4. **Create RDS Database**:
   - Launch PostgreSQL in a private subnet with the security group allowing traffic from private EC2 instances.

5. **Configure Auto Scaling**:
   - Create an AMI from the configured private EC2 instance.
   - Define a launch template using the AMI.
   - Set up ASG with min=1, desired=1, max=4 instances across private subnets.

6. **Deploy Application Load Balancer**:
   - Attach the ALB to the ASG and configure listeners for HTTP/HTTPS.

7. **Set Up CloudWatch Alarms**:
   - Create alarms for CPU utilization thresholds (60% for scaling out, 30% for scaling in).

---

## Validation & Testing

1. **Application Accessibility**:
   - Access the app via the ALB DNS name (e.g., `http://ALB-DNS-NAME`).
   - Ensure direct EC2 instance access is blocked (test via SSH to private instance IP).

2. **Auto Scaling**:
   - Simulate load using Apache Bench:  
     ```bash
     ab -n 100000 -c 500 http://ALB-DNS-NAME/
     ```
   - Verify ASG scales out to 3 instances when CPU > 60% and scales back to 1 when CPU < 30%.

3. **CloudWatch Alarms**:
   - Confirm alarms trigger email notifications when thresholds are breached.

---

## Troubleshooting
- **SSH to Private Instances**: Use the Bastion Host as a jump server.
- **Unhealthy Instances**: Check EC2 user data scripts to ensure the Node.js service starts on boot.
- **Database Connectivity**: Verify security group rules and RDS endpoint configuration.

---

## Conclusion
This architecture provides a resilient, secure, and cost-effective solution for high-availability applications. It adheres to AWS best practices and can be extended with additional services like WAF, S3, or Lambda for future enhancements.

## Team Members
- Rabbi Agyei
- Akwasi Osei Frimpong
- Freda Esi Egyir
