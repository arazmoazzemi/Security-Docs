#### Mikrotik: Regularly Export, Backup ROS & Userman DB + Send in Email

---

1: Create the script: system > scripts > + > Name: Backup


#### SCRIPT:

```
# Export Config
export file=ROS-Export
delay 5s
log/info "Current configuration exported successfully!"

# Backup ROS
system/backup/save name=ROS-Backup dont-encrypt=yes
delay 5s
log/info "ROS backed up successfully!"

# Backup UM DB
user-manager/database/save name=UM-DB overwrite=yes
delay 5s
log/info "UM DB backed up successfully!"

# Send Backup files via Email
tool/e-mail/send to=YOU@EXAMPLE.COM subject="Daily Backup | $[/system/identity/get name] | $[/system/clock/get date]" body="Hello,\nThis is a daily backup from ROS and UM DB.\nRouterOS version is $[/system/resource/get version]" file=ROS-Backup.backup,UM-DB.umb,ROS-Export.rsc
```

# ----

# Create the sheduler: system > Sheduler > + > Name: Daily-Backup
## Set the Start Date, Start Time & Interval

# ----

## COMMAND:

/system/script/run Backup

------------------------------------------
# Video Link: https://youtu.be/M7GdE9oDA7w
------------------------------------------


# Best regards :)
# Ramtin
# youtube.com/c/NetAdminPlus
