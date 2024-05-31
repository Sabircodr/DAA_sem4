## Program 9: Implement Tower of Hanoi Using Recursion

### Description
This program demonstrates the Tower of Hanoi problem using recursion. The Tower of Hanoi is a classic problem where the objective is to move a tower of disks from one rod to another, with the constraint that only one disk can be moved at a time, and no disk can be placed on top of a smaller disk. The program takes the number of disks as input and recursively solves the problem, printing each move required to solve the puzzle.
#### _Image Illustration for 3 Disks_
![image](https://media.geeksforgeeks.org/wp-content/uploads/tower-of-hanoi.png)  

### Code
```c
// Write a program in C to implement Tower of Hanoi using recursion.
#include <stdio.h>

void towerOfHanoi(int n, char source, char destination, char aux_rod) {
  if (n == 1) {
    printf("\n Move disk 1 from rod %c to rod %c", source, destination);
    return;
  }
  towerOfHanoi(n - 1, source, aux_rod, destination);
  printf("\n Move disk %d from rod %c to rod %c", n, source, destination);
  towerOfHanoi(n - 1, aux_rod, destination, source);
}

int main() {
  int n;
  printf("Enter the number of disks: ");
  scanf("%d", &n);
  towerOfHanoi(n, 'A', 'C', 'B'); // A, B and C are names of rods
  return 0;
}
```

### Output
```
Enter the number of disks: 3

 Move disk 1 from rod A to rod C
 Move disk 2 from rod A to rod B
 Move disk 1 from rod C to rod B
 Move disk 3 from rod A to rod C
 Move disk 1 from rod B to rod A
 Move disk 2 from rod B to rod C
 Move disk 1 from rod A to rod C
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/towerOfHanoi).
