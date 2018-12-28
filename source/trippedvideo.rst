tripped video
=============

The tripped video tab controls and enables video recordings to be triggered by other activities. So far this means cpu based movement 
detection or using external hardware that can interface with a gpio input pin.

It allows a few seconds of video from before the trigger to be combined with video that runs until several seconds after the last trigger
occurs.

It works by continuously recording to a circular buffer, and when triggered, it switches recording to a temporary file, and saves (part of)
the circular buffer to another temprary file, and finishes by using MP4Box to merge the 2 files into an mp4 file.

tripped video fields
--------------------

state
    Shows the current state of this stream. See :ref:`state field for details <common-field-state>`.

stream resolution
    The feed from the camera (which can be of much higher resolution) is scaled to this size. 
    See :ref:`stream resolution field for details <common-field-stream-res>`.

pre-trigger record time
    This is the number of seconds from before the trigger happens to use at the start of the video. The time is approximate and can vary, expecially
    at low frame rates.

post trigger record time
    The video keeps running until this number of seconds after the last trigger time.

video folder
    This field needs changing it doesn't work properly. Should be the base folder for video recordings
    
filename
    The filename used for video files. Can include folders as well as the final file name.

start recording
     This button starts the recorder so it will create video files when triggered. If it is already running, it stops it.

recordings
    The count of recordings in this session

last trigger time
    The last (local) time a video was triggered

started at
    The local time the stream last started. See :ref:`started at field for details <common-field-started-at>`.

stopped at
    The local time the stream last stopped. See :ref:`stopped at field for details <common-field-stopped-at>`.

