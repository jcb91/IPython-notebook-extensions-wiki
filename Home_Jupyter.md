The Jupyter notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

## Now where in the world did everything go ?
Jupyter/IPython 4.x works differently than IPython 3.x.

In short
----
* The notebook was split from IPython. You need to install both to run the notebook with IPython now. The easiest way is to use Anaconda and do a `conda install jupyter`
* There are no profiles anymore. You can specify environment variables to change the default, see [Jupyter ML](https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!topic/jupyter/7q02jjksvFU)].
* The configuration has moved to a new place. To find out where, see below.
* There is a kind of automatic upgrade of the configuration files from IPython 3.x to Jupyter.

## So where can I find things now?
To find where the configuration files are, start IPython 
```Python
from __future__ import print_function
from jupyter_core.paths import jupyter_config_dir, jupyter_config_path
print(jupyter_config_dir())
print(jupyter_config_path)
```
`jupyter_config_dir()` shows you where your *local* configuration files are, `jupyter_config_path` shows you where Jupyter will look for configuration files. For the notebook, there are two files that will be used:
`jupyter_notebook_config.py` and `jupyter_notebook_config.json`. 

The `nbextension` directory has moved to a different location and can be found in one of these directories:
```Python
from __future__ import print_function
from jupyter_core.paths import jupyter_data_dir, jupyter_data_path
print(jupyter_data_dir())
print(jupyter_path())
```

## Checking/loading notebook extension from IPython
You can check if the directory or a file (or list of files) exists:
```Python
notebook.nbextensions.check_nbextension('usability/codefolding', user=True)
notebook.nbextensions.check_nbextension('usability/codefolding/main.js', user=True)
```
Make sure to use `user=True` if you have the extensions installed in your local path (in `jupyter_data_dir()`).

To enable an extension:
```Python
E = notebook.nbextensions.EnableNBExtensionApp()
E.enable_nbextension('usability/codefolding/main')
```

To disable an extension:
```Python
D = notebook.nbextensions.DisableNBExtensionApp()
D.disable_nbextension('usability/codefolding/main')
```
The configuration is stored in either `jupyter_config_dir()/notebok.json` or `jupyter_config_dir()/nbconfig/jupyter_config_dir()` depending on your Jupyter version.

If you reload the notebook after enableing the installation, it will be loaded. You can check the Javascript console to confirm.

# Notebook extensions for Jupyter Version 4.x
The repository is organized in different categories: 

| Name | Description |
|------------|-------------|
| [usability](#usability)  | Additional functionality for the notebook       |
| [publishing](#publishing) | Getting your notebooks out in the wild       |

##Usability

| File or Directory      | Description                                            | Status |
| ---------------------- |--------------------------------------------------------|--------|
| [chrome_clipboard](chrome_clipboard_v3) | Add system clipboard actions with crome   | working |
| [codefolding](Codefolding_v3)  | Fold code blocks using Alt-F or clicking on gutter | working |
| [comment-uncomment.js](Comment-uncomment) | Toggle comments in selected lines using Alt-C  | working |
| [executeTime.js](execute_timings) | Display when each cell has been executed and how long it took | working |
| [drag-and-drop](drag-and-drop) | Allow dragging of images into a notebook | working |
| [hide_input_all](hide_input_all) | Hide all codecells in a notebook | untested    |
| [limit-output](limit-output) | Limit codecell output | working |
| [navigation-hotkeys.js](navigation_hotkeys) | Change hotkeys for navigation in notebook | working |
| [python-markdown.js](python-markdown_v3) | Display Python variables in markdown | working |
| [read-only.js](Readonly) | Allow codecells to be set read-only, so no editing is possible   | untested |
| [rubberband](Rubberband) | Multi-cell selection tool   | working |
| [runtools](Runtools) | Add toolbar buttons for additional code execution options  | working |
| [search-replace](search-replace) | Add a toolbar for notebook-wide search and replace  | working |
| [skip-traceback](skip-traceback) | Skip traceback and only display error message  | working |

##Publishing

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| [printview](Printview) | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile.     | working |
| [htmltools/js_highlight.py](js_highlight.py) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter | untested |

# General installation instruction
Installing and activating notebook extensions works differently in Jupyter compared to Python. Please be aware that Jupyter is still in development stage and some commands would change in future. 

* There is a graphical interface for activating/deactivating notebook extensions now. You might want to use it:
[config-extension](config-extension)

##1. Installing an extension

`jupyter-nbextension install <name of extension>`

Example:
`jupyter-nbextension install usability/codefolding/main`

##2. Activating an extension

`jupyter-nbextension enable <name of extension>`

##3. Deactivating extensions

`jupyter-nbextension disable <name of extension>`

## Troubleshooting
If the extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/IPython-notebook-extensions-master/usability/runtools/main.js`
3. Check for error messages in the JavaScript console of the browser. 

Feel free to improve this Wiki documentation.