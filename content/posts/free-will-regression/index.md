---
title: "Linear Regression and Free Will"
author: "Rohan Arni"
date: 2025-07-24T09:10:42-05:00
draft: false

subtitle: ""
math: true

categories: ["Artificial Intelligence", "Math", "Philosophy"] 

---

Do we have free will? That’s a question that’s haunted many philosophers, scientists, and people contemplating their existence late at night. We might find some answers in linear regression, of all the places.

### Background
Linear regression can be simplified to drawing a line of best fit. Given any scattered set of data points, we want to create a line that best represents the shape of the data.
A simple, 2D linear regression model is given by a general form

$$y = \beta_0 + \beta_1 x$$

  
Where $\beta_0, \beta_1$ are learnable parameters of the system. We can collect this into a matrix system of equations for $N$ finite data points:


  $$\mathbf{y} = \mathbf{X}\mathbf{\beta} + \mathbf{\varepsilon}$$


Where:
1. $\mathbf{y}$ is the $N\times 1$ matrix of observed dependent variables
2. $\mathbf{X}$ is the $N \times 2$ matrix of independent variables (the first column is all ones, the second column is the $x$ values)
3. $\mathbf{\beta}$ is the $2 \times 1$ matrix of coefficients
4. $\mathbf{\varepsilon}$ is the $N \times 1$ matrix of errors for each prediction
These matrices look something like:

  
How do we go about learning the parameters $\mathbf{\beta}$ of the data? There are two approaches: solving the normal equations for least squares or performing gradient descent.

### Least Squares
We want to minimize the sum of squared residuals (how inaccurate the model is compared to the true dependent variable:

  $$S(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})^T (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})$$


To minimize the loss function, we can take the derivative with respect to $\boldsymbol{\beta}$ to get

  $$\frac{\partial S}{\partial \boldsymbol{\beta}} = -2 \mathbf{X}^T (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}) = 0$$


Now, we can solve for $\boldsymbol{\beta}$ as

  $$\mathbf{X}^\top \mathbf{y} - \mathbf{X}^{\top} \mathbf{X} \boldsymbol{\beta} = 0 $$$$
\mathbf{X}^\top \mathbf{y} = \mathbf{X}^{\top} \mathbf{X} \boldsymbol{\beta} $$$$
\boldsymbol{\beta} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{y}$$

This is an exact solution for our model parameter vector $\boldsymbol{\beta}$.

### Gradient Descent
We want to minimize this loss function called the mean squared error (MSE).


  $$J(\boldsymbol{\beta}) = \frac{1}{2n} (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})^T (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})$$

  
Once again, we take the derivative of the loss function with respect to $\boldsymbol{\beta}$.
 

  $$\nabla_{\boldsymbol{\beta}} J = -\frac{1}{n} \mathbf{X}^T (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})$$

- This gives the direction of steepest ascent, so for gradient descent we subtract it. Given some small learning rate $\alpha$, we update our parameters as follows
    $$\boldsymbol{\beta}^{(t+1)} = \boldsymbol{\beta}^{(t)} - \alpha \nabla_{\boldsymbol{\beta}} J$$




Or,

  $$\boldsymbol{\beta}^{(t+1)} = \boldsymbol{\beta}^{(t)} + \frac{\alpha}{n} \mathbf{X}^T (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}^{(t)})$$

  
We can repeat this process until the model converges to a minimum loss.
 
### Free Will and Regression
There's a pretty interesting correlation between these methods of solving linear regression and some ideas relating to the problem of free will. There's a direct correlation between hard determinism (the idea that the universe is pre-determined and you have no individual free will) and the least squares solution to regression. Notice how the least squares solution is an exact, precise computation, giving an exact answer every time. This is  similar to the idea that we follow pre-determined paths to an end result, an idea that comes from hard determinism.

The gradient descent approach has more degrees of freedom (learning rate, number of iterations), and the model "learns" the parameters of the solution as guided by some "cost" function (in this case the MSE loss function). This idea is similar to the idea of soft determinism, where we have our own freedom to choose the actions but will lead to the same result as if the universe was deterministic. We have the freedom to choose our actions (each step of gradient descent represents an action we take), but will approach the same result as if the universe had a pre-determined result (least squares regression). However, the main difference is that gradient descent is not guaranteed to take the same path every time, and it can get stuck in local minima. This is similar to the idea that we have the freedom to choose our actions, but we may not always make the best choices.

In addition, following either approach implies that we are guided by some cost/loss function that we are perpetually optimizing. What are the implications of that notion? For another day...


---