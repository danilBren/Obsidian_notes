## Support vector machine
**Support vector class**: For separable classes, the decision boundary is determined by the support vectors.
**Support vector**: data point that lies closest to the decision boundary (or hyperplane) that separates the classes. These points are crucial because they "support" or define the optimal margin between classes.
**Kernel Trick**: enables to operate in a high-dimensional feature space without explicitly computing the coordinates in that space. By using a **kernel function** to compute inner products directly, it allows for efficient computation and handling of non-linear relationships in the original data. 

![[Pasted image 20241101002719.png]]


## Decision tree
**Tree-shaped classifier**:
* In each internal node, test on an individual feature and branch
* In a leaf node, choose an output

**Splitting rules**:
* Often node purity: Split a node if the impurity can be decreased. 
![[Pasted image 20241101003000.png]]

## Bagging / Bootstrap Aggregation
![[Pasted image 20241101004210.png]]
Advantages
* Can be used to stabilize unstable classifiers (reduce variance, avoids overfitting)
* Can always be applied
* Individual classifiers can be applied in parallel
Disadvantages
* Not clear how many base classifiers to combine
* Need to train (and store) many classifiers
* For large datasets, bootstrapping may not give enough variability
## Boosting
Instead of averaging ‘independent’ classifiers, add classifiers sequentially
![[Pasted image 20241101004243.png]]
To optimize the set of base classifiers $\hat{y}_m (x)$  and their corresponding weights $\alpha_m$ is very hard; so **do it incrementally**.

Initialize all objects with an equal weight.
Randomly select a training set size $N^, < N$ according to the object weights
Train a simple/weak classifier
Increase the weights of the erroneously classified objects
Repeat as long as needed
Combine

## AdaBoost
1. Initialize all objects with an equal weight
2. Train a simple/weak classifier on weighted samples:  $\hat{y}_m$
3. Classify the entire dataset, using the weights, and get the error $\epsilon_m$
4. Define the classifier weight
![[Pasted image 20241101004836.png]]
5. Multiply weights of erroneously classified objects with $exp(-\alpha_m)$
6. Go to (2) for as long as needed

Use a simple decision stump for weak classifier
Compute $\alpha_K$ and reweigh each object using

![[Pasted image 20241101005242.png]]
Train a new decision stump on reweighted objects
Recompute $\alpha_K$ and $w_i$
**Repeat and repeat**
Finally we end up with:
![[Pasted image 20241101005455.png]]


## Combining classifiers
Very general idea: combine simpler (linear) classifiers to obtain nonlinear classifiers
* Combination should not be too similar, results will be too similar
* Combination often not better than the best
* Combiner should be trained: **trained combiner** can learn to use the strengths of each classifier
* Having less restrictive base outputs may help
