## Program 5: Calculate the GCD of Two Numbers Using Recursion

### Description
This program calculates the greatest common divisor (GCD) of two numbers `number1` and `number2` using recursion. The `findGCD()` function implements the Euclidean algorithm recursively to find the GCD by repeatedly taking the remainder of the larger number divided by the smaller number until the remainder is 0.

### Code
```c
//Write a program in C to find the GCD of two numbers using recursion
#include <stdio.h>

int findGCD(int num1, int num2) {
    if (num2 != 0) {
        return findGCD(num2, num1 % num2);
    } else {
        return num1;
    }
}

int main() {
    int number1, number2;
    printf("Enter two numbers: ");
    scanf("%d %d", &number1, &number2);
    printf("GCD of %d and %d is %d\n", number1, number2, findGCD(number1, number2));
    return 0;
}
```

### Output
```
Enter two numbers: 24
36
GCD of 24 and 36 is 12
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/RecGCD).
