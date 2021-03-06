---
title: "PAPi (Pangenome Analysis Pipeline) v1.0.0"
author: "Michał Kamiński"
output:
  word_document: default
  pdf_document: default
---
## DESCRIPTION
The analysis is designed to calculate core-pangenome for defined dataset of given protein sequences.
At the moment PAPi in not self-sufficient and require some user effort.
User should provide __.faa__ files with appropriately formatted fasta headers and file names:

Fasta header must contain protein ID and genome name separated by underscore sign

Please name your genome files according to this template:

 * __Genus_species_strain.faa__ eg. _Sphingopyxis_lindanitolerans_WS5A3p.faa_
 * __Genus_sp.\_strain.faa__ eg. _Sphingopyxis_sp.\_A083.faa_

## PREPROCESS .FAA FILES

1. Run "pre_papi.sh test" command to check if preprocessing step works correctly
2. Run "pre_papi.sh user _your/input/dir_ _your/output/dir_"
- __your input directory should contain only .faa files__
3. __IMPORTANT__ When script is completed please run __CD-HIT__ program with your own parameters and provide the .clstr file as an input for further analyses 


## RUN PAPi

From this point PAPi will do the analysis for you.

1. Ensure that you have _gnames_file.csv_ in PAPi directory (automatically generated
by pre_papi). If you didn't use pre_papi please create .csv file listing genomes in one column, one genome per row like this:
```{r gnames_file demo, echo=FALSE, message=FALSE}
df <- readr::read_delim(
  file = "gnames_file.csv",
  delim = ",",
  col_names = FALSE, )
head(df)
```

2. run ./papi.sh test to run the analysis on test data (sample from my publication dataset)

* If the analysis is completed with success you will see 4 plots in PAPi/plots directory

3. Run PAPi with your data and have fun :)

If you found this code usefull please cite this repository and/or this paper: 
Kaminski, M.A.; Sobczak, A.; Dziembowski, A.; Lipinski, L. Genomic Analysis of γ-Hexachlorocyclohexane-Degrading Sphingopyxis lindanitolerans WS5A3p Strain in the Context of the Pangenome of Sphingopyxis. Genes 2019, 10, 688.

Thanks!
