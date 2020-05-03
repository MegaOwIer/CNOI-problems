Time limit per test : $\texttt{1 s}$

Memory limit per test : $\texttt{512 MB}$

You can submit this problem at:

+ [LibreOJ](https://loj.ac/problem/3158)
    + Input : `sequence.in`
    + Output : `sequence.out`
+ [Luogu](https://www.luogu.org/problem/P5470)
+ [UOJ](https://uoj.ac/problem/480)

## Description

You are given two sequences $\{a_i\}$ and $\{b_i\}$ of length $n$, and the element of them are indexed from $1$ to $n$. You need to choose $K$ numbers in each sequence, and ensure that at least $L$ positions are chosen in both sequences. Your task is to maximize the sum of the $2K$ numbers.

Formally speaking, you need to assign $2$ sequences $\{c_i\}$ and $\{d_i\}$ of length $K$ such that 

+ $1 \leq c_1 < c_2 < \cdots < c_K \leq n$
+ $1 \leq d_1 < d_2 < \cdots < d_K \leq n$
+ $\left\lvert\{c_1, c_2, \cdots, c_K\} \cap \{d_1, d_2, \cdots, d_K\}\right\rvert \geq L$

Your goal is to maximize
$$
\sum_{i=1}^{K}{a_{c_i}} + \sum_{i=1}^{K}{b_{d_i}}
$$

## Input

The first line contains a single integer $T$ — the number of test cases.

Each test case contains $3$ lines.

The first line contains $3$ integers $n, K, L$.

The second line contains $n$ integers $a_1, a_2, \cdots, a_n$.

The third line contains $n$ integers $b_1, b_2, \cdots, b_n$.

## Output

For each test case, print a single integer — the maximal sum.

## Samples

### Sample 1
#### Input
```plain
5
1 1 1
7
7
3 2 1
4 1 2
1 4 2
5 2 1
4 5 5 8 4 
2 1 7 2 7 
6 4 1
1 5 8 3 2 4 
2 6 9 3 1 7 
7 5 4
1 6 6 6 5 9 1 
9 5 3 9 1 4 2 

```
#### Output
```plain
14
12
27
45
62

```
#### Explanation

For the first case, $\{c_i\} = \{d_i\} = \{1\}$.

For the second case, $\{c_i\} = \{1, 3\}$, $\{d_i\} = \{2, 3\}$.

For the third case, $\{c_i\} = \{3, 4\}$, $\{d_i\} = \{3, 5\}$.

For the fourth case, $\{c_i\} = \{d_i\} = \{2, 3, 4, 6\}$.

For the fifth case, $\{c_i\} = \{2, 3, 4, 5, 6\}$, $\{d_i\} = \{1, 2, 3, 4, 6\}$.

## Constraints

For all of the tests, $T \leq 10$, $1 \leq \sum{n} \leq 10^6$, $1 \leq L \leq K \leq n \leq 2 \times 10^5$, $1 \leq a_i, b_i \leq 10^9$.

For partial scores, you can look up at the origin statement (`NOI/2019/Day1.pdf`).
