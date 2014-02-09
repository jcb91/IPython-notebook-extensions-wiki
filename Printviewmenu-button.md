This extension provides a toolbar button to call the menu item `File->Print Preview` directly.

## Installation
Copy the `printpreviewmenu_button.js` file, and add `require(['/static/custom/printpreviewmenu_button.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/printpreviewmenu_button.js'])
});
```
