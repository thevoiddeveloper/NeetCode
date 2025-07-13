# 3 - Dynamic Arrays

Dynamic Arrays are a much more common alternative to static arrays. They are useful because they can grow as elements are added. In JavaScript and Python, these are the default arrays.

Unlike static arrays, with dynamic arrays we don’t have to specify a size upon initialization.

In different languages, dynamic arrays may be assigned a default size - Java being 10 and C# being 4. 
Regardless, these are automatically resized at runtime as the arrays grow.

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

<img width="1900" height="629" alt="Screenshot 2025-07-13 at 1 42 49 PM" src="https://github.com/user-attachments/assets/ed112c5e-43bd-426a-b0ec-0f25204b70f0" />



