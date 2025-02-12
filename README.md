# aws-production-vpc
A production-ready AWS VPC with Auto Scaling, Load Balancer, Bastion Host, and NAT Gateway.


AWS Production-Ready VPC with ASG, ALB & Bastion Host
This project demonstrates how to set up a secure, scalable, and highly available AWS environment using the AWS Management Console (manual setup). It follows best practices for networking, security, and resiliency, making it suitable for production workloads.

📌 What This Project Covers
This setup includes:
✅ Virtual Private Cloud (VPC) with public and private subnets across two Availability Zones (AZs)
✅ Auto Scaling Group (ASG) in private subnets to ensure scalability & high availability
✅ Application Load Balancer (ALB) in public subnets to distribute traffic to backend servers
✅ Bastion Host (Jump Server) in a public subnet for secure SSH access to private instances
✅ NAT Gateway in both AZs for internet access from private instances
✅ Strict Security Group configurations following least privilege access principles
✅ Python-based HTTP server on private instances for testing connectivity

🛠️ How This Was Built (Manual Setup Process)
1️⃣ VPC Creation
Created a VPC with two public and two private subnets (spread across two AZs).
Configured route tables:
Public subnets → Internet Gateway (IGW) for external access.
Private subnets → NAT Gateway (NGW) for secure outbound internet access.
2️⃣ Auto Scaling Group (ASG) & Launch Template
Created an EC2 Launch Template with:
AMI (Amazon Linux 2/Ubuntu)
Instance type (e.g., t2.micro)
Security groups and key pair
Configured an Auto Scaling Group (ASG) to launch instances only in private subnets.
3️⃣ Application Load Balancer (ALB) & Target Group
Deployed an Application Load Balancer (ALB) in public subnets.
Created a Target Group and registered private instances to receive traffic from ALB.
4️⃣ Bastion Host (Jump Server) Setup
Launched a Bastion Host in a public subnet to access private instances securely.
Used MobaXterm for SSH access.
Fixed private key permissions for security:

chmod 400 my-key.pem
5️⃣ Connecting to Private Instances & Running a Test Web Server
SSH’d into private instances from the Bastion Host:

ssh -i my-key.pem ubuntu@<private-instance-IP>
Created a test file in a private instance.
Ran a simple Python HTTP server to test connectivity:

python3 -m http.server 8000
6️⃣ Security Configurations
✅ ALB Security Group: Allows HTTP/HTTPS (80/443) from anywhere.
✅ Private Server Security Group: Allows traffic only from ALB on port 80.
✅ Bastion Host Security Group: Allows SSH (22) only from a specific IP.

📌 Next Steps / Improvements
🔹 Automate this setup using Terraform, AWS CLI, or CloudFormation
🔹 Deploy a real-world web application instead of a test Python server
🔹 Set up monitoring with CloudWatch, AWS Config, and AWS GuardDuty
🔹 Implement IAM Role-based access control for better security

📷 Architecture Diagram 
![image](https://github.com/user-attachments/assets/fa852645-d694-4396-8570-699274880f95)

🎯 Why This Project is Useful?
✅ Demonstrates AWS VPC networking, security, and high availability
✅ Great for DevOps, Cloud Engineer, or AWS Solution Architect roles
✅ Can be used as a foundation for real-world applications

📢 How to Use This Repository?
1️⃣ Clone the repository:
git clone https://github.com/your-github-username/aws-production-vpc.git
cd aws-production-vpc

2️⃣ Follow the setup-instructions folder for step-by-step guides.
3️⃣ Deploy your own secure & scalable AWS infrastructure! 🚀

