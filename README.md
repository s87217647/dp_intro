# dp_intro

The algorithm leverages dynamic programming techniques. Both time complexity and memory complexity are O(m*n). Solving this problem by brute force results in  O((m+n)^2) time complexity. Basic idea for dynamic programming -break down a complex problem into simpler, smaller subproblems in a recursive manner. 

![order.png](https://github.com/s87217647/dp_intro/blob/main/images/call_stack.png)

**Fibonacci Sequence**

Problem definition:  Starting with fib(0) = 0, fib(1) = 1, fib(n) = fib(n - 1) + fib(n - 2)

**Brute force**

```python
def fib(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fib(n - 1) + fib(n - 2)
```

Base cases are straightforward. Otherwise, fib recursively calls itself. A fib(6) call produces a call stack tree like the image below. Values are recursively calculated multiple times. The time complexity for such a recursive algorithm is O(n^2). 

![call_stack.png](https://github.com/s87217647/dp_intro/blob/main/images/call_stack.png)

**Dynamic Programming**

If an appropriate data structure, an array in this case, is applied to the algorithm to record calculated results, repetitive calculations can be avoided.

```python
def fib(n):
    if n == 0:
        return 0
    if n == 1:
        return 1

    dp = [0] * (n + 1)
    dp[0] = 0
    dp[1] = 1
    for i in range(2, len(dp)):
        dp[i] = dp[i - 1] + dp[i - 2]
        print(dp)
    return dp[-1]
```

An array, dp, is created to keep track of previous results. When looping the array from left to right. When solving the current problem, previous subproblems, which are problems on the left, have already been solved. Solving the current problem takes constant time. The loop takes O(n) time, and the array takes O(n) memory. Compared to the previous solution, the time complexity dropped significantly.

**Steps Analysis**

Always start with simplistic backtracking, then identify the subproblem and simplify

Define the overlapping problem

F(i) = ith Fib

Write recursion

F(i) = F(i - 1) + F(i - 2) 

Choose a data structure

In this case, the subproblems are linear, and an array will suffice. Suitable data structure varies depending on the specific problem. Needleman-Wunsch requires a table. It could be a tree or a graph.

DP processes the dependency graph in reverse topological order, postorder traversal. Data structures used to record results depend on the problems. They can be arrays, tables, trees, or graphs. In addition, the new dynamic algorithm’s time complexity does not always equal the time to loop through the memoized data structure. Each subproblem may take more than constant time to finish.

**References**

Introduction to Algorithms - TH Cormen
