---
layout:     post
title:      "Multi-material simulation using the ghost fluid method"
subtitle:   "Ghost fluid method is my personal favorite when it comes to multimaterial method. The shear beauty is it maintain a shapr material interface while simulating material interactions"
date:       2020-03-21 06:52:00
author:     "Albert"
header-img: 
category:   techblog
tags:       [Scientific computing, Maths]
---
<!DOCTYPE html>
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
<p>
  When \(a \ne 0\), there are two solutions to \(ax^2 + bx + c = 0\) and they are
  \[x = {-b \pm \sqrt{b^2-4ac} \over 2a}.\]
</p>
</body>
</html>
In this study, I investigated the techniques of Riemann ghost fluid method in solving the compressible multimaterial unsteady Euler equations. The study used MUSCL-Hancock with Super-bee slop limiter and HLLC as the approximate Riemann problem solver. Simulations are completed for single material shock tube test with a contact discontinuity, multimaterial shock tube test with a single and two interfaces. The later is also extended into two dimension with interface aligned with x and y axis, as well as having an angled with x axis. In addition, I have also investigated the effect of level set function reinitialisation using Mach 10 shock. The study confirmed the effectiveness of Riemann ghost fluid method in resolving the sharp interface and capturing the fine behaviour close to the interface. In addition, The use of second order numerical method that is also total variation diminishing ensuring high resolution and no presence of spurious oscillation. To be able to ensure an accurate representation of material interface, reinitialisation of the level set function is necessary. It also reduced dissipation cause by steepening, therefore reducing numerical error at the interface. 

<h2 class="section-heading">Euler's Equations </h2>

In this study, I consider the time-dependent Euler Equations. These are systems of non-linear hyperbolic equations obeying conservation law, describing the dynamics of compressible material. In comparison with original Navies-Stoke equations, the effect of gravity, viscosity and body forces are neglected 
The five governing conservation laws are: 

$$ \min_{x \in \R^n} f(x) \, .$$

$$
\rho_t + ( \rho u )_x + (\rho v)_y + (\rho w)_z = 0.
$$
$$
(\rho u)_t + ( \rho u^2 + P )_x + (\rho u v)_y + (\rho u w)_z = 0.
$$
$$
(\rho v)_t + ( \rho u v )_x + (\rho v^2 + p)_y + (\rho u w)_z = 0.
$$
$$
(\rho w)_t + ( \rho u w )_x + (\rho v w)_y + (\rho w^2 + P)_z = 0.
$$
$$
E_t + [u(E+p)_x + [v(E+p)]_y + [w(E + p)]_z = 0.

$$

 
<h2 class="section-heading">Manifolds</h2>

We are interested in generalizing the notion of Euclidean space into arbitrary smooth curved space, called smooth manifold. Intuitively speaking, a **_topological $n$-manifold_** $\M$ is a topological space that locally resembles $\R^n$. A **_smooth $n$-manifold_** is a topological $n$-manifold equipped with locally smooth map $\phi_p: \M \to \R^n$ around each point $p \in \M$, called the **_local coordinate chart_**.

**Example 1 (Euclidean spaces).** For each $n \in \mathbb{N}$, the Euclidean space $\R^n$ is a smooth $n$-manifold with a single chart $\phi := \text{Id}\_{\R^n}$, the identity map, for all $p \in \M$. Thus, $\phi$ is a _global coordinate chart_.

//
{:.right}

**Example 2 (Spaces of matrices).** Let $\text{M}(m \times n, \R)$ denote the set of $m \times n$ matrices with real entries. We can identify it with $\R^{mn}$ and as before, this is a smooth $mn$-dimensional manifold. Some of its subsets, e.g. the general linear group $\text{GL}(n, \R)$ and the space of full rank matrices, are smooth manifolds.

//
{:.right}

<h2 class="section-heading">References</h2>
