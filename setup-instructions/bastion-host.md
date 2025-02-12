### **`bastion-host.md` → Bastion Host Setup & SSH Access**  
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

