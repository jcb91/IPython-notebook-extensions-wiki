The indent and dedent hotkeys for the IPython notebook are `Ctrl-[` and `Ctrl-]`. Unfortunately, for non-US keyboards it can be difficult or even impossible to generate this key combination.

Therefore, the <b>shift-tab</b> extension allows using `Shift-tab` keys for dedent operation.

## Installation
Copy the `shift-tab.js` file, and add `require(['/static/custom/shift-tab.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/shift-tab.js'])
});
```

## Internals
The extension registers `Shift-tab` for `indentLess` operation in codemirror. Additionally, some magic is required to actually enable this functionality by intercepting the codemirror keyevent function.
