Multi-Tier Web Application Re-Architecture on AWS

This project demonstrates the re-architecture of a multi-tier web application on the AWS cloud, focusing on flexibility, cost reduction, and improved operational efficiency.  The existing infrastructure, comprised of physical, virtual, and cloud machines, was migrated to a fully managed AWS environment leveraging Infrastructure as Code (IaC), Platform as a Service (PaaS), and Software as a Service (SaaS) principles.

 Project Goals

 Flexibility: Build a highly adaptable and scalable infrastructure.
 Cost Optimization: Eliminate upfront capital expenditure and optimize operational expenditure.
 Automation: Implement Infrastructure as Code (IaC) to automate deployments and management.
 Scalability & Uptime: Improve application scalability and ensure high availability.
 Agility: Enhance development and deployment agility.

 Architecture Overview

The re-architected application utilizes the following AWS services:

 Compute: EC2 (Virtual Machines for Tomcat Application Server), Elastic Beanstalk (Application hosting and management), Auto Scaling (Automating VM scaling)
 Storage: S3 (Object Storage), EFS (Elastic File System)
 Database: RDS (Relational Database Service - MySQL), Elastic Cache (Memcached for in-memory caching)
 Message Broker: Active MQ
 Networking: Route 53 (DNS), CloudFront (CDN - Content Delivery Network)
 Load Balancing: Elastic Load Balancer (ELB) / NGINX (within Beanstalk)

![image](https://github.com/user-attachments/assets/fd5e7d4a-8539-441a-809d-056b6e0cd0f2)


 Deployment Steps

1. Initial Setup:
     Log in to your AWS account.
     Create a key pair for EC2 instance access.
     Create security groups for:
         Elastic Cache
         RDS
         Active MQ

2. Database Initialization:
     Launch an EC2 instance (or use a more automated approach like a Lambda function).
     Connect to the instance and initialize the RDS database schema.

3. Elastic Beanstalk Configuration:
     Create an Elastic Beanstalk environment (e.g., Tomcat).
     Configure security groups to allow traffic:
         From the load balancer to the EC2 instances within Beanstalk.
         Between backend services within the same security group.

4. Load Balancer and Health Checks:
     Configure the Elastic Load Balancer (ELB) within Elastic Beanstalk.
     Set the health check path (e.g., `/login`).
     Configure HTTPS listener on port 443 with an SSL certificate.

5. Build and Deploy Application Artifact:
     Build the application artifact (e.g., WAR file).
     Deploy the artifact to the Elastic Beanstalk environment.

6. CDN and DNS Configuration:
     Create a CloudFront distribution.
     Configure the distribution with an SSL certificate.
     Update DNS records in GoDaddy (or your DNS provider) to point to the CloudFront distribution's domain name.

7. Testing:
     Thoroughly test the application through the CloudFront URL.

 Comparison with Existing Setup

| Component        | Existing Setup        | AWS Setup                 |
|-----------------|-----------------------|---------------------------|
| Load Balancer   | NGINX                | ELB (within Beanstalk)    |
| Scaling         | Manual                 | Auto Scaling              |
| Storage         | NFS                  | EFS/S3                    |
| Database        | MySQL on VM/EC2       | RDS (MySQL)               |
| Caching         | Memcached on VM/EC2   | Elastic Cache (Memcached) |
| Messaging       | RabbitMQ on VM/EC2    | Active MQ                 |
| DNS             | GoDaddy/Local DNS     | Route 53                  |
| CDN             | None                   | CloudFront                |

 Technologies Used

 AWS Services (as listed above)
 Tomcat (Application Server)
 MySQL (Database)
 Memcached (Caching)
 Active MQ (Message Broker)
 Java (or the application's programming language)
 GoDaddy (or other DNS provider)

 Future Enhancements

 Implement Infrastructure as Code (IaC) using tools like CloudFormation or Terraform.
 Integrate monitoring and logging solutions (e.g., CloudWatch).
 Implement CI/CD pipelines for automated deployments.
 Explore serverless technologies for specific components.

 Team

 Cloud Computing Team
 Virtualization Team
 Data Center Operations Team
 Monitoring Team
 System Administrators
![image](https://github.com/user-attachments/assets/d4b3c011-e906-427f-aae1-0f6ffcd82ff8)
![image](https://github.com/user-attachments/assets/b4429a7c-671f-4ccc-a7eb-292092bdb16a)
![image](https://github.com/user-attachments/assets/499e1a4c-a65c-4de4-9a48-2efab46588f7)
![image](https://github.com/user-attachments/assets/96b30162-fb33-4348-a56c-3cc3f3d2332c)

Outcome:
Reduced operational overhead.
Improved uptime and scalability.
Eliminated upfront CapEx, with optimized OpEx.
Automation of processes for seamless management.
