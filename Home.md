# About
The IPython notebook allows extending the frontend functionality (i.e. what you do in the Browser) using extensions written in Javascript. This repository contains a collection of such extensions. The maturity of the provided extensions may vary, please create an issue if you encounter any problems.

# Overview
| Name                   | Description                                                                       | 
| ---------------------- |:---------------------------------------------------------------------------------:|
| [nbconvert-button]()	 | add a button to call 'nbconvert --to html' for current notebook                   |
| printview-button	 | like nbconvert-button, additionally display in new browser tab                    |
| navigation-hotkeys     | add PGUP / PGDOWN / HOME / END for fast navigation in codecells                   |
| comment-uncomment      | toggle comments in selected lines using Alt-C                                     |
| read-only              | allow codecells to be set read-only, so no editing or celle execution is possible |
| breakpoints            | allow setting breakpoints at individual notebook cells                            |
| shift-tab              | assign shift-tab to dedent                                                        |
| help-panel             | display a static help panel besides the notebook                                  |
| codefolding            | fold code blocks using Alt-F or clicking on line numbers                          |

# General installation instruction
Extensions can be installed by copying the corresponding javascript extension and it's accompanying files to the static/custom directory of your IPython profile. You can find out your profile directory by starting IPython and executing
```javascript
  $ ipython locate
```
This will give you something like
' /home/you/.ipython'

So your path to copy the extensions will be
'/home/you/.ipython/profile_default/static/custom'

Finally, modify the file custom.js to load the desired extension.
```javascript
IPython.hotkeys=[];
require(['/static/custom/helper-functions.js']) 

initExtensions = function(){
    require(['/static/custom/read-only.js'])
    require(['/static/custom/breakpoint.js'])
    require(['/static/custom/comment-uncomment.js'])
//    require(['/static/custom/split-combine.js'])
    require(['/static/custom/shift-tab.js'])
    require(['/static/custom/nbconvert_button.js'])
    }
 $([IPython.events]).on('app_initialized.NotebookApp',initExtensions);
```

 