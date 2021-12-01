---
title: 'text2sdg: An open-source solution to monitoring sustainable development goals from text'
tags:
  - R
  - Sustainable Development Goals
  - NLP
authors:
  - name: Dominik S. Meier
    orcid: 0000-0003-0872-7098
    affiliation: 1
  - name: Dirk U. Wulff
    orcid: 0000-0003-0872-7098
    affiliation: "1, 2"
  - name: Rui Mata
    orcid: 0000-0003-0872-7098
    affiliation: "1, 2"
affiliations:
 - name: University of Basel
   index: 1
 - name: Max Planck Institute for Human Development
   index: 2
date: 13 August 2017
bibliography: paper.bib
---



# Summary

Monitoring progress on the United Nations Sustainable Development Goals (SDGs) is important for both academic and non-academic organizations. Existing approaches to monitoring SDGs have focused on specific data types, namely, publications listed in proprietary research databases. We present the `text2sdg` R package, a user-friendly, open-source package that detects SDGs in any kind of text data using several different query systems from any text source. The text2sdg package thereby facilitates the monitoring of SDGs for a wide array of text sources and provides a much-needed basis for validating and improving extant methods to detect SDGs from text.

# Statement of need


The United Nations’ Sustainable Development Goals (SDGs) have become an important guideline for both governmental and non-governmental organizations to monitor and plan their contributions to social, economic, and environmental transformations. As the latest UN report [@SGD_report2021] attests, progress is still needed and the availability of high-quality data will be critical to identify areas requiring most attention moving forward. One promising way to monitor progress on SDGs is to screen the increasing amount of digitally available text using automatized, natural language processing methods. This approach has taken hold, for example, in scientometric efforts that monitor the SDGs in academic publications (e.g., Jayabalasingham et al., 2021). These efforts have so far been spearheaded by for-profit organizations with methodologies that are only partly publicly available and cannot be easily applied beyond academic publishing databases. In what follows, we describe some of these approaches and discuss their shortcomings before introducing our open-source solution, the `text2sdg` R package, which is designed to help monitor work on the sustainable development goals from any text source.

There are currently five leading approaches to monitoring SDGs from text. The most influential of these was developed by the Elsevier SDG Research Mapping Initiative and uses Lucene-like queries to map several features available from a proprietary database of scientific publications (i.e., Scopus; https://www.scopus.com) to map publications to SDGs [@Jayabalasingham]. The Elsevier system is able to detect millions of SDG-related publications and is used by the Times Higher Education Impact Rankings to rank over 1000 universities worldwide according to their SDG-related research output. Elsevier recently partnered with Aurora, a network of universities that had independently developed a query system to detect SDGs in publications [@aurora]. Other extant query systems include those of SDG ontology [@Bautista2019], Siris [@duran_silva_nicolau_2019_3567769], and the Sustainable Development Solutions Network [@sdsn]. Despite the effort put into developing these systems, they are not without shortcomings. First, they are not directly applicable to text sources other than academic citation databases (e.g., Scopus). Second, the systems lack user-friendly and transparent ways to communicate which features are matched to which documents or how they compare between a choice of query systems.

We alleviate these shortcomings by providing an open-source solution, `text2sdg`, that lets users detect SDGs in any kind of text using any of the above-mentioned systems or, even, customized, user-made query systems. The package provides a common framework to implement the different extant approaches and makes it easy to quantitatively compare and visualize their results. We showcase its potential with an analysis of a publicly available database of research projects funded by the Swiss National Science Foundation (https://p3.snf.ch).

![Analysis of 26,811 research projects funded by the Swiss National Science Foundation using the different query and keyword systems available in `text2sdg`. Panel A illustrates the identification of SDGs based on a query search: The example shows an excerpt of one abstract with some terms highlighted that match a query of the Aurora query system indicating SDG-14 (i.e., conserve and sustainably use the oceans, seas and marine resources for sustainable development). Panel B shows the number of hits per document for the different systems made available in `text2sdg`, which reveals striking differences in numbers of hits. Panel C shows the relative number of hits per SDG cumulatively across systems. Panel D shows the correlations between query systems, which reveal overall small to medium levels of correspondence between them. Panel E shows the correlation between detected SDGs over all query systems.\label{example}](paper_figure_2.pdf) 

Figure \ref{example} shows a search example and a number of results for this database comparing the different search systems available (i.e., Aurora, SIRIS, Elsevier, SSDN, Ontology). We highlight only three main results here. First and foremost, the results show it is possible to systematically map SDGs to text from sources other than citation databases. Second, as can be seen in panels B-D, the results suggest important and sizable differences between query systems in both the number of hits and the profiles of most researched SDGs, suggesting it is important to question the results from any single approach. Third, the results suggest that the SDGs vary considerably in their overlap (panel E), emphasizing the promise and challenges of tackling different SDGs simultaneously.


# Features

The `detect_sdg()` function identifies SDGs in texts that are provided via the `text` argument. By default, the three query systems Aurora, Elsevier, and SIRIS are used and queries for all SDGs are run. Other query systems can be specified with the `system` argument and a subset of SDGs to be detected can be specified with the `sdgs` argument. With the `crosstab_sdg` function, users can extract either correlations between systems (Figure \ref{example} D) or between SDGs (Figure \ref{example} E). `text2sdg` also allows users to run user specified query systems with the `detect_any` function and provides the `plot_sdg` function to plot the results (Figure \ref{example} C), see the package vignette (https://cran.r-project.org/web/packages/text2sdg/vignettes/text2sdg.html) for more details. 





# References



