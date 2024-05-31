## Program 2: Print the Sum of First n Natural Numbers Using Recursion

### Description
This program computes the sum of the first `n` natural numbers using recursion. It utilizes a recursive function `sum()` which adds the current number `n` to the sum of the first `n-1` natural numbers until reaching the base case of `n = 0`.
### Code
```c
// Write a program in C to print the sum of first n natural numbers using
// recursion
#include <stdio.h>

int sum(int n) {
  if (n == 0) {
    return 0;
  }

  return n + sum(n - 1);
}

int main() {
  int n, total;
  printf("Enter the number: ");
  scanf("%d", &n);

  total = sum(n);

  printf("The sum of first %d natural numbers is: %d\n", n, total);

  return 0;
}
```

### Output
```
Enter the number: 6
The sum of first 6 natural numbers is: 21
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/RecSum).
