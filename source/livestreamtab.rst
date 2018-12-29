live stream tab
===============

The live stream tab shows the status of the live stream feed and allows the resolution to be set.

The default resolution (640 x 480) provides a reasonably detailed view without loading the system too much.

On Raspberry Pi Zeros, if there are other streams active, it can help to turn the resolution down if you want it
permanently on view.

Reducing resolution also helps if there are network problems (such as a poor wifi signal to the raspberry pi).

Note that on the main screen, the live stream is always the same size on screen - even when changed here. The stream
is resized in the web browser to do this. This reduces network bandwidth and load on the Raspberry Pi.

displaying the live stream in other web pages
---------------------------------------------

The live stream can also be viewed from other web pages. The page 'vstream.mjpg' within the website will display the live stream feed.
(for example 'http://192.168.0.123:8000/vstream.mjpg'). Viewing this way will show the real size of the stream.

Note that at higher frame rates only a small number of streams can be active before the wifi will start to choke. Lan (Ethernet) 
connection will improve this somewhat (using a dongle on a raspberry Pi Zero).

live stream fields
------------------

Note that there is no button to start / stop the live stream, as the stream is started and stopped from the live stream area on the
main screen.

state
    Shows the current state of this stream. See :ref:`state field for details <common-field-state>`.

stream resolution
    The feed from the camera (which can be of much higher resolution) is scaled to this size. See Common Tab fields for details.

started at
    The local time the stream last started. See :ref:`started at field for details <common-field-started-at>`.

stopped at
    The local time the stream last stopped. See :ref:`stopped at field for details <common-field-stopped-at>`.
    