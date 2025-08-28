# 9 - Fibonacci Sequence

Recursion (Two Branch)
A more common case of recursion is multi-branch recursion. In this lesson we will attempt to solve the Fibonacci sequence problem using two-branch recursion.

The Fibonacci sequence is a set of numbers that starts with 0 and 1, and each subsequent number is the sum of the two preceding numbers. The sequence starts like this: 0,1,1,2,3,5,8,13,21,34,....

Generally, the formula to calculate the nth fibonacci number is to sum the two previous fibonacci numbers, i.e. the (n−1)th and (n−2)th fibonacci numbers.

More formally, we say that:
F(0)=0 and F(1)=1 
F(n)=F(n−1)+F(n−2)
Part 1 is the base case, and part 2 is the recursive case. The Fibonacci sequence is a classic example of a recursive function:

The below formula is the recursive formula for the Fibonacci sequence, also known as the recurrence relation:
**fib(n)=fib(n−1)+fib(n−2)**

We can visualize the mathematical formula with the following tree.

<img width="1084" height="558" alt="Screenshot 2025-08-28 at 3 57 52 PM" src="https://github.com/user-attachments/assets/9ee9e18b-f5c3-4529-bf40-b8199f9243ca" />

```java
// Base case: n = 0 or 1
public static int fibonacci(int n) {
    if (n <= 1) {
        return n;
    }
    // Recursive case: fib(n) = fib(n - 1) + fib(n - 2)
    return fibonacci(n-1) + fibonacci(n-2);
}
```

The above pseudocode is similar to our previous example with factorial, except this is a branch factor of two. Notice how we are calling the function twice in the last line, this results in the tree that is shown in the visual.

We have our base case, we know the function calls itself in the last return statement, and we know that at some point when the base case is reached, we will have to travel back "up" to calculate the ultimate answer.

To calculate fibonacci(5), we get fibonacci(4) + fibonacci(3).
Now, both of these will execute within their own function calls. Looking at
fibonacci(4) will call fibonacci(3) + fibonacci(2) and so on, until n hits 1 or 0
After that it will return the result, and keep going back up all the way until fibonacci(4) which will give us an answer of 3.
Now, we have the answer to fibonacci(4) and do the same for fibonacci(3) which results in 2.
Add the two together, and the 5th fibonacci number is 5.

Time and Space Complexity

Evaulating the time complexity for this is a little bit more tricky. Let's analyze the tree, and the number of nodes on each one of the levels. On the 1st level (0 indexed), there is 1, on the 2nd level, there are 2, then 4, after which we can see a pattern. Each level has the potential to hold 2x the nodes of the previous level.

Therefore, a reasonable upperbound for the total number of nodes in the tree is 1+2+4+8+...+2^n. This is a geometric series, similar to what we saw in the dynamic array chapter. We know the last term is the dominating term, and the sum of the series is roughly 2^(n+1) -1

This means that the total number of nodes in the tree is O(2^n). Each node itself is a function call and simply calculates the sum of two values, thus the time complexity of the function is O(2^n)

<img width="1080" height="487" alt="Screenshot 2025-08-28 at 4 01 48 PM" src="https://github.com/user-attachments/assets/6f4c8942-be21-44d4-9228-189825dcc4d6" />

