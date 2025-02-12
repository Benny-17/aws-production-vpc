bastion-host.md → Bastion Host Setup & SSH Access
🔹 What It Does
Acts as a jump server to access private instances.
Placed in the public subnet with a public IP.
Only allows SSH access from your local machine’s IP.
🛠 Steps to Set Up a Bastion Host

1️⃣ Launch the Bastion Host Instance
Go to AWS EC2 Dashboard → Launch Instance
AMI: Ubuntu 22.04
Instance Type: t2.micro (Free Tier)
Subnet: Choose a Public Subnet
Enable Auto-assign Public IP
Security Group:
Allow SSH (22) from your public IP
Allow outbound traffic to all

2️⃣ Connect to Bastion Host from Your Local Machine
Once the instance is running, connect to it using MobaXterm or Terminal:

ssh -i your-key.pem ubuntu@<BASTION-PUBLIC-IP>
