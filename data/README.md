# Data

Files produced by `notebooks/T3_T4.ipynb`. Tables are compressed CSV (`.csv.gz`), readable with `pd.read_csv(path)`.

Node ids are the original SNAP ids of `wiki-topcats` (not 0..N-1):
they must be renumbered before using the graphs in PyTorch Geometric.

## Graphs

| File | Content |
|---|---|
| `train_nodes.csv.gz`, `train_edges.csv.gz` | Training graph (science and technology): 70,365 nodes, 559,152 links |
| `second_nodes.csv.gz`, `second_edges.csv.gz` | Second graph (geography): 65,109 nodes, 256,833 links; no nodes in common with the training graph |
| `perturbed_XX_nodes.csv.gz`, `perturbed_XX_edges.csv.gz` | Training graph with XX = 01, 05, 10, 20 % of the links changed (half deleted, half added at random); same nodes, PageRank recomputed |

**Node tables**, one row per node:
- `node`: SNAP id
- `title`: article title
- `in_degree`, `out_degree`: degrees inside the graph
- `pagerank`: exact PageRank (teleport probability 0.15, tolerance 1e-10)
- `y`: target, log(N · PageRank), natural log
- `split` (training and perturbed graphs only): `train`, `val` or `test` (70/15/15, seed 42)
- `y_old` (perturbed graphs only): target in the original training graph
- `pred_baseline` (perturbed graphs only): prediction of the in-degree baseline

**Edge tables**, one row per directed link: `source`, `target`.

## Metrics

- `baseline_metrics.csv`: in-degree baseline on the train, val and test nodes of the training graph and on all the nodes of the second graph.
- `perturbed_metrics.csv`: baseline and old PageRank on the test nodes of each perturbed graph.

Metrics: Spearman correlation, MSE, top-p% overlap and NDCG@p% for p = 1, 5, 10.

## How the graphs were built

- `keywords_train.txt`, `keywords_second.txt`: keyword stems and excluded words.
- `categories_train.txt`, `categories_second.txt`: selected categories.
- `categories_train_excluded.txt`, `categories_second_excluded.txt`: categories that matched a stem but were removed by an excluded word.
