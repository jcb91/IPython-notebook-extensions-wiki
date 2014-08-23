 __For 2.x:__ This extension provides a toolbar button to call the menu item `File->Print Preview` directly.

 __For 3.x:__ This extension provides a toolbar button to call `nbconvert` with your current profile and shows the output in a new browser window.

## Installation
Copy the `publishing/printviewmenu_button.js` file to `/nbextensions/publishing/printviewmenu_button.js` in your IPython notebook server installation, and either load it by executing this cell
```Javascript
%%Javascript
IPython.load_extensions('publishing/printviewmenu_button')
```
or add `IPython.load_extensions('publishing/printviewmenu_button')` to `custom.js` in your profile's `/static/custom` directory.
