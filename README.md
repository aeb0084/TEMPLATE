# TITLE
## RUNNING TITLE
 
 AUTHORS

This repository holds all supplemental files for "XX".

## Abstract: 
> ""

### Quick Key to File Directory: Detailed descriptions of file use can be found below.
Analysis and File Names| Brief Description | File Download
-------------------------------------|------------------------------------ | -----------------------------------------------------
CATEGORY TITLE                   
FILE NAME                   | DESCRIPTION                  | [FILE TITLE](FILE_LINK)
&nbsp; (THIS WILL GIVE EMPTY CELL, REMOVE IF NOT NEEDED)


## Project Summary: 
> 

## Supplementary Materials: 


Image of phylogenetic tree produced from the [Dendrogram for Phylogeny](amniota_2.txt). This image was used to create plot3ID CSV file and produce Figure 1 in BioRender.

<img src="Amniota_tree.jpeg" width="600">

<img src="Table_S1.jpg" width="1200">

<img src="Table_S2.jpg" width="1200">


## Example Code:

EXAMPLE: The statistical analyses were performed in R (version 4.0.3) using the code file titled [Quantitative Analysis R Code](CrossSpecGraph_Final.Rmd) in an R Markdown format. The code output displays all statistical models, results, and figures produced in either [PDF](CrossSpecGraph_Final.pdf) or [HTML](CrossSpecGraph_Final.html) format. Note, you will have to download the HTML file to visualize the data output. 

Examples of required packages, statistical models, and plots used can be seen below. Note: These are generalized examples produced for ease of adaptation.  Files containing RNAseq Analysis [code](q.down_trim_map_Carnivora.sh), Parsing Counts and merging metadata [code](MergingCounts_toMetadata_2021-06-10.R), and all Statistical Analysis/Visualization [code](CrossSpecGraph_Final.Rmd) contains the specific models used for publication.

```ruby
#Required Packages
library(tidyverse)
library(viridis)
library(Rmisc)
library(ggplot2)
library(nlme)
library(arsenal)
library(janitor)
library(ggforce)
library(ggalt)
library(dplyr)
library(ggalt)
library(ggforce)

#Linear Mixed Models
#Run linear model comparing variable of interest across time, including Content as a random effect variable to account for triplicate replication in qPCR runs.
model=(lme(Dependent_Variable~Independent_Variable, data=dat, na.action=na.omit, random=~1|Content))
#Run an anova output to display F-values and P-values
anova(model)
#Run summary output to obtain Estimates, Confidence Intervals and p-values
summary(model)


#Graph patterns using ggplot2 package
plot=ggplot(data=dat, aes(x=Independent_Variable, y=Dependent_Variable, fill=GeneTarger)) + geom_violin(trim=F, position=dodge, scale="width") + 
 geom_boxplot(width=0.15, position= dodge, outlier.shape = NA, color="black") +
 geom_point(data = Independent_Variable, size =2, shape = 19, color="black", position=position_dodge(width=0.6)) +
 geom_point(position=position_jitterdodge(jitter.width = 0.05, dodge.width = 0.6), size=1, alpha=0.5, aes(group= GeneTarget),   color="white") + 
    theme_bw() +
  xlab('x_IndependentVariable_Title') +
  ylab('y_DependentVariable_Title')
```



