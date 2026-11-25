1. `T3_T4.ipynb`: data, exact PageRank and in-degree baseline (tasks T3–T4).
   - downloads `wiki-topcats` from SNAP;
   - extracts two topic graphs: science and technology (training) and geography (second graph);
   - describes both graphs (statistics, degree distributions);
   - computes the exact PageRank and the target y = log(N · PageRank), and checks them;
   - splits the training nodes into train/val/test (70/15/15);
   - fits and evaluates the in-degree baseline;
   - builds perturbed copies of the training graph (1, 5, 10 and 20% of the links changed).
   - 
   Output: the node and edge tables, the category lists and the metrics in `data/`, and the plots in `figures/`.
   
