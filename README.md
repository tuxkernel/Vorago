# Tools for Vorago 404 "gaming mouse" under GNU/Linux

![Sample Run](https://github.com/tuxkernel/vorago-gaming-mouse-404/blob/master/images/00.png)

# Enable mouse polling rate (1000 Hz)

### Method one:

Open a terminal and type:

- `$ cd /`
- `$ sudo pluma etc/modprobe.d/usbhid.conf`

In that file, add the following:

`options usbhid mousepoll=1`

Save and exit.

`$ sudo reboot`

### Method two:

Open a terminal and type:

- `$ cd /`
- `$ sudo pluma /etc/default/grub`

In that file, look for the line that says `"GRUB_CMDLINE_LINUX_DEFAULT="quiet"` and add the following:

`usbhid.mousepoll=1`

The line should look like this:

`"GRUB_CMDLINE_LINUX_DEFAULT="usbhid.mousepoll=1 quiet"`

Save and exit.

- `$ sudo update-grub`
- `$ sudo update-grub2`
- `$ sudo reboot`

Tools for Vorago 404 "gaming mouse" under GNU/Linux. Coming soon... ;-)´
