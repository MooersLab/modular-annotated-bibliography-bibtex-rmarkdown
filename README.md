# modular-annotated-bibliography-bibtex-rmarkdown
![Version](https://img.shields.io/static/v1?label=modular-annotated-bibliography-bibtex-rmarkdown&message=0.1&color=brightcolor)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)


# Template in R Markdown for generating a modular, illustrated, and annotated bibliography for the 21st Century with BibTeX

## Status: works

## What is this?

This template supports making single-paragraph annotations found in classical annotated bibliographies for undergrad homework.
It also supports making multi-paragraph entries illustrated with figures, tables, equations, code listings, hyperlinks to videos online, and citations inside and outside the annotated bibliography.
Yes, the annotated bibliography includes an inclusive Literature Cited section.
These additional features make this modern approach to knowledge management more effective as a tool in science research and for self-study.
We have to use a modular approach to the annotatons to be able to avoid the loss of whitespace between paragraphs and to enable textwrapping around embedded figures.
The modular approach also enables the reuse of annotations in the  bibliographies of related projects.

The 21st Century bibliography has the following enhanced features that the classic annotated bibliography lacks:

- No longer restrained by the `annote` field in the BibTeX entry.
- Modular annotation for easy reuse in related projects.
- Images
- Tables
- Equations
- Code blocks
- Hyperlinks: internal and external
- Bibliographic entries can be reordered for subgrouping by category. 
- Table of contents, hyperlinked to sections
- Index of terms
- Bibliography includes papers cited outside of those listed in the annotated bibliography.
- List of acronyms used
- List of glossary terms used
- List of mathematical notation
  
## Why R Markdown?

This template can be used in RStudio or an advanced text editor.
Many people prefer to write in R Markdown.
R Markdown is a [wrapper](https://everyday.codes/tutorials/how-to-use-latex-in-rmarkdown/) for LaTeX.


## System requirements

You need a recent version of R.
R Studio is optional.

You can use your current install of LaTeX (e.g., texlive).
If you lack one, you can install via R a slimmed-down version of texlive called tinytex.
It will fetch and install packages as you need them.

```R
tinytex::install_tinytex()
```

You can install and import LaTeX packages using the following in the YAML header of the main Rmd file:

```yaml
pdf_document:
  extra_dependencies: ['amsmath', 'minted']
```

The template has a code block to send the `-shell-escape` flag to the PDF compiler to enable the use of the minted package for syntax highlighting of code blocks.


## You will need to install the following R packages: 

The packages in [ ] are alternatives to the gloassaries package in LaTeX.

- rmarkdown
- [acronymsdown](https://rchaput.github.io/acronymsdown/)
- [glossary](https://debruine.github.io/glossary/) 

## Additional requirements

- a BibTeX file (annote fields are not used. )
- a `~/bibNotes` folder for storing the annotations
- a `~/bibNotes/images` folder for storing image files
- a `~/glossaries` folder to store the list of acronyms and glossary files
  
## Adding to the bibliography

1. Provide path to your BibTeX file in aragument to `\bibliography{}`.
2. Create a tex or Rmd file for each entry and store it in the bibNotes folder.
3. Store associated image files in the images subfolder.
4. Inject the bibliographic entry in a subsection heading by calling with its citekey in the argument for \bibentry{}. See below.
   
```latex
\subsection*{\bibentry{Mooers2021TemplatesForWritingPyMOLScripts}}
\addcontentsline{toc}{subsection}{Mooers2021TemplatesForWritingPyMOLScripts}
\input{/Users/blaine/bibNotes/Mooers2021TemplatesForWritingPyMOLScripts.Rmd}
```

## Bash function for compiling to PDF and automatically opening the PDF

This function supports editing the R Markdown file outside of R Studio and then compiling it from the command line (e.g., `rmd myabib` to compile to PDF and have the PDF opended in the Preview.app).

```bash
function rmd {
echo "Compile Rmd (R Markdown) file with R, and open the resulting PDF with the Preview.app. (Mapped ot the alias 'pre')."
if [ $# -lt 1 ]; then
  echo 1>&2 "$0: not enough arguments"
  echo "Usage1: rmd <filename stem>"
  return 2
elif [ $# -gt 1 ]; then
  echo 1>&2 "$0: too many arguments"
  echo "Usage1: rmd  <filename stem>"
  return 2
fi
Rscript -e "library('rmarkdown');library('acronymsdown');library('gloassary');rmarkdown::render('$1.Rmd')" && pre $1.pdf
}

```

### Notes
The compiling of the PDF is slow.
This is tolerable if you only occasional need to compile the master file to make a PDF.
If you seek a more interactive experience, try the typst variant found [here](https://github.com/MooersLab/modular-annotated-bibliography-typst).
Typst may be easier for beginners to learn.
It has all of the same features except support for interactive computing in code blocks in RStudio.

## Python function for converting acronyms.tex to YAML format for acronymsdown

## Python function for converting glossary.tex to YAML format for glossary


## Update history

|Version      | Changes                                                                                                                                                    | Date                |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| Version 0.1 |   Added badges, funding, and update table. Initial commit.                                                                    | 2024 November 1     |

## Sources of funding

- NIH: R01 CA242845
- NIH: R01 AI088011
- NIH: P30 CA225520 (PI: R. Mannel)
- NIH: P20 GM103640 and P30 GM145423 (PI: A. West)
