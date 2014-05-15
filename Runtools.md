Runtools provide additional execution modes for code cells:

* Execute single cell
* Execute from top to current cell
* Execute from current cell to bottom
* Execute all
* Execute all, ignore exceptions
* Execute marked codecells
* Stop execution 

![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/runtools.png)


Installation
============
Copy the `runtools` directory to a new `/static/custom/runtools` directory of your IPython profile and add
```javascript
require(['/static/custom/runtools/runtools.js'])
```
to your `custom.js` file so it looks like this:

```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/runtools/runtools.js'])
});
```

