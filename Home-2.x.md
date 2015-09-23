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


Notebook extensions for IPython/Jupyter Version 2.x
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
| [aspell](Aspell)                                    | Spellchecker using aspell                                      |          |
| [breakpoints](Breakpoints)                          | Allow setting breakpoints to stop execution of notebook cells  |          |
| [codefolding](Codefolding)                          | Fold code blocks using Alt-F or clicking on gutter             |          |
| [comment-uncomment.js](Comment-Uncomment)           | Toggle comments in selected lines using Alt-C                  |          |
| [executeTime.js](Execute-Timings)                   | Display when each cell has been executed and how long it took  |          |
| [help_panel.js](Help-Panel)                         | Display panel with hotkey help                                 |          |
| [hide_input_all](Hide-Input-All)                    | Hide all codecells in a notebook                               |          |
| [linenumbers.js](Linenumbers)                       | Add line numbers to code cells                                 |          |
| [navigation-hotkeys](Navigation-Hotkeys)            | Change hotkeys for navigation in notebook                      |          |
| [python-markdown](Python-Markdown)                  | Display Python variables in markdown                           |          |
| [read-only.js](Readonly)                            | Allow codecells to be set read-only, so no editing is possible |          |
| [rubberband](Rubberband)                            | Multi-cell selection tool                                      |          |
| [runtools](Runtools)                                | Add toolbar buttons for additional code execution options      |          |
| [search.js](Search)                                 | Search notebook for expressions                                |          |
| [shift-tab.js](Shift-Tab-3.x)                       | Assign "shift-tab" key to dedent tabulator                     |          |
| [international_keymap.js](International-Keymap)     | Add new shortcuts to resolve issues with non US keymaps        |          |


Publishing
----------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|----------|
| [printview-button](Printview-Button)                | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile. |          |
| [printviewmenu-button](Printviewmenu-Button)        | Add a toolbar button to call menu entry `File->Print Preview` directly (V2 only)                                                            |          |
| gist_it                                             | Publish notebook as a gist                                                                                                                  |          |
| nbviewer_theme                                      |                                                                                                                                             |          |
| [htmltools/js_highlight.py](Javascript-Highlighter) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter                      | untested |


Styling
-------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| styling/css_selector                                |                                                                |          |
| styling/zenmode                                     |                                                                |          |


Slidemode
---------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| slidemode                                           | Make slide creation for reveal.js easier                       |          |


Testing
-------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| [hierarchical_collapse](wiki/Hierarchical-Collapse) |  Adds a button to hide all cells below the selected heading    |          |
| history                                             |                                                                |          |
| swc                                                 |                                                                |          |
| cellstate                                           |                                                                |          |


General installation instructions
=================================

Installing and activating notebook extensions works differently in IPython 3.x compared to 2.x.
Although it is still possible to use the instructions below to modify `custom.js` for versions above 2.x, it is discouraged.

Notebook extensions can be installed by copying the extension's corresponding javascript file and its accompanying files to the `nbextensions` directory of your local IPython directory (aka IPYTHONDIR) and loading it either directly in a single notebook, or adding it to the `custom.js` in your local profile in order for it to load for every notebook.


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

First, you need to get hold of the files for the notebook extension.
Next, you need to find your local IPython directory. This can be done from command line:

```
ipython locate
```

or in IPython by executing:

```python
from IPython import get_ipython
ip=get_ipython()
ip.ipython_dir
```

Now copy your notebook extension files into the `nbextensions` subdirectory of your local IPython directory.

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
In Ipython 2.x, if you want an extension to be always loaded, you need to call it in your local `custom.js` file.
First locate your profile directory:

```python
from IPython import get_ipython
ip=get_ipython()
ip.config.ProfileDir
```

This will give you something like

`{'location': u'C:\\Users\\you\\.ipython\\profile_default'}`
on Windows, or on Unix something like
`{'location': u'/home/you/.ipython/profile_default'}`

So on Unix, your file will be located here:
`/home/you/.ipython/profile_default/static/custom/custom.js`

This is where you add a line to call your notebook extension.
How to do this is described in the next section.


Adding the extension to custom.js
---------------------------------

Your `custom.js` should look like this:
```javascript
// activate extensions only after Notebook is initialized
require(["base/js/events"], function (events) {
$([IPython.events]).on("app_initialized.NotebookApp", function () {
    /* load your extension here */
    IPython.load_extensions('usability/runtools/main');
    });
});
```

In the example above, the `usability/runtools/main.js` extension will be loaded. Note: You don't need to specify the `.js` file extension.

A template `custom.js` file that assumes you've copied the contents of this repo into your `nbextensions` directory is given here: [ipython-contrib/custom.example.js](https://raw.github.com/ipython-contrib/IPython-notebook-extensions/2.x/custom.example.js)

It is also possible to add additional locations where extensions or the `custom.js` file can be placed.
This can be configured in the `ipython_notebook_config.py` file. To find out if
you have configured an extra path type:

```python
ip.config.NotebookApp.extra_static_paths
```


Troubleshooting
===============

If the extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify your `custom.js` is the one the IPython notebook is seeing, by opening it in the browser:
    `http://127.0.0.1:8888/static/custom/custom.js`
    <br/>_(as opposed to `../site-packages/IPython/html/static/custom/custom.js`,_
    <br/>_which may the only `custom.js` loaded if you are using a virtualenv)_
3. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/gist.js`
3. Check for error messages in the JavaScript console of the browser.

Feel free to improve this Wiki documentation.