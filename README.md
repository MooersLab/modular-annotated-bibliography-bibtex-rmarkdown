# modular-annotated-bibliography-bibtex-rmarkdown
In surgery![Version](https://img.shields.io/static/v1?label=matplotlib-voice-in&message=0.0&color=brightcolor)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)


# Template in R Markdown for generating a modular, illustrated, and annotated bibliography with BibTeX


This template can be used in RStudio or an advanced text editor.
Many people prefer to write in R Markdown.
R Markdown is a wrapper for LaTeX.


## System requirements

You need a recent version of R.
R Studio is optional.

You can install R's slimmed-down version of texlive.

```R
tinytex::install_tinytex()
```
I have yet to test this.
I used the full texlive distribution to develop this template.

You can import LaTeX packages using the following in the YAML header of the Rmd file:

``` yaml
pdf_document:
  extra_dependencies: ['amsmath', 'minted']
```

The template has a code block to send the shell escape flag to the PDF compiler to enable the use of the minted package for syntax highlighting of code blocks.


## You will need to install the following R packages: 

The packages in [] are optional.

- rmarkdown
- [acronymsdown]()
- [glossary](https://debruine.github.io/glossary/) 


## bash function for compiling and 



## Update history

|Version      | Changes                                                                                                                                  | Date                 |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------|:--------------------|
| Version 0.1 |   Added badges, funding, and update table.  Initial commit.                                                                                                                | 2024 October 26  |

## Sources of funding

- NIH: R01 CA242845
- NIH: R01 AI088011
- NIH: P30 CA225520 (PI: R. Mannel)
- NIH: P20 GM103640 and P30 GM145423 (PI: A. West)
