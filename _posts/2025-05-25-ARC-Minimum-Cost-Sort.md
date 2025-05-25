---
title: "APIO-Bridges15"
date: 2025-05-02
layout: default
---

{% include mathjax.html %}
//I got lazy ~sick~ and didn't do IO for quite some time 🤡.  
link: https://atcoder.jp/contests/arc194/tasks/arc194_b

Abridged statement: the statement is 1 line so uhh no


We start by noting the cost of moving an element $P_i$ from its position $i$ in $P$ to its rightful position of $P_i$.  
Assuming $P_i > i$:  
The cost to do so will be $i + (i+1) + ... + (P_i-2) + (P_i-1)$
This is an arithmetic progression with a first term of $i$, a last term of $P_i-1$ and a total of $P_i-i$ terms.  
As such the cost to move $P_i$ into its "rightful" position will be: 

$$(\frac{P_i-i}{2})(i+P_i-1)$$  

Expanding we get:

$$(\frac{P_i^2 - P_i - i^2+i}{2}) = \frac{P_i^2 - i^2 - (P_i-i)}{2}= \frac{(P_i-i)(P_i+i)-(P_i-i)}{2} = \frac{(P_i-i)(P_i+i-1)}{2}$$  


[Code](https://atcoder.jp/contests/arc194/submissions/66169581)
