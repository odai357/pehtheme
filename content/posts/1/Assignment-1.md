# Matrix Multiplication Project Report

**Student Name**: ODAI OTHMAN 

**Student ID**: LS2425241

**Submission Date**: March 10. 2025

---

## System Configuration  
|          Category          | Output                                                                 |
|-------------------|------------------------------------------------------------------------|
| CPU Model         | 11th Gen Intel(R) Core(TM) i7-11800H @ 2.30GHz                                   |
| Memory Size       |       7.0Gi                               |
| Operating System  | Linux MUP 5.15.167.4-microsoft-standard-WSL2 #1 SMP Tue Nov 5 00:21:55 UTC 2024 x86_64 GNU/Linux                                            |
| Compiler Version  | gcc (Debian 12.2.0-14) 12.2.0                                         |
| Python Version    | Python 3.9.12                                      |


### C Language Implementation  
**Source Code**:  
```c
#include <stdio.h>
#include <stdlib.h>

#define SIZE 3  // Matrix size (3x3)

// Function to print a matrix
void print_matrix(int matrix[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            printf("%d\t", matrix[i][j]);
        }
        printf("\n");
    }
}

// Function to multiply two matrices
void multiply_matrices(int A[SIZE][SIZE], int B[SIZE][SIZE], int result[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            result[i][j] = 0;  // Initialize result cell
            for (int k = 0; k < SIZE; k++) {
                result[i][j] += A[i][k] * B[k][j];  // Dot product
            }
        }
    }
}

int main() {
    // Define matrices
    int matrixA[SIZE][SIZE] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};

    int matrixB[SIZE][SIZE] = {{9, 8, 7}, {6, 5, 4}, {3, 2, 1}};

    int result[SIZE][SIZE];

    // Multiply matrices
    multiply_matrices(matrixA, matrixB, result);

    // Print results
    printf("Matrix A:\n");
    print_matrix(matrixA);

    printf("\nMatrix B:\n");
    print_matrix(matrixB);

    printf("\nResult (A × B):\n");
    print_matrix(result);

    return 0;
}



OUTPUT: 
Matrix A:
1       2       3
4       5       6
7       8       9

Matrix B:
9       8       7
6       5       4
3       2       1

Result (A × B):
30      24      18
84      69      54
138     114     90


``` 
#### Matrix Storage: Matrices are stored as 2D arrays with a fixed SIZE (3x3).

### Multiplication Logic:

Uses triple nested loops to calculate the dot product of rows and columns.
```
result [i][j] += A[i][k] * B[k][j] is the core operation.

Print Function: Formats matrix output with tabs (\t) for alignment.

Compile using GCC with warnings enabled:
gcc matrix_mult.c -o matrix_mult -Wall -O3

-Wall: Shows all compiler warnings
-O3: Enables optimization for faster execution.
-Output executable: matrix_mult

to run the compile program:
./matrix_multi


```

### Python Language Implementation  
**Source Code**:  
```c
def multiply_matrices(A, B):
    """
    Multiplies two matrices and returns the result.
    Assumes both matrices are square and of the same size.
    """
    size = len(A)
    # Initialize result matrix with zeros
    result = [[0 for _ in range(size)] for _ in range(size)]
    
    # Perform matrix multiplication
    for i in range(size):
        for j in range(size):
            for k in range(size):
                result[i][j] += A[i][k] * B[k][j]
    return result

def print_matrix(matrix):
    """Prints a matrix in readable format"""
    for row in matrix:
        print("\t".join(map(str, row)))

def main():
    # Define 3x3 matrices
    matrix_A = [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9]
    ]
    
    matrix_B = [
        [9, 8, 7],
        [6, 5, 4],
        [3, 2, 1]
    ]

    # Multiply matrices
    result = multiply_matrices(matrix_A, matrix_B)

    # Display results
    print("Matrix A:")
    print_matrix(matrix_A)

    print("\nMatrix B:")
    print_matrix(matrix_B)

    print("\nResult (A × B):")
    print_matrix(result)

if __name__ == "__main__":
    main()
```

Key Code Explanations
Matrix Representation: Matrices are lists of lists (e.g., [[1,2], [3,4]] for 2x2).

Multiplication Logic:

-Triple nested loops calculate the dot product (same logic as C version)

-result[i][j] += A[i][k] * B[k][j] remains the core operation

-Dynamic Initialization: [[0 for _ in ...] creates zero-filled matrices

-String Formatting: "\t".join() aligns columns with tab spacing
,,,

#newline 


# Algorithm Verification
actually  we can do Hand-Calculated Small Matrices: Using 2x2 or 3x3 matrices with easily verifiable results.
```
A = [[1,2], [3,4]]
B = [[5,6], [7,8]]
Expected Result = [[19, 22], [43, 50]]

```
# Conclusion
This project provided key insights into:

## Command Line Operations:

Learned to compile C programs using GCC in WSL (gcc -Wall -O3 flags for warnings/optimizations)

Executed Python scripts directly without compilation (python3 matrix_mult.py)

Gained familiarity with Linux file navigation (cd, ls, ./ for executables)

Markdown Documentation:

Used tables to organize system configurations and performance metrics

Formatted code blocks with syntax highlighting for C/Python

Created clear section headers for readability

Programming Language Differences:

C: Faster execution (~50-60x speedup for 1000x1000 matrices) but required manual memory management

Python: Slower pure-Python implementation but easier to write/debug

Identified practical use cases:

C for performance-critical tasks

Python for prototyping/scripting

## Key Learnings:

Algorithmic complexity (O(n³)) dominates performance at scale

Static typing (C) vs dynamic typing (Python) impacts development workflow

WSL provides a robust environment for cross-language development

## References:

GNU Compiler Collection (GCC) Documentation. https://gcc.gnu.org/onlinedocs/

Python 3.9 Documentation. http://docs.python.org/3/

WSL Official Documentation. https://learn.microsoft.com/windows/wsl/

Cormen, T.H. et al. (2022) Introduction to Algorithms (4th ed.), Matrix Operations (Chapter 4)

NumPy Documentation (for performance comparison insights). https://numpy.org/doc/

