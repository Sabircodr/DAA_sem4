## Program 10: Implement Job Sequencing with Deadline

### Description
This program implements Job Sequencing with Deadline. It takes the number of jobs as input along with their profits and deadlines. The program then schedules the jobs in such a way that the maximum profit is obtained while adhering to the deadlines. It sorts the jobs based on their profits in descending order and then allocates each job to the nearest available slot before its deadline. If a slot is not available, the job is rejected.


#### Jobs Information
| Job Index | Profit | Deadline |
|:---------:|:------:|:--------:|
|     1     |   50   |    2     |
|     2     |   10   |    1     |
|     3     |   15   |    2     |
|     4     |   30   |    1     |

### Code
```c
//Write a program to implement Job Sequencing with deadline.
#include<stdio.h>
#include<stdlib.h>

int n, i, j, k, t;

int check(int s[], int p) { 
  int ptr = 0;
  for(int i = 0; i < n; i++) {
    if(s[i] == p)
      ptr++;
  }
  if(ptr == 0)
    return 1;
  else
    return 0;
}

int main() {
  int profit;
  int *slot, *d, *p;
  printf("Enter the number of jobs: ");
  scanf("%d", &n);
  slot = (int*)malloc(n * sizeof(int));
  d = (int*)malloc(n * sizeof(int));
  p = (int*)malloc(n * sizeof(int));
  
  for(i = 0; i < n; i++) {
    printf("\nEnter the profit of job #%d: ", i + 1);
    scanf("%d", &p[i]);
    printf("Enter the deadline of job #%d: ", i + 1);
    scanf("%d", &d[i]);
  }
  
  for(i = 0; i < n; i++)
    for(j = i + 1; j < n; j++)
      if(p[i] < p[j]) {
        t = p[i];
        p[i] = p[j];
        p[j] = t;
        t = d[i];
        d[i] = d[j];
        d[j] = t;
      }
      
  for(i = 0; i < n; i++)
    slot[i] = 0;
  for(i = 0; i < n; i++)
    for(j = d[i]; j > 0; j--) {
      if(check(slot, j) == 1) {
        slot[i] = j;
        break;
      }
    }
    
  printf("\n\nINDEX PROFIT DEADLINE SLOT ALLOTTED ");
  for(i = 0; i < n; i++) {
    if(slot[i] > 0)
      printf("\n\n %d\t\t%d\t\t%d\t\t\t[%d - %d]", i + 1, p[i], d[i],
    else
      printf("\n\n %d\t\t%d\t\t%d\t\t\tREJECTED", i + 1, p[i], d[i]);
  }
}
```

### Output
```
Enter the number of jobs: 4

Enter the profit of job #1: 50
Enter the deadline of job #1: 2

Enter the profit of job #2: 10
Enter the deadline of job #2: 1

Enter the profit of job #3: 15
Enter the deadline of job #3: 2

Enter the profit of job #4: 30
Enter the deadline of job #4: 1

INDEX  PROFIT  DEADLINE    SLOT ALLOTTED 
 1      50      2           [1 - 2]
 2      30      1           [0 - 1]
 3      15      2           REJECTED
 4      10      1           REJECTED 
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/JobSequencing).
