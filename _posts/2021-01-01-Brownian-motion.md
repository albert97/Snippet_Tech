---
layout:     post
title:      "Stochastic Calculus -- Brownian motion and Diffusion Process"
subtitle:   " "
date:       2021-01-01 12:00
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

<h2 class="section-heading">Disclaimer </h2>

The following content was extracted from Stochastic Calclus lecture note by Jonathan Goodman at Courant Insititute 

<h2 class="section-heading">Brownian Motion </h2>

Brownian motion is the name of the phenomenon that small particles in water, when you look at them with a powerful enough microscope, seem to move in a random fashion. It’s the simplest example of a diffusion process.
Many of the properties of diffusion processes can be seen in Brownian motion first and then generalized to more general processes. For example, the backward and forward equations for Brownian motion are special cases of the backward and forward equations for general diffusions.

The central limit theorem is behind the fact that Brownian motion is a model for the random motion of small particles, and for many other random processes. You can view the motion the the particle as the result of a large number of small and independent steps. The position Xt is thought of as the result of a large number (an infinite number in the Brownian motion limit) of small indepen- dent steps. The sum of a large number of independent identically distributed steps, according to the central limit theorem, is approximately Gaussian. The Brownian motion limit produces Xt that is exactly Gaussian.

But the Brownian motion limit is about more than the distribution of Xt. It’s about other properties of the whole Brownian motion path. For example, is is about the hitting probability
$$
Pr(|X_{t}| \ge{R}  \text{for some} t< T) (1)
$$

<html>
  <body>
There is a path version of the central limit theorem, called the Donsker in- variance principle.2 The invariance principle says that you can estimate prob- abilities like (1) for complicated physical processes like the physical Brownian particle motion using the simple mathematical Brownian motion model.
</body>
</html>


<html>
  <body>
Finally, Brownian motion serves as a model of the random noise that “drives” other diffusion processes. This allows us to express general diffusions as func- tions of Brownian motion. The Ito calculus, developed several lessons from now, is the tool for doing this. Brownian motion is used in computer simulation of general diffusions through what is called the Euler Mayurama method.
</body>
</html>


<html>
  <body>
Brownian motion is a random function of time. The position of a particle at time t is \(X_{t}\). We suppose \(X_{0} = 0\) and model the motion for \(t > 0\). The defining properties of Brownian motion are
</body>
</html>

<ol>
<li>. Xt is a continuous function of t.</li>
<li>  The increment Xt2 − Xt1 is Gaussian with mean zero and variance t2 − t1
(t2 > t1 for this to make sense). </li>
<li> X is a Markov process, which means that conditional on Xt, the future
(Xs, with s > t )is independent of the past (Xs with s < t). </li>
</ol>

<html>
  <body>
  The Markov property of the mathematical Brownian motion reflects the fact that the increments of Brownian motion after time t1 are the result of small steps after time t1 that are independent of whatever happened before t1. The random forces moving the particle after t1 are independent of the forces that moved it before t1. The increment variance formula (2.) depends only on the time difference. The Brownian motion model is statistically homogeneous in time in the sense that the distribution of the random increment doesn’t depend on Xt1 or t1, but only on the amount of time in the increment. From a microscopic point of view, this reflects the idea that whatever in the environment that is causing Xt to move is homogeneous in time. The physical Brownian particle moving in a fluid is like this (to some degree of approximation).
</body>
</html>


<html>
  <body>
  A stochastic process (also called random process) is a function of t whose values are random. Brownian motion is a stochastic process. A random vari- able with a specific distribution may be called a sample of the distribution. A sample of a stochastic process may be called a sample path. A diffusion pro- cess is a random process that is a Markov process and has continuous sample paths. Brownian motion is the central and most basic example of a diffusion process. Other diffusion processes have non-Gaussian increments, or Gaussian increments with non-zero mean.
</body>
</html>


<html>
  <body>
Brownian motion is important for many reasons, among them
 </body>
</html>
<ol>
<li>.It is a good model for many physical processes. </li>
<li> It illustrates the properties of general diffusion processes. </li>
<li> It can be used to construct other diffusion processes through the Ito cal- culus. </li>
</ol>
