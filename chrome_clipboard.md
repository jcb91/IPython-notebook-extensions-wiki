**Please note:** This extension now uses the contents service of IPython 3.x currently under development. If you really need to use it with IPython 2.x, you will need to get an older version of this extension from Github. As the older version was really an unsafe hack, please don't.

This IPython notebook extension adds system clipboard actions for single cells. It allows cut/copy/paste operation of notebook cells and images. This works only for Chrome.

| Hotkey | Function |
|--------|----------|
| CTRL+C | Copy cell to system clipboard             |
| CTRL+X | Cut cell and copy to system clipboard     |
| CTRL+V | Paste cell or image from system clipboard |

A demo showing copy&paste operating in Chrome here:
http://youtu.be/iU9dNe4vMUY

## Installation
## Installation
From IPython simply call
```python
import IPython
IPython.html.nbextensions.install_nbextension('https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/usability/chrome_clipboard.js')
```

Then load the extension from within the IPyton notebook:
```javascript
%%javascript
IPython.load_extensions('chrome_clipboard');
```
Alternatively, you can add the load command to your `custom.js`.

This extension was tested using Windows and Chrome. Feedback and improvements are welcome.

## Internals
Regarding copying notebook cells over the clipboard, they are stored as mime-type `notebook-cell/json`.
