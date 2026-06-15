---
Title: Assignment 1
Course: Network Science - CS-7280-O01
Points: 100
Available: 25 May 2026, 7:00 – 11 Jun 2026, 7:00
Due: 8 Jun 2026, 7:00
Submission: External tool (Gradescope)
---

# Assignment 1

Download: [assignment_1.zip](https://gatech.instructure.com/courses/552990/files/74400443/download?download_frd=1)

In the zip file above you will find:

- **A1.ipynb**: a Jupyter notebook (.ipynb) file
- **data/**: a directory called 'data' with one or more files

## Instructions

To complete this assignment, follow the steps below:

1. Extract the contents into a local working directory (which we'll refer to as LWD) on your machine.
2. Open your Conda CLI and navigate to your LWD.
3. Open Jupyter from the Conda CLI (a Jupyter interface should open in your default browser).
4. Within the Jupyter interface, open the Jupyter notebook (.ipynb) file and follow the instructions provided there. **Instructions about environment setup will be included in the notebook and must be strictly followed to run appropriately in Gradescope.**
5. **When you have completed all the work possible/desired:**
   - **Delete any cells that you added that were not already part of the notebook (such as testing cells). Additionally, remove any print statements that were not already part of the notebook or ones you weren't instructed to include in your implementation. Extra cells and print statements can sometimes trip up the autograder in Gradescope.**
   - **Run and rerun your entire notebook several times to make sure that there are no fatal errors such as improper syntax, etc.**
   - **Make sure that your entire notebook runs in a reasonable amount of time (Gradescope has a 10 minute maximum so ideally you should aim for a faster runtime locally) and avoids excessive memory usage (submissions that exceed Gradescope's memory limit can fail to run or will receive deductions).**
6. When you have completed all the notebook instructions:
   - Save a copy of the notebook as `X-A1.ipynb`, where X is your Georgia Tech username (for example, George Burdell would submit a file named `gburdell123-A1.ipynb`).
   - Submit **only your notebook** to Assignment 1 in Gradescope.
   - Ensure that your notebook runs properly in Gradescope. A visible test case will indicate whether your submission was successfully executed and graded. Please note that a successful run does **not** imply that your code is free of errors.
   - By default, Gradescope will activate the latest submission to be graded. **If you would like some other submission to be used in grading, make sure it is activated.**
7. Please note the following while working on the assignment:
   - **There are unlimited submissions.**
   - **Local testing is strongly encouraged. Sanity checks are included for some parts of the assignment.**
   - **Do not modify imports, metatags, and provided utility functions as this can cause further issues with our autograder in Gradescope.**

## Submission

Please save a copy of the notebook as `X-A1.ipynb`, where X is your Georgia Tech username (for example, George Burdell would submit a file named `gburdell123-A1.ipynb`), and upload the file to Assignment 1 on Gradescope.

## Notebook Structure

The following part breakdown, point values, and function signatures are sourced from `A1.ipynb`, not the Canvas assignment page.

All code must be written between the `####IMPLEMENTATION STARTS HERE####` and `####IMPLEMENTATION ENDS HERE####` markers. Do not add additional cells; remove any helper/testing functions before submitting.

### Part 1 — [20 pts] Getting Started with NetworkX (US cities network)

- **1.1 [6 pts] Creating graphs with certain properties** — `graphs_with_certain_props()`
- **1.2 [4 pts] Relationship between algebraic features of a graph** — `max_degree(G)`, `avg_degree(G)`, `leading_eigenvalue(G)`, `algebraic_comparison()`
- **1.3 [2 pts] Loading graph data from a graphml file and checking it** — `load_cities_data()`
- **1.4 [3 pts] Weighted graphs** — `get_edge_weight(G, e)`, `dist_from_YOH_to_WSNC()`, `num_cities_within_50()`
- **1.5 [5 pts] Generating subgraphs according to certain conditions** — `subgraph_cities_within_100_of(city_list)`

### Part 2 — [20 pts] Walks and Paths (Les Misérables character network)

- **2.1 [2 pts] Loading the data into a graph** — `load_lesmis_data()`
- **2.2 [2 pts] Checking connectedness** — `graph_is_connected(G)`
- **2.3 [6 pts] Analyzing a network using shortest path lengths** — `shortest_path_dict(G)`, `average_shortest_path_length(G)`, `maximum_shortest_path_length(G)`
- **2.4 [4 pts] Random walks (probability)** — `prob_dict(G)`, `get_random_next_node(G, source_node)`, `random_walk(G, source_node, walk_length)`
- **2.5 [6 pts] Stationary distribution (linear algebra)** — `get_lesmis_P()`, `get_an_eigenvector_of_1(M)`, `top_three_lesmis_chars()`

### Part 3 — [20 pts] Connectedness in Directed Graphs (Biological neural network)

- **3.1 [2 pts] Loading graph data from a graphml file and checking it** — `load_drosophila_medulla_data()`
- **3.2 [6 pts] Weakly connected components** — `weak_connectedness(G)`
- **3.3 [6 pts] Strongly connected components** — `strong_connectedness(G)`
- **3.4 [6 pts] Weak connectedness vs strong connectedness** — `ratios_strong_over_weak(G)`

### Part 4 — [20 pts] Topological Ordering (Programming languages network)

- **4.1 [2 pts] Loading graph data from a txt (edgelist) file** — `load_language_data()`
- **4.2 [2 pts] Directed acyclic graph (DAG)** — `is_graph_dag(G)`
- **4.3 [6 pts] Topological generations of a DAG** — `top_gen_dicts(G)`
- **4.4 [4 pts] Topological ordering of nodes in a DAG** — `a_topological_ordering(G)`
- **4.5 [6 pts] Start nodes and highest total influence** — `start_nodes(G)`

### Part 5 — [20 pts] Bipartite Graphs and Projections (Github network)

- **5.1 [2 pts] Checking if a graph is bipartite** — `is_graph_bipartite(G)`
- **5.2 [6 pts] Loading graph data from a txt (edgelist) file** — `load_github_data()`
- **5.3 [2 pts] Biadjacency matrix of a bipartite graph** — `get_biadjacency_matrix(G, row_nodes, column_nodes)`
- **5.4 [4 pts] Matrix products** — `sparse_array_products(B)`
- **5.5 [6 pts] One mode projections and greatest commonality** — `greatest_github_commonality()`
