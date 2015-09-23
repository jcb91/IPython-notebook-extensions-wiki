(some) LaTeX environments for Jupyter notebook
==============================================

This extension for IPython 3.x or Jupyter enables to use some LaTeX commands and environments in the notebook's markdown cells. 

1. **LaTeX commands and environments**
 - support for some LaTeX commands within markdown cells, *e.g.* `\textit`, `\textbf`, `\underline`
 -  support for **theorems-like environments**
 -  support for **lists**: *enumerate, itemize*,  
 -  limited support for a **figure environment**,
 -  support for an environment *listing*,
 -  additional *textboxa* environment
2. **Citations and bibliography**
 -  support for `\cite` with creation of a References section, rendering of references can be customized (to some extent)
3. **Document-wide numbering of equations, support for `\label` and `\ref`**
4. **Configuration toolbar**
5. Styles can be customized in the *latex\_env.css* stylesheet

More environments can be simply added in the source file (`thmsInNb4.js`). 

The `conversion` directory contains scripts for converting the notebooks to html and LaTeX while taking into account the structures 
enabled by the extension. Theses scripts require nodejs, perl, ipython3. Examples of such conversions are in the `doc` subdirectory that constains an example notebook and its html and pdf versions. This serves as the documentation.


Demo/documentation
==================

A demo notebook `latex_env_doc.ipynb` is provided. Its html version is [latex_env_doc.html](https://rawgit.com/jfbercher/latex_envs/master/doc/latex_env_doc.html) and a pdf resulting from conversion to LaTeX is available as [documentation](https://rawgit.com/jfbercher/latex_envs/master/doc/documentation.pdf). 


Installation
============

Follow the installation instructions appropriate to your IPython version as explained on the main wiki home pages:
* [Home generic](Home)
* [Home 4.x (Jupyter)](Home-4.x-(Jupyter))
* [Home 3.x](Home-3.x)
* [Home 2.x](Home-2.x)
