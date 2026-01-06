# Troubleshooting Guide

This document describes common issues encountered during the Zabbix setup
and how they were resolved.

---

## 🐞 Issue: PHP Deprecated Warning in Zabbix UI

### ❗ Problem

Zabbix Web UI displayed the following warning message:

session_set_save_handler(): deprecated

yaml
Copy code

This warning appeared on the dashboard and affected UI cleanliness.

---

### 🔍 Cause

- The installed **PHP version was newer** than the version expected by Zabbix
- Zabbix uses a **separate PHP-FPM pool**, so global PHP settings did not apply

---

### 🛠️ Solution

A **pool-level PHP override** was applied for the Zabbix PHP-FPM pool.

#### Step 1: Update Zabbix PHP-FPM Pool Configuration

```bash
sudo tee -a /etc/php/8.4/fpm/pool.d/zabbix.conf <<'EOF'
php_admin_value[error_reporting] = E_ALL & ~E_DEPRECATED & ~E_STRICT
php_admin_flag[display_errors] = off
EOF
Step 2: Restart Required Services
bash
Copy code
sudo systemctl restart php8.4-fpm
sudo systemctl restart nginx
✅ Result
Deprecated PHP warning removed

Zabbix dashboard displayed cleanly

No impact on monitoring functionality

📝 Notes
Pool-level configuration ensures changes apply only to Zabbix

Global PHP settings remain unaffected

This approach is recommended for production-like environments
