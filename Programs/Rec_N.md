## Program 1: Print the First n Natural Numbers Using Recursion

### Description
This program prompts the user to enter a number `n` and prints the first `n` natural numbers using recursion. The `print()` function recursively calls itself with decreasing values of `n` until `n` becomes 0 or less, printing the numbers in ascending order.

### Code
```c
// Write a program in C to print the first n natural numbers using recursion
#include <stdio.h>

void print(int n) {
  if (n <= 0) {
    return;
  }

  print(n - 1);
  printf("%d ", n);
}

int main() {
  int n;
  printf("Enter the number: ");
  scanf("%d", &n);

  printf("The first %d natural numbers are: ", n);
  print(n);

  return 0;
}
```

### Output
```
Enter the number: 10
The first 10 natural numbers are: 1 2 3 4 5 6 7 8 9 10
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/RecN).
