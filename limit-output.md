This extension limits the number of characters a codecell can output as text.
This prevents endless loops.

You can set the number of characters using the ConfigManager:
```Python
from IPython.html.services.config import ConfigManager
ip = get_ipython()
cm = ConfigManager(parent=ip, profile_dir=ip.profile_dir.location)
cm.update('notebook', {"limit_output": 1000})
```
