# Zabbix Installation Guide (Beginner Friendly)

This document explains **how to install Zabbix step by step** on an Ubuntu server.
It is written for **absolute beginners**.

If you can copy and paste commands, you can complete this installation.

---

## 1️⃣ Prerequisites (Before You Start)

Before starting, make sure you have:

- Ubuntu Server (20.04 / 22.04)
- Sudo or root access
- Internet connection
- A public IP (Azure VM or any cloud VM)

Check internet connectivity:

ping -c 3 google.com
If you get replies, internet is working ✅

2️⃣ Step 1: Update the Server
Why?
Updating ensures the system is secure and avoids package issues.

Command:

sudo apt update && sudo apt upgrade -y
Wait until it finishes.

3️⃣ Step 2: Install Nginx and PHP
Why?
Nginx serves the Zabbix web interface

PHP runs the Zabbix UI

Command:

sudo apt install -y nginx php-fpm php-mysql php-gd php-xml php-bcmath php-mbstring
Check if Nginx is running:


systemctl status nginx
You should see:


Active: active (running)
Press q to exit.

4️⃣ Step 3: Install Zabbix Packages
What this installs:
Zabbix Server

Zabbix Web Frontend

Zabbix Agent

Nginx configuration for Zabbix

Command:

sudo apt install -y zabbix-server-mysql zabbix-frontend-php zabbix-nginx-conf zabbix-agent
Let the installation complete without interruption.

5️⃣ Step 4: Start and Enable Required Services
Why?
Start services now

Automatically start after reboot

Command:

sudo systemctl enable --now nginx
sudo systemctl enable --now zabbix-server
sudo systemctl enable --now zabbix-agent
sudo systemctl enable --now php8.4-fpm
Check service status (optional):


systemctl status zabbix-server
systemctl status php8.4-fpm
6️⃣ Step 5: Open Zabbix Web Interface
Important:
Make sure port 80 (HTTP) is allowed in:

Firewall

Azure Network Security Group (NSG)

Open browser and visit:

http://<YOUR_SERVER_PUBLIC_IP>/zabbix
Example:


http://20.xxx.xxx.xxx/zabbix
7️⃣ Step 6: Zabbix Web Setup Wizard
Follow the on-screen wizard:

Welcome page → Click Next

Check of pre-requisites → All should be OK

Database configuration → Use default values

Zabbix server details → Click Next

Summary → Click Finish

8️⃣ Step 7: Login to Zabbix
After setup, login using:


Username: Admin
Password: zabbix
⚠️ Change password later for security.

✅ Installation Completed Successfully
If you can see:

Zabbix dashboard

No installation error

Menu on the left side

Then Zabbix is installed correctly 🎉

📌 Next Step

After installation:

Fix PHP deprecated warning (see troubleshooting.md)

Add first monitored host
