# Hepatic-Immune-Cell-Patterns-Code
**The script in this repository holds a sequential workflow of 6 steps**

1. SingleR reference database annotations, marker assessment of annotated cell types, and initial visualization
2. Use of reference database annotated cell type markers, marker gene-based principal component analysis (PCA), and quality control and filtering
3. Addition of custom metadata labels to rename annotated cells for visualization with dimensional reduction methods
4. Quantification of annotated cell subsets with scSorter and re-visualization of subsets
5. Functional assessment of cell types with DESeq2 to upload results to Ingenuity Pathway Analysis (IPA)
6. Investigation of intercellular communication networks with CellChat

Each set of steps do not need to be performed in this exact order, but the first three steps are critical to understand and manipulate known cell types in subsequent steps

**Required Software: R or Rstudio**

Steps 1-4 use scran, scater, Seurat, scSorter, ggplot2, patchwork, dplyr, tidyr, ggrepel, SingleR, celldex, scuttle, pheatmap, and viridis libraries

Step 5 uses ggplot2, Seurat, rhapsodykit, scuttle, tidyverse, and DESeq2 libraries (along with data.table, dplyr, and tibble libraries to export a saved reference file of barcodes and meta.data)

Step 6 uses Seurat, patchwork, and CellChat libraries (along with NMF and ggalluvial if desired for additional pattern analyses)

**Notes about script structure:**

All required packages/libraries are included in the script, with all at the top used for steps 1 to 4, whereas steps 5 and 6 have the required packages before they start; only packages involving heatmap generation and coloration for heatmaps are interspersed throughout where needed

Hash lines are used to separate steps and specific portions of steps within the code to show where they start and stop

A double hash indicates a specific note in the script providing insight or rationale for specific portions of code

A single hash or a single hash followed by an exclamation point are pieces of code that can have the hash removed to perform functions a different way, with another object, etc.

**Purpose of Steps:**

Step 1 enables access to SingleR reference databases to annotate all of our cells and visualize them; along with testing for markers of the annotated cells to use in PCA later to give a more optimized visualization

Step 2 performs the PCA of the marker genes from Step 1, then annotates all of our cells again after filtering cells with quality control measures

Step 3 lets us manipulate all annotated cell labels in the meta.data column, if we want to give different labels during visualization for example

Step 4 sorts known subsets with the scSorter algorithm coupled to a list of manually given marker genes for subsets of cells (ex. SingleR annotated macrophages sorted into M1, M2, and Kupffer cells); followed by re-visualization of immune cells and non-immune cells separately after finding subsets of interest

Step 5 performs a functional assessment of specific cell populations by using either Seurat functions or performing DESeq2 on specific cell types of interest to compare the results in IPA

Step 6 employs CellChat, which uses a manually curated database of known ligand-receptor (L-R) interactions to infer cell types that may be sending or receiving signals based on their gene expression of the L-R pairs

**Marker Genes Table Information**

The SingleR Annotated Cell Markers excel file contains marker genes of each annotated cell type and all of the ones used for PCA in the column titled "Genes for PCA"
The IC Patterns scSorter genes and PMIDs excel file contains marker genes used in scSorter to identify subsets of cells, along with any meaningful references for the use of specific markers; "GeneList# for R" column shows all of the ones used together during one run to sort subsets out of the annotated cell populations. 
