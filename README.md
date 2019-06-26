# Tools for Vorago 404 "gaming mouse" under GNU/Linux

![Sample Run](https://raw.githubusercontent.com/tuxkernel/Vorago/master/images/00.png)

## Enable mouse polling rate (1000 Hz)

### Method one (via `etc/modprobe.d/`):

Open a terminal and type:

- `cd /`
- `sudo pluma etc/modprobe.d/usbhid.conf`

In that file, add the following:

`options usbhid mousepoll=1`

Save and exit.

`sudo reboot`

You can check your mouse polling rate, opening a terminal and typing:

- `cd /`
- `cat sys/module/usbhid/parameters/mousepoll`

If you get "1", then mouse polling rate (1000 Hz) is ENABLED.

### Method two (via boot kernel module parameter):

Open a terminal and type:

- `cd /`
- `sudo pluma /etc/default/grub`

In that file, look for the line that says `"GRUB_CMDLINE_LINUX_DEFAULT="quiet"` and add the following:

`usbhid.mousepoll=1`

The line should look like this:

`"GRUB_CMDLINE_LINUX_DEFAULT="quiet usbhid.mousepoll=1"`

Save and exit.

- `sudo update-grub`
- `sudo update-grub2`
- `sudo reboot`

You can check your mouse polling rate, opening a terminal and typing:

- `cd /`
- `cat sys/module/usbhid/parameters/mousepoll`

If you get "1", then mouse polling rate (1000 Hz) is ENABLED.

## Fix hid-generic 0003:1D57:FA0A.0002: usb_submit_urb(ctrl) failed: -1

Open a terminal and type:

- `cd /`
- `sudo pluma /etc/default/grub`

In that file, look for the line that says `"GRUB_CMDLINE_LINUX_DEFAULT ="quiet"` and add the following:

`usbhid.quirks=0x1D57:0xFA0A:0x20000000`

The line should look like this:

`"GRUB_CMDLINE_LINUX_DEFAULT="quiet usbhid.quirks=0x1D57:0xFA0A:0x20000000"`

Save and exit.

- `sudo update-grub`
- `sudo update-grub2`
- `sudo reboot`

Tools for Vorago 404 "gaming mouse" under GNU/Linux. Coming soon... ;-)´
