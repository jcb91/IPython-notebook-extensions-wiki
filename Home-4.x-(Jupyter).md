The Jupyter notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please [create an issue](https://github.com/ipython-contrib/IPython-notebook-extensions/issues/new) if you encounter any problems.

Some extensions may work with other languages than Python, however this currently has not been tested.


IPython/Jupyter version support
===============================

There are different branches of the notebook extensions in this repository.
Please make sure you use the branch corresponding to your IPython/Jupyter version.
Not all extensions are available for all versions.
This page concerns the 4.x versions, which are supported by the `master` branch
of this repository.
Note: This is not related to the __Python__ version.
See the main [Home][Home] page for other versions.

Jupyter/IPython 4.x works differently than IPython 3.x.
To learn what's changed see [Changes-3.x-to-4.x]


Checking/loading notebook extensions from Jupyter
-------------------------------------------------

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
The configuration is stored in either `jupyter_config_dir()/notebook.json` or `jupyter_config_dir()/nbconfig/notebook.json` depending on your Jupyter (4.0.xx or master) version.

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
| codemirrormode            | Extra codemirror highlighting syntaxes              |

Some extensions have wiki pages of their own, but the repository is gradually
switching to having documentation stored in readme files in the extensions
themselves.
All recently-updated extensions should have a readme file, or at least a yaml
descriptor file, which can be viewed either from the
[config extension](Config-Extension), or failing that, on the github repository.



Usability
---------

| File or Directory                         | Description                                                                          | Status   |
| ------------------------------------------|--------------------------------------------------------------------------------------|----------|
| autosavetime                              | Set the notebook autosave interval, and/or add a selector to the toolbar to set it   | working  |
| autoscroll                                | Exert control over the output autoscroll threshold                                   | working  |
| code_font_size                            | Adds toolbar buttons to increase and decrease code cells' font size                  | working  |
| [chrome_clipboard](Chrome-Clipboard)      | Add system clipboard actions with Chrome browser                                     | working  |
| [codefolding](Codefolding)                | Fold code blocks using `Alt-F` or clicking on gutter                                 |          |
| collapsible_headings                      | Make notebook into collapsible sections, separated by headings                       | working  |
| [comment-uncomment](Comment-Uncomment)    | Toggle comments in selected lines using `Alt-C`                                      |          |
| datestamper                               | Add a toolbar button which pastes the current time & date into the current cell      | working  |
| [dragdrop](Drag-and-Drop)                 | Allow dragging of images into a notebook                                             | working  |
| equation-numbering                        | Enables equation autonumbering and resetting the equation count                      |          |
| [execute_time](Execute-Timings)           | Display when each cell was last executed, and how long it took                       | working  |
| exercise                                  | Define a group of cells as an "exercise", then hide/show the solution cells          |          |
| exercise2                                 | As above, but with a different UI for showing/hiding solutions                       |          |
| help_panel                                | Display keyboard help in a panel to the right side of the notebook, or fullscreen    | working  |
| highlighter                               | Enable highlighting selected text in markdown cells                                  |          |
| hide_input                                | toggle display of selected code cell's input                                         |          |
| [hide_input_all](Hide-Input-All)          | Hide all codecells in a notebook                                                     |          |
| init_cell                                 | Mark cells as 'initialization' cells, to be run on notebook load, or clicking button |          |
| keyboard_shortcut_editor                  | Edit or remove Jupyter keyboard shortcuts, or add own new ones                       | working  |
| [latex_envs](LaTeX-Environments)          | (some) LaTeX commands and environments in markdown cells                             | working  |
| [limit-output](Limit-Output)              | Limit length of codecell output                                                      | working  |
| move_selected_cells                       | Move selected cell(s) using keyboard shortcuts `Alt-up` and `Alt-down`               |          |
| [navigation-hotkeys](Navigation-Hotkeys)  | Change hotkeys for navigation in notebook (see also keyboard shortcut editor, above) |          |
| notify                                    | Show a browser notification when kernel becomes idle after being busy for a while    | working  |
| [python-markdown](Python-Markdown)        | Display Python variables in markdown                                                 |          |
| qtconsole                                 | Launch a QTConsole attached to the running kernel                                    |          |
| [read-only](Readonly)                     | Allow codecells to be set read-only, so no editing is possible                       |          |
| [rubberband](Rubberband)                  | Multi-cell selection tool (this is redundant in newer Jupyter versions)              |          |
| ruler                                     | Enables the CodeMirror ruler feature                                                 | working  |
| [runtools](Runtools)                      | Add toolbar buttons for additional code execution options                            |          |
| [search-replace](Search-&-Replace)        | Add a toolbar for notebook-wide search and replace                                   | working  |
| [skip-traceback](Skip-Traceback)          | Don't display traceback, only error type and message                                 | working  |
| toc2                                      | Displays a table of contents composed of the notebook's markdown header cells        | working  |
| toggle_all_line_numbers                   | Add a toolbar button and hotkey to toggle all cells' line numbers on or off          | working  |


Publishing
----------

| File or Directory                                   | Description                                                                                                                                            | Status   |
| ----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| [printview-button](Printview-Button)                | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile.            | working  |
| [htmltools/js_highlight.py](Javascript-Highlighter) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter                                 | untested |
| publishing/gist_it                                  | Add a toolbar button to publish the current notebook as a gist. Can make anonymous gists, or use an access token to create and update user-owned gists | working  |

Styling
-------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| styling/css_selector                                |                                                                |          |
| styling/zenmode                                     | Adds a distraction-free 'zen' mode to the notebook             | working  |


Slidemode
---------

| File or Directory                                   | Description                                                    | Status   |
| ----------------------------------------------------|----------------------------------------------------------------|----------|
| slidemode                                           | Make slide creation for reveal.js easier                       |          |


Testing
-------

| File or Directory                                   | Description                                                                                                    | Status    |
| ----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|-----------|
| history                                             |                                                                                                                | broken    |
| swc                                                 | software carpentry - seems broken                                                                              | broken    |
| cellstate                                           | See usability/runtools, which includes this plus more functionality                                            | redundant |

Codemirrormode
--------------

| File or Directory                                   | Description                                | Status    |
| ----------------------------------------------------|--------------------------------------------|-----------|
| codemirrormode/skill                                | Enable SKILL syntax support for CodeMirror | working   |


General installation instructions
=================================

In general, it's easiest to install all the extensions in the repository using
the Anaconda package, or the setup.py script (see below).
Then you can use the [config extension](Config-Extension) to choose which
extensions to activate, and configure any options they provide.

You can also attempt to use the instructions below to install individual extensions.

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

On some systems, for example Mac OSX using MacPorts, `jupyter nbextension` is executed using `jupyter-nbextension-#.#` where `#.#` is the version of Python being used by the notebook. 

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

Configuration
-------------
During the package installation the jupyter-notebook and jupyter-nbconvert configuration files will be automatically updated. You can now configure the individual extensions through the config page `http://localhost:8888/nbextensions`.

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

If an extension does not work, here is how you can check what is wrong:

1. Clear your browser cache or start a private browser tab.
2. Verify the extension can be loaded by the IPython notebook, for example:
    `http://127.0.0.1:8888/nbextensions/usability/runtools/main.js`
3. Check for error messages in the JavaScript console of the browser.

Feel free to improve this Wiki documentation!
