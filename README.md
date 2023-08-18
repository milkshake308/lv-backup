# LV-BACKUP
Save your LVM-based volume into state-consistent disk dump files.

## What is really?
LV-BACKUP is essentially an abstraction of various commands from LVM and `dd`, used for backing up files. These tools are designed to provide an easy and straightforward (though basic) backup solution for LVM-based storage.

### Who is it for?
- System administrators who want a simple way to back up LVM volumes.
- Users who need to create consistent disk dump backups of their LVM volumes.

## Installation
You can download the files or just clone this repository and make the scripts executables :

```bash
   git clone https://github.com/milkshake308/lv-backup.git
   cd lv-backup
   chmod +x lv-*
   ```

## Examples
- Interactively backup an lvm volume (LV)
```bash
sudo ./lv-wizard lv
```
- Interactively backup all LVs within a volume group (VG)
```bash
sudo ./lv-wizard vg
```
- Backup the lvm volume `mylv` 
```bash
sudo ./lv-backup --lvm-volume mylv
```
- Backup the lvm volume `mylv` to the path /nfs/backups/ 
```bash
sudo ./lv-backup --lvm-volume mylv --backup-dest /nfs/backups/
```
- Backup the lvm volume `mylv` with a 7% snapshot size (size is calculated from a % the original LV size)
```bash
sudo ./lv-backup --lvm-volume mylv --snapshot-size 7
```
- Mount a volume backup `lv-lab_14-07-2023--04-29_CEST.img` to `/mnt/mounted_bkp`
```bash
losetup /dev/loop1 ./lv-lab_14-07-2023--04-29_CEST.img
mount /dev/loop1 /mnt/mounted_bkp
```