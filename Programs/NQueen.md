## Program: N Queens Problem Solver

### Description
This program solves the N Queens problem, which is a classic problem in computer science and combinatorial optimization. The problem involves placing N chess queens on an N×N chessboard so that no two queens threaten each other. In other words, no two queens can share the same row, column, or diagonal. 

The program uses a backtracking algorithm to find all possible solutions for placing N queens on the chessboard. It starts with an empty board and recursively explores all possible placements of queens, backtracking whenever it encounters a conflict with the placement rules. 

Once a solution is found, it prints the arrangement of queens on the chessboard. The program continues searching for all possible solutions until all arrangements are explored. 

#### Solution for 4 Queens
![image](https://github.com/Sabircodr/DAA_sem4/assets/121866176/a56cc2c3-a6bc-4353-b246-c0559f989d1c)



### Code
```c
#include <math.h>
#include <stdio.h>

int a[30], count = 0;

int place(int pos) {
  int i;
  for (i = 1; i < pos; i++) {
    if ((a[i] == a[pos]) || ((abs(a[i] - a[pos]) == abs(i - pos))))
      return 0;
  }
  return 1;
}

void print_sol(int n) {
  int i, j;
  count++;
  printf("\n\nSolution #%d:\n", count);
  for (i = 1; i <= n; i++) {
    for (j = 1; j <= n; j++) {
      if (a[i] == j)
        printf("Q\t");
      else
        printf("*\t");
    }
    printf("\n");
  }
}

void queen(int n) {
  int k = 1;
  a[k] = 0;
  while (k != 0) {
    a[k] = a[k] + 1;
    while ((a[k] <= n) && !place(k))
      a[k]++;
    if (a[k] <= n) {
      if (k == n)
        print_sol(n);
      else {
        k++;
        a[k] = 0;
      }
    } else
      k--;
  }
}

int main() {
  int n;
  printf("Enter the number of Queens: ");
  scanf("%d", &n);
  queen(n);
  printf("\nTotal solutions: %d", count);
  return 0;
}

```

### Output
```
Enter the number of Queens: 4

Solution #1:
*   Q   *   *
*   *   *   Q
Q   *   *   *
*   *   Q   *

Solution #2:
*   *   Q   *
Q   *   *   *
*   *   *   Q
*   Q   *   *

Total solutions: 2
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/NQueen).
