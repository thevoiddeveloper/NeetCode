# 6 - Doubly Linked Lists

Having learned about singly linked lists, let’s next learn about its variation - the Doubly Linked List. As the name implies, each node now has two pointers. In addition to the next pointer, we have a prev pointer which points to the previous node. If the prev pointer points to null, it is an indication that we are at the head of the linked list.

<img width="971" height="519" alt="Screenshot 2025-08-16 at 1 05 28 PM" src="https://github.com/user-attachments/assets/7825c8bf-accc-40af-ae35-bcbb419fbdad" />

**6.1 Operations of a Doubly Linked Lists**

**6.1.1 Insertion End**
Similar to the singly linked list, adding a node to a doubly linked list will run in O(1) time. Only this time, we have to update the prev pointer as well.

For example, if we have three nodes in our linked list, ListNode1, ListNode2 and ListNode3. Now we have another node, ListNode4, that we wish to insert at the end. We will have to update both the next pointer of ListNode3 and the prev pointer of ListNode4.

```java
tail.next = ListNode4;
ListNode4.prev = tail;
tail = tail.next;
```

<img width="986" height="203" alt="Screenshot 2025-08-16 at 1 07 39 PM" src="https://github.com/user-attachments/assets/a79da102-7b62-48a4-a7a0-e425455358d1" />

<img width="988" height="665" alt="Screenshot 2025-08-16 at 1 08 04 PM" src="https://github.com/user-attachments/assets/22b7a4b1-c156-4edc-8b6b-3148e0335d78" />

**6.1.2 Insertion Front**
<img width="1070" height="592" alt="Screenshot 2025-08-16 at 1 08 51 PM" src="https://github.com/user-attachments/assets/7c577194-8e2d-4716-b4c0-2b48b20ec0a2" />

**6.1.3 Deletion End**

Deleting at the end is also a O(1) operation.

- First we get a reference to the node before the tail.
- We update the next pointer of the node before the tail to null.
- We update the tail to be the node before the tail.
- (Optional) We can also update the prev pointer of the old tail to null.

```java
ListNode2 = tail.prev;
ListNode2.next = null;
tail = ListNode2;
```

<img width="881" height="881" alt="Screenshot 2025-08-16 at 1 11 38 PM" src="https://github.com/user-attachments/assets/4674f2c7-3a24-40fa-ab2f-60334180fbea" />

> Since we can insert and remove from the end in O(1) time, in theory, we could implement a stack with a linked list instead of an array. This is less common, but it is a possibility.

**6.1.4 Deletion Front**
<img width="983" height="360" alt="Screenshot 2025-08-16 at 1 12 51 PM" src="https://github.com/user-attachments/assets/a6593f55-e4dc-4b11-b179-b350092d6a69" />

**6.2 Access**

Similar to singly linked lists, we cannot randomly access a node. So in the worst case, we will have to traverse n nodes before reaching the desired node. This would run in O(n) time.

Doubly linked lists have the benefit that we can traverse the list in both directions, as opposed to singly linked lists.

**6.3 Time Complexity**
<img width="1096" height="237" alt="Screenshot 2025-08-16 at 1 14 13 PM" src="https://github.com/user-attachments/assets/f6f6d6c4-7eb8-449e-8bd9-d2b9d1512a0e" />
