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

In this study, I investigated the techniques of Riemann ghost fluid method in solving the compressible multimaterial unsteady Euler equations. The study used MUSCL-Hancock with Super-bee slop limiter and HLLC as the approximate Riemann problem solver. Simulations are completed for single material shock tube test with a contact discontinuity, multimaterial shock tube test with a single and two interfaces. The later is also extended into two dimension with interface aligned with x and y axis, as well as having an angled with x axis. In addition, I have also investigated the effect of level set function reinitialisation using Mach 10 shock. The study confirmed the effectiveness of Riemann ghost fluid method in resolving the sharp interface and capturing the fine behaviour close to the interface. In addition, The use of second order numerical method that is also total variation diminishing ensuring high resolution and no presence of spurious oscillation. To be able to ensure an accurate representation of material interface, reinitialisation of the level set function is necessary. It also reduced dissipation cause by steepening, therefore reducing numerical error at the interface. 

<h2 class="section-heading">Euler's Equations </h2>

In this study, I consider the time-dependent Euler Equations. These are systems of non-linear hyperbolic equations obeying conservation law, describing the dynamics of compressible material. In comparison with original Navies-Stoke equations, the effect of gravity, viscosity and body forces are neglected 
The five governing conservation laws are: 
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

<h2 class="section-heading">References</h2>
