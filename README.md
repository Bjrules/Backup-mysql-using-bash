# This is a simple Automation Script that backup MySQL Database using Bash
### This project assume you have a MySQL Database Administration Skills already

#!/bin/bash

# Database credentials
DB_USER="your_username"
DB_PASS="your_password"
DB_NAME="your_database"

# Backup directory
BACKUP_DIR="/path/to/backup/directory"

# Date format for the backup file
DATE=$(date +"%Y-%m-%d_%H-%M-%S")
BACKUP_FILE="$BACKUP_DIR/$DB_NAME-backup-$DATE.sql"

# Create backup directory if it doesn't exist
mkdir -p "$BACKUP_DIR"

# Perform database backup using mysqldump
mysqldump -u "$DB_USER" -p"$DB_PASS" "$DB_NAME" > "$BACKUP_FILE"

# Check if the backup was successful
if [ $? -eq 0 ]; then
    echo "Database backup successful: $BACKUP_FILE"
else
    echo "Database backup failed"
fi

### CRONTAB
```
crontab -e
```
### Enter the following code
```
0 17 * * * /home/banjo/backup.sh
```



