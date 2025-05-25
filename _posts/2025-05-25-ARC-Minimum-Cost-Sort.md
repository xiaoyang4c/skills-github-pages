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

$$\frac{P_i^2 - P_i - i^2+i}{2} = \frac{P_i^2 - i^2 - (P_i-i)}{2}= \frac{(P_i-i)(P_i+i)-(P_i-i)}{2} = \frac{(P_i-i)(P_i+i-1)}{2}$$  

Now we can make another ~wild guess~ observation:
We should move the elements to their respective position in descending order. The reason I made this guess is just that it will not mess up the ordering between the elements when you just take an element and keep swapping it with the element to the right till unable to do so (which is when it is already in its place).  
I have no clue for the proof 😅😎.  
This conveniently also ensures that $P_i$ will always be $>= i$  hence allowing us to use our formula without any additional cases.  


The only additional thing we have to note is that after moving an element all the way to its sorted position, all the elements to the right of that element will have their position in the array decreased by 1 (shifted left).  
This implies that we need a way to constantly update the position $j$ of element $P_i$.  


To do this we can use a "classic" trick with a fenwick tree (that I admittedly forgot when doing this problem 🤡):  
Consider building a fenwick tree consisting an array of 1s.  
We aim to let the position $j$ of an element $P_i$ be $query(pos[P_i])$ where pos[x] is the initial position of x in the permutation $P$.  
Notice that as we iterate through $P_i$ in descending order and move them towards the right, we can just update $pos[P_i]$ to be 0 in the array so that all the elements to its right can be "shifted" to the left by 1.  
This ensures that when we run $query(pos[x])$ after moving $P_i$ ($pos[P_i]<x$) it will be 1 less than before moving $P_i$.  

Thus we just have to find  $\sum \frac{(P_i-j)(P_i+j-1)}{2}$ as we iterate $P_i$ in descending order (from $N$ to $1$) and obtain $j$ with $query(pos[P_i])$ while maintaining the fenwick tree.  



I believe that the fenwick tree trick is also used in IOI 2019 shoes (https://oj.uz/problem/view/IOI19_shoes) and EGOI 2021 Luna Likes Love (https://codeforces.com/gym/103148/problem/B). A bit embarrassing for me to not instantly see this considering I used the EGOI question in a lecture during Deccourse oops. 


[Code](https://atcoder.jp/contests/arc194/submissions/66169581)
