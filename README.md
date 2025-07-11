
<!-- README.md is generated from README.Rmd. Please edit that file -->

=========================================================

<!-- badges: start -->

[![License CC BY
4.0](https://img.shields.io/badge/License-CC%20BY%204.0-green.svg)](https://creativecommons.org/licenses/by/4.0/)
![Lifecycle
Experimental](https://img.shields.io/badge/Lifecycle-Experimental-339999)
<!-- badges: end -->

<p align="left">

• <a href="#overview">Overview</a><br>  
• <a href="#description">Description</a><br> •
<a href="#get-started">Get started</a><br> •
<a href="#contributing">Contributing</a><br> •
<a href="#citation">Citation</a><br> •
<a href="#acknowledgments">Acknowledgments</a><br> •
<a href="#references">References</a>
</p>

## Overview

This repository is a bank centralizing metadata files describing various
published trait databases.

Its content (folder `metadata/`) is used by the R package
[`traitdatabases`](https://github.com/frbcesab/traitdatabases) to
download, import, clean, and homogenize trait data.

## Description

The metadata file describe all information needed to document and
process the trait database.

| name | description | example |
|----|----|----|
| status | Status of the metadata file. One of ‘draft’, ‘incomplete’ or ‘complete’ | draft |
| id | Dataset identifier. | hodgson_2023 |
| title | Dataset title | .dataset_title |
| description | Short description of the dataset | .description |
| license | Dataset license | CC BY-SA 4.0 |
| bibtex | Name of the dataset citation file in a bibtex format (if any) | hodgson_2023.bib |
| doi | DOI of the dataset description (paper) | 10.5287/ora-pp4y9nkoz |
| url | URL of the dataset description (paper) |  |
| taxon | Taxonomic group (mammals, birds, etc.) | plants |
| taxonomic_level | Taxonomic resolution (species, genus, etc.) | species |
| type | One of ‘static’ or ‘api’ | static |
| file_url | Full URL to download the static file |  |
| file_name | Name of the static file |  |
| file_extension | File extension of the static file | .xlsx |
| manual_download | Need manuel download? One of ‘yes’ or ‘no’ | no |
| sheet | Sheet number for xslx dataset | 1 |
| long_format | Format of the trait database. One of ‘yes’ (long) or ‘no’ (wide, most commun) | no |
| skip_rows | Number of header rows to remove | .na |
| col_separator | Character used to separate columns (for text file or csv) | .na |
| na_value | Character used for missing values | NA |
| comment | add any relevant comment, if any |  |
|  | **Taxononomy** |  |
| genus | Column name of the genus (when binomial name not available) | .na |
| species | Column name of the species (when species name separated from genus) | NA |
| binomial | Column name of the binomial name | Species |

For each trait, there are five fields that are important to describe:

| name     | description                          | example            |
|----------|--------------------------------------|--------------------|
| variable | Column name of the trait             | SLA                |
| name     | Full name of the trait               | Specific leaf area |
| category | Category of the trait                | Leaf morphology    |
| type     | One of ‘quantitative’ or ‘categoric’ | quantitative       |
| units    | Original unit                        | mm2.mg-1           |

Additionally, for categorical traits, all categories should be listed
with two information (‘value’ and ‘description’). These information
describe each level of the categorical traits. For instance:

    - variable: VEGPROP      
      name: Vegetative propagation of perennials
      category: reproduction
      type: categorical      
      units: .na 
      levels: 
      - value: 1            
        description: yes
      - value: 0 
        description: no 

In excel, make sure to add a new lines for every label.

## Get started

Follow this 6-steps procedure to add a new metadata in the
`traitdatabases` package.  
Before proceeding, make sure that the dataset you want to add is not
already in `traitdatabases-metadata`.

#### 1. Fork this repository

Click on the fork icon on the top right of this folder.

<figure>
<img src="doc/figures/fork-1.png" alt="fork screenshot" />
<figcaption aria-hidden="true">fork screenshot</figcaption>
</figure>

#### 2. Install the traitdatabases package

``` r
## Install < remotes > package (if not already installed) ----
if (!requireNamespace(c("remotes", "here"), quietly = TRUE)) {
  install.packages(c("remotes", "here"))
}

## Install < traitdatabases > from GitHub ----
remotes::install_github("frbcesab/traitdatabases")
```

#### 3. Create a new empty metadata file

Choose the name of your dataset and in which format you prefer to fill
in the metadata (yaml or excel). Then use the function
`td_create_metadata_file` as follow:

``` r
traitdatabases::td_create_metadata_file(
  name = "hodgson_2023", # name of your dataset
  path = here::here("metadata"), # where to store the metadata
  format = "yaml" # either 'yaml' or 'xlsx' format
)
```

#### 4. Complete the metadata

Depending on the format, open a text editor or excel to fill in the
metadata.

It is recommended to add a bibtex file with the citation information of
the trait database in the same folder as the metadata file.

#### 5. Check and commit changes

Double check that everything is complete, without errors. Finally,
update the status of the metadata file (‘complete’, or ‘incomplete’),
stage the new files and commit the changes.

#### 6. Make a pull request

This will contribute directly to the growth of the metadata on trait
databases. Your pull request will be reviewed in the shortest delay.  
Thank you for your contribution :)

## Contributing

All types of contributions are encouraged and valued. For more
information, check out our [Contributor
Guidelines](https://github.com/frbcesab/traitdatabases/blob/main/CONTRIBUTING.md).

Please note that the `traitdatabases-metadata` project is released with
a [Contributor Code of
Conduct](https://contributor-covenant.org/version/2/1/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms.

## Citation

Please cite `traitdatabases` as:

> Casajus N, Coux C & Frelat R (2025) traitdatabases: An R package to
> compile trait databases. R package version 0.0.0.9000.
> <https://github.com/frbcesab/traitdatabases/>

## Acknowledgments

Coming soon…

<!-- Should we have automatic list of contributors that participated in one or more metadata? (e.g. Github bot?)-->

## References

Coming soon…

<!-- Should we have automatic list of metadata covered in the package?-->
