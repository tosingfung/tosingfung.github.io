---
layout: post
tag: software
title: Python-related software
---

- WinPython
- Jupyter Notebook
- Notepad++

<!--more-->

## WinPython

When I started to learn Python, most tutorials and textbook recommended [Anaconda](https://www.anaconda.com). But this package was extremely huge and took very long time to install on old computers. It included many libraries useful for Data Science, but frankly these were all too advanced for a beginner. Later I found a wonderful IDE called [Thonny](https://thonny.org/). It was very user friendly, and the step-by-step debug function was extremely helpful for beginners. But for every script to run, you need to save it as .py files, making it quite troublesome to build slightly long scripts. Then I ran into this awesome portable [WinPython](https://winpython.github.io/). It is green, so you don't need to install it (only extraction). You can even put it in an USB drive and use it on any computer. 

Download the **WinPython64-3.xx.xx.0dot.exe** from SourceForge. It is only 25 Mb in size and is not bundled with any library. Extract it to D drive. Run the **WinPython Command Prompt.exe** and install the following libraries (the last three for web scraping):

> pip install biopython  
> pip install jupyter  
> pip install jupyterthemes  
> pip install requests  
> pip install beautifulsoup4  
> pip install lxml

Now that WinPython is installed, you can execute `.py` files by opening it with **{root}\python-3.9.5.amd64\python.exe**. Combining with Notepad++ mentioned below, it becomes very handy to test simple scripts. 

## Jupyter Notebook

Now you can start the **Jupyter Notebook.exe** in the root folder of WinPython. Needless to say, Jupyter Notebook is the go-to IDE to learn python and to write script. However, the default display of Jupyter is not user friendly. That's why I have included [jupyterthemes](https://github.com/dunovank/jupyter-themes) in the above libraries. Run the **WinPython Command Prompt.exe** and type:

```python
# Reset default theme
jt -r

# monokai dark theme with larger fonts
jt -t monokai -f roboto -fs 12 -nf opensans -nfs 10 -tf opensans -tfs 10 -ofs 10 -cellw 95% -lineh 150 -T

# grade3 light theme with larger fonts
jt -t grade3 -f roboto -fs 12 -nf opensans -nfs 10 -tf opensans -tfs 10 -ofs 10 -cellw 95% -lineh 150 -T
```

Another amazing feature of Jupyter Notebook is to export the notebook as a `.md` file. By Adding the YAML front matter to the notebook as follows, the `.md` file can be directly uploaded to GitHub Page, keeping another accessible record of the learning process.

```yaml
---
title:
layout: post
tag:
---
```

## Notepad++

This is one of the many enhanced notepad applications available. Notepad++ has a portable version and very good auto-completion and syntax highlight features for most programing languages, even including HTML and CSS. Another great feature is that by combining with WinPython, you can set a keyboard shortcut to run the script. Press F5 and type (change the path when necessary), set `Ctrl-E` as shortcut:

```
cmd /k D:\software\WPy64-3950\python-3.9.5.amd64\python.exe "$(FULL_CURRENT_PATH)" & PAUSE & EXIT
```

