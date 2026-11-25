# Can Graph Neural Networks Learn PageRank?
### Accuracy, Generalisation and Bias on Wikipedia Networks

Final degree project (TFG), Grau en Ciència de Dades Aplicada, Universitat Oberta de Catalunya (UOC).
Author: Carlo-Romeo Andreoli Zacquini. Supervisor: Alfons Marquès i Cancio.

## Question
PageRank must be recomputed every time a network changes. This project studies whether
Graph Neural Networks (GCN, GraphSAGE, APPNP) can learn to approximate the PageRank
ranking from the graph structure, and whether they generalise to unseen nodes,
to a second graph and to perturbed copies of the training graph. The models are
compared with an in-degree baseline, and their error is audited by in-degree group.

## Data
Two topic subgraphs of `wiki-topcats` (SNAP, Wikipedia hyperlinks, 2011):
- training graph: science and technology, 70,365 articles, 559,152 links;
- second graph: geography, 65,109 articles, 256,833 links.

## Repository
- `notebooks/`: Jupyter notebooks, to run in Google Colab in order (see `notebooks/README.md`).
- `data/`: graphs, exact PageRank, split and metrics (see `data/README.md`).
- `figures/`: plots used in the report (see `figures/README.md`).
- `tfg_utils.py`: functions shared by the notebooks (loading graphs, features, metrics).

## Requirements
Google Colab with Python 3, NetworkX, pandas, scikit-learn, matplotlib,
PyTorch and PyTorch Geometric (`pip install torch_geometric`).
Exact versions are printed at the start of each notebook.
