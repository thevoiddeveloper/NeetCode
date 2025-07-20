# 5 - Singly Linked Lists

A linked list is another data structure that is like an array in the sense that it stores elements in an ordered sequence. But there are also some key differences.

The main difference is that linked lists are made up of objects called ListNode's. This object contains two attributes:

  1. value - This stores the value of the node. It could be a character, an integer, etc.
  2. next - This stores the reference to the next node in the linked list. The picture below visualizes the ListNode object. This will make more sense a little later on.

**5.1 Creating a Linked List from scratch**

By chaining these ListNode objects together we can build a linked list. We start with a ListNode class:

```java
public class ListNode {
    int val;
    ListNode next;

    public ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}
```
Using the next pointer of each, we can connect the nodes together. Suppose that we have three ListNode objects – ListNode1, ListNode2, ListNode3.

<img width="1076" height="177" alt="Screenshot 2025-07-20 at 7 13 18 PM" src="https://github.com/user-attachments/assets/6a0f3088-c50d-45c2-a65e-52b5df7d8154" />

In this case, our value attribute is a string - red, blue, green.

>When we instantiate a list node, we don't know where it is stored in memory. The nodes likely won't be contiguous like arrays, but that isn't an issue for linked lists. The visual below gives a glimpse of how the nodes would be stored in memory.

<img width="1061" height="362" alt="Screenshot 2025-07-20 at 7 13 53 PM" src="https://github.com/user-attachments/assets/023c0840-36db-4057-9220-6b4e34fc3804" />

Next, we would need to make sure that our next pointers point to another ListNode, and not null. Only the last node in the linked list would have its next pointer point to null.

```java
ListNode1.next = ListNode2;
```
>The address for ListNode2 is retrieved from memory.

<img width="1071" height="248" alt="Screenshot 2025-07-20 at 7 16 00 PM" src="https://github.com/user-attachments/assets/1c3e9aa7-32ec-4abe-87bf-708f8f1ee119" />

ListNode1’s next pointer points to ListNode2. Next, we set the next pointer for ListNode2 and ListNode3.
```java
ListNode2.next = ListNode3;
ListNode3.next = null;
```

<img width="1087" height="147" alt="Screenshot 2025-07-20 at 7 16 53 PM" src="https://github.com/user-attachments/assets/f86bb9cf-a70d-4a1d-b72e-ae911902fce9" />

