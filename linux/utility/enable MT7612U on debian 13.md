-- -
install the aircrack suite on your linux, and make sure you have the non-free firmware drivers installed

Run this the command to get the interface name
```bash
sudo airmon-ng
```

Then you'll get a table with the network cards, youll need to `MTH7612U` interface and copy the the interface in the follewing command
```bash
sudo airmon-ng start <interface-name>
```
