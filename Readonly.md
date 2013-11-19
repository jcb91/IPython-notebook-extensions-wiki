![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/read_only_ext.png)

Clicking on the lock symbol makes the current cell read-only. This means it can be executed, but the input area cannot be altered. This behavior is persistant, i.e. the information is stored as metadata in the ipynb file. Even when the read-only extension is not loaded, the read-only information is kept, but not applied to the cell.

Costomization
------
The read-only information is stored in the metadata field of the codecell
```
run_control.read_only = true | false
```
and stored in the IPython notebook. 
 