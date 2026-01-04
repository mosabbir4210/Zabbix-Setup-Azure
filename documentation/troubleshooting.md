# Troubleshooting

## Issue: PHP Deprecated Warning

### Problem
Zabbix UI showed:
session_set_save_handler(): deprecated

bash
Copy code

### Cause
- PHP version newer than expected
- Zabbix uses a separate PHP-FPM pool

### Solution
Applied pool-level override:
```bash
sudo tee -a /etc/php/8.4/fpm/pool.d/zabbix.conf <<'EOF'
php_admin_value[error_reporting] = E_ALL & ~E_DEPRECATED & ~E_STRICT
php_admin_flag[display_errors] = off
EOF
Restarted services:

bash
Copy code
sudo systemctl restart php8.4-fpm
sudo systemctl restart nginx
Result
Warning removed, dashboard clean
