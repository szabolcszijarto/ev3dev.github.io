---
autogen: This file was automatically generated by kernel-doc-text-to-markdown.py
title: HiTechnic NXT Sensor Multiplexer I2C sensor driver
---

A `ht-smux-i2c-sensor` device is loaded by the [ht-smux-input-port] driver
when it is detected by the [sensor mux] (automatic detection only works with
the sensors listed in the linked page) or when the sensor is set via the
[ht-smux-i2c-host] device. You can use any one of the sensors that has the
`nxt-i2c-sensor` module from the [list of supported sensors]. Keep in mind
though that the [sensor mux] operates in a read-only mode with I2C sensors.
Some modes of I2C sensors require writing data to the sensor and as a result,
these modes will not be usable via the [sensor mux].

### sysfs attributes

These sensors use the [msensor class]. Follow the link for more information.

This device can be found at `/sys/bus/legoev3/devices/in<N>:mux<M>:<device-name>`
where `<N>` is the input port on the EV3 (1 to 4), `<M>` is the input port
on the sensor mux (1 to 4) and `<device-name`> is the name of the sensor
(e.g. `lego-nxt-ultrasonic`).

`device_type` (read-only)
: Returns `ht-smux-i2c-sensor`

`port_name` (read-only)
: Returns the name of the port this host is connected to (e.g. `in1:mux1`).

[sensor mux]: ../hitechnic-nxt-sensor-multiplexer
[list of supported sensors]: ../#supported-sensors
[msensor class]: ../msensor-class
