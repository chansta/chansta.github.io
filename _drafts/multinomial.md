---
layout: post
title: Generating multinomial terms with loop and recursion
---

Background
==========

Consider the multinomial expansion:

$$ \left ( \sum^n_{i=1} x_i \right )^k = \sum_{k_1=0}^k \ldots \sum_{k_{n-1}=0}^{k_{n-2}} \left [ \frac{k!}{\prod_{i=1}^{n-1} k_i!} \prod ^n_{i=1} x_i^{\Delta k_i} \right ] $$ 


where \\( \Delta k_i = k_{i+1} - k_i \\) with \\( k_0 = k \\) and \\( k_n = 0 \\). 

Note that 

\\[ \frac{k!}{\prod_{i=1}^{n-1} k_i!} \\]

represents the number of repeatitions of the term \\( \prod_{i=1}^n x_i^{\Delta k_i} \\) for a given tuple  \\( \left ( \Delta k_1, \ldots, \Delta k_n \right ) \\). 

An example may help to demonstrate this. Set \\( n=2 \\) then this is simply the binomial expansion. That is, 

\\[ \left ( x_1 + x_2 \right )^k = \sum^k_{i=0} \frac{k!}{i! (k-i)!} x_1^i x_2^{k-i} \\]

Note that the exponents of both terms on the right hand side form a set of tuples \\( (i, k-i ) \\) for \\( i = 0,\ldots k \\). 

Assuming we are interested in generating all the unique terms on the right hand side. That is, we are interested in generating all the tuples \\( \left ( \Delta k_1, \ldots, \Delta k_n \right ) \\). 

The Naive Approach
==================

The problem is relatively straightforward to solve for any given \\( k \\) and \\( n \\) using mulitple "for" loops. The code below shows the solution for \\( k=4 \\) with with \\( n = 4 \\). 

 {% comment %}{% gist chansta/f37503258f8de7c056a857adefc3de83 multinomial_naive.py%} {% endcomment %}
<script src="https://gitlab.com/snippets/1746200.js"></script>

However, the value of \\( k \\) dictates the number of loops required. This makes it difficult to allow user-specified \\( k \\). A more flexible way to accommodate user-specified \\( k \\) is 

{% comment %}{% gist chansta/f37503258f8de7c056a857adefc3de83 multinomial_recursion.py%}{% endcomment %}
<script src="https://gitlab.com/snippets/1746201.js"></script>
Note that this is a mixed of "for" loop and recursion. Or

