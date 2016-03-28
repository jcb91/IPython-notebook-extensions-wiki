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
