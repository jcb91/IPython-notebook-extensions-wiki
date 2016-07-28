Removed extension
=================

This extension is no longer necessary so it has been removed [on pull request 185](https://github.com/ipython-contrib/jupyter_contrib_nbextensions/pull/185).

You can see the last version of the code there if you are interested in the internals
of how it was working. 


Shift tab
---------

The dedent hotkey for the IPython notebook is `Ctrl-]`. Unfortunately, for non-US keyboards it is difficult or even impossible to generate this key combination.

Therefore, the <b>shift-tab</b> extension allows using `Shift-tab` keys for dedent operation.


Installation
============

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)



Internals
=========

The extension registers `Shift-tab` to the IPython `keyboard_manager` and calls the `indentLess` command in codemirror when `shift-tab` is pressed. Be aware, this overrides the configuration to show docstrings when pressing `shift-tab`. Your choice...
