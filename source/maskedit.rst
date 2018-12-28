Mask editing
============

The cpu movement detection can use a mask to prevent triggering from specific areas of the view.

The mask is edited on the main web page using an overlay on the live view.

When the live view is active, clicking on 'edit mask' overlays the live view with a grid, showing the
individual cells of the mask. 'edit mask' changes to 'finish edit'.

.. image:: _static/mask1.png

Use the mouse to turn on or off blocks of cells in the mask. Initially all cells are off (NOT masked).
Left click on any cell will enable that cell in the mask, and by holding the mouse down and dragging,
a rectangular area can be enabled in a single operation. Just release the mouse button to complete
an area. Masked areas have a blue wash applied.

.. image:: _static/mask2.png

To turn off a cell or block of cells hold the shift key down as the mouse button is clicked. (Shift can
be released after the mouse button is clicked).

Once editing is complete click on 'finish edit' about the live view. A small prompt screen appears, enter
a name for the mask in the field provided and the mask is saved on the raspberry pi. It can later be selected
in the cpumovetab before enabling detection.
