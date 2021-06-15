# Introduction

This tutorial explains how to proficiently use the GeneSeqToFamily Galaxy workflow, published in the paper Thanki et al. (2018) "GeneSeqToFamily: a Galaxy workflow to find gene families based on the Ensembl Compara GeneTrees pipeline", https://doi.org/10.1093/gigascience/giy005

## Galaxy
If you are new to Galaxy then get familiarised with Galaxy using [slides](https://training.galaxyproject.org/training-material/topics/introduction/slides/introduction.html#1) and [hands-on](https://training.galaxyproject.org/training-material/topics/introduction/tutorials/galaxy-intro-short/tutorial.html).

## GeneSeqToFamily workflow

The GeneSeqToFamily workflow can be either installed from the Galaxy ToolShed, or downloaded from https://github.com/TGAC/earlham-galaxytools/tree/master/workflows/GeneSeqToFamily and then imported into a local Galaxy or a public instance where the necessary tools are installed, e.g. [Galaxy Europe](https://usegalaxy.eu).


# Importing input data

### Hands-on: Data upload
1. Make sure you have an empty analysis history. Give it a name.
### Tip: Starting a new history
* Click the gear icon at the top of the history panel
* Select the option Create New from the menu


2. Import Sample Data
* FASTA file:  [`CDS.fasta`](https://doi.org/10.5281/zenodo.1256760)
* JSON file: [`gene.json`](https://doi.org/10.5281/zenodo.1256762)
* Species tree: [`species.nhx`](https://doi.org/10.5281/zenodo.1256753)
### Tip: Importing data via links
* Copy the link locations
* Open the Galaxy Upload Manager
* Select Paste/Fetch Data
* Paste the link into the text field
* Press Start
### Tip: Change the file type text to nhx once the data file is in your history
Click on the pencil button displayed in your data file in the history
* Choose Datatype on the top
* Select nhx
* Press save

### 
	Rename the dataset to “First dataset”

By default, when data is imported via its link, Galaxy names it with its URL.

# Data Preparation

To convert uploaded data into the format acceptable by GeneSeqToFamily workflow:

## GeneSeqToFamily preparation 
GeneSeqToFamily preparation is a Galaxy tool that converts genomic information from GFF/JSON format to SQLite format for easy access during the workflow. It can also add species information to the header line of the FASTA sequences.

### Hands-on: GeneSeqToFamily preparation : Run GeneSeqToFamily preparation on the imported GFF/JSON and FASTA files
1. GeneSeqToFamily preparation 
* Select JSON and/or GFFs files
* Add specific species name (in-case of GFFs)
* Corresponding CDS datasets in FASTA format: select all FASTA datasets
* Which transcripts to keep: Only canonical transcripts (or longest CDS per gene)
* Change the header line of the FASTA sequences to the following format: TranscriptId_species
* Comma-separated list of region IDs (e.g. chromosomes or scaffolds) for which FASTA sequences should be filtered:
* Run tool



# Running workflow

1. GeneSeqToFamily workflow 
* Select the CDS dataset generated by the GeneSeqToFamily preparation tool
* Select Gene Feature information, SQLite generated using GeneSeqToFamily preparation tool
* Select species tree, 
  * Species tree can be generated using the `ete_species_tree` generator tool
* Run the workflow


# Visualisation

## Aequatus visualisation Plugin 

The SQLite database generated by the GAFA tool can be rendered using a new visualization plugin, Aequatus.js. The Aequatus.js library, developed as part of the Aequatus project, has been configured to be used within Galaxy to visualize homologous gene structure and gene family relationships. 

### Hands-on: Aequatus visualization plugin 
1. Aequatus visualisation Plugin 
* In the history panel, expand the dataset generated by the previous step
* Choose GeneTree from side panel
* Visualise different GeneTrees



# Conclusion


Here we covered the various steps of the GeneSeqToFamily workflow. In this tutorial we used the default parameters for the workflow steps. They might need to be changed for different sources of data.