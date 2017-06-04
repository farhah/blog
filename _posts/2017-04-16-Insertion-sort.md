---
layout:     post
title:      Chapter 2 - 2.1-2
date:       2017-04-16GMT+8 09:27:00
summary:    Insertion sort nonincreasing.
categories: cs
tags: [algorithm, tutorial]
---
`[^1]`
```python
def insertion_sort_nonincresing(A):
    for i in range(1, len(A)):
        key = A[i]
        j = i - 1
        while j >= 0 and A[j] < key:
            A[j + 1], A[j] = A[j], key
            j -= 1
    return A


print(insertion_sort_nonincresing([5, 2, 3, 4]))
```
lala

$$a^2 + b^2 = c^2$$

$$ \mathsf{Data = PCs} \times \mathsf{Loadings} $$

$$ \mathbf{X}\_{n,p} = \mathbf{A}\_{n,k} \mathbf{B}\_{k,p} $$


`test`
we have `\(x_1 = 132\)` and `\(x_2 = 370\)` and so .


And test a display math without equaltion number:

$$ \frac{\delta E_{x}}{\delta t} = \frac{\delta f(z-ct)}{\delta t} = f^{\prime}(z - ct)\Big(\frac{\delta(z-ct)}{\delta t}\Big) = -c*f^{\prime}(z - ct) $$


$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$

$$
\begin{equation}
   E = mc^2
\end{equation}
$$
