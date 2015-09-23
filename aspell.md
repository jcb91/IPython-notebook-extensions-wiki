**There is a Javascript-only spellchecker available now from Doug Blank:**

* [Demonstration](https://www.youtube.com/watch?v=Km3AtRynWFQ)
* [Installation](http://calicoproject.org/ICalico#Installation_2)
* [Installation Video](https://www.youtube.com/watch?v=o4xCp3b4oCw)

It is recommended to use the above spellchecker instead of this aspell-based one.


Aspell-based spell checker
--------------------------

This IPython notebook extension allows spellchecking using aspell (http://aspell.net/).
It allows spell checking as you type in markdown cells or on demand using a toolbar button for any cell type.

The technical implementation is a server side spell checker, that communicates with the IPython notebook over a websocket.

A short demo video can be found here:
http://www.youtube.com/watch?v=yk5ID5SAlLw


Installation
============

* First you need to have the program `aspell` installed on a computer. 
* Next, you need the `aspell-python` package (https://pypi.python.org/pypi/aspell-python-py2 or https://pypi.python.org/pypi/aspell-python-py3).
* Finally, start `ipy-aspell-server.py`. If you want to run it in background, use something like `nohup python ipy-aspell-server.py &`. 

For now the spell check language is configured to english in the line

```python
s = aspell.Speller('lang', 'en')
```

of `ipy-aspell-server.py`.

Now install the IPython notebook extension: follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)

If the computer `ipy-aspell.py` is running on is also running the IPython notebook server, 
add the line 

```javascript
var wsUri = "ws://" + document.domain + ":8889/"+ "websocket";
```

to `ipy-aspell.js`.
If you use another computer, please add

```javascript
var wsUri = "ws://" + "**my computer name**" + ":8889/"+ "websocket";
```

This extension needs some testing. Also, it does not do much error checking for now.
Feedback and enhancements are welcome. 


Note
----

As all text to be spellchecked is transferred over the network unencrypted, this can be a major security risk. 
Also, someone might modify the server program `ipy-aspell-server.py` to spy on you.
Therefore, you should only use the spellchecker when it running on your local machine or setup.


Internals
=========

The communication between the computer running `ipy-aspell.py` and the IPython notebook extension `ipy-aspell.js` running in your browser is realized using websockets at port 8989.

The notebook extensions sends each word to be spell checked using a JSON string `"text":word, "line": i, "start":start, "end":end, "id":cell.cell_id` and receives back antother JSON string `"text":curWord, "line": cur.line, "start":start, "end":end, "id":cell.cell_id`.
If `curWord` is returned as `true` from aspell, then it is not a valid word in the dictionary and will be marked using CodeMirror`s `markText()`. The marking can be cleared either by typing on or by clicking on the trashcan toolbar symbol.