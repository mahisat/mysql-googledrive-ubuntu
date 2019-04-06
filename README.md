# mysql-googledrive

Bash Script to backup mysql and upload it to Google Drive. Tested with Ubuntu 14.04, 16.04 and 18.04.



 To make this script work you have to install gdrive on your server
 
 # Step 1

Go to this link then  follow the Steps To Install Gdrive on Server:
https://medium.com/auto-backup-mysql-to-google-drive/auto-backup-mysql-to-google-drive-c8b2178b097e

After configuring gdrive on server, Create folder in your google drive account then move into that folder. Look at URL note down the id

For example,
https://drive.google.com/drive/u/0/folders/1Rp3Cr6coisUI_wOScPdDnwD0Ll2HE1r7

Id from above is 1Rp3Cr6coisUI_wOScPdDnwD0Ll2HE1r7

# Step 2
Now create backup.sh in your server

# step 3

create a cronjob as root  using below steps
  step1:
  Edit crontab file
   # sudo nano /etc/crontab
  Add the below your script in crontab
  
  0 9  * * * /your/path/to/backup.sh Backup_Folder DatabaseName DatabaseUser DatabasePassword GdriveFolderId 
  
  we should pass parameters to script
  Backup_Folder ===> This is the folder name to which your mysql file dump into server
  DatabaseName  ===> Provide  database name which you should backup
  DatabaseUser  ===> Provide username of your mysql, mostly root is the username
  DatabasePassword ===>Provide database password
  GdriveFolderId   ===> Put your google drive folder which you noted down above
  Every morning at 9 AM the backup should take place automatically
  
  For example, In  my case the cronjob should be,
  0 9  * * * /backup.sh MysqlBackup Blog_Database root pass1234 1Rp3Cr6coisUI_wOScPdDnwD0Ll2HE1r7  
  
  
  
  
  
  
  













