---
layout: post
title:  "Normal Equation"
excerpt: "A step by step guide for solving the problem of Multivariate Linear Regression, using the Normal Equations..."
---

Hi guys. For the last couple of weeks I have been taking an awesome course on `Machine Learning`.

** 
I have to change this one
 I was going through the topic `Multivariate Linear Regression` where the instructor presented an analytic solution `Normal Equation`. 

The derivation of the equation was not discussed, probably due to it was too mathematical. Blah blah...

**

Let's us assume we are given the `hypothesis function` as: 

$$h_{\theta}(x)=\theta_0x_0+\theta_1x_1+\cdots+\theta_nx_n$$

where $$ \theta_0 , \theta_1, \cdots \theta_n $$ are the parameters and  $$ x_0 , x_1, \cdots x_n $$ are the features.

We aim to minimize our `cost function` which is as follows:

$$J(\theta_{0...n})=\frac{1}{2m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2$$

where $$x^{(i)}$$ is the $$i^{th}$$ sample $$($$from a set of m samples$$)$$ and $$y^{(i)}$$ is the $$i^{th}$$ expected result.

Let us consider the parameter vector as follows: 

$$\theta = \begin{bmatrix} \theta_0\\ \theta_1\\ ...\\ \theta_n \end{bmatrix}$$  

Now the question arises why a matrix ? We have a system of linear equations here and these equations can easily handled by matrix algebra $$($$or linear algebra$$)$$.

Now we consider our feature vector as 

$$x = \begin{bmatrix} 1\\ x_1\\ ...\\ x_n \end{bmatrix}$$ 

where  $$x_1$$,  $$x_2$$ up to $$x_n$$ are $$n$$ features. We have considered $$x_0$$ as $$1$$ for sake of easy calculations. Now intuitively we can say that, for a single feature vector we can write the `hypothesis function` as
$$h_{\theta}(x)=\theta^Tx$$ 

Recall that we have $$m$$ `data samples` with us. Let us consider a matrix $$(X)$$ with $$m$$ rows, each representing a data sample and $$n+1$$ columns. Now the `hypothesis function` can be re-written as 
$$h_{\theta}(x)=X\theta$$ 

With this, we can rewrite the `least-squares cost function` as following, replacing the sum by matrix multiplication:

$$J(\theta)=\frac{1}{2m}(X\theta-y)^T(X\theta-y)$$

Let us get rid of $$\frac{1}{2m}$$  term, as it plays no role when the derivative is compared to zero.

$$J(\theta)=(X\theta-y)^T(X\theta-y)$$

We now apply the following transpose identity $$(A-B)^T = (A^T-B^T)$$ and get the following equation.

$$J(\theta)=((X\theta)^T-y^T)(X\theta-y)$$

Further solving the equation,we get:

$$J(\theta)=(X\theta)^TX\theta-(X\theta)^Ty-y^T(X\theta)+y^Ty$$

Now again applying the following identity $$(A*B)^T = (B^T*A^T)$$ , we can rewrite the equation as given below.  

$$J(\theta)=(\theta^TX^T)X\theta-(X\theta)^Ty-y^T(X\theta)+y^Ty$$

Now one can easily show that $$(X\theta)^Ty=y^T(X\theta)$$ and hence we get our final `least-squares cost function` is: 

$$J(\theta)=\theta^TX^TX\theta-2(X\theta)^Ty+y^Ty$$

We know that the above function has a minimum value for the $$\theta$$ at which  $$\frac{\partial J}{\partial \theta}= 0 $$


