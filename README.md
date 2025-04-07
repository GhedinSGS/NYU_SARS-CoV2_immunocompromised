<h1> Longitudinal analyses of the respiratory microbiome in ventilated COVID-19 patients reveals dysbiosis in the immunocompromised</h1>


Matthew Chung<sup>1</sup>, Clea R. Barnett<sup>2,3</sup>, Lars Hunger<sup>4</sup>, Imran Sulaiman<sup>2,3</sup>, Benjamin G. Wu<sup>2,3,5</sup>, Yonghua Li<sup>2,3</sup>, Jun-Chieh J. Tsay<sup>2,3,5</sup>, James T. Morton<sup>4</sup>, Leopoldo N. Segal<sup>2,3,5,6</sup>, Elodie Ghedin<sup>1</sup>

<p>The project assesses the metatranscriptomes of individuals with SARS-CoV2 at NYU Langone Health monitored longitudinally across 3+ weeks. Samples were compared to identify key microbiomes dynamics linked to poor clinical outcome or immunosuppression.</p>

**For more information please contact**: [elodie.ghedin@nih.gov](mailto:elodie.ghedin@nih.gov)

---

## Table of Contents

<!-- MarkdownTOC autolink="true" levels="1,2,3,4" -->

- [Overview](#overview)
- [Data](#data)
- [Analysis](#analysis)

<!-- /MarkdownTOC -->

---

## Overview

This repository contains files and figures for recreating the manuscript analysis:

- `/data`: Includes output tables used to run the analysis
- `/scripts`: Scripts used for downstream analysis
- `/figures`: PDFs of manuscript figures

---

## Data

The following tables are included in /data and were used as inputs for downstream analyses:

1. Samples were sequenced across a pilot run and 3 separate runs. Each run contains:
	- `counts.taxa.bracken.tsv`: taxa counts quantified using Kraken2 and Bracken
	- `annotation.taxa.bracken.tsv`: taxonomic information for each of the identified taxa

2. Additionally, the dataset as a whole was quantified for functional annotations and antimicrobial resistance categories using the databases:
	- `counts.coverM.CARD.tsv`: antmicrobial resistances quantified against the CARD database using coverM
	- `counts.coverM.MEGARes.tsv`: antmicrobial resistances quantified against the MEGARes database using coverM
	- `counts.ko.module.fmap.tsv`: KEGG orthology terms quantified at the module level using FMAP
	- `counts.ko.ortho.fmap.tsv`: KEGG orthology terms quantified at the ortholog level using FMAP
	- `counts.ko.pathway.fmap.tsv`: KEGG orthology terms quantified at the pathway level using FMAP
	- `counts.ko.pathway_metabolism.fmap.tsv`: KEGG orthology terms quantified at the pathway level for only metabolism terms using FMAP

3. Metadata for the cohort:
	- `w1to3_smpl_metadatamapping_covidpos_intub_imsupp_sequenced_v2.xlsx`
	- `w1to3_smpl_metadatamapping_covidpos_intub_notimsupp_sequenced_v2.xlsx`

---

## Analysis

Analyses were conducted post-quantification using Bracken, FMAP or coverM using R scripts:

- **Upstream**
	- `upstream_v3.Rmd`: Upstream processing of taxonomic counts, metadata, and annotation files to create R object for downstream analyses
	- `upstream_for_amr_and_ko.Rmd`: Upstream processing of functional counts and metadata to create R object for downstream analyses

- **Downstream**
	- `decontam_and_top_taxa_v2.Rmd`: Identifies top taxa across the dataset along with potential contaminant taxa in the data
	- `cluster_v3.Rmd`: Runs diversity and clustering analyses
	- `de_analysis_v2.Rmd`: Runs differential abundance analyses between samples based on clinical outcome and immunosuppression status
	- `netcomi.Rmd`: Runs comparative network analysis
	- `mupi_upstream.Rmd`: Processes mupirocin counts data
	- `mupi_analysis.Rmd`: Conducts differential abundance and taxonomic analyses for mupirocin analysis

---