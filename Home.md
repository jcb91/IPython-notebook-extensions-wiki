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


General installation instructions
=================================

Installing and activating notebook extensions works slightly differently depending on your IPython/Jupyter version.
Please see the correct homepage for your version:
* [2.x](Home-2.x)
* [3.x](Home-3.x)
* [4.x (Jupyter)](Home-4.x-(Jupyter))


Notebook extensions for IPython/Jupyter
=======================================

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

| File or Directory                                   | Description                                                    |
| ----------------------------------------------------|----------------------------------------------------------------|
| [chrome_clipboard](Chrome-Clipboard)                | Add system clipboard actions with Chrome                       |
| [codefolding](Codefolding)                          | Fold code blocks using Alt-F or clicking on gutter             |
| [comment-uncomment.js](Comment-Uncomment)           | Toggle comments in selected lines using Alt-C                  |
| [executeTime.js](Execute-Timings)                   | Display when each cell has been executed and how long it took  |
| [drag-and-drop](Drag-and-Drop)                      | Allow dragging of images into a notebook                       |
| [hide_input_all](Hide-Input-All)                    | Hide all codecells in a notebook                               |
| [latex_envs](LaTeX-Environments)                    | (some) LaTeX commands and environments in markdown cells       |
| [limit-output](Limit-Output)                        | Limit codecell output                                          |
| [navigation-hotkeys](Navigation-Hotkeys)            | Change hotkeys for navigation in notebook                      |
| [python-markdown](Python-Markdown)                  | Display Python variables in markdown                           |
| [read-only.js](Readonly)                            | Allow codecells to be set read-only, so no editing is possible |
| [rubberband](Rubberband)                            | Multi-cell selection tool                                      |
| [runtools](Runtools)                                | Add toolbar buttons for additional code execution options      |
| [search-replace](Search-&-Replace)                  | Add a toolbar for notebook-wide search and replace             |
| [skip-traceback](Skip-Traceback)                    | Don't display traceback, only error type and message           |


Publishing
----------

| File or Directory                                   | Description                                                                                                                                 |
| ----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| [printview-button](Printview-Button)                | Add a toolbar button to call `nbconvert --to html` for current the notebook and display html in new browser tab. Uses current user profile. |
| [htmltools/js_highlight.py](Javascript-Highlighter) | A python tool to customize the css classes of nbconvert's html code blocks to fit your favourite JS syntax highlighter                      |


Styling
=======

| File or Directory                                   | Description                                                    |
| ----------------------------------------------------|----------------------------------------------------------------|
| styling/css_selector                                |                                                                |
| styling/zenmode                                     |                                                                |


Slidemode
=========

| File or Directory                                   | Description                                                    |
| ----------------------------------------------------|----------------------------------------------------------------|
| slidemode                                           | Make slide creation for reveal.js easier                       |


Testing
=======

| File or Directory                                   | Description                                                    |
| ----------------------------------------------------|----------------------------------------------------------------|
| [hierarchical_collapse](wiki/Hierarchical-Collapse) |  Adds a button to hide all cells below the selected heading    |
| history                                             |                                                                |
| swc                                                 |                                                                |
| cellstate                                           |                                                                |
