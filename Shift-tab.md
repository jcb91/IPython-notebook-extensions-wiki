The dedent hotkey for the IPython notebook is `Ctrl-]`. Unfortunately, for non-US keyboards it is difficult or even impossible to generate this key combination.

Therefore, the <b>shift-tab</b> extension allows using `Shift-tab` keys for dedent operation.

## Installation
Copy the file `shift-tab.js` to the `/nbextensions/usability/` directory of your local `.ipython` directory.
Then load the extension from within the IPyton notebook:
```javascript
%%javascript
IPython.load_extensions('usability/shift-tab');
```

Alternatively, you can add the load command to your `custom.js`. Take a look at the general installation instructions in the Wiki if you are unsure how to proceed.

## Internals
The extension registers `Shift-tab` to the IPython `keyboard_manager` and calls the `indentLess` command in codemirror when `shift-tab` is pressed. Be aware, this overrides the configuration to show docstrings when pressing `shift-tab`. Your choice...

