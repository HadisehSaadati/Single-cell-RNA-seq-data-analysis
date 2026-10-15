# Overview

This project implements a single-cell RNA sequencing (scRNA-seq) analysis workflow in Python using Scanpy. The notebook processes gene expression data from a 10x Genomics HDF5 file and applies standard single-cell analysis techniques to explore cellular heterogeneity and identify cell populations.

The workflow covers data quality control, normalization, highly variable gene selection, dimensionality reduction, graph-based clustering, cell-type annotation, and marker gene visualization.

# Objectives

- [x] Perform quality control and filtering of single-cell gene expression data.
- [x] Normalize gene expression measurements and identify highly variable genes.
- [x] Reduce data dimensionality using Principal Component Analysis (PCA).
- [x] Identify cell populations using graph-based clustering.
- [x] Visualize cell clusters and their relationships using Uniform Manifold Approximation and Projection (UMAP).
- [x] Explore marker genes to support cell-type annotation and characterize cellular populations.

# Analysis Workflow

## 1. Data Loading

Load the gene expression matrix from a 10x Genomics HDF5 file and ensure that gene names are unique.

## 2. Quality Control and Filtering

Calculate quality control metrics, including:

- Number of genes detected per cell.
- Total counts per cell.
- Percentage of counts attributed to mitochondrial genes.

Apply filtering criteria to remove cells outside the selected gene-count range and cells with a high percentage of mitochondrial counts. Genes detected in fewer than three cells are also filtered out.

## 3. Normalization

Normalize total counts per cell to a target sum of 10,000, followed by logarithmic transformation using log1p.

## 4. Highly Variable Gene Selection

Identify highly variable genes to focus subsequent analysis on genes that capture meaningful variation across cells. The notebook selects up to 2,000 genes using Scanpy's highly variable gene selection method.

## 5. Scaling

Scale gene expression values and cap extreme values to improve their suitability for downstream dimensionality reduction.

## 6.Dimensionality Reduction

Perform PCA to represent gene expression variation in a lower-dimensional space and examine the variance explained by principal components.

## 7. Clustering

Construct a neighborhood graph using the PCA representation and apply the Leiden algorithm to identify groups of transcriptionally similar cells.

## 8. UMAP

Generate a two-dimensional UMAP embedding to visualize the resulting clusters and explore the structure of the cellular populations.

## 9. Gene Identification

Rank genes associated with each Leiden cluster using the Wilcoxon rank-sum test. Visualize the top-ranked genes to explore differences in gene expression between clusters.

## 10. Cell-type Annotation and Visualization

Assign descriptive cell-type labels to clusters and visualize their distribution using UMAP. Generate feature plots for selected marker genes and a heatmap to compare expression patterns across annotated populations.

The notebook includes the following marker genes:

- **CD3D**: T-cell-associated marker
- **CD14**: Monocyte-associated marker
- **MS4A1**: B-cell-associated marker
- **NKG7**: Natural killer cell-associated marker

  Additional genes, including ***IL32***, ***LTB***, ***LYZ***, and ***PPBP***, are included in the heatmap analysis.

  # *Tools*

  - **Python** — Programming language
  - **Scanpy** — Single-cell RNA-seq analysis
  - **AnnData** — Representation and management of annotated expression matrices
  - **NumPy and pandas** — Numerical operations and data manipulation
  - **Matplotlib** — Data visualization
  - **igraph and leidenalg** — Graph-based clustering
 
# Outputs

- Quality control violin plots
- Highly variable gene plots
- PCA visualizations and explained-variance plots
- Leiden cluster assignments
- UMAP cluster visualizations
- Ranked marker gene plots
- Marker gene feature plots
- A gene expression heatmap across annotated cell populations

