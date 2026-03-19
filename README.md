# 📘 WordPress Hosting Automation using Ansible

## 📌 Project Overview

This project demonstrates how to automate the deployment of a secure **WordPress hosting environment** on a Linux server using **Ansible**.

The setup includes:
- Nginx Web Server  
- PHP 8+  
- MariaDB (MySQL 10.6 compatible)  
- SFTP Configuration  
- phpMyAdmin Setup  
- SSL using Let’s Encrypt  
- WordPress Deployment  

---

## 🎯 Objectives

- Automate server setup using Ansible  
- Configure a user-based web directory  
- Enable secure file transfer using SFTP  
- Provide database access via phpMyAdmin  
- Secure the website with HTTPS  
- Deploy and configure WordPress  
- Publish a personal blog post  

---

## 🛠️ Technologies Used

- Ansible  
- Linux (RHEL / Rocky / Ubuntu)  
- Nginx  
- PHP 8+  
- MariaDB  
- OpenSSH (SFTP)  
- phpMyAdmin  
- Certbot (Let’s Encrypt)  
- WordPress  

---

## 📁 Project Structure
ansible-wordpress-project/
├── hosts.ini
├── site.yml
├── vars.yml
├── templates/
│ ├── nginx.conf.j2
│ └── wp-config.php.j2


---

## ⚙️ Prerequisites

- Ansible installed on control node  
- Linux server (EC2 or local VM)  
- SSH access configured  
- Domain name (for SSL)  

---

## 🚀 Setup Instructions

### 1️⃣ Configure Inventory

Edit `hosts.ini`:

```ini
[webserver]
your_server_ip ansible_user=ec2-user ansible_ssh_private_key_file=~/.ssh/key.pem
2️⃣ Configure Variables

Edit vars.yml:

username: shifin
websitename: myblog
domain_name: yourdomain.com

db_name: wordpressdb
db_user: wpuser
db_password: StrongDBPassword@123

wp_admin_user: wpadmin
wp_admin_password: StrongWPPassword@123
wp_admin_email: admin@yourdomain.com
3️⃣ Run the Playbook
ansible-playbook -i hosts.ini site.ymlWhat the Playbook Does

✔ Installs required packages:

Nginx

PHP 8+

MariaDB

phpMyAdmin

Certbot

✔ Creates user and directory:

/home/username/websitename/public

✔ Configures:

Nginx virtual host

PHP-FPM

Database (MariaDB)

SFTP access

phpMyAdmin

✔ Deploys:

WordPress

✔ Enables:

HTTPS using Let’s Encrypt

🌐 Access URLs
Service	URL
Website	https://shifin.duckdns.org

phpMyAdmin	https://shifin.duckdns.org/phpmyadmin

WordPress Admin	https://yourdomain.com/wp-admin
🔐 Credentials
SFTP

Host: <your-server-ip>

Username: <username>

Password: <password>

phpMyAdmin

URL: https://yourdomain.com/phpmyadmin

Username: <db_user>

Password: <db_password>

WordPress

Admin URL: https://yourdomain.com/wp-admin

Username: <wp_admin_user>

Password: <wp_admin_password>

⚠️ Note: Do not expose real credentials in public repositories.

✅ Verification

Run the following commands:

systemctl status nginx
systemctl status php-fpm
systemctl status mariadb
systemctl status sshd

Check website:

curl -I https://shifin.duckdns.org
