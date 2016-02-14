As of pull request #452, the [keyboard_shortcut_editor](https://github.com/ipython-contrib/IPython-notebook-extensions/blob/5f46a725155548d6320f2f05ff04dba1265f3694/nbextensions/usability/keyboard_shortcut_editor/README.md) extension is available to modify or remove any action-based keyboard shortcuts you have problems with, or add any new ones you want. It doesn't yet handle CodeMirror shortcuts though, which are used to implement some of the editing shortcuts.

This extension adds new keybindings for the functions comment/uncomment and indent/dedent. This is necessary, because the default key-bindings are not accessible on a non US-keyboard. Furthermore, this extension resolves the problem that the move-cell-up/down keybindings won't with most browsers.

The new Key-bindings are:

'Alt-3': toggle_comments
'Alt-2': dedent_selection
'Alt-1': indent_selection
'Shift-k': move-selected-cell-up
'Shift-j': move-selected-cell-down


Installation
============

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)
