# static-website-on-ec2instance
## 🌐 Hosting a Static Website on AWS EC2 Using NGINX

# 📌 Overview

This guide explains how to host a **static website** (HTML, CSS, JavaScript) on an **AWS EC2 instance** using a web server such as **Apache** or **Nginx**.  
It is suitable for learning purposes, interviews, and small-scale deployments. It reflects a real-world production-like setup commonly discussed in DevOps / Cloud interviews.

# 🧰 Prerequisites

AWS Account

Basic Linux commands

SSH client

Static website files (index.html, style.css, etc.)

# 🏗️ Architecture Overview

User accesses the website via a browser

Request reaches AWS EC2 public IP / DNS

Security Group allows HTTP/HTTPS traffic

NGINX serves static content from /var/www/html

# Production-Style Architecture Diagram
```
mermaid 
flowchart TB
    User[User Browser]
    DNS[Public DNS / Elastic IP]
    SG[Security Group<br/>Port 80 / 443]
    EC2[EC2 Instance]
    NGINX[NGINX Service]
    Files[Static Content<br/>HTML / CSS / JS]

    User --> DNS
    DNS --> SG
    SG --> EC2
    EC2 --> NGINX
    NGINX --> Files
```

# ⚙️ Implementation Steps

## 1️⃣ Launch EC2 Instance

Choose Amazon Linux 2 / Ubuntu

Instance type: t2.micro (Free Tier)

Attach Security Group with HTTP & SSH access

## 2️⃣ Install NGINX

```
sudo yum update -y
sudo amazon-linux-extras install nginx1 -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

## 3️⃣ Deploy Static Website

```
cd /usr/share/nginx/html
sudo rm -rf *
sudo vi index.html
```
## 4️⃣ Access Website

```

```
## 📁 Directory Structure

```
/var/www/html
 ├── index.html
 ├── style.css
 └── assets/
```

# 🚀 Real-Life Use Case

A startup wants to host a marketing landing page quickly without managing complex infrastructure.

They use EC2 + NGINX for:
Low cost
Full server control
Easy scalability later using Load Balancer

# ❓ Real-Life Scenario Based Interview Questions

## 🔹 Scenario 1

Q: Website is not loading even though EC2 is running. What will you check?
A:

Security Group inbound rules (Port 80)

NGINX service status

Correct document root

EC2 public IP/DNS

OS firewall (iptables)

## 🔹 Scenario 2

Q: How would you make this website highly available?
A:

Use Application Load Balancer

Deploy EC2 in multiple AZs

Use Auto Scaling Group

Store static files in S3

## 🔹 Scenario 3

Q: How do you secure this setup?
A:

Restrict SSH access to specific IP

Use HTTPS with SSL (Certbot)

Harden NGINX configuration

Disable root login

## 🔹 Scenario 4

Q: Traffic suddenly increases. What do you do?
A:

Add Load Balancer

Enable Auto Scaling

Move static content to S3 + CloudFront

## 🔹 Scenario 5

Q: Why NGINX over Apache?
A:

Lightweight & faster for static content

Better concurrency handling

Lower memory footprint

# 📈 Possible Enhancements

HTTPS with Let’s Encrypt

CI/CD pipeline using GitHub Actions

S3 + CloudFront integration

Monitoring using CloudWatch

# 🧠 Key Interview Takeaways

Understand networking + security

Know NGINX basics


