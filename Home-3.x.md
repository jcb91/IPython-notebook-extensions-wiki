The IPython/Jupyter notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please [create an issue](https://github.com/ipython-contrib/IPython-notebook-extensions/issues/new) if you encounter any problems.

Some extensions may work with other languages than Python, however this currently has not been tested.


IPython/Jupyter version support
===============================

There are different branches of the notebook extensions in this repository.
Please make sure you use the branch corresponding to your IPython/Jupyter version.
Not all extensions are available for all versions.

| IPython/Jupyter Version             |       Description      |
|-------------------------------------|------------------------|
| 1.x                                 | not supported          |
| [2.x](Home-2.x)                     | checkout 2.x branch    |
| [3.x](Home-3.x)                     | checkout 3.x branch    |
| [4.x (Jupyter)](Home-4.x-(Jupyter)) | checkout master branch |

Note: This is not related to the __Python__ version.


Notebook extensions for IPython/Jupyter Version 3.x
===================================================

The repository is organized in different categories:

| Name                      | Description                                         |
|---------------------------|-----------------------------------------------------|
| [usability](#usability)   | Additional functionality for the notebook           |
| [publishing](#publishing) | Getting your notebooks out in the wild              |
| [styling](#styling)       | Styling schemes for different looks of the notebook |
| [slidemode](#slidemode)   | Slideshow creation                                  |
| [testing](#testing)       | Extensions in a early stage                         |


Usability
---------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| [chrome_clipboard](Chrome-Clipboard)                | Add system clipboard actions with Chrome                       | working  |
| [codefolding](Codefolding)                          | Fold code blocks using Alt-F or clicking on gutter             |          |
| [comment-uncomment.js](Comment-Uncomment)           | Toggle comments in selected lines using Alt-C                  |          |
| [executeTime.js](Execute-Timings)                   | Display when each cell has been executed and how long it took  |          |
| [drag-and-drop](Drag-and-Drop)                      | Allow dragging of images into a notebook                       | working  |
| [hide_input_all](Hide-Input-All)                    | Hide all codecells in a notebook                               |          |
| [limit-output](Limit-Output)                        | Limit codecell output                                          | working  |
| [navigation-hotkeys](Navigation-Hotkeys)            | Change hotkeys for navigation in notebook                      |          |
| [python-markdown](Python-Markdown)                  | Display Python variables in markdown                           |          |
| [read-only.js](Readonly)                            | Allow codecells to be set read-only, so no editing is possible |          |
| [rubberband](Rubberband)                            | Multi-cell selection tool                                      |          |
| [runtools](Runtools)                                | Add toolbar buttons for additional code execution options      |          |
| [search-replace](Search-&-Replace)                  | Add a toolbar for notebook-wide search and replace             | working  |
| [skip-traceback](Skip-Traceback)                    | Don't display traceback, only error type and message           | working  |


Publishing
----------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|----------|
| [printview-button](Printview-Button)                | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile. |          |
| [htmltools/js_highlight.py](Javascript-Highlighter) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter                      | untested |


Styling
=======

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| styling/css_selector                                |                                                                |          |
| styling/zenmode                                     |                                                                |          |


Slidemode
=========

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| slidemode                                           | Make slide creation for reveal.js easier                       |          |


Testing
=======

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| [hierarchical_collapse](wiki/Hierarchical-Collapse) |  Adds a button to hide all cells below the selected heading    |          |
| history                                             |                                                                |          |
| swc                                                 |                                                                |          |
| cellstate                                           |                                                                |          |


General installation instructions
=================================

Installing and activating notebook extensions works differently in IPython 3.x compared to 2.x.
Although it is still possible to use the old 2.x and modify `custom.js`, it is discouraged. Using one of the newer methods below is encouraged.

* If you are using Anaconda, you can try using one of the conda packages on binstar (the standard installation steps below will install the package to the standard system paths, not the custom Anaconda paths; note also that  these packages are updated manually and may lag behind the Github repository):
 * (Windows or Mac) ```conda install -c https://conda.binstar.org/juhasch nbextensions```
 * (Linux) ```conda install -c https://conda.binstar.org/ostrokach nbextensions```


## 1. Installing the notebook extension repository:

First install the notebook extensions repository on your local `.ipython/nbextensions` directory. The new subdirectory is called `IPython-notebook-extensions-3.x`.

*Note: This will overwrite a previous version of this installation*

You can either install extensions locally or system wide. There is a helper function in IPython that will do this automatically for you:

```Python
import IPython.html.nbextensions as nb
ext= 'https://github.com/ipython-contrib/IPython-notebook-extensions/archive/3.x.zip'
nb.install_nbextension(ext)
```

**NB** If you want to install them system wide, as above, you need to be root. Alternatively, you can install them in your local .ipython directory. In order to do that, you need to execute the command with the keyword argument `user` set to `True`:

```Python
nb.install_nbextension(ext, user=True)
```


## 2. Manually installing a single notebook extension:

First, you need to get hold of the files for the notebook extension, say by downloading and extracting a .zip archive of the repository, say from <https://github.com/ipython-contrib/IPython-notebook-extensions/archive/3.x.zip>.
Next, you need to find your local IPython directory. This can be done from command line:

```
ipython locate
```

or in IPython by executing:

```python
ip=get_ipython()
ip.ipython_dir
```

Now copy your notebook extension files from the .zip package to the `nbextensions` subdirectory of your local IPython directory.

You can verify if your extension has been installed by using (e.g.)

```python
IPython.html.nbextensions.check_nbextension('usability/runtools/main.js')
```


## 2. Loading an extension in a single notebook

Once a notebook extension has been installed, it can be loaded for a single notebook as follows.
To load the extension you need to provide the name and local path without the `.js` extension:

```Javascript
%%javascript
IPython.load_extensions('usability/rubberband/main');
```

_Note_: Be careful not to include the `.js` file extension in the extension name.


## 2. Activating an extension

*Activating*, or *enabling* an extension means configuring things such that the extension loads automatically for every notebook.

There is a graphical interface for activating/deactivating notebook extensions now. You might want to use it: [config-extension](Config-Extension)

Without using the GUI [config-extension](Config-Extension), the easiest way to enable an extension is to use
the requests module to communicate with the IPython config service directly.
For example, to activate the `python-markdown` extension, you need to provide the name and local path (without the `.js` extension) and call the config service in IPython:

```python
from IPython.html.services.config import ConfigManager
ip = get_ipython()
cm = ConfigManager(parent=ip, profile_dir=ip.profile_dir.location)
cm.update('notebook', {"load_extensions": {"usability/runtools/main": True}})
```


4. Deactivating extensions
--------------------------

To deactivate an extension from being reloaded, you can either use the [config-extension](Config-Extension) mentioned above, or you can use a very similar approach to that detailed previously, talking to the IPython config service. In this case you specify `None` as value with the extension name as key:

```Python
from IPython.html.services.config import ConfigManager
ip = get_ipython()
cm = ConfigManager(parent=ip, profile_dir=ip.profile_dir.location)
cm.update('notebook', {"load_extensions": {"usability/runtools/main": None}})
```


5. Viewing activated extensions
-------------------------------

You can generate a table of currently activated extensions by executing the following in a notebook cell:

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


## Troubleshooting

If the extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/usability/runtools/main.js`
3. Check for error messages in the JavaScript console of the browser.

Feel free to improve this Wiki documentation.