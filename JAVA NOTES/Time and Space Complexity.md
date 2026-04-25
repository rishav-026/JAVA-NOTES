
Let’s say you wrote two solutions:
- Solution A → runs in 1 second
- Solution B → runs in 10 seconds

Both give correct output.
- Which one is better?
- Obviously, Solution A.

## **Time Complexity measures:**
- How the **number of operations grows** with input size.
- Time complexity is a function that gives us the relationship between about how the time will grow as the input grows.

## **Space Complexity or Auxiliary space measures:**
- How much **extra memory** your program uses.
- Auxiliary space is the extra space or temporary space used by an algorithm.
- Space complexity of an algorithm is the total space taken by the algorithm with respect to the input size.
- Space Complexity = Auxiliary space +Space used by input.

Unit to represent complexity:
1. Big-O notation : Worst case -> Upper bound
2. Theta notation : Average case 
3. Omega notation : Best case -> lower bound 

Full Order(Best-> Worst)
O(1) < O(log n) < O(√n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)

# 1️⃣ **O(1) — Constant Time 

Execution time **does not depend on input size**.
##  Example
int x = arr[5];
## Where Used
- Array index access
- Stack push/pop
- HashMap get() (average)
---
# 2️⃣ **O(log n) — Logarithmic Time**
Input size **reduces by half** each step.

##  Example
```java
Binary Search:
while (left <= right) {  
    int mid = (left + right) / 2;  
}
or
while(n>1){
   n=n/2;
}
```
##  Where Used
- Binary Search
- TreeMap operations
- Heap operations
---
# 3️⃣ **O(√n) — Square Root Time**

Operations grow with **square root of n**.
##  Example
```java
Finding factors of a number:

for (int i = 1; i * i <= n; i++) {  
    System.out.println(i);  
}
```
##  Where Used
- Prime checking
- Factor finding
---
# 4️⃣ **O(n) — Linear Time**

Time increases **linearly** with input size.
##  Example
```java
for (int i = 0; i < n; i++) {  
    System.out.println(arr[i]);  
}
```
##  Where Used
- Traversing array
- Linear Search
---
# 5️⃣ **O(n log n) — Linearithmic Time**
Combination of **linear + logarithmic**.
##  Example Algorithms
- Merge Sort
- Heap Sort
- Quick Sort (average)

Example:
Arrays.sort(arr);
---
# 6️⃣ **O(n²) — Quadratic Time**
Time increases with **square of input**.
Usually caused by **nested loops**.
## Example
```java
for (int i = 0; i < n; i++) {  
    for (int j = 0; j < n; j++) {  
        System.out.println(i + " " + j);  
    }  
}
```
##  Where Used
- Bubble Sort
- Selection Sort
- Insertion Sort (worst)

---
# 7️⃣ **O(n³) — Cubic Time**
Three nested loops.
##  Example
```java
for (int i = 0; i < n; i++) {  
    for (int j = 0; j < n; j++) {  
        for (int k = 0; k < n; k++) {  
            System.out.println(i + j + k);  
        }  
    }  
}
```
##  Where Used
- Matrix multiplication
- Floyd–Warshall algorithm

---
# 8️⃣ **O(2ⁿ) — Exponential Time**
Time **doubles** with every extra input.
Very slow ⚠️
##  Example
```java
Recursive Fibonacci:
int fib(int n) {  
    if (n <= 1)  
        return n;  
  
    return fib(n - 1) + fib(n - 2);  
}
```
##  Where Used
- Backtracking
- Subset problems

---
# 9️⃣ **O(n!) — Factorial Time**
Extremely slow — grows **factorially**.
##  Example
Generating all permutations:
n! permutations
##  Where Used
- Traveling Salesman Problem
- Permutation generation

---
# 🔟 **O(nⁿ) — Power of n Time (Extreme Worst Case)**
Worst theoretical growth.
Very rare in real algorithms.
##  Example Idea
n choices at each of n steps  
Total possibilities = nⁿ

Used in:
- Some brute-force recursive problems
- Highly inefficient algorithms

Some Questions :
1.
```java
for (int i = 0; i < 2*n; i++) {
    System.out.println(i);
} //O(2n)= O(n)
```
2.
```java
for (i = 0; i < n; i++)
    for (j = 0; j < n; j++) 
    //O(n+n)= O(n)
```
3.
```java
for(int i = 1 ; i< n ; i *=2) //O(log n)
//or 
for(int i = 1 ; i<n ; i++){
    for(int j = 1 ; j< n ; j=j*2){
    }//O(n log n)
}
```
4.
```java
for (int i =0 ; i<n/2 ; i++){
   System.out.println(i); //O(n/2)= O(n)
}
```
5.
```java
for(int i = 0 ; i<n ; i+=2) //O(n/2)= O(n)
```
6. 
```java
   for(int i =1 ; i<n ; i*=2)
   //(n/2^k =1)=(n = 2^k) =(log n =k) = O(k) =O(log n)
```

7.
```java
for( int i = 0 ; i<n ; i++){
    if(arr[i]==target) return i;
    //Best case = O(1)
    //Worst case = O(n)
}
```

8 . 
```java
for (i = 1; i < n; i++){
     for (j = 1; j < n^2; j++){
     } 
}
// n(n+1)(2n+1) = n^3 +n^2 +n^1... = O(n^3)
```
9 .
```java
for (i = 0; i < n; i++){
     for (j = 0; j <i; j++){
     } //O((n*(n-1))/2)= O(n^2)
}
```
10 . 
```java
for (i = 0; i >0; i/=2) // O(log n)
```
11.
```java
int [] arr = new int [n];// O(n)
```
12.
```java
for (i = 0; i < n; i++){
     for (j = 0; j <i; j++){
        for( int k =0 ; k<j ;k++){
        System.out.println(i+j+k);// n*(n-1)*(n-2)=O(n^3)
            }
     } 
}
```
13 . 
```java
int i =0;
while(i<n){
  i+=2; //O(n/2)= O(n)
}
```
14.
```java
int i =1;
while(i<n){
  i*=2; //O(log n)
}
```
15 .
```java
for( int i=0 ; i< n ;i++){
   i++; //O(n/2)
}
```
16.
```java
for( int i=0 ; i< n ;i++){
   for(int j =0 ;j<Math.sqrt(n);j++){
      Sop(i+j);//n*root(n) = O(n root n)
   }
}
```
17.
```java
for( int i=0 ; i< n ;i++){
    if(i%2==0){
       sop(i); //O(n)
    }
}
```

 Space Complexity:
1.
```java
int a = 10;// O(1)
``` 
2.
```java
int [] arr = new int [n];// O(n)
```
3.
```java
int [][] matrix = new int[n][n];//O(n^2)
```
4.
```java
int sum = 0 //O(1)
```
5.
```java
int []a = new int [n];
int []b = new int [n];//O(n^n)
```
6.
```java
int [][] grid = new int [n][m] //O(n*m)
```