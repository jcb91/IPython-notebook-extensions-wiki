The IPython notebook allows extending the html frontend functionality (i.e. what you do in the Browser) using extensions written in Javascript. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

The repository is organized in several directories: 

| Directory              | Description                                                                       | 
| ---------------------- |:---------------------------------------------------------------------------------:|
| [publishing](wiki/publishing)             | publish notebooks on the web or convert to other formats                          |
| [slidemode](wiki/slidemode)              | make slide creation for reveal.js easier                                          |
| [styling] (wiki/styling)               | add custom styles to the notebook                                                 |
| testing                | alpha-level extension, not for general usage                                      |
| [usability](wiki/usability)              | improve usability of the notebook                                                 |

# General installation instruction
Extensions can be installed by copying the corresponding javascript extension and it's accompanying files to the static/custom directory of your IPython profile. You can find out your profile directory by starting the IPython notebook and executing
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

Finally, you have to add the extensions to the file `custom.js` in order to load them.
This can be done best using the `require` statement. If not stated otherwise in the extension description, for example:
```javascript
require(['/static/custom/styling/css-selector/main.js']) 
```
