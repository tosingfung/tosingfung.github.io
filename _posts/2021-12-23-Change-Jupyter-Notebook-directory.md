---
title: Change Jupyter Notebook directory
layout: post
tag: software
---

- For Jupyter Notebook in WInPython.

<!--more-->

## Step-by-step

1. Run `WinPython Command Prompt.exe`
2. Run `jupyter notebook --generate-config`
3. A configuration file will be generated in the following location: `.\WPy64-3950\python-3.9.5.amd64\etc\jupyter\jupyter_notebook_config.py`
4. Open it using any text editor.
5. Search for `c.NotebookApp.notebook_dir =`
6. Change it to `c.NotebookApp.notebook_dir = 'c.NotebookApp.notebook_dir = 'D:/Jupyter'`
7. Save and restart Jupyter Notebook.