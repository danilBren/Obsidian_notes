**Pattern recognition pipeline** - i.e. from an picture:
1. Feature extraction
2. This creates the **dataset**
3. Learning
4. This creates the **classifier**
From measurements, extract features, define labels,
and train a classifier.

**Classification**: given labelled data $x$, assign to each object a class label $w$. 
If instead:
	class labels -> real values: **regression**
	supervised labels -> no labels: **clustering**

Several ways to describe **classifier**:
- if $p(y_1|x) > p(y_2|x)$ then assign to $y_1$ otherwise $y_2$
- if $p(y_1|x) - p(y_2|x) > 0$ then assign to $y_1$
- or $\frac {p(y_1|x)} {p(y_2|x)} > 1$
- or $log(p(y_1|x)) - log(p(y_2|x)) > 0$

The sum of all the probabilities = 1

In many cases the posterior is hard to estimate
use **Bayes’ theorem** to rewrite one into the other: $$ p(w|x) = \frac {p(x|w)p(w)} {p(x)} $$
Class (conditional) distribution     $p(x|w)$
Class prior                                     $p(w)$: the prior probability of a particular class before observing any data.
(unconditional) data distribution  $p(x)$: the probability distribution of the features x across all classes

**Classification error**: $$p(error) = \sum_{i=1}^{C}p(error|w_i)p(w_i)$$
**Bayes error** $\epsilon^*$ is the minimum attainable error: typically >0.
- In practice, we do not have the true distributions, and we can not obtain.
- The Bayes’ error does not depend on the classification rule that you apply, but on the distribution of the data.
- In general you can not compute the Bayes’ error:
	- you don’t know the true class conditional probabilities
	- the (high) dimensional integrals are very complicated

Sometimes misclassification of class A to class B is much more dangerous than misclassification of class B to class A. Introduce a loss that measures the cost of assigning an object that came from class $w_j$ to class $w_i$: $$\lambda_{ji}$$
