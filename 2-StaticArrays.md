# 2-Static Arrays

In statically typed languages like Java, C++ and C#, arrays have to have an allocated size and type when initialized. These are known as static arrays.

They are called static because the size of the array cannot change once declared. And once the array is full, it can not store additional elements. Some dynamically typed languages such as Python and JavaScript do not have static arrays to begin with. They have an alternative, which we will discuss in the next lesson.

Let's cover the key operations of an array, and the time complexity associated with each.

**Reading from an array**
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

**Traversing through an array**
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
