# EX 4B Frog Jump - Dynamic Programming.
## Date:
## Aim:
To compute the number of distinct ways a frog can reach the top of a staircase where it can jump either 1 step or 2 steps at a time.

## Problem Statement:
To write a Java program to for given constraints. A Frog Jump 1 or 2 steps at a time. A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

**Input Format:**

A single integer n (1 ≤ n ≤ 45) – number of steps.

**Output Format:**

A single integer – number of distinct ways to reach step n.

## Algorithm
1. Read input `n` representing the number of steps.
2. If `n == 1`, return `1`; if `n == 2`, return `2`.
3. Create a DP array `dp` of size `n+1` and initialize `dp[1] = 1`, `dp[2] = 2`.
4. For each step from `3` to `n`, compute `dp[i] = dp[i-1] + dp[i-2]`.
5. Return `dp[n]` which represents total ways to reach step `n`.

## Program:
```
Program to implement frog jump

Developed by: Krithick Vivekananda 
Register Number: 212223240075

import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
       
        int n = scanner.nextInt();
        scanner.close();

        System.out.println(countWays(n));
    }

   
    public static int countWays(int n) {
        if (n == 1) return 1;
        if (n == 2) return 2;

        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;

        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }

        return dp[n];
    }
}
```

## Output:
<img width="468" height="187" alt="image" src="https://github.com/user-attachments/assets/8b445242-fb48-479a-922f-4d41c1bf4009" />

## Result:
The program was successfully implemented and the expected output is verified.
