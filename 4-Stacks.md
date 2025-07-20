# 4 - Stacks

A stack is a data structure that supports a subset of operations from a dynamic array. With a stack you may only add and delete elements from one end of the array (referred to as the top of the stack).

In the physical world, a stack can be conceptualized by thinking of a stack of plates. You may grab a plate from the top or you may add a plate to the top. You cannot remove or add a plate to the middle of the stack. This is the same as the stack data structure.

Stacks are a dynamic data structure that operate on a LIFO (Last In First Out) manner. The last element added to the stack is the first element that comes out. The stack supports three operations - push, pop, peek.

**4.1 Push**
The push operation adds an element to the top of the stack, which in dynamic array terms would be appending an element to the end. This is an efficient O(1) operation as discussed in the previous lesson.

It helps to visualize a stack as an array that is vertical. The pseudocode demonstrates the concept, along with the visual where we add the integers 1 through 4 to the top. The top pointer updates to point at the last item added. The following pseudocode and visual demonstrates this.

```java
// using the pushback function from dynamic arrays to add to the stack
public void push(int n) {
    stack.add(n);
}
```

<img width="1078" height="453" alt="Screenshot 2025-07-18 at 8 13 16 PM" src="https://github.com/user-attachments/assets/160b035b-bd93-4084-8db3-88c00932accf" />

>In many languages there is no built-in stack data structure, but you can use a dynamic array to simulate a stack.

>Since a stack will remove elements in the reverse order that they were inserted in, it can be used to reverse sequences - such as a string, which is just a sequence of characters.

**4.2 Pop**
The pop operation removes the last element from top of the stack, which in dynamic array terms would be reading and removing the last element. This is also an efficient O(1) operation as discussed previously.

```java
public int pop() {
    return stack.remove(stack.size() - 1);
}
```

<img width="887" height="535" alt="Screenshot 2025-07-18 at 8 15 17 PM" src="https://github.com/user-attachments/assets/026eaf81-163b-420c-a4cb-de3b49667bc1" />

>In most languages, before popping, it is a good measure to check if the stack is empty to avoid errors.

**4.3 Peek**
The peek operation is the simplest. It simply returns, the top element without removing it. This is also an efficient O(1) operation.

```java
public int peek() {
    return stack.get(stack.size() - 1);
}
```

Implement Stack from Array List
```java
import java.util.ArrayList;

// Implementing a stack is trivial using a dynamic array
// (which we implemented earlier).
public class Stack {

    ArrayList<Integer> stack = new ArrayList<Integer>();

    public Stack() {   
    }

    public void push(int n) {
        stack.add(n);
    }

    public int pop() {
        return stack.remove(stack.size() - 1);
    }

    public int size() {
        return stack.size();
    }
}
```


**4.4 Time Complexity**
<img width="1096" height="191" alt="Screenshot 2025-07-18 at 8 16 43 PM" src="https://github.com/user-attachments/assets/2e07bc07-b0e0-424c-beed-8721694b2ce7" />

**20. Valid Parentheses**
- For this scenario use a stack
- Push the elements to the stack when you encounter (,{,[ open brackets
- Create a Hash Map which contains ),},] close brackets as key and (,{,[ open brackets as value
- Now, when you encounter a ),},] close brackets check if the top element in Stack is a (,{,[ open brackets, return if no
- If yes, POP out the top element.
- Continue till you reach the end of string.
- Return isEmpty value

```java
public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        Map<Character,Character> closeToOpen = new HashMap<>();
        closeToOpen.put(')','(');
        closeToOpen.put('}','{');
        closeToOpen.put(']','[');

        for(char c:s.toCharArray()){
            if(closeToOpen.containsKey(c)){
                if(!stack.isEmpty() && stack.peek()==closeToOpen.get(c)){
                    stack.pop();
                } else {
                    return false;
                }
            } else {
                stack.push(c);
            }
        }
        return stack.isEmpty();
    }
```

