# 🚀 LAMP Stack Setup on AWS EC2 with a Custom Webpage

## 📌 Project Overview
This project demonstrates how to set up a LAMP (Linux, Apache, MySQL(creating and logging in with a MySQL user), PHP) stack on an AWS EC2 instance. The final deliverable is a hosted webpage displaying the message: **"I Love DevOps"** .
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

### 2. SSH into Server
- SSH into the instance using `class2-publickey.pem` key.
```bash
chmod 400 class2-publickey.pem
ssh -i class2-publickey.pem ubuntu@<16.171.240.231>
```



### 3. Install LAMP Components

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y
sudo apt install mysql-server -y
sudo apt install php libapache2-mod-php php-mysql -y
```

### 4. Secure MySQL

```bash
sudo mysql_secure_installation
```

### 5. Create & Login as SQL User

```sql
CREATE USER 'devops_user'@'localhost' IDENTIFIED BY 'StrongP@ssw0rd!';
GRANT ALL PRIVILEGES ON *.* TO 'devops_user'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

Then login with:

```bash
mysql -u devops_user -p
```

### 6. Deploy Web Page (after SQL login)

```html
<!DOCTYPE html>
<html>
<head><title>I Love DevOps!</title></head>
<body style="font-family: Arial, sans-serif; text-align: center; margin-top: 100px;">
<h1 style="color: #4CAF50;">I Love DevOps!</h1>
<p>Welcome to my full stack project by Ani Chidimma</p>
</body>
</html>
```

Save as: `/var/www/html/index.html`


## Author

Ani Chidimma
Medium Documentary: https://medium.com/@chidimma516/how-i-deployed-a-full-lamp-stack-on-aws-ec2-with-a-custom-web-page-0e20d98ab6c8
