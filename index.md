# Lesson 2 --- Filling the document

We've set up our basic document, now it's time to put some information in it! For this step, you'll need the [Project Gutenberg version of *Alice in Wonderland*](). Notably, you'll want to grab the text version [here](http://www.gutenberg.org/files/11/11-0.txt).

## Okay, I grabbed it, what next?

First things first, we need to put the context from the downloaded text file into the {{site.data.macros.latex}} file we created in the previous lesson. Now, we could just copy and paste the whole document in there, but a book is more than just letters; we'll want to give it some structure.

## Parts of a book.

A book comes in several parts. This may be obvious when said aloud, but now that you're going to be typesetting one, it's worth thinking about what those parts are.

Lets see...well, you've got the title page, and then probably the copyright.  From there, you go to the table of contents. Maybe a preface after that? Then you get to the content.

Lets agree that everything up until the content is called the *frontmatter*, and that the beefy part of the book --- all those tasty words --- is the *mainmatter*.

In the mainmatter, you will probably have some chapters, and in each of those chapters you may have some sections, or subsections, or subsubsections, or...well, lets not get carried away.

Still, within those chapters, you'll have words, and those words come in paragraphs (or stanzas, if it's verse we're talking about), and they may be styled in various ways, such as *italics* or **boldface** or `monospaced`.

After all of those chapters, perhaps we'll have an afterword, or index, or attributions. Lets agree to call that the *backmatter*.

So, our book looks like this:

* Frontmatter
    * Title page
    * Copyright page
    * Table of contents
    * Preface
* Mainmatter
    * Chapters
        * paragraphs or verses
            * words
* Backmatter
    * Afterword
    * Attribution

## Putting it into {{site.data.macros.latex}}.

Thankfully, {{site.data.macros.latex}} comes with some commands to make this happen. Notably, it has `\frontmatter`, `\maketitle` (as we've seen), `\tableofcontents`, `\mainmatter`, `\chapter{}`, and `\backmatter`

If we are to put our downloaded copy of *Alice* into the format, it's easy to get that done.  There is obviously some title material in there, which we've already done in our `\title{}` commands. There's also the Project Gutenberg attribution. That's our frontmatter. We can start that whole section with `\frontmatter`, and once we've pasted up to the `CHAPTER I...` bit, we can put `\mainmatter`.

The chapters are easy to manage as well. We can cut and paste the content of each chapter directly in there. As for the chapter names, that's a simple command: `\chapter{Chapter name}`. So, the first chapter would be `\chapter{Down the Rabbit Hole}`.

Why no `Chapter I.` in there? {{site.data.macros.latex}} will take care of that for us.

Once we've finished with the chapters, we can start the end of the book with `\backmatter`. In here, we can paste the Project Gutenberg license.

## Basic formatting.

If you run the command as specified in the first lesson, you might be disappointed:


```
$ pdflatex alice-in-wonderland.tex
This is pdfTeX, Version 3.14159265-2.6-1.40.18 (TeX Live 2017) (preloaded format=pdflatex)
 restricted \write18 enabled.
entering extended mode
(./alice-in-wonderland.tex
LaTeX2e <2017-04-15>
Babel <3.10> and hyphenation patterns for 84 language(s) loaded.
(/usr/local/texlive/2017/texmf-dist/tex/latex/memoir/memoir.cls
Document Class: memoir 2016/05/16 v3.7f configurable book, report, article docu
ment class
(/usr/local/texlive/2017/texmf-dist/tex/generic/oberdiek/ifpdf.sty)
(/usr/local/texlive/2017/texmf-dist/tex/latex/ifetex/ifetex.sty
(/usr/local/texlive/2017/texmf-dist/tex/plain/ifetex/ifetex.tex))
(/usr/local/texlive/2017/texmf-dist/tex/generic/ifxetex/ifxetex.sty)
(/usr/local/texlive/2017/texmf-dist/tex/generic/oberdiek/ifluatex.sty)
(/usr/local/texlive/2017/texmf-dist/tex/latex/memoir/mem10.clo)
(/usr/local/texlive/2017/texmf-dist/tex/latex/memoir/mempatch.sty))
(./alice-in-wonderland.aux) [1{/usr/local/texlive/2017/texmf-var/fonts/map/pdft
ex/updmap/pdftex.map}]
No file alice-in-wonderland.toc.
[2] [1] [2] [3] [4]
! Missing $ inserted.
<inserted text>
                $
l.240 _
       I_ shan’t be able! I shall be a great deal too far off to trouble
?
```

What happened here? Well, some of the formatting used in the text file to show italics was shown with `_words to be italicized_`, which {{site.data.macros.latex}} isn't a fan of. Thankfully, there are only two instances of this, both of which are `_I_`. Replace both of those with `\emph{I}`.

`\emph{}` is another {{site.data.macros.latex}} command. It tells the software to make the text within the brackets *emphasized*. In particular, it makes it italicized. You can also use the `\textit{}` command which, as might be inferred, makes italic text. Using `\emph{}` is a design decision on my part, due to the way HTML works, but you can use either.

Now, when we run our command, we should see some better output!

## The license.

The license provides some interesting structural and layout challenges.

### The trademark symbol.

While there are prettier ways of accomplishing it, for now, lets replace the `-tm` with a trademark symbol. We can do this with a simple `\textsuperscript{TM}`. This, naturally, puts a TM in superscript next to the word. Find and replace all instances of `-tm` with this.

### The sections.

All of the parts of the license may be broken down into sections, subsections, and subsubsections. For each section, encase the section header in `\section{}` commands. Then for each subsection (e.g: 1.A.), encase that number in `\subsection{}`, commands (followed by newlines), and for each subsubsection (e.g: 1.A.1.), encase that number in `\subsubsection` commands (followed by newlines).

This will give the license some structure

### Addresses and newlines.

For the address, we'll be using linebreaks, which are accomplished with a simple `\\`. After the first line introducing the address ("For additional contact information:"), include a `\\`. Do so also for the first two lines of the address. We don't need one for the last line, as that's at the end of a paragraph anyway.

### Lists.

In subsubsection 1.E.8., there is a list of items. Lists in {{site.data.macros.latex}} are accomplished with an *environment*. In {{site.data.macros.latex}}, an environment is a section of the document that is interpreted in a specific way or wherein commands may have a certain meaning.

In this case, we want a list, which is accomplished with the `itemize` environment. This environment looks like this:

```
\begin{itemize}
  \item Lorem ipsum
  \item dolor sit argument
  \item ...
\end{itemize}
```

If those `being`s and `end`s seem familiar, that's because the whole document is an environment, starting with `\begin{document}`.

Turn that text list into a {{site.data.macros.latex}} list by surrounding it with the `begin`/`end` commands, and replacing the bullets (here, a hyphen) with `\item`.

### Gotchas: special characters.

There are a few characters here we'll want to be careful of:

* `%` - A percent sign begins a comment. That means that {{site.data.macros.latex}} ignores everything following that symbol on the line.
* `$` - A dollar sign indicates a math environment, which we don't want.

To get those characters to print literally, we need to *escape* them. In {{site.data.macros.latex}}, that means preceding them with a backslash: `\$` or `\%`.

## Table of contents.

Back up in the frontmatter, you can include a table of contents with the helpfully-named command `\tableofcontents`.

This is a good time to introduce the idea of references. When {{site.data.macros.latex}} builds a document, it puts it together page by page. When it gets to a chapter, it makes a note to itself saying, "aha, chapter 1 begins on this page".

The table of contents, however, has already been written! {{site.data.macros.latex}} can't go back and rewrite that part. Therefore, it's a good idea to run the command *twice* when page numbers have changed (or just in general). The first time through will generate the page numbers for the chapters, and the second time through will make sure the page numbers in the table of contents are correct.

## Awesome. What's next?

Next, we'll introduce some commands to help make it easier to work on the book by splitting it into different files. See you in lesson 3!
