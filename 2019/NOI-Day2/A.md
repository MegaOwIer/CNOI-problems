## A. jump

Time limit per test : 2 s

Memory limit per test : 128 MB

You can submit this problem at:

+ [LibreOJ](https://loj.ac/problem/3159)
  + Input : `jump.in`
  + Output : `jump.out`
+ [Luogu](https://www.luogu.org/problem/P5471)

### Description

There are $n$ cities in the Kingdom of Flea, numbered from $1$ to $n$, and city $1$ is the capital. All of the cities are located in a grid graph of size $w \times h$. Each city has an integer coordinate $(x, y)\,(1 \leq x \leq w, 1 \leq y \leq h)$, and the coordinates of the cities are different from each other.

There are $m$ bouncing devices in the Kingdom of Flea, numbered from $1$ to $m$. The $i$-th device is located in city $p_i$ and with this device, a flea in city $p_i$ can jump to any city that satisfies $L_i \leq x \leq R_i$, $D_i \leq y \leq U_i$ in $t_i$ time units.

Since that the cities are quite far away from each other, so fleas always travel by the bouncing devices. Specifically, during a trip a flea will pass through several cities in turn, whose indices are $a_0, a_1, \cdots, a_k$, respectively; in this trip, the indices of bouncing devices used in turn are $b_1, b_2, \cdots, b_k$. Each cities can appear any number of times in the sequence $\{a_j\}$, and each bouncing devices can appear any number of times in the sequence $\{b_j\}$ and for each $j\, (1 \leq j \leq k)$, bouncing devices $b_j$ is located in the city $a_{j−1}$ and the flea can jump to city $a_j$ with the help of the bouncer. We call this a trip from city $a_0$ to city $a_k$, which costs $\sum_{i=1}^{k}{t_{b_i}}$ time units.

Now the Flea King wants to know that for every city except the capital of the kingdom (city $1$), how much time it will at least take to get to the city from the capital.

### Input

The first line contains $4$ integers $n, m, w, h$.

Each of the next $n$ lines contains $2$ integers $x_i, y_i$.

Each of the next $m$ lines contains $6$ integers $p_i, t_i, L_i, R_i, D_i, U_i$, describing the information of the $i$-th bouncing device.

It's guaranteed that every city is reachable from the capital.


### Output

You should print $n - 1$ lines, the $i$-th line contains the minimum time it needs to get to city $i + 1$ from the capital.

### Samples

#### Sample 1
##### Input
```plain
5 3 5 5
1 1
3 1
4 1
2 2
3 3
1 123 1 5 1 5
1 50 1 5 1 1
3 10 2 2 2 2

```
##### Output
```plain
50
50
60
123

```

More samples can be found in the folder `jump/`.

### Constraints

+ $1 \leq n \leq 70000$
+ $1 \leq m \leq 150000$
+ $1 \leq w, h \leq n$
+ $1 \leq t_i \leq 10000$

For partial scores, you can look up at the origin statement (`2019-NOI-Day2.pdf`).

**Please note that the memory limit of this problem is 128 MB.**