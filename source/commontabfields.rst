Common tab fields
=================

There are a number of fields that appear on multiple tabs, this section provides more details on these fields than the individual tab sections.

.. _common-field-state:

state
-----

Most activities have a small number of standard states that they use:

* off - The activity has not run since the web service started
* run - The activity is currently running, the time it started is shown in the 'started at' field
* complete - the activity was running, but has now stopped. The time it stopped is shown in the 'stopped at' field

.. _common-field-stream-res:

stream resolution
-----------------

Activities that use the `camera splitter port <https://picamera.readthedocs.io/en/release-1.13/fov.html#pipelines>`_ can resize the video output of the camera to a more suitable size for their own purposes. 
As this resizing is handled by the GPU is is faster and more efficient than code running in the CPU, as well as leaving the CPU to do 
other work.

A list of built in resolutions are provided, mostly 4x3 to match the aspect ratio of the camera sensor. The list is tailored to the model of
camera in use (V1 or V2) and the cpu based motion detection has a special list that goes to smaller sizes than that ysed elsewhere.

.. _common-field-started-at:

started at
----------

This field is one of the last on most tabs. It records the last time the activity started. Before recording a specific time, it will be 'never'

.. _common-field-stopped-at:

stopped at
----------

This field is one of the last on most tabs. It records the last time the activity stopped. Before recording a specific time, it will be 'never'

