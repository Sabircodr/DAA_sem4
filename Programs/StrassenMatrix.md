## Program 8: Perform Matrix Multiplication Using Strassen's Formula

### Description
This program demonstrates matrix multiplication using Strassen's formula. It prompts the user to enter the elements of two 2x2 matrices, computes the product matrix using Strassen's algorithm, and then displays the result. Strassen's formula optimizes matrix multiplication by reducing the number of multiplications from 8 to 7. The algorithm calculates 7 intermediary matrices (m1 to m7) based on the input matrices and then computes the resulting matrix `c` using these intermediaries.

### Code
```c
// Write a program in C to perform matrix multiplication using Strassen's
// formula
#include <stdio.h>

int main() {
  int a[2][2], b[2][2], c[2][2], i, j;
  int m1, m2, m3, m4, m5, m6, m7;

  printf("Enter the 4 elements of first matrix:\n");
  for (i = 0; i < 2; i++)
    for (j = 0; j < 2; j++)
      scanf("%d", &a[i][j]);

  printf("Enter the 4 elements of second matrix:\n");
  for (i = 0; i < 2; i++)
    for (j = 0; j < 2; j++)
      scanf("%d", &b[i][j]);

  printf("\nThe first matrix is:\n");
  for (i = 0; i < 2; i++) {
    for (j = 0; j < 2; j++)
      printf("%d\t", a[i][j]);
    printf("\n");
  }

  printf("\nThe second matrix is:\n");
  for (i = 0; i < 2; i++) {
    for (j = 0; j < 2; j++)
      printf("%d\t", b[i][j]);
    printf("\n");
  }

  m1 = (a[0][0] + a[1][1]) * (b[0][0] + b[1][1]);
  m2 = (a[1][0] + a[1][1]) * b[0][0];
  m3 = a[0][0] * (b[0][1] - b[1][1]);
  m4 = a[1][1] * (b[1][0] - b[0][0]);
  m5 = (a[0][0] + a[0][1]) * b[1][1];
  m6 = (a[1][0] - a[0][0]) * (b[0][0] + b[0][1]);
  m7 = (a[0][1] - a[1][1]) * (b[1][0] + b[1][1]);

  c[0][0] = m1 + m4 - m5 + m7;
  c[0][1] = m3 + m5;
  c[1][0] = m2 + m4;
  c[1][1] = m1 - m2 + m3 + m6;

  printf("\nAfter multiplication: \n");
  for (i = 0; i < 2; i++) {
    for (j = 0; j < 2; j++)
      printf("%d\t", c[i][j]);
    printf("\n");
  }

  return 0;
}
```

### Output
```
Enter the 4 elements of the first matrix:
7 4
9 5
Enter the 4 elements of the second matrix:
5 3
7 9

The first matrix is:
7   4
9   5

The second matrix is:
5   3
7   9

After multiplication: 
63  57
80  72
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/StrassenMatrix).
