Description
===========

This IPython notebook extension adds system clipboard actions for single or multiple cells. It allows cut/copy/paste operation of notebook cells and images. Images will be saved to the directory where the current notebook sits. There is currently no way to embed images in markdown cells, due to the google-caja sanitizer used to prevent malicous code execution.

Multi-cell operation is possible using the `rubberband` extension, also  in this repository.

This extension works only for Chrome, as other browsers do not expose the system clipboard to Javascript.

| Hotkey | Function |
|--------|----------|
| CTRL+C | Copy cell to system clipboard             |
| CTRL+X | Cut cell and copy to system clipboard     |
| CTRL+V | Paste cell or image from system clipboard |

A demo showing single-cell copy&paste operating in Chrome here:
http://youtu.be/iU9dNe4vMUY


Installation
============

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)

This extension was tested using Windows and Chrome. Feedback and improvements are welcome - you can open issues at the main repository.


Internals
=========

Regarding copying notebook cells over the clipboard, they are stored as mime-type `notebook-cell/json`.
