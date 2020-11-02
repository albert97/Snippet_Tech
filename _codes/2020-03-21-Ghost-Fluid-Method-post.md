---
layout: post
title:  "Multi-material Simulation using the Ghost Fluid method"
date:   2020-03-21 10:00:40
author: Albert
---
<br />
<br />


_**Disclaimer.** This post is served as a summarisation of my study notes on RKHS theory [1], and classes I took on relevant topics, containing theoratical details from [1, 2, 3] along with my interpretations directed by my personal interests on those topics. I am by no means an expert in functional analysis and spectral theory, so please feel free to point out any mistakes in the post._
<br/><br/>

In this article, we assume that $\calX$ is a locally compact Hausdorff space equipped with a positive Borel measure $\mu$. Moreover, let $\calL^2(\calX, \mu)$ be the separable Hilbert space of real functions defined on $\calX$. We will mainly consider the spectral property of the integral operator for $k\in \calL^2(\calX\times\calX, \mu)$, which is defined as
<div>


#### Table of Contents
1. [The Equations of Fluid Dynamics](#The Equations of Fluid Dynamics)
2. [Introduction](#Introduction)
    * [The Extinction Events](#The extinction events)
    * [Siberian Traps](#Siberian Traps)
3. [The Extinction Mechanism](#The Extinction Mechanism)
4. [Footnotes](#footnotes)

## The Equations of Fluid Dynamics

### Euler's Equations
In this study, I consider the time-dependent Euler Equations. These are systems of non-linear hyperbolic equations obeying conservation law, describing the dynamics of compressible material. In comparison with original Navies-Stoke equations, the effect of gravity, viscosity and body forces are neglected  \cite{Toro2009}.
<br />
The five governing conservation laws are: 
\begin{equation}
\rho_t + ( \rho u )_x + (\rho v)_y + (\rho w)_z = 0.
\label{3D Euler equation in Conservation form1}
\end{equation}
\begin{equation}
(\rho u)_t + ( \rho u^2 + P )_x + (\rho u v)_y + (\rho u w)_z = 0.
\label{3D Euler equation in Conservation form2}
\end{equation}
\begin{equation}
(\rho v)_t + ( \rho u v )_x + (\rho v^2 + p)_y + (\rho u w)_z = 0.
\label{3D Euler equation in Conservation form3}
\end{equation}
\begin{equation}
(\rho w)_t + ( \rho u w )_x + (\rho v w)_y + (\rho w^2 + P)_z = 0.
\label{3D Euler equation in Conservation form4}
\end{equation}
\begin{equation}
E_t + [u(E+p)_x + [v(E+p)]_y + [w(E + p)]_z = 0.
\label{3D Euler equation in Conservation form5}
\end{equation}

<br />
