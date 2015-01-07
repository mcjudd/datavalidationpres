Automating routine surveillance data validation using RMarkdown, knitr, and some basic HTML 
========================================================
author: Mike Judd, MPH
date: Presented to the CDC R User Group on January 29, 2015
css: css/custom.css
autosize: true

Overview
========================================================
- Routine reporting
- Data validation in passive surveillance systems (i.e., synchronizing with partners)
- An R toolkit to (mostly) automate this process
- Further steps


Introduction: Routine Reporting
========================================================
- For any given health condition, the surveillance data that we collect are often reported by regional, state, and local public health authorities 
- Scarcity of electronic systems providing synchronized data between regional/state/local and national partners necesitates routine data validation to ensure both submitting and receiving partners have the same information

Data Validation
========================================================
- Often a manual process whereby surveillance data submitted by partners is copied into spreadsheets and sent back to partners by email
- These manual data checks may be
  - Labor intensive
  - Error prone
  - Inefficient

Open source tools for (mostly) automated data validation
======================================================== 
type: section

Next slide
===
title: false
<small>
- The R programming language (R version 3.1.2 (2014-10-31) -- "Pumpkin Helmet")
- A database interface package, such as `RODBC` or `DBI`
- A basic understanding of [RMarkdown](http://rmarkdown.rstudio.com/)
- The function `knit2html()` from the `knitr` package (version 1.8)
- The function `htmlTable()` from the `Gmisc` package (version 0.6.7)
- The function `for()` from the `base` package

_Optional:_
- An [IDE](http://en.wikipedia.org/wiki/Integrated_development_environment) for convenient scripting 
([RStudio version 0.98.1062](http://www.rstudio.com/))
- Packages `dplyr` (0.3.0.2) and `stringr` (0.6.2) for data and text manipulation
- Basic knowledge of HTML and CSS
</small>


knitr
======================================================== 

```r
library(knitr)
formals(knit2html)[1:2]
```

```
$input


$output
NULL
```


Row highlighting syntax
========================================================

Empty

An example of automation: NTPFS yearly closeout
======================================================== 
- NTPFS = National Typhoid and Paratyphoid Fever Surveillance system
- [Enhanced surveillance form](http://www.cdc.gov/nationalsurveillance/PDFs/typhi-surveillance-form.pdf)
- All 50 states + DC report
- Generate two data tables:
  1. All received report forms for calendar year
  2. All isolate data corresponding to Typhi or Paratyphi case patients (NARMS)
- Abbreviated variable set to keep it simple

Acknowledgements
===
- The CSS file that formatted my NTPFS reports is a modified version of "markdown7.html"
from [jasonm23's markdown-css-themes repository](https://github.com/jasonm23/markdown-css-themes)
- I learned a good bit about "knitting by hand" from [Jenny Bryan](http://www.stat.ubc.ca/~jenny/STAT545A/topic10_tablesCSS.html#my-table-looks-better-than-yours)

