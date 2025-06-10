---
layout: post
title: Notetaking with Markdown, LaTeX and beyond
---

As a professional scientist and lifelong geek, I take notes a lot. After several decades of note-taking, I accumulated 
a significant amount of information that I sometimes need to retrieve ("I read a nice article that explained Rayleigh vs. Raman scattering really well. Now where is it ?!"). As a person living the Google era, I have also gotten less patient with looking for information. Fortunately, I've figured out how to keep notes. The hard way. Mostly.

### The early days: plaintext and and Journler
In college I wrote all my notes by hand since I did not have a laptop (and using one in lecture was generally frowned upon anyway). When I started working in a lab I kept a physical lab notebook. Since my research was entirely computational, saving notes in plaintext files solved my biggest problem: text searching. 

During graduate school I only used two computers: my personal MacBook and the lab computer that powered the high-dynamic-range imager that was my PhD thesis. As it became obviously that the majority of my work would be computational, I used a OSX app called Journler on my MacBook that could embed images and also supports searching. Journler was a made by a one-person software company but when it was shut down I was still able to save all the notes from my PhD as a single PDF. This was an instructive experience: though I don't have super-sensitive information like missile launch codes in my notes, the idea of one day being locked out of them because my subscription lapsed or the vendor going out of business concerns me.

### EverNote and NixNote
After graduate school my work involved an HPC cluster, my office desktop and sometimes I would also work from home on my personal laptop, so my main concern was keeping notes in all 3 places consistent. A few of my colleagues were using EverNote and it seemed to offer what I needed: it supported multimedia content, full-text search and offered cross-platform syncing. Being wary of vendor lock-in, I also used [NixNote](https://github.com/baumgarr/Nixnote2), which connects to EverNote servers from Linux but also saves a user-accessible copy of my notes locally. However, EverNote kept reducing the number of computers you can store your notes on, eventually down to one, which negated its use case for me. 

### Markdown, LaTeX+VSCode
I have used RStudio for a long time so was familiar with RMarkdown and by extension Markdown. Markdown text can be manually converted to most other formats using [Pandoc](https://pandoc.org/). At the same time, I also wrote and ran most of my Python code in VSCode, which can preview Markdown files. This meant that I can keep my notes and code together and sync both through GitHub, regardless of where or what I was doing.

Except, occasionally I would need to write an equation or insert a citation. What I really needed was LaTeX. I have used it previously, but re-transcribing my PhD thesis into LaTeX showed me the exponential benefit LaTeX had for larger projects (my committee asked me to write my thesis in Word so they can edit and share it easily among themselves). 

Fortunately, here VSCode's extensions came to the rescue. Once set up, I can write LaTeX and upon saving, the `.tex` file would render and display a PDF, same for my `.bib` bibliography files. As an added bonus, there are also great LaTeX templates for common document types like theses, resumes, _etc._ I have achieved notetaking nirvana ! Or have I...?

### Typst+VSCode
[Typst](https://typst.app/) looks pretty interesting, having many of LaTeX's greatest features while simplifying syntax and error messages. While there is a web interface, there also are [instructions to set up Typst in VSCode](https://gist.github.com/jason-s/a91b6b70017766ba9143b662405512a4).