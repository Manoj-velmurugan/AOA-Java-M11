
# EX 1E Integer Multiplication using Divide and Conquer Approach(Strassen’s algorithm).
## DATE: 28/08/2025
## AIM:
To write a Java program to for given constraints.
You are given two square matrices A and B of size n × n (where n is a power of 2). Your task is to compute their matrix product using Strassen’s Matrix Multiplication algorithm and return the resulting matrix.

Unlike traditional matrix multiplication which takes O(n3)O(n^3)O(n3) time, Strassen’s algorithm improves this by reducing the number of recursive multiplications from 8 to 7, achieving approximately O(n2.81)O(n^{2.81})O(n2.81) complexity.
## Algorithm
1. **Start**

2. **Input**
   - Read integer `n` (size of matrices).
   - Read matrix `A` of size `n × n`.
   - Read matrix `B` of size `n × n`.

3. **Base Case**
   - If `n == 1`, return a 1×1 matrix containing `A[0][0] * B[0][0]`.

4. **Divide Matrices**
   - Split `A` into 4 submatrices: `A11`, `A12`, `A21`, `A22`.
   - Split `B` into 4 submatrices: `B11`, `B12`, `B21`, `B22`.
   - Each submatrix is of size `(n/2) × (n/2)`.

5. **Compute Strassen’s Seven Products**
   - `M1 = (A11 + A22) × (B11 + B22)`
   - `M2 = (A21 + A22) × B11`
   - `M3 = A11 × (B12 - B22)`
   - `M4 = A22 × (B21 - B11)`
   - `M5 = (A11 + A12) × B22`
   - `M6 = (A21 - A11) × (B11 + B12)`
   - `M7 = (A12 - A22) × (B21 + B22)`

6. **Compute Result Submatrices**
   - `C11 = M1 + M4 - M5 + M7`
   - `C12 = M3 + M5`
   - `C21 = M2 + M4`
   - `C22 = M1 + M3 - M2 + M6`

7. **Combine Result**
   - Form the final matrix `C` by placing `C11, C12, C21, C22` into their respective quadrants.

8. **Output**
   - Print the resulting matrix `C`.

9. **Stop**  

## Program:
```
import java.util.Scanner;

public class StrassenMatrix {

    static int[][] add(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] + B[i][j];
        return C;
    }

    static int[][] subtract(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] - B[i][j];
        return C;
    }

    static int[][] strassen(int[][] A, int[][] B) {
        int n = A.length;
        if (n == 1) return new int[][]{{A[0][0] * B[0][0]}};

        int m = n / 2;
        int[][] A11 = new int[m][m], A12 = new int[m][m], A21 = new int[m][m], A22 = new int[m][m];
        int[][] B11 = new int[m][m], B12 = new int[m][m], B21 = new int[m][m], B22 = new int[m][m];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < m; j++) {
                A11[i][j] = A[i][j];
                A12[i][j] = A[i][j + m];
                A21[i][j] = A[i + m][j];
                A22[i][j] = A[i + m][j + m];
                B11[i][j] = B[i][j];
                B12[i][j] = B[i][j + m];
                B21[i][j] = B[i + m][j];
                B22[i][j] = B[i + m][j + m];
            }
        }

        int[][] M1 = strassen(add(A11, A22), add(B11, B22));
        int[][] M2 = strassen(add(A21, A22), B11);
        int[][] M3 = strassen(A11, subtract(B12, B22));
        int[][] M4 = strassen(A22, subtract(B21, B11));
        int[][] M5 = strassen(add(A11, A12), B22);
        int[][] M6 = strassen(subtract(A21, A11), add(B11, B12));
        int[][] M7 = strassen(subtract(A12, A22), add(B21, B22));

        int[][] C11 = add(subtract(add(M1, M4), M5), M7);
        int[][] C12 = add(M3, M5);
        int[][] C21 = add(M2, M4);
        int[][] C22 = add(subtract(add(M1, M3), M2), M6);

        int[][] C = new int[n][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < m; j++) {
                C[i][j] = C11[i][j];
                C[i][j + m] = C12[i][j];
                C[i + m][j] = C21[i][j];
                C[i + m][j + m] = C22[i][j];
            }
        }
        return C;
    }

    static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        int[][] A = new int[n][n];
        int[][] B = new int[n][n];

        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                A[i][j] = sc.nextInt();

        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                B[i][j] = sc.nextInt();

        int[][] result = strassen(A, B);

        System.out.println("Result of Strassen Matrix Multiplication:");
        printMatrix(result);
        sc.close();
    }
}

Program to implement Reverse a String
Developed by: MANOJ M V
Register Number: 212222220023 

```

## Output:
<img width="1339" height="839" alt="image" src="https://github.com/user-attachments/assets/463e47fb-2ef8-4e69-8c98-1c4bb67dc59c" />



## Result:
The program successfully implemented and the expected output is verified.
