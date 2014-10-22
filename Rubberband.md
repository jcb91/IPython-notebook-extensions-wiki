Multi-Cell selection using a rubberband

Description
===========
The *rubberband* extension allows selecting multiple cells. It is still a work-in-progress.

Two other extensions make use of this feature: exercise and chrome_clipboard.

Installation
============
Copy the `rubberband` directory to a new `/nbextensions/usability/rubberband` directory of your user's IPython directory and add
```javascript
IPython.load_extensions('usability/rubberband/main')
```
to your `custom.js` file. Take a look at the general installation instructions in the Wiki if you are unsure how to proceed.

Internals
=========

New metadata element added to each cell:
* `cell.metadata.selected` - means this cell is selected

