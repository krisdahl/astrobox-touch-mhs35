# astrobox-touch-mhs35

Scripts to get the MHS35 screen working on Astrobox Touch working.

# Background

Astrobox Touch [documentation](https://astroprint.zendesk.com/hc/en-us/articles/360000761606-Step-1-Hardware-requirements-for-the-AstroBox-Touch) states that only a few screens (Waveshare, Kumon, GeekPi) are supported. Getting additional screens like the Geekworm screens is pretty simple. This should work with any screen that uses the "LCD-show" configuration workflow.

In my case, the Geekworm screen config files can be snagged at https://github.com/goodtft/LCD-show. I've included the scripts in this repo, but you can snag any other screen config, not just the Geekworm / GoodTFT panels.

## Step 1: Enable SSH

Astrobox disabled SSH out of the box, so put a "ssh" folder on your boot. Snag your IP by looking at DHCP reservations, or reboot your Pi without a SD card to see your IP address.

## Step 2: Snag this repo

`cd ~
git clone https://github.com/krisdahl/astrobox-touch-mhs35.git`

## Step 3: Install/Enable Driver

Essentially you need to install the driver and then update the /boot/config.txt for your display. Pick the correct script for your display.

`sudo ./MHS-35-show`

This will also create a config file in ./boot/config.txt.bak.

## Step 4: Copy config

`sudo cp ./boot/config.txt.bak /boot/config.txt`

I've put an example config in ./boot/config.txt.

## Step 4: Reboot

`sudo shutdown -r now`

# Additional Notes

Screen configuration scripts on Astrobox are located in /screen-config/. The main script is /screen-configchange-screen-config.sh, which just runs the "LCD-show" driver install and then copies the config file to /boot/config.txt
