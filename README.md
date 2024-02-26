# Fake sources project

### Machine Learning and Causal Inference. MSc in Data Science Methodology. Barcelona School of Economics.

Project idea contributed by Miquel Torrens (Centre for Genomic Regulation).

## Description

In this project you should attempt to conduct a causal analysis of
molecular data profiled in beta cells from human pancreatic islets.
Human beta cells, located in pancreatic islets, are endocrine cells which are
responsible for secreting insuline, a vital horm one that is the key regulator
of blood glucose levels in humans. They do so by transcribing the INS gene in
large quantities, a gene that composes over 30% of the transcripts generated in
the average human beta cell, making it a highly specialised cell type. However,
the process of insulin secretion is highly complex and is affected by the
co-regulation of hundreds of genes, meaning that there is a complex genomic
architecture involving said genes and other genomic regulatory elements that
must interact and cooperate for a functional beta cell to work correctly.

We will study the regulation of two genes whose function is essential in the
beta cell regulation machinery, a protein coding gene, and a transcription
factor (TF) gene. A TF gene encodes a protein that binds to the DNA sequence in
nearby locations of other genes and contributes to (de-)activate transcriptional
machinery of said targets. In this way, we know that if a TF binds to the
[promoter](https://en.wikipedia.org/wiki/Promoter_%28genetics%29) of another
gene, it has a very good chance of regulating said gene, in the form of
increasing its transcription or, contrarily, of repressing it.

Let's say that we have very solid experimental results, gathered by in-vitro
gene-editing assays in the lab, that said transcription factor gene, named "d"
in the provided dataset, is helping increase the transcription of our protein
coding gene of interest, which will be our output variable "y", as, among other
evidence, we find a strong binding of the TF to the promoter of "y".

Since usually lab experiments cannot be done in living human cells, we need to
confirm the evidence obtained in the lab on real human islet cells. We have
collected samples of donor human islet beta cells, sequenced and processed them
in the lab using a modern single-cell prospection technique called
[VASA-seq](https://www.nature.com/articles/s41587-022-01361-8), and counted the
amount and type of transcripts found in each of them, providing us with a matrix
containing for each cell (in rows) a normalised and standardised count for each
of the genes (in columns). 

### Task

Our task here is to corroborate the experimental knowledge of co-regulation
between these two genes using the gene expression data, i.e. confirming that "d"
has a causal effect on "y". Since both "y" and "d" are regulated by other genes,
some of which might affect either or both of them, there are many confounding
effects that can mask the actual effect of "d" on "y".

In a previous practical session in class we have:

* Tried out different methodologies to make inference on the average treatment
  effect (ATE).
* Observed the principles of over- and under- selection of different methods.
* Analyse their performance through treatment inclusion indicators, and
  treatment effect confidence intervals.
* Assess whether we can confirm that transcription on gene “d” has an effect on
  the transcription of gene "y".

This project consists of continuing to validate this relationship. You will use
[single-cell RNA-seq](https://en.wikipedia.org/wiki/Single-cell_sequencing#Transcriptome_sequencing_%28scRNA-seq%29)
data (provided), a more established and standard sequencing technology, for
which we have sequenced many more cells (about ~10x more) but for which we get
many fewer transcripts per cell (i.e. counts per gene are lower, thus yielding
a lot of sparsity and weaker gene-to-gene correlations). Despite technological
differences, both techniques measure the same metric on beta cells from donor
pancreatic islets, but the scRNA-seq data is split in 10 different i.i.d.
samples. We hope that the results on this data should confirm and expand our
findings in the previous dataset. The tasks for the project are as follows:

1. [3p] Generate a boxplot of the sample point estimates (for each of the 10
   samples) for (one version of) each of the following methods: MLE, LASSO, BMA,
   DL, ACPME, CIL. Do these sampling distributions resemble the results and
   principles observed in the analysis done in class, where we used a dataset
   obtained with a different sequencing technology?
2. [3p] Build a model using the integrated dataset (all 10 samples together) and
   generate a plot comparing point estimates and 95% confidence intervals across
   methods in [1.]. Report also in a table the corresponding p-values or
   (marginal) posterior probabilities of inclusion (depending on the method) for
   the treatment variable.
3. [2p] Whenever possible, compute the size of the models in [2.] to disentangle
   which methods might be over- or under-selecting covariates, and comment about
   the observed effect on point estimate precision.
4. [2p] Interpret the results: does the combined evidence from the two datasets
   confirm the existence of the regulation between “d” and “y”? Can you spot any
   relevant flaws or limitations of our data or the analysis? Justify your claims.

## Submission procedure

This project has to be submitted using
[GitHub Classroom](https://classroom.github.com). This
means that you should have cloned the GitHub repo of this project
from the organization account for MLCI in the corresponding academic
year at https://github.com/MLCIXXXX using the submission link
provided at the Google Classroom.

Once you have cloned this GitHub repo, then you can work on it in
your local disk and _push_ your changes whenever you like, but make
sure that you have pushed the last version of your assignment before
the deadline; consult the Google Classroom if you are unsure about
the deadline. There is no _submit_ button or any other specific
submission procedure or action than just pushing your changes to your
GitHub assignment repo. When correcting the assignment, the version
available at the deadline will be retrieved. If the last update to
the repo is posterior to the deadline, then the mark of the
assignment will have a penalty.
