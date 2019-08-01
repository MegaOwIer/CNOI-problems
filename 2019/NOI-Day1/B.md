## B. robot

Time limit per test : 3 s

Memory limit per test : 512 MB

You can submit this problem at:

+ [LibreOJ](https://loj.ac/problem/3157)
  + Input : `robot.in`
  + Output : `robot.out`
+ [Luogu](https://www.luogu.org/problem/P5469)

### Description

Recently, Bob invented $2$ kinds of robots: type P and type Q. Now he wants to test the mobility of these two robots.

There are $n$ pillars arranged in a row, numbered from $1$ to $n$. The $i$-th pillar has a height of $h_i$. The robots can only move between adjacent pillars, that is, if the robot is currently on the $i$-th pillar. it can only move to the $(i-1)$-th or $(i+1)$-th pillar.

In each test, Bob will choose a number $s\,(1 \leq s \leq n)$, and put the robots on the $s$-th pillar. Then the robots will move according to their own rules.

Robots of type P will always move to the **left**, but it **can't** move to the pillars that are **higher than** pillar $s$. Formally, it will stop at pllar $l\,(l \leq s)$ if and only if:

+ $l = 1$ or $h_{l-1} > h_s$
+ $h_j \leq h_s$ holds for all $l \leq j \leq s$

Robots of type Q will always move to the **right**, but it **can** only move to the pillars that are **shorter than** pillar $s$. Formally, it will stop at pllar $r\,(r \leq s)$ if and only if:

+ $r = n$ or $h_{r+1} \geq h_s$
+ $h_j < h_s$ holds for all $s < j \leq r$

Bob can set the height of all the pillars, the height of the $i$-th pillar can be any integer in range $[A_i, B_i]$. He wants to know how many possible ways are there to set the heights so that no matter which number $s$ is, the difference between the number of pillars that the robots pass by is **not greater than** $2$.

Since the answer could be very large, you should print the answer module $10^9 + 7$ instead.

### Input

The first line contains a single integer $n$.

Each of the next $n$ lines contains twp integers $A_i, B_i$.

### Output

Print a single integer — the answer module $10^9 + 7$.

### Samples

#### Sample 1
##### Input
```plain
5
3 3
2 2
3 4
2 2
3 3

```
**Note : In Chinese statement, the sample input isn't printed correctly.**

##### Output
```plain
1

```
##### Explanation

There are two possible ways to set the heights:

+ If the heights are $3\,2\,3\,2\,3$ respectively. When $s = 5$, we can see that Robot of type P will stop at pillar $1$ (pass by $4$ pillars in total) and robot of type Q will stop at pillar $5$ (pass by $0$ pillars in total), which breaks the condition.
+ If the heights are $3\,2\,4\,2\,3$ respectively. We can show that no matter which number $s$ is, the condition is always satisfied.


More samples can be found in the folder `robot/`.

### Constraints

For all of the tests, $1 \leq n \leq 300$, $1 \leq A_i \leq B_i \leq 10^9$.

For partial scores, you can look up at the origin statement (`2019-NOI-Day1.pdf`).
