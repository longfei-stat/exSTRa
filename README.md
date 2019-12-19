[![Build Status](https://travis-ci.org/bahlolab/exSTRa.svg?branch=master)](https://travis-ci.org/bahlolab/exSTRa)
[![Coverage status](https://codecov.io/gh/bahlolab/exSTRa/branch/master/graph/badge.svg)](https://codecov.io/github/bahlolab/exSTRa?branch=master)

# exSTRa
expanded STR algorithm: detecting expansions with paired-end Illumina sequencing data. 

This depends on the Perl package 
[Bio::STR::exSTRa](https://github.com/bahlolab/Bio-STR-exSTRa) 
for processing of BAM files. 

# Installation

For easy installation, run from within R:
```
  # install.packages("devtools") # if devtools is not already installed
  devtools::install_github("bahlolab/exSTRa")
```
  

# Using exSTRa
At present, the pipeline requires:
- Paired-end Illumina sequencing. Has been tested with some whole-exome sequencing, and whole-genome sequencing with and without PCR in the library preparation step. (Testing on single-end data has not occured, but we presume it would perform poorly due to the affect on alignment.)
- Alignment with bowtie2 in local mode is recommended. (Works for most other aligners and settings, however this has not been tested extensively.)
- Sorting 
- PCR duplicate marking (recommended)

A database of repeats is required:
- known repeat expansion disorder loci databases are included in the `inst/extdata` directory. Files are available for [hg19](https://github.com/bahlolab/exSTRa/blob/master/inst/extdata/repeat_expansion_disorders_hg19.txt), [GRCh37](https://github.com/bahlolab/exSTRa/blob/master/inst/extdata/repeat_expansion_disorders_grch37.txt), [hg38](https://github.com/bahlolab/exSTRa/blob/master/inst/extdata/repeat_expansion_disorders_hg38.txt), [GRCh38](https://github.com/bahlolab/exSTRa/blob/master/inst/extdata/repeat_expansion_disorders_grch38.txt).
- genome wide STR databases based on the UCSC simple repeats track is available to [download from FigShare](https://figshare.com/s/bb1e6358781bb3ca12c2). (An example script to generate this database of all STRs genome wide, or those in genes that are expressed in the brain, is provide in `inst/tools/prepare_exSTRa_input_db.R`.)

Use the Perl scripts and modules from https://github.com/bahlolab/Bio-STR-exSTRa to analyse reads in BAM files. This generates STR counts. 
In the future this functionality may be included within the R exSTRa package. 

This R package provides an OO S3 interface. 
Currently makes extensive use of the data.table package, and understanding its use may help with this package. 

# Examples

Please see the exSTRa vignette for a workable example; 
this can be viewed in R after installation of the package with
```
vignette("exSTRa")
```
or can be downloaded in the repository from [doc/exSTRa.html](https://bahlolab.github.io/exSTRa/doc/exSTRa.html).
 
Other datasets in BAM/CRAM format can be analysed in a similar way after processing with the Perl 
[Bio::STR::exSTRa](https://github.com/bahlolab/Bio-STR-exSTRa) package. 

# Citation

Rick M. Tankard,
Mark F. Bennett,
Peter Degorski,
Martin B. Delatycki,
Paul J. Lockhart,
Melanie Bahlo.
        **Detecting Expansions of Tandem Repeats in Cohorts Sequenced with Short-Read Sequencing Data**. 
        *American Journal of Human Genetics*,
        103(6):858-873, 2018.
        https://doi.org/10.1016/j.ajhg.2018.10.015
        
Licenced under [GPL-2](LICENCE).