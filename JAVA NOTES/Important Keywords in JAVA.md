SUPER , THIS , CONSTRUCTOR , FINAL , STATIC , Garbage Collection ,Dynamic method dispatch , Object classes ,var keyword , Wrapper class ,  Call by value and Call by Reference , Inner Class and Packages.

### Super Keyword:
The **`super` keyword** is used to **refer to the refer to the parent class** of a subclass.

**Short Definition:**  
`super` is used to **access parent class variables, methods, and constructors**.
##### Uses of `super` Keyword
There are **3 main uses**:
1️. To **access parent class variable**  
2️. To **call parent class method**  
3️. To **call parent class constructor

```java
//Access Parent Class Variable
class Animal {
    int x = 10;
}
class Dog extends Animal {
    int x = 20;
    void show() {
        System.out.println(super.x); // parent variable
    }
}
```

```java
//Call Parent Class Method
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}
class Dog extends Animal {
    void sound() {
        super.sound(); // calls parent method
        System.out.println("Dog barks");
    }
}
```

```java
//Call Parent Class Constructor
class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
}
class Dog extends Animal {
    Dog() {
        super(); // calls parent constructor
        System.out.println("Dog constructor");
    }
}
```

### `this` Keyword in Java 

The **`this` keyword** is used to **refer to the current class object**.
##### Uses of `this` Keyword:
1️. To **refer current class variable**  
2️. To **call current class method**  
3️. To **call current class constructor**  
4️. To **pass current object as argument**

```java
//Example: Using `this` to refer current class variable
class Student {
    int id;
    String name;
    // Constructor
    Student(int id, String name) {
        this.id = id;       // refers to current class variable
        this.name = name;   // refers to current class variable
    }
    void display() {
        System.out.println(id + " " + name);
    }
    public static void main(String[] args) {
        Student s1 = new Student(101, "Rishu");
        s1.display();
    }
}
```

# `final` Keyword in Java 
The **`final` keyword** is used to **restrict modification** in Java.

**Short Definition:**  
`final` is used to **make variables constant, prevent method overriding, and stop class inheritance**.
#### Uses of `final` Keyword
There are **3 main uses**:

1️. **final Variable**  :A **final variable** is a variable whose **value cannot be changed** once assigned.
Example:
```java
class Test {
    final int x = 10;
    void show() {
        // x = 20; ❌ Error (cannot change value)
        System.out.println(x);
    }
}
```
2️. **final Method**  :A **final method** **cannot be overridden** in a subclass.
Example:
```java
class Animal {
    final void sound() {
        System.out.println("Animal sound");
    }
}
class Dog extends Animal {
    // void sound() { } ❌ Error (cannot override final method)
}
```
3️. **final Class**:A **final class** **cannot be inherited** by another class.
Example:
```java
final class A {

    void show() {
        System.out.println("Hello");
    }
}

// class B extends A { } ❌ Error (cannot inherit final class)
```

**`final` keyword** is used to **restrict modification**:
- **final variable** → Value cannot change
- **final method** → Cannot override
- **final class** → Cannot inherit

# `static` Keyword in Java 

The **`static` keyword** is used to **create variables and methods that belong to the class rather than objects**.
`static` means **class-level member shared by all objects**.

#### Uses of `static` Keyword
There are **3 main uses**:
1️. **Static Variable**  : A **static variable** is **shared among all objects** of the class.
Example:
```java
class Student {
    static String college = "ABC College";
    void display() {
        System.out.println(college);
    }
}
```
2️. **Static Method**  : A **static method** belongs to the class and can be **called without creating an object**.
Example:
```java
class Test {
    static void show() {
        System.out.println("Static method called");
    }
    public static void main(String[] args) {
        show(); // calling static method
    }
}
```
3️. **Static Block** : A **static block** is used to **initialize static variables**.
Example:
```java
class Test {
    static int x;
    static {
        x = 100;
        System.out.println("Static block executed");
    }
}
```

# **What is Garbage Collection in Java?**

**Garbage Collection (GC)** in Java is the process of **automatically deleting unused objects** from memory.
It helps:
- Free memory 
- Prevent memory leaks
- Improve program performance

Garbage Collection is the automatic process of removing unused objects from heap memory to free space.
Garbage Collection works in Heap Memory only.

Garbage : An object becomes **garbage** when it is **no longer referenced** by any variable.
Example:
```java
class Main {
    public static void main(String[] args) {
        Main obj1 = new Main();
        obj1 = null;  // Object becomes garbage
    }
}
```
#### Steps of how garbage collection works :
Object is created in **heap**  
Object is **no longer used**  
JVM detects unused object  
Garbage Collector removes it  
Memory becomes free

### Constructor in java:
- A **constructor in Java** is a special method used to **initialize objects** when they are created.
- Constructors do not return any type while methods  have the return type or void if it doesn't return any value.
- If a class does not have constructor , the java compiler automatically create a default constructor during run-time.
- A constructor cannot be abstract  or static or final.
- A constructor can be overloaded but not be overridden.

Syntax:
```java
class ClassName {  
ClassName() {  
// constructor code  
}  
}
```
#### Two types of Constructor
#### 1 . Default Constructor: 
- It has no parameters.
- It can be implicit or explicit.
- If we don't define explicitly , we get an implicit default constructor.

Example:
```java
class Student {
    String name;
    // Default constructor
    Student() {
        name = "Unknown";
    }
    public static void main(String[] args) {
        Student s1 = new Student();  // constructor called
        System.out.println(s1.name);
    }
}
```

#### 2. Parameterized Constructor
 - A  Constructor that has parameters.
 - It is a special method used to initialize an object with specific values at the moment it is created.
  - It does not have a return type, not even `void`
Example :
```java
class Student {
    String name;
    int age;
    // Parameterized constructor
    Student(String n, int a) {
        name = n;
        age = a;
    }
    public static void main(String[] args) {
        Student s1 = new Student("Rishu", 20);
        System.out.println(s1.name);
        System.out.println(s1.age);
    }
}
```

#### Constructor Overloading:
You can create **multiple constructors** with different parameters.
Example:
```java
class Student {
    String name;
    int age;
    Student() {
        name = "Unknown";
        age = 0;
    }
    Student(String n, int a) {
        name = n;
        age = a;
    }
}
```

#### `var` Keyword in Java
The **`var` keyword** in Java is used for **local variable type inference**.  
It means **Java automatically determines the variable's type** from the value you assign to it.

Syntax:
```java
var variableName = value;
```
Example:
```java
var num = 10;        // int
var name = "Rishu";  // String
var price = 99.99;   // double

System.out.println(num);
System.out.println(name);
System.out.println(price);
```
Example 2:
```java
//using collections 
var list = new ArrayList<String>();

list.add("Java");
list.add("Python");

System.out.println(list);
// Instead of writing ArrayList<String> list = new ArrayList<String>();
```
### Dynamic Method Dispatch in Java (Runtime Polymorphism)

**Dynamic Method Dispatch** is the mechanism by which a call to an **overridden method** is resolved at **runtime**, not compile time.

A **parent class reference** can refer to a **child class object**,  
and the method that gets executed depends on the **actual object type at runtime**.

Syntax:
```java
Parent obj = new Child();
obj.method();
```

Example 1 :
```java
class Animal {

    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {

    public static void main(String[] args) {

        Animal obj = new Dog(); // upcasting
        obj.sound(); // runtime decision

    }
}
```

Example 2 :
```java
class Shape {
    void draw() {
        System.out.println("Drawing shape");
    }
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing circle");
    }
}

class Square extends Shape {
    void draw() {
        System.out.println("Drawing square");
    }
}

public class Test {
    public static void main(String[] args) {

        Shape s;

        s = new Circle();
        s.draw(); // Circle version

        s = new Square();
        s.draw(); // Square version
    }
}
```

### Object Class in Java
In Java, **`Object` class** is the **root (parent) class of all classes**.  
Every class you create in Java **automatically extends `Object` class**, even if you don’t write it explicitly.

```java
class A { }
```
Actually becomes:
```java
class A extends Object { }
```
So, every object in Java inherits methods from the **Object class**.

## Important Methods of Object Class

#### 1️. `toString()`
Returns a string representation of the object.

```java
class Student {  
    int id = 1;  
    String name = "Rishu";  
  
    public static void main(String[] args) {  
        Student s = new Student();  
        System.out.println(s.toString());  
    }  
}

OR we can override it.
class Student {
    int id = 1;
    String name = "Rishu";

    public String toString() {
        return id + " " + name;
    }
}
```

#### 2️. `equals(Object obj)`
Used to compare two objects.
By default → compares **memory address**

```java
Student s1 = new Student();  
Student s2 = new Student();  
  
System.out.println(s1.equals(s2)); // false
System.out.println(s1 == s2);//false
```
#### 3️. `hashCode()`
Returns an integer representation of the object (used in hashing structures like HashMap).

```java
Student s = new Student();  
System.out.println(s.hashCode());
```

#### 4️. `getClass()`
Returns runtime class information.
```java
Student s = new Student();  
  
System.out.println(s.getClass().getName());

```
#### 5️. `clone()`
Creates a **copy of an object** (requires implementing `Cloneable` interface).

---
#### 6️. `finalize()` (Deprecated)
Called before garbage collection (not used in modern Java).

## Wrapper Classes in Java
A **Wrapper Class** is a class that converts a **primitive data type into an object**.
####  Why Wrapper Classes?
Java is not purely object-oriented because it has primitives like:  
`int, char, boolean, etc.`
But sometimes we need objects (for Collections, Generics, etc.), so wrapper classes are used.

---
###  Primitive → Wrapper Mapping

|Primitive|Wrapper Class|
|---|---|
|int|Integer|
|char|Character|
|float|Float|
|double|Double|
|boolean|Boolean|
|byte|Byte|
|short|Short|
|long|Long|

---
##### 🔹 Example
```java
public class Main {  
    public static void main(String[] args) {  
        int a = 10;  
        // converting primitive to object (boxing)  
        Integer obj = Integer.valueOf(a);  
        System.out.println(obj);  
    }  
}

```
---
###  Types of Conversion

#### 1️⃣ Autoboxing (Primitive → Object)
Java automatically converts primitive to wrapper object.
```java
int a = 5;  
Integer obj = a;  // autoboxing
```
---
#### 2️⃣ Unboxing (Object → Primitive)
Wrapper object → primitive value.

```java
Integer obj = 10;  
int a = obj;  // unboxing
```

---
##### 🔹 Example (Both Together)
```java
public class Main {  
    public static void main(String[] args) {  
  
        Integer a = 100; // autoboxing  
        int b = a;       // unboxing  
  
        System.out.println(a);  
        System.out.println(b);  
    }  
}
```

Wrapper classes are used in **Collections**:
```java
ArrayList<Integer> list = new ArrayList<>();  
list.add(10); // int → Integer automatically (autoboxing)
```
Collections cannot store primitives directly.

### Call by Value vs Call by Reference in Java

This is a **very important interview concept**, but Java behaves in a slightly tricky way.

---
####  1. Call by Value (Java’s actual behavior)
 #### Java is **always Call by Value**.

This means:
- A **copy of the value** is passed to the method
- Changes inside the method **do not affect original variable**

---
##### 🔹 Example (Primitive Types)

```java
public class Main {

    static void change(int x) {
        x = 100;
    }

    public static void main(String[] args) {

        int a = 10;

        change(a);

        System.out.println(a);//10 because only a copy of 'a' is passes
    }
}
```

---
###  2. What about Objects?

Java still uses **Call by Value**, but for objects it passes:
 **copy of reference (address)**

---
#### 🔹 Example (Objects)

```java
class Student {  
    String name;  
}  
  
public class Main {  
  
    static void change(Student s) {  
        s.name = "Harry";  
    }  
  
    public static void main(String[] args) {  
  
        Student s1 = new Student();  
        s1.name = "Ron";  
  
        change(s1);  
  
        System.out.println(s1.name);  //Harry
    }  
}
```

Note: Call by Reference is not in java .


## Java Inner Classes

In Java, it is also possible to nest classes (a class within a class). The purpose of nested classes is to group classes that belong together, which makes your code more readable and maintainable.

To access the inner class, create an object of the outer class, and then create an object of the inner class:
Example:
```java
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);// Outputs 15 (5 + 10)
  }
}
```

## Static Inner Class

An inner class can also be `static`, which means that you can access it without creating an object of the outer class:
### Example
```java
class OuterClass {
  int x = 10;

  static class InnerClass {
    int y = 5;
  }
}
public class Main {
  public static void main(String[] args) {
    OuterClass.InnerClass myInner = new OuterClass.InnerClass();
    System.out.println(myInner.y);// Outputs 5
  }
}
```

# Java Packages
A **package** in Java is a **namespace** used to group related classes and interfaces together.
Think of it as **a folder in a file directory**. We use packages to avoid name conflicts, and to write a better maintainable code. Packages are divided into two categories:
- Built-in Packages (packages from the Java API)
- User-defined Packages (create your own packages)

#### 1. Built-in Packages (Java API)
Java provides many ready-made packages:
- `java.lang` → core classes (String, Math, etc.)
- `java.util` → utilities (ArrayList, Scanner, etc.)
- `java.io` → input/output classes
  ```java
  import java.util.Scanner;

public class Test {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
    }
}
  ```

#### 2. User-defined Packages
You can create your own package using the `package` keyword.

Example :
schoolapp
│
├── model        → data classes (Student)
├── service      → business logic (StudentService)
└── main         → execution (Main class)

```java
//Student.java
package model;
public class Student {
    private int id;
    private String name;
    private int marks;
    public Student(int id, String name, int marks) {
        this.id = id;
        this.name = name;
        this.marks = marks;
    }
    public int getId() {
        return id;
    }
    public String getName() {
        return name;
    }
    public int getMarks() {
        return marks;
    }
    public void display() {
        System.out.println(id + " - " + name + " - " + marks);
    }
}
```
```java
//StudentService.java
package service;
import model.Student;
import java.util.ArrayList;
public class StudentService {
    private ArrayList<Student> students = new ArrayList<>();
    // Add student
    public void addStudent(Student s) {
        students.add(s);
    }
    // Display all students
    public void showAll() {
        for (Student s : students) {
            s.display();
        }
    }
    // Get topper student
    public Student getTopper() {
        Student top = students.get(0);
        for (Student s : students) {
            if (s.getMarks() > top.getMarks()) {
                top = s;
            }
        }
        return top;
    }
}
```
```java
//main.java
package main;
import model.Student;
import service.StudentService;
public class Main {
    public static void main(String[] args) {
        StudentService service = new StudentService();
        // Adding students
        service.addStudent(new Student(1, "Ravi", 85));
        service.addStudent(new Student(2, "Amit", 92));
        service.addStudent(new Student(3, "Neha", 78));
        System.out.println("📋 All Students:");
        service.showAll();
        System.out.println("\n🏆 Topper Student:");
        Student top = service.getTopper();
        top.display();
    }
}
Output:All Students:
1 - Ravi - 85
2 - Amit - 92
3 - Neha - 78

Topper Student:
2 - Amit - 92
```
when we compiled , our project should look like :
schoolapp/
├── model/
│     └── Student.java
│     └── Student.class
│
├── service/
│     └── StudentService.java
│     └── StudentService.class
│
├── main/
│     └── Main.java
│     └── Main.class
This project demonstrates Java packages using a simple Student Management System. It is divided into three packages: **model** (stores the `Student` class with data like id, name, and marks), **service** (contains `StudentService` which handles logic like adding students and finding the topper), and **main** (contains the `Main` class which runs the program). This structure shows how packages help organize code into separate layers, making it clean, modular, and easier to maintain.

