**Please note:** This extension now uses the contents service of IPython 3.x currently under development. If you really need to use it with IPython 2.x, you will need to get an older version of this extension from Github. As the older version was really an unsafe hack, please don't.

Description
===========
This IPython notebook extension adds system clipboard actions for single or multiple cells. It allows cut/copy/paste operation of notebook cells and images. Images will be saved to the directory where the current notebook sits. There is currently no way to embed images in markdown cells, due to the google-caja sanitizer used to prevent malicous code execution.

Multi-cell operation is possible using the `rubberband` extension from this repository.

This extension works only for Chrome, as other browsers do not expose the system clipboard to Javascript.

| Hotkey | Function |
|--------|----------|
| CTRL+C | Copy cell to system clipboard             |
| CTRL+X | Cut cell and copy to system clipboard     |
| CTRL+V | Paste cell or image from system clipboard |

A demo showing single-cell copy&paste operating in Chrome here:
http://youtu.be/iU9dNe4vMUY

## Installation
From IPython simply call
```python
import IPython
IPython.html.nbextensions.install_nbextension('https://github.com/ipython-contrib/jupyter_contrib_nbextensions/raw/master/src/jupyter_contrib_nbextensions/nbextensions/chrome_clipboard/main.js')
```

Then load the extension from within the IPyton notebook:
```javascript
%%javascript
IPython.load_extensions('chrome_clipboard');
```
Alternatively, you can add the load command to your `custom.js`. Take a look at the general installation instructions in the Wiki if you are unsure how to proceed.

This extension was tested using Windows and Chrome. Feedback and improvements are welcome.

## Internals
Regarding copying notebook cells over the clipboard, they are stored as mime-type `notebook-cell/json`.
