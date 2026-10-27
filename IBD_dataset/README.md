# IBD Dataset (Figure 3 and Figure 4)

This dataset contains the results of profiling metagenomic samples from an inflammatory bowel disease (IBD) study ([https://doi.org/10.1038/s41564-018-0306-4](https://doi.org/10.1038/s41564-018-0306-4)) with DecoDiPhy and six other methods. For each method, we provide the per-sample placements and read counts, and the combined feature tables used in the alpha diversity, beta diversity, and differential abundance analyses.

The data is organized as `IBD_dataset/[method]_results/`. The placeholders mean the following:

* `[sample]` is the sample ID.
* `[method]` is the profiling method. Its possible values are:
  * `DecoDiPhy`
  * `krepp`
  * `Woltka`
  * `sylph`
  * `sourmash`
  * `Kraken`
  * `Bracken`

Here is the description of each file in this directory:

* `IBD_dataset/[method]_results/[sample].txt`: Placements output by `[method]` for sample `[sample]`, with the number of reads assigned to each placement.
* `IBD_dataset/feature-table_[method].biom`: Feature table of `[method]` combining all samples, in BIOM format. Entries are abundances. These tables are used in the alpha and beta diversity analyses.
* `IBD_dataset/feature-table_[method]_count.biom`: Feature table of `[method]` combining all samples, in BIOM format. Entries are read counts. These tables are used in the differential abundance analyses.
