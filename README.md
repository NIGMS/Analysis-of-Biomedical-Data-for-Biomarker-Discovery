![RIINBRE-Logo](images/RIINBRE-Logo.jpg)


---


# Analysis of Biomedical Data for Biomarker Discovery
## Dr. Christopher L. Hemme
## Director, [RI-INBRE Molecular Informatics Core](https://web.uri.edu/riinbre/mic/)
## The University of Rhode Island College of Pharmacy
Last Updated: March 17, 2022


---


Welcome to the cloud-based learning module **Analysis of Biomedical Data for Biomarker Discovery** presented by the [Rhode Island INBRE Molecular Informatics Core (MIC)](https://web.uri.edu/riinbre/mic/) at the University of Rhode Island.  The module was developed by Dr. Christopher L. Hemme, Director of the MIC using data from Dr. Nisanne Ghonem at the Department of Biomedical and Pharmaceutical Sciences, College of Pharmacy, University of Rhode Island.  Our goal with this module is to bridge the gap between bioinformaticians (particularly those from a non-clinical background) and clinicians or clincal researchers who often view the same biomedical data in very different ways.  For example, bioinformaticians may not be familiar with the conventions for data presentation and visualization in the clinical literature, while clinicians are often overwhelmed by the volumes of data generated by modern bioinformatics methods or may question the utility of the results of bioinformatics analyses compared to more traditional clinical methods.  We present this challenge in terms of clinical biomarker discovery, that is, biological measures of health and disease.  For the clinician, a biomarker must be cheap and easy to measure, accurate, and easily interpretable for both the clinician and the patient.  A bioinformatician, on the other hand, is often looking at biomarkers on a global scale, trying to identify multiple correlated biomarkers that may or may not be obvious clinical targets.  Understanding the basic principles behind biomarker discovery and analysis will help these two groups better communicate when it comes time for data analysis and publication.

This module will cost about $1.00 to run, assuming you shut down and delete all resources when you are finished.

Watch this [Introduction Video](https://youtu.be/THy_d33Ih6M) to learn more about the module.


## Overview of Page Contents


+ [Getting Started](#getting-started)
+ [Overview](#overview)
+ [Software Requirements](#software-requirements)
+ [Installing the Module](#installing-the-module)
+ [Workflow](#workflow)
+ [Data](#data)
+ [Troubleshooting](#troubleshooting)
+ [Funding](#funding)


The data used in this module is stored in a Google Cloud bucket and does require using `gsutil` commands to download the data sets.  R packages used will be downloaded from within each notebook.



## Getting Started

This learning module will introduce the user to basic concepts in biomarker discovery that the user is likely to encounter in the clinical and biomedical literature.  The   motivating factor behind the design of this module is that is to bridge the gap between how bioinformaticians and clinicians view biomarker data.  The bioinformatician typically takes a bird's eye view of the data, looking for global patterns that indicate statistically and biologically significant changes of state, whereas the clinician is motivated by more practical concerns such as cost, accuracy, specificity and clinical utility of potential biomarkers.  The field of biomarker discovery is complex and ever changing and it is not possible to cover every possible method and technique currently employed in clinical research.  As such, we will focus on common methods such as exploratory analysis (PCA, heatmaps, etc.), linear regression for comparison of biomarkers and analysis of omics data, logistic regression for binary classification schemes involving biomarkers, and machine learning for biomarker discovery.


## Overview

This repository contains files comprising a learning module covering concepts in biomarker discovery. The learning module consists of 9 submodules, with each submodule consisting of a Jupyter Notebook running the R programming language.  We assume the user has a basic knowledge of R and the R Bioconductor suite, but this is not required.  The submodules are organized as follows:

1. Introduction to Biomarkers
2. Introduction to R Data Structures (Optional)
3. Introduction to Linear Models (Optional)
4. Principles of Exploratory Analysis (Optional)
5. Rat Renal Ischaemia Reperfusion Injury Case Study
6. Linear and Logistic Regression for Comparison of Quantitative Biomarkers
7. Exploratory Analysis of Proteomics IRI Data
8. Identification of IRI Biomarkers from Proteomic Data
9. Machine Learning Methods for Biomarker Discovery

Submodules 2-4 cover optional background material for learners who need it and may be skipped for those who don't.


## Software Requirements

This module employs Jupyter Notebooks running R 4.2 using Bioconductor for bioinformatics data analysis and will employ tidy data principles implemented by the *tidyverse* package.  A basic knowledge of R is expected but not required for completing the module. Submodule 02 will review R data structures that will be particularly relevant in regression analysis.  Required R packages will be installed within each submodule.  The installation can take several minutes the first time the packages are installed.  Key packages used include *tidyverse* and BioConductor packages such as *limma* .  Prior understanding of these packages is not required to complete this module but users are encouraged to learn more about these packages prior to or following completion of this module to better understand the commands used.

Jupyter Notebooks are run through your browser and have the file extension *ipynb*.  Activate the notebook by double-clicking the file name and it will automatically open in your browser. Each notebook consists of markdown and code cells.  Markdown cells are for text and figures and are there to guide you through the chapters.  Code cells can be run by clicking the play arrow at the top of the screen or by hitting CTRL-ENTER.  The code will run within the notebook and generate the appropriate output.  You may freely change the code and re-run the block as often as you like.  This is useful if you want to test different analysis models or modify figures. 


## Installing the Module

The below steps guide you through setting up a virtual machine on Google Cloud Platform, downloading the module files, and launching the notebooks. You will need a Google account and access to a Google Cloud Platform Project.

Once you have these, you can begin by first navigating to https://console.cloud.google.com/ and logging in with your credentials. Use the following [instructions](https://github.com/STRIDES/NIHCloudLabGCP/blob/main/docs/open_GCP_project.md) to open a GCP project.


### Navigating to the Vertex AI Workbench

Once a project has been selected, navigate to the Vertex AI Workbench (either by scrolling through the left-hand navigation menu or by using the search bar).  From here you will build a virtual machine and launch the module notebooks.


### Creating a Virtual Machine

A virtual machine is exactly what it sounds like.  When creating a VM, we are allocating computing resources into a contained environment where we can perform whatever task we need to do.  In GCP, we can either create VM's manually through Compute Engine or we can create them automatically through other processes.  We will now create a new VM for our modules through Vertex AI.

Use the following [instructions](https://github.com/STRIDES/NIHCloudLabGCP/blob/main/docs/vertexai.md) to set up your VM in VertexAI.  Our notebooks include a notebook that uses R code, so make sure you are using the 'R' framework (R 4.2 at the time of this writing). You can then choose a name for your virtual machine (within GCP's naming rules) and preferably choose a server location closest to you. Ignore the advanced options for now, and a default virtual machine will be created. A default machine has 4 vCPUS and 15GB RAM.

Creating a machine may take a few minutes to finish.

![Workflow](images/R_notebook_setup.png)


### Starting Your Virtual Machine

Start your virtual machine by clicking __'OPEN JUPYTERLAB'__. This will automatically start your VM if it is not running (look for the green check mark).  You can also start the VM manually by clicking the start button.

Note, when you are finished running code, you should turn off your virtual machine to prevent unneeded billing or resource use by checking your notebook and pushing the 'STOP' button.


### Downloading Tutorial Files

Now that you have created your virtual machine, and are in the JupyterLab screen, you will need to download the module content.  The easiest way to do this is to clone the repository directly for the NIGMS Github. This can be done by opening a terminal in your JupyterLab environment (click the blue box with the white plus sign in the upper right corner and click the "Terminal" icon in the Launcher menu which comes up) and running the command `git clone https://github.com/NIGMS/BiomarkersURI`. 

This should download our repo, and the tutorial files inside, into a folder called 'BiomarkersURI'. Double click this folder now. Inside you will find all of the tutorial files, which you can double click and run.  You should also see a data file that contains the biomarker and proteomic data to be analyzed.


### Running Tutorial Files

All our tutorial workflows are Jupyter format. To run them you need only to double click the tutorial file you want.

This will open the Jupyter file in Jupyter notebook. From here you can run each section, or 'cell', of the code, one by one, by pushing the 'Play' button on the above menu or by hitting CTRL-ENTER (make sure your cursor is in the code block you want to run). Code blocks run in the order you click them, and a common source of errors is running code out of order (i.e. a code block requires another block of code to be run first).

Some 'cells' of code take longer for the computer to process than others. You will know a cell is running when a cell has an asterisk next to it \[\*\]. When the cell finishes running, that asterisk will be replaced with a number which represents the order that cell was run in.  In most cases, it takes only a few seconds for code to run, but some steps (such as package installation) may take several minutes.  If you try to run two or more code blocks at the same time, the code blocks will run sequentially in the order you executed them.

You can now explore the tutorials by running the code in each, from top to bottom. Look at the 'workflows' section below for a short description of each tutorial.

Jupyter is a powerful tool, with many useful features. For more information on how to use Jupyter, we recommend searching for Jupyter tutorials and literature online.


## Workflow


Below is the general workflow and GCP architecture of the module. We start by creating our experimental object (in our case, an R list data structure) from processed biomarker and proteomic data.  We then add metadata (i.e., data about the samples) and optional additional data (e.g. genome and annotation files, if we were using transcriptome data) appropriate to the experiment.  We can will save this object and reload it, add to it, and save it in subsequent notebooks.  It's important to run the notebooks in order to ensure that the experimental object is properly updated.  The next step will be analysis of known clinical biomarkers to each other using linear and logistic regression methods common in the clinical literature.  Once these methods are learned using known biomarkers, they can then be applied to newly discovered potential biomarkers. The next two notebooks will cover exploratory and differential analysis of proteomics data to identify new potential biomarkers.  We will look at how to normalize proteomics data, how batch effects can complicate data analysis and how to correct for them, and how to identify potential biomarkers by identifying proteins whose expression differs significantly between healthy and injured states. The final notebooks will cover background information on R data structures, the use of linear models in bioinformatics data analysis, principles of exploratory analysis, and how the methods covered in this module can be extended to machine learning methods for automated biomarker discovery.

![Workflow](images/uri_nosi_workflow.png)
![Architecture](images/URI_TID.png)

To summarize:

**Submodule 1: Introduction to Biomarkers** - Define what biomarkers are, identify the types of biomarkers, define properties of biomarkers that make them clinically useful, explore case studies of common clinical biomarkers.  
**Submodule 2: Introduction to R Data Structures** - (Optional).  
**Submodule 3: Introduction to Linear Models** - (Optional).  
**Submodule 4: Principles of Exploratory Analysis** - (Optional).  
**Submodule 5: Rat Renal Ischaemia Reperfusion Injury Case Study** - Introduce the mouse renal IRI model used in this module.  
**Submodule 6: Linear and Logistic Regression for Comparison of Quantitative Biomarkers** - Compare two known clinical biomarkers using linear regression to identify state changes, Compare two biomarkers using binary classification schemes using logistic regression, evaluate classification schemes using ROC curves.  
**Submodule 7: Exploratory Analysis of Proteomics IRI Data** - Normalize proteomics data for further analysis, identify and correct for batch effects in the data, explore trends in the data using dimensionality reduction methods such as principle components analysis, plot proteomics data using heatmaps.  
**Submodule 8: Identification of IRI Biomarkers from Proteomic Data** - Perform differential analysis on proteomic data to identify potential biomarkers indicating state changes.  
**Submodule 9: Machine Learning Methods in Biomarker Discovery** - Explore basic machine learning methods using the IRI proteomics data.  


## Data

These tutorials use example sequence data procured from the laboratory of Dr. Nisanne Ghonem at the Department of Biomedical and Pharmaceutical Sciences, College of Pharmacy, University of Rhode Island. The relevant manuscripts can be found [here](https://pubmed.ncbi.nlm.nih.gov/34328097/) and [here](https://pubmed.ncbi.nlm.nih.gov/34560548/)

## Troubleshooting

R packages, particularly those from BioConductor, often have many dependencies (i.e., other required packages they depend on to run).  This means that the first time you install these packages, it could take several minutes for everything to install. **Please don't assume the notebook has locked up!!!**  When a code block is running, an asterisk (\*) will appear in brackets to the left of the code box.  This indicates the code box is currently executing code.  Once it has completed, the asterisk will be replaced by a number indicating the order of commands.  Most of the code boxes should run very quickly.  You can execute multiple code blocks at the same time, but they will run in the order that you input them.  If a code block is taking longer to run than you expect, it may be waiting on another code block to finish executing.

If you get an error during package installation, it could be that R is trying to install a version of the package that is not compatible with the version of R you are using.  When you create your VM's to run this module, always use the latest version of R available (4.2 at the time of this writing).  Another common error is that a code block fails because the required package wasn't loaded.  All packages are loaded at the top of the notebook so double check that there are no errors there.

Necessary R packages will be loaded in each submodule.  When we begin working with experimental data, we will build an experimental object which will be reloaded and extended in later modules.  It's important that submodules 5-9 be run in order (at least the first time) to ensure that the experimental data is loading correctly. 

## Funding

This module was funded through an administrative supplement to the Rhode Island IDeA Network of Biomedical Research Excellence (RI-INBRE) from the National Institute of General Medical Sciences of the National Institutes of Health under grant number P20GM103430 (RI-INBRE).


## Version History

<b>v1.0 (11/2022)</b> - Launch of module with core notebooks (Chapter 1-6) and README.md.<br>
<b>v1.1 (04/2023)</b> - Launch of final module with all submodules on NIH CLoudLab


## License for Data


Text and materials are licensed under a Creative Commons CC-BY-NC-SA license. The license allows you to copy, remix and redistribute any of our publicly available materials, under the condition that you attribute the work (details in the license) and do not make profits from it. More information is available [here](https://tilburgsciencehub.com/about/#license).

![Creative commons license](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)
