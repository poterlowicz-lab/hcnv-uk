---
title: "hCNVbundles project- ELIXIR UK"
author: "Khaled Jumah, Krzysztof Poterlowicz" 
date: "11/04/2022"
output: html_document
---

# WP3 - Exploitation of the datasets by the Galaxy Community. 


## 1.  Intergrating a Copy number variant (CNV) detecting tools into Galaxy. 

Although  a number of the CNV detectiong tools have been developed over the recent years (ref Khaled) only a few of them were intergated into the Galaxy
and only couple of them are suported and functional (Khaled put tools table here).
 
Whole exome sequning CNV detection tools according to [reference paper] 

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
 
 
 
Galaxy training network community [web reference] provide a copmprehensive tutotial [ web link to the tutorial / https://training.galaxyproject.org/training-material/topics/dev/tutorials/tool-from-scratch/tutorial.html]  to instruct the reader in the full process of integrating a tool into Galaxy thorugh the process of  
 - the creation of a bioconda recipe for a new tool
 - writing a Galaxy tool wrapper
 - finally the testing and deployment of this tool into both a local and public Galaxy environment. 

This document present a case study of intergrating  [CNVkit](https://cnvkit.readthedocs.io/en/stable/) into the Galaxy using the above tutorial   

## 2. Benchmarking hCNV detection tools. 
Choosing a specific tool to carry on the analysis require information about   CNVs detection accuracy, execution time and required infrastructure.  
  
Our plan includes :  

1. Do a benchmark test for the CNV detection workflow in Galaxy to measure the run time and detected CNV

2. Compare them with a reference CNV test.    

The reference CNV workflow is available in the reference article below.  
https://www.nist.gov/programs-projects/genome-bottle  
 
The workflow and the tools/code used  
https://github.com/NCBI-Hackathons/TheHumanPangenome/tree/master/MHC/e2e_notebooks 
 

# WP4 - Training and dissemination 
Usually, The preprocessing steps for CNVs data (from the quality control to the mapping step) are the similar for all CNVs detecting workflows. The changes occur in the CNVs detection step. 

Our plan is to create a tutorial that allows the user to understand the CNVs detection process and give guidance on how to choose between the available CNVs tools. 

The process to create this tutorial is by: 

1. View the input requirements for some of the available CNVs tools. 

2. Create a shared prepossessing workflow for different tools data. 

3. Make the tool that requires the longest prepossessing as the main tool in the tutorial and locate the sections where we can introduce the different CBV tools for the data. 

4. add links for additional reading to provide the user with further knowledge on how to use a specific CNV tool 

5. Locate most of the CNV detecting tools available in/outside galaxy 

Our current progress can be found here [tutorial](https://github.com/kpbioteam/training-material/blob/project34/topics/variant-analysis/tutorials/somatic-variant-discovery/tutorial.md) that uses Contol-freec to detect CNVs which also can be the backbone tutorial for this cause.  


