# CMPS 2200 Recitation 07
## Answers

**Name:**Zack Mitra


Place all written answers from `recitation-07.md` here for easier grading.



- **2) (2 pts)** Write a recurrence for the **work** of this algorithm and solve it. Assume the input is $n$ to compute $F_n$.

W(n) = W(n-1) + W(n-2)+ O(1)
Base cases W(0) = W(1) = O(1)

W(n) ~ O(2^n)

- **3) (2 pts)** Write a recurrence for the **span** of this algorithm and solve it.

Assuming the recursive calls can execute in parallel, the span recurrence is:

S(n) = \max(S(n-1), S(n-2)) + O(1)

Since the longest recursive branch is S(n-1), we simplify to:

S(n) = S(n-1) + O(1)

With base cases S(0) = S(1) = Theta(1), this recurrence decreases by 1 at each level, giving:

S(n) = Theta(n)

Therefore, the span is linear because only the longest chain of recursive calls determines the parallel execution time.



- **4) (1 pt)** Inspecting the `counts` list, what interesting pattern emerges?

The counts follow the Fibonacci sequence in reverse order, except for the count at index 0. For n = 10, the counts are [34, 55, 34, 21, 13, 8, 5, 3, 2, 1, 1].

This happens because each recursive call generates two smaller recursive calls, causing the same Fibonacci numbers to be calculated repeatedly. The pattern demonstrates how much duplicate work the recursive algorithm performs.


- **6) (2 pts)** When computing $F_n$, what is the maximum number of times that `fib_top_down(i)` will be called for any value $i$? Based on this, what is the **work** and **span** of this algorithm?

The maximum number of times fib_top_down(i) is called for any particular value of i is 2. However, each Fibonacci number is only calculated once because previously computed values are stored in the fibs list.

Since there are n+1 Fibonacci values to calculate and each requires constant work, the work recurrence is:

W(n) = W(n-1) + O(1)

Therefore, W(n) = Theta(n)

The span recurrence is:

S(n) = S(n-1) + O(1)

Therefore, S(n) = Theta(n)


- **8) (2 pts)** When computing $F_n$, what is the maximum number of times that
  $F_i$ will be read from the list for any value $i$? Based on this, what is the **work** and **span** of `fib_bottom_up`?


The bottom-up Fibonacci algorithm has W(n) = Theta(n) because initializing the array and iterating through the Fibonacci numbers each require linear work. Each iteration performs a constant-time addition.

The span is S(n) = Theta(n) because each Fibonacci number depends on the previous two values, so the loop iterations must execute sequentially.

Therefore, both the work and span are Theta(n).