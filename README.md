# rtl8126
Driver for RTL8126 5GbE PCIe Module OpenWRT (Kernel 6.6.41)

1. Download tools with:
```
opkg update
opkg install kmod ethtool wget
```

2. Download RTL8126 driver with wget:
```
wget -O /lib/modules/$(uname -r)/r8126.ko https://raw.githubusercontent.com/Darktron/rtl8126/main/r8126.ko
```

3. Update driver dependencies with:
```
depmod -a
```

4. Load the RTL8126 driver with:
```
insmod /lib/modules/$(uname -r)/r8126.ko
```

5. Verify the RTL8126 driver is loaded with:
```
lsmod | grep r8126
```

6. Check interfaces with:
```
ip a
```
Or
```
ip link show
```
Or
```
ethtool eth#
```
Or
```
ifconfig -a
```

7. Add the driver name to this file to ensure it loads at boot.
```
echo "r8126" > /etc/modules.d/r8126
```

8. Reboot and Verify
Reboot the system and check if the module is loaded:
```
reboot
```

After rebooting, check:
```
lsmod | grep r8126
```

If the module does not appear, check for errors in the system logs:
```
dmesg | grep r8126
```
