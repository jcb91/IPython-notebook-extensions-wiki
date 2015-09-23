Multi-Cell selection using a rubberband. This extension is only available for IPython versions 3.x and 4.x.


Description
===========

The *rubberband* extension allows selecting multiple cells. Cells are selected by pressing `shift` or `ctrl`+`shift` + left mouse button click and dragging the rubber band over the cells.

* `shift` + left mouse button : select cells that are currently touched by the rubberband
* `ctrl` + `shift` + left mouse button : select cells that were touched by the rubberband

The `ctrl`+`shift` action is useful when scrolling inside the notebook. Scrolling is activated when the mouse reaches the upper or lower boundary of the notebook area. For now, the mouse has to be moved to achieve continuous scrolling.

A short video demonstrating the rubberband extension can be found here:
[![screenshot](https://cloud.githubusercontent.com/assets/2445216/4668769/b6dd5b72-5567-11e4-9b55-558da6da027c.jpg)](http://youtu.be/TOPfWhqa3oI)


Two other extensions make use of this feature: exercise and [Chrome Clipboard](Chrome-Clipboard).


Installation
============

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)


Internals
=========

New metadata element added to each cell:
* `cell.metadata.selected` - means this cell is selected
