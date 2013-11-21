This extension adds a button to the toolbar that calls nbconvert on the notebook server:

![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/nbconvert-button.png)

When pressing the button on the toolbar, the following python command is executed:
```python
import os; os.system(\"ipython nbconvert --to html ' + name + '\")
```
Where `name` ist the name of the current IPython notebook. 
This leaves the resulting static html file from your notebook in the directory where the notebook resides.
