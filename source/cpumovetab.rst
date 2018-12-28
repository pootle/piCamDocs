cpu move
========

The cpu move tab shows the settings and status for the cpu based movement detection.

The cpu based movement detection compares successive frames to see how much has changed, and raises a
trigger based on the size of change in individual pixels and the number of pixels that reach a threshold value.
The trigger is typically used to start a video recording or taking a still image. A mask can be applied to
stop particular areas from causing triggers.

The video feed is resized to a currently fixed size of 64 x 48 before analysis.

The overall cpu used to do this is actually quite small even on a raspberry pi zero.

When movement is detected, the 'triggers' field is incremented and the 'last trigger time' field is set to the current time.

Changes to this field are notified to the main application, which will trigger the 'triggered video' stream if it is active.

Overall detection process
-------------------------

* The main video feed is resized using a pi camera splitter port to the size defined in the field 'stream resolution. This is
  carried out in the GPU so is fast and efficient. The feed converts each frame to 'rgb' or 'yuv' as defined by the field 'image mode'.
  'yuv' mode means it is easy to test just the "brightness" of each pixel to reduce cpu load while still being sensitive.
* if frame ratio is > 1 then the specified number of frames are discarded between each analysis.
* If a mask is active then all pixels that are masked out are set to be ignored.
* The absolute difference between every unmasked pixel in the current and previous images is calculated, using only the channel in the
  field 'channel for test'.
* pixels are marked if the difference is greater than the field 'cell threshold', otherwise they are unmarked.
* if the count of marked pixels is > the field 'cell count' then the trigger fields are changed as described above.

cpu move fields
---------------

state
    Shows the current state of this stream. See :ref:`state field for details <common-field-state>`.

stream resolution
    The feed from the camera (which can be of much higher resolution) is scaled to this size. 
    See :ref:`stream resolution field for details <common-field-stream-res>`.

skip on start
    movement detection skips this number of frames before starting to look for movement. The camera uses a few frames to settle exposure
    and various other parameters when it first starts. This avoids these frames from raising false triggers

frame ratio
    If the movement detection code gets to cpu intensive, this reduces the number of times detection actually runs. 1 means every frame is 
    analysed, 3 means every 1/3rd frame is analysed....
    Currently the detection code will easily handle 30 frames per second at the set resolution.

cell threshold
    The difference between the pixel values is tested for each cell and only cells equal to or above the threshold are marked as changed.
    Note that the fairly small image size used currently also significantly reduces noise in the image to make this less likely to trigger
    accidentally

cell count
    When all the cells have been tested for threshold, this is number of cells that must be marked as changed to cause a trigger event.

image mode
    Either 'rgb' or 'yuv', yuv using channel 0 seems to work well.

channel for test
    Channel to be used for test, can be 0, 1 or 2. This refers to the the channels in the image, so for 'rgb' they are the red, green or blue channels,
    and for 'yuv', they are luminance or 1 of the chrominance channels.

image masks folder
    The folder the mask images are stored in - current fixed in the fields initialisation

use image mask
    The file in the image masks folder to use as a mask before checking for movement. This can also be 'off' if no mask is to be used.

start now
    This button starts cpu based movement detection if it is not running, and stops it if it is running. 

triggers
    The count of triggers in the current run of cpu based movement.

last trigger time
    The last (local) time a movement trigger happened. 

started at
    The local time the stream last started. See :ref:`started at field for details <common-field-started-at>`.

stopped at
    The local time the stream last stopped. See :ref:`stopped at field for details <common-field-stopped-at>`.
