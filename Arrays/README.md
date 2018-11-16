# Arrays & ArrayLists

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