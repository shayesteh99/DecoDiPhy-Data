# DecoDiPhy Data Repository

This repository contains the data and results for the DecoDiPhy paper. DecoDiPhy takes a reference tree and the average distances from a mixture of unknown queries to the reference taxa. From these, it estimates where the queries are placed on the tree and their relative abundances.

Each dataset has its own directory and its own README, which explains the details of the data and describes every file.

## Datasets

| Directory | Description | Figures |
|-----------|-------------|---------|
| [`biotrees/`](biotrees/README.md) | Queries selected from 12 biological species trees, with distances computed with and without noise | 2b, S4 |
| [`E2_dataset/`](E2_dataset/README.md) | Queries selected from two small subtrees (T1, T2), with true, sequence-based, and krepp-based distances | 2c, S5, S6 |
| [`E3_dataset/`](E3_dataset/README.md) | Simulated metagenomic samples on the WoLv2 backbone tree under low and high novelty | 2d, S3, S7, S8 |
| [`CAMI_II_marine/`](CAMI_II_marine/README.md) | CAMI-II marine samples on a 50,752-genome backbone tree | 2e, S10 |
| [`IBD_dataset/`](IBD_dataset/README.md) | IBD metagenomic samples profiled by seven methods | 3, 4 |
| [`EMP_dataset/`](EMP_dataset/README.md) | Earth Microbiome Project samples profiled by seven methods | 3, 5 |

### [Biological trees (E1 Dataset)](biotrees/README.md)

12 published species trees with 30 to 363 taxa. For each tree, 2, 3, 5, 7, or 10 queries are pruned, with 10 replicates per setting. The query distances are given either without noise or with five increasing levels of noise. The folder includes the results of the default DecoDiPhy, three other DecoDiPhy variants, and three baseline methods.

### [E2 Dataset](E2_dataset/README.md)

Two subtrees, T1 and T2. For each subtree, 3, 5, or 10 queries are pruned, with abundances drawn from a uniform or an exponential distribution, and 5 replicates per setting. DecoDiPhy runs on five types of query distances: true distances, sequence-based estimates under the JC and F81 models, and distances derived from krepp placements and multi-placements.

### [E3 Dataset](E3_dataset/README.md)

Simulated samples placed on the WoLv2 backbone tree (15,953 taxa), at three complexity levels (100, 1,000, and 10,000 draws) and two novelty conditions. The sample IDs follow the original study. The folder includes the placements of DecoDiPhy, krepp, sylph, and Woltka.

### [CAMI-II marine](CAMI_II_marine/README.md)

The 10 samples of the CAMI-II marine dataset, analyzed on a 50,752-genome backbone tree that is split into 32 subtrees. The folder includes DecoDiPhy and krepp placements and taxonomic profiles, with abundances given both raw and corrected for genome length.

### [IBD](IBD_dataset/README.md) and [EMP](EMP_dataset/README.md)

Real metagenomic samples from an inflammatory bowel disease study ([https://doi.org/10.1038/s41564-018-0306-4](https://doi.org/10.1038/s41564-018-0306-4)) and from the Earth Microbiome Project ([https://doi.org/10.1038/s41564-022-01266-x](https://doi.org/10.1038/s41564-022-01266-x)). Each sample is profiled by DecoDiPhy, krepp, Woltka, sylph, sourmash, Kraken, and Bracken. The folders include per-sample placements and combined BIOM feature tables: abundance tables for the alpha and beta diversity analyses, and read-count tables for the differential abundance analyses.
