---
layout:     post
title:      Solve log inequalities by changing log bases vs. using the same base
date:       2017-04-21GMT+8 20:26:14
summary:    complicated vs. less complicated
categories: [maths]
tags: [logarithm, inequalities]
---
$$1+\log_5\left(x^2+1\right)\ge \log_5\left(ax^2+4x+a\right)$$

$$a \in R$$ for which the following inequality is valid for all $$x \in R$$

we can solve it by

1. Using the same base
2. Change log bases.

The usual way and less complicated way is #1. But out of curiosity I wanted to test for #2.

Let's begin.

## Change log bases

$$\log_5 5 + \log_5(x^2+1) - \log_5 (ax^2+4x+a) \ge 0$$

$$\log_5\frac{5x^2+5}{ax^2+4x+a} \ge 0 \tag P$$

$$\frac{1}{\log_\frac{5x^2+5}{ax^2+4x+a}{5}} \ge 0$$

Nope, we can't do the inequality as $$\ge 0$$. Eg - $$\frac{1}{0.99999} \ge 1$$ It will never be 0. Let's change it to a new equation

$$\frac{1}{\log_\frac{5x^2+5}{ax^2+4x+a}{5}} \ge 1 \tag Q$$

$$\log_\frac{5x^2+5}{ax^2+4x+a}{5} > 0 \tag R$$

$$R$$ is a denominator of $$Q$$, thus it must be greater than $$0$$ and $$Q$$ shows that the fraction needs to be $$\ge 1$$. Hence, $$\log_\frac{5x^2+5}{ax^2+4x+a}{5} \in(0,1]$$.

Let's take an example and observe.

$$\log_2 4 = \frac{1}{\log_4 2}$$

$$2 = \frac{1}{\frac{1}{2}}$$

As you can see $$\frac{1}{2}\in (0,1]$$

If some number $$x$$ is $$x^{(0,1])} > 0$$ then $$x \ge 1$$


$$\frac{5x^2+5}{ax^2+4x+a} \ge 1 \tag S$$

$$
\begin{align}
5x^2+5 &\geq ax^2+4x+a  \tag 1\\
5x^2+5 &\ge 0   \tag 2\\
ax^2+4x+a &\gt 0  \tag 3
\end{align}
$$

We found the inequalities! As we'll observe later the inequalities are the same as the method 1 using the same base.

## Using the same base

Take from $$P$$ we can immediately get the inequalities. $$5^0=1$$ thus $$\frac{5x^2+5}{ax^2+4x+a} \ge 1$$.

Pheww, boy was that shorter!

Both methods have the same inequalities. Let's solve them up!

## Solve the inequalities

$$5x^2+5 \ge ax^2+4x+a \tag 1$$

$$
\begin{align}
5x^2+5 -ax^2-4x-a \ge 0\\
(5-a)x^2-4x+5-a \ge 0\\
\end{align}
$$

The graph is concave up and has a minimum point because the whole equation is $$\ge 0$$ therefore $$5-a>0$$. Find the minimum vertex point

$$
\begin{align}
x &=\frac{-b}{2a}\\
& = -\frac{-4}{2(5-a)}\\
& = \frac{2}{5-a}
\end{align}
$$

$$\begin{align}
(5-a)\left(\frac{2}{5-a}\right)^2 - 4\left(\frac{2}{5-a}\right) + 5-a \ge 0\\
\frac{4}{5-a}- \frac{8}{5-a} + 5-a \ge 0\\
4-8+(5-a)^2 \ge 0\\
(5-a)^2 \ge 4\\
5-a \ge 2\\
a \le 3
\end{align}
$$

We don't need to do the equation $$2$$ because if $$a>1$$ then $$\log_a{(f(x))} \ge \log_a{(g(x))}$$ is equivalent to
$$
\begin{cases}
f(x) \gt g(x)\\
f(x) \gt 0\\
g(x) \gt 0\\
\end{cases}
$$

If $$g(x) \gt 0$$ then automatically $$f(x) \gt 0$$.

In this case the original equation is $$\log_5 5x^2+5 \ge \log_5 ax^2+4x+a$$. Clearly $$ax^2+4x+a \gt 0$$


$$
\begin{align}
ax^2+4x+a \gt 0  \tag 3\\
x =\frac{-b}{2a}\\
x = \frac{-4}{2a}\\
x = \frac{-2}{a}\\
{ a\left( \frac { -2 }{ a }  \right)  }^{ 2 }+ {4\left(\frac{-2}{a} \right)}+a \gt 0\\
\frac{4}{a} - \frac{8}{a} + a^2 \gt 0\\
a^2 \gt 4\\
a \gt 2
\end{align}
$$

$$a \in (2,3]$$

$$
\begin{align}
(5-3)x^2-4x+5-3 \ge 0\\
x^2-2x+1 \ge 0\\
x=1\\
(5-2)x^2-4x+5-2 \ge 0\\
x=undefined
\end{align}
$$

When $$a=3, x=1$$ and $$a \in [2, 3)$$ , $$ x=imaginary$$

$$
\begin{align}
\log_5{5} +\log_5{2} \ge \log_5\left(3(1)+4(1)+3\right)\\
\log_5{10} \ge \log_5{10} \tag*{$\blacksquare$}
\end{align}
$$













