This extension limits the number of characters a codecell can output as text. This also allows the interruption of endless loops.

[![Demo Video](http://img.youtube.com/vi/U26ujuPXf00/0.jpg)](https://youtu.be/U26ujuPXf00)

You can set the number of characters using the ConfigManager:
```Python
from IPython.html.services.config import ConfigManager
ip = get_ipython()
cm = ConfigManager(parent=ip, profile_dir=ip.profile_dir.location)
cm.update('notebook', {"limit_output": 1000})
```


Installation
============

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)
