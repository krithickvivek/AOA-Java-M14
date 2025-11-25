
# EX 4E Longest Increasing Subsequence - Dynamic Programming
## Date:
## Aim:
To write a Java program that computes the length of the Longest Increasing Subsequence (LIS) in an integer array using dynamic programming.

## Problem statement:
To write a Java program to for given constraints. Given an integer array nums, return the length of the longest strictly increasing subsequence.

**Example:**

**Input:** nums = [10,9,2,5,3,7,101,18]

**Output:** 4

**Explanation:** The longest increasing subsequence is [2,3,7,101], therefore the length is 4.

## Algorithm
1. Read `n` and the array elements from the user.
2. Create a `dp` array of size `n` and initialize all values to `1` (each element is an LIS of length 1 by itself).
3. For each element `i`, check all previous elements `j < i`; if `nums[i] > nums[j]`, update `dp[i] = max(dp[i], dp[j] + 1)`.
4. Track the maximum value in the `dp` array as the length of LIS.
5. Print the final LIS length.

## Program:
```
Program to implement longest increasing subsequence

Developed by: Krithick Vivekananda 
Register Number: 212223240075

import java.util.*;

public class LongestIncreasingSubsequence {

    public static int lengthOfLIS(int[] nums) {
        int[] dp = new int[nums.length];
        Arrays.fill(dp, 1);

        for (int i = 1; i < nums.length; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
        }

        int longest = 0;
        for (int c : dp) {
            longest = Math.max(longest, c);
        }

        return longest;
    }

public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Prompt user input
        int n = scanner.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }

        // Calculate and display the length of LIS
        int result = lengthOfLIS(nums);
        System.out.println("Length of Longest Increasing Subsequence: " + result);

        scanner.close();
    }
}
```

## Output:
<img width="1156" height="238" alt="image" src="https://github.com/user-attachments/assets/5f84ae7b-db04-406c-81da-c06d0d9583d6" />

## Result:
The program was successfully implemented and the expected output is verified.
