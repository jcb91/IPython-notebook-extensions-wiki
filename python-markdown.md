This extension allows dynamically displaying Python variables in markdown cells.
Example:
If you set variable `a` in Python
```Python
a = 1.23
```
and write the following line in a markdown cell:
```Markdown
a = {{a}}
```
It will be displayed as:
```Markdown
a = 1.23
```

## Further examples
Before rendering the markdown cell:
![before](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/python-markdown-pre.png)

After rendering the markdown cell:
![after](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/python-markdown-post.png)


**Caution:** There is no restriction in the expression you can embedd in `{{ }}`. Be careful as you might crash your browser if you return too large datasets.

## Internals
The extension overrides the `textcell.MarkdownCell.prototype.render` function and searches for a Python expression enclosed in double curly braced `{{ <expr> }}`. It then executes the expression and replaces it with the result returned from Python.
Additionally, the result is saved in the metadata of the markdown cell, i.e. `cell.metadata.variables[varname]`. This stored value is displayed when reloading the notebook.

There is also a preprocessor `pymdpreprocessor.PyMarkdownPreprocessor` to allow `nbconvert` to display the computed variables, when converting to an output file format.

