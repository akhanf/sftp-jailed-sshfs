# cloud-utils

Simple set-up for creating root-locked sftp accounts, where the shared folders are themselves sshfs mounts to another system.

You should run this on a cloud instance, and use IP-restricted access  with only key-based ssh access enabled.

## Initial setup

- Edit your `/etc/ssh/sshd_config` to include what is in `sshd_config` here.
- Note: may be a few other steps missing here!


## Adding a new share:

1. Update the `user_list.csv` with the share names and directories.

2. Run: `sudo ./all_create_users user_list.csv` to create the users and shares. This also creates login instruction text files (random password) in the users folder.

3. Run: `./all_mount_nosudo user_list.csv` to mount the sshfs shares.

4. Share the login info with the user, and make sure you add the user's IP to your cloud instance security group (remember can use /24 at the end to allow the exact IP to vary)

5. If you need to unmount, use: `./all_unmount_nosudo user_list.csv`


