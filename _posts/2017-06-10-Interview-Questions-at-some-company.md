---
layout:     post
title:      Multiple of four
date:       2017-06-10GMT+8 09:47:00
categories: [algorithms]
---
**Note: It seems this particular page is indexed and ranked 1 in google with keyword hackerrank some-company. It's unethical to search for solutions before you actually take the test. My blog is mainly about algorithms and it wasn't my intention to help you scored 100% correct in hackerrank. It was purely my interest in algorithm that got me writing about it.** 

*Damaged is done therefore I'm just gonna leave this post as it is with some keywords removed. I hope they can come out with other questions.*


There were 2 questions. 

1. Given a txt file find the number of occurences of a website url. Easy peasy.

2. $$x*y=\text{multiple of 4}$$. $$x$$ is given from STDIN and the answer is to find $$y$$ and do $$z = 2(a) + b$$. Where $$a$$ is the number of occurences of 4 and $$b$$ is $$0$$. Multiple of 4 must be in the format $$4440000$$ or $$40$$ or $$440$$. $$404$$ is wrong though. So you see 4 must come consecutively. But be sure to get it ***very*** fast.

**STDIN**<br>
The first input 3 means 3 numbers to check.<br>
The line follows are the number to check.<br>

3<br>
4<br>
5<br>
80<br>

**STDOUT**<br>
2<br>
3<br>
4<br>


**STDIN**<br>
5<br>
62<br>
67<br>
20<br>
63<br>
81<br>

**STDOUT**<br>
30<br>
66<br>
3<br>
36<br>
162<br>


Here's the most optimal solution.
The reason that makes it faster than looping through 0 until infinity while checking if it's a multiple of 4 by calculation is that the code predetermined the value of four - 4, 40, 400, 440, 444, 4000, 4400, 4440, 4444 etc and just checking the modulus of it from there. 


```python
def checking(num):
    counter = 1
    while True:
        four = list("".join(str(e) for e in ['0' for x in range(counter)]))

        for x in range(1, counter + 1):
            print(x, counter)
            if x == 1:
                four[x - 1] = '4'
            else:
                four[: x] = ['4' for _ in range(x)]

            four_int = int("".join(four))

            if four_int % num == 0:
                count_0 = four.count('0')
                count_4 = four.count('4')

                return count_4, count_0

        counter += 1


N = int(input())

for x in range(N):
    num = int(input())
    a, b = checking(num)
    if a is None or b is None:
        print('Invalid')
    else:
        z = (2*a) + b
        print(z)
```

