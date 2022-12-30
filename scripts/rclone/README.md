# Cloud Snapshot

Script to backup and snapshot a cloud storage directory.

This script was originally designed to automatically backup files securely, easily, and on almost any hardware.


This allows backing up to your NAS *without port forwarding, VPNing, or proxying your server*. Because the backup is first sent to your cloud storage you're essentially piggy backing off of Google's/Dropbox's/Microsoft's/etc's security. For example you might want your phone to send periodic backups to your NAS, you can achieve that with this script. The flow of data looks like: 

```
Phone --> Google Drive --> NAS
```

Every time a backup is made we use rsnapshot to create a snapshot, allowing you to keep a history of your backups. rsnapshot uses hardlinks if a file doesn't change between snapshots, meaning snapshots only take up space if a file actually changes.

## Use Cases

Some personal use cases I've found:

1. Backing up my Keepass database.

2. Backing up my Steam Deck emulator saves.

## Requirements

* rclone installed AND configured
* rsnapshot installed (via NerdPack)
* Setup CRON (or UserScript schedule) to periodically run this script

## Setup

The only really important parameters to set are:

* `REMOTE`: This is the remote configured in rclone. Run `rclone config` on the command line to set this up.
* `REMOTE_PATH`: The path within the remote to clone. Leave blank to copy everything.
* `BACKUP_PATH`: The path to output to the backup. Should probably be somewhere under `/mnt/user/` for Unraid users.

