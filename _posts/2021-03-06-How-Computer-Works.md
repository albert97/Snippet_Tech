---
layout:     post
title:      "How computer works"
date:       2021-03-06 12:00
author:     "Albert"
category:   techblog
tags:       [Computer]
---

<html>
<head>
  <!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-QY6RDJK8PM"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-QY6RDJK8PM');
</script>
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

 
 <h2 class="section-heading">Disclaimer:  </h2>
  
  I was recently introduced to this GREAT Youtube channel called "[coding adventures](https://www.youtube.com/c/SebastianLague/videos)". I found this one particularly interesting [Exploring How Computers Work by Sebastian Lague](https://www.youtube.com/watch?v=QZwneRb-zqA).
  It discusses basic aspects of computer logic, in this section I intend to summarise the main points to help me understand and memorise. For anyone who is interested in Sebastian Lague's channel, do check it out!


 <h2 class="section-heading"> Arthmetric and Logic Unit  </h2>
 In the video, Sebastian breaks it down into small modules and I will follow this footstep into explaining the components of computer arthmetric and logic unit.
 
 <h3 class="section-heading"> AND Gate </h3>
 
 Truth table to explain the concepts of AND & OR gate, Imagine A, and B are two switches in serie in a 
 electric circit, output is a light bulb. The light bulb is only switched on if both switches are activated. Hence the following table.
 
  | A  | B | Output    |
| :----: |   :----:   |  :---: |
|  0    |  0    | 0  |
| 0     | 1     | 0  |
| 1     | 0     | 0  |
| 1     | 1     | 1  |

The above denotes an AND gate.

Imagine another circuit that has a switch in parallel with a light bulb, if the switch 
is on, the light bulb is short circuit, hence it goes off. Whiles is the swith is open 
the light is on. This is known as the NOT logic operation

| A | Output    |
| :----: | :---: |
|  0    |  1  |
|  1    |  0  | 

In the old days, engineers used magneitc to control the switches, which was slow. Nowadays
we have the fameous TRANSITORs to replace the switch that is must faster. 

A cavet: Moore's law states that the number of transistor in a dense integrated circuit doubles
about every two years. Although it is an observation, we have largely followed it till recently....
Time for quantum computing to SHINE !!!!!



