# 8 - Factorial

**Recursion (One Branch)**

Recursion can be a difficult concept to wrap your head around so don't be discouraged if you don't understand it right away.

Simply put, recursion is when a function calls itself, usually with a different input. This is known as a recursive function.

Recursive functions can be thought of as functions that breaks down a problem into smaller sub-problems and solves them in reverse order. It's usually possible to convert a recursive function into an iterative one, and vice versa.

> For some problems an iterative solution can be much more simple to implement than a recursive one, and vice versa.

Recursive functions have two parts:

- The base case.
- The recursive case.
The concept of recursion applies to the real world as well. Consider a box that contains another box, which contains another box, and so on. This is a recursive structure.

In this case, the base case would be the smallest box, and the recursive case would be the larger boxes that contain the smaller boxes.

There are two types of recursion, one-branch and multi-branch. Let's discuss one-branch recursion first.

If we want to compute n! (n-factorial), we can use recursion. The formula for n! is n∗(n−1)∗(n−2)∗...∗1.

For example, 5!=5∗4∗3∗2∗1=120.

- Notice that 5! can be broken down into 5∗4! -
- 4! can be broken down into 4∗3!, and so on. This is the recursive case.
- The base case is when n=0 or n=1. The result of 0! and 1! is 1.

<img width="209" height="977" alt="Screenshot 2025-08-24 at 8 57 01 PM" src="https://github.com/user-attachments/assets/a9b04769-ea3c-4e48-aeae-964fe55a9b49" />

``` java
public static int factorial(int n) {
    // Base case: n = 0 or 1
    if (n <= 1) {
        return 1;
    }
    // Recursive case: n! = n * (n - 1)!
    return n * factorial(n-1);
}
```

Let's analyze this. We have our two parts: the base case and the recursive case (the function calling itself).

When the code reaches the last line with the initial input of 5, we get: 5 * factorial(4), which starts executing the function again from line 1, only now with input 4, so we get 4 * factorial(3) and then 3 * factorial(2) and lastly 2 * factorial(1) after which the base case is reached.

But what happens when the base case is reached? When the function is called with 1 as the input, 1 is returned, and now it can be multiplied by 2, which will result in 2, which is the answer to 2!. We have only solved the first sub-problem so far. Now, we compute 3 * factorial(2), which results in 6, then 4 * factorial(3), which is 24, and finally 5 * factorial(4), which is 120 - the final answer to 5!

The most important part is that when we trigger the base case, we move back "up" the recursion tree because now we have to "piece" together the answers to our sub-problems to get to the final solution.

> The complicated part about this is you have to think about the problem in reverse order.

This process is visualized below.
<img width="1084" height="620" alt="Screenshot 2025-08-24 at 8 59 23 PM" src="https://github.com/user-attachments/assets/c301499e-d139-4db4-90b9-78713b49be5a" />

> As observed, we took the original problem, factorial(5) and broke it down into smaller sub-problems, and by combining the answer to those sub-problems, we were able to solve the original problem. It is important to note that if there is no base case in recursion, the recursive case would execute forever resulting in a stack overflow error.

**Time and Space Complexity**
Time: O(n)

In total, n calls are being made to the factorial function, where each function call is O(1), making the total time complexity O(n).
Space: O(n)

While we aren't using any data structures, recursion operates off of an implicit stack, known as the function call stack. That is how we are able to return from one function call to the previous one. Since there are n recursive calls, there will be n function calls placed on the stack, which results in O(n) space.

**Iteration and Recursion**
Most recursive algorithms can be written iteratively. The iterative implementation of this is the following:

``` java
int n = 5;
int res = 1;
while (n > 1) {
    res = res * n;
    n--;
}
```

In the iterative case, we store our answer in a variable named res and decrement n until n becomes 1.

The iterative implementation is much simpler than the recursive one in this case, but that's not always the case. Recursion will be especially useful when we start learning about trees.

This solution is also more space efficient since it doesn't require the function call stack.
