# 🚀 Simple Pterodactyl Complete Backup System

## 📋 Features
- ✅ Complete backup (Panel + Database + Wings + Configs)
- 🔄 Simple restore with menu selection
- ☁️ OneDrive auto-sync
- ⏰ Cronjob ready
- 🎨 Simple colorful menu
- 🧹 Auto cleanup old backups

---

## 🛠️ Super Simple Setup

### Step 1: Install Basic Stuff
```bash
sudo apt update
sudo apt install -y mysql-client curl
curl https://rclone.org/install.sh | sudo bash

Step 2: Setup OneDrive

rclone config

1. n


2. Name: onedrive


3. Type: 26


4. Client ID/Secret: Enter


5. Region: 1


6. Advanced: n


7. Auto config: y


8. Login in browser


9. Choose account type


10. y



Test:

rclone ls onedrive:

Step 3: Download & Setup Script

sudo mkdir -p /opt/pterodactyl-backup
sudo nano /opt/pterodactyl-backup/backup.sh
sudo chmod +x /opt/pterodactyl-backup/backup.sh
sudo ln -s /opt/pterodactyl-backup/backup.sh /usr/local/bin/ptero-backup

Step 4: Configure Script

sudo nano /opt/pterodactyl-backup/backup.sh

Change:

DB_NAME="panel"
DB_USER="pterodactyl"
DB_PASS="your_password_here"

Step 5: Test Script

sudo ptero-backup


---

⏰ Cronjob Setup

Every 30 minutes

*/30 * * * * /opt/pterodactyl-backup/backup.sh --backup

Daily at 2 AM

0 2 * * * /opt/pterodactyl-backup/backup-manager.sh --backup

Every 6 hours

0 */6 * * * /opt/pterodactyl-backup/backup-manager.sh --backup


---

🎮 How to Use

Interactive Menu

sudo ptero-backup

1. Create backup


2. Restore backup


3. List backups


4. Clean old backups


5. System status



Direct Backup

sudo ptero-backup --backup


---

🔧 What Gets Backed Up

Pterodactyl Panel Files

Complete Database

Wings Configuration

Nginx Config

Backup Info



---

🚨 Quick Troubleshooting

Database Error

mysql -u pterodactyl -p panel -e "SHOW TABLES;"

OneDrive Error

rclone ls onedrive:

Permission Error

sudo chmod +x /opt/pterodactyl-backup/backup.sh
sudo chown root:root /opt/pterodactyl-backup/backup.sh


---

🔧 Advanced Configuration

Secure Config

sudo mkdir -p /opt/pterodactyl-backup/config
sudo touch /opt/pterodactyl-backup/config/.env
sudo chmod 600 /opt/pterodactyl-backup/config/.env
echo "DB_PASS=your_real_password" | sudo tee /opt/pterodactyl-backup/config/.env

Backup Encryption

gpg --symmetric --cipher-algo AES256 --output "$backup_file.gpg" "$backup_file"


---

📊 Monitoring & Maintenance

Check Backup Status

sudo tail -f /var/log/pterodactyl-backup.log
sudo crontab -l

Check OneDrive Usage

rclone about onedrive:
rclone ls onedrive:/PterodactylBackups/

Check Backup Sizes

du -sh /opt/pterodactyl-backups/
ls -lah /opt/pterodactyl-backups/local/


---

📈 Backup Strategy

Small Setups (<10 servers)

Every 2 hours

Retain 5 local + 10 OneDrive


Medium Setups (10–50 servers)

Every 1 hour

Retain 3 local + 7 OneDrive


Large Setups (50+ servers)

Every 30 minutes

Retain 2 local + 5 OneDrive



---

🔐 Security Best Practices

# Store DB password in .env
echo "DB_PASS=secure_password" > /opt/pterodactyl-backup/config/.env
chmod 600 /opt/pterodactyl-backup/config/.env

# Encrypt backups with GPG
gpg --symmetric --cipher-algo AES256 backup.tar.gz

# Restrict script permissions
chmod 700 /opt/pterodactyl-backup/backup-manager.sh


---

📞 Support & Maintenance

Weekly

Verify backups

Check OneDrive storage

Test restore


Monthly

sudo rclone selfupdate

Review retention policy

Test full restore
