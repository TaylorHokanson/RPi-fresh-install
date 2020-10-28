# RPi-fresh-install

1. Insert a 16Gb SD card into a desktop/laptop computer.
2. Use Raspberry Pi Imager to burn Raspian on the SD.
1. Make a blank text file called "ssh" (no extension) and copy it to the SD's root folder.
1. Insert the SD into a pi.
1. Attach a monitor, ethernet cable, keyboard and mouse.
1. Boot up and follow the prompts for localization, wifi, etc.
    - Update will take 15-20 minutes.
    - It's totally worth getting out the monitor so you don't have to mess with wifi via command line.
      - It's possible that this is easy now via raspi-config, but I haven't tried it.
1. ```sudo raspi-config```
    - System options > Hostname
      - Pick something memorable so you don't have to hunt for the IP address moving forwards.
1. ```sudo su``` ```update-alternatives --install /usr/bin/python python /usr/bin/python3 1```
    - this makes Python 3 the default version
1. ```sudo nano /boot/config.txt``` to rotate screen if needed
    ```- add display_rotate=2```
1. Set up [SAMBA](https://magpi.raspberrypi.org/articles/samba-file-server) so that you can directly edit files on the pi
