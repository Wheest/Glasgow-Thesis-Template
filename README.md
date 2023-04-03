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

Forked from:

<https://github.com/sdstrowes/Glasgow-Thesis-Template>
Stephen D. Strowes, 2011.
sdstrowes@gmail.com


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#notes-from-the-original-repo">Notes from the original repo</a></li>
    <li><a href="#fork-notes">Fork notes</a></li>
    <li><a href="#changelog">Changelog</a></li>
    <li><a href="#some-pg-tips">Some PG-Tips</a></li>
  </ol>
</details>

<!-- ORIGINAL NOTES -->
### Notes from the original repo

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

<!-- Fork notes -->
### Fork notes

The latest thesis guidelines I have from the College of Science & Engineering say that:

> The layout and binding of the thesis should generally conform to the British Standards Institution's “Recommendations for the Presentation of Theses and Dissertations” (BS 4821:1990), but figures and tables may be produced on separate pages or embedded in the body of the text.

You can get this document [here from the BSI Group](https://landingpage.bsigroup.com/LandingPage/Standard?UPI=000000000000216017).  You may need to login with your institution to access it.  Note that at time of writing their website did not work on Firefox, I reported the bug on 2023-04-01.  The digital version was also described "Withdrawn" when I attempted to access it.  I could download a PDF, but it was password protected.  Opening it in "Quick View" appeared to work.

My workflow is Overleaf based, so I don't need the makefile, YMMV.  On Overleaf, ensure your main file is `00-main.tex`

<!-- Changelog -->
### Changelog
- Made new main file `00-main.tex` (numbered files are much easier to navigate, especially in a structured document).
- Updated the default title, [let's not go mad](https://github.com/Wheest/Glasgow-Thesis-Template/commit/c1b3e5d71db15d19b9c3ba53b00922e7c88d2349#r107069334).
- ~~Removed sans-serif headings. There are no guidelines that I can find for CSE that say this is required, BS 5848:1980 does not mention this.  In addition, [the template given by CSE](https://www.gla.ac.uk/colleges/scienceengineering/graduateschool/postgraduateresearchstudy/submitthesis/) has serif headings.~~ Reverted this change, as I decided I liked the default more.  You can edit this under the [`% Fonts.` section of `glasgowthesis.cls`](https://github.com/Wheest/Glasgow-Thesis-Template/blob/pg-tweaks/glasgowthesis.cls#L36).
- Changed bibliography style from IEEEtran, as guidelines say "preferably following the Vancouver system or the Harvard system".  I adopt Vancouver because it uses numbers rather than names.
- Added `99-standalone.tex` file, for compilation of individual chapters, if your compile times are too long.
- Added a declaration page `01-declaration`.
- Added default background, related work, and conclusion chapters and sections.
- Changed default rendering style to `nogutter`, since the digital version is King now.
- Added an optional glossary

### Some PG-Tips

Here are some notes that may make writing your thesis easier, or improve the quality of your layout.

###### Short-title for list of figures

At the start of the thesis is a list of your figures.  By default this will take the full caption of your figure, which may be too verbose to have here.  You can define a short caption that will be used in the list of figures like this:

``` tex
\caption[Short version for LoF]{Long version to appear next to the figure}
```

###### Consider at least a semi-local workflow

I got used to using Overleaf during my PhD because it made collaborating with co-authors much easier.
However, thesis writing is a solo endeavour, and there are some things that Overleaf is not well suited for.
For example, renaming or moving a large number of files at once is cumbersome and annoying on Overleaf.
Fortunately all Overleaf projects are also `git` repos, so you should consider doing at least some tasks such as these locally.

###### Use a thesis-o-meter

To keep motivated and track your progress, consider using a thesis-o-meter, which will track how you thesis is changing over time.
I developed and open sourced one [available here](https://github.com/Wheest/thesis-o-meter).
