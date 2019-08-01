## A. route

Time limit per test : 1 s

Memory limit per test : 512 MB

You can submit this problem at:

+ [LibreOJ](https://loj.ac/problem/3156)
  + Input : `route.in`
  + Output : `route.out`
+ [Luogu](https://www.luogu.org/problem/P5468)
  + Memory limit is changed to 128 MB here

### Description

There are $n$ railway stations in the Kingdom of Cat, numbered from $1$ to $n$. Little cat is going home (at station $n$) from station $1$. There are $m$ trains in the kingdom, numbered from $1$ to $m$. For the $i$-th train, it will depart station $x_i$ at time $p_i$, and arrive at station station $y_i$ directly at time $q_i$. At time $0$, little cat is at station $1$.

Little cat can go home by multiple transfers. One transfer is that for a pair of trains $u$ and $v$, if $y_u = x_v$ and $q_u \leq p_v$, then after taking train $u$, little cat can wait at station $y_u$ for $p_v - q_u$ time units, and take train $v$ at time $p_v$.

Little cat wants to minimize its *anxiety*, which is calculated as followed:

+ If little cat waits at some stations for $t\,(t \geq 0)$ time units, its anxiety will be increased by $At^2 + Bt + C$, where $A, B, C$ are given constants.
  + Note that before little cat taking the first train at time $t$, it has been waiting for $t$ time units at station $1$.
+ If little cat arrives at station $n$ at time $z$, its anxiety will be increased by $z$.

Formally, if little cat takes $k$ trains totally, whose numbers are $s_1, s_2, \cdots, s_k$, little cat can get home if and only if:

+ $x_{s_1} = 1, y_{s_k} = n$
+ $y_{s_j} = x_{s_{j + 1}}$ and $q_{s_j} \leq p_{s_{j + 1}}$ hold for $1 \leq j < k$

and its anxiety will be
$$
q_{s_k} + (A \cdot p_{s_1}^2 + B \cdot p_{s_1} + C) + 
\sum_{j = 1}^{k - 1}\left(A(p_{s_{j + 1}} - q_{s_j})^2 + B(p_{s_{j + 1}} - q_{s_j}) + C\right)
$$

Your task is to figure out the minimal anxiety.

### Input

The first line contains $5$ integers $n, m, A, B, C$.

Each of the next $m$ lines contains $4$ integers $p_i, q_i, x_i, y_i$.

### Output

Print a single integer — the minimal anxiety.

### Samples

#### Sample 1
##### Input
```plain
3 4 1 5 10
1 2 3 4
1 2 5 7
1 2 6 8
2 3 9 10

```
##### Output
```plain
94

```
##### Explanation
There are $3$ ways to go home.

1. Take train $1, 4$ in turn, and the anxiety is
   $$10 + 1 \times 3^2 + 5 \times 3 + 10 + 1 \times (9-4)^2 + 5 \times (9-4) + 10 = 104$$
2. Take train $2, 4$ in turn, and the anxiety is
   $$10 + 1 \times 5^2 + 5 \times 5 + 10 + 1 \times (9-7)^2 + 5 \times (9-7) + 10 = 94$$
3. Take train $3, 4$ in turn, and the anxiety is
   $$10 + 1 \times 6^2 + 5 \times 6 + 10 + 1 \times (9-8)^2 + 5 \times (9-8) + 10 = 102$$

So the minimal anxiety is $94$.

#### Sample 2
##### Input
```plain
4 3 1 2 3
1 2 2 3
2 3 5 7
3 4 7 9

```
##### Output
```plain
34

```

More samples can be found in the folder `route/`.

### Constraints

For all of the tests, $2 \leq n \leq 10^5$, $1 \leq m \leq 2 \times 10^5$, $0 \leq A \leq 10$, $0 \leq B, C \leq 10^6$, $1 \leq x_i, y_i \leq n$, $x_i \neq y_i$, $0 \leq p_i < q_i \leq 10^3$.

For partial scores, you can look up at the origin statement (`2019-NOI-Day1.pdf`).
