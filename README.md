# PageRank

> **Course:** COSC 621 Data Science · MSc, Khalifa University

Implementation of the PageRank-Iterate algorithm. The assignment was to run PageRank-Iterate, as given in the course's "Link Analysis" lecture, on a 10-page example graph with damping factor d = 0.85. Epsilon was to be chosen so the algorithm converges in a few rounds (about 5 to 20).

## Approach

- The graph is encoded as a 10 × 10 row-stochastic transition matrix `A`: row *i* splits page *i*'s weight evenly over its out-links. The graph image is embedded in the notebook.
- Starting from the uniform vector P₀ = 1/n, each round computes

  P<sub>k</sub> = (1 − d)·e + d·Aᵀ·P<sub>k−1</sub>, with e = 1/n for every page

- The loop stops when the change between rounds falls below epsilon, or after at most 20 rounds.
- Parameters: n = 10, d = 0.85, epsilon = 0.15.
- All rounds are collected into a pandas DataFrame, one column per page (`P1`–`P10`).

## Results

Saved output from the notebook:

| Round | P1 | P2 | P3 | P4 | P5 | P6 | P7 | P8 | P9 | P10 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0.1000 | 0.1000 | 0.1000 | 0.1000 | 0.1000 | 0.1000 | 0.1000 | 0.1000 | 0.1000 | 0.1000 |
| 1 | 0.1283 | 0.0858 | 0.1425 | 0.0575 | 0.1708 | 0.0150 | 0.1283 | 0.0433 | 0.1425 | 0.0858 |

After one round, page 5 has the highest score (0.1708). Page 6 has the lowest (0.0150), because no page links to it.

With epsilon = 0.15, the saved run converges after the first round.

## Project structure

```
PageRank/
├── PageRank.ipynb   # Notebook with the task, graph image, code and saved outputs
└── pagerank.py      # Python export of the notebook (from Google Colab)
```

## Getting started

Requirements: Python 3, `numpy`, `pandas` and Jupyter.

```bash
pip install numpy pandas notebook
jupyter notebook PageRank.ipynb
```

The notebook was exported from Google Colab and can also be opened there.

## Tech

Python · NumPy · pandas · Jupyter
