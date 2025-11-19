
# EX 1B Power of 2
## DATE: 07/08/2025
## AIM:
To write a Java program to for given constraints.Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.

## Algorithm
1. **Start**

2. **Input**
   - Read an integer `n` from the user.

3. **Check for Power of Two**
   - Loop `i` from `0` to `n`:
     - Calculate `2^i` using `Math.pow(2, i)`.
     - If `n` equals `2^i`, return **true** (it *is* a power of two).

4. **If no match found in the loop**
   - Return **false** (it is *not* a power of two).

5. **Output**
   - Print the boolean result (`true` or `false`).

6. **Stop**

## Program:
```
import java.util.Scanner;

public class Solution {

    public boolean isPowerOfTwo(int n) {
        for(int i = 0; i <= n; i++){
            if(n == Math.pow(2, i)){
                return true;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();

        boolean result = sol.isPowerOfTwo(n);
        System.out.println(result);

        scanner.close();
    }
}

Developed by: MANOJ M V
Register Number: 212222220023
```

## Output:
<img width="1314" height="353" alt="image" src="https://github.com/user-attachments/assets/d7f7c2b0-6242-4901-9014-a574ba6d83a0" />



## Result:
The program successfully implemented and the expected output is verified.
