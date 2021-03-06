The Jupyter notebook functionality (i.e. what you do with the Browser) can be extended using Javascript extensions. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please [create an issue](https://github.com/ipython-contrib/jupyter_contrib_nbextensions/issues/new) if you encounter any problems.

Some extensions may work with other languages than Python, however this currently has not been tested.


IPython/Jupyter version support
===============================

There are different branches of the notebook extensions in this repository.
Please make sure you use the branch corresponding to your IPython/Jupyter version.
Not all extensions are available for all versions.
This page concerns the 4.x versions, which are supported by the `master` branch
of this repository.
Note: This is not related to the __Python__ version.
See the main [Home](Home) page for other versions.

Jupyter/IPython 4.x works differently than IPython 3.x.
To learn what's changed see [Changes-3.x-to-4.x](Changes-3.x-to-4.x)


Checking/loading notebook extensions from Jupyter
-------------------------------------------------

You can check if the directory or a file (or list of files) exists:

```Python
from notebook.nbextensions import check_nbextension
check_nbextension('codefolding', user=True)
check_nbextension('codefolding/main.js', user=True)
```

Make sure to use `user=True` if you have the extensions installed in your local path (in `jupyter_data_dir()`).

To enable an extension:

```Python
ext_require_path = 'codefolding/main'
try:  # notebook >= 4.2.0
    from notebook.nbextensions import enable_nbextension
    enable_nbextension('notebook', ext_require_path)
except ImportError:
    from notebook.nbextensions import EnableNBExtensionApp
    EnableNBExtensionApp().enable_nbextension(ext_require_path)
```

To disable an extension:

```Python
ext_require_path = 'codefolding/main'
try:  # notebook >= 4.2.0
    from notebook.nbextensions import disable_nbextension
    disable_nbextension('notebook', ext_require_path)
except ImportError:
    from notebook.nbextensions import DisableNBExtensionApp
    DisableNBExtensionApp().disable_nbextension(ext_require_path)
```

The configuration is stored in either `jupyter_config_dir()/notebook.json` or `jupyter_config_dir()/nbconfig/notebook.json` depending on your Jupyter (4.0.xx or master) version.

If you reload the notebook after enabling a notebook extension, the extension will be loaded. You can check the Javascript console to confirm.


Notebook extensions for Jupyter Version 4.x
===========================================

Some extensions have wiki pages of their own, but the repository is gradually
switching to having documentation stored in readme files in the extensions
themselves.
All recently-updated extensions should have a readme file, or at least a yaml
descriptor file, which can be viewed either from the
[config extension](Config-Extension), or failing that, on the github repository.

| File or Directory                         | Description                                                                          | Status   |
| ------------------------------------------|--------------------------------------------------------------------------------------|----------|
| autosavetime                              | Set the notebook autosave interval, and/or add a selector to the toolbar to set it   | working  |
| autoscroll                                | Exert control over the output autoscroll threshold                                   | working  |
| cellstate                                 | See runtools, which includes this plus more functionality                  | redundant |
| [chrome_clipboard](Chrome-Clipboard)      | Add system clipboard actions with Chrome browser                                     | working  |
| code_font_size                            | Adds toolbar buttons to increase and decrease code cells' font size                  | working  |
| [codefolding](Codefolding)                | Fold code blocks using `Alt-F` or clicking on gutter                                 |          |
| skill                                     | Enable SKILL syntax support for CodeMirror                                           | working  |
| collapsible_headings                      | Make notebook into collapsible sections, separated by headings                       | working  |
| [comment-uncomment](Comment-Uncomment)    | Toggle comments in selected lines using `Alt-C`                                      |          |
| datestamper                               | Add a toolbar button which pastes the current time & date into the current cell      | working  |
| [dragdrop](Drag-and-Drop)                 | Allow dragging of images into a notebook                                             | working  |
| equation-numbering                        | Enables equation autonumbering and resetting the equation count                      |          |
| [execute_time](Execute-Timings)           | Display when each cell was last executed, and how long it took                       | working  |
| exercise                                  | Define a group of cells as an "exercise", then hide/show the solution cells          |          |
| exercise2                                 | As above, but with a different UI for showing/hiding solutions                       |          |
| help_panel                                | Display keyboard help in a panel to the right side of the notebook, or fullscreen    | working  |
| hide_input                                | toggle display of selected code cell's input                                         |          |
| [hide_input_all](Hide-Input-All)          | Hide all codecells in a notebook                                                     |          |
| highlighter                               | Enable highlighting selected text in markdown cells                                  |          |
| history                                   |                                                                                      | broken   |
| htmltools/js_highlight.py](Javascript-Highlighter) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter   | untested |
| init_cell                                 | Mark cells as 'initialization' cells, to be run on notebook load, or clicking button |          |
| keyboard_shortcut_editor                  | Edit or remove Jupyter keyboard shortcuts, or add own new ones                       | working  |
| [latex_envs](LaTeX-Environments)          | (some) LaTeX commands and environments in markdown cells                             | working  |
| [limit-output](Limit-Output)              | Limit length of codecell output                                                      | working  |
| move_selected_cells                       | Move selected cell(s) using keyboard shortcuts `Alt-up` and `Alt-down`               |          |
| [navigation-hotkeys](Navigation-Hotkeys)  | Change hotkeys for navigation in notebook (see also keyboard shortcut editor, above) |          |
| notify                                    | Show a browser notification when kernel becomes idle after being busy for a while    | working  |
| [printview-button](Printview-Button)      | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile.            | working  |
| gist_it                                   | Add a toolbar button to publish the current notebook as a gist. Can make anonymous gists, or use an access token to create and update user-owned gists | working  |
| [python-markdown](Python-Markdown)        | Display Python variables in markdown                                                 |          |
| qtconsole                                 | Launch a QTConsole attached to the running kernel                                    |          |
| [read-only](Readonly)                     | Allow codecells to be set read-only, so no editing is possible                       |          |
| [rubberband](Rubberband)                  | Multi-cell selection tool (this is redundant in newer Jupyter versions)              |          |
| ruler                                     | Enables the CodeMirror ruler feature                                                 | working  |
| [runtools](Runtools)                      | Add toolbar buttons for additional code execution options                            |          |
| [search-replace](Search-&-Replace)        | Add a toolbar for notebook-wide search and replace                                   | working  |
| [skip-traceback](Skip-Traceback)          | Don't display traceback, only error type and message                                 | working  |
| slidemode                                 | Make slide creation for reveal.js easier                                             |          |
| css_selector                              |                                                                                      |          |
| zenmode                                   | Adds a distraction-free 'zen' mode to the notebook                                   | working  |
| swc                                       | software carpentry - seems broken                                                    | broken   |
| toc2                                      | Displays a table of contents composed of the notebook's markdown header cells        | working  |
| toggle_all_line_numbers                   | Add a toolbar button and hotkey to toggle all cells' line numbers on or off          | working  |


General installation instructions
=================================

In general, it's easiest to install all the extensions in the repository using
the installation instructions on the main repository readme, and use the
[jupyter_nbextensions_configurator](https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator)
to choose which extensions to enable, and configure any options they provide.

Alternatively, to enable/diable an nbextension form the command line, you can
use its require path together with the jupyter commands:

    jupyter nbextension enable <extension require path>

and

    jupyter nbextension disable <extension require path>

The require path is the relative path to the extension's main javascript file
in the nbextensions directory, minus the files extensions (the `.js`).
So for example for the `collapsible_headings` nbextension, it is
`collapsible_headings/main`, and you would use

    jupyter nbextension enable collapsible_headings/main


You can generate a table of currently enabled extensions by executing the
following in a notebook cell:

```Python
import os

from IPython.display import HTML
from notebook.services.config import ConfigManager

table = (
    '<table border="1"> <tr>'
    '<th>section</th> <th>require path</th> <th>enabled?</th>'
    '</tr>{}</table>')
table_rows = ''
cm = ConfigManager()
for section in ['common', 'notebook', 'tree', 'edit', 'terminal']:
    for req, enabled in cm.get(section).get('load_extensions', {}).items():
        table_rows += '<tr><td>{}</td><td>{}</td><td>{}</td></tr>\n'.format(
            section, req, enabled)
HTML(table.format(table_rows))
```

Configuration
-------------

During the second part of the install (executing
`jupyter contrib nbextension install`), the jupyter-notebook and
jupyter-nbconvert configuration files will be automatically updated.
In addition, `jupyter_nbextensions_configurator` is enabled.
You can now configure the individual extensions through the config page
`http://localhost:8888/nbextensions`, or from the nbextensions tab on the main
jupyter dashboard (files page).

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
    `http://127.0.0.1:8888/nbextensions/runtools/main.js`
3. Check for error messages in the JavaScript console of the browser.

Feel free to improve this Wiki documentation!