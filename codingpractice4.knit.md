---
title: "codingpractice4"
author: "Erica Maul"
date: "2025-02-26"
output:
  pdf_document:
    toc: true
  md_document:
    variant: gfm
    toc: true
  word_document:
  html_document:
    toc: true
---
[link to souce publication](https://doi.org/10.1094/PDIS-06-21-1253-RE)

# Question 1. Explain the following:

## YAML header

The YAML header begins every R Markdown document. It includes title, author, date, and also details on how the document will be knit (html, pdf, etc.)

## Literate programming

Literate programming is a type of programming documentation that includes explanatory chunks of natural language as well as code. R Markdown files are an example of literate programming.

# Question 2. Take the code you wrote for coding challenge 3 question 5 and incorporate it into your R markdown file. Your final R markdown file should have the following elements.

- At the top of the document, make a clickable link to the manuscript where these data are published. 
- Read the data using a relative file path with na.strings option set to "na". This means you need to put the Mycotoxin.csv file we have used for the past two weeks into your directory, which git tracks.
- Make a separate code chunk for the figures plotting the DON data, 15ADON, and seedmass, and one for the three combined using ggarrange().



## DON plot

```r
DONplot.stats <- DONplot +
  geom_pwc(aes(group = Treatment), method = "t.test", label = "p.adj.format")
DONplot.stats
```

![](codingpractice4_files/figure-latex/unnamed-chunk-1-1.pdf)<!-- --> 

## X15ADON plot

```r
X15ADONplot.stats <- X15ADONplot +
  geom_pwc(aes(group=Treatment), method = "t.test", label = "p.adj.format")
X15ADONplot.stats
```

![](codingpractice4_files/figure-latex/unnamed-chunk-2-1.pdf)<!-- --> 

## seed mass plot

```r
seedmassplot.stats <- seedmassplot +
  geom_pwc(aes(group=Treatment), method = "t.test", label = "p.adj.format")
seedmassplot.stats
```

![](codingpractice4_files/figure-latex/unnamed-chunk-3-1.pdf)<!-- --> 

## combined plot

```r
combinedfigure.stats <- ggarrange(DONplot.stats, X15ADONplot.stats, seedmassplot.stats, labels = "AUTO", nrow = 1, ncol = 3, common.legend = T)
combinedfigure.stats
```

![](codingpractice4_files/figure-latex/unnamed-chunk-4-1.pdf)<!-- --> 



