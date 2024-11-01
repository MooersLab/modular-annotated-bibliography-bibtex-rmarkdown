# modular-annotated-bibliography-bibtex-rmarkdown
In surgery![Version](https://img.shields.io/static/v1?label=modular-annotated-bibliography-bibtex-rmarkdown&message=0.1&color=brightcolor)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)


# Template in R Markdown for generating a modular, illustrated, and annotated bibliography for the 21st Century with BibTeX

## Status: Work in Progress

## What is this?

This template supports making single-paragraph annotations found in classical annotated bibliographies for undergrad homework.
It also supports making multi-paragraph entries illustrated with figures, tables, equations, code listings, hyperlinks to videos online, and citations inside and outside the annotated bibliography.
Yes, the annotated bibliography includes an inclusive Literature Cited section.
These additional features make this modern approach to knowledge management more effective as a tool in science research and for self-study.

## Why R Markdown?

This template can be used in RStudio or an advanced text editor.
Many people prefer to write in R Markdown.
R Markdown is a [wrapper](https://everyday.codes/tutorials/how-to-use-latex-in-rmarkdown/) for LaTeX.


## System requirements

You need a recent version of R.
R Studio is optional.

You can install R's slimmed-down version of texlive.

```R
tinytex::install_tinytex()
```
I have yet to test this.
I used the full texlive distribution to develop this template.

You can install and import LaTeX packages using the following in the YAML header of the main Rmd file:

```yaml
pdf_document:
  extra_dependencies: ['amsmath', 'minted']
```

The template has a code block to send the shell escape flag to the PDF compiler to enable the use of the minted package for syntax highlighting of code blocks.


## You will need to install the following R packages: 

The packages in [] are optional.

- rmarkdown
- [acronymsdown](https://rchaput.github.io/acronymsdown/)
- [glossary](https://debruine.github.io/glossary/) 

## Addition requirements

- a BibTeX file (no annote fields required)
- a `~/bibNotes` folder for storing the annotations
- a `~/glossaries` folder to store the list of acronyms and glossary files
  


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
This is tolerable if you only occasional need to 
If you seek a more interactive experience, try the typst variant found [here](https://github.com/MooersLab/modular-annotated-bibliography-typst).
It has all of the same features except support for interactive computing in code blocks.

## Python function for converting acronyms.tex to YAML format for acronymsdown

## Python function for converting glossary.tex to YAML format for glossary


## Update history

|Version      | Changes                                                                                                                                   | Date                |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| Version 0.1 |   Added badges, funding, and update table.  Initial commit.                                                                               | 2024 November 1     |

## Sources of funding

- NIH: R01 CA242845
- NIH: R01 AI088011
- NIH: P30 CA225520 (PI: R. Mannel)
- NIH: P20 GM103640 and P30 GM145423 (PI: A. West)
