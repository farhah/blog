---
layout:     post
title:      Chapter 15 solutions - Dynamic Programming
date:       2017-06-04GMT+8 01:19:00
summary:    Introduction to Algorithms by CLRS.
categories: [algorithms]
tags: [Introduction to Algorithms by CLRS, QA]
---

### From pseudo-code to python

#### Recursive top-down implementation
```python
p = [0, 1, 5, 8, 9, 10, 17, 17, 20, 24, 30]

def cut_rod(p, n):
    if n == 0:
        return 0
    q = p[0]
    for i in range(1, n+1):
        q = max(q, p[i] + cut_rod(p, n-i))
    return q


res = cut_rod(p, 4)
print(res)
```



#### Memoized cut rod
```python
def memoized_cut_rod(p, n):
    r = [-1 for _ in range(n + 1)]

    return memoized_cut_rod_aux(p, n, r)


def memoized_cut_rod_aux(p, n, r):
    if r[n] >= 0:
        return r[n]
    q = p[0]
    if n == 0:
        q = 0
    else:
        for i in range(1, n + 1):
            q = max(q, p[i] + memoized_cut_rod_aux(p, n - i, r))

    r[n] = q
    return q

res = memoized_cut_rod(p, 4)
print(res)
```


#### Bottom up cut rod
```python
def bottom_up_cut_rod(p, n):
    r = [0 for _ in range(n + 1)]

    for j in range(1, n + 1):
        q = p[0]
        for i in range(1, j + 1):
            q = max(q, p[i] + r[j - i])
        r[j] = q

    return r[n]

res = bottom_up_cut_rod(p, 4)
print(res)
```

### 15.1-1
> Show that equation (15.4) follows from equation (15.3) and the initial condition $$T(0)=1$$.

$$
\begin{align}
T(n) = 2^n \tag{15.4}\\
T(n) = 1 + \sum_{j=0}^{n-1} T(j) \tag{15.3}\\
\end{align}

$$

Binomial of one variable [refer here](https://en.wikipedia.org/wiki/Binomial_theorem)
$$T(j)$$ counts the number of calls (including recursive calls) due to the call CUT-ROD.
It also means how many ways we can cut the rod. 

$$
\begin{align}
\sum_{j=0}^{n-1} \binom{n-1}{j} x^j & = \binom{n-1}{0}x^0 + \binom{n-1}{1}x^1 + \binom{n-1}{2}x^2 + \cdots + \binom{n-1}{j}x^{n-1}\\
& = (1+x)^{n-1} \\
\end{align}
$$

Let $$x = 1$$ so we can get $$2^{n-1}$$


$$
\sum_{j=0}^{n-1} \binom{n-1}{j} 1^j = 2^{n-1} \\
$$

Now we want to run ***how many ways to cut the rod*** from $$0$$ until $$n-1$$.
This recursion tree has $$2^n nodes$$

[incase I forgot, the sum of power of 2 is a geometric series](https://math.stackexchange.com/questions/1990137/the-idea-behind-the-sum-of-powers-of-2)

$$
\sum_{j=0}^{n-1} 2^j = 2^0 + 2^1 + 2^2 + 2^3 \cdots 2^{n-1} = 2^n - 1 \\

\begin{align}
T(n) = 1 + \sum_{j=0}^{n-1} 2^j\\
T(n) = 1 + 2^n - 1 = 2^n\\
\end{align}

$$




### 15.1-2
> Show, by means of a counterexample, that the following "greedy" strategy does not always determine an optimal way to cut rods. Define the ***density*** of a rod of length $$i$$ to be $$p_i/i$$, that is, its value per inch. The greedy strategy for a rod of length $$n$$ cuts off a first piece of length $$i$$, where $$1 \le i \le n$$, having maximum density. It then continues by applying the greedy strategy to the remaining piece of length $$n - i$$.


### 15.1-3 
> Consider a modiﬁcation of the rod-cutting problem in which, in addition to a price $$p_i$$ for each rod, each cut incurs a ﬁxed cost of $$c$$. The revenue associated with a solution is now the sum of the prices of the pieces minus the costs of making the cuts. Give a dynamic-programming algorithm to solve this modiﬁed problem.

```python
def bottom_up_cut_rod(p, n, c):
    r = [0 for _ in range(n + 1)]

    for j in range(1, n + 1):
        q = p[0]
        for i in range(1, j + 1):
            q = max(q, p[i] + r[j - i] - c)
        r[j] = q

    return r[n]

res = bottom_up_cut_rod(p, 4, 0.5)
print(res)
```

### 15.1-4 
> Modify MEMOIZED-CUT-ROD to return not only the value but the actual solution, too.


### 15.1-5 
> The Fibonacci numbers are deﬁned by recurrence (3.22). Give an $$O(n)$$-time dynamic programming algorithm to compute the $$n$$th Fibonacci number. Draw the subproblem graph. How many vertices and edges are in the graph?

```python
def fibonacci_dynamic(n):
    a, b = 0, 1
    while n > 0:
        a, b = b, a + b
        n -= 1
    return a

res = fibonacci_dynamic(8)
print(res)
```