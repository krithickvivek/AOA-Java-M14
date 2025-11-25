
# EX 4C Coin Change Problem - Dynamic Programming
## Date:
## Aim:
To determine the minimum number of coins required to make a given amount using the available coin denominations, using a bottom-up dynamic programming approach.

## Problem Statement:
To write a Java program to for given constraints. You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money. Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1. You may assume that you have an infinite number of each kind of coin.

## Algorithm
1. Read coin denominations and the target amount from the user.  
2. Create a DP array `dp[amount + 1]` and initialize all values to `amount + 1` (a large placeholder).  
3. Set `dp[0] = 0` since 0 coins are needed to make amount 0.  
4. For each coin, update the DP table by iterating from the coin value to the target amount, computing the minimum coins needed.  
5. If `dp[amount]` is greater than `amount`, return `-1` (not possible). Otherwise return `dp[amount]`.  

## Program:
```
Program to implement coin change

Developed by: Krithick Vivekananda 
Register Number: 212223240075

import java.util.*;

public class Solution 
{
    public int coinChange(int[] coins, int amount) 
    {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1); 
        
        dp[0] = 0;
        
        for (int coin : coins)
        {
            for (int i = coin; i <= amount; i++) 
            {
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
            }
        }
        return dp[amount] > amount ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution solution = new Solution();
        String coinsLine = scanner.nextLine();
        String amountLine = scanner.nextLine();
        coinsLine = coinsLine.replaceAll("[^0-9,]", "");
        String[] coinsStr = coinsLine.split(",");
        int[] coins = new int[coinsStr.length];
        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }
        int amount = Integer.parseInt(amountLine.replaceAll("[^0-9]", ""));
        int result = solution.coinChange(coins, amount);
        System.out.println(result);
        scanner.close();
    }
}
```

## Output:
<img width="397" height="229" alt="image" src="https://github.com/user-attachments/assets/7723e99f-403e-49a8-af7f-131b339c731e" />

## Result:
The program was successfully implemented and the expected output is verified.
