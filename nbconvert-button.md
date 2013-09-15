Add a button to the toolbar that calls nbconvert:
```python
import subprocess; subprocess.call("ipython nbconvert --to html " + name )
```