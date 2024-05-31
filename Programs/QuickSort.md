## Program: Quick Sort Implementation

### Description
This program implements the Quick Sort algorithm in C. Quick Sort is a popular sorting algorithm known for its efficiency and simplicity. It works by partitioning an array into two sub-arrays around a pivot element and recursively sorting the sub-arrays.

### Code
```c
#include <stdio.h>

void swap(int *a, int *b) {
  int temp = *a;
  *a = *b;
  *b = temp;
}

int partition(int arr[], int low, int high) {
  int pivot = arr[high];
  int i = (low - 1);

  for (int j = low; j <= high - 1; j++) {
    if (arr[j] < pivot) {
      i++;
      swap(&arr[i], &arr[j]);
    }
  }
  swap(&arr[i + 1], &arr[high]);
  return (i + 1);
}

void quickSort(int arr[], int low, int high) {
  if (low < high) {
    int pi = partition(arr, low, high);

    quickSort(arr, low, pi - 1);
    quickSort(arr, pi + 1, high);
  }
}

void printArray(int arr[], int size) {
  for (int i = 0; i < size; i++)
    printf("%d ", arr[i]);
  printf("\n");
}

int main() {
  int arr[] = {10, 7, 8, 9, 1, 5};
  int n = sizeof(arr) / sizeof(arr[0]);
  printf("Original array: \n");
  printArray(arr, n);
  quickSort(arr, 0, n - 1);
  printf("\nSorted array: \n");
  printArray(arr, n);
  return 0;
}
```

### Output
```
Original array: 
10 7 8 9 1 5 

Sorted array: 
1 5 7 8 9 10 
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/QuickSort).
