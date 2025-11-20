
# EX 4A Kadane's Algorithm - Dynamic Programming
## Date:
## Aim:
To Write a Java program to solve the below problem using Kadane's Algorithm. A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed). The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy. Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

**Input Format:**

First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

**Output Format:**

A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

**Constraints:**

1 <= n <= 10^6

## Algorithm:
1. **Compute non-wrapping maximum (Kadane's)**  
   Use Kadane's algorithm (`kadaneMax`) to find the maximum subarray sum for the non-wrap case.
2. **Compute minimum subarray sum (Kadane's variant)**  
   Use a modified Kadane (`kadaneMin`) to find the minimum subarray sum.
3. **Compute total sum**  
   Sum all elements of the array.
4. **Compute wraparound maximum**  
   The maximum sum that uses wraparound equals `totalSum - minKadane` (i.e., take all except the minimum contiguous subarray).
5. **Handle edge case (all negative)**  
   If `wraparoundMax` becomes `0` because all elements are negative (or minKadane == totalSum), return `maxKadane`.
6. **Final answer**  
   The result is `max(maxKadane, wraparoundMax)`. Print this integer.  

## Program:
```
Program to implement kadane's algorithm

Developed by: Krithick Vivekananda 
Register Number: 212223240075

import java.util.*;

public class SolarEnergyMaximizer {

    public static int maxCircularEnergy(int[] energy) {
        int totalSum = 0;
        int maxKadane = kadaneMax(energy);  // Non-wrapping case
        int minKadane = kadaneMin(energy);  // Minimum subarray sum

        for (int val : energy) {
            totalSum += val;
        }

        int wraparoundMax = totalSum - minKadane;

        if (wraparoundMax == 0) // All numbers are negative
            return maxKadane;

        return Math.max(maxKadane, wraparoundMax);
    }

    private static int kadaneMax(int[] arr) {
        int maxSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.max(arr[i], current + arr[i]);
            maxSoFar = Math.max(maxSoFar, current);
        }
        return maxSoFar;
    }

    private static int kadaneMin(int[] arr) {
        int minSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.min(arr[i], current + arr[i]);
            minSoFar = Math.min(minSoFar, current);
        }
        return minSoFar;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
    }
}
```

## Output:
<img width="485" height="233" alt="image" src="https://github.com/user-attachments/assets/b2150b60-899a-4278-98a0-6f8fddc6db69" />

## Result:
The program was successfully Implemented and the output is verified. 
