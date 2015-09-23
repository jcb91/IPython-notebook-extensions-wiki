This extension hides Python tracebacks and only displays the error type and name.

![](skip-traceback.png)

After loading the extension, only newly executed cells are affected. Previous tracebacks will remain visible until the corresponding cell is executed again.

If you press the button on the toolbar with the exclamation mark, you can turn on tracebacks again.


Installation
============

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)


Internals
=========

This extensions works by overriding the `OutputArea.prototype.append_error` function, replacing it with a new function that only displays the error type and message.
