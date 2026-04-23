Exception handling lets you catch and handle errors during runtime - so your program doesn't crash.
It uses different keywords:

The `try` statement allows you to define a block of code to be tested for errors while it is being executed.
The `catch` statement allows you to define a block of code to be executed, if an error occurs in the try block.
```java
try {
  //  Block of code to try
}
catch(Exception e) {
  //  Block of code to handle errors
}
```
Example:
```java
public class Test {  
public static void main(String[] args) {  
int a = 10;  
int b = 0;  
  
int c = a / b; // ❌ Error: divide by zero  
System.out.println(c);  
}  
}
```
Program crashes here.
# Solution: Exception Handling

Java uses these keywords:

##  1. try
Code that may cause error

##  2. catch
Handles the error

##  3. finally (optional)
Always executes

## 4. throw
Manually throw exception

##  5. throws
Declares exception in method

##### try-catch block:
```java
public class Test {
    public static void main(String[] args) {

        try {
            int a = 10;
            int b = 0;
            int c = a / b;  // risky code
            System.out.println(c);
        }
        catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero!");
        }

        System.out.println("Program continues...");
        //Cannot divide by zero!  
        //Program continues...
    }
}
```
##### finally block:
```java
try {
    int a = 10 / 0;
}
catch (Exception e) {
    System.out.println("Error occurred");
}
finally {
    System.out.println("Always executed");
}
```
##### throw keyword:
```java
public class Test {
    static void checkAge(int age) {
        if (age < 18) {
            throw new ArithmeticException("Not eligible");
        } else {
            System.out.println("Eligible");
        }
    }
    public static void main(String[] args) {
        checkAge(15);
    }
}
```
##### throws keyword:
```java
public class Test {
    static void show() throws Exception {
        throw new Exception("Error occurred");
    }

    public static void main(String[] args) {
        try {
            show();
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
    }
}
```
#### Types of Exceptions
##### 1. Checked Exception:
These are exceptions that are **checked by the compiler before running the program**. You must handle them using `try-catch` or `throws`, otherwise code will not compile.
## Common Examples:
- `IOException`
- `FileNotFoundException`
- `SQLException`
- `ClassNotFoundException
Example :
```java
import java.io.FileReader;

public class Test {
    public static void main(String[] args) {
        FileReader fr = new FileReader("abc.txt"); // ❌ Checked Exception
    }
}//this may give the compile time error because file may not exist
```
Correct code:
```java
import java.io.*;

public class Test {
    public static void main(String[] args) {
        try {
            FileReader fr = new FileReader("abc.txt");
        } catch (IOException e) {
            System.out.println("File not found!");
        }
    }
}
```

#### 2️. Unchecked Exceptions (Runtime Exceptions)
These exceptions occur **during program execution** and are **not checked by the compiler**.
## Common Examples:
- `ArithmeticException`
- `NullPointerException`
- `ArrayIndexOutOfBoundsException`
- `NumberFormatException`
Example 1: 
```java
public class Test {
    public static void main(String[] args) {
        int a = 10 / 0; // ❌ Runtime exception
        System.out.println(a);
    }
}
```
Example 2:
```java
public class Test {
    public static void main(String[] args) {
        int arr[] = new int[3];
        System.out.println(arr[5]); // ❌ Error
    }
}
```
#### Errors (Not Exceptions, but related)
Errors are **serious problems that cannot be handled in most cases**.
##### Common Examples:
- `StackOverflowError`
- `OutOfMemoryError`
- `VirtualMachineError`
Example:
```java
public class Test {
    public static void main(String[] args) {
        main(args); // ❌ Infinite recursion → StackOverflowError
    }
}
```
#### Chained Exception:
One exception is caused by another exception.

Sometimes the **real cause of an error is hidden inside another error**.
So chained exceptions help to:
- Identify the **original cause**
- Track the **full error history**
- Debug problems easily
Example:
```java
public class Test {
    public static void main(String[] args) {

        try {
            try {
                int a = 10 / 0; // original exception
            }
            catch (ArithmeticException e) {

                // wrapping original exception inside a new one
                throw new Exception("High-level exception occurred", e);
            }

        } catch (Exception e) {
            System.out.println("Message: " + e.getMessage());

            // printing original cause
            System.out.println("Cause: " + e.getCause());
        }
    }
}
```
#### Custom Exceptions in Java

A **custom exception** is an exception that you **create yourself** in Java to handle specific business rules or application-specific errors.
There are **2 types**:
1️⃣ Checked Custom Exception (extends Exception)
Example:
```java
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}
public class Test {

    static void checkAge(int age) throws InvalidAgeException {
        if (age < 18) {
            throw new InvalidAgeException("Age must be 18 or above");
        } else {
            System.out.println("Eligible to vote");
        }
    }

    public static void main(String[] args) {
        try {
            checkAge(15);
        } catch (InvalidAgeException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }//Output :Error: Age must be 18 or above
}
```

2️⃣ Unchecked Custom Exception (extends RuntimeException)

Example:
```java
class InsufficientBalanceException extends RuntimeException {
    public InsufficientBalanceException(String message) {
        super(message);
    }
}
public class Bank {

    static void withdraw(int balance, int amount) {
        if (amount > balance) {
            throw new InsufficientBalanceException("Not enough balance");
        } else {
            System.out.println("Withdrawal successful");
        }
    }

    public static void main(String[] args) {
        withdraw(1000, 1500);
    }
}
```

### What is Multiple Catch?

**Multiple catch blocks** are used when a single `try` block may throw **different types of exceptions**, and we want to handle each exception separately.
Syntax:
```java
try {
    // risky code
}
catch (ExceptionType1 e) {
    // handling 1
}
catch (ExceptionType2 e) {
    // handling 2
}
catch (ExceptionType3 e) {
    // handling 3
}
```

Example:
```java
public class Test {
    public static void main(String[] args) {

        try {
            int arr[] = new int[3];

            int result = 10 / 0;   // ArithmeticException
            arr[5] = 100;          // ArrayIndexOutOfBoundsException

        }
        catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero!");
        }
        catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index is invalid!");
        }
        catch (Exception e) {
            System.out.println("Some other error occurred!");
        }

        System.out.println("Program continues...");
    }
}
```
# Multithreading

- **Multithreading** in Java is a feature that allows a program to execute **multiple threads simultaneously**.
- Thread is a lightweight subprocess , a smallest unit of processing.
- A process can consist of multiple threads , each of which run concurrently  , sharing the same resource.
Threads can be created in 2 ways :
#### 1. By extending Thread class:
It is the one way to create a thread by extending the thread class and overriding its run () method.
Steps:
- Create a subclass of thread class 
- Override the run() method to define the task 
- Create an object
- Call thee start() method to begin the thread

Example:
```java
class MyThread extends Thread{
public void run(){
System.out.println("Thread is running");
}}
public class Main{
public static void main(String[]  args){
MyThread t1 = new MyThread();
t1.start();
}}
```
#### 2. By Implementing Runnable Interface
It defines the single method run() that must be implemented.
- Instead of extending thread class , we must implement Runnable and pass it to a Thread object.

Example:
```java
class MyRunnable  implements Runnable{
public void run(){
System.out.println("Runnable Thread is running");
}
}
public class Main{
public static void main(String[]  args){
MyRunnable run = new MyRunnable();
MyThread t1 = new MyThread();
t1.start();
}
}
```
# Methods of Thread Class

## (i) `start()`

- It is used to start the execution of a thread.
- `start()` method should be called only once for a thread.
- Calling `start()` creates a new thread and then internally calls the `run()` method.

---
## (ii) `run()`

- Each thread starts in a separate call stack.
- Calling `run()` directly does **not** create a new thread.
- It behaves like a normal method call.

### Example:

```java
class Main extends Thread {  
    public void run() {  
        System.out.println("Thread is running...");  
    }  
  
    public static void main(String[] args) {  
        Main t1 = new Main();  
        t1.run();   // normal method call (no new thread)  
    }  
}
```
---
## (iii) `isAlive()`

- It is used to check whether a thread is alive or not.
- Returns a boolean value:
    - `true` → thread has started and not yet finished
    - `false` → thread not started OR already finished
### Example:

```java
class MyThread extends Thread {  
    public void run() {  
        for (int i = 1; i <= 5; i++) {  
            System.out.println("Child Thread");  
        }  
    }  
}  
  
class DemoThreadMethod {  
    public static void main(String[] args) {  
        MyThread t1 = new MyThread();  
  
        System.out.println(t1.isAlive()); // false  
        t1.start();  
        System.out.println(t1.isAlive()); // true  
    }  
}
```
---

## (iv) `join()`

- It is used to pause the execution of the current thread  
    until the thread on which `join()` is called has finished execution.
### Example:

```java
class MyThread extends Thread {  
    public void run() {  
        for (int i = 1; i <= 5; i++) {  
            System.out.println("Child Thread i = " + i);  
        }  
        System.out.println("Exiting from MyThread");  
    }  
}  
  
class DemoJoin {  
    public static void main(String[] args) throws InterruptedException {  
        MyThread t1 = new MyThread();  
  
        t1.start();  
        t1.join();  // main thread waits for t1 to finish  
  
        for (int i = 1; i <= 5; i++) {  
            System.out.println("Main Thread i = " + i);  
        }  
    }  
}

```
---
## (v) `sleep()`

- It is used to pause execution of a thread for a specified time.
- Time is given in milliseconds.
### Example:

```java
class MyThread extends Thread {  
    public void run() {  
        try {  
            for (int i = 1; i <= 5; i++) {  
                Thread.sleep(2000); // 2 seconds  
                System.out.println(i);  
            }  
        } catch (Exception e) {  
            System.out.println(e);  
        }  
    }  
}  
  
class DemoSleep {  
    public static void main(String[] args) {  
        MyThread t1 = new MyThread();  
        t1.start();  
    }  
}
```
## Thread Lifecycle in Java

A thread in Java goes through different **states** during its execution.
#### Main Thread States

##### 1. 🆕 NEW
- Thread is created but not started yet.
- Example:

Thread t = new Thread();

---
##### 2. ▶️ RUNNABLE

- Thread is ready to run.
- After calling `start()`, it enters this state.

t.start();

---
##### 3.  RUNNING

- Thread is actually executing.
- CPU is allocated to this thread.
---
##### 4. ⏸️ BLOCKED / WAITING / TIMED WAITING
Thread is temporarily inactive.
##### 🔹 BLOCKED
- Waiting to acquire a lock.
##### 🔹 WAITING
- Waiting indefinitely (e.g., `join()`, `wait()`)
##### 🔹 TIMED WAITING
- Waiting for a specific time (`sleep(ms)`)

Thread.sleep(1000);   // TIMED WAITING  
t.join();             // WAITING

---
##### 5. TERMINATED (DEAD)
- Thread has finished execution.
- Cannot be restarted.

![image](![https://github.com/rishav-026/JAVA-NOTES/blob/main/Pasted%20image%2020260423110953.png])
