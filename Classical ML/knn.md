# K-Nearest Neighbors (KNN) - Paper Review

## 1. Summary
K-Nearest Neighbors (KNN) is one of the most basic machine learning algorithms, used for both classification and regression tasks. Instead of learning a model during training, KNN simply stores the dataset and makes predictions by finding the 'k' closest points to a new input, using distance metrics like Euclidean distance. The main idea is pretty straightforward: points that are close together are likely to belong to the same class. 

## 2. Key Concepts
- KNN doesn’t build an explicit model — it’s a lazy learner.
- To predict a new point, it finds the 'k' nearest neighbors in the training set and takes a majority vote (for classification) or averages the outputs (for regression).
- Common distance metrics include Euclidean, Manhattan, and Minkowski distances.
- Choosing 'k' is important: a small 'k' can lead to overfitting, while a large 'k' might oversimplify things.
- The algorithm can also be weighted, meaning closer neighbors can have more influence than farther ones.

## 3. Strengths
- Very simple to understand and implement — no training time needed.
- Naturally handles multi-class problems without any special adjustments.
- It adapts well when there’s a clear local structure in the data (for example, in clustering-like patterns).
- Works well even with small datasets.

## 4. Weaknesses or Limitations
- Prediction time can be slow, especially with large datasets, because it needs to compute the distance to every point.
- Sensitive to irrelevant features and to the scaling of data (needs proper feature normalization).
- Struggles with high-dimensional data because of the "curse of dimensionality" — distances become less meaningful.
- Choosing the right 'k' and distance metric can feel a bit like guesswork without good cross-validation.

## 5. My Thoughts
KNN is one of those algorithms that may seem too simple at first, but it actually teaches a lot about how machine learning fundamentally works — thinking in terms of "closeness" and "patterns" instead of rigid rules. It's still useful in certain practical cases, especially when the dataset is small and well-structured. 
I think improvements like using KD-trees or Ball-trees to speed up neighbor searches are essential if you’re planning to apply KNN on anything bigger than a toy dataset.

## 6. Citation
Scikit-learn documentation: [https://scikit-learn.org/stable/modules/neighbors.html](https://scikit-learn.org/stable/modules/neighbors.html)
