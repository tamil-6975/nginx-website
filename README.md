# Static Website Hosting on AWS EC2 with Nginx

A static website deployed on **AWS EC2** using **Nginx** web server on **Amazon Linux 2**. This project demonstrates core cloud and Linux administration skills including server setup, web server configuration, and AWS networking.

---

## Live Demo

Access the website via EC2 Public IP:
```
http://<34.229.63.117>
```

---

##  Tech Stack

| Technology | Purpose |
|-----------|---------|
| AWS EC2 (t2.micro) | Cloud virtual server |
| Amazon Linux 2 | Operating system |
| Nginx | Web server |
| HTML & CSS | Website content |
| AWS Security Groups | Network/firewall rules |

---

## Features

- Static website hosted on AWS EC2 cloud server
- Nginx web server configured to serve HTML content
- AWS Security Group configured to allow HTTP traffic on port 80
- Server accessible globally via public IP address
- Nginx auto-starts on server reboot using systemctl

---

## Architecture

```
User (Browser)
      ↓
  Internet
      ↓
AWS Security Group (Port 80 open)
      ↓
EC2 Instance (Amazon Linux 2)
      ↓
Nginx Web Server
      ↓
index.html (Website)
```

---

##  Setup Instructions

### Step 1 — Launch EC2 Instance
- Go to AWS Console → EC2 → Launch Instance
- AMI: Amazon Linux 2023 (Free tier)
- Instance type: t2.micro (Free tier)
- Create and download key pair (.pem file)

### Step 2 — Connect to EC2
```bash
ssh -i my-key.pem ec2-user@<YOUR-EC2-PUBLIC-IP>
```

### Step 3 — Install Nginx
```bash
# Update packages
sudo yum update -y

# Install Nginx
sudo yum install nginx -y

# Start Nginx
sudo systemctl start nginx

# Enable auto-start on reboot
sudo systemctl enable nginx

# Check status
sudo systemctl status nginx
```

### Step 4 — Deploy Website
```bash
# Go to Nginx web folder
cd /usr/share/nginx/html

# Edit the default page
sudo nano index.html

# Paste your HTML content and save
# Ctrl+X → Y → Enter
```

### Step 5 — Configure AWS Security Group
1. Go to EC2 → Security Groups
2. Edit Inbound Rules
3. Add Rule:
   - Type: HTTP
   - Port: 80
   - Source: 0.0.0.0/0

### Step 6 — Access Website
Open browser and visit:
```
http://<34.229.63.117>
```

---

## 📁 Project Structure

```
nginx-website/
│
├── index.html       # Main website page
└── README.md        # Project documentation
```

---

##  Useful Commands

```bash
# Check Nginx status
sudo systemctl status nginx

# Restart Nginx
sudo systemctl restart nginx

# Stop Nginx
sudo systemctl stop nginx

# View Nginx logs
sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log

# Test Nginx configuration
sudo nginx -t
```

---

## AWS Services Used

| Service | Usage |
|---------|-------|
| EC2 | Virtual server to host the website |
| Security Groups | Firewall to allow HTTP traffic |
| VPC | Network isolation for EC2 instance |
| IAM | Secure access management |

---

## Resume Bullet Points

- Deployed and configured Nginx web server on AWS EC2 (Amazon Linux 2) to host a static website accessible via public IP
- Configured AWS Security Group inbound rules to allow HTTP traffic on port 80
- Enabled Nginx auto-start using systemctl for high availability on server reboot
- Managed Linux server administration including package installation, file permissions, and service management

---

 Future Improvements

- [ ] Add a custom domain using AWS Route 53
- [ ] Enable HTTPS using AWS Certificate Manager (ACM)
- [ ] Add CloudFront CDN for faster global delivery
- [ ] Deploy using AWS CodeDeploy for CI/CD automation
- [ ] Containerize with Docker

---

Author

**Tamilarasan P**
- GitHub: [github.com/tamil-6975](https://github.com/tamil-6975)

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).
