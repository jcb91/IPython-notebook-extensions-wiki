**For IPython version 2 or greater, please use the `File` menu entries for downloading and print preview instead.**

This extension adds a button to the toolbar that calls nbconvert on the notebook server:

![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/nbconvert-button.png)

When pressing the button on the toolbar, the following python command is executed:
```python
import os; os.system(\"ipython nbconvert --to html ' + name + '\")
```
Where `name` ist the name of the current IPython notebook. 
This leaves the resulting static html file from your notebook in the directory where the notebook resides.

## Installation
Copy the `nbconvert_button.js` file, and add `require(['/static/custom/nbconvert_button.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/nbconvert_button.js'])
});
```
