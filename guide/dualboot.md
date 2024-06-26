<img align="right" src="https://github.com/Ost268/SAMSUNG-WINNER-WindowsARM/blob/main/winner.png" width="350" alt="Windows 11 running on winner">

# Running Windows on the SAMSUNG GALAXY FOLD SM-F900F

## Dualboot guide

### Prerequisites
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [UEFI image](https://github.com/woa-msmnile/msmnilePkg/releases/download/2402.86/samsung-winner_NOSB.img) 

- [WOA Helper app](https://github.com/n00b69/woa-beryllium/releases/download/Dualboot/woahelper.apk)

- [Switch To Android package](https://mega.nz/file/n11EVLhI#7wCPb6_q-4JiPNXLDdV7Xc0IMd66WmXSr57buH_2Irk) 


## Dualboot guide
This guide assumes you are rooted, if you aren't, please do that first.

### Setup - Android
- Download and install the WOA Helper app, then open it and grant it root access.
- Download the UEFI image for your panel and place it inside the folder named `UEFI` in your internal storage. If this folder does not exist, create it.
- Press the `Mount Windows` button to mount Windows to your internal storage at `/sdcard/Windows`
- Create a folder called `sta` in Windows and unpack the two files in the `Switch to Android package` file here (the files should go to `/sdcard/Windows/sta`
> [!Note]
> If the above step fails, press `flash UEFI` instead, then reboot to boot to Windows, press restart in Windows, then as it is restarting boot back to recovery to flash your Android boot.img located in your internal storage, and try again.
- Return to the WOA Helper app and press the `Quickboot` button.

### Setup - Windows
- Navigate to C:\sta and create a shortcut of `sta.exe` to your desktop.

#### Booting to Android
- Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

#### Booting to Windows
- Press `Quickboot to Windows` inside the app, or use the newly created toggle in your quick settings panel
  
## Finished!

















### Enabling USB host mode
> Without this, unpowered USB devices will not work
- Download [this script](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/tag/USBHost) and run it. Select "Enable USB host mode", then reboot your Galaxy Fold.
