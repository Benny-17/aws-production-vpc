private-server-setup.md → Connecting & Testing Private Server
🔹 What It Does
Private servers don’t have public IPs.
Can only be accessed via the Bastion Host.
Can connect to the internet using a NAT Gateway.
🛠 Steps to Access & Test Private Server

1️⃣ Connect to Private Instance via Bastion
Once inside the Bastion Host, use SSH to access a private instance:

ssh -i your-key.pem ubuntu@<PRIVATE-IP>

📌 Example: If your private server’s IP is 10.0.10.226, use:

ssh -i your-key.pem ubuntu@10.0.10.226

2️⃣ Verify Private Server Connectivity
Inside the private instance, check network connectivity:

ping google.com  # If using NAT Gateway, this should work

3️⃣ Run a Simple Web Server on Private Server
In your private instance, create a test page:

echo "Hello from Private Server" > index.html

Start a basic Python web server:

python3 -m http.server 8000

Check if it’s running:

curl http://localhost:8000
4️⃣ Test ALB Routing
Copy your ALB DNS name from AWS.
Paste it into your browser (http://your-alb-dns-name).
You should see: "Hello from Private Server".
