# Zabbix Installation Guide (Beginner)

## Step 1: Update Server
```bash
sudo apt update && sudo apt upgrade -y
Step 2: Install Nginx & PHP
bash
Copy code
sudo apt install -y nginx php-fpm php-mysql php-gd php-xml php-bcmath php-mbstring
Step 3: Install Zabbix
bash
Copy code
sudo apt install -y zabbix-server-mysql zabbix-frontend-php zabbix-nginx-conf zabbix-agent
Step 4: Start Services
bash
Copy code
sudo systemctl enable --now nginx zabbix-server zabbix-agent php8.4-fpm
Step 5: Open Web UI
Open browser:

arduino
Copy code
http://<Server_IP>/zabbix
