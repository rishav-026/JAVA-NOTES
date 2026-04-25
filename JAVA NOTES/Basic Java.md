JAVA Is an  Object oriented programming language developed at sun microsoft systems of USA in 1991.
It was originally called Oak by James Goslin
Java is a platform independent because WORA(write once read anytime).
It is used for:
- Mobile applications (specially Android apps)
- Desktop applications
- Web applications
- Web servers and application servers
- Database connection
- And much, much more!

## Working of Java Program:
Source code --Compiled by Javac-->>Byte Code --Interpreted by JVM-->> Machine Code

JVM (Java Virtual Machine):JVM is the engine that runs Java programs.
It **converts Java code into machine code** so your computer understands it.
## What JVM does:
- Runs compiled Java code (.class files)
- Converts bytecode → machine code
- Manages memory
- Handles garbage collection

**JRE**(Java Runtime Environment): It provides everything needed to run Java programs.
It contains:
- JVM (to run programs)
- Libraries (ready-made Java code)

**JDK**(Java development Kit):JDK is used to create Java programs.
It contains:
- JRE
- Compiler (javac)
- Development tools

## Basic Structure of Java

```java
java.util.Scanner;
public class Main {
  public static void main(String[] args) {
    System.out.println("Hello World");
  }
}
```
In this , there are 4 classes ->Scanner , Main , String , System .
We use static keyword , so JVM can invoke it without needing to create an instance of the class .
The main method is the entry point of program and JVM needs to call it directly to start execution before any objects created.

`System.out.println()` may look long, but you can think of it as a single command that means: **"Send this text to the screen."**

Here's what each part means :
- `System` is a built-in Java class.
- `out` is a member of `System`, short for "output".
- `println()` is a method, short for "print line".

Finally, remember that each Java statement must end with a semicolon (`;`).

### Java Type Casting
Type casting means converting one data type into another. For example, turning an `int` into a `double`.
In Java, there are two main types of casting:

- **Widening Casting** (automatic) - converting a smaller type to a larger type size  
    `byte` -> `short` -> `char` -> `int` -> `long` -> `float` -> `double`  
      
    
- **Narrowing Casting** (manual) - converting a larger type to a smaller type size  
    `double` -> `float` -> `long` -> `int` -> `char` -> `short` -> `byte`
### Widening Casting

Widening casting is done automatically when passing a smaller size type into a larger size type.
```java
int myInt = 9;
double myDouble = myInt; // Automatic casting: int to double

System.out.println(myInt);    // Outputs 9
System.out.println(myDouble);
```
### Narrowing Casting

Narrowing casting must be done manually by placing the type in parentheses `()` in front of the value.
```java
double myDouble = 9.78d;
int myInt = (int) myDouble; // Manual casting: double to int

System.out.println(myDouble); // Outputs 9.78
System.out.println(myInt); 
```

## Java Operators

**Operators** are symbols used to **perform operations on variables and values**
Java operators are mainly divided into:
1. Arithmetic Operators
2. Relational (Comparison) Operators
3. Logical Operators
4. Assignment Operators
5. Unary Operators
6. Increment and Decrement Operators
7. Conditional (Ternary) Operator
8. Bitwise Operators
### 1️. Arithmetic Operators

Used to perform **mathematical calculations**.

|Operator|Meaning|Example|
|---|---|---|
|`+`|Addition|`a + b`|
|`-`|Subtraction|`a - b`|
|`*`|Multiplication|`a * b`|
|`/`|Division|`a / b`|
|`%`|Modulus (remainder)|`a % b`|

### Example:
```java
int a = 10, b = 5;  
System.out.println(a + b); // 15  
System.out.println(a % b); // 0

```
---
# 2️. Relational (Comparison) Operators
Used to **compare two values**.  
Result is always **true** or **false**.

|Operator|Meaning|
|---|---|
|`==`|Equal to|
|`!=`|Not equal to|
|`>`|Greater than|
|`<`|Less than|
|`>=`|Greater than or equal to|
|`<=`|Less than or equal to|

### Example:
```java
int a = 10, b = 20;  
System.out.println(a > b); // false  
System.out.println(a == b); // false
```

---
### 3️. Logical Operators
Used to **combine conditions**.

|Operator|Meaning|
|---|---|
|`&&`|Logical AND|
|`||
|`!`|Logical NOT|

### Example:
```java
int a = 10;  
System.out.println(a > 5 && a < 20); // true  
System.out.println(!(a > 5)); // false
```

---
### 4️. Assignment Operators
Used to **assign values** to variables.

|Operator|Meaning|Example|
|---|---|---|
|`=`|Assign|`a = 10`|
|`+=`|Add and assign|`a += 5`|
|`-=`|Subtract and assign|`a -= 5`|
|`*=`|Multiply and assign|`a *= 5`|
|`/=`|Divide and assign|`a /= 5`|
### Example:
```java
int a = 10;  
a += 5; // a = a + 5
```

---
### 5️. Unary Operators
Operate on **single operand**.

|Operator|Meaning|
|---|---|
|`+`|Unary plus|
|`-`|Unary minus|
|`!`|Logical NOT|
### Example:
```java
int a = 5;  
System.out.println(-a); // -5
```
---

### 6️. Increment and Decrement Operators
Used to **increase or decrease value by 1**.

|Operator|Meaning|
|---|---|
|`++`|Increment|
|`--`|Decrement|
### Types:
**Pre-Increment**      ++a;
**Post-Increment**     a++;
### Example:
```java
int a = 5;  
a++; // a becomes 6
```

---
### 7️. Conditional (Ternary) Operator
Used as **shortcut for if-else**.

### Syntax:
condition ? value1 : value2;
### Example:
```java
int a = 10, b = 20;  
int max = (a > b) ? a : b;

```
---
### 8️. Bitwise Operators (Basic Idea)
Used to perform **bit-level operations**.

|Operator|Meaning|
|---|---|
|`&`|Bitwise AND|
|`|`|
|`^`|Bitwise XOR|
|`~`|Bitwise NOT|
## Operator Precedence (Important Short Note)

Order of execution:

1. `()`
2. `++ --`
3. `* / %`
4. `+ -`
5. Relational
6. Logical
7. Assignment

## Data Types in Java
**Data Types** define the **type of data** a variable can store.

### Types of Data Types in Java
Java data types are divided into:

1️.Primitive Data Types  
2️. Non-Primitive Data Types

### Primitive Data Types
Primitive data types store **simple values**.
There are **8 primitive data types** in Java.

|Data Type|Size|Description|Example|
|---|---|---|---|
|byte|1 byte|Small integer|`byte b = 10;`|
|short|2 bytes|Short integer|`short s = 100;`|
|int|4 bytes|Integer|`int a = 1000;`|
|long|8 bytes|Large integer|`long l = 10000L;`|
|float|4 bytes|Decimal number|`float f = 10.5f;`|
|double|8 bytes|Large decimal|`double d = 20.99;`|
|char|2 bytes|Single character|`char c = 'A';`|
|boolean|1 bit|True/False|`boolean b = true;`|

### 2️. Non-Primitive Data Types
Non-primitive data types store **complex data**.

They are **created by the programmer**.
### Examples:
- String
- Array
- Class
- Object
- Interface
## What is a Variable?
A **variable** is a **named memory location** used to store data.
### Types of Variables in Java
Java variables are divided into **3 types**:

1️. Local Variables  
2️. Instance Variables  
3️. Static Variables

#### 1.Local Variables
- Declared **inside a method**
- Used **only within that method**
- Must be initialized before use
#### 2.Instance Variables
- Declared **inside class but outside method**
- Each object gets its own copy
- Also called **non-static variables**
#### 3.Static Variables
- Declared using **static keyword**
- Shared among all objects
- Only one copy exists

## Identifiers

All Java **variables** must be **identified** with **unique names**.
These unique names are called **identifiers**.
Identifiers can be short names (like x and y) or more descriptive names (age, sum, totalVolume).

The general rules for naming variables are:

- Names can contain letters, digits, underscores, and dollar signs
- Names must begin with a letter
- Names should start with a lowercase letter, and cannot contain whitespace
- Names can also begin with $ and _
- Names are case-sensitive ("myVar" and "myvar" are different variables)
- Reserved words (like Java keywords, such as `int` or `boolean`) cannot be used as names.


