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