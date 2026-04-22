
# Conditional Statements in Java

## What are Conditional Statements?

**Conditional statements** are used to **make decisions** based on conditions.
They execute different blocks of code depending on whether a condition is **true or false**.

---

# 1️⃣ if Statement

Used to execute code **only if condition is true**.
### Syntax:

```java
if(condition) {  
    // code to execute  
}
```
### Example:

```java
int age = 18;  
  
if(age >= 18) {  
    System.out.println("Eligible to vote");  
}
```

---
# 2️⃣ if-else Statement

Used to execute **one block if true** and **another block if false**.

### Syntax:
```java
if(condition) {  
    // true block  
}  
else {  
    // false block  
}
```
### Example:

```java
int number = 5;  
  
if(number % 2 == 0) {  
    System.out.println("Even Number");  
}  
else {  
    System.out.println("Odd Number");  
}
```

---

# 3️⃣ else-if Ladder

Used to check **multiple conditions**.
### Syntax:
```java
if(condition1) {  
    // code  
}  
else if(condition2) {  
    // code  
}  
else {  
    // default code  
}

```
### Example:
```java
int marks = 85;  
if(marks >= 90) {  
    System.out.println("Grade A");  
}  
else if(marks >= 75) {  
    System.out.println("Grade B");  
}  
else {  
    System.out.println("Grade C");  
}
```

---

# 4️⃣ switch Statement

Used to select **one block from many options**.

### Syntax:
```java
switch(variable) {  
    case value1:  
        // code  
        break;  
    case value2:  
        // code  
        break;  
    default:  
        // code  
}
```

### Example:
```java
int day = 2;  
  
switch(day) {  
  
    case 1:  
        System.out.println("Monday");  
        break;  
  
    case 2:  
        System.out.println("Tuesday");  
        break;  
  
    default:  
        System.out.println("Invalid Day");  
}
```

📌 **break** is used to stop execution.

---

# 🔹 Looping Statements in Java

## What are Loops?

**Loops** are used to **repeat a block of code multiple times**.

---
# 1️⃣ for Loop

Used when the **number of iterations is known**.
### Syntax:
```java
for(initialization; condition; update) {  
    // code  
}
```

### Example:
```java
for(int i = 1; i <= 5; i++) {  
    System.out.println(i);  1 2 3 4 5
}

```

---

# 2️⃣ while Loop

Used when the **condition is checked first**.
### Syntax:

```java
while(condition) {  
    // code  
}
```

### Example:
```java
int i = 1;  
  
while(i <= 5) {  
    System.out.println(i);  
    i++;  
}
```

---
# 3️⃣ do-while Loop

Executes **at least once**, even if condition is false.
### Syntax:

```java
do {  
    // code  
}  
while(condition);
```

### Example:
```java
int i = 1;  
  
do {  
    System.out.println(i);  
    i++;  
}  
while(i <= 5);
```

---

# 🔹 Loop Control Statements

Used to control loop execution.

---
## break Statement: 
It is used to exit the loop irrespective of whether the condition is true or false.

Used to **stop loop immediately**.
### Example:

```java
for(int i = 1; i <= 5; i++) {  
  
    if(i == 3) {  
        break;  
    }  
    System.out.println(i);  //1 2 
}
```

---
## continue Statement
It is used to immediately move to the next iteration of the loop.
### Example:
```java
for(int i = 1; i <= 5; i++) {  
  
    if(i == 3) {  
        break;  
    }  
    System.out.println(i);  //1 2 4 5 
}
```
### return Statement
It is used to exit from the current method.
Example:
```java
public int sum(int a, int b) {
    return a + b; // Returns the result to the caller
}

```
## What is For-Each Loop?

The **for-each loop** (also called **enhanced for loop**) is used to **traverse elements of an array or collection**.

It is **simpler than a normal for loop** and mainly used when you want to **read elements one by one**.

---

# 🔹 Syntax of For-Each Loop

```java
for(dataType variable : arrayName) {  
    // code to use variable  
}
```
### Explanation:
- **dataType** → type of array elements
- **variable** → temporary variable
- **arrayName** → array to traverse

Example:
```java
class SumArray {
public static void main(String[] args) {  
  
int[] arr = {1, 2, 3, 4, 5};  
int sum = 0;  
  
for(int num : arr) {  
  
sum = sum + num;   
}  
System.out.println("Sum = " + sum);   
}  
}
```

