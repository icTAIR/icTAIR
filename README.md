# icTAIR
##Introduction

Contextual Transcriptional Activity Inference of Regulators (icTAIR) is an iterative algorithm that takes as its input previously-defined target genes of regulators and gene expression data from a dataset of samples for a given context. It then employs Binding Association with Sorted Expression (BASE) method to integrate these inputs and calculate individual Regulatory Activity Scores (iRASs) for each sample for that regulator. It then correlates each target gene’s expression with the regulator’s iRAS across the samples, drops the weakly and uncorrelated target genes to create an updated target gene list, and repeats the whole process. Once N iterations are used to generate a stable list of contextually-refined target genes, this list can be used for a final BASE-derived iRAS discernment for additional samples within that context, enabling further downstream analyses.

##Usage
refined_gset <- icTAIR(geneExp, tarGene, iterativeMax, setMin, corCut, permTimes, channel)

###icTAIR requires as input two data sources:
(1) geneExp: a gene expression data from a dataset of samples for a given context.<br/>
(2) tarGene: a previously-defined target genes of regulators.<br/>

###icTAIR also requires five parameters:
(1) iterativeMax: the maximum number of allowed iterations, default set to 10.<br/>
(2) setMin: the minimum allowable length of a target gene list, default set to 20.<br/>
(3) corCut: the minimum correlation threshold, either as a value (0-1), default set to 0.1.<br/>
(4) permTimes: the number of permutation times in BASE, default set to 1000.<br/>
(5) channel: the Microarray channel of dataset of gene expression profiles of samples, True means one channel and FALSE means two channel, default set to T.<br/>

##Install
(1) download the icTAIR_0.0.1.tar.gz file.
(2) install the package using install.packages("file_path/icTAIR_0.0.1.tar.gz").
(3) library("icTAIR_0.0.1.tar.gz").

##Example
Here, we use the gene expression data of 50 TCGA breast cancer samples, and pre-defined target gene lits of 100 regulators from MsigBD c3 as examples.<br/>
refined_gset <- iTARI(geneExp = tcga_example, tarGene = MSigDB_example, iterativeMax = 10, setMin = 20, corCut = 0.1, permTimes = 1000, channel = T)

##Contact
Please contact Yue Wang by yue.wang@dartmouth.edu and Chao Cheng by Chao.Cheng@dartmouth.edu if you have any questions.
