# E3 Dataset (Figure 2d, Figure S3, Figure S7, and Figure S8)

This dataset contains simulated samples placed on the WoLv2 backbone tree. Each sample is a set of query genomes with abundances. We compare the placements estimated by DecoDiPhy, krepp, sylph, and Woltka. DecoDiPhy uses the krepp placements as input. Samples are simulated under two novelty conditions (low and high) and three complexity levels.

The data is organized as `E3_dataset/[novelty]/n[n]/[sample]/`. The placeholders mean the following:

* `[novelty]` is the novelty condition: `low` or `high`.
* `[n]` is the complexity (number of draws), one of `{100, 1000, 10000}`.
* `[sample]` is the sample ID. It matches the original sample IDs from <https://doi.org/10.1128/msystems.00167-22>.
* `[method]` is the method that produced the placements. Its possible values are:
  * `DecoDiPhy`
  * `krepp`
  * `sylph` (low novelty only)
  * `Woltka`

Here is the description of each file in this directory:

* `E3_dataset/backbone-WoLv2.nwk`: Backbone tree with 15,953 taxa, from <https://doi.org/10.1038/s41587-023-01868-8>.
* `E3_dataset/[novelty]/n[n]/[sample]/query.txt`: True queries and their abundances.
* `E3_dataset/low/n[n]/[sample]/removed.txt`: List of taxa pruned from the backbone tree, which is a subset of the true queries. This file exists for the low novelty condition only.
* `E3_dataset/[novelty]/n[n]/[sample]/[method]_placements.txt`: Placements output by `[method]`. `DecoDiPhy_placements.txt` is computed using `krepp_placements.txt` as input. `sylph_placements.txt` is available for the low novelty condition only.
