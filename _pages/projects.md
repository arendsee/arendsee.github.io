---
layout: single
title: "Projects"
permalink: /projects/
comments: true
author_profile: true
---


## Morloc

[morloc](http://www.morloc.io) is a functional programming language where
functions are imported from foreign languages and unified through a common type
system. The compiler generates the code needed to compose functions across
languages and also to direct automation of mundane tasks such as data
validation, type/format conversions, data caching, distributed computing, and
file reading/writing. The ultimate goal is to develop `morloc` into a query
language that returns optimized programs from an infinite "library" of
functions and compositions of functions.


Import many implementations for a function from any supported language:
<img src="{{site.baseurl}}/assets/img/morloc-1.png" style="display:block;margin-left:auto;margin-right:auto;">

Declare one common type signature that describes many implementation-specific ones
<img src="{{site.baseurl}}/assets/img/morloc-2.png" style="display:block;margin-left:auto;margin-right:auto;">

Specify new programs by composing these general functions
<img src="{{site.baseurl}}/assets/img/morloc-3.png" style="display:block;margin-left:auto;margin-right:auto;">

Build executables and let the compiler optimize the choice of implementations
<img src="{{site.baseurl}}/assets/img/morloc-4.png" style="display:block;margin-left:auto;margin-right:auto;">

## Haskell projects

 * [lsystems](https://github.com/arendsee/lsystems) an experimental package for
   specifying and generating deterministic or stochastic L-systems graphics.

<img src="{{site.baseurl}}/assets/img/lsystems.png" style="display:block;margin-left:auto;margin-right:auto;">

 * [lsystems](https://github.com/arendsee/tessellate) an experimental
   semi-regular tesselation package with aspirations of growing up to be
   something different. 

<img src="{{site.baseurl}}/assets/img/tessellate.png" width=400 style="display:block;margin-left:auto;margin-right:auto;">

## Python packages on PyPi

 * [pgraphdb](https://github.com/arendsee/pgraphdb) is a Python library and CLI
   tool for interacting with a GraphDB database. It allows uploading of RDF
   data, submission of SPARQL queries, deletion of triples specified in RDF
   files, etc.

 * [octofludb](https://github.com/flu-crew/octofludb) is a specialized tool for
   parsing the data used in our swine influenza surveillance program into
   triple format and uploading it to a GraphDB database. It allows access to
   the data through SPARQL queries and can return FASTA file sequence.

<img src="{{site.baseurl}}/assets/img/octofludb.png" width=400 style="display:block;margin-left:auto;margin-right:auto;">

 * [flutile](https://github.com/flu-crew/flutile) is a specialized suite of
   tools designed for the flu-crew at
   [USDA-ARS](https://www.ars.usda.gov/midwest-area/ames/nadc/#) and
   collaborators. The foundational feature is handling for indexing amino acid
   positions relative to references for each influenza A subtype. This allows
   sequences to be compared across studies.

<img src="{{site.baseurl}}/assets/img/flutile.png" width=400 style="display:block;margin-left:auto;margin-right:auto;">

 * [smot](https://github.com/flu-crew/smot) is a python package and CLI tool
   for general purpose phylogenetic tree sub-sampling, annotation, and
   summarization.

![smot]({{site.baseurl}}/assets/img/smot.png)

 * [smof](https://github.com/incertae-sedis/smof) is a CLI tool for working
   with FASTA files.

<img src="{{site.baseurl}}/assets/img/smof1.png" style="display:block;margin-left:auto;margin-right:auto;">

 * [regref](https://github.com/arendsee/regref) offers regular expression based
   search and replace using pattern and replacement expressions from a table.


## R CRAN/rOpenSci packages

 * [rmonad](https://github.com/arendsee/rmonad) an experimental monadic
   pipeline tool for building branching workflows, storing select intermediate
   data, automatic benchmarking, and storing of any raised error messages or
   warnings.

<img src="{{site.baseurl}}/assets/img/rmonad1.png" width="40%">
<img src="{{site.baseurl}}/assets/img/rmonad2.png" width="50%">

 * [rhmmer](https://github.com/arendsee/rhmmer) a wrapper around the
   bioinformatics package HMMER.

 * [onekp](https://github.com/ropensci/onekp) scrape plant transcritomic data
   from the 1KP project website, select the species or clades or interest, and
   automatically download them.


## Other

 * [Language Of Dice](https://github.com/arendsee/language-of-dice) was my
   first attempt at developing a programming language. The goal was to develop
   a language for specifying discrete probability problems (dice problems) that
   was sufficiently advanced to model outcomes of encounters in D&D. For
   example, what is the probability that my group of 3 level-2 fighters will
   beat the Kraken. All possible attacks, buffs, debuffs, etc would have to be
   modeled. The project currently consists only of loose specification of
   syntax, grammar, and a rudimentary lexer and parser.


## R Shiny apps

[octoflushow](https://github.com/flu-crew/octofludb) (private) imports data
generated by `octofludb` and produces interactive visuals and tables for
subsetting/downloading data.

![octoflushow-barchart]({{site.baseurl}}/assets/img/octoflushow-barchart.png)

[metaoku](https://github.com/arendsee/metaoku)
([app](https://metaoku.shinyapps.io/archive/)) was my grand vision for a means
of sharing and visualizing data organized into normal folders. The project is
described in my dissertation appendix. The project is basically dead now, but
it seemed my approach to automatically visualizing data and my simlple data
type-system are worth returning to at some point.

[Orphan survey](https://github.com/arendsee/orphan-survey)
([app](http://arendsee.shinyapps.io/orphan-survey)) is a Shiny visualization
program for an unpublished orphan gene study I ran in grad school. Nothing come
of it ultimately.

![orphan]({{site.baseurl}}/assets/img/orphan-survey.png)

[dnd](https://github.com/arendsee/dnd)
([app](http://arendsee.shinyapps.io/dnd-rolls)) is a rudimentary dice
probability app. Someday, when I feel sufficiently motivated, I'll come back to
it and expand the functionallity. Dice probability gets interesting when you
start adding in advantage/disadvantage and other D&D shenanigans.

![dnd]({{site.baseurl}}/assets/img/dnd.png)

[Small population survival](https://github.com/arendsee/interstellar)
([app](http://arendsee.shinyapps.io/interstellar)) was a visualization app for
a class project concerning how long a colony on a generation ship would survive
before the proportion of females reched 0 or 1 and natural reproduction became
impossible.

![interstellar]({{site.baseurl}}/assets/img/interstellar.png)


## Genomics and orphan-gene sleuthing from grad-school

 * [synder](https://github.com/arendsee/synder) is a high-performance program
   that maps genomic loci from one species to another using a synteny map. The
   core algorithm is written in C++ and wrapped in R.

<img src="{{site.baseurl}}/assets/img/synder.png" width="75%" style="display:block;margin-left:auto;margin-right:auto;">

 * [phylostratr](https://github.com/arendsee/phylostratr) an R pipeline for conventional phylostratigraphy.

<img src="{{site.baseurl}}/assets/img/phylostratr.png" width="75%" style="display:block;margin-left:auto;margin-right:auto;">

 * [fagin](https://github.com/arendsee/fagin) an R pipline based on `synder`
   and `rmonad` for inferring the origins of genes.

<img src="{{site.baseurl}}/assets/img/fagin.png" width="75%" style="display:block;margin-left:auto;margin-right:auto;">
