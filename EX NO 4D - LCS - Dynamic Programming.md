
# EX 4D Longest Common Subsequence - Dynamic Programming
## Date:
## Aim:
To compute the length of the Longest Common Subsequence (LCS) between two strings using dynamic programming.

## Problem statement:
To write a Java program to for given constraints. Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0. A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters. For example, "ace" is a subsequence of "abcde". A common subsequence of two strings is a subsequence that is common to both strings.

**Input:** text1 = "abcde", text2 = "ace" 

**Output:** 3

**Explanation:** The longest common subsequence is "ace" and its length is 3.

**Constraints:**

1 <= text1.length, text2.length <= 1000
text1 and text2 consist of only lowercase English characters.

## Algorithm
1.Read the two input strings.  
2.Initialize a 2D DP array `dpGrid[m+1][n+1]` where `m` and `n` are lengths of the strings.  
3.Iterate through both strings; if characters match, set `dpGrid[i][j] = 1 + dpGrid[i-1][j-1]`.  
4.If characters do not match, set `dpGrid[i][j] = max(dpGrid[i-1][j], dpGrid[i][j-1])`.  
5.After filling the DP table, the value `dpGrid[m][n]` gives the LCS length.  

## Program:
```
Program to implement longest common subsequence

Developed by: Krithick Vivekananda 
Register Number: 212223240075

import java.util.Scanner;

public class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] dpGrid = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1))
                    dpGrid[i][j] = 1 + dpGrid[i - 1][j - 1];
                else
                    dpGrid[i][j] = Math.max(dpGrid[i - 1][j], dpGrid[i][j - 1]);
            }
        }

        return dpGrid[m][n];
    }


    // Main method for input and output
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String text1 = sc.nextLine().replaceAll("\"", "");
        String text2 = sc.nextLine().replaceAll("\"", "");

        int lcsLength = sol.longestCommonSubsequence(text1, text2);
        System.out.println("Length of Longest Common Subsequence: " + lcsLength);

        sc.close();
    }
}
```

## Output:
<img width="960" height="241" alt="image" src="https://github.com/user-attachments/assets/90e0909d-1239-4601-9310-f1cc78a8cd6a" />

## Result:
The program was successfully implemented and the expected output is verified.
