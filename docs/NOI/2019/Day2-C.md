Time limit per test : $\texttt{2 s}$

Memory limit per test : $\texttt{512 MB}$

You can submit this problem at:

+ [LibreOJ](https://loj.ac/problem/3161)
    + Only `C++` is available.
+ [UOJ](https://uoj.ac/problem/483)
    + Both `C/C++` and `Pascal` are available.

**This is an interactive problem.**

## Description

The underground palace consists of $N$ caves and $M$ roads between them, which can be represented as an undirected simple graph of $N$ vertices and $M$ edges. The caves are numbered from $0$ to $n - 1$, and you **have no idea** where the roads are.

There is a light in each cave, all of them are either off or on. Initially, all the lights are off, and the status of the lights can be changed only by the mysterious machine in your hand. Specifically, it can perform the following $4$ operations:

1. For a certain $x$, it will change the status of the lights in cave $x$ and the caves that directly connected to cave $x$. That is, turn on the light if it's off, and turn off the light if it's on.
2. For a certain $x$, it will show you the current status of the lights in cave $x$.
3. For certain $x, y$, it will record an edge between cave $x$ and cave $y$.
4. For a certain $x$, it will tell whether all the roads connected to cave $x$ are recorded.

The machine can only deal with one operation at the same time, and the number of uses for each operation is limited, $L_m, L_q, M, L_c$ respectively.

Your task is to write a program to find all the $M$ edges correctly.

## Implementation details

You should implement the following function:

```c++
void explore(int N, int M);
```

+ $\texttt{N}$ : the number of caves.
+ $\texttt{M}$ : the number of roads.
+ This function is called exactly once for each test case.

Your program can call the following functions:

```c++
void modify(int x);
```

+ $\texttt{x}$ : The index of the cave you want to operate on.
+ You should guarantee that $0 \leq x < N$.
+ You cannot call this function more than $L_m$ times for each test case.
+ This function will perform the first operation on cave $x$ and return nothing.

```c++
int query(int x);
```

+ $\texttt{x}$ : The index of the cave you want to operate on.
+ You should guarantee that $0 \leq x < N$.
+ You cannot call this function more than $L_q$ times for each test case.
+ This function will perform the second operation on cave $x$.
+ This function will return `1` if the light in cave $x$ in on, and `0` otherwise.

```c++
void report(int x, int y);
```

+ $\texttt{x}, \texttt{y}$ : The indeies of the caves you want to operate on.
+ You should guarantee that $0 \leq x, y < N$ and $x \neq y$.
+ You cannot call this function more than $M$ times for each test case.
+ This function will record an edge between cave $x$ and cave $y$, and return nothing.

```c++
int check(int x);
```

+ $\texttt{x}$ : The index of the cave you want to operate on.
+ You should guarantee that $0 \leq x < N$.
+ You cannot call this function more than $L_c$ times for each test case.
+ This function will perform the fourth operation on cave $x$.
+ This function will return `1` if all the roads connected to cave $x$ are recorded, and `0` otherwise.

In this problem, the grader is **NOT** adaptive. This means that the graph is fixed at the beginning of the running of the grader and it does not depend on the operations performed by your solution.

It is guaranteed that grader will use no more than $\texttt{1 s}$ of time and no more than $\texttt{128 MB}$ of memory.

## Sample grader

You are given a sample grader (`grader.c/cpp` for `C/C++` and `graderhelperlib.pas` for `Pascal`) together with the sample tests. In order to test the samples, you need to compile the grader and your code into a single executable file.

The executable file will get input in the following format:

The first line contains $3$ integers $L_m, L_q, L_c$.

The second line contains $2$ integers $N, M$.

Each of the next $M$ lines contains $2$ integers $x, y$, refers to a road between cave $x$ and cave $y$.

If your program is judged as **Accepted**, the sample grader prints `Correct` and the number of times you call each function. Otherwise, it will print what's wrong with your solution.

## Sample

Assume that the input is as follows:

```plain
100 200 300
3 2
0 1
1 2

```

The first line shows that you can call `modify(x)` for no more than $100$ times, `query(x)` for no more than $200$ times, and `check(x)` for no more than $300$ times, respectively.

The second line shows that $N = 3$ and $M = 2$.

A possible way of interaction is listed below:

|Your Program|Grader|Comment|
|:-:|:-:|:-:|
| | call `explore(3, 2)` | Test Begins. |
| call `modify(0)` |  | Perform operate `1` on cave $0$. |
| call `query(2)` | return $0$. | The light in cave $2$ is off currently. |
| call `report(0, 1)` |  | Find a road $(0, 1)$ and record it. |
| call `check(0)` | return $1$. | All the roads connected to cave $0$ have been recorded. |
| call `report(2, 1)` |  | Find a road $(2, 1)$ and record it. |
| return | Print `Correct`. | You solve the problem correctly. |


## Constraints

+ $3 \leq N \leq 200000$
+ $2 \leq M \leq 300000$

More constraints are attached to each test, which can be found in the origin statement (`NOI/2019/Day2.pdf`).

Note: the lowest digit of $N$ may help you get partial scores easilier.
