This extension adds a button to the toolbar that calls nbconvert on the notebook server:

![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/printview-button.png)

When pressing the button on the toolbar, the following python command is executed:

`ipython nbconvert --profile=<current profile> --to html <notebook name>`

This leaves the resulting static html file from your notebook in the directory where the notebook resides. Additionally, a new tab in the browser is opened and the generated static html file of the notebook is displayed.

Your current profile is used to call nbconvert, allowing you to specify your own templates, pre- and postprocessors. 

## Installation
Copy the `printview_button.js` file, and add `require(['/static/custom/printview_button.js'])` to `custom.js` in your profile's `/static/custom` directory, so it looks like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  require(['/static/custom/printview_button.js'])
});
```

## Internals
Newer IPython versions (> 2.0) will have the ability to operate with subdirectories in the URL.
This extension takes this into account by checking the IPython notebook version and generating the correct path.