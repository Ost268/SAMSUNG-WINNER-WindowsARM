<img align="right" src="https://github.com/n00b69/SAMSUNG-WINNER-WindowsARM/blob/main/winner.png" alt="Windows 11 running on winner">

# Running Windows on the SAMSUNG GALAXY FOLD SM-F900F

## Partitioning your device

## Notes:
> **Warning** if you delete any partitions via diskpart later on or now windows will send a ufs command that gets misinterpreted which erase all your ufs
- All your data will be erased! Backup now if needed.
- These commands have been tested.
- Do not run the same command twice

### THE FIRST STEP UNLOCK BOOTLOADER 

### FLASH TWRP recovery through the PC with the Odin
> If you already have TWRP installed, just hold the power and vol+ buttons at startup

### Unmount all partitions
Go to TWRP settings and unmount all partitions

### Push necessary tools:
```cmd
adb push parted /sbin
```

### Start ADB shell
```cmd
adb shell
```

## Create Partitions

### Give permissions
```cmd
chmod +x /sbin/*
```

### Start parted
```sh
parted /dev/block/sda
```

### Delete the `userdata` partition
> You can make sure that 30 is the userdata partition number by running
>  `print all`
```sh
rm 3O
```

### Create partitions
> If you get any warning message telling you to ignore or cancel, just type i and enter

#### For all 512Gb models WITH WINPE:

- Create the ESP partition (stores Windows bootloader data and EFI files)
 ```sh
mkpart esp fat32 9730MB 10.2GB
```
- Create the main partition where WindowsPE will be installed to
```sh
mkpart pe fat32 10.2GB 25GB
```

- Create the main partition where Windows will be installed to
```sh
mkpart win ntfs 25GB 312GB
```

- Create Android's data partition
```sh
mkpart userdata ext4 312GB -0MB
```

#### For 512Gb models WITHOUT WindowsPE:

- Create the ESP partition (stores Windows bootloader data and EFI files)
```sh
mkpart esp fat32 9730MB 10.2GB
```

- Create the main partition where Windows will be installed to
```sh
mkpart win ntfs 10.2GB 312GB
```

- Create Android's data partition
```sh
mkpart userdata ext4 312GB -0MB
```


### Make ESP partiton bootable so the EFI image can detect it
```sh
set 30 esp on
```

### Quit parted
```sh
quit
```

### Reboot to TWRP

### Start the shell again on your PC
```cmd
cd C:\adb

adb shell

setprop sys.usb.ffs.ready 1

setprop sys.usb.config adb

echo 0 > /config/usb_gadget/g1/bDeviceClass
echo 0 > /config/usb_gadget/g1/bDeviceSubClass
echo 0 > /config/usb_gadget/g1/bDeviceProtocol
echo 0 > /config/usb_gadget/g1/functions/mass_storage.0/lun.0/cdrom
echo 0 > /config/usb_gadget/g1/functions/mass_storage.0/lun.0/ro
echo 0 > /config/usb_gadget/g1/functions/mass_storage.0/lun.0/removable 0
echo /dev/block/sda > /config/usb_gadget/g1/functions/mass_storage.0/lun.0/file
ln -s /config/usb_gadget/g1/functions/mass_storage.0 /config/usb_gadget/g1/configs/b.1/f4
sh -c 'echo > /config/usb_gadget/g1/UDC; echo a600000.dwc3 > /config/usb_gadget/g1/UDC' &
[1] 690
```

### Format partitions
-  Format the ESP partiton as FAT32
```sh
mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPWINNER
```

-  Format the Windows partition as NTFS
```sh
mkfs.ntfs -f /dev/block/by-name/win -L WINWINNER
```

- Format data
Go to Wipe menu and press Format Data, 
then type `yes`.

### Check if Android still starts
just restart the phone, and see if Android still works


## [Next step: Installing Windows](2-install.md)









