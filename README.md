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
    - ```display_rotate=2```
    - You'll want to [flip the touchscreen](https://www.instructables.com/Rotate-Raspberry-Pi-Display-and-Touchscreen/) as well
1. Set up [SAMBA](https://www.raspberrypi.org/documentation/remote-access/samba.md) so that you can directly edit files on the pi
  - I had to ```sudo chmod -R 777 /home/pi/Desktop``` as I kept getting authentication errors
  - I also restarted samba with ```sudo /etc/init.d/smbd restart```

## Extras
1. [HEre's a great tutorial on programs that run on startup](https://medium.com/@wasiullah.khan21/setup-a-python-script-as-a-service-through-systemctl-systemd-f0cc55a42267)
2. [Python interrupts (untested)](https://blog.miguelgrinberg.com/post/how-to-make-python-wait)
