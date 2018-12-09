# Arrays, ArrayLists & LinkedLists

## Arrays
Arrays in Java are a set amount of similar data types stored in a row in memory. Arrays are great when you know exactly how many elements you have and that they will all be of the same data type.

### Creating Arrays
There are several ways to create an array in Java. One similarity to each solution is that arrays always start with the data type that it will contain and followed with two square brackets e.g. `int[]`.

#### Initialize a variable but do not instantiate the array

```java
int[] myNumbers;
```

Doing it this way is a good idea when you know you will eventually have some data but we do not know how much space we require or what the values are at this moment.

#### Instantiate a new array with a set amount of elements

```java
int[] myNumbers = new int[5];
```

Here we are instantiating a new `int array` and we are passing in the number `5` between the square brackets. This is saying that we know we want an array of integers that can contain up to five integers.

#### Explicitly instantiate an array with elements

```java
int[] myNumbers = { 1, 2, 3, 4, 5 };
```

This method effectively means that we want an array of integers, we need space for five elements, and we already know their values.

### Adding new elements to an existing array

If you've already instantiated an array with a fixed width of elements, `new int[5]`, then all you have are five spaces of memory that will return `null`. The way to add values to this array is to specify the index and give it a value.

```java
int[] myNumbers = new int[3];  // [ null, null, null ]

myNumbers[0] = 1;

System.out.println(Arrays.toString(myNumbers))  // [ 1, null, null ]
```

#### Adding new elements to an already filled array
Sometimes we have an array and later realize the array needs to be larger. If this is the case, we need to increase the capacity the array can hold.

```java
int[] myNums = new int[1];
myNums[0] = 1;

int[] newNums = new int[2];

for (int i = 0; i < myNums.length; i++) {
  newNums[ i ] = myNums[ i ];
}

newNums[ 1 ] = 2;
System.out.println(Arrays.toString(newNums));  // [ 1, 2 ]
```

Maybe, you can already see the problem with this. Lot's of extra code, which means more chances for bugs, and we have to create a new array just to add even a single new element which is taking up more space in memory.

## ArrayLists

### Creating an ArrayList
When creating an ArrayList we need to specify the type that will be stored in the ArrayList, just like Arrays, but the syntax is a little different.

A major difference between Arrays and ArrayLists is:
- We don't need to concern ourselves with the capacity of the ArrayList. Java is smart enough to handle the size on its own so we can add and remove elements whenever we want to.

- ArrayLists consist of objects instead of primitive types. So instead of using `int` you would use `Int`. We can also pass our own created objects as values

### Add element to an ArrayList
Adding a new element to an ArrayList is as simple as calling `<<ArrayListName>>.add(value)`. What's even better is that we don't even need to worry about the size of the ArrayList.

### Removing elements from an ArrayList
Removing elements from an ArrayList would use the `<<ArrayListName>>.remove(value)` but isn't as simple as just adding a new element. You have two options of what you can pass. The first option would be the index of the element in the ArrayList. This is normally found by looping through the ArrayList and when you find the element pass in the iterator counter. The second option is to pass in the object itself and Java will handle it from there.

```java
// required import to work with ArrayLists
import java.util.ArrayList;

// creates a new ArrayList that will contain integers
ArrayList<Integer> myNumbers = new ArrayList<Integer>();
Integer one = new Integer(1);
Integer two = new Integer(2);
Integer three = new Integer(3);

// adding each Integer to the ArrayList
myNumbers.add(one);
myNumbers.add(two);
myNumbers.add(three);
System.out.println(Arrays.toString(myNumbers.toArray()));  // [ 1, 2, 3 ]

// finding the correct Integer and removing it with a for-loop
for (int i = 0; i < myNumbers.size(); i++) {
  if (myNumbers.get(i).equals(one)) {
    myNumbers.remove(i);
  }
}

System.out.println(Arrays.toString(myNumbers.toArray()));  // [ 2, 3 ]

// explicitly removing the value that is object two
myNumbers.remove(two);
System.out.println(Arrays.toString(myNumbers.toArray()));  // [ 3 ]
```

## LinkedLists
Much like an array list, a linked list is a special data type that can hold a list of values in a "ascending" order. I put ascending in quotes because while it appears each element is held in ascending order, 0, 1, 2, ...n, the elements are actually being held in different places in memory. A very simplistic example of this would be if we had 10bits of memory and we wanted to store two boolean values in a linked list, it's very possible one could be stored at memory-index 0, and another stored at memory-index 5. Arrays on the other hand will store each value next to each other in memory. So an array would be at memory-index 0, and memory-index 1.

### Comparing LinkedLists and Arrays
What this means is that we can no longer access our values with a normal iterator value, `int i = 0;`, like we can with an Array and ArrayLists. Instead, we need to use a special `ListIterator` type that contains some methods for getting the next and previous values of our LinkedList. Just to clear up any confusion, finding an element in a LinkedList will **always** be of `O(n)` time complexity. What this also means, is unless you are adding or removing elements from the **Head** or **Tail** of a LinkedList, first and last element respectively, this will also be of linear time complexity.

With so much bad, how could this data structure possibly be useful? Let's take a look back at an Array. Because Arrays need to be held in ascending order, and because each element is nicely seated next to each other in memory, what happens when we want to alter our Array? If we were using an Array at full capacity and we wanted to add to it, we would not only need to copy over all the elements into a new array, but now that new array has to go and find some open space in memory to fit all of the elements in order. If we wanted to remove the zeroth index in this array, the computer would then need to shift **all** the elements in the array to the left so that the array can stay in order. What if we wanted to push a new element in the middle of the Array? Now we want to add a new element to the beginning? All elements need to be shifted to the right in order to make room.

### Comparing LinkedLists to ArrayLists
ArrayLists work much in the same way as an Array. The difference is we don't need to assign any specific amount of space as Java does this for us. So while Java has taken it upon itself to remove this level of complexity from the developer, what do you think is still happening under the hood? Data needs space to live, and Java is going to find that space.

### Creating a LinkedList
To create a LinkedList we must first import the `LinkedList` object from `java.util`. Afterwards, just like an ArrayList we need to specify a type that will live in the LinkedList and instantiate it.

```java
import java.util.LinkedList;

class MyLinkedList {
  LinkedList<String> strings = new LinkedList<String>();
}
```

### Adding to a LinkedList
We can add to a LinkedList in constant time because the LinkedList object holds a pointer reference to its tail. Using the `.add(E e)` method will simply move our new String to the end, update the objects `tail` reference, and update the old tails `.next()` reference to the new tail. We can also add to the `head` of a LinkedList using the `.offerFirst(E e)` method. Both cases, `e` is just the element you want to add.

```java
System.out.println(strings.toString());  // []

strings.add("World!");
System.out.println(strings.toString());  // [World!]

strings.offerFirst("Hello");
System.out.println(strings.toString());  // [Hello, World!]
```

### Removing from a LinkedList
Removing from a LinkedList can also be done in either contant or linear time. Like we learned earlier, LinkedLists keep a reference to their **Head** and **Tail** at all times. Calling the appropriate methods, `.removeFirst()` and `removeLast()`, we can achieve constant time in our applications while removing these elements.

What happens though, if we need to remove elements from somewhere other than the Head or Tail of our LinkedLists? Unfortunately, in order to do this we can only remove these elements in linear time using the `.remove()` method where we can pass in either the "index" of the element we want to remove, or pass in the actual Object that is in the LinkedList.

```java
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) {
        LinkedList<Integer> myInts = new LinkedList<>();
        Integer four = Integer.valueOf(4);

        myInts.add(1);
        myInts.add(2);
        myInts.add(3);
        myInts.add(four);
        myInts.add(5);
        System.out.println(myInts.toString());  // [1, 2, 3, 4, 5]

        // removing the tail (last element)
        myInts.removeLast();
        System.out.println(myInts.toString());  // [1, 2, 3, 4]

        // removing the head (first element)
        myInts.removeFirst();
        System.out.println(myInts.toString());  // [2, 3, 4]

        // passing an "index" to be removed
        myInts.remove(1);
        System.out.println(myInts.toString());  // [2, 4]

        // passing in the actual Object we created earlier, "four"
        myInts.remove(four);
        System.out.println(myInts.toString());  // [2]
    }
}
```

