Runtools provide additional execution modes for code cells:

* Execute a single cell
* Execute from top cell to currently selected cell
* Execute from currently selected cell to bottom cell
* Execute all cells
* Execute all cells, ignore exceptions (requires https://github.com/ipython/ipython/pull/4993)
* Execute marked codecells (cells with green gutter area are marked)
* Stop execution (duplicate to standard toolbar button)

Description
===========
The *runtools* extension adds two button groups to the main toolbar:
![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/runtools.png)

Code execution buttons:
![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/runtools_execute.png)

Codecells can be marked by clicking on the gutter of a codecell or by clicking on the markers toolbar:
![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/runtools_marker.png)

A IPython notebook with marked cells looks like this:
![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/runtools_nb.png)

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
Internals
=========
A `cell.metadata.run_control.marked = true` property is added to a marked codecell.
The "Execute marked codecells" button loops over all codecells an executes only those cells that exhibit this metadata property.
