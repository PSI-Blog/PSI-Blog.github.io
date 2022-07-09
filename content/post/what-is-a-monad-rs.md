---
title: "WTF is a Monad (Explained with Rust)"
date: 2022-07-04T21:51:48+01:00
draft: true
tags: ["Maths","Rust","Haskell","Programming"]
author: "Diogo Valério"
math: true
---
<!-- f9b42b2acadb4dd8b56c35fdb18f8d24 -->


Have you ever wondered what the hell is a Monad? If yes this post will explain it to you like you're five.

> "A **monad** is just a **monoid** in the category of **endofunctors**"</p>
> -- <cite>Saunders Mac Lane[^1]</cite>

[^1]: [Categories for the Working Mathematician](https://en.wikipedia.org/wiki/Categories_for_the_Working_Mathematician)

<iframe width="640" height="480" src="https://www.youtube.com/embed/NM3TU5VfEMM" title="Bart Simpson learns Haskell" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## What is a monoid?

Let's see: 

If you have studied math you have seen symbols like this $\mathbb{Z}$, $\mathbb{R}$, or $\mathbb{Q}$. This are just groups of numbers.

A monoid just is a **set/semi-group** of numbers like this, with an **identity** element (let's call it $I$).

For example the operator (**+**):

If we have a set of numbers: $\mathbb{M} = [0,1,2,3,4,5,6,7]$

<!-- The (**+**) operator uses 2 parameters **a** and **b**. -->

For every $x$ in $\mathbb{M}$ 

$x + I = x = I + x$

If you watch closely you can see that the identity element $I$ can be presumed to be 0, so:

$x + 0 = x = 0 + x$

The monoid 




<!-- <iframe src="https://www.desmos.com/calculator/r47enguyzb?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe> -->
