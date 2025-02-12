📂 setup-instructions/
1️⃣ vpc-setup.md → VPC, Subnets & Routing Setup
What to include:

Create a VPC (CIDR: 10.0.0.0/16)
Create Public & Private Subnets (across two Availability Zones)
Attach an Internet Gateway (IGW) to the VPC
Create Route Tables:
Public Route Table → Associate Public Subnets & Route to IGW
Private Route Table → Associate Private Subnets & Route to NAT Gateway
Create NAT Gateways (one per AZ) in Public Subnets
📌 Example Content for vpc-setup.md

md
Copy
Edit
# VPC Setup for Production Environment

## 1️⃣ Create a VPC
- Go to AWS **VPC Dashboard** → **Create VPC**
- CIDR Block: `10.0.0.0/16`
- Name: `Production-VPC`

## 2️⃣ Create Subnets
- **Public Subnets:**  
  - `10.0.1.0/24` (AZ1)  
  - `10.0.2.0/24` (AZ2)  
- **Private Subnets:**  
  - `10.0.10.0/24` (AZ1)  
  - `10.0.20.0/24` (AZ2)  

## 3️⃣ Set Up Internet Gateway
- Attach **IGW** to `Production-VPC`
- Update **Public Route Table** to route `0.0.0.0/0 → IGW`

## 4️⃣ Set Up NAT Gateway
- Create **NAT Gateway** in each public subnet
- Update **Private Route Table** to route `0.0.0.0/0 → NAT Gateway`
