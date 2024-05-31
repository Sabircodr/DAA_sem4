## Program 3: Generate Fibonacci Series Using Recursion

### Description
This program generates the Fibonacci series up to the specified number of terms `n` using recursion. The `fibonacci()` function recursively computes each term of the series by summing the previous two terms. In the `main()` method, a loop from 1 to `n` iterates to print the Fibonacci series terms.

### Code
```c
// Write a program in C to print the Fibonacci series using recursion
#include <stdio.h>

int fibonacci(int n) {
    if (n <= 1) {
        return n;
    } else {
        return fibonacci(n-1) + fibonacci(n-2);
    }
}

int main() {

    int n;
    printf("Enter the number of terms for Fibonacci Series: ");
    scanf("%d", &n);
    printf("Fibonacci Series: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", fibonacci(i));
    }
    return 0;
}
```

### Output
```
Enter the number of terms for Fibonacci Series: 6
Fibonacci Series: 0 1 1 2 3 5
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/RecFibo).
