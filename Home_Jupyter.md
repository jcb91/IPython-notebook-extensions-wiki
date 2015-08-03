The Jupyter notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

** This is work in progress, configuration has changed significantly from Python 3.x **

#Notebook extensions for Jupyter Version 4.x
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

`jupyter-nbextension disenable <name of extension>`

## Troubleshooting
If the extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/IPython-notebook-extensions-master/usability/runtools/main.js`
3. Check for error messages in the JavaScript console of the browser. 

Feel free to improve this Wiki documentation.