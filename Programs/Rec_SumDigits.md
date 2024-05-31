## Program 4: Calculate the Sum of Digits Using Recursion

### Description
This program calculates the sum of digits of a given number `num` using recursion. The `sumOfDigits()` function recursively extracts the last digit of `num` using modulo operator and adds it to the sum of the remaining digits obtained by integer division by 10.

### Code
```c
//Write a program in C to find the sum of digits using recursion
#include <stdio.h>

int sumOfDigits(int n) {
    if (n == 0) {
        return 0;
    } else {
        return (n % 10) + sumOfDigits(n / 10);
    }
}

int main() {
    int num, sum;

    printf("Enter a number: ");
    scanf("%d", &num);

    sum = sumOfDigits(num);

    printf("Sum of digits: %d", sum);

    return 0;
}
```

### Output
```
Enter a number: 456
Sum of digits: 15
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/RecSumDigits).
