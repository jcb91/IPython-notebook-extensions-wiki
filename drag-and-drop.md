This IPython notebook extension allows dragging&dropping images from the desktop or other programs into a notebook. A new markdown cell is created below the currently selected cell and the image is embedded.
The notebook has been tested with Firefox and Chrome.

A demo video showing drag&drop of images is here:
http://youtu.be/buAL1bTZ73c

## Installation
1. Copy the file `drag-and-drop.js` to your `/static/custom/` directory of your IPython profile and add
```javascript
require(['/static/custom/dragdrop/drag-and-drop.js'])
```
to your `custom.js` file so it looks like this:

```javascript
$([IPython.events]).on('app_initialized.NotebookApp', function(){
  //... 
  require(['/static/custom/drag-and-drop.js'])
});
```
2. Configure the port
Edit you `ipython_notebook_config.py` file in your profile to include the line:
`c.DragDrop.port = 8901`

This will tell the websocket server on which port to communicate.

3. Start websocket service
Add a startup file to you startup directory, called `50-start-drag-and-drop.ipy`:

```python
# start websocket server for drag-and-drop extension

drag_and_drop_webport = get_ipython().config['DragDrop']['port']

def start_drag_and_drop():
    c = get_ipython()
    nb_dir = get_ipython().config['FileNotebookManager']['notebook_dir']
    newpath = os.path.normpath(c.config['NotebookApp']['extra_static_paths'][0]+'/custom/dragdrop/')
    sys.path.insert(0, newpath)

    import drag_and_drop
    drag_and_drop.start_server(drag_and_drop_webport, nb_dir)

start_drag_and_drop()
```
Link: ![](https://github.com/ipython-contrib/IPython-notebook-extensions/raw/master/usability/dragdrop/50-start-drag-and-drop.ipy)

## Internals
The image will be uploaded to the server where the notebook is running and into a directory called `images`. This means, the image is not copied to the notebook itself, it will only be linked to. The markdown cell in the notebook will contain this tag:
`<img  src="http://127.0.0.1:8888/notebooks//images/read_only_ext.png"/>`

A websocket server needs to be run on the machine where the IPython notebook server is running, so images can be saved. The server is located in `drag_and_drop.py` and needs to be called either manually or (ideally) automatically started from the startup directory.
