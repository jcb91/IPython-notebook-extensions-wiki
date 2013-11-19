This extension adds codefolding functionality from CodeMirror to a codecell. This functionality is still evolving and will improve in the next versions of CodeMirror. 

After clicking on the gutter (left margin of codecell) or typing `Alt+F`, the code gets folded. See the examples below. The folding status is saved in the cell metadata of the notebook, so reloading of a notebook will restore the folding view.

## Supported modes:
Three different folding modes are supported.

### Indent Folding
Python-style code folding, detetects indented code.
![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/wiki-images/codefolding_indent_unfolded.png)

The unfolded code above can be folded like this:

![](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/codefolding_indent_folded_1.png)

or this:

https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/codefolding_indent_folded_2.png

### Bracked Folding
For other languages like Javascript using brackets to designate code blocks. This works e.g. for Javascript in using the `%%javsscript` magic in a codecell.

### Firstline Comment Folding
Allows collapsing of Python code cells to a single comment line. This is useful for long codecells. The algorithm simply looks for a comment in the first line and allows folding in the rest of the cell.

![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/wiki-images/codefolding_firstline_unfolded.png)

The code above can be folded like this:

https://raw.github.com/ipython-contrib/IPython-notebook-extensions/master/wiki-images/codefolding_indent_folded.png


Installation
============
Copy the `codefolding` directory to you `/static/custom` directory of your IPython profile and add
```javascript
require(['/static/custom/codefolding/codefolding.js'])
```
to your `custom.js` file.

If the codefolding does not always work correctly, try updating the codemirror component of IPython with the current Github master one. Codefolding is still in active development.

