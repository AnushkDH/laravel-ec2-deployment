# Laravel Deployment Commands — EC2 Ubuntu

---

## PART 1 — EVERY LARAVEL DEPLOYMENT (Do this every time, any project)

These steps are required regardless of which Laravel project you are deploying.

---

### Step 1 — Update System
```bash
sudo apt update && sudo apt upgrade -y
```

---

### Step 2 — Install Nginx (Web Server)
```bash
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

### Step 3 — Install PHP + Required Extensions
```bash
# Check available PHP version first
apt-cache show php | grep Version

# Install PHP and all extensions Laravel needs
sudo apt install php php-cli php-mbstring php-xml php-bcmath \
php-curl php-zip php-mysql php-tokenizer unzip -y

# Verify
php -v
```

---

### Step 4 — Install PHP-FPM (Connects PHP to Nginx)
```bash
# Replace 8.5 with your actual PHP version from Step 3
sudo apt install php8.5-fpm -y
sudo systemctl start php8.5-fpm
sudo systemctl enable php8.5-fpm
```

---

### Step 5 — Install Composer (PHP Package Manager)
```bash
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer

# Verify
composer --version
```

---

### Step 6 — Install Node.js + npm (Frontend Assets)
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs

# Verify
node -v && npm -v
```

---

### Step 7 — Install MySQL (Database)
```bash
sudo apt install mysql-server -y
sudo systemctl start mysql
sudo systemctl enable mysql

# Verify
mysql --version
```

---

## PART 2 — PROJECT SPECIFIC (Laracoffee — Do this once per project)

These steps are specific to this project. Values like database name,
username and password will change per project.

---

### Step 8 — Create Database and User
```bash
sudo mysql
```
Inside MySQL shell:
```sql
CREATE DATABASE laracoffee;
CREATE USER 'larauser'@'localhost' IDENTIFIED BY 'Laravel@123';
GRANT ALL PRIVILEGES ON laracoffee.* TO 'larauser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

---

### Step 9 — Clone the Repository
```bash
cd /root
git clone https://github.com/snykk/Laracoffee.git
cd Laracoffee
```

---

### Step 10 — Install PHP Dependencies
```bash
composer install
```

---

### Step 11 — Install Node Dependencies
```bash
npm install
```

---

### Step 12 — Configure Environment File
```bash
cp .env.example .env
nano .env
```
Update these values inside .env:
```
DB_DATABASE=laracoffee
DB_USERNAME=larauser
DB_PASSWORD=Laravel@123
```
Save: Ctrl+X → Y → Enter

---

### Step 13 — Generate App Key
```bash
php artisan key:generate
```

---

### Step 14 — Create Storage Symlink
```bash
php artisan storage:link
```

---

### Step 15 — Run Migrations and Seeders
```bash
php artisan migrate
php artisan db:seed
```

---

### Step 16 — Set File Permissions
```bash
chmod -R 755 /root
sudo chown -R www-data:www-data /root/Laracoffee/storage
sudo chown -R www-data:www-data /root/Laracoffee/bootstrap/cache
```

---

### Step 17 — Configure Nginx
```bash
sudo nano /etc/nginx/sites-available/laracoffee
```
Paste this config:
```nginx
server {
    listen 80;
    server_name _;
    root /root/Laracoffee/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";

    index index.php;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.5-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}
```
Save: Ctrl+X → Y → Enter

---

### Step 18 — Enable Site and Restart Nginx
```bash
# Enable the site
sudo ln -s /etc/nginx/sites-available/laracoffee /etc/nginx/sites-enabled/

# Remove default site to avoid port 80 conflict
sudo rm /etc/nginx/sites-enabled/default

# If Apache is running and blocking port 80, stop it
sudo systemctl stop apache2
sudo systemctl disable apache2

# Test Nginx config
sudo nginx -t

# Restart services
sudo systemctl restart nginx
sudo systemctl restart php8.5-fpm
```

---

### Step 19 — Verify All Services are Running
```bash
sudo systemctl is-enabled nginx
sudo systemctl is-enabled php8.5-fpm
sudo systemctl is-enabled mysql
```
All three should return: enabled

---

### Step 20 — Access the App
Open browser and go to:
```
http://<your-ec2-public-ip>
```
No port number needed. Port 80 is default HTTP.

Admin login credentials (seeded):
- Email: najibfikri13@gmail.com
- Password: 1234

---

## QUICK REFERENCE — What Each Tool Does

| Tool | Job |
|---|---|
| Nginx | Web server — receives browser requests on port 80 |
| PHP-FPM | Processes PHP files — connected to Nginx via socket |
| PHP extensions | Libraries Laravel needs to run (database, encryption etc.) |
| Composer | PHP package manager — installs Laravel dependencies |
| Node.js + npm | Installs frontend dependencies, builds CSS/JS assets via Vite |
| MySQL | Database — stores users, products, orders |

---

## NOTE — php artisan serve vs Nginx

| | php artisan serve | Nginx + PHP-FPM |
|---|---|---|
| Use for | Quick local testing only | Actual deployment |
| Survives terminal close | No | Yes |
| Survives reboot | No | Yes |
| Interview acceptable | No | Yes |

`php artisan serve` is only used as a sanity check to confirm
the app works before setting up the real web server.
