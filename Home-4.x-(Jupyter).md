The Jupyter notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please [create an issue](https://github.com/ipython-contrib/IPython-notebook-extensions/issues/new) if you encounter any problems.

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


Now where in the world did everything go?
=========================================

Jupyter/IPython 4.x works differently than IPython 3.x.


In short
--------

* The notebook was split from IPython. You need to install both to run the notebook with IPython now. The easiest way is to use Anaconda and do a `conda install jupyter`
* There are no profiles anymore. You can specify environment variables to change the default, see [Jupyter ML](https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!topic/jupyter/7q02jjksvFU)].
* The configuration has moved to a new place. To find out where, see below.
* There is a kind of automatic upgrade of the configuration files from IPython 3.x to Jupyter.


So where can I find things now?
-------------------------------

To find where the configuration files are, start IPython 
```Python
from __future__ import print_function
from jupyter_core.paths import jupyter_config_dir, jupyter_config_path
print(jupyter_config_dir())
print(jupyter_config_path())
```
`jupyter_config_dir()` shows you where your *local* configuration files are, `jupyter_config_path` shows you where Jupyter will look for configuration files. For the notebook, there are two files that will be used:
`jupyter_notebook_config.py` and `jupyter_notebook_config.json`. 

The `nbextension` directory has moved to a different location and can be found in one of these directories:
```Python
from __future__ import print_function
from jupyter_core.paths import jupyter_data_dir, jupyter_path
print(jupyter_data_dir())
print(jupyter_path())
```


Checking/loading notebook extension from IPython
------------------------------------------------

You can check if the directory or a file (or list of files) exists:
```Python
import notebook
notebook.nbextensions.check_nbextension('usability/codefolding', user=True)
notebook.nbextensions.check_nbextension('usability/codefolding/main.js', user=True)
```
Make sure to use `user=True` if you have the extensions installed in your local path (in `jupyter_data_dir()`).

To enable an extension:
```Python
import notebook
E = notebook.nbextensions.EnableNBExtensionApp()
E.enable_nbextension('usability/codefolding/main')
```

To disable an extension:
```Python
import notebook
D = notebook.nbextensions.DisableNBExtensionApp()
D.disable_nbextension('usability/codefolding/main')
```
The configuration is stored in either `jupyter_config_dir()/notebok.json` or `jupyter_config_dir()/nbconfig/notebook.json` depending on your Jupyter (4.0.xx or master) version.

If you reload the notebook after enabling a notebook extension, the extension will be loaded. You can check the Javascript console to confirm.


Notebook extensions for Jupyter Version 4.x
===========================================

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
| [latex_envs](LaTeX-Environments)                    | (some) LaTeX commands and environments in markdown cells       | working  |
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

Installing and activating notebook extensions works differently in Jupyter compared to previous (<4.x) IPython versions.
Please be aware that since Jupyter is still in development, some commands may change in the future.

*There is a graphical interface for activating/deactivating notebook extensions now.* You might want to use it:
[config-extension](Config-Extension)


1. Installing an extension
--------------------------

`jupyter nbextension install <name of extension>`

Example:
`jupyter nbextension install nbextensions/usability/codefolding/main`

where the `nbextensions` directory is likely located in one of the locations given by running

`jupyter --paths`

Note the directory name for a package isn't always precisely the same as the name of the package. For instance, the directory for `drag-n-drop` is named `dragdrop`.

On some systems, for example MacOS X using MacPorts, `jupyter nbextension` is executed using `jupyter-nbextension-#.#` where `#.#` is the version of Python being used by the notebook. 

2. Activating an extension
--------------------------

`jupyter nbextension enable <name of extension>`


3. Deactivating extensions
--------------------------

`jupyter nbextension disable <name of extension>`


4. Viewing activated extensions
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


Installation instructions for Anaconda
======================================

The instructions were tested on Anaconda 3 v.2.4.1.

* First, clone nbextension master repository
* Then, build Anaconda package:<br>
`conda build IPython-notebook-extensions`

**Notice:**
At the end of a successful build, the last output lines will be something like these:
```
# If you want to upload this package to anaconda.org later, type:
#
# $ anaconda upload /home/myuser/anaconda3/conda-bld/linux-64/nbextensions-master-py35_0.tar.bz2
#
# To have conda build upload to anaconda.org automatically, use
# $ conda config --set anaconda_upload yes
```
In the 4th line from the end you can see the path to the built anaconda package:
`/home/myuser/anaconda3/conda-bld/linux-64/nbextensions-master-py35_0.tar.bz2`
Use this path to install the package.

* Now, install the newly built nbextensions package:<br>
`conda install /home/myuser/anaconda3/conda-bld/linux-64/nbextensions-master-py35_0.tar.bz2`

Configuration
-------------
During the package installation the jupyter-notebook and jupyter-nbconvert configuration files will be automatically updated.

**Note:**
If you have configured the Clusters tab in `jupyter_notebook_config.py` before installing the nbextensions package, the cluster tab may stop working and you will get the following warning when you start jupyter-notebook:
```
[W 13:20:31.257 NotebookApp] Collisions detected in jupyter_notebook_config.py and jupyter_notebook_config.json config files. jupyter_notebook_config.json has higher priority: {
      "NotebookApp": {
        "server_extensions": "<traitlets.config.loader.LazyConfigValue object at 0x7f9e117dce10> ignored, using ['nbextensions']"
      }
    }
```
Follow these instruction to move the Clusters tab configuration from `jupyter_notebook_config.py` to `jupyter_notebook_config.json`: [ipyparallel issue 64](/ipython/ipyparallel/issues/64)


Troubleshooting
===============

If the extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/usability/runtools/main.js`
3. Check for error messages in the JavaScript console of the browser.

Feel free to improve this Wiki documentation.