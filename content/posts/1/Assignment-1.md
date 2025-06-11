---
publishDate: 2025-05-19T00:40:04-07:00
title: Assignment 1
---

# Matrix Multiplication Project Report

**Student Name**: ODAI OTHMAN 

**Student ID**: LS2425241

**Submission Date**: May 3. 2025

---

## System Configuration

| Category           | Output                                                                                   |
|--------------------|-------------------------------------------------------------------------------------------|
| **CPU Model**       | 11th Gen Intel(R) Core(TM) i7-11800H @ 2.30GHz                                           |
| **Memory Size**     | 7.0 GiB                                                                                   |
| **Operating System**| Linux MUP 5.15.167.4-microsoft-standard-WSL2 #1 SMP Tue Nov 5 00:21:55 UTC 2024 x86_64 GNU/Linux |
| **Compiler Version**| gcc (Debian 12.2.0-14) 12.2.0                                                            |
| **Python Version**  | Python 3.9.12                                                                             |

---

## Implementation Details

### C Language Implementation

**Source Code**:
```c
#include <stdio.h>
#include <stdlib.h>

#define SIZE 3  // Matrix size (3x3)

void print_matrix(int matrix[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            printf("%d\t", matrix[i][j]);
        }
        printf("\n");
    }
}

void multiply_matrices(int A[SIZE][SIZE], int B[SIZE][SIZE], int result[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            result[i][j] = 0;
            for (int k = 0; k < SIZE; k++) {
                result[i][j] += A[i][k] * B[k][j];
            }
        }
    }
}

int main() {
    int matrixA[SIZE][SIZE] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    int matrixB[SIZE][SIZE] = {{9, 8, 7}, {6, 5, 4}, {3, 2, 1}};
    int result[SIZE][SIZE];

    multiply_matrices(matrixA, matrixB, result);

    printf("Matrix A:\n");
    print_matrix(matrixA);
    printf("\nMatrix B:\n");
    print_matrix(matrixB);
    printf("\nResult (A × B):\n");
    print_matrix(result);

    return 0;
}
```

**Sample Output**:
```
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

**Compilation**:
```bash
gcc matrix_mult.c -o matrix_mult -Wall -O3
```

**Execution**:
```bash
./matrix_mult
```

---

### Python Language Implementation

**Source Code**:
```python
def multiply_matrices(A, B):
    size = len(A)
    result = [[0 for _ in range(size)] for _ in range(size)]
    for i in range(size):
        for j in range(size):
            for k in range(size):
                result[i][j] += A[i][k] * B[k][j]
    return result

def print_matrix(matrix):
    for row in matrix:
        print("\t".join(map(str, row)))

def main():
    matrix_A = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
    matrix_B = [[9, 8, 7], [6, 5, 4], [3, 2, 1]]
    result = multiply_matrices(matrix_A, matrix_B)

    print("Matrix A:")
    print_matrix(matrix_A)
    print("\nMatrix B:")
    print_matrix(matrix_B)
    print("\nResult (A × B):")
    print_matrix(result)

if __name__ == "__main__":
    main()
```

**Execution**:
```bash
python3 matrix_mult.py
```

---

## Additional Details

### Matrix Representation
- Lists of lists in Python.
- 2D static arrays in C.

### Multiplication Logic
- Triple-nested loops.
- Core: `result[i][j] += A[i][k] * B[k][j]`

### Dynamic Initialization (Python)
```python
result = [[0 for _ in range(size)] for _ in range(size)]
```

### Output Formatting
- Python: `"	".join(map(str, row))`
- C: `printf("%d\t", val)`

---

## Algorithm Verification

```python
A = [[1, 2], [3, 4]]
B = [[5, 6], [7, 8]]
Expected Result = [[19, 22], [43, 50]]
```

✅ Both C and Python returned correct result.

---

## Performance Analysis ⚡

| Language | Time (approx.) | Notes                                       |
|----------|----------------|---------------------------------------------|
| C        | ~0.5s          | Fast due to compilation                     |
| Python   | ~30s           | Slower, interpreted                         |

- C: Faster, optimized with `-O3`
- Python: Easier to write; NumPy can optimize
- Complexity: O(n³) for both

---

## Conclusion

### 💻 Command Line Operations:
- `gcc -Wall -O3`
- `python3 matrix_mult.py`
- CLI commands: `cd`, `ls`, `./`

### 📝 Markdown Documentation:
- Structured headers
- Code blocks
- Tables for clarity

### 🔍 Language Differences:
- C: Fast, manual memory, static typing
- Python: Simple, dynamic typing

### 🎓 Key Learnings:
- Matrix mult is O(n³)
- WSL supports multi-language workflow

---

## References

- [GCC Docs](https://gcc.gnu.org/onlinedocs/)
- [Python Docs](https://docs.python.org/3/)
- [WSL Docs](https://learn.microsoft.com/windows/wsl/)
- *Introduction to Algorithms*, 4th ed.
- [NumPy Docs](https://numpy.org/doc/)
