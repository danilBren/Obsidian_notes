Linear discriminants, classifiers that **do not do** density estimation:
• Perceptron
• Fisher classifier
• Logistic classifier
• Least squares

**Perceptron**
Decision boundary: $$ g(x) = W^Tx + w_0 = 0 $$
Weight vector $W$ and bias term (offset) $w_0$

Classify $x$ to:
	$w_1$    $if$    $\mathbf{w}^T\mathbf{x} + w_0 \geq 0$
	$w_2$    $if$    $\mathbf{w}^T\mathbf{x} + w_0 \lt 0$

$\mathbf{w}^T\mathbf{x}$ represents the **projection** of the feature vector $\mathbf{x}$ onto the weight vector $\mathbf{w}$.

![[Pasted image 20241027202104.png]]

How can we find these $\mathbf{w}$ and $w_0$?

**Nearest mean classifier**:
For now we assume Gaussian distribution per class. When we assume $\sum = \sigma^2 I$, we find:
$$\begin{eqnarray} \mathbf{w} & = & \mu_2 - \mu_1 \\w_0 & = & bla bla \end{eqnarray}$$**Perceptron**:
First we need to assume that the (two) classes are linearly separable. So there is an optimal $\mathbf{w}^*$:
![[Pasted image 20241027203518.png]]

Perceptron error/loss:
![[Pasted image 20241027203500.png]]

Assume I have a cost function: $J(\theta)$ 
![[Pasted image 20241027203620.png]]
How do we minimize this function?
Option 1: Set the derivative to 0 and solve:
$$\frac{\partial J(\theta)} {\partial\theta} = 0$$
Typically **hard/impossible** to do.

Option 2: Follow the gradient until you hit a (local) minimum:
$$\theta_{t+1} = \theta_t - \rho\frac{\partial J(\theta)} {\partial\theta}$$

$\rho$ is the **learning rate**.

**Gradient descent**

$$\hat{w} = (X^TX)^{-1}X^Ty$$