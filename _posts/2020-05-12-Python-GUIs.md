---
layout: post
title: Building Graphical User Interfaces for Python code
---

When working in R, my work mostly involved reproducible analyses, and consisted mostly of scripts. For the occasional interactive report, [Shiny](https://shiny.rstudio.com) works well for creating graphical interfaces that can be made into stand-alone applications. For building GUIs in Python, there are more options, some of the most common are, in roughly chronological order, `tkinter`, `wxPython` and `PyQt`.

### A graphical batch file renamer

One task that I find easier with a GUI is renaming lots of files, and it turns out to provide a good use case:

* The various renaming options (prefixing, suffixing, numbering, *etc*) require different types of widgets.
* Live preview of the new file names require event-handling
* If possible, I would also like to be able to drag-and-drop the files into the application.

### wxpython

[wxPython](https://wxpython.org/)is a GUI based on the cross-platform [wxWidgets](https://www.wxwidgets.org/) library.
Setting up `wxPython` was problematic without using Conda, and although it's newer than `tkinter`, the documentation is somewhat spotty, so I decided to skip wxpython altogether.

### tkinter

The oldest GUI interface for Python is [tkinter](https://docs.python.org/3/library/tkinter.html), which usually comes bundled with Python, though you still have to install `python3-tk`. The widgets are somewhat limited. Event-handling is accomplished using the widgets' `validation` mechanism, which sadly is rather [poorly documented](https://stackoverflow.com/questions/4140437/interactively-validating-entry-widget-content-in-tkinter). Drag-and-drop support is [spotty](https://docs.python.org/3.9/library/tkinter.dnd.html).

### PyQt

The newest interface is [PyQt](https://wiki.python.org/moin/PyQt), the Python bindings to [Qt](https://www.qt.io/), another C++ cross-platform library. Like any GUI framework, you can specify the GUI you're building by hand in Python, but this gets increasingly tedious. Instead, Qt comes with [Qt Designer](https://doc.qt.io/qt-5/qtdesigner-manual.html), a graphical layout application to build your GUI.

Being more modern, PyQt has more widgets, most notably `table`, which allow a spreadsheet-like layout. I used this to show the old and new file names side-by-side. 

It was fairly straightforward to develop my batch file renamer in PyQt even without using Qt Designer as you can see in my [repository](https://github.com/ptvan/batchRenamer).
