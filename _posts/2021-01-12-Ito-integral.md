---
layout:     post
title:      "Stochastic Calculus -- Ito Integral"
subtitle:   "Ito integral is the stochastic calculus version of integration of ordinary calculus"
date:       2021-01-12 12:00
author:     "Albert"
category:   techblog
tags:       [math]
---


<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>MathJax example</title>
  <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
  <script id="MathJax-script" async
          src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>
</head>
<body>
  
</body>
</html>


...... Yap ............. 
Currently busy with work, so..... STILL NEED TO COMPELTE THIS 
<h2 class="section-heading">Ito Integral</h2>

The integral is the sum of infinitely many infinitely small contributions.
The expression:
$\int0_^T  F_t dt$
means that you divide the interval [0,T] into infinitely many tiny and non- overlapping pieces of length $dt$ and add $F_tdt$. The integral sign is a distorted S, for “sum”. It is possible to give a less vague definition by defining approximate integrals of the form:
$Y_T^{(h)} = \sum_{0 \let_k \lt T} F_{t_k} h = \sum_{0 \let_k \lt T} F_{t_k}(t_{k+1) - t_k  $

Here, h > 0 is a time step and tk = kh is the start of a time interval \[tk,tk+1 \]of lengthh. It is possible to prove that the following limit exists
$Y_T= lim_{h->0}Y_T^{(h)}   $
tHIS proof depends on the function Ft – is it continuous.
You can integrate (add up) contributions of the form FtdX, which gives an integral of the form:
$\Y_T= int0_^T  F_t dX_t$

<h2 class="section-heading">Application to SDE</h2>

<html>
<body>
  

</body>
</html>

$$
    \hat{{n}} \cdot \nabla Q = 0
$$

$$
    \hat{{n}} \cdot \nabla \phi = 1
$$


$$
    P(Q_{i,j,k}) = ( \frac{ Q_{i,j,k} - Q_x}{\Delta x})^2 +  ( \frac{ Q_{i,j,k} - Q_y}{\Delta y})^2 = 0
$$

<html>
<body>
  
The choice of \(Q_x\) and \(Q_y\) depends on the value of level set function (Sambasivan2009). 
</body>
</html>

<h2 class="section-heading">Borel Cantelli lemma </h2>



$$
     \phi = x - x_0
$$

<html>
<body>
 where \( x_0\) is the location of the contact discontinuity \cite{Toro2009}.

</body>
</html>

<h2 class="section-heading">Convergence for the Ito Integral</h2>


$$
    \phi = max( (x - x_1), (x_2 - x))
$$

