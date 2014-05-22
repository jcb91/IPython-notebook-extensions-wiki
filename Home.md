The IPython notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

#Overview
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
| [chrome_clipboard](wiki/chrome_clipboard) | Add system clipboard actions with crome      |
| [codefolding](wiki/Codefolding)  | Fold code blocks using Alt-F or clicking on gutter            |
| [comment-uncomment.js](wiki/Comment-uncomment) | Toggle comments in selected lines using Alt-C   |
| [drag-and-drop](wiki/drag-and-drop) | Allow dragging of images into a notebook         |
| [help_panel.js](wiki/help_panel) | Display panel with hotkey help |
| [hide_input_all](wiki/hide_input_all) | Hide all codecells in a notebook      |
| [linenumbers.js](wiki/Linenumbers) | Add line numbers to code cells   |
| [navigation-hotkeys.js](wiki/navigation_hotkeys) | Change hotkeys for navigation in notebook  |
| [read-only.js](wiki/Readonly) | Allow codecells to be set read-only, so no editing is possible   |
| [runtools](wiki/Runtools) | Add toolbar buttons for additional code execution options   |
| [search.js](wiki/Search) | Search notebook for expressions                      |
| [shift-tab.js](wiki/Shift-tab) | Assign "shift-tab" key to dedent tabulator                      |

##Publishing

| File or Directory      | Description                                            | 
| ---------------------- |---------------------------------------------------------------------------------|
| [nbconvert-button](wiki/Nbconvert-button)	   | Add a toolbar button to call `nbconvert --to html` for current the notebook (deprecated)     |
| [printview-button](wiki/Printview-button)	   | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab (deprecated)                   |
| [printviewmenu-button](wiki/Printviewmenu-button)	   | Add a toolbar button to call menu entry `File->Print Preview` directly (V2 only)                   |
| gist_it                             |  Publish notebook as a gist  |
| nbviewer_theme | |
| htmltools/js_highlight.py](wiki/js_highlight.py) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter |

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
| hierarchical_collapse              |  Adds a button to hide all cells below the selected heading |
| history              |   |
| swc             |   |
| cellstate       |   |


# General installation instruction
Extensions can be installed by copying the corresponding javascript extension and it's accompanying files to the static/custom directory of your IPython profile and adding it to `custom.js`. 

## Finding your profile directory
You can find out your profile directory directly from the commandline
```
ipython locate
```
Or by starting the IPython notebook and executing
```python
import IPython
ip=IPython.get_ipython()
ip.config.ProfileDir 
```
This will give you something like
`{'location': u'C:\\Users\\me\\.ipython\\profile_dev'}`
or for Unix
`{'location': u'/home/you/.ipython/profile_default'}`

So your path to copy the extensions into will be
`/home/you/.ipython/profile_default/static/custom`

## Adding the extension
Next, you copy the extension file or complete directory to the custom directory.

Finally, you have to add the extensions to the file `custom.js` in order to load them.
This can be done best using the `require` command:
```javascript
require(['/static/custom/styling/css-selector/main.js']) 
```

Your `custom.js` file might now look like this:
```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
    require(['/static/custom/clean_start.js']);
    require(['/static/custom/styling/css-selector/main.js']);
})
```
It is also possible to add additional locations where extensions can be placed.
This can be configured in the `ipython_notebook_config.py` file. To find out if
you have configured an extra path type:
```python
ip.config.NotebookApp.extra_static_paths
```

## Troubleshooting
If the extension does not work, here is how you can check what is wrong:
1. Verify your `custom.js` is the one the IPython notebook is seeing, by opening it in the browser:

`http://127.0.0.1:8888/static/custom/custom.js`

2. Verify the extension can be loaded by the IPython notebook, for example:

`http://127.0.0.1:8888//static/custom/styling/css-selector/main.js`

3. Check for error messages in the Javascipt console. 

