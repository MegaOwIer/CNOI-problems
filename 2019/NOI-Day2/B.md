## B. landlords

Time limit per test : 4 s

Memory limit per test : 512 MB

You can submit this problem at:

+ [LibreOJ](https://loj.ac/problem/3160)
  + Input : `landlords.in`
  + Output : `landlords.out`
+ [Luogu](https://www.luogu.org/problem/P5472)

### Description

Alice and Bob are playing card games, but Alice found that she can never win Bob, so she plans to cheat in the shuffling session.

There are $n$ cards in total, numbered from $1$ to $n$ from top to bottom. The card with index $i$ has a score of $f(i)$. In this problem, $f(i) = i$ or $f(i) = i^2$ always holds.

The whole shuffling session can be devided into $m$ rounds. During the $i$-th round:

+ Alice will take $A_i$ cards from the top, then all the cards are divided into 2 piles: the first contains $A_i$ cards from the top, the second contains the remaining $n - A_i$ cards.
  + In particular, when $A_i = 0$ or $A_i = n$, one of the piles will be empty.
+ Then Alice will merge the two piles in the following way. When there are $X$ cards left in the first pile and $Y$ in the second, she will take the card at the bottom of the first pile with the probability of $\frac{X}{X + Y}$, and put it on the top of the new pile; otherwise she will take the card at the bottom of the second pile and put it on the top of the new pile.

Since the shuffling session is random, Alice can't know which card it is at a certain position. But Alice wants to know the expected score of the card at a certain position after $m$ rounds of shuffling.

### Input

The first line contains $3$ integers $n, m, \text{type}$. When $\text{type} = 1$, $f(i) = i$, otherwise $f(i) = i^2$.

The second line contains $m$ integers $A_1, A_2, \cdots, A_m$.

The third line contains a single integer $Q$ — the number of queries.

Each of the next $Q$ lines contains a single integer $c_i$.

### Output

You should print $Q$ lines, the $i$-th line contains the expected score of the $c_i$-th card from top to bottom.

You should print the answer module $998244353$, that is, if the answer is $\frac{a}{b}$, where $(a, b) = 1$, you should print an integer $x$ such that $bx \equiv a \pmod{998244353}$ and $0 \leq x < 998244353$. One can prove that such $x$ is unique.

### Samples

#### Sample 1
##### Input
```plain
4 1 1
3
1
1

```
##### Output
```plain
249561090

```
##### Explanation

After shuffling, the cards will become:

+ $\{1, 2, 3, 4\}$ from top to bottom with the probability of $\frac{1}{4}$
+ $\{1, 2, 4, 3\}$ from top to bottom with the probability of $\frac{1}{4}$
+ $\{1, 4, 2, 3\}$ from top to bottom with the probability of $\frac{1}{4}$
+ $\{4, 1, 2, 3\}$ from top to bottom with the probability of $\frac{1}{4}$

So the expected score of the first place is $\frac{1}{4}(1 + 1 + 1 + 4) = \frac{7}{4}$.

If you still have no idea how the it shuffles, some pictures in the Chinese statement (`2019-NOI-Day2.pdf`) will show you how to get $\{1, 4, 2, 3\}$.

More samples can be found in the folder `landlords/`.

### Constraints

+ $3 \leq n \leq 10^7$
+ $1 \leq m, Q \leq 5 \times 10^5$
+ $0 \leq A_i \leq n$
+ $\text{type} \in \{1, 2\}$

For partial scores, you can look up at the origin statement (`2019-NOI-Day2.pdf`).
