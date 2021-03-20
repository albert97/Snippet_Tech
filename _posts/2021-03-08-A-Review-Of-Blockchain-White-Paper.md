---
layout:     post
title:      "A Review of the Blockchain/Bitcoin white paper "
date:       2021-03-06 12:00
author:     "Albert"
category:   techblog
tags:       [Computing, Blockchain] 
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
 In this post, I will review the Blockchain white paper - [Bitcoin: A Peer-to-Peer Electronic Cash System](https://bitcoin.org/bitcoin.pdf). The paper is regarded 
 as the first system utilising Blockchain technology. My goal is to understand Blockchain as a technology forward, and it has nothing to do with investing in Bitcoins. For the later, reddit may be a great place

 <h2 class="section-heading"> Some words before I start:  </h2>
 After reading the paper, unsurprisingly, the extent of the topic may be beyond my comprehension. I therefore, will try to address the concepts of Hash, Distributed Computing, maybe B-money before moving into Blockchain. From the paper, it seems to be Bitcoin was purely an incentive scheme, and Blockchain was the main concept of the paper. Hence, I am a little puzzled why the title were "Bitcoin (Rather than Blockchain): A Peer-to-Peer Electronic Cash System". anyway,let's dive in.
 
 <h2 class="section-heading"> Hash Function:  </h2>
 A hash function is any function that can be used to map data of arbitrary size to fixed-size values. The values returned by a hash function are called hash values, hash codes, digests, or simply hashes. The values are usually used to index a fixed-size table called a hash table. Use of a hash function to index a hash table is called hashing or scatter storage addressing.
 
The paper proposed the usage of SHA-256 as a way to allow extensive computational work (therefore acting as a proof of work). SHA-256 falls into the family of SHA-2. SHA-2 (Secure Hash Algorithm 2) is a set of cryptographic hash functions designed by the United States National Security Agency (NSA) and first published in 2001. They are built using the Merkle–Damgård construction, from a one-way compression function itself built using the Davies–Meyer structure from a specialized block cipher.

SHA-256 is a novel hash functions computed with 32-bit words. Here I need to explain what a one-way compression system is and how Merkle–Damgård construction and Davies-Meyer structure play the part. 


 <h2 class="section-heading"> One-way compression system, Merkle–Damgård construction and Davies-Meyer structure:  </h2>
In cryptography, a one-way compression function is a function that transforms two fixed-length inputs into a fixed-length output. The transformation is "one-way", meaning that it is difficult given a particular output to compute inputs which compress to that output. One-way compression functions are not related to conventional data compression algorithms, which instead can be inverted exactly (lossless compression) or approximately (lossy compression) to the original data. 

A one-way function is a function that is easy to compute but hard to invert. A one-way compression function (also called hash function) should have the following properties:
1.Easy to compute: If you have some input(s), it is easy to calculate the output.
2.Preimage-resistance: If an attacker only knows the output it should be infeasible to calculate an input. In other words, given an output h, it should be unfeasible to calculate an input m such that hash(m)=h;
3.Second preimage-resistance: Given an input m1 whose output is h, it should be infeasible to find another input m2 that has the same output h i.e. hash(m1) does not equal to hash(m2).
4.Collision-resistance: It should be hard to find any two different inputs that compress to the same output i.e. an attacker should not be able to find a pair of messages m1 does not equal to m2. such that hash(m1) does not equal to hash(m2).  Due to the birthday paradox (see also birthday attack) there is a 50% chance a collision can be found in time of about 2^(n/2)  where n is the number of bits in the hash function's output. An attack on the hash function thus should not be able to find a collision with less than about 2^(n/2) work. 

I think Merkle–Damgård construction and Davies-Meyer structure deserved separates posts, and to simplify things (with helpds from [Wikipedia](https://en.wikipedia.org/wiki/One-way_compression_function#cite_note-1) ), a few brief words on these two topics:

Merkle–Damgård construction consists of four parts: starting from initial values, also called initalisation vector (IV), it is a fixed value (algorithm or implementation specific). The next block is the compression (or compacting) function f that takes the result so far, combines it with the message block, and produces an intermediate result. There can be a chain of these f function. The last part is a finalisation block tha padds the results from a chain of f with zeros.  his is crucial to the security of this construction
<html>
  <body>

<img src="{{ "/assets/img/content/post-example/ Merkle–Damgård.png" | absolute_url }}" alt="bay" class="post-pic"/>

    </body>
</html>
 <h2 class="section-heading"> Referenece:  </h2>
 [SECRECY, AUTHENTICATION, AND PUBLIC KEY SYSTEMS, Ralph Charles Merkle, 1979](http://www.merkle.com/papers/Thesis1979.pdf)
