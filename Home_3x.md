The IPython notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

#Overview for IPython Version 3.x
The repository is organized in different categories: 

| Name | Description |
|------------|-------------|
| [usability](#usability)  | Additional functionality for the notebook            |
| [publishing](#publishing) | Getting your notebooks out in the wild               |
| [styling](#styling)    | Styling schemes for different looks of the notebook  |
| [slidemode](#slidemode)  | Slideshow creation                                   |
| [testing](#testing)    | Extensions in a early stage                          |

##Usability

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| [chrome_clipboard](wiki/chrome_clipboard) | Add system clipboard actions with crome      |
| [codefolding](wiki/Codefolding)  | Fold code blocks using Alt-F or clicking on gutter            |
| [comment-uncomment.js](wiki/Comment-uncomment) | Toggle comments in selected lines using Alt-C   |
| [executeTime.js](wiki/execute_timings) | Display when each cell has been executed and how long it took          |
| [drag-and-drop](wiki/drag-and-drop) | Allow dragging of images into a notebook         |
| [hide_input_all](wiki/hide_input_all) | Hide all codecells in a notebook      |
| [navigation-hotkeys.js](wiki/navigation_hotkeys) | Change hotkeys for navigation in notebook  |
| [python-markdown.js](wiki/python-markdown) | Display Python variables in markdown  |
| [read-only.js](wiki/Readonly) | Allow codecells to be set read-only, so no editing is possible   |
| [rubberband](wiki/Rubberband) | Multi-cell selection tool   |
| [runtools](wiki/Runtools) | Add toolbar buttons for additional code execution options   |
| [shift-tab.js](wiki/Shift-tab) | Assign "shift-tab" key to dedent tabulator                      |

##Publishing

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| [printview-button](wiki/Printview-button)	   | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile.                   |
| gist_it                             |  Publish notebook as a gist  |
| nbviewer_theme | |
| [htmltools/js_highlight.py](wiki/js_highlight.py) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter |

##Styling

| File or Directory      | Description                                  | 
| ---------------------- |----------------------------------------------|
| styling/css_selector   |                                              |
| styling/zenmode        |                                              |

##Slidemode

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| slidemode              | Make slide creation for reveal.js easier                                          |

##Testing

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| [hierarchical_collapse](wiki/hierarchical_collapse)  |  Adds a button to hide all cells below the selected heading |
| history              |   |
| swc             |   |
| cellstate       |   |


# General installation instruction
Installing and activating notebook extensions works differently in IPython 3.x compared to 2.x.
It is still possible to use the old method and modify `custom.js`. Using new method is encouraged, however.

##1.Install the notebook extension repository:
First install the notebook extensions repository on your local `.ipython/nbextensions` directory. The new subdirectory is calles `IPython-notebook-extensions-master`.
*Note: This will overwrite a previous version this installation*

There is a helper function in IPython that will do this automatically for you:
```Python
import IPython.html.nbextensions as nb
ext= 'https://github.com/ipython-contrib/IPython-notebook-extensions/archive/master.zip'
nb.install_nbextension(ext)
```
##2. Loading an extension
To load the extension you need to provide the name and local path without the `.js` extension:
```Javascript
%%javascript
IPython.load_extensions('IPython-notebook-extensions-master/usability/python-markdown');

##2. Automatically loading extensions
For the time being, there is no nice GUI to do this. The easiest way to enable an extension is to use
the requests module and communicate with the IPython config service directly. 
For example, to activate the `python-markdown` extension, you need to provide the name and local path without the `.js` extension and call the config service in IPython:
```Python
import requests
import json

extensions={}
notebook_config = {}
extensions['IPython-notebook-extensions-master/usability/python-markdown'] = True
notebook_config['load_extensions'] = extensions

payload = json.dumps(notebook_config)
r = requests.patch('http://127.0.0.1:8888/api/config/notebook', data=payload)
if r.ok == True:
    print("OK")
```
You can easily add more extensions by adding more lines like this:
```Python
extensions['IPython-notebook-extensions-master/usability/runtools/main'] = True
extensions['IPython-notebook-extensions-master/usability/codefolding/main'] = True
```

##3. Deactivating extensions
To deactivate an extension from being reloaded, you use a very similar approach talking to the IPython config service. In this case you specify `None` as value with the extension name as key:
`extensions['IPython-notebook-extensions-master/usability/python-markdown'] = None`

Full example:
```Python
import requests
import json

extensions={}
notebook_config = {}
extensions['IPython-notebook-extensions-master/usability/python-markdown'] = None
notebook_config['load_extensions'] = extensions

payload = json.dumps(notebook_config)
r = requests.patch('http://127.0.0.1:8888/api/config/notebook', data=payload)
if r.ok == True:
    print("OK")
```

##4. Viewing activated extensions
You can generate a table of currently activated extensions this way:
```Python
r = requests.get('http://127.0.0.1:8888/api/config/notebook')
if r.ok == True:
    print("OK")
import json
notebook_config=r.json()

from IPython.display import HTML
extensions = notebook_config['load_extensions']
table = ""
for ext in extensions:
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

## Manual installation
First you need to find your local IPython directory. This can be done from command line:
```
ipython locate
```
or in IPython by executing:
```python
import IPython
ip=IPython.get_ipython()
ip.ipython_dir
```
Now copy your notebook extension files in the `nbextensions` subdirectoy.

## Interactive loading of a notebook extension
Once the notebook extension has been installed, they can be loaded like this:
```javascript
%%javascript
IPython.load_extensions('gist');
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
    `http://127.0.0.1:8888/nbextensions/gist.js`
3. Check for error messages in the JavaScript console. 
