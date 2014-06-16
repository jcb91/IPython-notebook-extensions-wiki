# Wiki page in progress

This extension displays when the last execution of
a cell occurred and how long it took. This information is displayed in a box attached at the bottom of the input area. 

![](https://github.com/jcjaskula/IPython-notebook-extensions/raw/executeTimings/wiki-images/execution-timings-box.png)

It can be hide by double clicking on the box or using the option in the cell menu. Clicking on the "Toggle codecell display" toolbar button hides all codecells:


![](https://github.com/jcjaskula/IPython-notebook-extensions/raw/executeTimings/wiki-images/execution-timings-menu.png)

## Internals
The codecell hiding state is stored in the metadata `IPython.notebook.metadata.hide_input`.
If it is set to `true`, all codecells will be hidden on reload.

## Installation
Copy the `executeTime.js` file, and add `require(['/static/custom/executeTime.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/executeTime.js'])
});
```
