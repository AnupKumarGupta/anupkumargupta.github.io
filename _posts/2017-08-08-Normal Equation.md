---
layout: post
title:  "Normal Equation for Linear Regression"
excerpt: "A step by step guide for solving the problem of Multivariate Linear Regression, using the Normal Equations..."
---

Hi guys. For the last couple of weeks I have been taking an awesome course on `Machine Learning`.  I was going through the topic `Multivariate Linear Regression` in which I was introduced `Normal Equation`. The instructor presented the equation, but the derivation was left out for some reasons. I managed to perform a step-by-step derivation and I am sharing it with you. Let's get started 


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

Let us now breakdown the above equation of  `least-squares cost function` in two parts$$, P $$ and $$Q$$ such that:

$$ P = (\theta^TX^T)X\theta $$ 

$$ Q = 2(X\theta)^Ty $$ 

Notice that the third term $$y^Ty$$ can be skipped as its constant wrt $$\theta$$. Let us solve $$ P , Q$$ separately and merge the solution to get the results.

Let us start with the first part:


$$ P(\theta)=\theta^TX^TX\theta$$

Let us write down the equation in form of matrices:

$$P(\theta)=\begin{bmatrix}\theta_1...\theta_n\end{bmatrix}\begin{bmatrix}x_{11}  x_{21}  ...  x_{m1}\\ x_{12}  x_{22}  ...  x_{m2}\\ ...\\ x_{1n}  x_{2n}  ...  x_{mn}\\ \end{bmatrix}\begin{bmatrix}x_{11}  x_{12}  ...  x_{1n}\\ x_{21}  x_{22}  ...  x_{2n}\\ ...\\ x_{m1}  x_{m2}  ...  x_{mn}\\ \end{bmatrix}\begin{bmatrix} \theta_1\\ \theta_2\\ ...\\ \theta_n\\ \end{bmatrix}$$

Or

$$P(\theta)=\begin{bmatrix}\theta_1...\theta_n\end{bmatrix}\begin{bmatrix}x_{11}^2  x_{21}^2  ...  x_{m1}^2\\ x_{12}^2  x_{22}^2  ...  x_{m2}^2\\ ...\\ x_{1n}^2  x_{2n}^2  ...  x_{mn}^2\\ \end{bmatrix}\begin{bmatrix} \theta_1\\ \theta_2\\ ...\\ \theta_n\\ \end{bmatrix}$$


Or

$$P(\theta)= \begin{bmatrix} \theta_1...\theta_n \end{bmatrix} \begin{bmatrix}x^{2}_{11}\theta_1+...+x^{2}_{1n}\theta_n\\ x^{2}_{21}\theta_1+...+x^{2}_{2n}\theta_n\\ ...\\ x^{2}_{n1}\theta_1+...+x^{2}_{nn}\theta_n\end{bmatrix}$$

Or

$$P(\theta)=\theta_1(x^{2}_{11}\theta_1+...+x^{2}_{1n}\theta_n)+\theta_2(x^{2}_{21}\theta_1+...+x^{2}_{2n}\theta_n)+...+\theta_n(x^{2}_{n1}\theta_1+...+x^{2}_{nn}\theta_n)$$


Let's consider the $$\frac{\partial P}{\partial \theta_1}$$, from which we can intuitively calculate the rest:

$$\frac{\partial P}{\partial \theta_1}=(2\theta_1X^{2}_{11}+\theta_2X^{2}_{12}+...+\theta_nX^{2}_{1n})+\theta_2X^{2}_{21}+...+\theta_nX^{2}_{n1}$$

We know that $$X^{2}_{12}=X^{2}_{21}$$ and so on. Hence we can rewrite our equation as:

$$\frac{\partial P}{\partial \theta_1}=2\theta_1X^{2}_{11}+2\theta_2X^{2}_{12}+...+2\theta_nX^{2}_{1n}$$

The partial derivatives by $$\theta_2,\theta_3 ...\theta_n$$  are similar. Collecting the sequence of partial derivatives back into a vector equation, we get:

$$\frac{\partial P}{\partial \theta}=2X^2\theta=2X^TX\theta$$

Now lets go for $$Q$$ 

$$Q(\theta)=2(X\theta)^Ty$$

$$Q(\theta)=2\begin{bmatrix} \begin{bmatrix} x_{11}  x_{12}  ...  x_{1n}\\x_{21}  x_{22}  ...  x_{2n}\\ ...\\ x_{m1}  ...  ...  x_{mn}\\ \end{bmatrix}\begin{bmatrix} \theta_1\\ \theta_2\\ ...\\ \theta_n\\ \end{bmatrix} \end{bmatrix}^T\begin{bmatrix} y_1\\ y_2\\ ...\\ y_m\\ \end{bmatrix}$$

Or:

$$Q(x)=2\begin{bmatrix} x_{11}\theta_1+...+x_{1n}\theta_n\\x_{21}\theta_1+...+x_{2n}\theta_n\\ ...\\ x_{m1}\theta_1+...+x_{mn}\theta_n \end{bmatrix}^T\begin{bmatrix} y_1\\ y_2\\ ...\\ y_m\\ \end{bmatrix}$$

Or:

$$ Q(x)=2(x_{11}\theta_1+...+x_{1n}\theta_n)y_1+2(x_{21}\theta_1+...+x_{2n}\theta_n)y_2+...+2(x_{m1}\theta_1+...+x_{mn}\theta_n)y_m$$

Now we have to calculate its derivation wrt to $$\theta$$ Below we have partial derivative of above equation wrt to $$\theta_1$$ 

$$\frac{\partial Q}{\partial \theta_1}=2(x_{11}y_1+x_{21}y_2+...+x_{m1}y_m)$$

One can easily calculate the other partial derivatives similarly. After solving the derivative we have following expression:

$$\frac{\partial Q}{\partial \theta} = 2\begin{bmatrix} x_{11}+...+x_{1n}\\x_{21}+...+x_{2n}\\ ...\\ x_{m1}+...+x_{mn} \end{bmatrix}^T\begin{bmatrix} y_1\\ y_2\\ ...\\ y_m\\ \end{bmatrix}$$

Or


$$\frac{\partial Q}{\partial \theta}=2X^Ty$$

Recall that for convenience we broke $$J$$ up into three parts$$: P $$, $$ Q $$ and $$y^Ty$$, where third term was skipped.

The equation after combining the results of first two parts is:

$$\frac{\partial J}{\partial \theta}=2X^TX\theta-2X^{T}y=0$$

Or:

$$X^TX\theta=X^{T}y$$

Assuming that the matrix $$X^TX$$ is invertible(non-singular), we can multiply both sides by $$(X^TX)^{-1}$$ and get our solution as:

$$\theta=(X^TX)^{-1}X^Ty$$

which is the  `Normal Equation for Linear Regression`.
