This extension adds a button to the toolbar that calls nbconvert on the notebook server:

![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/printview-button.png)

When pressing the button on the toolbar, the following python command is executed:
```python
import os; os.system(\"ipython nbconvert --to html ' + notebookname + '\")
```
This leaves the resulting static html file from your notebook in the directory where the notebook resides. Additionally, a new tab in the browser is opened and the generated static html file of the notebook is displayed.

## Installation
Add `require(['/static/custom/printview_button.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  require(['/static/custom/printview_button.js'])
});
```