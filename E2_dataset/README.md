# E2 Dataset (Figure 2c, Figure S5, and Figure S6)

This dataset is simulated from two subtrees, T1 and T2 (described in the paper). For each subtree, we prune `[k]` taxa and treat them as queries with abundances drawn from a uniform or an exponential distribution. DecoDiPhy takes the pruned subtree and the average query distances to the remaining taxa, and estimates the query placements and abundances. We compare five ways of obtaining those distances: the true distances, two sequence-based distance estimates, and two estimates derived from krepp placements.

The data is organized as `E2_dataset/tree_[t]_k[k]_s[s]_[u]/[method]/`. The placeholders mean the following:

* `[t]` is the subtree: `15` is T1 and `17` is T2 in the paper.
* `[k]` is the number of queries, one of `{3, 5, 10}`.
* `[s]` is the random seed, `1`–`5`.
* `[u]` is the distribution used to draw the abundances: `uniform` or `exp` (exponential).
* `[method]` is how the query distances given to DecoDiPhy were obtained. Its possible values are:
  * `true_distances`: true distances.
  * `sequence_distances_JC`: distances estimated from sequences under the JC model.
  * `sequence_distances_F81`: distances estimated from sequences under the F81 model.
  * `krepp_placements`: distances derived from krepp placements.
  * `krepp_multiplacements`: distances derived from krepp multi-placements.

Here is the description of each file in this directory:

* `E2_dataset/tree_[t].trees`: Original subtree before pruning any queries (T1 for `[t]=15`, T2 for `[t]=17`).
* `E2_dataset/tree_[t]_k[k]_s[s]_[u]/true_queries.txt`: True placement edges and abundances of the queries.
* `E2_dataset/tree_[t]_k[k]_s[s]_[u]/pruned_tree.trees`: Subtree after pruning the queries. This file is an input to DecoDiPhy.
* `E2_dataset/tree_[t]_k[k]_s[s]_[u]/[method]/distances.txt`: Average distance from the queries to every taxon, either true or estimated by `[method]`. This file is an input to DecoDiPhy.
* `E2_dataset/tree_[t]_k[k]_s[s]_[u]/[method]/all_rounds.json`: Output of DecoDiPhy on the distances from `[method]`, including the output of each round.
* `E2_dataset/tree_[t]_k[k]_s[s]_[u]/[method]/log.txt`: Log file of DecoDiPhy on the distances from `[method]`, including running time details.
* `E2_dataset/tree_[t]_k[k]_s[s]_[u]/[method]/metrics.txt`: Metrics that compare the output of DecoDiPhy on the distances from `[method]` to the ground truth. See the column list below.

The columns of every `metrics.txt` file are, in order:

1. Jaccard
2. UniFrac
3. Weighted UniFrac
4. Estimated number of queries
5. Wasserstein distance
6. Bray–Curtis dissimilarity
