# Lesson 1 --- The Very Beginning

In this lesson, you will be introduced to {{site.data.macros.latex}} and its basic structure. We'll be starting our publication project: a new print copy of Lewis Carroll's *Alice's Adventues in Wonderland*, which is in the public domain.

## What is {{site.data.macros.latex}}?

{{site.data.macros.latex}} is a typesetting and layout program. It takes input in the form of `.tex` files, and from them produces output in many different formats. There are quite a few, but the one we will be paying attention to is PDF, which is good for printing just about anywhere.

## Okay, how do I get it?

There's a few ways, depending on your operating system.

### Ubuntu and Debian

Open a terminal and type the following:

    sudo apt install pdflatex

It will ask for your password, then start installing the software.

### macOS

Open a terminal and type the following:

    brew install cask mactex

This will download and install everything you need to run {{site.data.macros.latex}}.

### Windows

Follow the instructions [here](https://miktex.org/howto/install-miktex) to install the Windows distribution, <span class="LaTeX">MiKT<sub>e</sub>X.

## I've installed it, now what?

You'll need to the first step of the example. You can get it [here](https://github.com/makyo/latex-book-tutorial/blob/lesson-1/alice-in-wonderland.tex), but since it's quite small at the moment, here's the contents:

```latex
\documentclass{memoir}

\title{Alice's Adventures in Wonderland}
\author{Lewis Carroll}
\date{1865}

\begin{document}
\maketitle
\end{document}
```

You can save this file as `alice-in-wonderland.tex`

## Whoa, what the heck? What's going on here?

Let's walk through the document line by line.

1. Line 1 tells {{site.data.macros.latex}} what kind of document we want to make. There's a `book` type, but most everyone agrees that `memoir` is better. Another example would be `article`, but we don't want that here.
2. Lines 3-5 set up some information about the document. We have the title, obviously, as well as the author and the year of production. Notice how these start with a backslash and have the stuff we want in braces? Those are commands. There is a `title` *command* which accepts some information as an *argument*; in this case, `Alice's Adventures in Wonderland`. The same applies to `author` and `date`
3. Line 7 tells {{site.data.macros.latex}} that we are starting our document. `begin` and `end` on line 9 form an *environment*. This tells {{site.data.macros.latex}} it should treat everything between the `begin` command and the `end` command a certain way. In this case, it tells it to treat the contents as a document.
4. Line 8 tells {{site.data.macros.latex}} to print all of the stuff that forms the title. This includes the title, author, and date.

## Okay, I think I get that. How do I see it in practice?

You'll need to run `pdflatex` against that file. On linux and macOS, you can simply type:

    pdflatex alice-in-wonderland.tex

*Note:* Madison will need to see how to do this on Windows.

This will show you a bunch of information as {{site.data.macros.latex}} processes the file and generates the PDF output. For example, you may see the following:

```
This is pdfTeX, Version 3.14159265-2.6-1.40.17 (TeX Live 2016) (preloaded format=pdflatex)
 restricted \write18 enabled.
entering extended mode
(./alice-in-wonderland.tex
LaTeX2e <2016/03/31>
Babel <3.9r> and hyphenation patterns for 83 language(s) loaded.
(/usr/local/texlive/2016/texmf-dist/tex/latex/memoir/memoir.cls
Document Class: memoir 2016/05/16 v3.7f configurable book, report, article docu
ment class
(/usr/local/texlive/2016/texmf-dist/tex/generic/oberdiek/ifpdf.sty)
(/usr/local/texlive/2016/texmf-dist/tex/latex/ifetex/ifetex.sty
(/usr/local/texlive/2016/texmf-dist/tex/plain/ifetex/ifetex.tex))
(/usr/local/texlive/2016/texmf-dist/tex/generic/ifxetex/ifxetex.sty)
(/usr/local/texlive/2016/texmf-dist/tex/generic/oberdiek/ifluatex.sty)
(/usr/local/texlive/2016/texmf-dist/tex/latex/memoir/mem10.clo)
(/usr/local/texlive/2016/texmf-dist/tex/latex/memoir/mempatch.sty))
(./alice-in-wonderland.aux) [1{/usr/local/texlive/2016/texmf-var/fonts/map/pdft
ex/updmap/pdftex.map}] (./alice-in-wonderland.aux) )</usr/local/texlive/2016/te
xmf-dist/fonts/type1/public/amsfonts/cm/cmr10.pfb></usr/local/texlive/2016/texm
f-dist/fonts/type1/public/amsfonts/cm/cmr12.pfb>
Output written on alice-in-wonderland.pdf (1 page, 22850 bytes).
Transcript written on alice-in-wonderland.log.
```

That's a lot of stuff, but really, all we're looking for, is the line `Output written on alice-in-wonderland.pdf (1 page, 22850 bytes).` Success! We've generated our PDF! You can open the file `alice-in-wonderland.pdf` and take a look. It'll have one page with all of our title information on it.

## Sweeet. What's next?

Next, we'll start putting in some content. See you in Lesson 2!
