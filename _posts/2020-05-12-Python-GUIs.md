---
layout: post
title: Building Graphical User Interfaces for Python code
---

When working in R, my work mostly involved reproducible analyses, and consisted mostly of scripts. For the occasional interactive report, [Shiny](https://shiny.rstudio.com) works well for creating graphical interfaces that can be made into stand-alone applications. For building GUIs in Python, there are more options, the most common are, in roughly chronological order, `tkinter`, `wxPython` and `PyQt`.

### A graphical batch file renamer

One task that I find easier with a GUI is renaming lots of files. I wanted control over the various renaming options: prefixing, suffixing, numbering, *etc*, with a live preview of the new file names. If possible, I would also like to be able to drag-and-drop the files into the application.

### tkinter

The oldest GUI interface for Python is [tkinter](https://docs.python.org/3/library/tkinter.html), which usually comes bundled with Python, though you still have to install `python3-tk`.

### wxpython

Slightly more modern is [wxPython](https://wxpython.org/), a GUI based on the cross-platform [wxWidgets](https://www.wxwidgets.org/) library.
Setting up `wxPython` was problematic without using Conda, and the documentation is somewhat spotty, so I decided to skip wxpython altogether.

### PyQt

The newest interface is [PyQt](https://wiki.python.org/moin/PyQt), the Python bindings to [Qt](https://www.qt.io/), another C++ cross-platform library. Like any GUI framework, you can specify the GUI you're building by hand in Python, but this gets increasingly tedious. Instead, Qt comes with [Qt Designer](https://doc.qt.io/qt-5/qtdesigner-manual.html), a GUI application to build your GUI.

It was fairly straightforward to develop my batch file renamer in PyQt even without using Qt Designer as you can see in my [repository](https://github.com/ptvan/batchRenamer).
