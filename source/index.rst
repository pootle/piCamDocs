.. pootlecam documentation master file, created by
   sphinx-quickstart on Sun Dec 23 22:41:20 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to pootlecam's documentation!
=====================================
Pootlecam is a python program to use a Raspberry Pi camera that can do various camera related things such
as live streaming, video recording, movement detection and more. It exploits the Raspberry Pi's camera integration
with the GPU to enable all this to run well even on a Raspberry Pi Zero. It makes extensive use of 
the `picamera python module <https://picamera.readthedocs.io/en/release-1.13>`_,
and much of the camera related code is based on examples from that module.

This is the user documentation, it is for anyone that wants to use pootlecam without delving into the python
that makes it all work. 

.. toctree::
   :maxdepth: 2
   :caption: Contents:
   
   startup
   mainscreen
   cameratab
   livestreamtab
   cpumovetab
   gpiomovetab
   trippedvideo
   commontabfields
   maskedit
   