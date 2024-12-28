LINK TO MOVIE DATABASE: https://drive.google.com/file/d/1X2WAngDM85mX1tfxqh4Nv1wfyZbzfWfM/view?usp=sharing


# Comparative Analysis of Clustering and Retrieval Methods for Movie Genre Queries

## Overview

This project evaluates the effectiveness of clustering algorithms (K-means and Agglomerative Clustering) versus traditional information retrieval approaches for querying a movie dataset. Queries were tested against TF-IDF embeddings reduced with Singular Value Decomposition (SVD), and precision scores were compared across methods.

---

## Authors

- **Daniel Doyon**
- **David Margarin**

---

## Objectives

1. Analyze clustering methods (K-means and Agglomerative Clustering) for retrieving relevant movie plots based on specific queries.
2. Compare clustering results to direct information retrieval using TF-IDF and SVD.
3. Evaluate precision scores across methods to determine the optimal approach.

---

## Methods

### Preprocessing
- **Dataset:** Movie plots with genres reduced to the top 35.
- **Text Processing:** 
  - Lemmatization
  - Stop-word removal
  - TF-IDF transformation (top 5,000 terms)
- **Dimensionality Reduction:** SVD with 200 components, normalized for consistency.

### Clustering
1. **K-means Clustering:**
   - Optimal number of clusters determined using the Elbow and Silhouette Methods.
   - Final \(k = 5\).
   - Purity calculated using confusion matrices.

2. **Agglomerative Clustering:**
   - Linkage methods: Ward, Complete, and Average.
   - Distance metrics: Euclidean and Cosine.
   - Ward linkage with Euclidean distance produced the best purity score (0.2344).

3. **Purity Metrics:**
   - Purity calculated as the ratio of majority-class points to the total number of points in clusters.

### Retrieval
- **Clustering Retrieval Algorithm:**
  - Query vector mapped to reduced space.
  - Cosine distance calculated between query and cluster centroids.
  - Top 3 clusters identified for each query.
  - Points ranked based on proximity to query vector.

- **Direct Information Retrieval:**
  - Cosine and dot product similarity computed in 200 and 500 dimensions between the query vector and movie plot vectors.

---

## Results

### Clustering Precision
| Query                        | K-means Precision | Agglomerative Precision |
|------------------------------|-------------------|--------------------------|
| Inspiring Pirate Adventure   | 0.0               | 0.0                      |
| Depressing Ghost Story       | 0.2               | 0.0                      |
| Based on a True Story        | 0.0               | 0.4                      |

### Information Retrieval Precision
| Query                        | Cosine (200) | Dot Product (200) | Cosine (500) | Dot Product (500) |
|------------------------------|---------------|--------------------|---------------|--------------------|
| Inspiring Pirate Adventure   | 1.0           | 1.0                | 1.0           | 1.0                |
| Depressing Ghost Story       | 0.2           | 0.25               | 0.8           | 0.6                |
| Based on a True Story        | 0.2           | 0.4                | 0.4           | 0.4                |

---

## Key Observations

1. **Clustering Performance:**
   - K-means slightly outperformed Agglomerative Clustering for the "Depressing Ghost Story" query.
   - Agglomerative Clustering performed better for the "Based on a True Story" query.
   - Overall clustering precision was low, indicating suboptimal performance for specific queries.

2. **Information Retrieval Superiority:**
   - Direct retrieval using TF-IDF and SVD consistently outperformed clustering methods.
   - Precision scores were significantly higher across all dimensions and similarity measures.
   - Cosine similarity and dot product produced comparable results.

---

## Conclusions

- **Clustering Limitations:** Clustering methods struggled with sparse data and specific queries, resulting in low precision scores.
- **Information Retrieval Advantages:** Traditional retrieval methods were more effective for specific and adjective-rich queries, such as "Inspiring Pirate Adventure" and "Depressing Ghost Story."
- **Best Method:** Direct information retrieval using TF-IDF, SVD, and cosine similarity is recommended for tasks requiring high precision.

---

## Code and Notebooks

Detailed implementations and results are available in the accompanying `Cluster.ipynb` notebook.

---

## Questions?

For further clarification or collaboration, feel free to reach out.
