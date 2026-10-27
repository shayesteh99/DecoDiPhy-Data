# Biological Trees Dataset (Figure 1b and Figure S4)

This dataset is simulated from 12 biological species trees, listed in the table below. For each species tree, we prune `[k]` taxa and treat them as queries with assigned abundances. DecoDiPhy takes the pruned tree and the average query distances to the remaining taxa, and estimates the query placements and abundances. We run each setting with and without noise added to the distances.

| Dataset | Group | Publication | n | Comments |
|---------|-------|-------------|---|----------|
| [bees-bosseret](bees-bosseret/species_tree.tre) | bees | <https://doi.org/10.1093/sysbio/syaa097> | 30 | CASTLES-Pro on the ASTRAL tree from <https://doi.org/10.5061/dryad.z08kprrb6>, available at <https://github.com/ytabatabaee/CASTLES-Pro-paper/tree/main/data/biological/bees> |
| [mammals-song](mammals-song/species_tree.tre) | mammals (Song) | <https://doi.org/10.1073/pnas.1211733109> | 36 | CASTLES-Pro, available at <https://github.com/ytabatabaee/CASTLES-Pro-paper/tree/main/data/biological/mammals> |
| [birds-jarvis](birds-jarvis/species_tree.tre) | birds (Jarvis) | <https://doi.org/10.1126/science.1253451> | 48 | The `TENT.RAxML-GAMMA` tree |
| [tilapia-Ciezarek](tilapia-Ciezarek/species_tree.tre) | tilapia | <https://doi.org/10.1093/molbev/msae116> | 91 | `Mzeb_nc_iqtree.min4.phy.treefile` from <https://doi.org/10.5061/dryad.p2ngf1w0c> |
| [1kp](1kp/species_tree.tre) | plants (1kp pilot) | <https://doi.org/10.1073/pnas.1323926111> | 103 | The `FNA2AA.trim50genes50sites.no3rd.partitioned.gamma.final.tre` tree |
| [pancrustacean-Bernot](pancrustacean-Bernot/species_tree.tre) | Pancrustacea | <https://doi.org/10.1093/molbev/msad175> | 105 | `Fig2A_Dataset2_C60LG.tre` from <https://doi.org/10.5061/dryad.dr7sqvb2h> |
| [beetles-Johnson](beetles-Johnson/species_tree.tre) | beetles | <https://doi.org/10.1016/j.ympev.2018.05.028> | 127 | |
| [fish-Troyer](fish-Troyer/species_tree.tre) | fish (marine) | <https://doi.org/10.1073/pnas.2122486119> | 152 | `SI_Dataset_S6_IQTREE_Best_partition_scheme.part.contree.tre` from <https://datadryad.org/stash/dataset/doi:10.5061/dryad.z34tmpgfw> |
| [hemipteroid-johnson](hemipteroid-johnson/species_tree.tre) | hemipteroid insects | <https://doi.org/10.1073/pnas.1815820115> | 193 | `Supplementary_Archive_4_phylogenies_bootstraps/ML_tree_inference_nucleotide_12/bestTreeWithSupport.newick` from <https://doi.org/10.5061/dryad.t4f4g85> |
| [mammals-foley](mammals-foley/species_tree.tre) | mammals (Foley) | <https://doi.org/10.1126/science.abl8189> | 241 | |
| [fish_hughes](fish_hughes/species_tree.tre) | fish | <https://doi.org/10.1073/pnas.1719358115> | 305 | `1105_protein_ExaBayes.tre` from <https://datadryad.org/stash/dataset/doi:10.5061/dryad.5b85783> |
| [birds-stiller](birds-stiller/species_tree.tre) | birds (Stiller) | <https://doi.org/10.1038/s41586-024-07323-1> | 363 | CASTLES-Pro on the original ASTRAL tree, available at <https://github.com/ytabatabaee/CASTLES-Pro-paper/tree/main/data/biological/birds-stiller> |

`n` is the number of taxa in the full species tree.

The data is organized in two ways. Noise-free replicates are stored as `biotrees/[d]/k[k]_s[s]_noise0/`. Noisy replicates are stored as `biotrees/[d]/k[k]_s[s]_noise1_e[e]/`. The placeholders mean the following:

* `[d]` is the dataset name, taken from the first column of the table above.
* `[k]` is the number of queries, one of `{2, 3, 5, 7, 10}`.
* `[s]` is the random seed, `1`–`10`.
* `[e]` is the noise level, `1`–`5`. Higher values mean noisier distances.
* `[method]` is the version of DecoDiPhy or the baseline method, named as in Figure 1b and Figure S4. Its possible values are:
  * `default`: DecoDiPhy with default settings.
  * `exact-exact`, `exact-heu`, `heu-heu`: other DecoDiPhy variants.
  * `k_nearest`, `iterative_k_nearest`, `reverse_search`: baseline methods.

Here is the description of each file in this directory:

* `biotrees/[d]/species_tree.tre`: Rooted species tree with branch lengths in substitution units.
* `biotrees/[d]/k[k]_s[s]_noise0/true_queries.txt`: True placement edges and abundances of the queries.
* `biotrees/[d]/k[k]_s[s]_noise0/pruned_tree.trees`: Species tree after pruning the queries. This file is an input to DecoDiPhy.
* `biotrees/[d]/k[k]_s[s]_noise0/distances.txt`: Average distance from the queries to every remaining taxon in `pruned_tree.trees`. This file is an input to DecoDiPhy.
* `biotrees/[d]/k[k]_s[s]_noise1_e[e]/true_queries.txt`: True placement edges and abundances of the queries.
* `biotrees/[d]/k[k]_s[s]_noise1_e[e]/pruned_tree.trees`: Species tree after pruning the queries. This file is an input to DecoDiPhy.
* `biotrees/[d]/k[k]_s[s]_noise1_e[e]/distances.txt`: Average distance from the queries to every remaining taxon in `pruned_tree.trees`, with noise of level `[e]` added. This file is an input to DecoDiPhy.
* `biotrees/[d]/k[k]_s[s]_noise0/[method]/all_rounds.json`: Output of `[method]` on the noise-free input, including the output of each round.
* `biotrees/[d]/k[k]_s[s]_noise0/[method]/log.txt`: Log file of `[method]` on the noise-free input, including running time details.
* `biotrees/[d]/k[k]_s[s]_noise0/[method]/metrics.txt`: Metrics that compare the output of `[method]` on the noise-free input to the ground truth. See the column list below.
* `biotrees/[d]/k[k]_s[s]_noise1_e[e]/[method]/all_rounds.json`: Output of `[method]` on the noisy input, including the output of each round.
* `biotrees/[d]/k[k]_s[s]_noise1_e[e]/[method]/log.txt`: Log file of `[method]` on the noisy input, including running time details.
* `biotrees/[d]/k[k]_s[s]_noise1_e[e]/[method]/metrics.txt`: Metrics that compare the output of `[method]` on the noisy input to the ground truth. See the column list below.

The columns of every `metrics.txt` file are, in order:

1. Jaccard
2. UniFrac
3. Weighted UniFrac
4. Estimated number of queries
5. Wasserstein distance
6. Bray–Curtis dissimilarity
