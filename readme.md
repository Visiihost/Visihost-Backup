Here’s your complete GitHub README.md in one clean file with proper markdown formatting:

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
# Install rclone aur mysql-client
sudo apt update
sudo apt install -y mysql-client curl
curl https://rclone.org/install.sh | sudo bash

Step 2: Setup OneDrive

rclone config

OneDrive Setup (2 minute mein):

1. n (new remote)


2. Name: onedrive


3. Type: 26 (Microsoft OneDrive)


4. Client ID/Secret: Just press Enter (blank)


5. Region: 1 (Global)


6. Advanced: n (No)


7. Auto config: y (Yes)


8. Login in browser


9. Choose account type


10. y to confirm



Test:

rclone ls onedrive:

Step 3: Download aur Setup Script

# Create folder
sudo mkdir -p /opt/pterodactyl-backup

# Copy the script content to this file:
sudo nano /opt/pterodactyl-backup/backup.sh

# Make executable 
sudo chmod +x /opt/pterodactyl-backup/backup.sh

# Create shortcut
sudo ln -s /opt/pterodactyl-backup/backup.sh /usr/local/bin/ptero-backup

Step 4: Configure Script (Sirf 3 lines change karo)

sudo nano /opt/pterodactyl-backup/backup.sh

Change these lines:

DB_NAME="panel"                    # Tumhara database name
DB_USER="pterodactyl"               # Database user
DB_PASS="your_password_here"        # YAHAN APNA DATABASE PASSWORD DALO

Step 5: Test Script

sudo ptero-backup


---

⏰ Cronjob Setup

Every 30 minutes:

*/30 * * * * /opt/pterodactyl-backup/backup.sh --backup

Daily at 2 AM:

0 2 * * * /opt/pterodactyl-backup/backup-manager.sh --backup

Every 6 hours:

0 */6 * * * /opt/pterodactyl-backup/backup-manager.sh --backup


---

🎮 How to Use

Interactive Menu:

sudo ptero-backup

Menu Options:

1. Create backup


2. Restore backup


3. List backups


4. Clean old backups


5. System status



Direct Backup (cronjob ke liye):

sudo ptero-backup --backup


---

🔧 What Gets Backed Up

1. Pterodactyl Panel Files


2. Complete Database


3. Wings Configuration


4. Nginx Config


5. Backup Info file




---

🚨 Quick Troubleshooting

Database Error?

mysql -u pterodactyl -p panel -e "SHOW TABLES;"

OneDrive Error?

rclone ls onedrive:

Permission Error?

sudo chmod +x /opt/pterodactyl-backup/backup.sh
sudo chown root:root /opt/pterodactyl-backup/backup.sh


---

💡 Pro Tips

1. Test restore monthly


2. Check /var/log/pterodactyl-backup.log


3. Monitor OneDrive space


4. Always backup before updates




---

🔧 Advanced Configuration

Secure Config:

sudo mkdir -p /opt/pterodactyl-backup/config
sudo touch /opt/pterodactyl-backup/config/.env
sudo chmod 600 /opt/pterodactyl-backup/config/.env
echo "DB_PASS=your_real_password" | sudo tee /opt/pterodactyl-backup/config/.env

Backup Encryption:

gpg --symmetric --cipher-algo AES256 --output "$backup_file.gpg" "$backup_file"


---

📊 Monitoring & Maintenance

Check Backup Status:

sudo tail -f /var/log/pterodactyl-backup.log
sudo crontab -l

Check OneDrive Usage:

rclone about onedrive:
rclone ls onedrive:/PterodactylBackups/

Check Sizes:

du -sh /opt/pterodactyl-backups/
ls -lah /opt/pterodactyl-backups/local/


---

📈 Backup Strategy

Small setups (<10 servers):

Every 2 hours

Retain 5 local + 10 OneDrive


Medium setups (10-50 servers):

Every 1 hour

Retain 3 local + 7 OneDrive


Large setups (50+ servers):

Every 30 minutes

Retain 2 local + 5 OneDrive



---

🔐 Security Best Practices

1. Store DB password in .env


2. Encrypt backups with GPG


3. Restrict script permissions


4. Use dedicated OneDrive account with 2FA




---

📞 Support & Maintenance

Weekly:

Verify backups

Check OneDrive storage

Test restore process


Monthly:

sudo rclone selfupdate

Review retention policy

Test full restore



---

💡 Pro Tips

Test restore monthly

Monitor disk space

Use multiple backup destinations

Keep documentation of restore steps



---

🎉 Your Pterodactyl backup system is ready!

sudo ptero-backup

If you want, I can also make you a **color-coded badge section, GitHub styling, and screenshots** so the README looks premium and attractive.  
Do you want me to make that version next?

