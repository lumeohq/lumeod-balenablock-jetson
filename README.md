# Lumeo Gateway Balena Block

> Currently only supports Jetson Xavier NX


# Additional Info
When you use this block in your application, be sure to log into your hardware device and set max perf mode : 

```.bash
$ balena ssh <device-uuid>

# NVP Mode 8 sets Jetson NX to 20W, 6 core (max perf).
$ nvpmodel -m 8
```
