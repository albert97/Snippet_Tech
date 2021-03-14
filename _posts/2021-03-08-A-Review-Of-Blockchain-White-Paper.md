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

SHA-256 is a novel hash functions computed with 32-bit words. Here I need to explain what a one-0way compression system is and how Merkle–Damgård construction and Davies-Meyer structure play the part. 
