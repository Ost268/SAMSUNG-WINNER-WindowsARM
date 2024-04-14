<img align="right" src="https://github.com/Ost268/SAMSUNG-WINNER-WindowsARM/blob/main/winner.png" width="350" alt="Windows 11 running on winner">

# Running Windows on the SAMSUNG GALAXY FOLD SM-F900F

## Driver updating

### Prerequisites
- [Windows on ARM image](https://worproject.com/esd)
  
- [Drivers](https://mega.nz/file/j9lREBJA#AwA4xIovsHdK4Bpb4-9bDEbxJdCDDr_LYulJ8w3qvcc) 

- [Modded TWRP](https://mega.nz/file/LoVGETDK#-lwSOZeVRTuyOYOOv84RqhZJs8Ns-ESpoM6cT6-X-Kg) (should already be installed)

- [Rdrive backup](son)


### Boot to the modded TWRP
> Flash it in Odin if you don't have it installed for whatever reason

#### Running the msc script
```cmd
adb shell msc.sh
```
or open cmd.exe and paste this lines
cd C:\adb

after paste 

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


### Open RDrive
<img align="right" src="https://github.com/Ost268/SAMSUNG-WINNER-WindowsARM/blob/main/guide/guide
/RDrive/Screen1.png" width="350" alt="RDrive">
Click Restore from an Image
```open image  E_HDD5-image.rdr
```Click Restore disk or partitions and click next

<img align="right" src="https://github.com/Ost268/SAMSUNG-WINNER-WindowsARM/blob/main/guide/guide
/RDrive/Screen2.png" width="350" alt="RDrive">
#### Wait for some time and exit

> Flash Latest UEFI image and reboot 
```Drivers install manualy .\DriverUpdater.exe -d .\definitions\Desktop\ARM64\Internal\winner.txt -r . -p R:\
```

### Boot back into Windows
> Reboot your device to boot back into Windows. If this boots you to Android, reflash the UEFI image through fastboot or by using the WOA Helper app

  
  

# Finished!
