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

## Jupyter Notebook

Now you can start the **Jupyter Notebook.exe** in the root folder of WinPython. Needless to say, Jupyter Notebook is the go-to IDE to learn python and to write script.
