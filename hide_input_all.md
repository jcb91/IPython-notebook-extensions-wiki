This extension allows hiding all codecells of a notebook. This can be achieved by clicking on the button toolbar:
![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/wiki-images/toggle_codecells.png)

## Installation
Copy the `hide_input_all.js` file, and add `require(['/static/custom/hide_input_all.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/hide_input_all.js'])
});
```