# RMarkdown Template for IEEE Access Articles

## Introduction

This is an RMarkdown template for working on papers using the IEEE Access format, based on the LaTeX template available for download [here](https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/authoring-tools-and-templates/ieee-article-templates/templates-for-ieee-access/). This is not a detailed review of the IEEE Access template, nor the guidelines on how to write papers that comply with the required formatting and structure of this journal. You can find some details on how to prepare papers for this journal [here](https://www.sharelatex.com/templates/5a761d0d47ce0af37e1c6035/v/0/pdf?inline=true&name=IEEE%20Access%20template).

Instead, I focused on describing the small changes I added to be able to generate PDF documents with the corresponding general formatting of this journal using RMarkdown.

## Description

I have used the RMarkdown template for IEEE Trans articles, included in the `rticles` package. The general styling of the document is provided in the `ieeeaccess.cls` file, a \LaTeX class file provided by the journal.

All the files are contained in a R project (RStudio). The file structure of the project is:

* The `images` folder contains all the images and figures used to produce this paper. 
* The \LaTeX templates and classes are stored in the `latex` folder. Bear in mind that the files `template.tex` and `ieeeaccess.cls` are the ones used to structure the paper in the corresponding formatting, so they should not be changed.
* The `bib` folder contains the bibliography files, including the Citation Style file (.csl) to show the references in the corresponding format. This file can be found [here](https://paperpile.com/s/ieee-access-citation-style/).

The template uses three images (bullet.png, Logo.png, notaglineLogo.png) that have been place in the `images` sub-directory. The `ieeeaccess.cls` file has been modified to be able to access these images in the corresponding folder. This is the only change added to the orignal class file. 

### Authors, affiliations and footnotes

First, I adjusted the "authors" section, to be able to translate the info from the YAML into a comma-separated list of authors, in the order they have been provided. A reference mark for each author is added, related to the affiliations/institutions and e-mails corresponding to each author. I also added the key *membership* to be shown in this section.

Some other changes in the YAML are the key *corresp*, related to the author to whom proofs of the paper will be sent, and also the key *footnote* , to contain information regarding the support, sponsorship and financial aid for the research project.

### Biographies 

The last section of the paper is destined to the biographies of the authors. For such purpose, a `bios.tex` template has been created. This template will be included after the body and should be modified to include the actual information of the authors. 

### Tables and images

You can create your tables from your own data using any of the available r packages of your choice (find some [here](https://rmarkdown.rstudio.com/lesson-7.html)). There will be conflicts between the `longtable` environment and the two-column format of this paper, so I have opted for not using longtables in any case. Also, I prefer to inlcude my tables using LaTeX directly, so I can have more control over aspects like borders, column size, cell spacing and alignment, line breaks, ect. That way, I don't have to edit again the TEX file after the generation. 

## Recommendations

When using this template, is important to bear in mind that some information will have to be modified directly in the TEX file generated when *knitting* to a PDF (see `keep_tex = true` in YAML). That will be the case for:

* Date of publication and DOI shown above the title in the first page, that can be found as `\history{}` and `\doi{}` in the .tex file. This information would not be available while working on a paper, so it can be left blank in the first place.
* Author and title in header, that can be found under `\markboth` tag in .tex file. 
* Volume and year in footer, hard-coded to the .cls file. The have not been modified since I tried to keep the changes to the class file to the bare-minimum.


## Contribute

I am still working on this template so feel free to drop any suggestions you might have to help me improve it.
