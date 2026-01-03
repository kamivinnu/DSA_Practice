# Fibonacci Using Dynamic Programming in Java
## Top-Down (Memoization) and Bottom-Up (Tabulation)

---

## Problem Statement
Find the **n-th Fibonacci number** using **Dynamic Programming**.

---

## Fibonacci Definition
```

F(0) = 0
F(1) = 1
F(n) = F(n − 1) + F(n − 2), for n ≥ 2

```

---

# 1️⃣ Top-Down Dynamic Programming (Memoization)

## Concept
- Uses **recursion**
- Stores results of subproblems
- Avoids repeated computation
- Solves problem from **n → base cases**

---

## Algorithm (Top-Down)
1. Create a DP array `dp[]` of size `n + 1`
2. Initialize all values of `dp[]` with `-1`
3. If `n <= 1`, return `n`
4. If `dp[n] != -1`, return `dp[n]`
5. Otherwise compute:
```

dp[n] = fib(n - 1) + fib(n - 2)

````
6. Return `dp[n]`

---

## Java Code – Top-Down (Memoization)

```java
import java.util.Scanner;

public class FibonacciTopDown {

 static int[] dp;

 public static int fibonacci(int n) {

     // Base cases
     if (n <= 1)
         return n;

     // Return if already computed
     if (dp[n] != -1)
         return dp[n];

     // Compute and store
     dp[n] = fibonacci(n - 1) + fibonacci(n - 2);
     return dp[n];
 }

 public static void main(String[] args) {
     Scanner sc = new Scanner(System.in);

     System.out.print("Enter n: ");
     int n = sc.nextInt();

     // Initialize DP array
     dp = new int[n + 1];
     for (int i = 0; i <= n; i++) {
         dp[i] = -1;
     }

     System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
     sc.close();
 }
}
````

---

## Complexity (Top-Down)

| Aspect | Complexity                            |
| ------ | ------------------------------------- |
| Time   | **O(n)**                              |
| Space  | **O(n)** (DP array + recursion stack) |

---

# 2️⃣ Bottom-Up Dynamic Programming (Tabulation)

## Concept

* Uses **iteration**
* Solves smaller subproblems first
* Builds solution from **base cases → n**
* No recursion (no stack overhead)

---

## Algorithm (Bottom-Up)

1. Create a DP array `dp[]` of size `n + 1`
2. Initialize:

   ```
   dp[0] = 0
   dp[1] = 1
   ```
3. For `i = 2` to `n`, compute:

   ```
   dp[i] = dp[i - 1] + dp[i - 2]
   ```
4. Return `dp[n]`

---

## Java Code – Bottom-Up (Tabulation)

```java
import java.util.Scanner;

public class FibonacciBottomUp {

    public static int fibonacci(int n) {

        if (n <= 1)
            return n;

        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;

        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        return dp[n];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter n: ");
        int n = sc.nextInt();

        System.out.println("Fibonacci(" + n + ") = " + fibonacci(n));
        sc.close();
    }
}
```

---

## Complexity (Bottom-Up)

| Aspect | Complexity |
| ------ | ---------- |
| Time   | **O(n)**   |
| Space  | **O(n)**   |

---

## 🔁 Comparison: Top-Down vs Bottom-Up

| Feature                | Top-Down (Memoization) | Bottom-Up (Tabulation) |
| ---------------------- | ---------------------- | ---------------------- |
| Technique              | Recursive              | Iterative              |
| DP Direction           | Top → Base             | Base → Top             |
| Stack Usage            | Yes                    | No                     |
| Ease of Understanding  | High                   | Medium                 |
| Risk of Stack Overflow | Possible               | None                   |

---

## Exam Note

Dynamic Programming is applicable when a problem has:

* **Overlapping subproblems**
* **Optimal substructure**

The Fibonacci problem is a classic example demonstrating both.

---

## File Name

**Fibonacci_DP.md**

---

## Keywords

Dynamic Programming, Memoization, Tabulation, Top-Down, Bottom-Up, Fibonacci Series
