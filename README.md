---
title: "ELIXIR UK milestones made by Khaled Jumah on behalf of Potworloicz team."
author: "Khaled, Krzysztof" 
date: "11/04/2022"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

# Elixir UK Milestones for Implementation srudes. 


## 1.  Create documentation to guide the resurchers to wrap Copy number variant (CNV) detecting tools into Galaxy and Bioconda. 

With the availability of only a few tools for CNV detection on Galaxy, still, alot of them are not available, so we will create documentation to show the process of wrapping the tools into Bioconda and then to Galaxy by: 

1. Locate the available tutorials on how to wrap a tool into Bioconda

- This link, [how to containerise a bioinformatics tool into Bioconda](https://bioconda.github.io/contributor/index.html),  has all the information to contribute to Bioconda  
2. Locate the available tutorials on how to wrap a tool from Bioconda to Galaxy 
- Use this link, [how to use planemo to wrap containerised bioinformatics tool into galaxy](https://planemo.readthedocs.io/en/latest/writing_standalone.html), to use Planemo to wrap a tool into galaxy  
- If you don’t know how to git Planemo use this link, [how to install Planemo](https://planemo.readthedocs.io/en/latest/installation.html)
 - For more information about Planemo use this link, [for more information on Planemo](https://planemo.readthedocs.io/en/latest/).
3. Create documentation on Galaxy using those tutorials to guide the user to wrap his CNV tool into Galaxy. 

After the discussion, We have agreed to wrap [CNVkit](https://cnvkit.readthedocs.io/en/stable/) as an example.  


## 2. The CNV tools are different from each other in the outcomes and infrastructure requirements. 
Choosing a specific tool to carry on the analysis can be considered on the accuracy of CNVs detection, analysis time and the required infrastructure. Even though Galaxy shows the time for the analysis, creating a graph that compares the available CNVs workflows on Galaxy for the same data with each other can give an additional point of view to the user in terms of accuracy, time spent and infrastructure required. 
  
This can be done by:  

1. Do a benchmark test for the available workflows in Galaxy (We are orking on expanding this part) to measure the run time and detected CNV
2. compare them with a reference CNV test.    

The reference CNV workflow is available in the reference article below.  
https://www.nist.gov/programs-projects/genome-bottle  
 
The workflow and the tools/code used  
https://github.com/NCBI-Hackathons/TheHumanPangenome/tree/master/MHC/e2e_notebooks 
 
Part of of the availabel bioinformatics tools for CNV detection using exome sequencing data 

Tool| Reference | Ural | Availabel on tool shed    
----| --------- | ---- | -------------------
Control-FREEC| [1](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR53)| [1](http://bioinfo-out.curie.fr/projects/freec/) | [Yes](https://toolshed.g2.bx.psu.edu/repository/browse_repositories?f-free-text-search=Control-FREEC&sort=name&operation=view_or_manage_repository&id=fafcb3ceb9215f19) / [owner](https://toolshed.g2.bx.psu.edu/repository/browse_repositories_by_user?user_id=b563abc230aa8fd0)
CoNIFER | [2](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR54) | [2](http://conifer.sf.net/) | No
XHMM | [3](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR55) | [3](http://atgu.mgh.harvard.edu/xhmm) | No 
ExomeCNV | [4](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR49) | [4](http://cran.r-project.org/src/contrib/Archive/ExomeCNV/) | No
CONTRA | [5](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR77) | [5](http://contra-cnv.sourceforge.net/) | [Yes](https://toolshed.g2.bx.psu.edu/repository/browse_repositories?f-free-text-search=CONTRA&sort=name&operation=view_or_manage_repository&id=5ed52e96157e1d8b) / [owner](https://toolshed.g2.bx.psu.edu/repository/browse_repositories_by_user?user_id=fa71383023bd0c81)
CONDEX | [6](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR78) | [6](http://code.google.com/p/condr) | No
SeqGene | [7](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR79) | [7](http://seqgene.sourceforge.net/) | No
PropSeq | [8](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR52) | [8](http://bioinformatics.nki.nl/ocs/) | No
VarScan2 | [9](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR50) | [9](http://genome.wustl.edu/software/varscan) | [Yes](https://toolshed.g2.bx.psu.edu/repository/browse_repositories?f-free-text-search=VarScan2&sort=name&operation=view_or_manage_repository&id=2a3dbf8c5c7d05b5) / [alternative](https://toolshed.g2.bx.psu.edu/repository/browse_repositories?f-free-text-search=VarScan2&sort=name&operation=view_or_manage_repository&id=885b054013c7d7ba) / [alternative 2](https://toolshed.g2.bx.psu.edu/repository/view_repository?sort=name&operation=view_or_manage_repository&id=af4ecd84770259cd) /[owner1-2](https://toolshed.g2.bx.psu.edu/repository/browse_repositories_by_user?user_id=5487164d09c88395) / [owner2](https://toolshed.g2.bx.psu.edu/repository/browse_repositories_by_user?user_id=fa71383023bd0c81)
ExoCNVTest | [10](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR56) | [10](http://www1.imperial.ac.uk/medicine/people/l.coin) | No 
ExomeDepth | [11](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-14-S11-S1#ref-CR30) | [11](http://cran.r-project.org/web/packages/ExomeDepth/index.html) | [Yes](https://toolshed.g2.bx.psu.edu/repository/browse_repositories?f-free-text-search=ExomeDepth&sort=name&operation=view_or_manage_repository&id=7dc050469e4bd1bb) / [Owner](https://toolshed.g2.bx.psu.edu/repository/browse_repositories_by_user?user_id=63e16d726d394a5e)
XCAVATOR | NA | [12](https://sourceforge.net/projects/xcavator/) | NO 
CNVkit |  [13](https://cnvkit.readthedocs.io/en/stable/) | [13](https://github.com/imgag/ClinCNV) | No 


## Same preprocess different CNV tool (WES) tutorial. 
Usually, the CNVs workflows share the same process to prepare the data from the quality control to the mapping step. The changes occur in the CNVs detection step, so we will work to create a tutorial that allows the user to understand the process of the CNVs detection method and give him guidance on how to choose between the available CNVs tools to proceed with his analysis. 

The process to create this tutorial is by: 

1. View the input requirements for some of the available CNVs tools. 

2. Create a shared prepossessing workflow for different tools data. 

3. Make the tool that requires the longest prepossessing as the main tool in the tutorial and locate the sections where we can introduce the different CBV tools for the data. 

4. add links for additional reading to provide the user with further knowledge on how to use a specific CNV tool 

5. Locate most of the CNV detecting tools available in/outside galaxy 

We have almost done creating [tutorial](https://github.com/kpbioteam/training-material/blob/project34/topics/variant-analysis/tutorials/somatic-variant-discovery/tutorial.md) that uses Contol-freec to detect CNVs which also can be the backbone tutorial for this cause.  



