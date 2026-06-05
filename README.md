Make sure you din't have any old stuff:
sudo rmmod aic8800_fdrv aic_load_fw 2>/dev/null && sudo rm -rf /lib/firmware/aic8800*

If it isn't obvious, clone:
git clone https://github.com/MimoAW/AIC8800-Linux-Driver && cd AIC8800-Linux-Driver

Udev stuff I think?:
sudo sh install_setup.sh && cd drivers/aic8800

Make:
sudo make clean && sudo make && sudo make install

DKMS:
cd ~/AIC8800-Linux-Driver && sudo cp -a . /usr/src/aic8800-1.0 && sudo dkms add -m aic8800 -v 1.0 && sudo dkms build -m aic8800 -v 1.0 && sudo dkms install -m aic8800 -v 1.0

Modprobe:
sudo modprobe cfg80211 && sudo modprobe aic_load_fw && sudo modprobe aic8800_fdrv

Finally:
lsmod | grep aic
