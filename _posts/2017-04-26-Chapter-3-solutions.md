---
layout:     post
title:      Chapter 3 solutions
date:       2017-04-26GMT+8 12:14:43
summary:    Introduction to Algorithms by CLRS.
categories: [algorithms]
tags: [Introduction to Algorithms by CLRS, QA]
---
# Introduction to Algorithms by CLRS

## Exercises

### 3.1-1
>Let $$f(n) + g(n)$$ be asymptotically nonnegative functions. Using the basic definition of $$\Theta$$-notation, prove that $$\max(f(n), g(n)) = \Theta(f(n) + g(n))$$.


$$0 \le c_1{n} \le max(f(n) + g(n)) \le c_2{n}$$

$$0 \le c_1\left(f(n) + g(n)\right) \le max\left(f(n)+g(n)\right) \le c_2\left(f(n)+g(n)\right)$$

$$
f(n) + g(n) \ge 0\\
f(n) + g(n) \ge max(f(n) + g(n))\\
\frac{1}{2}\left(f(n) + g(n)\right) \le max(f(n) + g(n))\\
\frac{1}{2}\left(f(n) + g(n)\right) \le max\left(f(n)+g(n)\right) \le \left(f(n)+g(n)\right)\\
$$

## 3.1-2
>Show that for any real constants $$a$$ and $$b$$, where $$b > 0$$,<br>
$$(n + a)^b = \Theta(n^b)$$

$$a$$ could be $$-0.5$$. But the difinition of $$\Theta(g(n))$$ : $$0\le c_1{g(n)}\le f(n)\le c_2 {g(n)}$$ for all $$n \ge n_0$$. Whatever value $$a$$ is, the equation will always be $$\ge 0$$ as it is raised to the positive power of $$b$$. Let $$a = \lvert a \rvert$$

$$f(n) = (n+a)^b$$.

Prove that $$0 \le c_1{n^b} \le f(n) \le c_2{n^b}$$ for all $$ n \ge n_0$$

$$
\begin{align}
n+|a| \le 2n\\
\therefore (n+a)^b \le (2n)^b
\end{align}
$$

$$
\begin{align}
n+|a| \ge n \\
\therefore (n+a)^b \ge n^b
\end{align}
$$

$$
n^b \le (n + a)^b \le (2n)^b\\
c_1 = 1, c_2=2^b, n_0\ge \lvert a \rvert
$$

## 3.1-3
>Explain why the statement, "The running time of algorithm A is at least $$O(n^2)$$" is meaningless.

Big $$O$$ is the asymptotic upper bound. "At least" means the asymtotic lower bound $$\Omega$$.

## 3.1-4
>Is $$2^{n+1} = O(2^n)$$? Is $$2^{2n} = O(2^n)$$?

$$
c_1 n \le 2^{n+1} \le c_2 2^n\\
2^{n+1} \le c_2 2^n\\
2^{n+1-n} \le c_2 2^{n-n}\\
2^{1} \le c_2\\
c_1 n \le 2^{n+1}\\
\therefore 2^{n+1} = O(2^n)
$$

$$
c_1 n \le 2^{2n} \le c_2 2^n\\
2^{2n} \le c_2 2^n\\
2^{2n-n} \le c_2 2^{n-n}\\
2^{n} \ne c_2\\
\therefore 2^{2n} \ne O(2^n)
$$

## 3.1-5
> Prove Theorem 3.1

$$f(n) = \Theta(g(n)$$ is asymptotic tight bound. The upper bound is the $$f(n) = O(g(n))$$ and the lower bound is the $$f(n) = \Omega(g(n))$$

$$
0 \le c_1 g(n) \le f(n)\\
0 \le f(n) \le c_2 g(n)\\
\therefore 0 \le c_1 g(n) \le f(n) \le c_2 g(n)
$$

## 3.1-6
>Prove that the running time of an algorithm is $$\Theta(g(n))$$ if and only if its worst-case running time is $$O(g(n))$$ and its best-case running time is $$\Omega(g(n))$$

$$
0 \le c_1 g(n) \le f(n)\\
0 \le f(n) \le c_2 g(n)\\
\therefore 0 \le c_1 g(n) \le f(n) \le c_2 g(n)
$$

## 3.1-7
>Prove $$o(g(n)) \cap \omega(g(n))$$ is the empty set.

## 3.1-8
>We can extend our notation to the case of two parameters n and m that can go to infinity independently at different rates. For a given function $$g(n, m)$$ we denote $$O(g(n, m))$$ the set of functions:<br><br>
$$
\begin{align}
     O(g(n, m) = \lbrace f(n, m):
       &\text{ there exist positive constants } c, n_0, \text{and } m_0 \\
       &\text{ such that } 0 \leq f(n, m) \leq cg(n, m) \\
       &\text{ for all } n \geq n_0 \text{ or } m \geq m_0.
   \end{align}
$$<br><br>
Give corresponding definitions for $$\Omega(g(n, m))$$ and $$\Theta(g(n, m))$$.









