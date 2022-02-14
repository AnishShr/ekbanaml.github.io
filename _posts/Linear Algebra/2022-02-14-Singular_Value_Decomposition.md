---
title: "Singular Value Decomposition"
excerpt_separator: "This post covers matrix decomposition, especially singular value decomposition, and points out some of the SVD's applications"
last_modified_at: 2022-02-14
categories:
  - Linear Algebra
tags:
  - Vectors
  - Matrices
  - Eigen Decomposition  
header:
  image: "https://images.pexels.com/photos/772803/pexels-photo-772803.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260"
  caption: "Photo credit: [**Pexel**](https://images.pexels.com/)"
author: AnishShr
---

## Brief Introduction to the Singular Value Decomposition (SVD)   

Back in elementary mechanics, we learned that any force vector can be decomposed into it's components along the x and y axes:   
   
![Vector Decomposition]({{ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_Decomposition/vector_decomposition.gif)
   
This is what the SVD does to a matrix, i.e., decompose the vectors in orthogonal axes.   

Any vector when decomposed yields 3 pieces of information:
   
![Vector Decomposition Components]({{ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_Decomposition/Vector_Decomposition_components.png)
   
1. The directions of projection (direction of v1 and v2)
    - The unit vectors (v1 and v2) represent the directions in which we project (or decompose the vectors).
    - These directions can be any orthogonal axes, not just the x and y axes.

2. The length of projection (line segments sa1 and sa2)
    - These tell us how much of the vector is contained in each direction of projection
    - sa1>sa2 means that the vector a is leaning more towards v1 than v2

3. The vectors of projection (pa1 and pa2)
    - pa1 and pa2 are used to reconstruct the original vector a by adding them together.

SCD extends this decomposition to more than one vector, and to all dimensions. In order to accomplish this, we use matrices.   
   
![Vector Decomposition Components2]({{ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_decomposition/Vector_Decomposition_components(2).png)
   
Here, the orthogonal axes are the directions of v1 and v2, along which we want to decompose the vector 2.   

Projection operation in vector algebra is done by dot product.
   
$$ a^{T}.v_{1} = \begin{bmatrix}a_{x} &a_{y}\end{bmatrix}. \begin{bmatrix}v_{1x}\\v_{1y}\end{bmatrix} = sa_{1} $$   
$$ a^{T}.v_{2} = \begin{bmatrix}a_{x} &a_{y}\end{bmatrix}. \begin{bmatrix}v_{2x}\\v_{2y}\end{bmatrix} = sa_{2} $$   

Encompassing v_{1} and v_{2} in a single matrix V:   

$$ a^T.V = \begin{bmatrix}a_{x} &a_{y}\end{bmatrix} \begin{bmatrix}v_{1x} & v_{2x} \\ v_{1y} & v_{2y}\end{bmatrix} = \begin{bmatrix}sa_{1} &sa_{2}\end{bmatrix} $$   

After adding another point **b**:   

![Vector Decomposition 2 Points]({{ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_Decomposition/Vector_Decomposition_components_2points.png)   

$$ A.V = \begin{bmatrix}a_{x} &a_{y} \\ b_{x} &b_{y}\end{bmatrix}.\begin{bmatrix}v_{1x} & v_{2x} \\ v_{1y} & v_{2y}\end{bmatrix} = \begin{bmatrix}sa_{1} &sa_{2} \\ sb_{1} &sb_{2}\end{bmatrix} $$   

![SVD Generalization]({{ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_decomposition/SVD_generalization.gif)   

i.e.,   
$$ A.V = S $$   
This implies, $$ A = SV^{-1} = SV^T $$   

if we look the matrix **S** closely, it consists of:   
![Analyzing S]({ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_Decomposition/Analyzing_S.png)   

In order to break this matrix **S**, it would be best if we normalize the column vectors.   
   
$$ Magnitude of 1^{st} column = \sigma _{1} =  \sqrt{(sa_{1})^{2} + (sb_{1})^{2}} $$  
$$ Magnitude of 2^{nd} column = \sigma _{1} =  \sqrt{(sa_{2})^{2} + (sb_{2})^{2}} $$  

![Decomposing S]({{ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_Decomposition/Decomposing_S.png)   

Finally, the conventional SVD formula is obtained:   
$$ A = U \Sigma V^{T} $$
   
$$ S = \begin{bmatrix}sa_{1} &sa_{2} \\ sb_{1} &sb_{2}\end{bmatrix} = \begin{bmatrix}ua_{1} &ua_{2} \\ ub_{1} &ub_{2}\end{bmatrix} \begin{bmatrix}\sigma_{1} &0 \\ 0 &\sigma_{2}\end{bmatrix} = U \Sigma $$   

![analyzing U Sigma]({ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_decomposition/Analyzing U_Sigma.png)   

**Why did we introduced sigmas for normalizaing S?**   
As the sigmas are defined as the square roots of the sum of squared projection lengths, they represent how close all points ar to that specific projection axis.   

![sigma animation]({{ site.url }}{{ site.baseurl }}/assets/images/linear_algebra/Singular_Value_Decomposition/sigma_animation.gif)   

The closer the points to a specific projection axis, the larger the value of the corresponding sigma   
