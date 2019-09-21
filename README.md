# Antigen receptor gene profiler (ARGP)

ARGP is a software framework that provides analytics services on NGS Data, implemented in [R Shiny](https://shiny.rstudio.com/).

## Installation

#### R Shiny packages

```
install.packages(c("shiny","shinyFiles", "shinyjs", "shinyBS"))
```

#### Other packages for data processing and visualization

```
install.packages(c("DT","plyr","dplyr","pryr","data.table","stringr","tidyr","xtable","plot3D","gridExtra","stringdist","plotly"))
source("http://bioconductor.org/biocLite.R")
biocLite("Biostrings")
source("https://bioconductor.org/biocLite.R") 
biocLite("motifStack")
```

##  Run the Application

- You can run the application by pressing the **"Run App"** button, from either **ui.R** or **server.R** script.
- The Datasets you want to process together must be contained into a folder organised into sub-folders. The Data folder contains some sample datasets.

You may find a detailed documentation of the ARGP tool at [Wiki](https://github.com/mariakotouza/ARGP-Tool/wiki/Antigen-receptor-gene-profiler-(ARGP)). 

##  Run ARGP as an R script-based tool 
There are two ways to run the script-based tool:
- Through R Studio: run the **make_options.R** file, after first changing/editing the default values for the parameters that are in the **option_list** in the file. The working directory should be the path where the file **make_options.R** is.
- Through the command line: run the command **Rscript --vanilla make_options.R** followed by a list of the parameters you need to change from the default values. For example, in order to run only the 1st & 2nd pipeline choice, the command should look like this:

```
Rscript --vanilla make_options.R --pipeline 1,2 
```

To run a pipeline that computed the highly similar clonotypes, the user should insert the number of mismatches by setting the --highly_sim_params option, using dashes and spaces as follows:

"6-1 7-1 8-1 9-2 12-2,1,Yes"   (i.e. for cdr3 length = 6 - number of mismatches = 1, for cdr3 length = 7 - number of mismatches = 1, etc. ) 

In this case, the command should look like this:

```
Rscript --vanilla make_options.R --pipeline 1,2,3 --highly_sim_params 6-1 7-1 8-1 9-2 12-2,1,Yes
```

All the available and the deafault parameters are available in the **make_options.R** files. The user can ask for help using the following command:
```
Rscript --vanilla make_options.R --help
```

##  Run ARGP as a Docker container
The docker image of ARGP is available throught https://cloud.docker.com/u/mariakotouza/repository/docker/mariakotouza/argp.

##  License
This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. To view a copy of this license, visit https://creativecommons.org/licenses/by-nc-sa/4.0/.