# erase and format disk or drive

## Find the correct drive
```
lsblk
```
This will show all the drives mounted to computer. Find the drive you want to format.
Note!: Do not mess the first step up.

## Format the drive/disk

```
/home/assi# dd if=/dev/zero of=/dev/sdb bs=1024k count=2048
```

1. **`/home/assi#`**  
   This indicates the command prompt, showing that the command is being run as a user named `assi`.

2. **`dd`**  
   This is a Unix/Linux command-line utility used for low-level copying and conversion of raw data.

3. **`if=/dev/zero`**  
   - `if` stands for "input file."  
   - `/dev/zero` is a special file in Unix/Linux that provides as many null (zero) bytes as are read from it.  
   - So, the input source here is a stream of zeros.

4. **`of=/dev/sdb`**  
   - `of` stands for "output file."  
   - `/dev/sdb` typically refers to a second hard drive or storage device connected to the system.  
   - The command will write data directly to this device.

5. **`bs=1024k`**  
   - `bs` stands for "block size."  
   - Set to `1024k`, meaning each read/write operation will process 1024 kilobytes (1 megabyte) at a time for efficiency.

6. **`count=2048`**  
   - Specifies the number of blocks to copy.  
   - Here, it will copy 2048 blocks of 1024k each.

**Summary:**  
This command writes zeros to the entire `/dev/sdb` device, overwriting 2048 blocks of 1024 kilobytes each, which totals approximately 2 gigabytes (since 2048 * 1024 KB = 2,097,152 KB ≈ 2 GB).

**Warning:**  
Running this command will erase all data on `/dev/sdb`. Use it with caution!

## sync

```
sync
```

The **`sync`** command will make sure you write all the date from the computer buffer to the drive.
Because **`dd`** may not write everthing to disk. **_Its just good practice to do so_**. 

**_Note!_**: If this is a thumbdrive unplug and replug it after you ran the sync command, Wait a bit first. after that run **`lsblk`** again to see your drive so you can proseed to the next step.

## parted -> making our partion rable and partion/s
```sudo apt install -y gparted```
Just make sure its installed. (debian)

```
sudo parted /dev/sdb mklabel msdos
```
This will make our partition tabel.

**_Note!:_**: You can ignore the **`fstab`** warning for thumbdrives and removable drives.

```
sudo parted /dev/sdb mkpart primary 1Mb 100%
```
```
sync
```
sync again

## make an ext4 fille system on your drive

```
sudo mkfs.ext4 /dev/sdb1
```
**_Note!_**: You can use with ever type of fille system you want but in this example wherer using ext.4 .

## labeling your fille system
```
sudo e2label /dev/sdb1 thumbdrive
```
Where calling our drive thumbdrive in this example but you can call it what ever you want.
```
sync
```
Now unplug and replug your drive.


