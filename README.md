# openwrt-adblock
hosts file based ad blocking for OpenWRT

####To use it:

* Download the ad block script, save it to /etc/, and make it executable.
```
wget --no-check-certificate https://raw.githubusercontent.com/jjack/openwrt-adblock/master/adbblock.sh -O /etc/adblock.sh
chmod +x /etc/adblock.sh
```

* Run it.
```
/etc/adblock.sh
```

####Run on boot.
* Add the following to /etc/rc.local (In LuCI, it's System > Startup) [the sleep is to make sure that your connection is fully up]
```
sleep 15 && /etc/adblock.sh &
```

####Optional - serve a 1 pixel transparent .gif for all of the newly un-routable things.
```
wget --no-check-certificate -O /www/1.gif http://upload.wikimedia.org/wikipedia/commons/c/ce/Transparent.gif
uci set uhttpd.main.error_page="/1.gif" && uci commit
/etc/init.d/uhttpd restart
```
