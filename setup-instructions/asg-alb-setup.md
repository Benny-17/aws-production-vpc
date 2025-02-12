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

2️⃣ Create an Auto Scaling Group
Attach the Launch Template
Select Private Subnets
Set Minimum Instances = 2, Maximum = 4
Attach to an existing Target Group
3️⃣ Create an ALB
Go to Load Balancer Dashboard → Create ALB
Select Public Subnets
Attach ALB Security Group
Create a Target Group and Register ASG instances

### **4️⃣ `bastion-host.md` → Bastion Host Setup & SSH Access**  
**What to include:**  
- **Launch a Bastion Host in a Public Subnet**  
- **Connect to Bastion via SSH (MobaXterm)**  
- **Use the Bastion to SSH into private instances**  

📌 **Example Content for `bastion-host.md`**  
# Bastion Host Setup

## 1️⃣ Launch a Bastion Host
- **Subnet:** Public Subnet
- **Security Group:** Bastion Host Security Group
- **Key Pair:** Use the same key pair as other instances

## 2️⃣ Connect to Bastion Host (from your local machine)

ssh -i your-key.pem ubuntu@<BASTION-PUBLIC-IP>

3️⃣ SSH into Private Instances from Bastion Host

ssh -i your-key.pem ubuntu@10.0.10.226

### **5️⃣ `private-server-setup.md` → Testing Private Server & NAT Gateway**  
**What to include:**  
- **Create a test file inside private instances**  
- **Run a Python HTTP server on port 8000**  
- **Test connectivity via ALB**  

📌 **Example Content for `private-server-setup.md`**  

# Private Server Setup & Testing

## 1️⃣ Create a Test File

echo "Hello from Private Server" > index.html

2️⃣ Run a Simple Python HTTP Server

python3 -m http.server 8000

3️⃣ Test Connectivity
From the Bastion Host, test if it's running:

curl http://10.0.10.226:8000
From the Internet, test ALB:
arduino
Copy
Edit
http://your-alb-dns-name


## **🚀 Next Steps**
1️⃣ **Copy & Paste these files into your GitHub repository.**  
2️⃣ **Update the AWS details with your actual values.**  
3️⃣ **Push the repo to GitHub and share the link!**  
