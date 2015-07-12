The IPython notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

#Notebook extensions for IPython/Jupyter Version 3.x
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
| [navigation-hotkeys](navigation_hotkeys) | Change hotkeys for navigation in notebook | working |
| [python-markdown](python-markdown_v3) | Display Python variables in markdown | working |
| [read-only.js](Readonly) | Allow codecells to be set read-only, so no editing is possible   | untested |
| [rubberband](Rubberband) | Multi-cell selection tool   | working |
| [runtools](Runtools) | Add toolbar buttons for additional code execution options  | working |
| [skip-traceback](Skip-Traceback) | Don't display traceback, only error type and message | working |

##Publishing

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| [printview](Printview) | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile.     | working |
| [htmltools/js_highlight.py](js_highlight.py) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter | untested |

# General installation instruction
Installing and activating notebook extensions works differently in IPython 3.x compared to 2.x.
It is still possible to use the old method and modify `custom.js`. Using new method is encouraged, however.

* There is a graphical interface for activating/deactivating notebook extensions now. You might want to use it:
[config-extension](config-extension)

* If you are using Anaconda, you can try using one of the conda packages on binstar (the standard installation steps below will install the package to the standard system paths, not the custom Anaconda paths; note also that  these packages are updated manually and may lag behind the Github repository):
 * (Windows or Mac) ```conda install -c https://conda.binstar.org/juhasch nbextensions```
 * (Linux) ```conda install -c https://conda.binstar.org/ostrokach nbextensions``` 

##1.Install the notebook extension repository:
First install the notebook extensions repository on your local `.ipython/nbextensions` directory. The new subdirectory is calles `IPython-notebook-extensions-3.x`.

*Note: This will overwrite a previous version of this installation*

There is a helper function in IPython that will do this automatically for you:
```Python
import IPython.html.nbextensions as nb
ext= 'https://github.com/ipython-contrib/IPython-notebook-extensions/archive/3.x.zip'
nb.install_nbextension(ext)
```
##2. Loading an extension
To load the extension you need to provide the name and local path without the `.js` extension:
```Javascript
%%javascript
IPython.load_extensions('IPython-notebook-extensions-3.x/usability/python-markdown/main');
```

##2. Automatically loading extensions
For the time being, there is no nice GUI to do this. The easiest way to enable an extension is to use
the requests module and communicate with the IPython config service directly. 
For example, to activate the `python-markdown` extension, you need to provide the name and local path without the `.js` extension and call the config service in IPython:
```Python
from IPython.html.services.config import ConfigManager
ip = get_ipython()
cm = ConfigManager(parent=ip, profile_dir=ip.profile_dir.location)
cm.update('notebook', {"load_extensions": {"IPython-notebook-extensions-3.x/usability/runtools/main": True}})
```

##3. Deactivating extensions
To deactivate an extension from being reloaded, you use a very similar approach talking to the IPython config service. In this case you specify `None` as value with the extension name as key.

Full example:
```Python
from IPython.html.services.config import ConfigManager
ip = get_ipython()
cm = ConfigManager(parent=ip, profile_dir=ip.profile_dir.location)
cm.update('notebook', {"load_extensions": {"IPython-notebook-extensions-3.x/usability/runtools/main": None}})
```

##4. Viewing activated extensions
You can generate a table of currently activated extensions this way:
```Python
from IPython.html.services.config import ConfigManager
from IPython.display import HTML
ip = get_ipython()
cm = ConfigManager(parent=ip, profile_dir=ip.profile_dir.location)
extensions =cm.get('notebook')
table = ""
for ext in extensions['load_extensions']:
    table += "<tr><td>%s</td>\n" % (ext)

top = """
<table border="1">
  <tr>
    <th>Extension name</th>
  </tr>
"""
bottom = """
</table>
"""
HTML(top + table + bottom)

```

# Manual installation
First you need to find your local IPython directory. This can be done from command line:
```
ipython locate
```
or in IPython by executing:
```python
ip=get_ipython()
ip.ipython_dir
```
Now copy your notebook extension files from the .zip package to the `nbextensions` subdirectoy.

## Interactive loading of a notebook extension
Once the notebook extension has been installed, they can be loaded like this:
```javascript
%%javascript
IPython.load_extensions('IPython-notebook-extensions-3.x/usability/runtools/main');
```
## Automatic loading of a notebook extension
If you want an extension to be always loaded, you need to call it in your local `custom.js` file.
First locate your profile directory:
```python
import IPython
ip=IPython.get_ipython()
ip.config.ProfileDir 
```
This will give you something like
`{'location': u'C:\\Users\\me\\.ipython\\profile_dev'}`
or for Unix
`{'location': u'/home/you/.ipython/profile_default'}`

So your file will be located here:
`/home/you/.ipython/profile_default/static/custom/custom.js`

This is where you add a line to call your notebook extension.
How to do this is described in the next section.

## Troubleshooting
If the extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/IPython-notebook-extensions-3.x/usability/runtools/main.js`
3. Check for error messages in the JavaScript console of the browser. 

Feel free to improve this Wiki documentation.