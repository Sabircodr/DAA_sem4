## Program: Matrix Chain Multiplication

### Description
This program implements the Matrix Chain Multiplication algorithm to find the optimal way to multiply a chain of matrices. The goal is to minimize the number of scalar multiplications needed to compute the product of multiple matrices. 

The program takes the number of matrices as input along with their dimensions and calculates the minimum number of scalar multiplications required. It also prints the sequence of matrix multiplications involved in the optimal solution. 

The algorithm works by considering all possible ways to parenthesize the sequence of matrices and computing the cost of each parenthesization. It uses dynamic programming to efficiently compute the optimal solution by breaking down the problem into smaller subproblems and storing the solutions to these subproblems in a table.

The output includes the sequence of matrix multiplications along with the minimum number of scalar multiplications needed to compute the final product.

### Code
```c
# include <stdio.h>
# include <stdlib.h>
# define sz 20
# define INF 200000

void print(unsigned long z[][sz], int i, int j) {
  if (i == j)
    printf(" A%d ",i);
  else {
    printf(" ( ");
    print(z, i, z[i][j]);
    print(z, z[i][j] + 1, j);
    printf(" ) ");
  }
}

void printm(unsigned long z[][sz], int n) {
  int i,j;
  for(i = 1; i <= n; i++) {
    for(j = 1; j <= n; j++) {
      printf("%5d", z[i][j]);
    }
    printf("\n\n");
  }
  printf("\nThe number of multiplications required is: %d", z[1][n]);
}

void Matrix_Chain_Order(int w[], int num1) {
  unsigned long x[sz][sz] = {0};
  unsigned long z[sz][sz] = {0};
  unsigned int q = 0;
  int i, j, k, l;
  int n = num1;
  for(i = 1; i <= n; i++)
    x[i][i] = 0;
  for(l = 2; l <= n; l++)
    for(i = 1; i <= (n - l + 1); i++) {
      j = i + l - 1;
      x[i][j] = INF;
      for(k = i; k <= j - 1; k++) {
        q = x[i][k] + x[k+1][j] + w[i-1] * w[k] * w[j];
        if(q < x[i][j]) {
          x[i][j] = q;
          z[i][j] = k;
        }
      }
    }
  print(z, i-1, j);
  printf("\n\n");
  printf("The Minimum Number of Multiplication Required is:\n\n");
  printm(x, n);
}

int main() {
  int i, num1 = 0, w[sz] = {0};
  printf("Enter the number of matrices: ");
  scanf("%d", &num1);
  printf("Enter the order of sequence for %d matrix Multiplication:\n", num1 + 1);
  for(i = 0; i <= num1; i++)
    scanf("%d", &w[i]);
  printf("\n\n");
  printf("MATRIX MULTIPLICATION SEQUENCE IS: ");
  printf("\n\n\t");
  Matrix_Chain_Order(w, num1);
  return 0;
}
```

### Output
```
Enter the number of matrix : 4
Enter the order of sequence for 5 matrix Multiplication :
3
4
5
3
4


MATRIX MULTIPLICATION SEQUENCE IS : 

     (  (  A1  (  A2  A3  )  )  A4  ) 

The Minimum No. of Multiplication Required is:

    0   60   96  132

    0    0   60  108

    0    0    0   60

    0    0    0    0


The No. of multiplication required is : 132 
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/MatrixChain).
