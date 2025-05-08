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
    
![ec2 creation 1 (lamp_server)](https://github.com/user-attachments/assets/6dd1627f-9cb4-4346-afd2-d6b14134e0cf)

### 2. SSH into Server
- SSH into the instance using `class2-publickey.pem` key.
```bash
chmod 400 class2-publickey.pem
ssh -i class2-publickey.pem ubuntu@<16.171.240.231>
```
![SSH -i](https://github.com/user-attachments/assets/1db288a2-3c71-4874-a2fa-84fedd004687)

### 3. Install LAMP Components

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 -y
sudo apt install mysql-server -y
sudo apt install php libapache2-mod-php php-mysql -y
```
![Apache server](https://github.com/user-attachments/assets/f6687b3a-53a0-471c-9e91-6c2245ff1c4b)

![my Apache2 default page](https://github.com/user-attachments/assets/9010277c-0e0e-4e55-8c05-ea5ac857cc08)

![PHP running](https://github.com/user-attachments/assets/78fd2430-973f-49a0-8d20-28e8e0ae35fe)

![PHP default page](https://github.com/user-attachments/assets/ed0ab93e-8067-4c32-aae4-8636433361fc)

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
![user,privilege etc](https://github.com/user-attachments/assets/787b1600-a7ea-4a9a-9c19-3a6818b661bb)

Then login with:

```bash
mysql -u devops_user -p
```
![sql login](https://github.com/user-attachments/assets/ddaa36d0-4ed1-4e14-bd50-58c4f42b74a1)

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
![HTML DOC](https://github.com/user-attachments/assets/35a141f2-b193-402b-8bce-daac5597bfd8)

Save as: `/var/www/html/index.html`

![I-Love-DevOps--05-08-2025_05_48_PM](https://github.com/user-attachments/assets/868b0ab9-9175-40aa-9ebd-ac65a880e0f1)

## Author

Ani Chidimma

Medium Documentary: https://medium.com/@chidimma516/how-i-deployed-a-full-lamp-stack-on-aws-ec2-with-a-custom-web-page-0e20d98ab6c8
