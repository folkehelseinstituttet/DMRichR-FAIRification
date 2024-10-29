# FAIRification of DMRichR Pipeline: Advancing Epigenetic Research on Environmental and Evolutionary Model Organisms

![Flowchart showing the process of adapting DMRichR for a new organism with an annotated genome](https://github.com/wassimsalam01/DMRichR-FAIRification/blob/main/img/DMRichR%20Diagram.png)

**Figure 1.** Steps required to adapt DMRichR to a new organism with an annotated genome. *Yellow:* User input files (methylation calls) resulting from Whole-Genome Bisulfite Sequencing (WGBS) experiment; *Light-orange:* User input files with information on the reference genome; *Dark-orange:* Intermediary tools for producing input files; *Green:* Newly-computed species-specific packages; *Blue:* Modified versions of DMRichR and additional packages used within it; *Grey:* Results generated by DMRichR, which include Blocks, Differentially Methylated Regions (DMRs), Smoothed Individual Methylation Values, Heatmaps.

## Abstract

Bioinformatics tools often prioritize humans or human-related model organisms, overlooking the requirements of environmentally relevant species, which limits their use in ecological research. This gap is particularly challenging when implementing existing software, as inadequate documentation can delay the innovative use of environmental models, for modern risk assessment of chemicals that can cause aberration in methylation patterns. The establishment of fairness in ecological and evolutionary studies is already constrained by more limited resources in these fields of study, and an additional imbalance in tool availability further hinders comprehensive ecological research.

To address these gaps, we adapted the DMRichR package, a tool for epigenetic analysis, for use with custom, non-model genomes. As an example we here use the crustacean _Daphnia_, a keystone grazer in aquatic ecosystems. This adaptation involved the modification of specific code, computing three new species-specific packages (BSgenome, TxDb, and org.db), and computing a CpG islands track using the makeCGI package. Additional adjustments to the DMRichR package were also necessary to ensure proper functionality. The developed workflow shown in Fig. 1 can now be applied not only to different _Daphnia_ species that were previously unsupported, but also to any other species for which an annotated reference genome is available.

## How To Use Repository

### [R Scripts](https://github.com/wassimsalam01/DMRichR-FAIRification/tree/main/r-scripts)

The code used to compute the necessary packages and input files used in the case study is provided here for transparency. The code in [computeDatabases.R](https://github.com/wassimsalam01/DMRichR-FAIRification/blob/main/r-scripts/computeDatabases.R) shows in a first step how the BSgenome, TxDb and org.db packages for _Daphnia pulex_ were computed. When adapting the code to a different species, adjust the code and seed file accordingly depending on the resources available for given species.

Successful installation of the BSgenome package is a prerequisite to computing the CpG Islands track in a second step in [makeCGI.R](https://github.com/wassimsalam01/DMRichR-FAIRification/blob/main/r-scripts/makeCGI.R). Runtime may vary greatly depending on your genome size.

### [Case Study](https://github.com/wassimsalam01/DMRichR-FAIRification/tree/main/case-study)

The directory contains all files needed to execute the run for the case study. Simply follow the instructions listed in [DMRichR-Testing.R](https://github.com/wassimsalam01/DMRichR-FAIRification/blob/main/case-study/DMRichR-Testing.R). Important is to not skip the step of reloading the R session after installing all the custom packages, as this may cause the user to encouter some errors. Adapt your code accordingly to your sample data and genome. Fig. 2 below displays one of many DMRs obtained by this case study run, which successfully demonstrates the FAIRification of the DMRichR pipeline.

![DMR Plot](https://github.com/wassimsalam01/DMRichR-FAIRification/blob/main/img/DMR%20Plot.PNG)

**Figure 2.** DMR plot displaying a DMR consisting of 13 CpGs with 23% hypomethylation in young samples compared to old samples. The methylation level of each CpG site in an individual sample is shown as a point, with its size directly proportional to its coverage. Smoothed methylation levels are represented by lines, color-coded as blue for control samples (old) and red for experimental samples. A track of CpG and gene annotations are additionally displayed under the plot, retrieved from the computed CGI track and org.db package respectively.

## Utility of Custom BSgenome, TxDb, and org.db Packages

## [Citations](https://github.com/wassimsalam01/DMRichR-FAIRification/blob/main/CITATIONS.md)

