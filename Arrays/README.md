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