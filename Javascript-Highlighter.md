`js_highlight.py` is a script to strip off static syntax highlighting from the html output of nbconvert and to customize the CSS classes of the containing \<code\> or \<pre\> elements so that your favorite JS syntax highlighter can pick up the code and do its job.

``` bash
# This one is for a blog post using Google prettify.
$ nbconvert --to html --template basic MyNotebook.ipynb
$ python $IPYTHON_CONTRIB_DIR/htmltools/js_highlight.py MyNotebook.html "prettyprint  lang-{lang}".
```


Installation
============

You still need to include in your website's template code the \<script\> tag to load the JS syntax highlighter.

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)
