This extension allows hiding all codecells of a notebook. This can be achieved by clicking on the button toolbar:
![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/wiki-images/toggle_codecells.png)

Typically, all codecells are shown with their corresponding output:
![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/wiki-images/hide_input_all_show.png)

Clicking on the "Toggle codecell display" toolbar button hides all codecells:
![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/wiki-images/hide_input_all_hide.png)

## Internals
The codecell hiding state is stored in the metadata `IPython.notebook.metadata.hide_input`.
If it is set to `true`, all codecells will be hidden on reload.

## Installation
Copy the `hide_input_all.js` file, and add `require(['/static/custom/hide_input_all.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/hide_input_all.js'])
});
```
