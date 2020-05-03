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

### Implementation details

You should implement the following function:

```c++
void explore(int N, int M);
```

+ $\texttt{N}$ : the number of caves.
+ $\texttt{M}$ : the number of roads.
+ This function is called exactly once for each test case.

Your program can call the following function:

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

The sample grader reads the input in the following format:

The first line contains $3$ integers $L_m, L_q, L_c$.

The second line contains $2$ integers $N, M$.

Each of the next $M$ lines contains $2$ integers $x, y$, refers to an road between cave $x$ and cave $y$.

If your program is judged as **Accepted**, the sample grader prints `Correct` and the number of times you call each function. Otherwise it will print what's wrong with your solution.

## Sample

You can find an example of communication in the Chinese statement (`NOI/2019/Day2.pdf`).


## Constraints

+ $3 \leq N \leq 200000$
+ $2 \leq M \leq 300000$

The constraints of each test can be found in the origin statement (`NOI/2019/Day2.pdf`).

Note: the lowest digit of $N$ may help you get partial scores easilier.
