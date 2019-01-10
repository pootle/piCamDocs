Installation and first setup
============================
These notes explain how to get pootlecam running on a clean build of Raspbian Lite (or any other Raspbian build).

Additional software needed by pootlecam
---------------------------------------

After a clean build of raspbian (any version including lite), enable the camera in raspi-config and do your 
preferred extra setup (for example, setting network name, enabling ssh)::   

    sudo apt-get install git python3-pip gpac python3-pigpio python3-numpy

Note that pigpio is only used for gpio related functionality (e.g. using an attached PIR sensor).

Note also that numpy is only used for the CPU based motion detection.

The python camera support and a simple png file hander also needs to be installed::

    sudo pip3 install picamera
    sudo pip3 install pypng

picamera fix
^^^^^^^^^^^^

There seems to be a problem sometimes in picamera, it is `described here <https://github.com/waveform80/picamera/issues/535>`_.
The small edit below will prevent this from causing problems until this is either fixed or a better workaround is in place::

    sudo nano -ET4 /usr/local/lib/python3.5/dist-packages/picamera/streams.py


Note that by default nano will insert tab characters if you use the tab key - which python won't like!. The -ET4 prevents this.
`Also see this fix <https://stackoverflow.com/questions/11173769/how-to-make-the-tab-character-4-spaces-instead-of-8-spaces-in-nano>`_.


replace line 521, which should look like this::

                    self._data[0] = chunk[self._length - self._size:]

with this::

                    try:
                        self._data[0] = chunk[self._length - self._size:]
                    except TypeError:
                        self._length=round(self._length)
                        self._size=round(self._size)
                        self._data[0] = chunk[self._length - self._size:]

installing pootlecam
--------------------

Now you can install pootlecam itself. Pootlecam is in a repository on github. The `repository is here <https://github.com/pootle/piCameraWeb>`_
You can most easily do this using git::

    git clone https://github.com/pootle/piCameraWeb.git

Setup
-----
If you need to use gpio (e.g. PIR motion detection) arrange to start the `pigpio daemon <http://abyz.me.uk/rpi/pigpio/pigpiod.html>`_
on startup::

    sudo crontab -e

and add the line::

    @reboot              /usr/local/bin/pigpiod -c 256 -s 10

The -c 256 parameter runs the daemon in realtime mode - that is it is given a high CPU priority.

The -s 10 parameter means that the daemon runs with a sample rate of 10 microseconds, rather than the default
of 5 microseconds. This reduces the CPU load especially on a Raspberry Pi Zero. For this application a few extra microseconds to trigger
something is not important.

If you want to start pootlecam automatically on boot a simple way is::

    crontab -e

and add this line at the end of the file::

    @reboot              ~/piCameraWeb/start.sh

(adjust the folder name to match the folder this package is in.)

Test running
------------

Before rebooting, or if you don't have the start script run automatically, you can run the program interactively. This is a slight 
variation on the command used in start.sh as it logs messages to the console.

Remember to cd piCameraWeb (or whatever folder you installed to).::

    python3 webserv.py -v 10 -c dummyConfig.py

The first line logged identifies the ip address and port that the web server is using. Copy and paste this to a web browser to see the web site.
You can run the web browser on any local PC, phone or tablet. (Local means in network terms, on the same subnet)

You should now see a screen something like this:

.. image:: _static/screen1.png
