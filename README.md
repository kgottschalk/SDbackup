SDbackup

Create and maintain a sychronized image file of an SD card boot disk.

Backup a SD based system to a image file. The SD card must have at least 2 partition
root / and /boot. Nested mounts of file systems are not supported. All file systems
must be mounted within the root / file system.
The image file must reside not reside on the SD card. Use another mounted file system
to storge the image file. This can be an network file system.
Script needs to run as root user.

Usage:  $mynm [-c|-s] [-d] [-m [-n]] [-r] [-s] [-q] [-v] [-V] <path to disk image>

Create or synchronize an image file from the local SD card (or disk). The image file is intended
as a backup of the SD card. It can be written back to an SD card and will boot the system in the
state from the last image file synchronization.

Options:
        -c      Create new image file. Fail if file exists. After the image is created,
                the initial synchronization is done.

        -d      Debug output. Lists syncronized files.

        -m      Maintenance mode. Mount file systems and exit.

        -n      Don't flag loop devices as autoclear

        -r      Resize / root partition in the image to current disk usage + %d%% free space.
                Resizing is only supported with ext2, ext3 and ext4 file systems.

        -s      Synronize existing image with local drive. Fail if image does not exist.

        -q      Quite modus. Don't write output except for errors and warnings.

        -v      Verbose output. Shows all steps of the process to synchronize the image.

        -V      Display script version and exit.

The script uses external unix commands:
losetup, mount, umount, sync, sfdisk, mkfs.vfat, mkfs.ext4, resize2fs, fsck.ext4, fsck.fat, rsync, lsblk, df, truncate

Based on the RasPBX backup utility, version 1.3 by: Gernot Bauer <gernot at raspbx.org>

This is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License 
as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This file is distributed in the hope that it will be useful,but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.
