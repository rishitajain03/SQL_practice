# Gene Expression Explorer

A small bioinformatics data-analysis project combining **SQL and Python** to explore gene expression differences between control and disease samples.

## Project Overview

This project demonstrates how a biological dataset can be organized in a relational database, analyzed using SQL, and visualized using Python.

The analysis focuses on comparing average gene expression between control and disease samples and calculating disease/control fold changes.

## Tools & Technologies

* **SQLite** — relational database
* **SQL** — data querying and analysis
* **Python** — data analysis and visualization
* **pandas** — data manipulation
* **matplotlib** — visualization
* **Jupyter Notebook** — analysis environment

## Dataset

The project uses a small illustrative gene-expression dataset containing:

* 10 genes
* 3 samples
* 1 control sample
* 2 disease samples

The dataset includes a deliberately missing expression value to demonstrate appropriate handling of `NULL` values.

## Database Design

The original dataset was normalized into three related tables:

```text
genes
├── gene_id
└── gene_name

samples
├── sample_id
└── condition

expression
├── gene_id
├── sample_id
└── expression
```

The `expression` table uses a composite primary key consisting of `gene_id` and `sample_id`.

## SQL Analysis

The project uses SQL to perform:

* Table creation and data insertion
* Primary and foreign keys
* SQL JOINs
* Filtering with `WHERE`
* Aggregation with `GROUP BY`
* Filtering aggregated results with `HAVING`
* Conditional aggregation using `CASE WHEN`
* Missing-value handling with `NULL`
* Common Table Expressions (CTEs)
* Subqueries
* Window functions
* Ranking with `RANK()`
* Disease/control average expression calculations
* Fold-change calculations

### Fold Change

For each gene:

```text
Fold Change = Disease Average / Control Average
```

Genes with fewer than two available disease measurements were excluded from the final comparison.

## Python Analysis

The SQL results were exported to CSV and analyzed using pandas.

Visualizations include:

1. Average expression in control vs disease samples
2. Disease/control fold change for each gene

## Key Findings

CDK2 showed the highest disease/control fold change among the genes passing the filtering criterion in this illustrative dataset.

PTEN showed lower average expression in disease samples compared with control.

EGFR contained a missing disease measurement, which was represented as `NULL` rather than zero and excluded appropriately from the relevant average and count calculations.

## Limitations

This is a small illustrative dataset created for learning SQL and Python rather than for drawing biological conclusions.

The dataset is too small for robust statistical inference and does not include the experimental design, biological replicates, normalization procedures, or statistical testing required for a real RNA-seq differential-expression analysis.

Therefore, the fold changes reported here should be interpreted as descriptive measurements rather than evidence of statistically significant differential expression.

A real RNA-seq analysis would require appropriate quality control, normalization, replicate-aware statistical analysis, and specialized tools such as DESeq2 or edgeR.

## Project Structure

```text
gene-expression-explorer/
│
├── Gene_Expression_Explorer.ipynb
├── gene_results.csv
└── README.md
```

## Learning Objectives

This project was created to build practical experience with:

* Relational databases
* SQL for biological data
* Data cleaning and missing-value handling
* Basic gene-expression analysis
* Python/pandas
* Data visualization
* Communicating bioinformatics results

