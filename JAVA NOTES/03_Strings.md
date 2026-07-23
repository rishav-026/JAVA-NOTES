A string is a Sequence of characters used to store texts.

```java
String name = "Rishu";
```
Strings are immutable and cannot be changed .
Java.lang.String class is used to create a string object .
The String is a class but can be used as a data type.

# Ways to Create a String

## 1️. Using String Literal 

String str = "Hello";
- Stored in **String pool**
- Saves memory
- Recommended method

String str1 ="harry"
String str2 = "harry"
 Harry is already present in the string pool , pointed by str1. When we try to create the same string object using str2 , JVM finds that string object with the value "harry " is already present so instead of creating a new object , a reference to the same object is returned. 

---
## 2️. Using new Keyword

String str = new String("Hello");
- Stored in **heap memory**
- Creates new object every time
When we create a string using "new" keyword , a new object is always created in the heap memory.
Str1->Harry
str2->Harry
harry still 2 different objects are created and they referred to 2 different reference variable i. e str1 and str2.

# Important String Methods and Definitions

**1️. length()**  
Returns the **number of characters** present in the string.

**2️.charAt(int index)**  
Returns the **character** at the specified index position.

**3️.toUpperCase()**  
Converts all characters of the string into **uppercase** letters.

**4️. toLowerCase()**  
Converts all characters of the string into **lowercase** letters.

**5️.equals(String anotherString)**  
Compares two strings and returns **true if both strings have the same content**.

**6️. equalsIgnoreCase(String anotherString)**  
Compares two strings **ignoring case differences**.

**7️. concat(String str)**  
Joins one string to the **end of another string**.

**8️. substring(int beginIndex)**  
Returns a **portion of the string** starting from the specified index.

**9️. substring(int beginIndex, int endIndex)**  
Returns a **portion of the string** between the specified beginning and ending indexes.

**10. contains(CharSequence s)**  
Checks whet.her the string **contains the specified sequence of characters**.

**1️1. replace(char oldChar, char newChar)**  
Replaces all occurrences of a **specified character** with a new character.

**1️2. trim()**  
Removes **leading and trailing spaces** from the string.

**1️3. isEmpty()**  
Checks whether the string is **empty (length is zero)**.

**1️4. indexOf(String str)**  
Returns the **index of the first occurrence** of the specified substring.

**1️5. lastIndexOf(String str)**  
Returns the **index of the last occurrence** of the specified substring.

**1️6. startsWith(String prefix)**  
Checks whether the string **begins with the specified prefix**.

**17. endsWith(String suffix)**  
Checks whether the string **ends with the specified suffix**.

**18. compareTo(String anotherString)**  
Compares two strings **lexicographically** (based on dictionary order).

**19. valueOf(dataType value)**  
Converts different data types into their **string representation**.

**2️0. split(String regex)**  
Splits the string into an **array of substrings** based on a given pattern.


### String vs String Buffer vs String Builder

**StringBuilder:**  
**StringBuilder** is a **mutable class in Java used to create and modify strings without creating new objects, mainly used in single-threaded programs.**

**StringBuffer:**  
**StringBuffer** is a **mutable and thread-safe class in Java used to create and modify strings safely in multi-threaded programs.**
###### Difference Between String, StringBuilder, and StringBuffer

| Feature         | String             | StringBuilder        | StringBuffer         |
| --------------- | ------------------ | -------------------- | -------------------- |
| Mutability      | Immutable          | Mutable              | Mutable              |
| Speed           | Slow               | Fast                 | Medium               |
| Thread-Safe     | Yes                | No                   | Yes                  |
| Memory Usage    | More               | Less                 | Less                 |
| Modification    | Creates new object | Modifies same object | Modifies same object |
| Synchronization | Not needed         | No                   | Yes                  |
**Why Do We Need StringBuffer and StringBuilder?**

Ans. We need **StringBuffer** and **StringBuilder** because **String objects are immutable** (cannot be changed).  
When we modify a String many times, it creates **many new objects**, which wastes **memory and time**.
**StringBuffer** and **StringBuilder** solve this problem because they are **mutable** (can change without creating new objects).

## Common Methods of StringBuffer and StringBuilder

**1️. append()**  
Adds data to the **end** of the string.

**2️. insert()**  
Inserts data at a **specified position** in the string.

**3️. replace()**  
Replaces characters between **specified indexes** with new characters.

**4️. delete()**  
Removes characters between **specified indexes**.

**5️. deleteCharAt()**  
Removes the character at a **specific index**.

**6️. reverse()**  
Reverses the characters in the string.

**7️. length()**  
Returns the **number of characters** in the string.

**8️. capacity()**  
Returns the **current storage capacity** of the object.

**9️. ensureCapacity()**  
Increases the **capacity** of the buffer if needed.

**10 charAt()**  
Returns the character at the **specified index**.

**1️1. setCharAt()**  
Changes the character at a **specified index**.

**12. substring()**  
Returns a **portion of the string**.

**13. toString()**  
Converts the buffer content into a **String object**.

**14. indexOf()**  
Returns the **index of first occurrence** of specified substring.

**15. lastIndexOf()**  
Returns the **index of last occurrence** of specified substring.

#### **Difference between String , String builder and String buffer**

| Feature         | String             | StringBuilder | StringBuffer        |
| --------------- | ------------------ | ------------- | ------------------- |
| Mutability      | Immutable          | Mutable       | Mutable             |
| Thread-safe     | Yes                | No            | Yes                 |
| Performance     | Slow (for changes) | Fastest       | Slower than Builder |
| Memory usage    | More               | Less          | Less                |
| Synchronization | No                 | No            | Yes                 |
| Introduced in   | Java 1.0           | Java 1.5      | Java 1.0            |
