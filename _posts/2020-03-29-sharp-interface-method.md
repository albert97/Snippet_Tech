---
layout:     post
title:      "Sharp Interface method and levelset function -Ghost Fluid Method serie 3"
subtitle:   "Sharp interface method as one methods used in multi material simulation has the advantage of maintaining a sharp interface and swiftness in tracking the movement of the interface"
date:       2020-03-29 12:00
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

<h2 class="section-heading">Level Set methods</h2>

For Eulerian single-code model used in this study, A level set function is used to models the interface location and has the following purpose: 

<ol>
<li> It represents a sharp interface. item</li>
<li>It identified the location of a material interface, and is used ti split the computational domain into multiple regions.item</li>
</ol>

<html>
<body>
  A level set method is a implicit representation of the interface, it can be considered as the zero-contour of a scalar field. A signed distance function is usually used to define the level set function as it gives the shortest distance to the interface ($|\nabla \phi (x)| = 1$). I define the level function to be zero at the interface (equation \ref{levelsetfunction }):
</body>
</html>


$$
    \phi (x) = 0 
$$

<html>
<body>
Numerical errors at the interface can accumulate, causing increased dissipation and simulation errors. When the level set function steepened enough it resembles a discontinuity and disrupts simulation.  To correct this I use reinitialisation techniques to revert a general level set function to a signed distance function, whilst maintaining the zero contour. During reinitialisation, the interface is treated as fixed by keeping the region with \(\phi < 0 \) fixed. The reinitialisation process is equivalent to solving the Eikonal equation below : 
</body>
</html>

$$
    |\nabla \phi | = 1
$$

There are three techniques that are available for reinitialisation -- Iterative reinitialisation, fast marching and fast sweeping. iterative reinitialisation is an iterative scheme where the Eikonal equation is transformed to a hyperbolic PDE by introducing a time derivative :


$$
\frac{\partial \phi}{\partial \tau} + sgn(\phi)(| \nabla \phi|-1) = 0
$$


<html>
<body>
The sign of the level set function depends on which side of the interface we are reinitialising. The variable \(\tau\) is known as 'fictitious time', in which the boundaries of the level set function are held fixed, thus this equation has a steady state solution.

Due to inefficiency, and uncertainty in the number of iterations, I adopt the fast sweep reinitialisation approach purposed by. The principle of the fast sweeping method is the level set function, also a signed distance function always gives the shortest distance to an interface and therefore a numerical technique to compute a value \(\phi _i\) is dependent only on \(|\phi|<|\phi_i|\). The fast sweeping method carries out a series of sweep which compute values of level set function such that \(| \nabla \phi|=1 \) based on neighbouring values. Multiple sweep alternates in x, y, z, positive and negative directions . \par

The movement of interface is modelled using a Hamilton-Jacobi equation :

</body>
</html>

$$
    \frac{\partial \phi}{\partial t} + H( \nabla \phi) = 0
$$

where the operator H acts upon the gradient of the level set function. 
For the problem involved in this study, a simple advection equation is adequate to describe the evolution of interface : 

$$
    \frac{\partial \phi}{\partial t} + \textbf{v} \cdotp \nabla \phi = 0
$$

<html>
<body>
$\textbf{v}$ is the velocity of the materials, which has no dependence on the level set function.  Hence the discretisation can be derived:
</body>
</html>

$$
\frac{\phi_i^{n+1}-\phi_i^{n}}{\Delta t} + v_{x,i}^n(\frac{\partial \phi}{\partial x})_i^{n}+ v_{y,i}^n(\frac{\partial \phi}{\partial y})_i^{n}+v_{y,i}^n(\frac{\partial \phi}{\partial z})_i^{n} =0
$$

Several numerical scheme are available for the spatial derivative, for this study first order upwind scheme is adopted. The upwind and downwind approximation depends on the direction of the velocity.

<h2 class="section-heading">References</h2>

1. Fedkiw, R. P., T. Aslam, B. Merriman, and S. Osher (1999), A Non-oscillatory Eulerian Ap- proach to Interfaces in Multimaterial Flows (the Ghost Fluid Method), Journal of Compu- tational Physics, 152(2), 457–492.
2. Osher, S., R. Fedkiw, and K. Piechor (2004), Level Set Methods and Dynamic Implicit Surfaces, Applied Mechanics Reviews
3.Zhao, H. (2004), A fast sweeping method for Eikonal equations, Mathematics of Computation,

