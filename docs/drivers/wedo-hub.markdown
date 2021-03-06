---
autogen: This file was automatically generated by kernel-doc-text-to-markdown.py
title: WeDo Hub
---

The LEGO WeDo hub device provide a high level interface to the WeDo.
Each hub has two ports - `port0` and `port1` - that are capable of
autodetecting WeDo compatible devices that are connected to the WeDo hub.

The WeDo hub was designed to be a HID device, and the `hidraw` driver
will automatically bind to the WeDo hub. This behaviour can be
overridden with the following udev rule:

    SUBSYSTEM=="usb", ATTRS{idVendor}=="0694", ATTRS{idProduct}=="0003" ACTION=="add", \
        RUN+="/bin/sh -c 'echo $kernel > /sys/bus/usb/drivers/usbhid/unbind;           \
                          echo $kernel > /sys/bus/usb/drivers/legowedo/bind'"

### sysfs Attributes

WeDo `hub` devices can be found at `/sys/bus/wedo/devices/hub<N>`, where `<N>`
is incremented each time a WeDo hub is plugged in to a USB port (it is
not related to which USB port the hub is plugged in to).
Use the `dmesg` log to determine which USB port particular hub device is
plugged into.

`error` (read-only)
: Returns a 1 if the output current source has detected an error - most
likely due to a stalled motor. If everything is OK, 0 is returned.

`clear_error` (write-only)
: Clears an error condition. Write a 1 to begin the clear operation. It
is not necessary to write a 0 to stop clearing the error.

`high_power` (read/write)
: Sets or clears the high power (500 mA) capability of the output port. A
value of 1 will request 500 mA from the USB port that the WeDo is
plugged into. Returns 1 of the USB port is able to supply 500 mA to the
WeDo hub, 0 if only 100 mA is available.

`shut_down` (write-only)
: Sets or clears the shut_down state of the WeDo hub. Writing 1 to this
attribute turns off the output driver for both ports, writing a 0
turns the output port back on.

`reset` (write-only)
: Sets or clears the reset state of the WeDo hub. Writing 1 to this
attribute sets the output state to off and clears any errors.

`voltage` (read-only)
: Returns the voltage being supplied to the WeDo hub by the USB port, in
millivolts. The nominal value is 5000.
