---
layout: post
title: Interactive data visualization in Python
---

A few years ago, I wrote about making [GUI applications in Python](https://ptvan.github.io/Python-GUIs/). However, in my experience, most of the time what we really need are just _dashboards_, simple Python apps that visualize data, with interactive filtering and faceting. One path of low (if not least) resistance is of course iPython notebooks, but there are increasingly more feature-rich options, depending on your particular needs and constraints.

### HoloViews
Typically, output in iPython notebooks like dataframes or figures are rendered as static inline "chunks". [HoloViews](https://holoviews.org/getting_started/index.html) allows these chunks to contain interactive plots. I actually wrote about HoloViews [briefly in the past](https://ptvan.github.io/analyzing-geographic-data/). 

Individual plots can be composed together in the same chunk using the `+` operator used in the ["grammar of graphics"](https://vita.had.co.nz/papers/layered-grammar.pdf) style. Facetting is also possible. Individual Holoview elements can be exported as HTML files, but the overall experience still feels like a notebook since the underlying Python code REPL is still visible.

### Plotly Dash
[Dash](https://dash.plotly.com/) is built on top of [Flask](https://flask.palletsprojects.com/en/stable/), [Plotly](https://plotly.com/javascript/) and [React](https://react.dev/). If you have used R and [Shiny](https://shiny.posit.co/) previously, Dash will feel very familiar. The entire dashboard is invoked using a single `Dash()` call, visual widgets are added and interactivity is handled via callbacks. The experience feels more like a dashboard: by default no REPL is exposed, and code changes require the entire app to be rebuilt and restarted.  

### Streamlit
The latest visualization framework is [Streamlit](https://streamlit.io/) (started 2019). Its widgets look a bit more modern with sensible defaults that contribute to an easier learning curve and faster prototyping. Compared to Dash, Steamlit has a smaller (but rapidly growing) user community.