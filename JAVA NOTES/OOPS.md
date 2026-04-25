OOP stands for **Object-Oriented Programming**.

Procedural programming is about writing procedures or methods that perform operations on the data, while object-oriented programming is about creating objects that contain both data and methods.

# Access Modifiers in Java 

**Access Modifiers** are **keywords used to control the visibility (accessibility) of classes, variables, methods, and constructors** in Java.

**Short Definition:**  
**Access modifiers** define **where a class member can be accessed from.**

---

#  Types of Access Modifiers in Java

There are **4 types of access modifiers**:

1️. public  :Members declared as **public** can be **accessed from anywhere** in the program.
2️. private  : Members declared as **private** can be **accessed only within the same class**.
3️. protected  :Members declared as **protected** can be **accessed within the same package and in subclasses of other packages**.
4️. default (no keyword):When no access modifier is specified, it is called **default access modifier**, and members are accessible **only within the same package**.

| Modifier  | Same Class | Same Package | Subclass | Different Package |
| --------- | ---------- | ------------ | -------- | ----------------- |
| public    | ✅          | ✅            | ✅        | ✅                 |
| protected | ✅          | ✅            | ✅        | ❌                 |
| default   | ✅          | ✅            | ❌        | ❌                 |
| private   | ✅          | ❌            | ❌        | ❌                 |


# Methods (Functions) in Java 
A **method** is a **block of code** that performs a **specific task** and runs when it is called.
###  Syntax
```java
returnType methodName(parameters) {  
    // statements  
}
```
---
#  Parts of a Method

- **Return Type** → Type of value returned
- **Method Name** → Name of the method
- **Parameters** → Input values
- **Method Body** → Code inside `{ }`
- **Return Statement** → Sends value back

---
#  Types of Methods

##### 1️. **Predefined Methods**  (Also known as built in methods)
Methods already available in Java libraries. 
ex: System.out.println( ) , String.length( ) , Math.max( ) , Math.sqrt( ) , Arrays.sort(array) etc.

##### 2️. **User-defined Methods**  
Methods created by the programmer.

# Java Classes and Objects

#### Create a Class
- A class is a blueprint used to create objects that share common properties and behavior.
- Classes is a blueprint which defines some properties and behaviours .

To create a class, use the keyword `class`.
```java
public class Main {
  int x = 5;
}
```

#### Create an Object
- An object is an instance of a class. It represents a specific entity created from the class template.

In Java, an object is created from a class. After defining a class, you can create objects from it using the `new` keyword:
```java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
```

Example : The animal type dog is a class while a particular dog named Tommy is an object of the dog class
### Multiple Objects

You can create multiple objects of one class:
```java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj1 = new Main();  // Object 1
    Main myObj2 = new Main();  // Object 2
    System.out.println(myObj1.x);
    System.out.println(myObj2.x);
  }
}
```

###### **`Main myobj = new Main();`**
- The **reference variable `myobj`** is stored in **stack memory**.
- The **object created using `new Main()`** is stored in **heap memory**.
- `myobj` stores the **address of the object** in heap.
# Method Overloading:
- **Compile-time Polymorphism**
- **Static Polymorphism**
- Early Binding
**Method Overloading** is defining **multiple methods with the same name but different parameters** in the **same class**.

# Method Overriding:
- **Runtime Polymorphism**
- **Dynamic Polymorphism**
- Late Binding
**Method Overriding** occurs when a **subclass provides a specific implementation** of a method already defined in its **parent class**.

| Feature           | Method Overloading                     | Method Overriding               |
| ----------------- | -------------------------------------- | ------------------------------- |
| Definition        | Same method name, different parameters | Same method name and parameters |
| Class             | Same class                             | Different classes               |
| Parameters        | Must be different                      | Must be same                    |
| Inheritance       | Not required                           | Required                        |
| Polymorphism Type | Compile-time                           | Runtime                         |
| Return Type       | Can change (but not alone)             | Must be same or compatible      |

Method Overloading example :
```java
class MathOperations {
    int add(int a, int b) {
        return a + b;
    }
    int add(int a, int b, int c) {
        return a + b + c;
    }
    double add(double a, double b) {
        return a + b;
    }
}
```

Method Overriding Example:
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
```

OOPs mainly includes **four core concepts**:
1️. **Encapsulation**  
2️. **Inheritance**  
3️. **Polymorphism**  
4️. **Abstraction**
These are called the **four pillars of OOPs**.

# 1️. Encapsulation
**Definition:**  
Encapsulation is the **wrapping of data and methods into a single unit (class)**.

**Key Point:**  
Data is **hidden** using **private variables** and accessed using **getter and setter methods**.

---
#  2️. Inheritance
**Definition:**  
Inheritance is the **process of creating a new class from an existing class**.

**Key Point:**  
Helps in **code reuse**.

---
#  3️. Polymorphism

**Definition:**  
**Polymorphism** means **"many forms"**.
In Java, **polymorphism** allows **one method or object to behave in different ways**.
**Types:**
- Method Overloading (**Compile-time polymorphism**)
- Method Overriding (**Runtime polymorphism**)

---
#  4. Abstraction

**Definition:**  
Abstraction is the **process of hiding implementation details and showing only essential features**.

**Key Point:**  
Achieved using **abstract classes** and **interfaces**.

---
# 🔹 Other Supporting Concepts in OOPs

Besides the four pillars, these are also important:

5️. **Class**  
6️. **Object**  
7️. **Constructor**  
8️. **Method**

Example of Encapsulation:
class Student {
```java
    private int marks;   // private data (hidden)
    // Setter method
    void setMarks(int m) {
        marks = m;
    }
    // Getter method
    int getMarks() {
        return marks;
    }
}
```

Example of Abstraction:
```java
abstract class Shape {
    abstract void draw();  // abstract method
}
class Circle extends Shape {
    void draw() {
        System.out.println("Drawing Circle");
    }
}
```

### Inheritence:
**Inheritance** is the process in which **one class acquires the properties , behaviours and methods of another class**.
##### Purpose of Inheritance

- Code **reusability**
- Reduces code duplication
- Improves maintainability
- Supports **method overriding**
- extends keyword is used
Syntax:
```java
class Parent {
    // parent class members
}
class Child extends Parent {
    // child class members
}
```

Example:
```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}
class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```
### Types of Inheritance in Java
There are **5 types**:
##### 1️.**Single Inheritance**  
**Single inheritance** is when **one child class inherits from one parent class**.
Example :
```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}
class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```

##### 2️. **Multilevel Inheritance**  
**Multilevel inheritance** is when **a class inherits from a class that already inherits another class**.
Example:
```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}
class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
class Puppy extends Dog {
    void weep() {
        System.out.println("Puppy weeps");
    }
}
```
##### 3️. **Hierarchical Inheritance**  
**Hierarchical inheritance** is when **multiple child classes inherit from one parent class**.
```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}
class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
class Cat extends Animal {
    void meow() {
        System.out.println("Cat meows");
    }
}
```

##### 4️. **Multiple Inheritance**  
**Multiple inheritance** is when **one class inherits properties from more than one parent class**.
❌ **Not supported using classes in Java**  
✔ Supported using **interfaces**

Example:
```java
interface A {
    void methodA();
}
interface B {
    void methodB();
}
class C implements A, B {
    public void methodA() {
        System.out.println("Method A");
    }
    public void methodB() {
        System.out.println("Method B");
    }
}
```

##### 5️. **Hybrid Inheritance**  
**Hybrid inheritance** is a **combination of two or more types of inheritance** (like hierarchical + multiple).  
✔ Supported using **interfaces
Example:
```java
interface A {
    void methodA();
}
interface B extends A {
    void methodB();
}
class C implements A, B {
    public void methodA() {
        System.out.println("Method A");
    }
    public void methodB() {
        System.out.println("Method B");
    }
}
```
### Interface in Java
An **interface** is a **blueprint of a class** that contains **abstract methods** (methods without body).
Syntax:
```java
interface InterfaceName {
    void method1();
    void method2();
}
class ClassName implements InterfaceName {
    public void method1() {
        // implementation
    }
    public void method2() {
        // implementation
    }
}
```
Example :
```java
interface Animal {
    void sound();
}
class Dog implements Animal {
    public void sound() {
        System.out.println("Dog barks");
    }
}
```

### Abstraction and `abstract` Keyword in Java

**Abstraction** is the process of **hiding implementation details** and showing **only essential features** to the user.
#### How Abstraction is Achieved
Abstraction is achieved using:
1️. **Abstract Class**  
2️. **Interface

The `abstract` keyword is a non-access modifier, used for classes and methods:

- **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).
  
- **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from).

Syntax of abstract class :
```java
abstract class Shape {
    abstract void draw();  // abstract method
}
```

Example of Abstract class :
```java
abstract class Animal {
    abstract void sound();  // abstract method
}
class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```
##### `abstract` Keyword
The **`abstract` keyword** is used to **declare abstract classes and abstract methods**.
Example :
```java
abstract class Shape {
    abstract void draw();
    void display() {
        System.out.println("Display shape");
    }
}
```

(class , class ) -> extends
(Interface ,  class) -> Implements
(Interface , Interface) -> extends
class implements 2 interfaces
interface extends 2 interfaces

```java
// Interface Example
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

#### Multiple Interfaces:
To implement multiple interfaces, separate them with a comma:
```java
interface FirstInterface {
  public void myMethod(); // interface method
}

interface SecondInterface {
  public void myOtherMethod(); // interface method
}

class DemoClass implements FirstInterface, SecondInterface {
  public void myMethod() {
    System.out.println("Some text..");
  }
  public void myOtherMethod() {
    System.out.println("Some other text...");
  }
}

class Main {
  public static void main(String[] args) {
    DemoClass myObj = new DemoClass();
    myObj.myMethod();
    myObj.myOtherMethod();
  }
}
```