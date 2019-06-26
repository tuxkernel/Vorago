Tools for Vorago 404 "gaming mouse" under GNU/Linux

![Sample Run](https://github.com/tuxkernel/vorago-gaming-mouse-404/blob/master/images/00.png)

#### Official Site: http://www.voragolive.com/mouse-404.php

#### User manual: http://www.voragolive.com/manuales/mo-404.pdf

#### Technical specs: http://www.voragolive.com/fichas/ficha-mouse-optico-vorago-MO-404.pdf

#### Drivers (Windows): http://www.voragolive.com/drivers/mouse/mo-404.rar

#### Enable mouse polling rate (1000 Hz)

#### Method one:

pen a terminal and type:

$ cd /
$ sudo pluma etc/modprobe.d/usbhid.conf

In that file, add the following:

options usbhid mousepoll=1

Save and exit.

$ sudo reboot

#### Method two:

Open a terminal and type:

$ cd /
$ sudo pluma /etc/default/grub

In that file, look for the line that says "GRUB_CMDLINE_LINUX_DEFAULT ="quiet" and add the following:

usbhid.mousepoll=1

The line should look like this:

"GRUB_CMDLINE_LINUX_DEFAULT="usbhid.mousepoll=1 quiet"

Save and exit.

$ sudo update-grub
$ sudo update-grub2
$ sudo reboot

Coming soon... ;-)´
