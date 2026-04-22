An arrays is a collection of similar types of data having continuous memory allocation.
The indexing of the array starts from 0 .
Arrays are used to store multiple values in a single variable, instead of declaring separate variables for each value.

To declare an array, define the variable type with **square brackets** `[ ]` :
```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
```
```java
int[] myNum = {10, 20, 30, 40};


System.out.println(cars[0]);//Volvo

```

# Declaration of Array
**Syntax:**

dataType[ ] arrayName;


# Array Initialization
**Syntax:**

dataType[] arrayName = {value1, value2, value3};

## The `new` Keyword

You can also create an array by specifying its size with `new`. This makes an empty array with space for a fixed number of elements, which you can fill later:
```java
String[] cars = new String[4]; // size is 4

cars[0] = "Volvo";
cars[1] = "BMW";
cars[2] = "Ford";
cars[3] = "Mazda";

System.out.println(cars[0]); // Outputs Volvo
```


Other example in looping:

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};

for (int i = 0; i < cars.length; i++) {
  System.out.println(cars[i]);
}
```

Calculate the sum of elements:
```java
int[] numbers = {1, 5, 10, 25};
int sum = 0;

for (int i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}
System.out.println("The sum is: " + sum);
```


# Types of Arrays in Java

1️⃣ Single Dimensional Array  
2️⃣ Multidimensional Array

---

# 1️⃣ Single Dimensional Array

Stores elements in **one row**.

**Syntax:**
```java
int[] arr = new int[5];
```

# 2️⃣ Multidimensional Array

Stores elements in **rows and columns**.

**Syntax:**

```java
int[][] arr = new int[3][3];

```

# Traversing an Array

Traversing means **accessing all elements** of an array.

Using **for loop**:

```java
for(int i = 0; i < arr.length; i++) {  
    // access elements  
}

\\using for each loop

for(int num : arr) {  
    // access elements  
}

```

Multidimensional Array

A **multidimensional array** is an array of arrays used to represent **table or matrix form of data**.

## 🔹 Creation of Multidimensional Array

**Syntax:**

```java
arrayName = new dataType[rows][columns];

```

## Declaration of Multidimensional Array

**Syntax:**

```java
dataType[][] arrayName;
```

## Initialization Example

```java
int[][] arr = {  
    {1, 2, 3},  
    {4, 5, 6}  
};

```

# Jagged Array

A **jagged array** is a **multidimensional array** in which **each row can have different number of columns**.

**Short Definition:**  
A **jagged array** is an array of arrays where **rows have different lengths**.

## Declaration of Jagged Array

**Syntax:**

```java
dataType[][] arrayName = new dataType[rows][];
```

## Creation of Jagged Array

Each row is created separately.

```java
arrayName[0] = new dataType[size1];  
arrayName[1] = new dataType[size2];
```

## Initialization Example

```java
int[][] arr = new int[3][];  
  
arr[0] = new int[2];  
arr[1] = new int[3];  
arr[2] = new int[1];

```


**Difference between Array and Arrays in Java:**

|Feature|Array|Arrays|
|---|---|---|
|Definition|An **array** is a data structure used to store multiple values of the same type.|**Arrays** is a **utility class** in Java used to perform operations on arrays.|
|Type|Data structure|Class|
|Package|Built-in language feature|Part of `java.util` package|
|Purpose|Stores data|Provides methods to manipulate arrays|
|Example Use|Storing elements|Sorting, searching, comparing arrays|
|Syntax|`int[] arr = new int[5];`|`Arrays.sort(arr);`|

# Common Methods of Arrays Class

- `sort()` → Sorts array elements
- `binarySearch()` → Searches element
- `equals()` → Compares arrays
- `fill()` → Fills array with values
- `toString()` → Converts array to string

