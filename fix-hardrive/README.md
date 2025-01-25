## What error: 

`This location could not be displayed`

which is relat4rd to `Filesystem Error`


## How to solve:


Step 1:

find where your hardrive is mounted  by `udisksctl status` :

> Here on assuming it is in `/dev/sda1`

Only run ntfsfix/fsck on an unmounted partition. Therefore, unmount it first `sudo umount /dev/sda1`

Confirm file system:

`sudo blkid /dev/sda1`

It should print something like TYPE="ntfs" or TYPE="ext4", etc.

Step 2:

Based on the file system

`sudo ntfsfix /dev/sda1` OR `sudo fsck -f /dev/sda1`

/dev/sda1 is where your hardrive is mounted 

Step 2.1:

if `ntfsfix/fsck` fails or only partially fixes the issue, attach the drive to a Windows system and run `chkdsk D: /f` on it. That’s more thorough for NTFS. This worked for me in windows 10.

Step by step of this process:

1. Right-click on Command Prompt in the search results and select Run as administrator.
2. Find the Drive Letter of the Faulty Drive
3. Note the drive letter assigned to your external drive (e.g., "D:", "E:", etc.).
> assuming its D now
run `chkdsk D: /f` The /f flag tells chkdsk to fix errors on the disk.

You should see in the end `Windows has scanned the file system and found no problems.`

EXTRA 

If you suspect physical sector issues, you can add the /r flag to scan for bad sectors and recover readable data:
`chkdsk D: /f /r`

Note: This will take longer to complete.

---


### GENERAL CHECK

Check the disk health (SMART Data) 
Even if you repair the filesystem, hardware failures can recur if your disk is physically failing. Check S.M.A.R.T. data:

if not installed 
```bash
sudo apt-get update
sudo apt-get install smartmontools
```

Run a short test: `sudo smartctl -t short /dev/sda`

After it completes show the results:

`sudo smartctl -a /dev/sda`

Look for any “FAIL” lines or high counts of “Reallocated_Sector_Ct,” “Pending_Sectors,” etc.
