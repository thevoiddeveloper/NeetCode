# 7 - Queues

Another data structure that overlaps with arrays is a Queue. They are also similar to stacks, except they follow a FIFO approach (First in First Out).
A real world example would be a line at the bank. The first person added to the line (queue) is the first person to be served.

**Implementation and Operations**
The easiest way to implement a queue is using a linked list.

>It is also possible to implement a queue using a dynamic array, but is more involved. To get the same time complexity as a linked list, you would need to use a circular array and perform some additional operations.

The main two operations that queues support are enqueue and dequeue.

## Enqueue

The enqueue operation inserts an element to the end of the queue. If we implement this operation with a singly linked list it runs in O(1) time.

```java
public void enqueue(int val) {
    ListNode newNode = new ListNode(val);

    if (this.right != null) {  
    // Queue is not empty 
        this.right.next = newNode;
        this.right = this.right.next;
    } else {       
    // Queue is empty             
        this.left = newNode;
        this.right = newNode;
    }
}
```
<img width="1054" height="164" alt="Screenshot 2025-08-20 at 10 46 10 PM" src="https://github.com/user-attachments/assets/fcd39c78-a00c-4790-ac49-aab2a211774a" />

## Dequeue

The dequeue operation removes an element from the front of the queue and returns that element.

```java
public int dequeue() {
    if (this.left == null) {
        // Queue is empty 
        System.exit(0);
    }
    int val = this.left.val;
    this.left = this.left.next;
    if (this.left == null) {
        this.right = null;
    }
    return val;
}
```

<img width="1064" height="173" alt="Screenshot 2025-08-20 at 10 58 04 PM" src="https://github.com/user-attachments/assets/83a66572-1cc7-40ec-ab6b-6ddb8f53cbea" />

Similar to stacks, it is a good measure to check if the queue is empty before performing the dequeue opeartion.

There is also a variation of the queue, a double-ended queue, known as a deque (pronounced "deck"). A deque allows you to add and remove elements from both the head and the tail in O(1) time.

One of the most important use cases for the queue is when performing breadth-first search for trees and graphs, which we will cover later in the course.

## Implement Queue

```java
// public class ListNode {
//     int val;
//     ListNode next;
//
//     public ListNode(int val) {
//         this.val = val;
//         this.next = null;
//     }
// }

public class Queue {
    ListNode left;  // front of Queue   front -> [1,2,3]
    ListNode right; // back of Queue   [1,2,3] <- back
    
    public Queue() {
        this.left  = null;
        this.right = null;
    }

    public void enqueue(int val) {
        ListNode newNode = new ListNode(val);
        if (this.right != null) {  
        // Queue is not empty 
            this.right.next = newNode;
            this.right = this.right.next;
        } else {       
        // Queue is empty             
            this.left = newNode;
            this.right = newNode;
        }
    }

    public int dequeue() {
        if (this.left == null) {
            // Queue is empty 
            System.exit(0);
        }
        int val = this.left.val;
        this.left = this.left.next;
        if (this.left == null) {
            this.right = null;
        }
        return val;
    }

    public void print() {
        ListNode cur = this.left;
        while(cur != null) {
            System.out.print(cur.val + " -> ");
            cur = cur.next;
        }
        System.out.println();
    }

}
```

## 1700. Number of Students Unable to Eat Lunch

```java
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        int n = students.length;
        int res = n;
        Queue<Integer> q = new LinkedList<>();
        for(int student:students){
            q.offer(student);
        }

        for(int sandwich:sandwiches){
            int count = 0;
            while(count<n && q.peek()!=sandwich){
                q.offer(q.poll());
                count++;
            }
            if(q.peek()==sandwich){
                q.poll();
                res--;
            }else{
                break;
            }
        }
        return res;
    }
}
```

## 225. Implement Stack using Queues

```java
class MyStack {
    
    private Queue<Integer> q;

    public MyStack() {
        q = new LinkedList<>();
    }
    
    public void push(int x) {
        q.offer(x);
        for(int i=q.size()-1;i>0;i--){
            q.offer(q.poll());
        }
    }
    
    public int pop() {
        return q.poll();
    }
    
    public int top() {
        return q.peek();
    }
    
    public boolean empty() {
        return q.isEmpty();
    }
}
```
