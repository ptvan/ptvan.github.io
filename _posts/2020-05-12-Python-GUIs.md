---
layout: post
title: Building Graphical User Interfaces for Python code
---

When working in R, my work mostly involved reproducible analyses, and consisted mostly of scripts. For the occasional interactive report, [Shiny](https://shiny.rstudio.com) works well for creating graphical interfaces that can be made into stand-alone applications. For building GUIs in Python, there are more options, the most full-featured and documented are `tkinter`, `PyQt` and `wxpython`.

### tkinter

The oldest GUI interface for Python is [tkinter](https://docs.python.org/3/library/tkinter.html), which usually comes bundled with Python.

### PyQt

A more modern interface is [PyQT](https://wiki.python.org/moin/PyQt), the python bindings to [Qt](https://www.qt.io/), itself written in C++. Like any GUI framework, you can specify the GUI you're building by hand in Python, but this gets increasingly tedious. Instead, Qt comes with [Qt Designer], a GUI application to build your GUI.

### wxpython

### A small example application

One task that I find easier with a GUI is renaming lots of files in a programmatic way. It was fairly straightforward to develop one, as you can see in my [batchRenamer](https://github.com/ptvan/batchRenamer) repository.
