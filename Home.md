The IPython notebook allows extending the html frontend functionality (i.e. what you do in the Browser) using extensions written in Javascript. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

The repository is organized in several directories: 

| File or Directory      | Description                                                                       | 
| ---------------------- |---------------------------------------------------------------------------------|
| [publishing/nbconvert-button](wiki/Nbconvert-button)	   | Add a toolbar button to call `nbconvert --to html` for current the notebook (deprecated)     |
| [publishing/printview-button](wiki/Printview-button)	   | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab (deprecated)                   |
| [publishing/printviewmenu-button](wiki/Printviewmenu-button)	   | Add a toolbar button to call menu entry `File->Print Preview` directly (V2 only)                   |
| publishing/gist_it                             |  Publish notebook as a gist  |
| publishing/nbviewer_theme | |
| slidemode              | Make slide creation for reveal.js easier                                          |
| styling/css_selector   |                                              |
| styling/zenmode        |                                              |
| testing                | Alpha-level extensions, not for general use                                   |
| [usability/breakpoints](wiki/Breakpoints)  | Allow setting of breakpoints to stop execution of notebook cells            |
| [usability/codefolding](wiki/Codefolding)  | Fold code blocks using Alt-F or clicking on gutter            |
| [usability/comment-uncomment.js](wiki/Comment-uncomment) | Toggle comments in selected lines using Alt-C   |
| [usability/linenumbers.js](wiki/Linenumbers) | Add line numbers to code cells   |
| [usability/read-only.js](wiki/Readonly) | Allow codecells to be set read-only, so no editing is possible   |
| [usability/shift-tab.js](wiki/Shift-tab) | Assign "shift-tab" key to dedent tabulator                      |
| [usability/chrome_clipboard](wiki/chrome_clipboard) | Add system clipboard actions with crome      |
| [usability/drag-and-drop](wiki/drag-and-drop) | Add drag&drop of images into the notebook         |
| [usability/aspell](wiki/aspell) | Spellchecker using aspell |

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
## Troubleshooting
If the extension does not work, here is how you can check what is wrong:
1. Verify your `custom.js` is the one the IPython notebook is seeing, by opening it in the browser:

`http://127.0.0.1:8888/static/custom/custom.js`

2. Verify the extension can be loaded by the IPython notebook, for example:

`http://127.0.0.1:8888//static/custom/styling/css-selector/main.js`

3. Check for error messages in the Javascipt console. 

