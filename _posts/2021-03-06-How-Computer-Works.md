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
 
 <h3 class="section-heading"> AND Gate , NOT, NAND, OR Gate</h3>
 
 Truth table to explain the concepts of AND & OR gate, Imagine A, and B are two switches in serie in a 
 electric circit, output is a light bulb. The light bulb is only switched on if both switches are activated. Hence the following table.
 
  | A  ||  B || Output    |
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

So what happens next is we pack these into individual modules, and give them fancy names "AND" and "NOT" gate.
We then link them up in a circuit that has the following truth table:


  | A  | B | Output    |
| :----: |   :----:   |  :---: |
|  0    |  0    | 1  |
| 0     | 1     | 1  |
| 1     | 0     | 1  |
| 1     | 1     | 0  |

Because of the existence of NOT gate, the turth table tells the opposite story of the first table. This is named as 
NAND gate. 

Alright, if we pack NAND gate into a separate unit and connect it with two NOT gates, we have the next truth table. 

  | A  | B | Output    |
| :----: |   :----:   |  :---: |
|  0    |  0    | 0  |
| 0     | 1     | 1  |
| 1     | 0     | 1  |
| 1     | 1     | 1  |

This can be a little confusing, but taking the first row as an eample, what it deos is the NOT gate trun an inupt A = 0 into 
A = 1 and B=0 into B = 1, they are then passed to the NAND  gate. According to the table above, for A = 1, B =1, the ouput is 0. Hence 
we have zero as the output. 

The above truth table denotes an OR gate.

Here is a summary of AND, NOT, NAND , OR logic operation. 

 <h3 class="section-heading"> Binary system  </h3>
 
 In decimal system, with a single digit we can express up to 9, with twop digits, we can do up to 19 and so...
 
 In binary system, a similar thing happens, but with a single digits can only express "0" and "1". That means, using the combination theory in mathemtics 
 we have the following table (basically 2 to the power of n, n is the nth digit):
 
 |  Number of Combination :    |  8         | 4       | 2    | 1    |
 |          :----:             |   :----:   |  :---: | :---: | :---: |
 |                             |    1       |   1    |   0   |    1   |
 
 so the above number means 1 x 8 + 4 x 1 + 2 x 0 + 1x 1 = 13
 
 <h3 class="section-heading"> Arithmetic sum, XOR, Adder and 4bits Adder </h3>
 
 The question is how do with repersent arithmetic sum for example 100011  + 000111? 
 To asnwer the question, we have to introduce the concept of Carry and Sum. 
 Carry is the number carried on when doing summation. for example adding two single bits, 1 + 1 has a carry of 1 and a sum of 0 (becasue of bunary system).
 
 Again, we can summarise the above using our friend Truth table: 
 
   | A  | B | Carry | Sum |
| :----: |   :----:   |  :---: | :---: |
|  0    |  0    | 0  | 0  |
| 0     | 1     |  0 | 1  |
| 1     | 0     | 0 | 1  |
| 1     | 1     | 1  | 0 |

If we take Carry column out, does it looks familiar? If not please have a look at the AND gate ? Yes it looks exactly the same as the AND gate. ohhhwoooo 
Keep that in mind and now look at the sum column. Unfortunately, it does not look like anything we did perviously, however, it is similar to a OR gate. 

So we need to turn the last output into 0, hopeful, it comes natural to you, all you need is to connet an NAND gate to check if both inputs are 1 and turn it
into 0. 

The conplete circuit has an OR gate (that does the Sum) and a NAND gate (that does the correction for the last row), with an AND gate to complete. This is known as
the exclusive or or XOR. This is for the SUM column. 

Now we are ready to do binary Sum, if we summarise the sum of two binary numbers in the table below: 

|  Carry | 0     | 0     |  1   |   1  |   1  |  0  |
| ------ | ----- |----- |----- |----- |----- |----- |
| First Number |1     | 0     |   0  |  0   |   1  |   1  |
| Second Number | 0     | 0     |   0  |  1   |   1  |  1   | 
| Sum | 1    | 0     |   1  |  0   |   1  |  0   | 

Therefore we are always adding three numbers together, what we need now is to construct an adder that takes care of binary summation process.
This adder is a bit tricky to describe in words therefore I am not goung to do so, if you are interested p0lease check out Sebastian's Youtube video 
[Exploring How Computers Work](https://www.youtube.com/watch?v=QZwneRb-zqA), at 10.30 mins. A hint is you need two XOR gates, two AND gates and an OR gate. 

The next steo is to use adder to construct a 4bit adder  that add two four bits binary numbers, I am not going to illustrate it here and please check out the video if you are interested.

I think so far you should have a good idea of how computer logic works, it is pretty smart to think about. Now the next big question is how substraction works. 

 <h3 class="section-heading"> Arithmetic Substraction  </h3>
 
 Let's stop here for NOW, A bit tried, and have other work to dm, will come back to it and complete it soon 
 07/03/2021
 
 
