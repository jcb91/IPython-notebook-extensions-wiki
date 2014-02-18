This IPython notebook extension allows spellchecking using aspell (http://aspell.net/).
It allows spell checking as you type in markdown cells or on demand using a toolbar button for any cell type.

The technical implementation is a server side spell checker, that communicates with the IPython notebook over a websocket.

A short demo video can be found here:
http://www.youtube.com/watch?v=yk5ID5SAlLw

## Installation
* First you need to have the program `aspell` installed on a computer. 
* Next, you need the `aspell-python` package (https://pypi.python.org/pypi/aspell-python).
* Finally, start `ipy-aspell.py`. If you want to run it in background, use something like `nohup python ipy-aspell.py &`

For now the spell check language is configured to english in the line 
`s = aspell.Speller('lang', 'en')` of `ipy-aspell.py`.

Now install the IPython notebook extension:

Add `require(['/static/custom/aspell/ipy-aspell.js'])` to your `custom.js` 
Copy the directory `aspell` to your `/static/custom/` directory of your IPython profile and add
```javascript
require(['/static/custom/aspell/ipy-aspell.js'])
```
to your `custom.js` file so it looks like this:

```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/aspell/ipy-aspell.js'])
});
```

If the computer `ipy-aspell.py` is running on is als running the IPython notebook server, 
add the line 
`var wsUri = "ws://" + document.domain + ":8889/"+ "websocket"`
to `ipy-aspell.js`.
If you use another computer, pleas add
`var wsUri = "ws://" + "**my computer name**" + ":8889/"+ "websocket"`

This extension needs some testing. Also, it does not do much error checking for now.
Feedback and enhancements are welcome. 

## Internals
The communication between the computer running `ipy-aspell.py` and the IPython notebook extension `ipy-aspell.js` running in your browser is realized using websockets at port 8989.

The notebook extensions sends each word to be spell checked using a JSON string `"text":word, "line": i, "start":start, "end":end, "id":cell.cell_id` and receives back antother JSON string `"text":curWord, "line": cur.line, "start":start, "end":end, "id":cell.cell_id`.
