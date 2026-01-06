# Zabbix Installation Steps

This document explains how Zabbix was installed on the Azure VM.

---

## Step 1: Update the System

```bash

sudo apt update && sudo apt upgrade -y
Step 2: Install Zabbix Repository

wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-4+ubuntu22.04_all.deb
sudo dpkg -i zabbix-release_6.0-4+ubuntu22.04_all.deb
sudo apt update
Step 3: Install Zabbix Server, Agent & Frontend

sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-agent -y

Step 4: Install MySQL

sudo apt install mysql-server -y
sudo mysql_secure_installation


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


Key setting:

DBPassword=StrongPassword
PHP Configuration for Zabbi

File:

/etc/zabbix/nginx.conf
Timezone setting:


php_value[date.timezone] = Asia/Dhaka


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


sudo systemctl status zabbix-server
Verify database password in config file

PHP Warnings in UI
Confirm correct PHP timezone

Restart services after configuration changes


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

sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-agent -y
Service Management

sudo systemctl restart zabbix-server zabbix-agent nginx mysql
sudo systemctl enable zabbix-server zabbix-agent nginx mysql


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
