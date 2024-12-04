If there is no "Safely Remove" option for the hard drive, follow these steps:

1. Identify the correct drive:
   Use the following commands to locate the drive based on its size, mount point, or name:

   - `lsblk`
   - `df -h`
   - `udisksctl status`

2. Unmount the drive:
   After identifying the correct partition (e.g., /dev/sda1), unmount it to detach the filesystem:

   `sudo umount /dev/sda1`

3. Power off the drive:
   Once unmounted, power off the entire drive to stop its spinning and make it safe to disconnect:

   `udisksctl power-off -b /dev/sda`
