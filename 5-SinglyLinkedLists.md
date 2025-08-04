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

**5.2 Traversal**

To traverse a linked list from beginning to end, we can just make use of a simple while loop.

```java
ListNode cur = ListNode1;
while (cur != null) {
    cur = cur.next;
}
```

  1. We start the traversal at the head of the list, which is ListNode1.
  2. We assign it to a variable cur, denoting the current node we are at.
  3. We execute the while loop until we reach the end of the list which is null.
  4. In each iteration, we update cur to be the next node in the list by setting cur = cur.next.
  5. The traversal runs in O(n) time where n is the number of nodes in the linked list.

<img width="1078" height="876" alt="Screenshot 2025-07-20 at 7 23 11 PM" src="https://github.com/user-attachments/assets/bcac7ec7-8f0c-4a61-a1f1-b2c94536e658" />

**5.3 Circular Linked List**

An interesting scenario presents itself if ListNode3’s next pointer is set to ListNode1 instead of null. This results in a circular linked list.

Attempting to iterate through a circular linked list would result in an infinite loop. We would never reach the end of the linked list.

<img width="1081" height="187" alt="Screenshot 2025-07-20 at 7 24 23 PM" src="https://github.com/user-attachments/assets/047ef31f-dbd9-48d6-80c2-f6972a6022be" />

**5.4 Operations of a Singly Linked List**

Linked Lists have a head, and a tail pointer. The head pointer points to the very first node in the linked list, ListNode1, and the tail pointer points to the very last node — ListNode3. If there is only one node in the Linked List, the head and the tail point to the same node.

5.4.1 Appending

An advantage that Linked Lists have over arrays is that inserting a new element can be performed in O(1) time, even if we insert in the middle.

We do not have to shift any elements since there is no requirement for the elements to be stored contiguously in memory.

>This assumes we already have a reference to the node at the desired position we want to insert. If we have to traverse the list to arrive at the insertion point, the operation would take O(n) time.

If we wanted to append a ListNode4 to the end of the list, we would be appending to the tail. Once ListNode4 is appended, we update our tail pointer to be at ListNode4. This operation would be done in O(1) time since it is only one operation. The steps would look like the following, with code.

<img width="1085" height="311" alt="Screenshot 2025-07-20 at 7 26 53 PM" src="https://github.com/user-attachments/assets/13830ce3-3b46-498f-9a33-a8645b8b1f9b" />

```java
tail.next = ListNode4;
```

<img width="1079" height="244" alt="Screenshot 2025-07-20 at 7 27 34 PM" src="https://github.com/user-attachments/assets/50b6aa7d-6011-430a-b301-477e187fafb5" />

```java
tail = ListNode4;
```

<img width="1082" height="217" alt="Screenshot 2025-07-20 at 7 28 09 PM" src="https://github.com/user-attachments/assets/cb65514f-70f7-4654-9e1a-8e53d79fa72e" />

5.4.2 Deleting from a Singly Linked List

Deleting a node from a singly linked list will take O(1) since we can accomplish this by updating a single pointer.

>This assumes we already have a reference to the node at the desired position we want to delete. If we have to traverse the list to arrive at the deletion point, the operation would take O(n) time.

Suppose we want to delete ListNode2. Currently, our head points to ListNode1, and head.next points to ListNode2. We can update our head.next pointer to ListNode3, which can be accessed by chaining next pointers like head.next.next. This makes sense since head.next is ListNode2, and logically, head.next.next would be ListNode3.

<img width="1075" height="297" alt="Screenshot 2025-07-20 at 7 30 19 PM" src="https://github.com/user-attachments/assets/1b6c5dc6-56ad-4fc6-bbbc-ffa6524f2904" />

```java
head.next = head.next.next;
```
<img width="1076" height="256" alt="Screenshot 2025-07-20 at 7 30 52 PM" src="https://github.com/user-attachments/assets/aaf18d82-e865-4886-8a70-caa7480acb43" />

Updated linked list after deletion of ListNode2. Notice that now ListNode1’s next pointer points to ListNode3, instead of ListNode2

<img width="1078" height="282" alt="Screenshot 2025-07-20 at 7 31 21 PM" src="https://github.com/user-attachments/assets/a47b5287-f608-4d89-84a5-6e56109166d1" />


>It can be assumed that the memory occupied by ListNode2 will be cleared via garbage collection in most languages. In other languages like C, you would have to manually free the memory.

## Time Complexity

<img width="1100" height="244" alt="Screenshot 2025-07-20 at 7 31 35 PM" src="https://github.com/user-attachments/assets/4d6e2231-406f-41a8-aaf9-1cf05a80b2a9" />

**206. Reverse Linked List**
- Basicly we need to make Head as tail and tail as Head with reversing the pointing direction from front to back
- Start with two pointers Current pointing to head and previous pointing to null.
- Loop through the list till we reach current != null
- First, Take a temp var and store the current.next
- Second, currrent.next will point to previous
- Third, Move previous to current and current to the temp variable
- Return head as previous at the end

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode current = head;
        ListNode previous = null;
        while(current!=null){
            ListNode next = current.next;
            current.next=previous;
            previous=current;
            current=next;
        }
        return previous;
    }
}
```

**21. Merge Two Sorted Lists**
- Take a dummy pointer

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode();
        ListNode cur = dummy;
        while(list1 != null && list2 != null){
            if(list1.val < list2.val){
                cur.next = list1;
                list1 = list1.next;
            } else {
                cur.next = list2;
                list2 = list2.next;
            }
            cur = cur.next;
        }
        
        if(list1!=null)
            cur.next = list1;
        else if(list2!=null)
            cur.next = list2;
        return dummy.next;
    }
}
```

## Design Singly Linked List
Solved 
Design a Singly Linked List class.

Your LinkedList class should support the following operations:

LinkedList() will initialize an empty linked list.
int get(int i) will return the value of the ith node (0-indexed). If the index is out of bounds, return -1.
void insertHead(int val) will insert a node with val at the head of the list.
void insertTail(int val) will insert a node with val at the tail of the list.
bool remove(int i) will remove the ith node (0-indexed). If the index is out of bounds, return false, otherwise return true.
int[] getValues() return an array of all the values in the linked list, ordered from head to tail.
Example 1:

Input: 
["insertHead", 1, "insertTail", 2, "insertHead", 0, "remove", 1, "getValues"]

Output:
[null, null, null, true, [0, 2]]


```java
// Singly Linked List Node
class ListNode {
    int val;
    ListNode next;

    // Constructor that sets 'next' to null by default
    public ListNode(int val) {
        this(val, null);
    }

    // Constructor that accepts both value and next node
    public ListNode(int val, ListNode next) {
        this.val = val;
        this.next = next;
    }
}

// Implementation for Singly Linked List
class LinkedList {
    private ListNode head;
    private ListNode tail;

    // Constructor
    public LinkedList() {
        // Init the list with a 'dummy' node which makes
        // removing a node from the beginning of list easier.
        this.head = new ListNode(-1);
        this.tail = this.head;
    }

    public int get(int index) {
        ListNode curr = head.next;
        int i = 0;
        while (curr != null) {
            if (i == index) {
                return curr.val;
            }
            i++;
            curr = curr.next;
        }
        return -1;  // Index out of bounds or list is empty
    }

    public void insertHead(int val) {
        ListNode newNode = new ListNode(val);
        newNode.next = head.next;
        head.next = newNode;
        if (newNode.next == null) {  // If list was empty before insertion
            tail = newNode;
        }
    }

    // Method to insert at the end
    public void insertTail(int val) {
        this.tail.next = new ListNode(val);
        this.tail = this.tail.next;
    }

    // Method to remove at given index
    public boolean remove(int index) {
        int i = 0;
        ListNode curr = this.head;
        while (i < index && curr != null) {
            i++;
            curr = curr.next;
        }

        // Remove the node ahead of curr
        if (curr != null && curr.next != null) {
            if (curr.next == this.tail) {
                this.tail = curr;
            }
            curr.next = curr.next.next;
            return true;
        }
        return false;
    }

    // Method to get values of the linked list
    public ArrayList<Integer> getValues() {
        ArrayList<Integer> res = new ArrayList<>();
        ListNode curr = this.head.next;
        while (curr != null) {
            res.add(curr.val);
            curr = curr.next;
        }
        return res;
    }
}
```
