# AWS Cloud Projects

This repository contains a collection of hands-on AWS infrastructure projects demonstrating proficiency with core AWS services. Each project showcases real-world cloud engineering skills applicable to production environments.

## Projects Overview

### 1. Serverless Web Application
**Description:** Multi-tier serverless web application using AWS Lambda, API Gateway, DynamoDB, and S3 for static hosting.  
**Technologies:** Lambda, API Gateway, DynamoDB, S3, CloudFront, Route 53  
**Key Features:**
- Serverless backend API with Lambda functions
- NoSQL database interaction with DynamoDB
- Global content delivery with CloudFront
- Custom domain configuration with Route 53
- CI/CD pipeline for automated deployments

### 2. Two and Three-Tier Web Architecture
**Description:** Scalable web application infrastructure with load balancing, auto-scaling, and high availability.  
**Technologies:** EC2, VPC, ELB, Auto Scaling, RDS, Security Groups  
**Key Features:**
- Load-balanced web tier with EC2 instances
- Private application tier with custom AMIs
- Multi-AZ RDS database for high availability
- Secure network architecture with proper subnet isolation
- Infrastructure as Code deployment with CloudFormation

### 3. Containerized Microservices Platform
**Description:** Microservices architecture deployed using containers with orchestration.  
**Technologies:** ECS, ECR, Fargate, CloudWatch, Application Load Balancer  
**Key Features:**
- Containerized services with Docker
- CI/CD pipeline for container builds and deployments
- Service discovery and routing
- Container monitoring and logging
- Autoscaling based on demand patterns

### 4. Data Processing Pipeline
**Description:** Automated data ingestion, transformation, and analysis pipeline.  
**Technologies:** S3, Lambda, Kinesis, Glue, Athena, QuickSight  
**Key Features:**
- Event-driven data processing with Lambda triggers
- Stream processing with Kinesis
- Data transformation with AWS Glue
- Data cataloging and SQL querying with Athena
- Visualization dashboards with QuickSight

### 5. Disaster Recovery Solution
**Description:** Cross-region disaster recovery setup with automated failover.  
**Technologies:** Route 53, CloudFormation, S3 Cross-Region Replication, DynamoDB Global Tables  
**Key Features:**
- Multi-region infrastructure deployment
- Automated backup and recovery procedures
- Data replication across regions
- Failover routing policies
- Recovery time objective (RTO) and recovery point objective (RPO) measurements

### 6. Infrastructure Monitoring System
**Description:** Comprehensive monitoring and alerting solution for AWS resources.  
**Technologies:** CloudWatch, SNS, Lambda, EventBridge, X-Ray  
**Key Features:**
- Custom CloudWatch dashboards
- Automated alerting with SNS
- Cost optimization monitoring
- Performance metrics and anomaly detection
- Tracing with X-Ray for distributed applications

### 7. Secure Static Website with CI/CD Pipeline
**Description:** Static website with secure hosting and automated deployment pipeline.  
**Technologies:** S3, CloudFront, AWS Certificate Manager, CodePipeline, GitHub Actions  
**Key Features:**
- S3 website hosting with proper bucket policies
- HTTPS implementation with ACM
- Content distribution with CloudFront
- Automated deployment from GitHub
- Custom error pages and redirects

### 8. Hybrid Cloud Connection
**Description:** Connection between on-premises network and AWS cloud resources.  
**Technologies:** VPC, Direct Connect, Site-to-Site VPN, Transit Gateway  
**Key Features:**
- Secure connectivity between environments
- Network address translation
- Routing configurations
- Security group and NACL implementations
- Hybrid DNS resolution

### 9. Serverless ETL Process
**Description:** Extract, transform, load process using serverless technologies.  
**Technologies:** Lambda, Step Functions, S3, DynamoDB, Glue  
**Key Features:**
- Orchestrated workflows with Step Functions
- Parallel processing of large datasets
- Error handling and retry logic
- Parameter passing between workflow steps
- Scheduled and event-driven execution

### 10. Cloud Security Compliance Framework
**Description:** Implementation of security best practices and compliance controls.  
**Technologies:** IAM, AWS Config, Security Hub, GuardDuty, CloudTrail, KMS  
**Key Features:**
- Least privilege access with IAM
- Resource compliance monitoring with AWS Config
- Security findings aggregation with Security Hub
- Threat detection with GuardDuty
- Audit trailing with CloudTrail
- Data encryption with KMS

## Repository Structure

Each project is contained in its own directory with the following structure:
```
project-name/
├── README.md           # Project description, architecture diagram, and instructions
├── infrastructure/     # IaC templates (CloudFormation, Terraform, etc.)
├── src/                # Application source code if applicable
├── scripts/            # Utility scripts for deployment and management
└── docs/               # Additional documentation, including architecture diagrams
```

## Getting Started

To explore any project:

1. Navigate to the project directory
2. Read the project-specific README.md for detailed information
3. Follow the setup instructions to deploy the project to your own AWS account

## Prerequisites

- AWS account with appropriate permissions
- AWS CLI configured with access credentials
- Basic knowledge of AWS services and cloud concepts
- Git installed on your local machine

## AWS Cloud Projects

1. **[Serverless Web Application](serverless-web-application/)**  
   [infrastructure](serverless-web-application/infrastructure/) • 
   [src](serverless-web-application/src/) • 
   [scripts](serverless-web-application/scripts/) • 
   [docs](serverless-web-application/docs/)

2. **[Two-Tier Architecture](two-tier-architecture/)**  
   [infrastructure](two-tier-architecture/infrastructure/) • 
   [src](two-tier-architecture/src/) • 
   [scripts](two-tier-architecture/scripts/) • 
   [docs](two-tier-architecture/docs/)

3. **[Three-Tier Architecture](three-tier-architecture/)**  
   [infrastructure](three-tier-architecture/infrastructure/) • 
   [src](three-tier-architecture/src/) • 
   [scripts](three-tier-architecture/scripts/) • 
   [docs](three-tier-architecture/docs/)

... (pattern continues for all 10 projects)


## Contribution Guidelines

Contributions are welcome! Please feel free to submit a Pull Request.


