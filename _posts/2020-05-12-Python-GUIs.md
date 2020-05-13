---
layout: post
title: Building Graphical User Interfaces for Python code
---

When working in R, my work mostly involved reproducible analyses, and consisted mostly of scripts. For the occasional interactive report, [Shiny](https://shiny.rstudio.com) works well for creating graphical interfaces that can be made into stand-alone applications. For building GUIs in Python, there are more options, the most full-featured and documented are `tkinter`, `wxPython` and `PyQt`.

### tkinter

The oldest GUI interface for Python is [tkinter](https://docs.python.org/3/library/tkinter.html), which usually comes bundled with Python.

### wxpython

Slightly more modern is [wxPython](https://wxpython.org/), a GUI based on the cross-platform [wxWidgets](https://www.wxwidgets.org/).

### PyQt

The newest interface is [PyQt](https://wiki.python.org/moin/PyQt), the Python bindings to [Qt](https://www.qt.io/), another C++ cross-platform library. Like any GUI framework, you can specify the GUI you're building by hand in Python, but this gets increasingly tedious. Instead, Qt comes with [Qt Designer](https://doc.qt.io/qt-5/qtdesigner-manual.html), a GUI application to build your GUI.

### A small example application

One task that I find easier with a GUI is renaming lots of files in a programmatic way. It was fairly straightforward to develop one, as you can see in my [batchRenamer](https://github.com/ptvan/batchRenamer) repository.
