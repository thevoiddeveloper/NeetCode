# 2-Static Arrays

In statically typed languages like Java, C++ and C#, arrays have to have an allocated size and type when initialized. These are known as static arrays.

They are called static because the size of the array cannot change once declared. And once the array is full, it can not store additional elements. Some dynamically typed languages such as Python and JavaScript do not have static arrays to begin with. They have an alternative, which we will discuss in the next lesson.

Let's cover the key operations of an array, and the time complexity associated with each.

**1.1 - Reading from an array**

To read an individual element from an array we can choose the position we want to access via an index. Below we have initialized an array of size 3 called myArray. We also attempt to access an arbitrary element using the index i.

``` java
// initialize myArray
int[] myArray = {1,3,5};

// access an arbitrary element, where i is the index of the desired value
myArray[i];
```

<img width="1168" alt="Screenshot 2025-06-26 at 9 04 18 AM" src="https://github.com/user-attachments/assets/4c442fd9-bfd7-41da-90e5-95cff7311eb6" />

Accessing a single element in an array is always instant because each index of myArray is mapped to an address in the RAM. Regardless of the size of the input array, the time taken to access a single element is the same. We refer to this operation as O(1) in terms of time complexity.

> Note: There is a common confusion that O(1) is always fast. This is not the case. There could be 1000 operations and the time complexity could still be O(1). If the number of operations does not grow as the size of the data or input grows then it is O(1).

**1.2 - Traversing through an array**

We can also read all values within an array by traversing through it. Below are examples of how we could traverse myArray from the start to the end using loops.

``` java
for (int i = 0; i < myArray.length; i++) {
    System.out.println(myArray[i]);
}

// OR

int i = 0;
while (i < myArray.length) {
    System.out.println(myArray[i]);
    i++;
}
```
> The last element in an array is always at index n−1 where n is the size of the array. If the size of our array is 3, the last accessible index is 2.

To traverse through an array of size n the time complexity is O(n). This means the number of operations grows linearly with the size of the array.

For example, with an array of size 10 we would have to perform 10 operations to traverse through it, with an array of size 100 we would have to perform 100 operations, and so on.

**1.3 - Deleting from an array**

1.3.1 - Deleting from the end of the array

In statically typed languages, all array indices are filled with 0s or some default value upon initialization, denoting an empty array.

When we want to remove an element from the last index of an array, setting its value to 0 / null or -1 is the best we can do. This is known as a soft delete. The element is not being "deleted" per se, but it is being overwritten by a value that denotes an empty index. We will also reduce the length by 1 since we have one less element in the array after deletion. The code below demonstrates the concept using [4, 5, 6] as an example.

``` java
// Remove from the last position in the array if the array
// is not empty (i.e. length is non-zero).
public void removeEnd(int[] arr, int length) {
    if (length > 0) {
        // Overwrite last element with some default value.
        // We would also consider the length to be decreased by 1.
        arr[length - 1] = 0;
        length--;
    }
}
```
<img width="1017" alt="Screenshot 2025-06-27 at 8 33 19 AM" src="https://github.com/user-attachments/assets/0051ec51-f6ff-4f6d-a903-aac6c61f5559" />

> 6 is deleted/overwritten by either 0 or −1 to denote that it does not exist anymore. Length is also decremented by 1.

1.3.2 - Deleting at an ith index

If instead of deleting at the end, we wanted to delete an element at a random index i. Would we be able to perform this in O(1)?

We could naively just replace it with a 0, but this would break the contiguous nature of our array. Notice that deleting from the end of an array doesn't make it non-contigious, but deleting from the middle will.

A better approach would be the following:

- We are given the deletion index i.
- We iterate starting from i + 1 until the end of the array.
- We shift each element 1 position to the left.
- (Optional) We replace the last element with a 0 or null to mark it empty, and decrement the length by 1.


The following code demonstrates this operation.
``` java
// Remove value at index i before shifting elements to the left.
// Assuming i is a valid index.
public void removeMiddle(int[] arr, int i, int length) {
    // Shift starting from i + 1 to end.
    for (int index = i + 1; index < length; index++) {
        arr[index - 1] = arr[index];
    }
    // No need to 'remove' arr[i], since we already shifted
}
```

<img width="1085" alt="Screenshot 2025-06-27 at 8 36 46 AM" src="https://github.com/user-attachments/assets/5b3da53d-0310-4e82-9ae1-881d299a12fe" />

26. Remove Duplicates From Sorted Array - Explanation
    Input: nums = [0,0,1,1,1,2,2,3,3,4]
    Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
    - Take two pointers , left and right, start at second element
    - Move the right pointer and check if r != r-1, not equal means we are at a point where both the element is not unique
    - If yes, take the element from r and update it to element at l and increase l by 1.
   
``` java
    public int removeDuplicates(int[] nums) {
        int l = 1;
        for(int r = 1; r < nums.length; r++ ){
            if(nums[r]!=nums[r-1]){
                nums[l++]=nums[r];
            }
        }
        return l;
    }
```


