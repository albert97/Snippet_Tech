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

<h2 class="section-heading"> Transition probabilities and value functions </h2>

<html>
  <body>
The Brownian motion path is too complicated to be described by a single prob- ability density. But there are useful probability densities for simpler quantities related to the Brownian motion path. These densities do not describe the whole path. They are densities of some simple functions of a Brownian motion path. For example, Xt is the position at a specific time t. We denote the PDF of Xt by u(x,t). There is a simple Gaussian formula for u(x,t), which comes from the fact that Xt − X0 is the increment of Brownian motion for the time interval ending at t2 = t and starting at t1 = 0. The increment is equal to Xt because X0 = 0. It (by property 2) is Gaussian with mean zero and variance t. This is
    </body>
</html>

$$
  u(x,t) = \frac{a}{\sqrt{2 \pi t}} e^{- \frac{x^{2}}{2t}}
$$

<html>
  <body>
    
This probability density describes the probability density at time t but it says littleaboutthepathXs for0<s<t.
Properties 2 and 3 lead to formulas for the joint density of several ob- servations of the Brownian motion path at several times. To start, suppose 0 < t1 < t2. Write X1 for Xt1, etc. We want the joint density function u2(x1, x2, t1, t2), which is defined by
    </body>
</html>

$$
  u2(x1, x2,t1, t2) dx1dx2 =Pr(x1 ≤X1 ≤x1 +dx1 \quad and \quad x2 ≤X2 ≤x2 +dx2) .
$$

<html>
  <body>
The expression for u2 comes from the density of X1 and the conditional density of X2 given X1. The PDF for X1 is (2) with x = x1. The conditional probability of X2 given X1 is given by (not writing t1 and t2 to shorten the formulas)
    </body>
</html>

$$
 u(x2|x1)dx2 =Pr(x2 ≤X2 ≤x2 +dx2 |X1 =x1) .
$$

<html>
  <body>
Property 2 implies that this is Gaussian with mean x1 and variance t2 − t1. Thus
    </body>
</html>

$$
u(x_{2} | x_{1}) = \frac{1}{\sqrt{2 \pi (t_{2} - t_{1}) }} e^{-\frac{1}{2(t_{2} - t_{1})} (x_{2} - x_{1})^{2}}
$$

<html>
  <body>
This is called the transition density of Brownian motion because it describes the
  probability density of transitions from x1 at time t1 to x2 at time t2. Bayes’ rule for this context is
</body>
</html>

$$
u2(x1, x2) = u(x1)u(x2|x1) .
$$

<html>
  <body>
Specifically, we get (with some algebra)
</body>
</html>

$$
u(x_{2} | x_{1}) = \frac{1}{\sqrt{(2 \pi )^{2} (t_{2} - t_{1}) t_{1}}} e^{ - \frac{1}{2} [\frac{(x_{2} - x_{1})^{2}}{t_{2} -t_{1}} + \frac{x_{1}^{2}}{t_{2}}]}
$$

<html>
  <body>
The formula for the joint density of three or more observations is analogous, but its derivation requires the Markov property 3.
Suppose we want to know the expected value of some function of the Brow- nian motion position at time T:
</body>
</html>

$$
f0 =E[V(XT)] 
$$

<html>
  <body>
The value function is the conditional expectation of V (XT ), conditional on the
location at an earlier time
  </body>
</html>

$$
f(x,t)=E[V(XT)|Xt =x] .
$$


<html>
  <body>
This is often written
  </body>
</html>

$$
f(x,t)=Ex,t[V(XT)] .
$$

<html>
  <body>
The subscript on the expectation indicates which “probability measure” is used for the expectation. Future lessons will say more about probability measure, but without giving all the mathematical details. Either the conditional probability formula (3), or the property 2 that it comes from, gives (writing x for x2, y for x1,T fort2 andtfort1)
  </body>
</html>

$$
f(x,t) = \frac{1}{\sqrt{2 \pi (T-t)}} \int_{-\infty}^{\infty} V(x) e^{ - \frac{1}{2} \frac{(x-y)^{2}}{T-t}} dy 
$$

<html>
  <body>
In more complicated problems, the expectation (5) is calculated by solving the partial differential equation that the value function satisfies. The value function gives \(f_{0} \) because \(f_{0} =f(0,T) \).
    </body>
</html>


<h2 class="section-heading">Forward and Backward equations </h2>

$$
\partial_{t} u = \frac{1}{2} \partial_{x}^{2}u
$$


<html>
  <body>
The u equation (8) is called forward because it describes how u changes (evolves) as time moves forward. The initial data u0(x) are specified in a somewhat arbitrary way.
  </body>
</html>

$$
\partial_{t} f(x,y) + \frac{1}{2} \partial_{x}^{2} f(x,t) = 0 
$$

<html>
  <body>
  This is commonly called the backward equation (or Kolmogorov backward equa- tion) to indicate that the unknown f is a value function and that the sign is different. It is called the "backward" becasue, the value function f satisfies final conditions f (x, T ) = V (x). This is “obvious” from the abstract definition . If we know \(X_{T} = x\), then the expected value is irrelevant, you just get V (x). The solution to the final value problem is also unique, so the formula  \( f(x,t) = \frac{1}{\sqrt{2 \pi (T-t)}} \int_{-\infty}^{\infty} V(x) e^{ - \frac{1}{2} \frac{(x-y)^{2}}{T-t}} dy  \)represents this unique solution. It is necessary that t < T . The value function evolves backwards in time from its given final condition. In the integral, G(x, y, T − t) makes sense only if t < T .
  </body>
</html>
