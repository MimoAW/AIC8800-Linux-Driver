Make sure you don't have any old drivers that are broken af:
```sudo rmmod aic8800_fdrv aic_load_fw 2>/dev/null && sudo rm -rf /lib/firmware/aic8800*```

If it isn't obvious, clone:
```git clone https://github.com/MimoAW/AIC8800-Linux-Driver && cd AIC8800-Linux-Driver```

Udev stuff I think? yes:
```sudo sh install_setup.sh && cd drivers/aic8800```

Make (this one sucks ass):
```sudo make clean && sudo make && sudo make install```

DKMS (this good):
```cd ~/AIC8800-Linux-Driver && sudo cp -a . /usr/src/aic8800-1.0 && sudo dkms add -m aic8800 -v 1.0 && sudo dkms build -m aic8800 -v 1.0 && sudo dkms install -m aic8800 -v 1.0 --force```

If not worky: 
```sudo dnf install dkms make gcc kernel-devel```

Modprobe (idk):
```sudo modprobe cfg80211 && sudo modprobe aic_load_fw && sudo modprobe aic8800_fdrv```

Finally:
```lsmod | grep aic```
