# RPi-fresh-install

## Burn SD
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
1. ```sudo nano /boot/config.txt``` to rotate screen if needed
    - ```display_rotate=2```
    - You'll want to [flip the touchscreen](https://www.instructables.com/Rotate-Raspberry-Pi-Display-and-Touchscreen/) as well

## Install Python 3
Also installs IDLE, sets Python3 to default
1. ```sudo apt install python3 idle3```
2.  ```sudo su```
3.  ```update-alternatives --install /usr/bin/python python /usr/bin/python3 1```
4.  ```su pi```

## Set up [SAMBA](https://www.raspberrypi.org/documentation/remote-access/samba.md)
Lets you edit files from your laptop
  1. ```sudo apt install samba samba-common-bin smbclient cifs-utils```
  2. ```sudo nano /etc/samba/smb.conf```
  3. Add the following to the end of the file:
    ```[share]
    path = /home/pi
    read only = no
    public = yes
    writable = yes```
  4. ```sudo chmod -R 777 /home/pi```
  5. ```sudo /etc/init.d/smbd restart```

## Extras
1. [HEre's a great tutorial on programs that run on startup](https://medium.com/@wasiullah.khan21/setup-a-python-script-as-a-service-through-systemctl-systemd-f0cc55a42267)
2. [Python interrupts (untested)](https://blog.miguelgrinberg.com/post/how-to-make-python-wait)
