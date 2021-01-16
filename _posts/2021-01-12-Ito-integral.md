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
<html>
<body>
The integral is the sum of infinitely many infinitely small contributions.
The expression:
</body>
</html>

$$
\int_{0}^{T}  F_{t} dt
$$

<html>
<body>
means that you divide the interval [0,T] into infinitely many tiny and non- overlapping pieces of length $dt$ and add $F_{t}dt$. The integral sign is a distorted S, for “sum”. It is possible to give a less vague definition by defining approximate integrals of the form:
</body>
</html>

$$
Y_T^{(h)} = \sum_{0 <= t_{k} < T} F_{t_{k}} h = \sum_{0 <= t_{k} \lt T} F_{t_{k}}(t_{k+1) - t_{k}} 
$$

<html>
<body>
Here, h > 0 is a time step and tk = kh is the start of a time interval [tk,tk+1]of lengthh. It is possible to prove that the following limit exists
</body>
</html>

$$
Y_{T}= lim_{h->0}Y_T^{(h)}  
$$

<html>
<body>
This proof depends on the function Ft – is it continuous.
You can integrate (add up) contributions of the form FtdX, which gives an integral of the form:
</body>
</html>  

  
$$
  Y_{T}= \int_{0}^{T}  F_{t} dX_{t}            (1)
$$


<html>
<body>
If Xt is a random process, then the “decision” Ft must be made on the basis of information available at time t. This information does not include future values Xs, for $s > t$, but it might involve predictions of future values from present information. A trading strategy Ft is adapted, or non-anticipating, or progressively measurable1 if Ft is a function of X[0,t].
 </body>
</html>  

<html>
<body>
If Xt is a diffusion process and Ft is adapted, then the integral (1) is the Ito integral. The random processes Xt and Ft define a new random process YT . This Lesson explains (not in complete mathematical rigor) the proof that the following limit exits
  </body>
</html>  
  

$$
Y_{T}= lim_{h->0}Y_T^{(h)}  = lim_{h->0} \sum_{0 <= t_{k} \lt T} F_{t_{k}}(t_{k+1) - t_{k}}
$$

<html>
<body>
Starting here, the concept of a martingale will be used constantly. A stochas- tic process is a martingale if its increments have expected value zero at the start of each increment interval. That is, if s > 0, then
</body>
</html>  
  
$$
  E[X_{t+3} - X_{t} | F_{t}] = 0
$$

<html>
<body>
(The full technical definition of martingale requires more technical hypotheses on Xt and a full technical definition of Ft.) Some important facts about mar- tingales: (1) Brownian motion is a martingale. (2) If Xt is a martingale then YT , defined by the Ito integral (1), is a martingale. This is sometimes called Doob’s martingale theorem. The financial interpretation is that a trading strat- egy from a martingale produces a martingale – you cannot make an expected profit from a non-anticipating trading strategy. (3) A diffusion is a martingale if the infinitesimal drift is zero.
</body>
</html>  


<html>
<body>
The Ito isometry formula, for a martingale diffusion, is
</body>
</html>  

$$
   E[Y_{T}^2] = \int_{0}^{T} E{F_{t}^{2}} E[v(X_{t})^{2}]dt
$$

<html>
<body>
This is an intergal version of a simple face about random sums. First, suppose that Uk are random vairbale with E[Uk] = 0, and 
</body>
</html>  

$$
  S_{n} = \sum_{1}^{n} U_{k}
$$

<html>
<body>
Then  
</body>
</html>  

$$
  E[S_{n}^2] = \sum_{1}^{n} E[U_{k}^{2}]
$$


<html>
<body>
Now suppose that Fn is “all the information” in the random numbers F1, . . . , Fn and U1,...,Un−1, and suppose that the Un are martingale differences in the sense that
<html>
<body>

$$
  E[U_{n}|F_{n}]=0.
$$

<html>
<body>
Define a sum that looks more like (1)
<html>
<body>

$$
  S_{n} = \sum_{1}^{n} F_{k}U_{k}
$$

<html>
<body>
This has 
<html>
<body>

$$
  E[S_{n}^{2}] = \sum_{1}^{n} E[F_{k}^{2}] E[U_{k}^{2} | F_{k}]
$$

<h2 class="section-heading">Application to SDE</h2>

<html>
<body>
  


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

