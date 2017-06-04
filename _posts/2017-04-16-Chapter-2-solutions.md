---
layout:     post
title:      Chapter 2 solutions
date:       2017-04-16GMT+8 12:16:21
summary:    Introduction to Algorithms by CLRS.
categories: [algorithms]
tags: [Introduction to Algorithms by CLRS, QA]
---
### Introduction to Algorithms by CLRS.


### Insertion sort from pseudo code to python
```python
def insertion_sort(A):
    for i in range(1, len(A)):
        key = A[i]
        j = i - 1
        while j >= 0 and A[j] > key:
            A[j + 1], A[j] = A[j], key
            j -= 1
    return A


print(insertion_sort([5, 2, 3, 4]))
```
---

### 2.1-1
>Using Figure 2.2 as a model, illustrate the operation of INSERTION-SORT on the array A(31, 41, 59, 26, 41, 58)

---

### 2.1-2
>Rewrite the INSERTION-SORT procedure to sort into nonincreasing instead of non- decreasing order.

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

---

### 2.1-3
>Consider the __searching problem:__<br>
Input: A sequence of n numbers $$ A = (a_{1}, a_{2}, a_{3}, .., a_{n}) $$ and a value $$ v $$ .<br>
Output: An index $$ i $$ such that $$ v =  A[i] $$ or the special value NIL if $$ v $$ does not apper in $$ A$$<br><br><br>
Write pseudocode for linear search, which scans through the sequence, looking for $$ v $$ . Using a loop invariant, prove that your algorithm is correct. Make sure that your loop invariant fulfills the three necessary properties.

```python
def linear_search(A, val):
    for i in range(len(A)):
        if A[i] == val:
            return A[i]

    return None

print(linear_search([5, 2, 3, 4], 4))
```

---

### 2.1-4
>Consider the problem of adding two $$ n $$-bit binary integers, stored in two $$ n $$-element arrays $$ A $$ and $$ B $$. The sum of the two integers should be stored in binary form in an $$ (n+1) $$element array C. State the problem formally and write pseudocode for adding the two integers.


```python
def add_2bin(A, B):
    # both A and B has the same length n
    C = []
    carry = 0
    for i in range(len(A) - 1, 0 - 1, -1):
        add = int(bin(A[i] + B[i] + carry)[2:])
        add = map(int, str(add))
        if len(add) > 1:
            carry = add[0]

        for x in range(len(add) - 1, 0 - 1, -1):
            C.insert(x, add[x])

    return C

print(add_2bin([1, 0], [1, 0]))
```

---

### 2.2-1
>Express the function $$ n^3 = 1000 - 100n^2 - 100n + 3 $$ in terms of $$ \Theta $$-notation.

$$ n^3 = \Theta n $$

---

### 2.2-2
>Consider sorting n numbers stored in array $$ A $$ by first finding the smallest element of $$ A $$  and exchanging it with the element in $$ A[1] $$. Then find the second smallest element of $$ A$$ and exchange it with $$ A[2] $$. Continue in this manner for the first $$ n - 1 $$ elements of $$ A$$. Write pseudocode for this algorithm, which is known for selection sort. What loop invariant does this algorithm maintain? Why does it need to run for only the first $$ n - 1 $$ elements, rather than for all $$ n $$ elements? Give the best case and worst case running times of selection sort in $$\Theta$$-notation.

```python
def selection_sort(A):
    for i in range(len(A) - 1):
        smallest = A[i]
        for j in range(i + 1, len(A)):
            if A[j] < smallest:
                smallest = A[j]
                index_smallest = j
        A[i], A[index_smallest] = smallest, A[i]

    return A

print(selection_sort([5, 4, 3, 2, 8, 0, 8, 11, 1]))
```

---

### 2.2-3
>Consider linear search again (see Exercise 2.1-3). How many elements of the input sequence need to be checked on the average, assuming that the element being searched for is equally likely to be any element in the array? How about in the worst case? What are the average-case and worst-case running times of linear search in $$\Theta$$-notation? Justify your answers.

worst case: checking every n element to compare with the search value.<br><br>
average case: $$\frac{n}{2}$$<br><br>
worst case: $$n$$.<br><br>
Both of them are $$\Theta n$$

---

### 2.2-4
>How can we modify almost any algorithm to have a good best-case running time?

when the elements are pre-sorted we can have a good base-case running time.

---

### Merge sort from pseudo code to python

```python
def merge(left, right):
    result = []
    i, j = 0, 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result += left[i:]
    result += right[j:]
    return result

def merge_sort(A):
    if len(A) < 2:
        return A
    mid = len(A) // 2
    L = A[:mid]
    R = A[mid:]
    return merge(merge_sort(L), merge_sort(R))

print(merge_sort([5, 4, 8, 7, 1]))
```

### Merge sort from pseudo code in the book
```python
def merge2(A, p, q, r):
    n1 = q - p + 1
    n2 = r - q
    L, R = [], []

    for i in range(n1):
        L.append(A[p + i])
    for j in range(n2):
        R.append(A[q + j + 1])
    L.append(float('inf'))
    R.append(float('inf'))
    # print('p {}, q {}, r {}, n1 {}, n2 {}, L {}, R {}').format(p, q, r, n1, n2, L, R)
    i = j = 0
    for k in range(p, r + 1):
        if L[i] <= R[j]:
            A[k] = L[i]
            i += 1
        else:
            A[k] = R[j]
            j += 1


def merge_sort2(A, p, r):
    if p < r:
        q = (p + r) // 2  # mid
        # print('mid is q - {}, p - {}, r - {}').format(q, p, r)
        merge_sort2(A, p, q)  # A[p:q+1]
        # print('merge sort right')
        merge_sort2(A, q + 1, r)  # A[q+1+1:r]
        merge2(A, p, q, r)


A = [5, 4, 8, 7, 1]
merge_sort2(A, 0, len(A) - 1)
print(A)
```

---

# 2.3-1
>Using Figure 2.4 as a model, illustrate the operation of merge sort on the array $$ A = [3, 41, 52, 26, 38, 57, 9, 49] $$

 __L__[3, 41] . __R__[26, 52] $$\vert \vert \vert$$ __L__[38, 57] . __R__[9, 49] <br>
__L__[3, 26, 41, 52] . __R__[9, 38, 49, 57]<br>
[3, 9, 26, 38, 41, 49, 52, 57]

---

# 2.3-2
>Rewrite the MERGE procedure so that it does not use sentinels, instead stopping once either array L or R has had all its elements copied back to A and then copying the remainder of the other array back into A

---

# 2.3-3
>Use mathematical induction to show that when $$n$$ is an exact power of 2, the solution of the recurrence<br>
$$
T(n) = \left\{\begin{array}{ll}
2 & if n=2 \\
2T(\frac{n}{2})+n & if n=2^k, for & k>1 \\
\end{array}
\right.
$$<br><br>
is $$ T(n)=nlogn$$

Statement:<br>
$$n=2^i$$<br>
$$T\left(n\right)=T\left(2^i\right)=2^ilog2^i$$<br><br>
Base:<br>
$$T\left(2\right)=T\left(2^1\right)=2log2$$<br><br>
Hypothesis:<br>
$$ T\left(k\right)=T\left(2^j\right)=2^jlog2^j$$<br><br>
Induction:<br>
$$T\left(k+1\right)=T\left(2^{j+1}\right)=2^{j+1}log2^{j+1}$$<br><br><br>
$$2T\left(\frac{2^{j+1}}{2}\right)+2^{j+1} $$<br><br>
$$=2T\left(2^j\right)+2^{j+1}$$<br><br>
$$=2.2^jlog2^j+2^{j+1}$$<br><br>
$$=2^{j+1}.log2^j+2^{j+1}$$<br><br>
$$=2^{j+1}.log2^j+2^{j+1}$$<br><br>
$$=2^{j+1}\left(log2^j+1\right)$$<br><br>
$$=2^{j+1}\left(log2^j+log2\right)$$<br><br>
$$=2^{j+1}\left(log2^{j+1}\right)$$<br><br>

---

# 2.3-4
>We can express insertion sort as a recursive procedure as follows. In order to sort $$A[1..n]$$, we recursively sort $$ A[1..n-1]$$ and then insert $$A[n]$$ into the sorted array $$A[1..n-1]$$. Write a recurrence for the running time of this recursive version of insertion sort.


$$
T(n) =
\begin{cases}
1  & n=1 \\
T(n-1)+n & n>1
\end{cases}
$$

---

# 2.3-5
>Referring back to the searching problem (see Exercise 2.1-3), observe that if the sequence $$A$$ is sorted, we can check the midpoint of the sequence against $$v$$ and eliminate half of the sequence from further consideration. The binary __search__ algorithm repeats this procedure, halving the size of the remaining portion of the sequence each time. Write pseudocode, either iterative or recursive, for binary search. Argue that the worst-case running time of binary search is $$\Theta(lg n)$$

```python
def binary_search(A, val):
    mid = (len(A) // 2) - 1
    if mid < 0:
        return False

    if A[mid] == val:
        return True
    elif A[mid] < val:
        binary_search(A[mid + 1:], val)
    elif A[mid] > val:
        binary_search(A[:mid], val)

print(binary_search([1, 4, 5, 7, 8, 9, 10], 5))
```

Binary search array must be pre-sorted.

$$
T(n) =
\begin{cases}
1  & n=1 \\
T(\frac{n}{2})+ C & n>1
\end{cases}
$$

$$
\begin{align}
\cssId{line1a}{\frac{n}{2^i}} &\cssId{line1b}{ = 1} \\
\cssId{line1a}{n} &\cssId{line1b}{ = 2^i} \\
\cssId{line1a}{\log_2 n} &\cssId{line1b}{ = i} \\
& \therefore \Theta(log_2 n)
\end{align}
$$

---

# 2.3-6
>Observe that the while loop of lines 5–7 of the INSERTION-SORT procedure in Section 2.1 uses a linear search to scan (backward) through the sorted subarray $$A[1..j-1]$$. Can we use a binary search (see Exercise 2.3-5) instead to improve the overall worst-case running time of insertion sort to $$\Theta(n lg n)$$?

No because all the array elements before the current index need to be shifted in order to place the element of the current index to its correct position. Hence $$\Theta(n^2)$$

If perform binary search on $$A[0..j-1]$$, where $$j$$ is the current element, and we found $$ j <$$ all elements in $$A[0..j-1]$$. The two elements will just need to be swapped, then the array will never be corrected.

---

# 2.3-7 $$\star$$
>Describe a $$\Theta(n log n)$$-time algorithm that, given a set $$S$$ of $$n$$ integers and another integer $$x$$, determines whether or not there exist two elements in $$S$$ whose sum is exactly $$x$$.

```python
def sum_x(A, x):
    # need to sort the array. Merge sort is nlogn

    def merge(left, right):
        result = []
        i, j = 0, 0
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                result.append(left[i])
                i += 1
            else:
                result.append(right[j])
                j += 1
        result += left[i:]
        result += right[j:]
        return result

    def merge_sort(A):
        if len(A) < 2:
            return A
        mid = len(A) // 2
        L = A[:mid]
        R = A[mid:]
        return merge(merge_sort(L), merge_sort(R))

    arr = merge_sort(A)

    i, j = 0, len(A) - 1
    while i < len(A) and j >= 0:
        if arr[i] + arr[j] < x:
            i += 1
        elif arr[i] + arr[j] == x:
            return True
        elif arr[i] + arr[j] > x:
            j -= 1

    return False


print(sum_x([5, 4, 8, 3, 2], 12))
```

$$T(n) = nlogn + n \\ \therefore \Theta(nlogn)$$

---

Problems
# 2-1 Insertion sort on small arrays in merge sort
>Although merge sort runs in $$\Theta (n\log{n})$$ worst-case time and insertion sort runs in $$\Theta (n^2)$$ worst-case time, the constant factors in insertion sort can make it faster in practice for small problem sizes on many machines. Thus, it makes sense to *__coarsen__* the leaves of the recursion by using insertion sort within merge sort when subproblems become sufficiently small. Consider a modification to merge sort in which $$n/k$$ sublists of length $$k$$ are sorted using insertion sort and then merged using the standard merging mechanism, where $$k$$ is a value to be determined.<br><br>
  $$\boldsymbol a.$$ Show that insertion sort can sort the $$n / k$$ sublists, each of length $$k$$, in  $$\Theta(nk)$$ worst-case time.<br><br>
  $$\boldsymbol b.$$ Show how to merge the sublists in $$\Theta(n\log{(n/k)})$$ worst-case time.<br><br>
  $$\boldsymbol c.$$ Given that the modified algorithm runs in $$\Theta(nk + n\log\frac{n}{k})$$ worst-case time, what is the largest value of $$k$$ as a function of $$n$$ for which the modified algorithm has the same running time as standard merge sort, in terms of $$\Theta$$-notation?<br><br>
  $$\boldsymbol d.$$ How should we choose $$k$$ in practice?


a. We ask insertion sort to sort $$k$$ length of list. The worst-case time is $$\Theta(k^2)$$.<br>
But actually, $$k$$ length sublist is just a portion of the actual array $$n$$.<br>
Therefore, $$\frac{n}{k}$$ of $$ k^2$$ is $$\frac{n}{k} \times k^2 = nk$$
<br><br><br>
** This problem was very tricky for me **

b. Why $$n/k$$? Well think of a tree structure $$n$$ is always at the top. $$\log{n/k} + 1$$ means there are some levels that will not be accessed by our merge sort - meaning halving the list stops when it reaches $$\log{\frac{n}{k}} + 1$$ level (the same goes to merge sorting the whole $$n$$ when level < 2 it'll stop halving and continue merging instead). From that point merging operation takes place.

Example -
There are 8 elements in a list. Merge sort divides by 2 each time. $$\log_2{8} + 1 = 3 + 1 = 4$$ There are 4 levels in the tree. But what if the halving(dividing by 2) stops midway? For example - it doesn't go all the way down to the 4th level but just to the 3rd level.
$$\log{n/k} + 1 = \log{8/2} + 1= \log4 + 1 = 3$$.
Only the first 3 levels in the tree structure that our halving will go.

<pre>
          8
    /           \
 8/2=4          8/2=4
   /    \           / \
  8/4=2   2        2    8/4=2
</pre>

We also notice that in the tree structure above, $$2$$ is at the 3rd level. It's also the same as saying divides $$n$$ as many until it reaches $$k$$.
<br><br>

Yes that's what $$\log{n/k}$$ means. But, bear in mind this merge sort:
1. halves the elements for some $$\log{n/k}$$ level
2. sort the remaining elements if the number of elements is small enough for efficient insertion sort
3. merge those.

The second step is the last level of $$\log{n/k}+1$$. If we use the previous example, the are total of 3 levels and 1 level is left for the second step. Therefore, $$3-1=2$$. $$1$$ level for insertion sort and $$2$$ levels for halving and merging. Therefore $$\log n - log k = \log 8 - \log 2 = 3 - 1$$.


Thus, we have gotten the crucial information needed to understand the next step. Insertion sort is $$\Theta(n)$$

$$\therefore \Theta(n\log\frac{n}{k})$$
<br><br><br>

c. value of $$k$$ as a function of $$n$$ means $$k$$ value is exactly as $$n$$ value then we will get the standard merge sort time. $$T(n) = cn(\log{n} + 1)$$<br> $$\log{n} + 1$$ is number of levels. Thus, $$k = \log{n} + 1$$ or just $$k= \log{n}$$. Substitue terms we get:

$$
\begin{align}
\Theta(nk + n\log\frac{n}{k}) &= n\log{n} + n\log\frac{n}{\log{n}}\\
& = n\log{n} + n\log{n} - n\log(\log{n})\\
& u = \log{n} \\
& n = 2^u\\
& = n\log{n} + n\log{n} - n\log{n} \\
& = n\log{n}
\end{align}
$$
<br><br><br>

d. If $$k$$ is equals to $$n$$ and is a function of $$n$$ then the sorting time is $$\Theta(n\log{n})$$. In order to find efficiency, constants must be taken into consideration. $$Cnk + Cn\log\frac{n}{k} <= Cn\log{n}$$.


# 2-2 Correctness of bubblesort
>Bubblesort is a popular, but inefficient, sorting algorithm. It works by repeatedly swapping adjacent elements that are out of order.<br><br>
  $$\boldsymbol a.$$ Let A' denote the output of BUBBLESORT(A) To prove that BUBBLESORT is correct, we need to prove that it terminates and that <br>
  $$A'[1]<=A'[2]<=...<=A'[n]$$,<br>
  where $$n = A.length$$. In order to show that BUBBLESORT actually sorts, what else do we need to prove?<br><br>
  $$\boldsymbol b.$$ State precisely a loop invariant for the for loop in lines 2–4, and prove that this loop invariant holds. Your proof should use the structure of the loop invariant proof presented in this chapter.<br><br>
  $$\boldsymbol c.$$ Using the termination condition of the loop invariant proved in part (b), state a loop invariant for the for loop in lines 1–4 that will allow you to prove inequality (2.3). Your proof should use the structure of the loop invariant proof presented in this chapter.<br><br>
  $$\boldsymbol d.$$ What is the worst-case running time of bubblesort? How does it compare to the running time of insertion sort?


a. Permutation means arrangement. We say arrangement of $$A'$$ is $$A'$$ permutation

b.

c.

d. Worst case time of bubble sort is $$\Theta(n^2)$$ and best case is also the same. While insertion sort worst case is $$\Theta(n^2)$$ and best case is $$\Theta(n)$$


# 2-3 Correctness of Horner’s rule
>The following code fragment implements Horner’s rule for evaluating a polynomial<br><br>
$$
\begin{align}
P(x) &= \sum_{k=0}^n a_kx^k \\
&= a_0 + x(a_1 + x(a_2 + \cdots + x(a_{n-1} + xa_n) \cdots))
\end{align}
$$
<br><br>
given the coefficients $$a_0, a_1, \ldots ,a_n$$ and a value for x:
```python
y = 0
for i = n downto 0
    y = ai + x y
```


>$$\boldsymbol a.$$ In terms of $$\Theta$$-notation, what is the running time of this code fragment for Horner’s rule?<br><br>
$$\boldsymbol b.$$ Write pseudocode to implement the naive polynomial-evaluation algorithm that computes each term of the polynomial from scratch. What is the running time of this algorithm? How does it compare to Horner’s rule?<br><br>
$$\boldsymbol c.$$ Consider the following loop invariant:<br><br>
$$\boldsymbol d.$$ Conclude by arguing that the given code fragment correctly evaluates a polynomial characterized by the coefficients $$a_0, a_1, \ldots ,a_n$$.


a. $$\Theta(n)$$

b. Naive polynomial evaluation in python
```python
def naive_poly(A, x):
    sum_ = 0
    highest_power = len(A) - 1

    for i in range(len(A)):
        print(sum_)
        sum_ += A[i] * (x ** highest_power)
        highest_power -= 1

    return sum_

A = [2, -3, 5, -7]
print(naive_poly(A, 3))
```

Running time is $$\Theta(n)$$<br>
But I guess the book wants it in $$\Theta(n^2)$$. With nested for loop.

c.

d.


# 2-4 Inversions
>Let $$A[1..n]$$ be an array of $$n$$ distinct numbers. If $$i < j$$ and $$A[i] > A[j]$$, then the pair $$(i, j)$$ is called an __inversion__ of $$A$$.<br><br>
$$\boldsymbol a.$$ List the five inversions of the array $$\langle 2, 3, 8, 6, 1 \rangle$$.<br><br>
$$\boldsymbol b.$$ What array with elements from the set $$\lbrace 1, 2, \ldots, n \rbrace $$ has the most inversions? How many does it have?<br><br>
$$\boldsymbol c.$$ What is the relationship between the running time of insertion sort and the number of inversions in the input array? Justify your answer.<br><br>
$$\boldsymbol d.$$ Give an algorithm that determines the number of inversions in any permutation on $$n$$ elements in $$\Theta(n \lg n)$$ worst-case time. (Hint: Modify merge sort.)


a. $$(2,1), (3,1), (8,6), (8,1), (6,1)$$


b. Inverse of set $$\lbrace 1, 2, \ldots, n \rbrace $$. Which is $$\lbrace n, n-1, n-2, \ldots, 1 \rbrace$$<br>
When array is inverse, inversion starts from position 0 until the end (with the end has no inversion because it has no pairs). Thus, it's the same as saying $$\frac{(n-1)(n-1+1)}{2} = \frac{n^2-n}{2}$$


c. Insertion sort compares current element with elements before it one by one (start from element at position 1). While inversion checks current element with elements after it one by one with the last element has no pair, has no inversion. Mechanism of Insertion sort and inversion are an inverse of each other. Insertion sort and inversion has the same running time.


d.
