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

