<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/Wheest/Glasgow-Thesis-Template">
    <img src="logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Glasgow Thesis Template for LaTeX.</h3>

  <p align="center">
    An updated thesis template for UoG PhDs
  </p>
</div>

Originally forked from: [sdstrowes/Glasgow-Thesis-Template](https://github.com/sdstrowes/Glasgow-Thesis-Template), Stephen D. Strowes, cheers!

This LaTeX template provides a starting point for CS PhD thesis writing, mostly following the CSE guidelines.
A log of the changes made is given in this README, as well as some comments made during my writing that might help out if you're doing some thesis writing of your own using this or a similar template.

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#fork-notes">Fork notes</a></li>
    <li><a href="#changelog">Changelog</a></li>
    <li><a href="#notes-from-the-original-repo">Notes from the original repo</a></li>
    <li><a href="#some-pg-tips">Some PG-Tips</a></li>
  </ol>
</details>


<!-- Fork notes -->
### Fork notes

The latest thesis guidelines I have from the College of Science & Engineering say that:

> The layout and binding of the thesis should generally conform to the British Standards Institution's “Recommendations for the Presentation of Theses and Dissertations” (BS 4821:1990), but figures and tables may be produced on separate pages or embedded in the body of the text.

You can get this document [here from the BSI Group](https://landingpage.bsigroup.com/LandingPage/Standard?UPI=000000000000216017).  You may need to login with your institution to access it.  Note that at time of writing their website did not work on Firefox, I reported the bug on 2023-04-01.  The digital version was also described "Withdrawn" when I attempted to access it.  I could download a PDF, but it was password protected.  Opening it in "Quick View" appeared to work.

My workflow is Overleaf based, so I don't need the makefile, YMMV.  On Overleaf, ensure your main file is `00-main.tex`

<!-- Changelog -->
### Changelog
- Made new main file `00-main.tex` (numbered files are much easier to navigate, especially in a structured document), with chapters included in the `01-chapters.tex` file.
- Updated the default title, [let's not go mad](https://github.com/Wheest/Glasgow-Thesis-Template/commit/c1b3e5d71db15d19b9c3ba53b00922e7c88d2349#r107069334).
- ~~Removed sans-serif headings. There are no guidelines that I can find for CSE that say this is required, BS 5848:1980 does not mention this.  In addition, [the template given by CSE](https://www.gla.ac.uk/colleges/scienceengineering/graduateschool/postgraduateresearchstudy/submitthesis/) has serif headings.~~ Reverted this change, as I decided I liked the default more.  You can edit this under the [`% Fonts.` section of `glasgowthesis.cls`](https://github.com/Wheest/Glasgow-Thesis-Template/blob/pg-tweaks/glasgowthesis.cls#L36).
- ~~Changed bibliography style from IEEEtran, as guidelines say "preferably following the Vancouver system or the Harvard system".  I adopt Vancouver because it uses numbers rather than names.~~ I transitioned the template to use `biblatex`, which gives us more features.  By default we now have an alphabetic cite style.
- Added `99-standalone.tex` file, for compilation of individual chapters, if your compile times are too long.
- Added a declaration page `01-declaration`.
- Added default background, related work, and conclusion chapters and sections.
- Changed default rendering style to `nogutter`, since the digital version is ~~King~~ Big Lad now.
- Added an optional glossary.
- Added an example code listing using the `minted` package.
- Added a custom chapter header style ("1 | Chapter Name", instead of "Chapter 1\n Chapter Name") See the relevant section in [glasgowthesis.cls](glasgowthesis.cls).
- Added a `\printpublication` command that prints all the authors, rather than `\fullcite`.  This is handy for complimentary publications.
- Added a `sidewaystable` to show how large figures and tables can be rotated if they are too large: there is no space limit in a thesis, make things as big as they need to be.

<!-- ORIGINAL NOTES -->
### Notes from the original repo

> note, not all of these comments may be relevant anymore.
> the original repo is available [@sdstrowes/Glasgow-Thesis-Template](https://github.com/sdstrowes/Glasgow-Thesis-Template)

The original template was built to follow the style guidelines presented in:
 http://www.lib.gla.ac.uk/enlighten/theses/Thesis%20preparation%20guidelines.pdf

The example document should build correctly by running 'make'.

The University guidelines are loose in places. Primarily:

* The front-matter description provided by the University is
  threadbare, and implies a lot of leeway. I do not include a
  University crest, as one is not required. The front page is much
  cleaner if it's text-only.

* The dissertation style is not specified. I use the IEEE transactions
  style mainly because I like it, but it's entirely choice.

Beyond that, I have tried to stick to what is specified. In
particular, font sizes, page borders. I stick to the font requirements
for chapter & section headings, much as I'd like to change
them. Two-sided printing is supported, by changing the "oneside"
parameter to "twoside" in header.tex.


The files are as follows:

* dissertation.tex, which includes:
  - header.tex, which includes:
    + glasgowthesis.cls
    + abstract.tex
    + acknowledgements.tex

  - 10-introduction/introduction.tex
    + 10-introduction/thesis_statement.tex

  - AA-appendix/appendix.tex

  - footer.tex


There's some stuff in the template that is not strictly necessary to
build according to the University guidelines (such as the
TLSind/TLSdel definitions used by texdiff; see
http://tex.stackexchange.com/questions/10134/ for why.)

There will be bugs, there will be errors. Please feed them back!


### Some PG-Tips

Here are some notes that may make writing your thesis easier, or improve the quality of your layout.

#### Short-title for list of figures

At the start of the thesis is a list of your figures.  By default this will take the full caption of your figure, which may be too verbose to have here.  You can define a short caption that will be used in the list of figures like this:

``` tex
\caption[Short version for LoF]{Long version to appear next to the figure}
```

#### Consider at least a semi-local workflow

I got used to using Overleaf during my PhD because it made collaborating with co-authors much easier.
However, thesis writing is a solo endeavour, and there are some things that Overleaf is not well suited for.
For example, renaming or moving a large number of files at once is cumbersome and annoying on Overleaf.
Other issues include: grepping and find-and-replace across files is not well supported, and quickly switching between files is not well supported.

Fortunately all Overleaf projects are also `git` repos, so you should consider doing at least some tasks such as these locally.
You also may find that Overleaf's IDE gets too slow when you have a large project.

Another advantage I found is that one can integrate grammar tools to suggest better ways of wording things.
I found the [LTeX Language server](https://github.com/valentjn/ltex-ls), which does this for LaTeX projects.
There's a plugin for [Emacs](https://github.com/emacs-languagetool/lsp-ltex), as well as other IDEs, thanks LSP.

#### Use a thesis-o-meter

To keep motivated and track your progress, consider using a thesis-o-meter, which will track how you thesis is changing over time.
I developed and open sourced one [available here](https://github.com/Wheest/thesis-o-meter).

#### Use the bibfile from your reference manager

Each paper you wrote will probably have its own bibfile, potentially with references provided by several co-authors.
The formatting may not be consistent, and you may have a bunch of arXiv papers in there that may now be published papers (congrats to them!).
Additionally, when you combine papers, you may have multiple references for the same paper, with different cite keys.

Personally, I would recommend making the main bibfile of you thesis the export from your reference manager (e.g., Mendeley, or [Zotero](https://www.zotero.org/) with the [Better Bibtex extension](https://github.com/retorquere/zotero-better-bibtex)).

When you compile your thesis, you'll get loads of warnings about undefined citations etc.
You can use project-wide find-and-replace to update these.
That being said, your reference manager may not be perfect either, you could have duplicates or arXiv papers in there.
Therefore I've got a wee tool that may help you: (https://github.com/Wheest/bib-boi)[https://github.com/Wheest/bib-boi].
Getting your references in a good state may take a while, but its a good task to do if you're not feeling in one day.

#### Use ChkTeX

Built in linters and error checkers for LaTeX from Overleaf and other IDEs.
But sometimes you should check everything yourself.
The [ChkTeX](https://www.nongnu.org/chktex/) is a battle-harden tool for identifying common typographic errors in your LaTeX project, for example not having a `~` before a `\cite`, or using an `x`` instead of $\times$.

It can be integrated into Emacs AUCTeX, however can also be run from the command line.
An example invocation is:

``` tex
chktex -I $MAIN_FILE --output chktex_output.txt
```

Where `-I` includes all the subfiles that we include with `\input`, and `--output chktex_output.txt` saves the output to a file that you can check at your leisure.
Running with `-W` will turn on all warnings, but will likely be quite pedantic and trigger some false positives.

#### Have each sentence as a new line

LaTeX is not a WYSIWYG word processor, and if you have each sentence on a new line, it will still be combined into a single paragraph.
But why do this?
Well, first it makes it easier to comment out blocks of text, since you can have individual sentences commented out, without having to replicate sentences you are keeping (or manually break them up).
Secondly, it is much cleaner from a version-control perspective.
Tools like Overleaf use `git`, and it is easier to see what has changed between versions if we go line-by-line.
