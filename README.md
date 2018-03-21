sudo dd if=/dev/rdisk2 of=~/Desktop/gateway.dmg bs=5m
sudo dd if=~/Desktop/2016-05-27-raspbian-jessie-lite.img of=/dev/rdisk3 bs=5m

sudo apt-get install ppp
sudo apt-get install python-pip
sudo pip install pyserial
sudo pip install flask
sudo raspi-config
sudo nano /boot/config.txt
dtoverlay=pi3-disable-bt //add at end of file
sudo nano /boot/cmdline.txt
remove console=serial0,115200
dwc_otg.lpm_enable=0 console=tty1 console=serial0,115200 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait

/etc/network/interfaces

auto ppp0
iface ppp0 inet ppp
provider provider


cd /etc/ppp/peers  provider
cd /etc/chatscripts gprs
cd /etc/ppp
sudo nano ip-down
add sudo reboot at end

sudo crontab -e
0 */4 * * * /home/pi/reboot.sh
sudo nano reboot.sh
#!/bin/sh

sudo reboot

sudo systemctl enable lora-gateway-config.service
sudo systemctl enable lora-gateway-bridge.service
sudo systemctl enable ttn-gateway.service
sudo pon
