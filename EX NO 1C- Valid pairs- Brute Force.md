
# EX 1C Valid Pairs using Brute Force Approach
## DATE: 13/08/2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.

## Algorithm
1. **Start**

2. **Input**
   - Read integer `n` (size of array).
   - Read `n` integers into array `nums`.
   - Read integer `k`.

3. **Initialize**
   - Set `count = 0`.

4. **Compare Pairs**
   - For each index `i` from `0` to `n - 1`:
     - For each index `j` from `i + 1` to `n - 1`:
       - Compute `|nums[i] - nums[j]|`.
       - If the result equals `k`, increment `count` by 1.

5. **Output**
   - Print the value of `count`.

6. **Stop**   

## Program:
```
import java.util.Scanner;
public class CountPairsWithDifference {
    public static int countKDifference(int[] nums, int k) {
        
        int count = 0;
        for(int i = 0; i<nums.length;i++){
            for(int j = i + 1; j<nums.length;j++){
                if(Math.abs(nums[i]-nums[j]) == k){
                    count++;
                }
            }
        }
        return count;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }
        int k = sc.nextInt();
        int result = countKDifference(nums, k);
        System.out.println(result);
        sc.close();
    }
}

Developed by: MANOJ M V
Register Number: 212222220023 

```

## Output:
<img width="1319" height="453" alt="image" src="https://github.com/user-attachments/assets/e09dd3b3-19cb-4599-9e6b-3b3905bf8baa" />



## Result:
The program successfully implemented and the expected output is verified.
