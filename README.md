# 🚀 LAMP Stack Setup on AWS EC2 with a Custom Webpage

## 📌 Project Overview
This project demonstrates how to set up a LAMP (Linux, Apache, MySQL, PHP) stack on an AWS EC2 instance. The final deliverable is a hosted webpage displaying the message: **"I Love DevOps"**. 
---

## ⚙️ Technologies Used
- AWS EC2 (Ubuntu 20.04 LTS), t3.micro (free tier)
- Apache2 (Web Server)
- MySQL (Database)
- PHP (Scripting Language)
- HTML (Web Page)
---

## 🧰 Steps to Reproduce

### 1. **Launch EC2 Instance**
- AWS EC2 Ubuntu 20.04 instance created (lamp_server)
- Security Group configured to allow ports:
  - 22 (SSH) 0.0.0.0/0
  - 80 (HTTP) 0.0.0.0/0
  - 443 (HTTPS) 0.0.0.0/0

- SSH into the instance using `class2-publickey.pem` key.
```bash
ssh -i class2-publickey.pem ubuntu@16.171.240.231

### 2. **Update system and Install Apache Web Server**
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y

### 3. **sudo apt install mysql-server -y**

### 4. **sudo apt install php libapache2-mod-php php-mysql -y**

### 5.  **Secure MySQL**
sudo mysql_secure_installation

### 6. **Create & Login as SQL User**
CREATE USER 'devops_user'@'localhost' IDENTIFIED BY 'StrongP@ssw0rd!';
GRANT ALL PRIVILEGES ON *.* TO 'devops_user'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;

Then login with:
mysql -u devops_user -p



