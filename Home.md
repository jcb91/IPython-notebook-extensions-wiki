The IPython notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

Some extension may work with other languages than Python, however this currently has not been tested.

IPython version support
=======================
There are different branches of the notebook extensions in this repository.
Please make sure you use the branch corresponding to your IPython version.
Not all extensions are available for version 2.x and 3.x.

| IPython Version | Description |
|------------|-------------|
| 1.x | not supported |
| 2.x | checkout 2.x branch |
| [3.x](Home_3x) | checkout 3.x branch |

**For IPython version 3.x information click here: [3.x](Home_3x)**

Note: This is not related to the __Python__ version.


#Overview for IPython Version 2.x
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
| [aspell](wiki/aspell) | Spellchecker using aspell |
| [breakpoints](wiki/Breakpoints)  | Allow setting of breakpoints to stop execution of notebook cells            |
| [codefolding](wiki/Codefolding)  | Fold code blocks using Alt-F or clicking on gutter            |
| [comment-uncomment.js](wiki/Comment-uncomment) | Toggle comments in selected lines using Alt-C   |
| [executeTime.js](wiki/execute_timings) | Display when each cell has been executed and how long it took          |
| [help_panel.js](wiki/help_panel) | Display panel with hotkey help |
| [hide_input_all](wiki/hide_input_all) | Hide all codecells in a notebook      |
| [linenumbers.js](wiki/Linenumbers) | Add line numbers to code cells   |
| [navigation-hotkeys.js](wiki/navigation_hotkeys) | Change hotkeys for navigation in notebook  |
| [python-markdown.js](wiki/python-markdown) | Display Python variables in markdown  |
| [read-only.js](wiki/Readonly) | Allow codecells to be set read-only, so no editing is possible   |
| [rubberband](wiki/Rubberband) | Multi-cell selection tool   |
| [runtools](wiki/Runtools) | Add toolbar buttons for additional code execution options   |
| [search.js](wiki/Search) | Search notebook for expressions                      |
| [shift-tab.js](wiki/Shift-tab) | Assign "shift-tab" key to dedent tabulator                      |

##Publishing

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| [printview-button](wiki/Printview-button)	   | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile.                   |
| [printviewmenu-button](wiki/Printviewmenu-button)	   | Add a toolbar button to call menu entry `File->Print Preview` directly (V2 only)                   |
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
Notebook extensions can be installed by copying the corresponding javascript extension and it's accompanying files to the `nbextensions` directory of your local IPython directory (aka IPYTHONDIR) and calling it either directly in a notebook or adding it to the `custom.js` in your local profile.

## Installing from a URL
The easiest way to install an extension is directly from IPython:
```python
import IPython
IPython.html.nbextensions.install_nbextension('https://rawgithub.com/minrk/ipython_extensions/master/nbextensions/gist.js')
```
You can verify if your extension has been installed by using
```python
IPython.html.nbextensions.check_nbextension('gist.js')
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

## Adding the extension to custom.js

Your `custom.js` should look like this:
```javascript
// activate extensions only after Notebook is initialized
require(["base/js/events"], function (events) {
$([IPython.events]).on("app_initialized.NotebookApp", function () {
    /* load your extension here */
    IPython.load_extensions('gist');
    });
});
```

In the example above, the `gist.js` is loaded. Note: You don't need to specify the `.js` file extension.

A template `custom.js` file is given here : [ipython-contrib/custom.example.js](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/custom.example.js)

It is also possible to add additional locations where extensions or the `custom.js` file can be placed.
This can be configured in the `ipython_notebook_config.py` file. To find out if
you have configured an extra path type:
```python
ip.config.NotebookApp.extra_static_paths
```

## Troubleshooting
If the extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify your `custom.js` is the one the IPython notebook is seeing, by opening it in the browser:
    `http://127.0.0.1:8888/static/custom/custom.js`
    <br/>_(as opposed to `../site-packages/IPython/html/static/custom/custom.js`,_
    <br/>_which may the only `custom.js` loaded if you are using a virtualenv)_
3. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/gist.js`
3. Check for error messages in the JavaScript console. 
