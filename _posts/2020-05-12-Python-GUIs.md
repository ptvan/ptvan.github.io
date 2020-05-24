---
layout: post
title: Building Graphical User Interfaces for Python code
---

When working in R, my work mostly involved reproducible analyses, and consisted mostly of scripts. For the occasional interactive report, [Shiny](https://shiny.rstudio.com) works well for wrapping graphical interfaces around R scripts that can be made into stand-alone applications. For building GUIs in Python, there are more options, including `tkinter`, `wxPython` and `PyQt`.

### A graphical batch file renamer

One task that I find easier with a GUI is renaming lots of files, and it turns out to provide a good use case:

* The various renaming options (prefixing, suffixing, numbering, *etc*) require different types of widgets.
* Live preview of the new file names require event-handling
* If possible, I also want to drag-and-drop the files into the application.

### wxpython: old and outdated

[wxPython](https://wxpython.org/) is a GUI library based on the cross-platform [wxWidgets](https://www.wxwidgets.org/) library.
Setting up `wxPython` was problematic without using Conda, and although it's newer than `tkinter`, the documentation is somewhat spotty, so I decided to skip wxpython altogether.

### tkinter: old but workable

The oldest GUI library for Python is [tkinter](https://docs.python.org/3/library/tkinter.html), which usually comes bundled with Python, though you still have to install `python3-tk`. You can use the [Python Automatic GUI Generator](http://page.sourceforge.net/) (PAGE), or specify the GUI you're building by hand in Python, which was what I did.

The widgets provided by `tkinter` are adequate for most purposes. To display the old and new file names in my app, I created two text fields, then populated one filename per line with linebreaks. Hacky, but functional.  

Event-handling is accomplished using the widgets' `validation` mechanism, which sadly is rather [poorly documented](https://stackoverflow.com/questions/4140437/interactively-validating-entry-widget-content-in-tkinter). Drag-and-drop support is possible via [tkinter.dnd](https://docs.python.org/3.9/library/tkinter.dnd.html), which apparently is due to be deprecated.

### PyQt: modern and slick

The newest interface is [PyQt](https://wiki.python.org/moin/PyQt), the Python bindings to [Qt](https://www.qt.io/), another C++ cross-platform library. Qt also comes with [Qt Designer](https://doc.qt.io/qt-5/qtdesigner-manual.html), a graphical layout tool to build your GUI, but it's certainly possible to create simple applications without it, as you can see in my [repository](https://github.com/ptvan/batchRenamer).

Being more modern, PyQt has more widgets, most notably `table`, which allow a spreadsheet-like layout. I used this to show the old and new file names side-by-side instead of two separate text fields in the `tkinter` version of the app.

Event-handling is straightforwardly supported for each widget type.
