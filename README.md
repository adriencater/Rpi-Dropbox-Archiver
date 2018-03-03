# Rpi-Dropbox-Archiver

*RPi + rclone + BRTFS + snapshots = dedicated TimeMachine for shared Dropbox folders*

- - - - - 


### The problem:

- Dropbox is frequently used for collaboration.
- For important data.
- Dropbox is magic, magic is opaque.
- Dropbox can be confusing for users, and even the best of us make make mistakes.
- If a user intentionally (to free space on their local drive) or accidentally deletes files in a dropbox folder, those files are deleted everywhere.
- Other users in the group may not notice the disappearance of data for some time.
- Individual backups may be inexistant, out of date, or not include Dropbox (and many users use dropbox itself as a “backup”).

### The Solution:

- Run a dedicated backup/archive server. 
- Raspberry Pi + external hard drive.
- rClone or similar to fetch data from Dropbox.
- Use BRTFS to make regular snapshots of the shared folder, à la TimeMachine™.
- Hopefully / Eventually:
	- Keep a log of activity in the dropbox folder.
	- Send a regular status report to a user: System status, dropbox activity, drive usage, etc.
	- Allow a user to access/browse the archive of snapshots to retrieve a deleted file.

- - - - - 

## Notes and Instructions

### Hardware

- Test unit is 
	- Raspberry Pi 3
	- [powered USB hub](https://thepihut.com/products/7-port-usb-hub-for-the-raspberry-pi)
	- portable external hard drive

### Dropbox 

- The system should be ‘read only’ for Dropbox.
- rClone – [https://rclone.org](https://rclone.org) – looks like it should do the trick.
- Will create a dedicated ‘DropBot’ user for accessing the dropbox.

### BRTFS

BTRFS for Pi:

- [https://hackaday.com/2017/06/18/btrfs-for-the-pi/](https://hackaday.com/2017/06/18/btrfs-for-the-pi/)
- [https://hackmd.io/IwFgZmBG0AwLQHYAcSxxAYwJzDlghgEwBscYGAJiZAlmDPUA](https://hackmd.io/IwFgZmBG0AwLQHYAcSxxAYwJzDlghgEwBscYGAJiZAlmDPUA)

BTRFS snapshots

- [https://btrfs.wiki.kernel.org/index.php/Incremental_Backup](https://btrfs.wiki.kernel.org/index.php/Incremental_Backup)
- [https://www.linux.com/learn/how-create-and-manage-btrfs-snapshots-and-rollbacks-linux-part-2](https://www.linux.com/learn/how-create-and-manage-btrfs-snapshots-and-rollbacks-linux-part-2)
- [https://wiki.archlinux.org/index.php/Snapper](https://wiki.archlinux.org/index.php/Snapper)

- - - - - 

### Project specific code

- Shell script cron job:
	- Sync files from Dropbox
	- Make a snapshot


