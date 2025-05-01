---
title: "APIO-Bridges15"
date: 2025-04-25
layout: default
---

{% include mathjax.html %}


link: https://codebreaker.xyz/problem/bridge_apio15

Abridged statement: lazy, and the statement is quite clear 🤡

$K=1$ case:  

Let the position of the bridge be $x$.  
If citizen $i$'s office and house are in the same zone, the distance that citizen has to travel is obviously $|S_i-T_i|$.  
Now let us consider the case where citizen $j$'s office and house are in different zones.  
Citizen $j$ would have to travel from their house at $S_j$ to the bridge at $x$, then travel from the bridge at $x$ to their office at $T_j$.  
Hence the distance traveled by citizen $i$ will be $|S_j-x|+|T_j-x|+1$ as the width of the river is equal to $1$ too.
As such the total distance traveled by all the citizens will be:  

$$\sum (|S_i-T_i|) + \sum (|S_j-x| + |T_j-x| + 1)$$ 

for each citizen $i$ (whose office and house are in the same zone) and $j$ (whose office and house are in different zones).

Now we just have to figure out how to choose $x$.  
We shall boldly guess that $x$ shall be the median in the set of all $S_j$ and $T_j$. Turns out this will minimise $\sum (|S_j-x| + |T_j-x| + 1)$.

Proof: 
We first reduce the problem to:  
Given a sorted array $A$ of $n$ numbers, find a value $x$ such that $\sum |A[i] - x|$ will be minimised.  
Assume $y$ is the optimal value for $x$ and $y != A[\floor{\frac{n}{2}}] $  
This implies that there will be $>=\frac{n}{2}$ values of $A[i]$ that are either greater than $y$ or smaller than $y$.
If 
