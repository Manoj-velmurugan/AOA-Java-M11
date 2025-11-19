
# EX 1D Sorted Array using Divide and Conquer Approach.
## DATE: 20/08/2025
## AIM:
To write a Java program to for given constraints.
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

## Algorithm
1. **Start**

2. **Input**
   - Read integer `m` and then `m` sorted integers into array `nums1`.
   - Read integer `n` and then `n` sorted integers into array `nums2`.

3. **Initialize**
   - Set two pointers `p1 = 0`, `p2 = 0`.
   - Calculate `totalLen = m + n`.
   - Compute:
     - `mid1 = totalLen / 2`
     - `mid2 = (totalLen % 2 == 0) ? mid1 - 1 : mid1`

4. **Merge Until Median**
   - For each index `i` from `0` to `mid1`:
     - Select the smaller of `nums1[p1]` and `nums2[p2]`.
     - Move the pointer of the selected array.
     - When `i == mid2`, store the value in `val1`.
     - When `i == mid1`, store the value in `val2`.

5. **Compute Median**
   - If `totalLen` is even:  
     `median = (val1 + val2) / 2`
   - Else:  
     `median = val2`

6. **Output**
   - Print the median.

7. **Stop**  

## Program:
```
import java.util.Scanner;

public class Solution {
    private int p1 = 0, p2 = 0;

    private int getMin(int[] nums1, int[] nums2) {
        if (p1 < nums1.length && p2 < nums2.length) {
            return nums1[p1] < nums2[p2] ? nums1[p1++] : nums2[p2++];
        } else if (p1 < nums1.length) {
            return nums1[p1++];
        } else if (p2 < nums2.length) {
            return nums2[p2++];
        }
        return -1;
    }

    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int totalLen = nums1.length + nums2.length;
        int mid1 = totalLen / 2;
        int mid2 = totalLen % 2 == 0 ? mid1 - 1 : mid1;
        int val1 = 0, val2 = 0;

        for (int i = 0; i <= mid1; i++) {
            int val = getMin(nums1, nums2);
            if (i == mid2) val1 = val;
            if (i == mid1) val2 = val;
        }

        return totalLen % 2 == 0 ? (val1 + val2) / 2.0 : val2;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        int m = sc.nextInt();
        int[] nums1 = new int[m];
        for (int i = 0; i < m; i++) {
            nums1[i] = sc.nextInt();
        }

        int n = sc.nextInt();
        int[] nums2 = new int[n];
        for (int i = 0; i < n; i++) {
            nums2[i] = sc.nextInt();
        }

        double median = sol.findMedianSortedArrays(nums1, nums2);
        System.out.println("Median of the two sorted arrays = " + median);
        sc.close();
    }
}

Developed by: MANOJ M V
Register Number: 212222220023

```

## Output:
<img width="1304" height="493" alt="image" src="https://github.com/user-attachments/assets/8d5a6c9a-1c13-4fa7-8950-6d51645432b4" />



## Result:
The program successfully implemented and the expected output is verified.
