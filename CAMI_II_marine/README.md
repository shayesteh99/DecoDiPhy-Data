# CAMI-II Marine Dataset (Figure 2e and Figure S10)

This dataset contains the 10 samples of the CAMI-II marine dataset, analyzed on a backbone tree of 50,752 genomes. The backbone tree is divided into 32 subtrees, and DecoDiPhy runs separately on each subtree, using krepp placements as input. The placements are then combined across all subtrees for each sample and converted into taxonomic profiles. Abundances are reported both raw and corrected for genome length.

The data is organized as `CAMI_II_marine/sample_[sampleID]/subtree_[t]/`. The placeholders mean the following:

* `[sampleID]` is the sample ID, `0`–`9`.
* `[t]` is the ID of the subtree of the backbone tree, `1`–`32`.
* `[method]` is the method that produced the placements: `DecoDiPhy` or `krepp`. DecoDiPhy uses the krepp placements as input.

Here is the description of each file in this directory:

* `CAMI_II_marine/backbone_tree-CAMI2_dedup-pruned.nwk`: Backbone tree with 50,752 genomes, from <https://doi.org/10.1186/s13059-026-03999-y>.
* `CAMI_II_marine/genome_sizes.txt`: Genome size of each genome in the backbone tree.
* `CAMI_II_marine/sample_[sampleID]/subtree_[t]/all_rounds.json`: Output of DecoDiPhy on subtree `[t]`, including the output of each round.
* `CAMI_II_marine/sample_[sampleID]/subtree_[t]/log.txt`: Log file of DecoDiPhy on subtree `[t]`, including running time details.
* `CAMI_II_marine/sample_[sampleID]/subtree_[t]/output.jplace`: Output of DecoDiPhy on subtree `[t]` in jplace format.
* `CAMI_II_marine/sample_[sampleID]/[method]_placements.txt`: Placements output by `[method]`, combined across all subtrees, with raw abundances.
* `CAMI_II_marine/sample_[sampleID]/[method]_placements_corected.txt`: Placements output by `[method]`, combined across all subtrees, with abundances corrected for genome length.
* `CAMI_II_marine/sample_[sampleID]/[method]_taxid.txt`: Placement edges of `[method]` with their assigned taxonomic IDs and corrected abundances. The columns are, in order:
  1. Placement edge label
  2. Kingdom taxonomic ID
  3. Phylum taxonomic ID
  4. Class taxonomic ID
  5. Order taxonomic ID
  6. Family taxonomic ID
  7. Genus taxonomic ID
  8. Species taxonomic ID
  9. Corrected abundance
* `CAMI_II_marine/[method]_results.profile`: Full taxonomic profile of `[method]` across all samples, with raw abundances.
* `CAMI_II_marine/[method]_corrected_results.profile`: Full taxonomic profile of `[method]` across all samples, with abundances corrected for genome length. These are the profiles shown in the paper.
