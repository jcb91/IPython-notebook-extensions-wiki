There is now a graphical user interface for activating/deactivating installed notebook extensions by going to the '/nbextensions/' URL:

![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/wiki-images/notebook-configuration.png)

This is realized using a notebook server extension, new to IPython 3.x. 
In order to work, this extensions needs to be installed and notebook extensions require a YAML description file in order to be found.

#Setup procedure
##1. Installation
All required files are originally located in the 'config' of the repository.
 * copy 'main.js' and 'main.css' to your '~/.ipython/nbextensions/config' folder
 * copy 'nbextensions.py' to your '~/.ipython/extensions' folder
 * copy 'nbextensions.html' to your '~/.ipython/templates' folder

##2. Configuration
Add the following lines to your 'ipython_notebook_config.py' file:
```
from IPython.utils.path import get_ipython_dir
import os
import sys

ipythondir = get_ipython_dir()
extensions = os.path.join(ipythondir,'extensions') 
sys.path.append( extensions )

c = get_config()
c.NotebookApp.server_extensions = [ 'nbextensions', 'preview' ]
c.NotebookApp.extra_template_paths = [os.path.join(ipythondir,'templates') ]
```

#YAML file format
* Type         - identifier 'IPython Notebook Extension'
* Name         - unique name of the extension
* Description  - short explanation of the extension
* Link         - link to more documentation
* Icon         - small icon 400px wide
* Main         - main file that is loaded, typically 'main.js'
* Compatibility- IPython version compatibility (e.g. 3.x)

Example:
```
Type: IPython Notebook Extension
Name: Shift-Tab
Description: Assign shift+tab key for dedent operation
Link: https://github.com/ipython-contrib/IPython-notebook-extensions/wiki/Shift-tab
Icon: icon.png
Main: main.js
Compatibility: 3.x 
```
