-   [S1: Citation information](#s1-citation-information)
-   [S2: Accessibility](#s2-accessibility)
    -   [S2.1: Install CRAN packages](#s2.1-install-cran-packages)
    -   [S2.2: Install Bioconductor packages](#s2.2-install-bioconductor-packages)
    -   [S2.3: Run the Shiny application](#s2.3-run-the-shiny-application)
-   [S3: Single-cell RNA-seq](#s3-single-cell-rna-seq)
    -   [S3.1: Overview](#s3.1-overview)
    -   [S3.2: A method to obtain this data](#s3.2-a-method-to-obtain-this-data)
    -   [S3.3: TPM filtration](#s3.3-tpm-filtration)
-   [S4: A note about input data](#s4-a-note-about-input-data)
    -   [S4.1: Expression matrices](#s4.1-expression-matrices)
    -   [S4.2: Condition matrices](#s4.2-condition-matrices)
-   [S5: Quality Control](#s5-quality-control)
    -   [S5.1: File Summary](#s5.1-file-summary)
-   [S6: Discovery-Driven Analyses](#s6-discovery-driven-analyses)
-   [S7: Differential Gene Expression](#s7-differential-gene-expression)
    -   [S7.1: An overview of experimental designs](#s7.1-an-overview-of-experimental-designs)
    -   [S7.2: Setting up an experiment](#s7.2-setting-up-an-experiment)
-   [S8: GEO Usage](#s8-geo-usage)
    -   [S8.1: Overview](#s8.1-overview)
    -   [S8.2: Series](#s8.1-series)
    -   [S8.3: Samples](#s8.3-samples)
    -   [S8.4: Protocols](#s8.4-protocols)
    -   [S8.5: Data processing pipeline](#s8.5-data-processing-pipeline)
    -   [S8.6: Processed data files](#s8.6-processed-data-files)
    -   [S8.7: Raw files](#s8.7-raw-files)
    -   [S8.8: Paired-end experiments / SOLiD data](#s8.8-paired-end-experiments-solid-data)
    -   [S8.9: Downloads](#s8.9-downloads)
-   [S9: BRIC Usage](#s9-bric-usage)
-   [S10: Using large expression matrices](#s10-using-large-expression-matrices)
-   [S11: References](#s11-references)

S1: Citation information <a id="s1-citation-information"></a>
========================

**Table 1:** A comparative overview of citation counts for DGE tools and
DGE servers. DGE analytical tools (*Tool*) are compared based on the
following criteria: Current number of citations (*Citations*),
percentage of total citations from the analytical tools presented
(*Citation %*), year the analytical tool was published (*Year*),
approximate citations per year based on data accrued through 2017
(*Citations/Year*), and if the analytical tool has an R-based
application (*R-based*).

<table>
<thead>
<tr class="header">
<th>Tool</th>
<th>Citations</th>
<th>Citation %</th>
<th>Year</th>
<th>Citations/Year (through 2017)</th>
<th>R-based?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>edgeR (Robinson et al. 2010)</td>
<td>7093</td>
<td>32.39700375</td>
<td>2010</td>
<td>1013.285714</td>
<td>Yes</td>
</tr>
<tr class="even">
<td>Cuffdiff (Trapnell et al. 2012)</td>
<td>4533</td>
<td>20.70430255</td>
<td>2012</td>
<td>906.6</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Cuffdiff2 (Trapnell et al. 2013)</td>
<td>1508</td>
<td>6.887731799</td>
<td>2013</td>
<td>377</td>
<td>No</td>
</tr>
<tr class="even">
<td>DESeq2 (Love et al. 2014)</td>
<td>4249</td>
<td>19.40714351</td>
<td>2014</td>
<td>1416.333333</td>
<td>Yes</td>
</tr>
<tr class="odd">
<td>limma (Ritchie et al. 2015)</td>
<td>2399</td>
<td>10.95733991</td>
<td>2015</td>
<td>1199.5</td>
<td>Yes</td>
</tr>
<tr class="even">
<td>DEGseq (Wang et al. 2009)</td>
<td>1237</td>
<td>5.649949758</td>
<td>2009</td>
<td>154.625</td>
<td>Yes</td>
</tr>
<tr class="odd">
<td>baySeq (Hardcastle et al. 2010)</td>
<td>562</td>
<td>2.56691331</td>
<td>2010</td>
<td>80.28571429</td>
<td>Yes</td>
</tr>
<tr class="even">
<td>SAMseq (Li et al. 2013)</td>
<td>275</td>
<td>1.256051886</td>
<td>2013</td>
<td>68.75</td>
<td>Yes</td>
</tr>
<tr class="odd">
<td>NOIseq (Tarazona et al. 2012)</td>
<td>38</td>
<td>0.173563533</td>
<td>2012</td>
<td>7.6</td>
<td>Yes</td>
</tr>
</tbody>
</table>

S2: Accessibility <a id="s2-accessibility"></a>
=================

IRIS-EDA can be freely accessed directly through this
[link](https://bmbls.bmi.osumc.edu/IRIS/) or through R using the following
code in the proceeding sections.

S2.1: Install CRAN packages <a id="s2.1-install-cran-packages"></a>
---------------------------

IRIS-EDA requires several packages to operate. To get these pacakages,
the following commands can be entereed into an R terminal to check if
you already have the necessary packages. If not, the following code will
install any missing packages:

    # CRAN
    packages <- c(
        "crosstalk", "dplyr", "DT", "gtools", "plotly", "shiny", "plyr",
        "shinyBS", "shinycssloaders", "shinythemes", "tibble", "tidyr",
        "Rcpp", "Hmisc", "ggplot2", "locfit", "GGally", "pheatmap", 
        "reshape2", "backports", "digest", "fields", "psych", "stringr", 
        "tools", "openxlsx", "Rtsne", "WGCNA", "flashClust", "parallel",
        "MCL", "kmed", "ape"
    )
    np <- packages[!(packages %in% installed.packages()[, "Package"])]
    if(length(np)) install.packages(np)

S2.2: Install Bioconductor and Devlopmental packages <a id="s2.2-install-bioconductor-packages"></a>
-----------------------------------

You will also need several Bioconductor packages. Similar to the prior
section, the following code will check and install any missing
Bioconductor packages into your R library:

    # Bioconductor
    bioc_packages <- c(
        "DESeq2", "edgeR", "limma", "QUBIC", "geneplotter", "GO.db", "impute",
        "preprocessCore", "AnnotationDbi"
    )
    np <- bioc_packages[!(bioc_packages %in% installed.packages()[,"Package"])]
    if (!require("BiocManager")) install.packages("BiocManager")
    BiocManager::install(np)


To run BRIC analysis, you also need to download the source code for this
clustering algorithm. Run this code to get the GitHub package:

    # GitHub
    if (!require("devtools")) install.packages("devtools")
    devtools::install_github("OSU-BMBL/BRIC",force = T)


S2.3: Run the Shiny application <a id="s2.3-run-the-shiny-application"></a>
-------------------------------

Once you have installed all of the necessary packages, you can now run
the application locally by entering the following code into an R
terminal:

    shiny::runGitHub("iris", "OSU-BMBL")

Typically, the link will provide an easier route to using IRIS-EDA. In
circumstances where internet connections will be limited (such as during
travel), loading IRIS-EDA through R while internet is still available
will allow users to utilize IRIS-EDA without an internet connection
later on.

Installing the local application via
[GitHub](https://github.com/OSU-BMBL/iris) will also let the user have
access to more "developmental" versions of IRIS-EDA. Be warned though;
using developmental versions of this application may be "cutting edge",
however, this could potentially break various features in the
application. Therefore, using the server
(<https://bmbls.bmi.osumc.edu/IRIS/>) will provide a more "stable",
peer-reviewed release of the application.

S3: Single-cell RNA-seq <a id="s3-single-cell-rna-seq"></a>
=======================

S3.1: Overview <a id="s3.1-overview"></a>
--------------

Upon sample submission to IRIS-EDA, you have two options: (1) Perform
analyses on a normal RNA-seq experiment or (2) run single-cell RNA-seq
analysis.

If you choose the latter option, you will need to provide a file
containing ID lengths to help reduce variability. This is crucial since
filtration of low TPM (transcripts per million) reads can lead to better
results. In order to calculate TPM, ID length approximations are needed
in conjunction with raw count data. To submit this information to
IRIS-EDA, **you will need to provide ID data that follows the proceeding
criteria**:

    id        id_len_kbp
    gene001          1.4
    gene002          5.6
    gene003          0.8
    ...              ...

**Note**: This file must be in a comma seperated value (CSV) format,
where column 1 is the ID (e.g. gene, transcript, etc.) and column 2 is
the approximation of length in **kilobase pairs**.

S3.2: A method to obtain this data <a id="s3.2-a-method-to-obtain-this-data"></a>
----------------------------------

There are many ways to obtain these values. A common procedure would be
to parse the respective general fearture format version 3 (GFF3) file
and determine the length through calculating the difference between the
start and end locations.

If you need help parsing this information, a primitive `R` function has
been made, which you can find
[here](https://gist.github.com/btmonier/409856fe22280603ca19345fdd4e5e22).
To run this function, you will need to install and load 3 packages into
your R library:

-   `ape`
-   `stringr`
-   `dplyr`

All of these packages can be found on the [CRAN
repository](https://cran.r-project.org/), or by using the
`install.packages()` function provided in the base package of `R`.

This function has four parameters:

-   `gff`: the location to the GFF3 file on your computer

-   `cts`: your raw count matrix that you will provide to IRIS-EDA.
    **Note**: this object must be a `matrix` type and have the same
    format that is found in the first section of this walkthrough (*A
    note about input data*).

-   `type`: the GFF3 type column identifier (e.g. gene, transcript,
    exon, CDS, etc.)

-   `attribute`: the GFF3 attribute (e.g. `ID`, `gene_id`,
    `transcript_id`, `gene_name`, or `transcript_name`)

Depending on the size of this file, this may take some time. This
function will return a `tibble` data frame, so make sure you assign it
to an object before you use `write.csv()`. After you perform this task,
the file can successfully be submitted to IRIS-EDA.

S3.3: TPM filtration <a id="s3.3-tpm-filtration"></a>
--------------------

Once you have submitted the data, you will notice that the
`Filter cutoff` changes from `count data row sums` to `TPM`:

<img src="../vignettes/img/geo-tpm-01.png" width="300px">

The default is set to a value of `1`, however, this can be changed at
the user's discretion.

**Note (1)**: this value corresponds to which rowsums (i.e. ID sums)
will be filtered out if they have a value that is less than the user
parameter.

**Note (2)**: “For users with 10X scRNA-Seq data or other data type with
expected low expression across all genes, we have a submission option
that changes default parameterizations to account for this. If
submitting 10X scRNA data, please use the `scRNA - 10X Genomics` option.

S4: A note about input data <a id="s4-a-note-about-input-data"></a>
===========================

IRIS-EDA requires two pieces of information for analysis. The first is
an expression estimation matrix, also referred to as a count matrix,
displaying the gene expression estimates for each sample. The format
requires a CSV file with the row names to list the gen IDs and column
names to list the sample IDs. The second required input is a condition
matrix, wherein the factor levels for each sample are provided. This
file requires a CSV format and row names to be the sample IDs matching
the sample IDs from the expression estimation matrix and the column
names to be the condition factors.

The data used for this tutorial are derived from 28 *Vitis vinifera*
(grape) samples with three distinct factors (Rootstock, row, and block).
This data can viewed as the "big" example data set found under the
`Submit and QC` tab under `1. Submission Parameters`.

S4.1: Expression matrices <a id="s4.1-expression-matrices"></a>
-------------------------

Typically, an expression matrix, also known as count data or a count
matrix refers to data where every *i*-th row and *j*-th column refer to
how many reads are assigned to gene (ID) *i* in sample *j*. For example,
if we have simplified count data for 4 samples and three genes, the `R`
output will look something like this:

            sample1 sample2 sample3 sample4
    gene001      23       3      45       2
    gene002       6       7       7       8
    gene003       0      34       3      42

**Note<sup>1</sup>:** When loading count data into IRIS-EDA, make sure
that the first column is your gene IDs and that sample names are short,
concise, and avoid the use of mathematical operators (`+`, `-`, `/`,
`*`, `^`, etc.) and spaces between words. If a space is necessary for
legibility, please consider using an underscore (`_`)

**Note<sup>2</sup>:** For sample names, **avoid starting any entries
with numerical elements** (e.g. `1sample`, `2_human`, `42_amf`, etc.).
This may potentially cause unexpected errors in downstream analyses!

S4.2: Condition matrices <a id="s4.2-condition-matrices"></a>
------------------------

Condition matrices, also known as metadata, details the design of your
experiment. In this type of matrix, every *i*-th row and *j*-th column
refer to factor levels assigned to sample *i* and factor *j*. For
example, if were to look at the samples given in the [count
data](#count-mat) section, the metadata `R` output will look something
like this:

            condition time
    sample1   treated   0h
    sample2 untreated   0h
    sample3   treated  24h
    sample4 untreated  24h

**Note<sup>1</sup>:** When loading metadata into IRIS-EDA, make sure
that the first column is your sample names and that column names and
treatment levels are short, concise, and avoid the use of mathematical
operators (`+`, `-`, `/`, `*`, `^`, etc.) and spaces between words. If a
space is necessary for legibility, please consider using an underscore
(`_`).

**Note<sup>2</sup>:** For this data, **avoid starting any entries with
numerical elements** (e.g. 1, 2, 42, etc.). This may potentially cause
unexpected errors in downstream analyses!

**Note<sup>3</sup>:** Metadata can be expanded to fit the nature of your
experiment (i.e. multiple factors can be added). The only thing that
must remain consistent between these two matrices, is the sample
information. Column names in count data **must** be the same as row
names in the metadata.

S5: Quality Control <a id="s5-quality-control"></a>
===================

1.  Click on the `Submit and QC` tab near the top-left corner of the
    application:

<img src="../vignettes/img/subqc-01.png" width="300px">

2. Under `1. Submission Paramters`, select either
`Start with a small example data set`,
`Start with a big example data set`, or `Load my own data` to upload
user data. **Note:** User data requires one count matrix and one
condition matrix:

<img src="../vignettes/img/subqc-02.png" width="300px">  
  
2. Under `2. Data Processing`, select a filter cutoff to simplify and
expedite computations by eliminating any rows that have below specified
expression totals. The default argument for our application is `10`:

<img src="../vignettes/img/subqc-08.png" width="300px">  
3. Right below the filter cutoff parameter, select a transformation
method for the count data for displaying the expression estimate.
**Note:** For more information about any of these topics, take a look at
the *FAQ* section at the bottom of this document:

<img src="../vignettes/img/subqc-09.png" width="300px">  
4. Click `Submit` to load the data under `3. Launch Overview`:

<img src="../vignettes/img/subqc-03.png" width="300px">  
5. After you click `Submit`, the main page will now be populated with
several pieces of information in two sub-tabs, `File Summary` and
`Count Summary`.

S5.1: File Summary <a id="s5.1-file-summary"></a>
------------------

`File Summary` provides a glimpse into the submitted data. This subtab
includes three main components.

1.  The `count data` section will detail the first and last five rows of
    the count data and also include the total number of IDs and samples:

<img src="../vignettes/img/subqc-10.png" width="300px">  
2. The second portion includes an overview of the condition data this is
simply an `R` console-based output of this submitted CSV file:

<img src="../vignettes/img/subqc-11.png" width="300px">  
3. Finally, pre- and post-filtered gene ID counts gives a
"before-and-after" count of the number of IDs that were filtered using
the filter cutoff parameter under `2. Data Processing`:

<img src="../vignettes/img/subqc-12.png" width="300px">  
  
\#\# S5.2: Count Summary `Count summary` provides three interactive,
downloadable visualizations based on the file for each sample.

1.  Box-and-Whisker Plot for transformed read counts by sample with
    interactivity showing the quartiles, maximum, and minimum count.
    *With the example data, it appears that the box-and-whisker plot for
    each sample is similar to the other samples. If one sample had a
    plot varying greatly from the others, it would indicate some
    required investigation into that specific sample in terms of the
    number of raw reads provided and proportion of reads aligned.*

<img src="../vignettes/img/subqc-13.png" width="300px">  
  
2. Count Data Distribution plot showing the frequency of transformed
count data by sample with interactivity displaying the value and
frequency. Additionally, double-clicking a sample ID in the legend
isolates just that sample's histogram. Additional sample IDs can be
select for more specific comparisons also. *With the example data, the
histograms appear similar for each sample, indicating no significant
derivation. Similar to the box-and-whisker plots, a single sample
varying greatly from other samples may indicate a required investigation
into the raw read counts or read alignment statistics.*

<img src="../vignettes/img/subqc-14.png" width="300px">  
<img src="../vignettes/img/subqc-15.png" width="300px">  

1.  Total Reads displays a histogram of total reads by sample with
    interactivity for displaying actual total read counts for each
    sample. Double-clicking on a sample ID in the legend isolates that
    sample's read count histogram and allows for selecting of specific
    adjacent sample IDs for comparison. Total reads counts for
    individual samples that vary greatly from the other total read
    counts may indicate some issues with data preparation (sequencing)
    or read alignment. *Here, sample H26313 has a much lower total reads
    count than the other samples. This may be reflected in further
    comparative analyses.*

<img src="../vignettes/img/subqc-16.png" width="300px">  

S6: Discovery-Driven Analyses <a id="s6-discovery-driven-analyses"></a>
=============================

1.  After examining your results on the `Submit and QC` tab, you may
    proceed to the `Discovery-Driven Analyses` tab:

<img src="../vignettes/img/prelim-01.png" width="300px">  
2. The `Discovery-Driven Analyses` tab will be populated with several
subtabs, similar to the `Submit and QC` tab. The first subtab you will
see is the `Correlation` tab. This tab provides correlation analysis of
the expression matrix by sample:

<img src="../vignettes/img/prelim-02.png" width="300px">  
  
3. Under the `Correlation` subtab you will see several visualizations.
`Interactive Correlation Analysis` displays a heatmap of the correlation
between samples with interactivity showing the actual correlation
between the two intersecting samples. *The example data shows most
sample-sample correlations of 0.95 or larger, indicating relatively high
correlation. The darker cells here signify less similar samples, which
may yield more interesting differential expression results. This graph
can indicate comparisons of interest in future analyses. In most cases,
the high number of gene IDs with similar or identical expression
estimates will cause correlations to be large, even for dissimilar
genetic expression profiles:*

<img src="../vignettes/img/prelim-03.png" width="300px">  
4. Clicking on a cell will provided a scatterplot of the two
intersecting samples with each data point representing one gene ID. A
scatterplot with points falling more closely along the diagonal
indicates samples with more similar genetic expression profiles. *This
scatterplot shows a clear trend of data points (gene IDs) falling along
or close to the diagonal. That means these two samples have very similar
genetic expression profiles. Data points that fall far from the diagonal
line represent genes with dissimilar expression levels between the
select samples:*

<img src="../vignettes/img/prelim-04.png" width="300px">  
  
5. The Sample Distance Matrix provides a heatmap of the Euclidean
distance between the gene expression vectors for each sample pair. The
larger distance (darker red color) indicates samples with the most
dissimilar genetic expression profiles. This matrix also includes a
clustering of the samples based on the vectorized expression profiles.
*With the example data, two distinct clusters can be observed through
the first branching of the dendrogram. Additionally, as with the
correlation heatmap, specific cells with a darker color indicate a more
dissimilar pair of samples based on genetic expression:*

<img src="../vignettes/img/prelim-05.png" width="300px">  
6. The next visualization will be under the `PCA` subtab. This subtab
provides Principal Component Analysis (PCA) for the expression
estimation matrix:

<img src="../vignettes/img/prelim-06.png" width="300px">  
  
7. This analysis has the option of selecting a factor of interest. *With
the example data, selecting "Rootstock" as the factor of interest
provides a visualization of the first two components for each sample. In
this application, PCA is a linear transformation of the gene expression
levels, with the first component representing the transformed dimension
with the most variability, and each subsequent component decreasing in
variability. This analysis has the potential to isolate samples based on
expression levels. Here, there does not appear to be any specific
rootstock that separates from the others. If there were, it could help
develop directions for further analysis. The axis labels indicate the
first principal component accounts for 37% of the variance between
samples, whereas the second principal component accounts for 7%:*

<img src="../vignettes/img/prelim-07.png" width="300px">  
8. The next visualization will be under the `MDS` subtab. This subtab
provides multi dimensional scaling for the expression estimation matrix.
This is similar to PCA except is develops components through non-linear
transformations of the gene expressions:

<img src="../vignettes/img/prelim-08.png" width="300px">  
  
9. *Looking back at our sample data, we observe similar results to that
of the PCA results, with similar potential interpretations if any sample
or groups of samples were to differentiate from the others:*

<img src="../vignettes/img/prelim-09.png" width="300px">  
  
10. t-SNE allows for visualization of results in two and three
dimensions. The three-dimensional figure is also interactive, allowing
users to move the axes to gain a better understanding of the
three-dimensional layout of the sample points.

<img src="../vignettes/img/tsne-01.png" width="300px">  
<img src="../vignettes/img/tsne-02.png" width="300px">  
11. The next visualization will be under the `Heatmap` subtab. This
subtab provides an interactive heatmap with rows representing the gene
IDs and columns representing sample IDs:

<img src="../vignettes/img/prelim-10.png" width="300px">  
  
12. This heatmap requires an ID cutoff to select the indicated number of
gene IDs with the highest mean expression values for display. Selecting
a cell displays a plot showing the total read counts for that specific
gene ID by the selected factor. *With the example data, the 20 most
variable gene IDs are displayed. The yellow color indicates gene IDs
with a higher expression level for that sample, and the darker blue
color represents a low expression level for that sample. Selecting ID:
rna25007 shows the read counts for that ID by rootstock factor. This
shows the "OWN" rootstock seems to have a higher expression level for
that ID, with the exception of one sample:*

<img src="../vignettes/img/prelim-11.png" width="300px">  
<img src="../vignettes/img/prelim-12.png" width="300px">  
  
13. On the next subtab (1), `Biclustering` performs a biclustering
analysis using one of the selected biclustering tools (3) with a maximum
bicluster size of the indicated cutoff value (2):

<img src="../vignettes/img/prelim-13.png" width="300px">  
  
14. Launching the analysis results in display of the first bicluster.
Alternative clusters can be selected from the dropdown menu and the IDs
and plot for each bicluster can be downloaded using the button below the
visualization. *With the sample data, the biclusters can help select the
samples under which certain gene IDs are similarly expressed. Since gene
expression levels can vary greatly over all samples and conditions, a
biclustering approach can isolate similar expression patterns on a level
where traditional clustering may miss. The first cluster for the example
data shows that samples B20715, D21515, and H12915 are expressed
similarly under the isolated gene IDs. Interpretations can be made
similarly for each subsequent bicluster:*

<img src="../vignettes/img/prelim-14.png" width="300px">  
  
15. The `Clustering` tab allows for users to select one of three
clustering methods respectively representing hierarchical,
representative, and graph-based clustering: Weighted Gene Co-expression
Network Analysis (WGCNA), k-medoids, and the Markov Clustering Algorithm
(MCL). While all three methods have demonstrated high performance
related to module detection, the default is WGCNA due to it being the
best of the three. Here, users should be careful with large datasets, as
these methods can take large amounts of time to run. Setting the
variable cutoff option lower will reduce the time by selecting fewer of
the most differentially expressed genes to use in clustering.

<img src="../vignettes/img/cluster-01.png" width="300px">  
  
16. The WGCNA method generates figures related to sample and gene
dendrograms, as well as a topological overlap matrix based on the genes.
Additionally, users can download lists of the genes and samples with
respective cluster assignments.

<img src="../vignettes/img/cluster-02.png" width="300px">  
<img src="../vignettes/img/cluster-03.png" width="300px">  
<img src="../vignettes/img/cluster-04.png" width="300px">  
  
17. The k-medoids method produces a downloadable consensus matrix
heatmap. Additionally, the generated clusters from this method are
downloadable.

<img src="../vignettes/img/cluster-05.png" width="300px">  
  
18. The MCL method generates a cluster diagram, along with downloadable
cluster compositions.

<img src="../vignettes/img/cluster-06.png" width="300px">  

S7: Differential Gene Expression <a id="s7-differential-gene-expression"></a>
================================

1.  After uploading the user data or selecting the example data, users
    can go directly to the `DGE Analysis` tab, preceding the
    `Discovery-Driven Analyses` functions:

<img src="../vignettes/img/dge-01.png" width="300px">  
  
2. Once you are on this tab, you will be greeted with several options.
`1. Experimental Setup` will allow users to select an experimental
design for their DGE analysis. Options are Two-group comparison,
Multiple factor comparisons, Classical interaction design, Additive
models (paired or blocking designs), Main effects, Main effects with
grouping factors, or Custom design:

<img src="../vignettes/img/dge-02.png" width="300px"> 

S7.1: An overview of experimental designs <a id="s7.1-an-overview-of-experimental-designs"></a>
-----------------------------------------

1.  The `Two-group comparisons` options is the traditional approach for
    DGE and compares two factors levels for the selected factor type.
    *With the example data, selecting "Two group comparisons" for the
    experimental design and "Rootstock" for the factor allows for
    specific pairwise comparisons of Rootstock factor levels. Here, we
    can select specific comparisons of interest from the permutations of
    all pairwise comparisons. Selecting all comparison options will
    provide inverse duplications, so specific selections may be needed.
    Below, all unique pairwise combinations are selected. The linear
    model is also displayed for users interested in the model used for
    comparisons:*

<img src="../vignettes/img/dge-03.png" width="300px">

1.  The `Multiple factor comparisons` design has users select two factor
    levels and performs all crosswise comparisons for the two chosen
    factor levels. *With the example data, the Multiple factor
    comparisons design with Rootstock and Block selected as the two
    factors provides optional comparisons for each rootstock separated
    by block. In this situation, as with the other designs, the user
    selects which comparisons are of interest. Selecting
    C3309\_B\_VS\_C3309\_E allows for a comparisons of gene expression
    levels for the same rootstock in two different blocks. This provides
    insight into the locations and possibly time (due to time
    requirements for sampling) for this specific rootstock:*

<img src="../vignettes/img/dge-04.png" width="300px">

1.  The `Classical interaction design` allows the user to select two
    factor levels and one reference level for each of the selected
    factors. *With the experimental data, the Classic interaction design
    allows for selection of two factors and a reference for each. In
    this case, the Rootstock and Row are the chosen factors and OWN and
    15 are the selected reference levels for comparison. The contrast
    levels selected upon submission will provide DEGs with respect to
    these two levels:*

<img src="../vignettes/img/dge-05.png" width="300px">

1.  The `Additive models` design is useful when samples are paired or
    blocked into distinct groupings. This format requires selected
    factors, one for the pairing or blocking factor and the other for
    the treatment factor. Additionally, a reference level for each
    selected factor is required. *In the example data, the Rootstock
    factor can be considered for grouping and the treatment factor is
    Block. OWN is selected as the reference level for the blocking
    factor and the A15 Block is selected for the treatment reference
    level:*

<img src="../vignettes/img/dge-06.png" width="300px"> 

1.  `Main Effects` experimental design allows for testing the
    significance of a factor across multiple factor levels. In this
    situation, any significant deviation from an intercept would result
    in a significantly differential expressed gene. Using this approach
    is most useful when users want to test the significance of a factor
    that has more than two levels. This design requires indication of
    which factor to test as the main effect. Additionally, users must
    specify a factor reference level for the lfc and for corresponding
    visualizations. The *p*-values, adjusted *p*-values, and related
    differentially expressed genes are not affected by the selected
    reference level. *In the example data, the Rootstock factor is
    selected, which will test whether Rootstock has a significant impact
    on the genetic expression across all Rootstock factor levels.
    Selection of the C3309 Rootstock factor level as a reference will
    provide lfc values and visualizations relative to this level, while
    *p*-values and adjusted *p*-values will be calculated with respect
    to the main effect of the chosen factor:*

<img src="../vignettes/img/dge-07.png" width="300px"> 

1.  `Main effects with grouping factors` design allows for a more
    detailed main effects testing to be performed. This design tests the
    indicated main effect when the data is subset by a user-indicated
    factor. Requirements for this design are indication of main effect
    to test, factor for grouping, and grouping factor level for which to
    provide results. As with the main effects design, the user also
    specifies a main effect reference level for lfc and visualizations.
    *In the example data, Rootstock is selected as the grouping factor,
    with C3309 selected as the grouping factor level for which the
    results table will be based on. The Block factor is selected to test
    the main effect, with B13 selected as the main effect reference
    level. This analysis will indicate which genes are differentially
    expressed when account for Block only for the C3309 samples:*

<img src="../vignettes/img/dge-08.png" width="300px"> 

1.  Finally, `Custom design` provides advanced users with a method for
    indicating their own design matrix. This method is provided so that
    users can perform more intricate DGE analyses beyond what IRIS-EDA
    already provides as experimental design options. It is only
    recommended that users with advanced knowledge of the modeling
    process to use this option, as the required design matrix may not be
    intuitive to use appropriately:

<img src="../vignettes/img/dge-09.png" width="300px"> 

S7.2: Setting up an experiment <a id="s7.2-setting-up-an-experiment"></a>
------------------------------

1.  Following experimental design selection, the user can then select
    the desired tool for performing differential gene expression
    analysis. This will be found under `2. DGE Parameters`. Options for
    this purpose are `DESeq2`, `edgeR`, and `limma-voom`. If the user
    selects one of the main effects design options, the only options for
    DGE tools are `DESeq2` and `edgeR`:

<img src="../vignettes/img/dge-10.png" width="300px">  
2. Also under `2. DGE Parameters`, adjusted *p*-value and log-fold
change cutoffs can be specified to filter the results provided. The
default values are 0.05 for adjusted *p*-value and 1 for the minimum
log-fold change. To provide all gene comparisons, select 1 for adjusted
*p*-value cutoff and 0 for the minimum log-fold change:

<img src="../vignettes/img/dge-11.png" width="300px">  
3. Upon indication of the experimental design, DGE tool and cutoffs, the
parameters and comparisons for the specified analysis must be provided.
Such parameters can be found under `3. Experimental Parameters`.
Depending on the selected experimental design, the required parameters
and comparisons will vary:

<img src="../vignettes/img/dge-12.png" width="300px">  
4. Launching the analysis will perform the DGE analysis and provide
results. This is found under `4. Launch Analysis`. **Note:** Be mindful
that this process may take more time than previous steps. Adjusting the
cutoff values after submission will automatically update the generated
visualizations and results table:

<img src="../vignettes/img/dge-13.png" width="300px">  
  
5. If you haven't crashed your computer or our server, the main page
will now be populated with data in the two subtabs: `Overview` and
`Plots`.

1.  The `Overview` subtab (1) will display information based on the
    number of differentially expressed genes (DEGs), including a table
    of significantly up- and down-regulated gene ID counts by selected
    comparisons (2) and an interactive barplot representing this data
    (3). *With the example data, the results show only one gene is
    differentially expressed in either direction from the two-group
    comparison based on the Rootstock factor. This information seems to
    follow with the previously investigated figures showing limited
    clustering of samples from the PCA and MDS and high correlation
    values between samples:*

<img src="../vignettes/img/dge-14.png" width="300px">  
  
7. The `Plots` subtab (1) will provides interactive visualizations based
on the differential expression analysis as well as the actual results
file from the previously-selected tool based on the selected comparison.
The MA plot (2) shows the transformed log-fold change compared to the
transformed base mean for each gene ID. Specific points can be selected,
highlighting both the point and the corresponding row in the results
table found below the figure. Additionally, the gene ID can be selected
from the results table, which will highlight the location of that gene
ID on the figure:

<img src="../vignettes/img/dge-15.png" width="300px">  
  
8. The Volcano plot shows a comparison of the transformed *p*-value
compared with the transformed log-fold change. As with the MA plot, the
Volcano plot is interactively connected with the results table found
below the figure:

<img src="../vignettes/img/dge-16.png" width="300px">  
  
9. Finally, the results table is generated in coordination with the
above plots and displays the output file of the selected tool's
differential gene expression analysis. This table can be sorted
increasingly or decreasingly by any of column. The integrated search
feature also allows for specific gene IDs to be found in the table. This
results file can be exported in a filtered or unfiltered format. *With
the example data, sorting by adjusted *p*-value (padj) shows that there
are no differentially expressed genes for this specific comparison
(C3309 vs. OWN):*

<img src="../vignettes/img/dge-17.png" width="300px">  

S8: GEO Usage <a id="s8-geo-usage"></a>
=============

S8.1: Overview <a id="s8.1-overview"></a>
--------------

GEO (**G**ene **E**xpression **O**mnibus) is a public data repository
that accepts array- and high throughput sequence-based data. To submit
data to GEO, you will need three components:

-   Metadata spreadsheet
-   Processed data files
-   Raw data files

The `GEO` section of this web server will aid in the production of two
of the prior components: **metadata and processed data generation.**
This works by having the user fill out a dynamic questionnaire which
follows the template foundation located on NCBI's servers shown
[here](https://www.ncbi.nlm.nih.gov/geo/info/seq.html). While the user
fills out this form, IRIS-EDA will automatically parse your raw count
data into seperate text files based on the number of samples found in
your raw count matrix. This can be downloaded via ZIP file.
Additionally, the information provided by the column data matrix will be
used to populate several components of the metadata, including sample
information, characteristics, and [MD5 checksum
generation](https://en.wikipedia.org/wiki/MD5).

To get started, you *must* load both the raw count data and sample
information on the `Submit and QC` tab. If you do not and head directly
to the `GEO` tab, you will be greeted with a page that looks like this:

<img src="../vignettes/img/geo-series-01.png" width="300px">  
S8.2: Series <a id="s8.2-series"></a>
--------------
After you have successfully submitted your sample data
and sample information, the first section that you will need to fill out
is the **Series** section. This section describes the overall
experiment. Specifically, there are six major components:

1.  **Title**: a unique title (*less than 255 characters*) that
    describes the overall study.

2.  **Summary**: a *thorough* description of the goals and objectives of
    this study. The abstract from the associated publication may be
    suitabe. You may provide as much text here as necessary.

3.  **Overall design**: Indicate how many samples are analyzed, if
    replicates are included, are there control and/or reference Samples,
    etc.

4.  **Contributor(s)**: Who contributed to this study? You must provide
    the information in the following format
    (`Firstname,Initial,Lastname`). Examples of this format:

        * "Brandon,T,Monier"
        * "Jane,Doe"

    This component is dynamic in this framework. If there was more than
    one contributor, click the `Add Contributor` button to add as many
    individuals who aided in this endeavor.
5.  **Supplementary file**: If you want to submit your raw count matrix
    provided earlier, include the file name here (**optional**).

6.  **SRA center name code**: Only enter a value if your institute
    already has a `Center_Name` code registered with SRA. Otherwise,
    leave empty (**optional**).

S8.3: Samples <a id="s8.3-samples"></a>
-------------

This section lists and describes each of the biological Samples under
investgation, as well as any protocols that are specific to individual
Samples. Additional "processed data files" or "raw files" may be
included.

Additionally, this section is dynamically generated. The tabs that will
populate this section will be based on the number of samples you have
submitted for analysis. For example, the "small example data set" has
seven samples, therefore the number of tabs that would have to be filled
out would be seven:

<img src="../vignettes/img/geo-samples-01.png" width="300px">  
**It is mandatory that you fill out all samples.** In order for the
spreadsheet to properly be formatted, all of these sample tabs need to
be filled out. Each sample has the following criteria:

1.  **Sample name**: This will automatically be filled out for you. This
    provides an unique identifier for each sample that will not affect
    any downstream naming schemes.

2.  **Title**: A unique title that describes the sample.

3.  **Source name**: Briefly identfiy the biological material. (e.g.
    vastus lateralis muscle)

4.  **Organism**: Identify the organism(s) from which the sequences were
    derived.

5.  **Molecule**: The type of molecule that was extracted from the
    biological material. Choose from one of the preselected items from
    the dropdown input.

6.  **Description**: Additional information not provided in the other
    fields, or paste in broad descriptions that cannot be easily
    dissected into the other fields.

7.  **Processed data file**: The name of the file containing the
    processed data. **Note (1)**: This step has partially been completed
    for you. This will be the individual sample text file of raw counts.
    If you have more than one processed data file that you would like to
    contribute to GEO, click the `Add Proc. Data File` button to add as
    many entries you need.

8.  **Raw file**: The name of the file containing the raw data. Similar
    to the processed data, additional raw data can be provided by
    clicking the `Add Raw Data File` button.

**Note (2)**: If you have taken a look at the metadata template before,
you will also notice that this section contains a characteristic column.
This column is automatically generated for you based on your sample
information provided in conjuntion with your raw count matrix. For
example, the "small example data set" contains the following columns of
conditions:

-   condition
-   type

Therefore, **two** characteristics columns will be generated in the
spreadsheet. Each of the rows in these columns will based on the factor
levels for each condition.

S8.4: Protocols <a id="s8.4-protocols"></a>
---------------

This section provides the public with information about what protocols
were used to conduct this experiment. This section has the following
criteria:

1.  **Growth protocol**: Describe the conditions that were used to grow
    or maintain organisms or cells prior to extract preparation
    (**optional**).

2.  **Treatment protocol**: Describe the treatments applied to the
    biological material prior to extract preparation.

3.  **Extract prototocol**: Describe the protocols used to extract and
    prepare the material to be sequenced.

4.  **Library construction protocol**: Describe the library construction
    protocol.

5.  **Library strategy**: A Short Read Archive-specific field that
    describes the sequencing technique for this library. Choose from one
    of the preselected items from the dropdown input.

S8.5: Data processing pipeline <a id="s8.5-data-processing-pipeline"></a>
------------------------------

This section includes steps for various data processing techniques.
Base-calling, alignment, filtering, peak-calling, generation of
normalized, abundance measurements, etc.

1.  **Data processing step**: Provide details of how processed data were
    generated. This can include procedures described in the paragraph
    above. Similar to prior steps, this section is dynamic. To add more
    steps, click the `Add Data Proc. Step` butto.

2.  **Genome build**: UCSC or NCBI genome build number (e.g. hg18, mm9,
    etc.) or reference sequence used for read alignment.

3.  **Processed data files format and content**: For each processed data
    file type, provide a description of the format and content.

S8.6: Processed data files <a id="s8.6-processed-data-files"></a>
--------------------------

For each file that you provided additional processed data in the
`Samples` section, you will need to provide additional information about
these files below:

1.  **File type**: The type of processed file. Examples include, peak,
    wig, bed, gff, bigWig, etc.

2.  **MD5 file checksum**: MD5 checksum of the file. This helps GEO
    verify that the file transfer was complete and didn't corrupt your
    file.

S8.7: Raw files <a id="s8.7-raw-files"></a>
---------------

Similar to the `Processed data files` section above, for each file
listed in the "raw files" of the `Samples` section, provide additional
information about these files below:

1.  **File name**: The name of the file provided in the `Samples`
    section.

2.  **File type**: The type of processed file. Examples include, peak,
    wig, bed, gff, bigWig, etc.

3.  **MD5 file checksum**: MD5 checksum of the file. This helps GEO
    verify that the file transfer was complete and didn't corrupt your
    file.

4.  **Instrument model**: Include the instrument make and model used to
    sequence the samples. Choose from one of the preselected items from
    the dropdown input.

5.  **Read length**: The number of bases expected in each raw sequence.
    If you are using variable read length technology (e.g. 454, PacBio,
    Ion Torrent), put `0` for variable read length.

6.  **Single or paired-end**: Choose either if your samples were
    sequenced with single reads or paired-end reads. If you used SOLiD
    technology, choose `SOLiD` in the options. **This is critical for
    the final section**.

S8.8: Paired-end experiments / SOLiD data <a id="s8.8-paired-end-experiments-solid-data"></a>
-----------------------------------------

This section will only need to be filled out if your raw files used
paired-end or SOLiD-based sequencing technologies. For paired-end
experiments, list the 2 associated raw files, along with some additional
information:

1.  **File name 1**: Paired-end read 1.

2.  **File name 2**: Paired-end read 2.

3.  **Average instert size**: Average size of the insert for paired-end
    reads.

4.  **Standard deviation**: Standard deviation of insert size. This is
    typically around 10% of the insert size stated.

**Note (1)**: The previously mentioned components are for standard
paired-end read sets only. If your raw reads used SOLiD technology, this
section will may appear void of any information (see example):

<img src="../vignettes/img/geo-pair-01.png" width="300px">  
Instead of 2 reads, you will need to provide 4 (due to the basis of this
technology) In the final section before the downloads portion. Therfore,
instead of 2 "File names", You will be prompted to fill out 4; each
corresponding to their respective read.

S8.9: Downloads <a id="s8.9-downloads"></a>
---------------

After you have submitted all of your information, you can download two
items:

-   An Excel spreadsheet of the metadata;
-   A ZIP file of individual sample reads as text files.

S9: BRIC Usage <a id="s9-bric-usage"></a>
===================================

The IRIS platform can also run the BRIC clustering algorithm. This integration
is based off of the initial `C` implementation of the algorithm.

BRIC is a novel biclustering method for the detection of the repertoire of 
active gene regulatory signals(GRSs) within each single cell, based on which, 
we annotate the type and/or physiological state of each cell.

For more details, please refer to the [tutorial](http://htmlpreview.github.io/?https://github.com/zy26/BRIC/blob/master/vignette/BRIC_Rpackage.html).

To begin your analyses with BRIC, simply click on the `BRIC` tab on the upper
part of the application:

<img src="../vignettes/img/bric-01.png">

Next, you will be given a series of options and inputs. First, you can either
enter your own data or work around with an example data set.

The input to BRIC is a single-cell RNA-seq expression matrix:

* Rows correspond to genes and columns correspond to samples (cells).
* Expression units: the preferred expression values are **RPKM/FPKM/CPM**. 
* **The data file needs to be be tab delimited.**

Once data has been submitted, you can alter the values of three BRIC parameters:

* `-f` : filtering overlapping blocks
* `-k` : minimum column width of block
* `-o` : number of blocks to report

Additionally, there are two clustering options:

* [Markov Clustering](https://micans.org/mcl/)
* [Spectral Clustering](https://en.wikipedia.org/wiki/Spectral_clustering)

If you specify spectral clustering, an additional parameter will be displayed.
This is the number of cell types your data contains. **If you are using
spectral clustering, you will need to enter the correct number of cell types!**

After you have entered the parameters, click the `Run BRIC` button:

<img src="../vignettes/img/bric-02.png">

This will start the BRIC analysis. **If you have a large number of samples,
this process can take a long time! Please consider this when running BRIC.**

Once the analysis has completed, a table of predicted cell clusters will be
displayed:

<img src="../vignettes/img/bric-03.png">

These predicted cell clusters can also be downloaded as a CSV file by clicking
on the `Download Cluster Predictions` button:

<img src="../vignettes/img/bric-04.png">


S10: Using large expression matrices <a id="s10-using-large-expression-matrices"></a>
===================================

For users interested in analyzing large expression matrices, commonly
experienced in single-cell analyses, we have proposed the following
best-practices.

First, users should locally load the IRIS-EDA tool. Using the webserver
version with large datasets will frequently lead to disconnecting from
the server due to time constraints. Instructions for how to run locally
can be found in S2: Accessibility.

Second, certain functionalities may either take too long to run or will
not generate usable information. Because of this, we recommend using
only the following functionalities within IRIS-EDA for large expression
matrices:

1.  PCA

2.  MDS

3.  t-SNE

4.  biclustering with QUBIC

Users with large datasets should expect significant wait times for each
analysis, even when using the above list.

A large example dataset and corresponding condition information is available
at http://bmbl.sdstate.edu/downloadFiles/sc_example.zip.
This dataset consists of 2717 cells and the first 2000 genes from
[Klein et al. 2015](https://www.ncbi.nlm.nih.gov/pubmed/26000487).


S11: References <a id="s11-references"></a>
===============

Hardcastle TJ, Kelly KA. baySeq: empirical Bayesian methods for
identifying differential expression in sequence count data, BMC
Bioinformatics 2010;11:422

Klein AM, Mazutis L, Akartuna I, Tallapragada N, Veres A, Li V, Peshkin L,
Weitz DA, Kirschner MW. Droplet barcoding for single-cell transcriptomics
applied to embryonic stem cells. Cell 2015;161(5):1187-1201

Li J, Tibshirani R. Finding consistent patterns: a nonparametric
approach for identifying differential expression in RNA-Seq data,
Statistical methods in medical research 2013;22:519-536

Love MI, Huber W, Anders S. Moderated estimation of fold change and
dispersion for RNA-seq data with DESeq2, Genome Biol 2014;15:550

Ritchie ME, Phipson B, Wu D et al. limma powers differential expression
analyses for RNA-sequencing and microarray studies, Nucleic Acids Res
2015;43:e47-e47

Robinson MD, McCarthy DJ, Smyth GK. edgeR: a Bioconductor package for
differential expression analysis of digital gene expression data,
Bioinformatics 2010;26:139-140

Tarazona S, Garc?a F, Ferrer A et al. NOIseq: a RNA-seq differential
expression method robust for sequencing depth biases, EMBnet. journal
2012;17:pp. 18-19

Trapnell C, Roberts A, Goff L et al. Differential gene and transcript
expression analysis of RNA-seq experiments with TopHat and Cufflinks,
Nat Protoc 2012;7:562-578

Trapnell C, Hendrickson DG, Sauvageau M et al. Differential analysis of
gene regulation at transcript resolution with RNA-seq, Nat Biotechnol
2013;31:46-53

Wang L, Feng Z, Wang X et al. DEGseq: an R package for identifying
differentially expressed genes from RNA-seq data, Bioinformatics
2009;26:136-138
