# Tools for Vorago 404 "gaming mouse" under GNU/Linux

![Sample Run](https://raw.githubusercontent.com/tuxkernel/Vorago/master/images/00.png)

## lsusb: Bus 005 Device 002: ID 1d57:fa0a Xenta

## Understanding mouse polling rate

- 1000 Hz = `options usbhid mousepoll=1`
- 500 Hz = `options usbhid mousepoll=2`
- 250 Hz = `options usbhid mousepoll=4`
- 125 Hz = `options usbhid mousepoll=8`

### Set mouse polling rate. Method one (via `etc/modprobe.d/`):

Open a terminal and type:

- `cd /`
- `sudo pluma etc/modprobe.d/usbhid.conf`

In that file, add the following:

`options usbhid mousepoll=1`

Save and exit.

- `sudo modprobe -r usbhid && sudo modprobe usbhid`

You can check mouse polling rate, opening a terminal and typing:

- `cd /`
- `cat sys/module/usbhid/parameters/mousepoll`

If you see "**1**", then mouse polling rate (1000 Hz) is **enabled**.

### Set mouse polling rate. Method two (via boot kernel module parameter):

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
- `sudo modprobe -r usbhid && sudo modprobe usbhid`

You can check mouse polling rate, opening a terminal and typing:

- `cd /`
- `cat sys/module/usbhid/parameters/mousepoll`

If you see "**1**", then mouse polling rate (1000 Hz) is **enabled**.

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
