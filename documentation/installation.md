# Zabbix Installation Steps

This document explains how Zabbix was installed on the Azure VM.

---

## Step 1: Update the System

```bash
sudo apt update && sudo apt upgrade -y
Step 2: Install Zabbix Repository
bash
Copy code
wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-4+ubuntu22.04_all.deb
sudo dpkg -i zabbix-release_6.0-4+ubuntu22.04_all.deb
sudo apt update
Step 3: Install Zabbix Server, Agent & Frontend
bash
Copy code
sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-agent -y
Step 4: Install MySQL
bash
Copy code
sudo apt install mysql-server -y
sudo mysql_secure_installation
yaml
Copy code

---

## 4️⃣ `documentation/configuration-details.md`

```md
# Configuration Details

This document contains important configuration settings used in this project.

---

## Zabbix Server Configuration

File:
/etc/zabbix/zabbix_server.conf

go
Copy code

Key setting:
```ini
DBPassword=StrongPassword
PHP Configuration for Zabbix
File:

bash
Copy code
/etc/zabbix/nginx.conf
Timezone setting:

ini
Copy code
php_value[date.timezone] = Asia/Dhaka
yaml
Copy code

---

## 5️⃣ `documentation/troubleshooting.md`

```md
# Troubleshooting Guide

Common issues faced during setup and their solutions.

---

## Zabbix Web UI Not Loading

- Check Nginx status:
```bash
sudo systemctl status nginx
Ensure port 80 is open in Azure NSG

Zabbix Server Not Running
Check service status:

bash
Copy code
sudo systemctl status zabbix-server
Verify database password in config file

PHP Warnings in UI
Confirm correct PHP timezone

Restart services after configuration changes

yaml
Copy code

---

## 6️⃣ `documentation/commands-used.md`

```md
# Commands Used

This document lists all important commands used during the project.

---

## System Update

```bash
sudo apt update
sudo apt upgrade -y
Zabbix Installation
bash
Copy code
sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-agent -y
Service Management
bash
Copy code
sudo systemctl restart zabbix-server zabbix-agent nginx mysql
sudo systemctl enable zabbix-server zabbix-agent nginx mysql
yaml
Copy code

---

## 7️⃣ `documentation/learning-summary.md`

```md
# Learning Summary

This document summarizes what was learned from this project.

---

## Key Learnings

- Azure VM provisioning and networking
- Linux system administration basics
- Zabbix server and agent architecture
- Monitoring concepts (items, triggers, dashboards)
- Writing professional technical documentation

---

## Outcome

This project strengthened both **technical skills** and **documentation skills**,
making it suitable for portfolio and interview discussion.
