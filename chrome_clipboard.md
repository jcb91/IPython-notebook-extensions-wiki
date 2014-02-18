** This is an experimental notebook extension **
This IPython notebook extension adds system clipboard actions. It allows cut/copy/paste operation of notebook cells and images. This works only for Chrome.

| Hotkey | Function |
|--------|----------|
| CTRL+C | Copy cell to system clipboard             |
| CTRL+X | Cut cell and copy to system clipboard     |
| CTRL+V | Paste cell or image from system clipboard |

A demo showing copy&paste operating in Chrome here:
http://youtu.be/iU9dNe4vMUY

## Installation

Add `require(['/static/custom/chrome_clipboard.js'])` to your `custom.js` 
Copy the file `chrome_clipboard.js` to your `/static/custom/` directory of your IPython profile and add
```javascript
require(['/static/custom/chrome_clipboard.js'])
```
to your `custom.js` file so it looks like this:

```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/chrome_clipboard.js'])
});
```
This extension was tested using Windows and Chrome. Feedback and improvements are welcome.

## Internals
Graphics imported into the notebook are storead as base64 coded binary. Importing large graphics therefore increases the size of the IPython notebook *.ipynb file. There is a warning for images > 100K in size, so please consider linking to large graphics instead of embedding them into the notebook.

The IPython developers do not reccomend puting large binary data into a notebook cell intended for text. On the other hand, there is no direct risk involved, as long as you keep your embedded graphics to a reasonable size and do not try to edit cells with embedded graphics (see next paragraph).

Because the graphics are encapsulated in a markdown cell using `<img src="..." />` tags with base64 encoding, editing such a cell is not a good idea. Best case is it will take a while to show the cell source, worst case is it will crash your browser. Therefore markdown cells with embedded graphics are set to read-only mode (`cell.read_only = true').

Regarding copying notebook cells over the clipboard, they are stored as mime-type `notebook-cell/json`.
