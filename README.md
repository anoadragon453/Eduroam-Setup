# UCM-CatNet-Setup
How to set up NetworkManager for use on school and other WPA2-Enterprise Networks using only systemctl, and the text editor of your choice.

# How To
If you don't have NetworkManager installed, either get it from your package manager, or transfer the source from a computer that has network access and go [here](http://www.linuxfromscratch.org/blfs/view/svn/basicnet/networkmanager.html) for instructions on how to install it.

First, generate a UUID with `uuidgen`:

```
[user@~]$ uuidgen
446c82e6-8635-4cb2-98a2-db7df9894bd7
[user@~]$ 
```

Then as root copy the base config from this repository into `/etc/NetworkManager/system-connections/`:
```
# cp '/path/to/UCM-CatNet-Setup/UCM CatNet' /etc/NetworkManager/system-connections/
```

Edit the file with your favorite text editor. Set `uuid` to the one you generated earlier, and add your UCMNet ID and password. 

Write and save the file, then run
```
chown root /etc/NetworkManager/system-connections/UCM\ CatNet && \
chmod 600 /etc/NetworkManager/system-connections/UCM\ CatNet
```

Finally you must restart the NetworkManager service with `sudo systemctl restart NetworkManager`. And with that you should have a functioning UCM CatNet connection on WPA2-Enterprise!
