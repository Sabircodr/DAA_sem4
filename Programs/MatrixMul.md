## Program 7: Perform Matrix Multiplication

### Description
This program implements the standard method to perform matrix multiplication. It prompts the user to enter the dimensions and elements of two matrices, checks if multiplication is possible by ensuring the number of columns of the first matrix matches the number of rows of the second matrix, and then computes the product matrix. The algorithm iterates over each element of the resulting matrix, calculating the sum of products of corresponding elements from the row of the first matrix and the column of the second matrix. Finally, it displays the resulting product matrix.

### Code
```c
//Write a program in C to perform normal matrix multiplication.
#include <stdio.h>

int main() {
    int m, n, p, q, c, d, k, sum = 0;

    printf("Enter the number of rows and columns of the first matrix\n");
    scanf("%d%d", &m, &n);

    int first[m][n];

    printf("Enter the elements of the first matrix\n");

    for (c = 0; c < m; c++)
        for (d = 0; d < n; d++)
            scanf("%d", &first[c][d]);

    printf("Enter the number of rows and columns of the second matrix\n");
    scanf("%d%d", &p, &q);

    if (n != p)
        printf("The matrices can't be multiplied with each other.\n");
    else {
        int second[p][q], multiply[m][q];

        printf("Enter the elements of the second matrix\n");

        for (c = 0; c < p; c++)
            for (d = 0; d < q; d++)
                scanf("%d", &second[c][d]);

        //Normal Matrix multiplication
        for (c = 0; c < m; c++) {
            for (d = 0; d < q; d++) {
                for (k = 0; k < p; k++) {
                    sum = sum + first[c][k] * second[k][d];
                }

                multiply[c][d] = sum;
                sum = 0;
            }
        }

        printf("Product of the matrices:\n");

        for (c = 0; c < m; c++) {
            for (d = 0; d < q; d++)
                printf("%d ", multiply[c][d]);

            printf("\n");
        }
    }

    return 0;
}
```

### Output
```
Enter the number of rows and columns of the first matrix
2 2
Enter the elements of the first matrix
7 4
9 5
Enter the number of rows and columns of the second matrix
2 2
Enter the elements of the second matrix
5 3
7 9
Product of the matrices:
63 57
80 72
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/MatrixMul).
