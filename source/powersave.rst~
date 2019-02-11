Power savings
=============

Here are some of the ways to save power.

Turn off hdmi
-------------

edit::

    sudo nano /etc/rc.local

and add these lines BEFORE the exit 0::

    # Disable HDMI
    /usr/bin/tvservice -o

Turn off the camera LED
-----------------------

The camera LED is quite bright and in low light can cause reflections as well as making the pi 'obvious' at night.

edit::

    sudo nano /boot/config.txt

and add the following at the end::

    # Disable camera LED
    disable_camera_led=1


Turn off activity LED -Pi ZERO ONLY!
------------------------------------

LEDs on other versions require different settings. 'See here <https://www.jeffgeerling.com/blogs/jeff-geerling/controlling-pwr-act-leds-raspberry-pi>'_.

edit::

    sudo nano /boot/config.txt

and add the following at the end::
    
    # Disable the ACT LED on the Pi Zero.
    dtparam=act_led_trigger=none
    dtparam=act_led_activelow=on

Convert USB port to USB1.1
--------------------------

DO NOT DO THIS if you want to use a LAN connection or USB connected storage (usb memory stick or usb conencted disc drive.

It is no problem for the wifi as that does not use the usb interface 

edit::

    sudo nano /boot/cmdline.txt

and add the line::

    dwc_otg.speed=1

