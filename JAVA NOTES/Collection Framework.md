![image|60](https://github.com/rishav-026/JAVA-NOTES/blob/main/Pasted%20image%2020260423112941.png)

-The **Java Collection Framework (JCF)** is a set of **classes and interfaces** used to store and manipulate groups of objects efficiently.
- Operations performed : Insertion , Deletion , Sorting , Searching
- It provides many interfaces and classes
- It provides **ready-made data structures** like: Lists , Queues , sets , map , 
Collection framework extends iterable Interface.

Declaration : 
```java
interface Collection <E> // E specifies the type of object that collection will hold.
```
### 1.List Interface
- A **List** is an **ordered collection** that allows duplicates.
- It allows Ordered elements, index-based access , insertion order.

Collection (Interface)
        ↓
       List (Interface)
        ↓
 ┌──────────────┬──────────────┬──────────────┐
 ArrayList     LinkedList              Vector              
                                      ↓
                                    Stack

#### a. ArrayList
- `ArrayList` uses a **dynamic array** to store elements.
- It extends Abstract list class and implements the list interface.
- Features: Fast Access , Allow duplicates , Maintains Order.
**ArrayList methods:**  
add(), add(int index, E element), get(int index), set(int index, E element), remove(int index), remove(Object o), size(), isEmpty(), contains(Object o), indexOf(Object o), lastIndexOf(Object o), clear(), toArray(), clone(), ensureCapacity(int minCapacity), trimToSize().

```java
import java.util.*;

public class ArrayListDemo {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Java");
        list.add("Python");
        list.add("C++");
        list.add("Java");
        System.out.println("After add(): " + list);
        list.add(1, "JavaScript");
        System.out.println("After add(index, element): " + list);
        System.out.println("Element at index 2: " + list.get(2));
        list.set(0, "HTML");
        System.out.println("After set(): " + list);
        list.remove(3);
        System.out.println("After remove(index): " + list);
        list.remove("Java");
        System.out.println("After remove(object): " + list);
        System.out.println("Size of list: " + list.size());
        System.out.println("Contains Python? " + list.contains("Python"));
        System.out.println("Index of Python: " + list.indexOf("Python"));
        System.out.println("Is list empty? " + list.isEmpty());
        System.out.println("\nUsing for loop:");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
        System.out.println("\nUsing for-each loop:");
        for (String item : list) {
            System.out.println(item);
        }
        list.clear();
        System.out.println("\nAfter clear(): " + list);
        System.out.println("Is list empty now? " + list.isEmpty());
    }
}
```

#### b. Linked list
- Linked list stores its elements as nodes in double linked list.
- It extends AbstractSequential List.
- It implements List , deque , Queue interface.
**LinkedList methods:**  
add(), add(int index, E element), addFirst(E e), addLast(E e), get(int index), getFirst(), getLast(), set(int index, E element), remove(), remove(int index), remove(Object o), removeFirst(), removeLast(), size(), isEmpty(), contains(Object o), indexOf(Object o), lastIndexOf(Object o), clear(), peek(), peekFirst(), peekLast(), poll(), pollFirst(), pollLast(), offer(E e), offerFirst(E e), offerLast(E e), push(E e), pop().

```java
import java.util.*;

public class LinkedListDemo {

    public static void main(String[] args) {

        LinkedList<String> list = new LinkedList<>();

        list.add("Java");
        list.add("Python");
        list.add("C++");
        list.add("Java");
        System.out.println("After add(): " + list);
        list.addFirst("HTML");
        list.addLast("JavaScript");
        System.out.println("After addFirst() and addLast(): " + list);
        list.add(2, "CSS");
        System.out.println("After add(index, element): " + list);
        System.out.println("Element at index 3: " + list.get(3));
        System.out.println("First element: " + list.getFirst());
        System.out.println("Last element: " + list.getLast());
        list.set(1, "Bootstrap");
        System.out.println("After set(): " + list);
        list.remove(2);
        System.out.println("After remove(index): " + list);
        list.remove("Java");
        System.out.println("After remove(object): " + list);
        list.removeFirst();
        list.removeLast();
        System.out.println("After removeFirst() and removeLast(): " + list);
        System.out.println("Size of list: " + list.size());
        System.out.println("Contains Python? " + list.contains("Python"));
        System.out.println("Index of Python: " + list.indexOf("Python"));
        System.out.println("Is list empty? " + list.isEmpty());
       System.out.println("\nUsing for loop:");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
        System.out.println("\nUsing for-each loop:");
        for (String item : list) {
            System.out.println(item);
        }
        list.clear();
        System.out.println("\nAfter clear(): " + list);
        System.out.println("Is list empty now? " + list.isEmpty());
    }
}
```

##### - NOTE:  Linked list for frequent insertion and deletion.
        Array list for fast access and better memory efficiency.

# 2.Queue Interface
**Queue** is a collection that follows the **FIFO (First In First Out)** principle, meaning the element inserted first is removed first.
**Queue methods :**  
add(E e), offer(E e), remove(), poll(), element(), peek(), size(), isEmpty(), contains(Object o), clear().

```java
import java.util.*;
public class QueueDemo {
    public static void main(String[] args) {
        Queue<String> q = new LinkedList<>();
        q.add("A");
        q.add("B");
        q.offer("C");
        System.out.println("Queue: " + q);
        System.out.println("Peek: " + q.peek());
        System.out.println("Element: " + q.element());
        q.remove();
        System.out.println("After remove(): " + q);
        q.poll();
        System.out.println("After poll(): " + q);
        System.out.println("Size: " + q.size());
        System.out.println("Is Empty: " + q.isEmpty());
        q.clear();
        System.out.println("After clear(): " + q);
    }
}
```

# a.PriorityQueue Class

**PriorityQueue** is a type of Queue where elements are processed based on **priority**, not insertion order.
**PriorityQueue methods :**  
add(E e), offer(E e), remove(), poll(), element(), peek(), size(), isEmpty(), contains(Object o), clear(), comparator().

```java
import java.util.*;
public class PriorityQueueDemo {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        pq.add(30);
        pq.add(10);
        pq.offer(20);
        pq.add(5);
        System.out.println("PriorityQueue: " + pq);
        System.out.println("Peek: " + pq.peek());
        System.out.println("Element: " + pq.element());
        pq.remove();
        System.out.println("After remove(): " + pq);
        pq.poll();
        System.out.println("After poll(): " + pq);
        System.out.println("Size: " + pq.size());
        System.out.println("Contains 20: " + pq.contains(20));
        System.out.println("Is Empty: " + pq.isEmpty());
        pq.clear();
        System.out.println("After clear(): " + pq);
    }
}
```

# b.Deque Interface

**Deque (Double Ended Queue)** is an interface that allows **insertion and deletion from both ends** (front and rear).
- Allows insertion at **front and rear**
- Allows deletion at **front and rear**
- Can work as both:
    - **Queue (FIFO)**
    - **Stack (LIFO)**
- Does **not allow null elements**
### Deque Methods
addFirst(E e), addLast(E e), offerFirst(E e), offerLast(E e), removeFirst(), removeLast(), pollFirst(), pollLast(), getFirst(), getLast(), peekFirst(), peekLast(), push(E e), pop(), size(), isEmpty(), clear().

```java
import java.util.*;
public class DequeDemo {
    public static void main(String[] args) {
        Deque<Integer> dq = new LinkedList<>();
        dq.addFirst(10);
        dq.addLast(20);
        dq.offerFirst(5);
        dq.offerLast(25);
        System.out.println("Deque: " + dq);
        System.out.println("First Element: " + dq.getFirst());
        System.out.println("Last Element: " + dq.getLast());
        dq.removeFirst();
        dq.removeLast();
        System.out.println("After removeFirst & removeLast: " + dq);
        dq.push(50);
        System.out.println("After push: " + dq);
        dq.pop();
        System.out.println("After pop: " + dq);
        System.out.println("Peek First: " + dq.peekFirst());
        System.out.println("Peek Last: " + dq.peekLast());
        System.out.println("Size: " + dq.size());
        dq.clear();
        System.out.println("After clear: " + dq);
    }
}
```
# c. ArrayDeque Class

**ArrayDeque** is a class that implements the **Deque interface** using a **resizable array**.
- Faster than **Stack** and **LinkedList**
- No capacity restrictions
- Does **not allow null values**
- Can be used as:
    - Queue
    - Stack
    - Deque
### ArrayDeque Methods :
add(E e), addFirst(E e), addLast(E e), offer(E e), offerFirst(E e), offerLast(E e), remove(), removeFirst(), removeLast(), poll(), pollFirst(), pollLast(), getFirst(), getLast(), peek(), peekFirst(), peekLast(), push(E e), pop(), size(), isEmpty(), clear().

```java
import java.util.*;
public class ArrayDequeDemo {
    public static void main(String[] args) {
        ArrayDeque<String> dq = new ArrayDeque<>();
        dq.add("A");
        dq.addFirst("B");
        dq.addLast("C");
        dq.offer("D");
        System.out.println("ArrayDeque: " + dq);
        System.out.println("First Element: " + dq.getFirst());
        System.out.println("Last Element: " + dq.getLast());
        dq.removeFirst();
        dq.removeLast();
        System.out.println("After removeFirst & removeLast: " + dq);
        dq.push("X");
        System.out.println("After push: " + dq);
        dq.pop();
        System.out.println("After pop: " + dq);
        System.out.println("Peek: " + dq.peek());
        System.out.println("Size: " + dq.size());
        dq.clear();
        System.out.println("After clear: " + dq);
    }
}
```

# 3.Set Interface in Java

**Set** is an interface in the Java Collection Framework that represents a **collection of unique elements**, meaning **duplicate values are not allowed**.
- Does **not allow duplicate elements**  
 - Does **not maintain insertion order** (except some implementations)  
 - Allows **at most one null value** (depends on implementation)  
 - Uses **hashing or tree structure** internally  
 - Faster searching compared to List in many cases
 - 
Collection (Interface)
        ↓
        Set (Interface)
        ↓
 ┌──────────────┬──────────────┬
 HashSet     LinkedHashSet      TreeSet

# Types of Set Implementations

### 1️⃣ HashSet
- Stores elements using **hash table**
- **No duplicates allowed**
- **No order maintained**
- Allows **one null value**
- Fastest among Set implementations

```java
import java.util.*;
public class HashSetExample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        set.add("Java");
        set.add("Python");
        set.add("C++");
        set.add("Java");
        System.out.println("HashSet: " + set);
        System.out.println("Contains Python: " + set.contains("Python"));
        set.remove("C++");
        System.out.println("After remove: " + set);
        System.out.println("Size: " + set.size());
        System.out.println("Is Empty: " + set.isEmpty());
        set.clear();
        System.out.println("After clear: " + set);
    }
}
```
---
### 2️⃣ LinkedHashSet
- Maintains **insertion order**
- Uses **hash table + linked list**
- Slightly slower than HashSet
- Allows **one null value**
```java
import java.util.*;

public class LinkedHashSetExample {
    public static void main(String[] args) {
        LinkedHashSet<String> set = new LinkedHashSet<>();
        set.add("Java");
        set.add("Python");
        set.add("C++");
        set.add("Java");
        System.out.println("LinkedHashSet: " + set);
        System.out.println("Contains Python: " + set.contains("Python"));
        set.remove("C++");
        System.out.println("After remove: " + set);
        System.out.println("Size: " + set.size());
        System.out.println("Is Empty: " + set.isEmpty());
        set.clear();
        System.out.println("After clear: " + set);
    }
}
```

---
### 3️⃣ TreeSet
- Stores elements in **sorted order**
- Uses **Red-Black Tree**
- Does **not allow null values**
- Slower than HashSet
```java
import java.util.*;
public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> set = new TreeSet<>();
        set.add(30);
        set.add(10);
        set.add(20);
        set.add(10);
        System.out.println("TreeSet: " + set);
        System.out.println("First Element: " + set.first());
        System.out.println("Last Element: " + set.last());
        set.remove(20);
        System.out.println("After remove: " + set);
        System.out.println("Size: " + set.size());
        System.out.println("Is Empty: " + set.isEmpty());
        set.clear();
        System.out.println("After clear: " + set);
    }
}
```
### Common Set Methods
add(E e), remove(Object o), contains(Object o), size(), isEmpty(), clear(), iterator(), toArray(), addAll(Collection c), removeAll(Collection c), retainAll(Collection c).
## 4.HashMap
**HashMap** is a class in Java that stores data in **key-value pairs**, where each key is unique.

Features:
- Stores **key-value pairs**  
- Keys must be **unique**  
- Allows **one null key**  
- Allows **multiple null values**  
- Does **not maintain order**
### Common HashMap Methods
put(K key, V value), get(Object key), remove(Object key), containsKey(Object key), containsValue(Object value), size(), isEmpty(), clear(), keySet(), values(), entrySet(), replace(K key, V value).

```java
import java.util.*;
public class HashMapDemo {
    public static void main(String[] args) {
        HashMap<Integer, String> map = new HashMap<>();
        map.put(1, "Java");
        map.put(2, "Python");
        map.put(3, "C++");
        map.put(4, "JavaScript");
        System.out.println("HashMap: " + map);
        System.out.println("Value for key 2: " + map.get(2));
        System.out.println("Contains key 3: " + map.containsKey(3));
        System.out.println("Contains value Python: " + map.containsValue("Python"));
        map.remove(3);
        System.out.println("After remove key 3: " + map);
        System.out.println("Size: " + map.size());
        System.out.println("Keys: " + map.keySet());
        System.out.println("Values: " + map.values());
        System.out.println("Entries: " + map.entrySet());
        map.replace(2, "HTML");
        System.out.println("After replace: " + map);
        System.out.println("Is Empty: " + map.isEmpty());
        map.clear();
        System.out.println("After clear: " + map);
    }
}
```

# Traversing HashMap 

#### Using keySet()
```java
for (Integer key : map.keySet()) {  
    System.out.println(key + " " + map.get(key));  
}
```
---
#### Using entrySet() (Most Efficient)
```java
for (Map.Entry<Integer, String> entry : map.entrySet()) {  
    System.out.println(entry.getKey() + " " + entry.getValue());  
}
```

|Feature|HashMap|LinkedHashMap|TreeMap|
|---|---|---|---|
|Order|No order|Insertion order|Sorted order|
|Null Key|One allowed|One allowed|Not allowed|
|Speed|Fastest|Slightly slower|Slowest|
|Data Structure|Hash Table|Hash Table + List|Red-Black Tree|

## LinkedHashMap 
**LinkedHashMap** stores data in **key-value pairs** and **maintains insertion order**.

---
###  LinkedHashMap Methods
put(K key, V value), get(Object key), remove(Object key), containsKey(Object key), containsValue(Object value), size(), isEmpty(), clear(), keySet(), values(), entrySet(), replace(K key, V value).

```java
import java.util.*;  
public class LinkedHashMapDemo {  
    public static void main(String[] args) {  
        LinkedHashMap<Integer, String> map = new LinkedHashMap<>();  
        map.put(1, "Java");  
        map.put(2, "Python");  
        map.put(3, "C++");  
        map.put(4, "HTML");  
        System.out.println("LinkedHashMap: " + map);  
        System.out.println("Value for key 2: " + map.get(2));  
        System.out.println("Contains key 3: " + map.containsKey(3));  
        map.remove(3);  
        System.out.println("After remove: " + map);  
        System.out.println("Keys: " + map.keySet());  
        System.out.println("Values: " + map.values());  
        map.replace(2, "CSS");  
        System.out.println("After replace: " + map);  
        System.out.println("Size: " + map.size());  
        System.out.println("Is Empty: " + map.isEmpty());  
        map.clear();  
        System.out.println("After clear: " + map);  
    }  
}
```

---
## TreeMap
**TreeMap** stores key-value pairs in **sorted order of keys**.
###  TreeMap Methods
put(K key, V value), get(Object key), remove(Object key), containsKey(Object key), containsValue(Object value), size(), isEmpty(), clear(), firstKey(), lastKey(), keySet(), values(), entrySet(), replace(K key, V value).

```java
import java.util.*;  
public class TreeMapDemo {   
    public static void main(String[] args) {  
        TreeMap<Integer, String> map = new TreeMap<>();   
        map.put(3, "Java");  
        map.put(1, "Python");  
        map.put(4, "C++");  
        map.put(2, "HTML");  
        System.out.println("TreeMap: " + map);  
        System.out.println("Value for key 2: " + map.get(2));  
        System.out.println("First Key: " + map.firstKey());  
        System.out.println("Last Key: " + map.lastKey());  
        map.remove(3);  
        System.out.println("After remove: " + map);  
        System.out.println("Keys: " + map.keySet());  
        System.out.println("Values: " + map.values());  
        map.replace(2, "CSS");  
        System.out.println("After replace: " + map);  
        System.out.println("Size: " + map.size());  
        System.out.println("Is Empty: " + map.isEmpty()); 
        map.clear();  
        System.out.println("After clear: " + map);  
    }  
}
```

## Legacy Classes 
**Legacy classes** are the classes that were introduced in **early versions of Java (before Java 1.2)** and later became part of the **Collection Framework**.

They are called **legacy** because they existed **before the modern collection classes** like ArrayList and HashMap.
###  List of Legacy Classes
The main **legacy classes** are:
Vector  
Stack  
Hashtable  
Enumeration  
Dictionary  
Properties  
BitSet
### Important Legacy Classes

### 1.Vector
**Vector** is a dynamic array that is **synchronized (thread-safe)**.
#### Common Vector Methods 
add(), addElement(), get(), set(), remove(), removeElement(), size(), capacity(), firstElement(), lastElement(), clear(), isEmpty().

```java
import java.util.*;  
public class VectorDemo {  
    public static void main(String[] args) {  
        Vector<String> v = new Vector<>();  
        v.add("Java");  
        v.add("Python");  
        v.add("C++");  
        System.out.println("Vector: " + v);  
        System.out.println("First Element: " + v.firstElement());  
        System.out.println("Last Element: " + v.lastElement());  
        v.remove("Python");  
        System.out.println("After remove: " + v);  
        System.out.println("Size: " + v.size());  
    }  
}

```
---
## 2️. Stack
**Stack** is a subclass of Vector that follows **LIFO (Last In First Out)**.
#### Stack Methods
push(), pop(), peek(), empty(), search().

```java
import java.util.*;  
public class StackDemo {  
    public static void main(String[] args) {    
        Stack<Integer> s = new Stack<>();  
        s.push(10);  
        s.push(20);  
        s.push(30);  
        System.out.println("Stack: " + s);  
        System.out.println("Top Element: " + s.peek());  
        s.pop();  
        System.out.println("After pop: " + s);  
        System.out.println("Is Empty: " + s.empty());  
    }  
}
```

## 3️. Hashtable
**Hashtable** stores data in **key-value pairs** and is **synchronized**.
#### Hashtable Methods 
put(), get(), remove(), containsKey(), containsValue(), size(), isEmpty(), clear(), keySet(), values(), entrySet().

```java
import java.util.*;  
public class HashtableDemo {  
    public static void main(String[] args) {    
        Hashtable<Integer, String> ht = new Hashtable<>();  
        ht.put(1, "Java");  
        ht.put(2, "Python");  
        ht.put(3, "C++");  
        System.out.println("Hashtable: " + ht);  
        System.out.println("Value for key 2: " + ht.get(2));  
        ht.remove(3);  
        System.out.println("After remove: " + ht);  
        System.out.println("Size: " + ht.size());  
    }  
}

```
---

### 4️. Enumeration (Interface)
**Enumeration** is used to **traverse elements** of legacy classes like Vector and Hashtable.
#### Methods 
hasMoreElements(), nextElement().

```java
import java.util.*;  
public class EnumerationDemo {  
    public static void main(String[] args) {  
        Vector<String> v = new vector<>();  
        v.add("Java");  
        v.add("Python");  
        v.add("C++");  
        Enumeration<String> e = v.elements();  
        while (e.hasMoreElements()) {  
            System.out.println(e.nextElement());  
        }  
    }  
}
```
# Difference Between Comparable and Comparator in Java
---
###  Comparable Interface

- **Comparable** is an interface used to **sort objects in natural order**.  
- It is present in:   java.lang.Comparable
- You must **override `compareTo()` method**.
####  Method in Comparable 
compareTo(Object o)

```java
import java.util.*;  
class Student implements Comparable<Student> {  
    int id;  
    String name;  
    Student(int id, String name) {  
        this.id = id;  
        this.name = name;  
    }  
    public int compareTo(Student s) {  
        /*if (this.id < s.id)
    return -1;

else if (this.id > s.id)
    return 1;

else
    return 0;
    }  */
    return this.id - s.id;
}  
public class ComparableDemo {   
    public static void main(String[] args) {  
        ArrayList<Student> list = new ArrayList<>();  
        list.add(new Student(3, "Java"));  
        list.add(new Student(1, "Python"));  
        list.add(new Student(2, "C++"));  
        Collections.sort(list);  
        for (Student s : list) {  
            System.out.println(s.id + " " + s.name);  
        }  
    }  
}
```
---
# Comparator Interface
- **Comparator** is an interface used to **sort objects in different ways (custom order)**.
- It is present in:   java.util.Comparator
- You must **override `compare()` method**.
####  Method in Comparator 
compare(Object o1, Object o2)
```java
import java.util.*;  
class Student {  
    int id;  
    String name;  
    Student(int id, String name) {  
        this.id = id;  
        this.name = name;  
    }  
}  
class SortByName implements Comparator<Student> {  
    public int compare(Student s1, Student s2) {  
        //return s1.name.compareTo(s2.name); 
        if (s1.name comes before s2.name)  
           return -1;  
        else if (s1.name comes after s2.name)  
           return 1;  
        else  
           return 0; 
    }  
}  
public class ComparatorDemo {  
    public static void main(String[] args) {  
        ArrayList<Student> list = new ArrayList<>();  
        list.add(new Student(3, "Java"));  
        list.add(new Student(1, "Python"));  
        list.add(new Student(2, "C++"));  
        Collections.sort(list, new SortByName());  
        for (Student s : list) {  
            System.out.println(s.id + " " + s.name);  
        }  
    }  
}
```
I can create multiple comparator which is not possible with comparable.
```java
class SortById implements Comparator<Student> { }

class SortByName implements Comparator<Student> { }

class SortByMarks implements Comparator<Student> { }
```

Question:  cond -> sort in dec order of marks.  
                // if marks is same then sort in increasing order of rollNo. 
```java
import java.util.*;  
  
class Student {  
    int rollNo;  
    String name;  
    int marks;  
  
    Student(int rollNo, String name, int marks) {  
        this.rollNo = rollNo;  
        this.name = name;  
        this.marks = marks;  
    }  
}  
public class ComparatorTrickDemo {  
    public static void main(String[] args) {  
        List<Student> list = new ArrayList<>();  
        list.add(new Student(3, "Amit",50));  
        list.add(new Student(1, "Ravi",70));  
        list.add(new Student(2, "Neha",80));  
        list.add(new Student(4, "Priya",80));  
        //(first, second)  
        // dec -> second - first        //inc -> first - second        
        // Using Comparator with Anonymous Class        
        Collections.sort(list, new Comparator<Student>(){  
            @Override  
            public int compare(Student s1, Student s2){  
                if(s1.marks == s2.marks){
                    return s1.rollNo - s2.rollNo;  
                }  
               return s2.marks - s1.marks;  
            }  
        });  
        for (Student s : list) {  
            System.out.println(s.marks + " " + s.name);  
        }  
    }  
}
```

| Feature            | Comparable           | Comparator                |     |
| ------------------ | -------------------- | ------------------------- | --- |
| Package            | java.lang            | java.util                 |     |
| Method             | compareTo()          | compare()                 |     |
| Sorting Type       | Natural sorting      | Custom sorting            |     |
| Number of Sortings | One sorting possible | Multiple sorting possible |     |
| Class Modification | Required             | Not required              |     |
| Interface Location | Inside class         | Separate class            |     |

**NOTE** : Comparable is used to sort objects in natural order using compareTo() method, while Comparator is used to sort objects in custom order using compare() method.

# What is a Lambda Function in Java?
A **Lambda function** is a **short way to write anonymous functions** (functions without a name).

Instead of writing:
```java
class SortByName implements Comparator<Student> {  
    public int compare(Student s1, Student s2) {  
        return s1.name.compareTo(s2.name);  
    }  
}
```
You can write it **in one line** using a lambda.

Syntax:
```java
(parameters) -> expression
(a, b) -> a - b  //Take a and b → return a - b
```
Example:
```java
import java.util.*;
class Student {
    int id;
    String name;
    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
}
public class LambdaDemo {
    public static void main(String[] args) {
        ArrayList<Student> list = new ArrayList<>();
        list.add(new Student(3, "Java"));
        list.add(new Student(1, "Python"));
        list.add(new Student(2, "C++"));
        // Lambda sorting by name
        Collections.sort(list,
            (s1, s2) -> s1.name.compareTo(s2.name));
        for (Student s : list) {
            System.out.println(s.id + " " + s.name);
        }
    }
}
```
Multiple Fields: Sort by id then name 
```java
list.sort((s1, s2) -> {
    if (s1.id != s2.id)
        return s1.id - s2.id;
    return s1.name.compareTo(s2.name);
});
```


# Iterator in Java
**Iterator** is an interface used to **traverse (iterate) elements** of a collection one by one.
It belongs to:
import java.util.Iterator;

###  Why Iterator is Used
- To **traverse elements** of collections
- Works with **List, Set, Queue**, etc.
- Safer than loops while removing elements
- Helps access elements **one by one**

###  Iterator Methods 
hasNext(), next(), remove().

| Method      | Description                         |
| ----------- | ----------------------------------- |
| `hasNext()` | Returns true if next element exists |
| `next()`    | Returns next element                |
| `remove()`  | Removes current element             |

### Iterator Example (Using ArrayList)

```java
import java.util.*;  
  
public class IteratorDemo {  
  
    public static void main(String[] args) {  
  
        ArrayList<String> list = new ArrayList<>();  
  
        list.add("Java");  
        list.add("Python");  
        list.add("C++");  
  
        Iterator<String> it = list.iterator();  
  
        while (it.hasNext()) {  
            System.out.println(it.next());  
        }  
    }  
}
```