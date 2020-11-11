---
layout:     post
title:      "HLLC Solver for Riemann problems for Fluid Dynamics -Ghost Fluid Method Serie 1"
subtitle:   "HLLC Solver uses Godunov flux to resolve shock wave emerged from hyperbolic PDEs. This finiste volume method ensure the conservative nature. "
date:       2020-03-21 06:52:00
author:     "Albert"
category:   techblog
tags:       [Scientific computing, Maths]
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


In this study, I investigated the techniques of Riemann ghost fluid method in solving the compressible multimaterial unsteady Euler equations. The study used MUSCL-Hancock with Super-bee slop limiter and HLLC as the approximate Riemann problem solver. Simulations are completed for single material shock tube test with a contact discontinuity, multimaterial shock tube test with a single and two interfaces. The later is also extended into two dimension with interface aligned with x and y axis, as well as having an angled with x axis. In addition, I have also investigated the effect of level set function reinitialisation using Mach 10 shock. The study confirmed the effectiveness of Riemann ghost fluid method in resolving the sharp interface and capturing the fine behaviour close to the interface. In addition, The use of second order numerical method that is also total variation diminishing ensuring high resolution and no presence of spurious oscillation. To be able to ensure an accurate representation of material interface, reinitialisation of the level set function is necessary. It also reduced dissipation cause by steepening, therefore reducing numerical error at the interface. 

<h2 class="section-heading">The Equations of Fluid Dynamics </h2>
<h3 class="section-heading">Euler's Equations </h3>

In this study, I consider the time-dependent Euler Equations. These are systems of non-linear hyperbolic equations obeying conservation law, describing the dynamics of compressible material. In comparison with original Navies-Stoke equations, the effect of gravity, viscosity and body forces are neglected 
The five governing conservation laws are: 


$$

  \rho_{t} + ( \rho u )_{x} + (\rho v)_{y} + (\rho w)_{z} = 0.
$$

$$
  (\rho u)_{t} + ( \rho u^2 + P )_{x} + (\rho u v)_{y} + (\rho u w)_{z} = 0.
$$

$$
  (\rho v)_{t} + ( \rho u v )_{x} + (\rho v^2 + p)_{y} + (\rho u w)_{z} = 0.
$$

$$
  (\rho w)_{t} + ( \rho u w )_{x} + (\rho v w)_{y} + (\rho w^2 + P)_{z} = 0.
$$

$$
  E_{t} + (u(E+p)_{x} + (v(E+p))_{y} + (w(E + p))_{z} = 0.
$$

<html>
<body>
<p>
  
   I used primitive variables to describes the flow under consideration, namely, \( \rho(x, y, z,t) = \) density or mass density, \( p(x,y,z,t) = \) pressure, \( u(x,y,z,t) = \) x-component of velocity, \( v(x,y,z,t) = \) y-component of velocity, \( w(x,y,z,t) = \) z-component of velocity and E is the total energy per unit volume.
  </p>
</body>
</html>

$$   
     E = \rho (\frac{1}{2 \textbf(V)^2 + e})
$$

<html>
<body>
<p>
       
   where \(\frac{1}{2}\textbf(V)^2 = \frac{1}{2}\textbf(V) \cdot \textbf(V) = \frac{1}{2}(u^2 + v^2 + w^2)\) is the specific kinetic energy and e is the specific internal energy. 
  </p>
</body>
</html>

<h3 class="section-heading">Thermodynamic consideration and equation of states </h3>



The state governing equation (i.e. Euler's equation) for the dynamics of a compressible material are insufficient to completely describe the physical processes involved. There are more unknowns than equations, therefore a closure condition is required. Such closing condition can be described by an equation of state.
A system in thermodynamic equilibrium can be completely described by the basic thermodynamic variables pressure $p$ and specific volume v. As two materials involved in the simulation are thermally ideal gases therefore the relationship between thermodynamic variables  p, v, T take the simple expression:

$$
    T = \frac{pv}{R}
$$

where \(R\) is a constant depending on the particular gas under consideration. The first law of thermodynamics states that for a non-adiabatic system the change in internal energy in a process will be given by 

$$
    \Delta e  = \Delta W + \Delta Q
$$
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
  
  where \( \Delta W \)is the work done on the system and  \( \Delta Q \) is the heat transmitted to the system. Taking the work done as 

  
</body>
</html>

$$
    dW = -pdv
$$

The first law of thermodynamics can be written as :

$$
    dQ = de + pdv
$$

For a calorically ideal gas the internal energy $e$ can be related to p and v via a caloric equation of state which has the simple expression:

$$
    e = \frac{pv}{\gamma -1} = \frac{P}{\rho(\gamma -1)}
$$

The caloric equation state is sufficient to close the system for the Euler equations, unless temperature 
$T$
is needed, in which case a thermal EOS needs to be given explicitly . 

<h2 class="section-heading">Numerical Solutions for Hyperbolic Equations</h2>

Hyperbolic Partial Differential Equations (PDEs) are time-dependent problems without dissipation. For such problems, discontinuity may form from smooth initial conditions. Therefore we often need to obtain solutions from a Riemann problem. A Riemann problem is defined as a specific initial value problem composed of a conservation law together with piece wise constant initial data which has a single discontinuity. For the propose of solving compressible Euler equation, HLLC approximate Riemann Solvers was used.

<h3 class="section-heading">The HLLC Riemann Solve</h3>
<html>
  <body>
    The approximate Riemann solver proposed by Harten Lax and Van leer (HLL) were later modified by Toro to form what is known as the HLLC (C stands for Contact) . HLLC adopts a three-waves model for the structure of the exact solution. Simulation resolution is improved via an incorporation of an intermediate wave. Figure below shows the three waves representation of a Riemann problem where four regions of solutions were separated by three waves with velocity \(S_{L}\), \(S_{*}\) and \(S_R\). They correspond to velocity for the left, intermediate and right wave

<img src="{{ "/assets/img/content/post-example/HLLC_three_wave_representation.png" | absolute_url }}" alt="bay" class="post-pic"/>

    </body>
</html>

<img src="{{ "/assets/img/content/post-example/Structure_of_the_exact_Riemann_problem.png" | absolute_url }}" alt="bay" class="post-pic"/>
<html>
  <body>
A general initial boundary value problem is concerned in this study, proposed as equation. \(\textbf{U}_{t}\) is the time derivative of the state vector and \(\textbf{F}\). \(\textbf{U}_{x})\) is the spatial derivative of the flux. Within the domain, I use the explicit conservative formula to update the numerical solution at each time step. 
   </body>
</html>

$$
\begin{cases}
   &PDEs:  \textbf{U}_{t} + \textbf{F}(\textbf{U})_{x} = 0,\\
   &ICs:  \textbf{U}(x, 0) = \textbf{U}^{(0)}(x),\\
   & BCs:  \textbf{U}(0, t) = \textbf{U}_I(t),   \textbf{U}(L,t) = \textbf{U}_{r(t)}\\
\end{cases}
$$

<html>
  <body>
    \( \textbf{U}_i^{i+1} = \textbf{U}_i^n - \frac{\Delta t}{\Delta x}[\textbf{F}_{i+\frac{1}{2}} - \textbf{F}_{i+\frac{1}{2}}]\)
    
    The unknown numerical flux \(\textbf{F}_{i+\frac{1}{2}}\) is determined using Godunov Flux. \textbf{U}_{1+\frac{1}{2}}(0) is the solution of the Riemann problem at each cell boundary 
   </body>
</html>    

$$
   \textbf{F}_{i+\frac{1}{2}} = \textbf{F}(\textbf{U}_{1+\frac{1}{2}}(0))
$$

$$
\textbf{U$^{hllc}$ (x,t)}=
\begin{cases}
    &\textbf{U}_L  , if \frac{x}{t} \leq S_L, \\
    &\textbf{U}_{\ast L}  , if S_L \leq \frac{x}{t} \leq S_\ast, \\
    &\textbf{U}_{\ast R}.  , if S_\ast \leq \frac{x}{t} \leq S_L, \\
    &\textbf{U}_R  , if \frac{x}{t} \geq S_R , 
\end{cases}
$$

$$
\textbf{F$^{hllc} _{I+\frac{1}{2}}$}=
\begin{cases}
    &\textbf{F}_L  , if \frac{x}{t} \leq S_L, \\
    &\textbf{F}_{\ast L}  , if S_L \leq \frac{x}{t} \leq S_\ast, \\
    &\textbf{F}_{\ast R}.  , if S_\ast  \leq \frac{x}{t} \leq S_L, \\
    &\textbf{F}_R  , if \frac{x}{t} \geq S_R , 
\end{cases}
$$

<html>
  <body>
    For HLLC approximate solver, we seek to find solutions for the two intermediate state vectors \(U_{*} L\) and \(U_{* R} \) thereby finding \(F_{* L}\) and \(F_{* R}\) using Godunov flux.Across the contact discontinuity pressure and tangential component of velocity are continuous whereas tangential components are discontinuous. However, tangential components are continuous the left and right waves ( which can be either rarefraction or shock waves). These conditions proposed in equations allow us to find an expression for velocity of the intermediate wave and intermediate fluxes 

   </body>
</html>

$$
\begin{cases}
   & p_{\ast L} =  p_{\ast R} = p _{\ast} \\
   & u_{\ast L} =  u_{\ast R} = u _{\ast} 
   
\end{cases}
$$

$$
\begin{cases}
   & v_{\ast L}  =  v_L  , v_{\ast R} = v_R \\
   & w_{\ast L} =  w_R  ,  w_{\ast R}= w_R 
   \label{cond:TVside}
\end{cases}
$$

Through some algebraic manipulation, we found the intermediate the intermediate wave velocity as:

$$
    S_{*} = \frac{p_R - p_L +\rho_L u_L(S_L - u_L) - \rho_R u_R (S_R - u_R)}{\rho_L(S_L - u_L) - \rho_R(S_R - u_R)}
$$

<html>
  <body>
fluxes \textbf{F}_{\ast L} and \textbf{F}_{\ast R} are related to fluxes on either side as :
   </body>
</html>

$$
    \textbf{F}_ {\ast K} = \textbf{F}_{K} + S_K(\textbf{U}_{\ast K} - \textbf{U}_K)
$$

<html>
  <body>
for \(K = L\) or \( K = R\), with the intermediate states given as 
   </body>
</html>

$$
\textbf{U}_{\ast K}= \rho_K (\frac{S_K - u_K}{S_K - S_\ast})
    \begin{bmatrix}
    1\\
    S_\ast \\
    v_K\\
    w_K\\
    \frac{E_K}{\rho_K} + (S_\ast - u_K)[S_\ast + \frac{p_K}{\rho_K(S_K - u_K)}]
    \end{bmatrix}
    \label{intermediate state vector}
$$

where the left and right speed are obtained using pressure based wave-speed estimate .


<h2 class="section-heading">References</h2>

1. Harten, A., P. D. Lax, and B. van Leer (1983), On Upstream Differencing and Godunov- Type Schemes for Hyperbolic Conservation Laws, SIAM Review, 25(1), 35–61
2. Toro, E. F. (2009), Riemann Solvers and Numerical Methods for Fluid Dynamics, thrid ed., Springer.
3. Toro, E. F., M. Spruce, and W. Speares (1994), Restoration of the contact surface in the HLL-Riemann solver, Shock Waves, 4 (1), 25–34, 
