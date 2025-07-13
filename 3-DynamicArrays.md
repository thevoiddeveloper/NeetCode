# 3 - Dynamic Arrays

Dynamic Arrays are a much more common alternative to static arrays. They are useful because they can grow as elements are added. In JavaScript and Python, these are the default arrays.

Unlike static arrays, with dynamic arrays we don’t have to specify a size upon initialization.

In different languages, dynamic arrays may be assigned a default size - Java being 10 and C# being 4. 
Regardless, these are automatically resized at runtime as the arrays grow.

**3.1 - Dynamic Array Insertion**

When inserting at the end of a dynamic array, the next empty space is found and the element is inserted there. 
Consider an array of size 3 where we push elements into it until we run out of space.
<img width="1900" height="629" alt="Screenshot 2025-07-13 at 1 42 49 PM" src="https://github.com/user-attachments/assets/ad4183d7-e31a-4fc0-889a-a2e60b0ed0bd" />

```java
// Insert n in the last position of the array
public void pushback(int n) {
    if (length == capacity) {
        this.resize();
    }
    // insert at next empty position
    arr[length] = n;
    length++;
}
```

**3.2 - Resize**

Since the array is dynamic in size, we can continue to add elements. But it's not magic, this is achieved by copying over the values to a new static array that is double the size of the original. This means that the resulting array will be of size 6 and will have new space allocated for it in memory. The following visual and code demonstrates this resize operation.

```java
public void resize() {
    // Create new array of double capacity
    capacity = 2 * capacity;
    int[] newArr = new int[capacity]; 
    
    // Copy elements to newArr
    for (int i = 0; i < length; i++) {
        newArr[i] = arr[i];
    }
    arr = newArr;
}
```
<img width="1082" height="590" alt="Screenshot 2025-07-13 at 1 54 01 PM" src="https://github.com/user-attachments/assets/b4422aab-099a-41b7-9188-67c174e63160" />

> When all the elements from the first array have been copied over, the first static array will be deallocated.

Adding elements to a dynamic array runs in O(1) amortized time.

Amortized time complexity is the average time taken per operation over a sequence of operations. The resize operation itself is O(n), but since it is not performed every time we add an element, the average time taken per operation is O(1). But this is only the case if we double the size of the array when we run out of space.

Why double the capacity?
The visual below shows a resulting array of size 8. Now imagine that we wanted to dynamically fill it up and we started with a size 1 array. We would add 5, double the space to add 6, double that space to add 7 and 8, double that space to add 9, 10, 11 and 12.

<img width="960" height="657" alt="Screenshot 2025-07-13 at 1 57 22 PM" src="https://github.com/user-attachments/assets/e1665e43-add3-4fc5-b208-54277e57d78d" />

The size of the above array went from 1 -> 2 -> 4 -> 8.

To analyze the time complexity we have to take into consideration the sum of all the operations that occured before the last one since we would not have gotten to the resulting array without these operations. To achieve an array of size 8, we would have to perform 1+2+4+8=15 operations, which includes the resize operations.

The pattern here is that the last term (the dominating term) is always greater than or equal to the sum of all the terms before it. In this case, 1+2+4=7, and 7<8. Add in the 8 to the 7, we get a total of 15 operations to create the resulting array of size 8.

Generally, the formula is that for any array size n, it will take at most 2n operations to create, which would belong to O(n).

Since inserting n elements into a dynamic array is O(n), the amortized time complexity of inserting a single element is O(1).

>With time complexity, we are concerned with asymptotic analysis. This means we care about how quickly the runtime grows as the input size grows. We don't distinguish between O(2n) and O(n) because the runtime grows linearly >with the input size, even if the constant is doubled.
>With time complexity analysis, we typically drop constant terms and coefficients.


Other Operations
Inserting or removing from the middle of a dynamic array would be similar to a static array. We would have to shift elements to the right or left to make space for the new element or to fill the gap left by the removed element. This would run in O(n) time.

## Time Complexity
<img width="1100" height="196" alt="Screenshot 2025-07-13 at 2 05 49 PM" src="https://github.com/user-attachments/assets/57be831f-9908-4b25-b1f6-0f91ab33d418" />

**1929. Concatenation of Array**
- Create a reult array of twice the size
- Run a loop from 0 to original size
- make ith element and i+nth element of result array equal to ith element in original array

```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int[] ans = new int[2*nums.length];
        int n = nums.length;
        for(int i=0;i<nums.length;i++){
            ans[i]=ans[i+n]=nums[i];
        }
        return ans;
    }
}
```
