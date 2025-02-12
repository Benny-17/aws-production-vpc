security-groups.md → Security Group Configurations

What to include:

ALB Security Group: Allows HTTP/HTTPS from anywhere.
Bastion Host Security Group: Allows SSH from your IP only.
Private Server Security Group:
Allows inbound traffic only from ALB on port 80.
Allows SSH only from the Bastion Host.

📌 Example Content for security-groups.md
# Security Groups Configuration

## 1️⃣ ALB Security Group
- **Inbound Rules:**
  - Allow HTTP (80) from `0.0.0.0/0`
  - Allow HTTPS (443) from `0.0.0.0/0`
- **Outbound Rules:** Allow all traffic

## 2️⃣ Bastion Host Security Group
- **Inbound Rules:**
  - Allow SSH (22) from `YOUR_IP`
- **Outbound Rules:** Allow all traffic

## 3️⃣ Private Server Security Group
- **Inbound Rules:**
  - Allow HTTP (80) from ALB's Security Group
  - Allow SSH (22) from Bastion Host's Security Group
- **Outbound Rules:** Allow all traffic
