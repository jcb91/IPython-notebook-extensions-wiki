This is a higly experimental notebook extension.

It adds two features:
1) Add system clipboard operation, allowing to cut/copy/paste cells in a notebook (Chrome only=
2) Allow drag and drop of images into the notebook (Chrome and Firefox tested)

A demo video showing drag&drop of images is here:
http://youtu.be/buAL1bTZ73c

A demo showing copy&paste operating in Chrome here:
http://youtu.be/iU9dNe4vMUY

## Installation

Add `require(['/static/custom/clipboard_dragdrop.js'])` to your `custom.js` 
Copy the file `clipboard_dragdrop.js` to your `/static/custom/` directory of your IPython profile and add
```javascript
require(['/static/custom/clipboard_dragdrop.js'])
```
to your `custom.js` file so it looks like this:

```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/clipboard_dragdrop.js'])
});
```
This extension was tested using Windows and Chrome. Feedback and improvements are welcome.

## Internals
Graphics imported into the notebook are storead as base64 coded binary. Importing large graphics therefore increases the size of the IPython notebook *.ipynb file.
Because the graphics are encapsulated in an markdown cell using `<embed src="..." />`, editing such a cell is not a good idea. In the best case it will take a while to show the cell source, worst case is crashing the browser. Therefore the markdown cell is set to read-only mode (`cell.read_only = true').
