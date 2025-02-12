### ** `private-server-setup.md` → Testing Private Server & NAT Gateway**  
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

http://your-alb-dns-name


## **Important**
1️⃣ **Update the AWS details with your actual values.**  
