
After installation these buttons should appear on the toolbar:
![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/breakpoint_ext.png)

The extension adds 8 buttons:
![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/breakpoint_ext_buttons.png)

## Installation
Copy the `breakpoints.js` file, and add `require(['/static/custom/breakpoints.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  require(['/static/custom/breakpoints.js'])
});
```
## Internals
The extension registers a codemirror gutter. Currently, this makes it incompatible with the codefolding-extension, as both extensions react on gutter clicks. 

A breakpoint flag is stored as metadata in each cell:
`cell.metadata.run_control.breakpoint = true | false`

As metadata is saved in the IPython notebook, all breakpoints are saved, too.
