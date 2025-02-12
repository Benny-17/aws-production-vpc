asg-alb-setup.md → Auto Scaling Group (ASG) & ALB Setup
What to include:

Create a Launch Template with EC2 AMI, Instance Type, Key Pair, Security Group
Set Up an Auto Scaling Group (ASG) in Private Subnets
Create an ALB in Public Subnets
Attach the ALB to a Target Group

📌 Example Content for asg-alb-setup.md
# Auto Scaling Group (ASG) & Application Load Balancer (ALB) Setup

## 1️⃣ Create a Launch Template
- Go to **EC2 Dashboard** → Launch Templates → **Create Template**
- **AMI:** Ubuntu 22.04
- **Instance Type:** t2.micro
- **Key Pair:** Choose an existing one or create a new one
- **Security Group:** Use `Private Server Security Group`
- **User Data Script (Optional):**
 
  #!/bin/bash
  sudo apt update -y
  sudo apt install -y apache2
  echo "Hello from $(hostname)" > /var/www/html/index.html
  sudo systemctl restart apache2

## 2️⃣ Create an Auto Scaling Group
Attach the Launch Template
Select Private Subnets
Set Minimum Instances = 2, Maximum = 4
Attach to an existing Target Group
## 3️⃣ Create an ALB
Go to Load Balancer Dashboard → Create ALB
Select Public Subnets
Attach ALB Security Group
Create a Target Group and Register ASG instances

