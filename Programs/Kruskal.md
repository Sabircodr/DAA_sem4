## Program: Kruskal's Algorithm Implementation

### Description
This program implements Kruskal's algorithm, which is a greedy algorithm that finds a minimum spanning tree for a connected weighted graph. It repeatedly adds the next lightest edge to the tree if it doesn't produce a cycle until all vertices are included in the spanning tree.

### Code
```c
#include<stdio.h>
#include<stdlib.h>

int i, j, k, a, b, u, v, n, ne = 1;
int min, min_cost = 0, cost[9][9], parent[9];

int find(int);
int uni(int, int);

int main() {
  printf("\n\n\tImplementation of Kruskal's algorithm\n\n");
  printf("\nEnter the no. of vertices\n");
  scanf("%d", &n);
  printf("\nEnter the cost adjacency matrix\n");
  for (i = 1; i <= n; i++) {
    for (j = 1; j <= n; j++) {
      scanf("%d", &cost[i][j]);
      if (cost[i][j] == 0)
        cost[i][j] = 999;
    }
  }
  printf("\nThe edges of Minimum Cost Spanning Tree are\n\n");
  while (ne < n) {
    for (i = 1, min = 999; i <= n; i++) {
      for (j = 1; j <= n; j++) {
        if (cost[i][j] < min) {
          min = cost[i][j];
          a = u = i;
          b = v = j;
        }
      }
    }
    u = find(u);
    v = find(v);
    if (uni(u, v)) {
      printf("\n%d edge (%d,%d) = %d\n", ne++, a, b, min);
      min_cost += min;
    }
    cost[a][b] = cost[b][a] = 999;
  }
  printf("\n\tMinimum cost = %d\n", min_cost);
}

int find(int i) {
  while (parent[i])
    i = parent[i];
  return i;
}

int uni(int i, int j) {
  if (i != j) {
    parent[j] = i;
    return 1;
  }
  return 0;
}
```

### Output
```
    Implementation of Kruskal's algorithm


Enter the no. of vertices
6

Enter the cost adjacency matrix
0 6 0 0 5 1
6 0 3 0 0 5
0 3 0 6 0 6
0 0 6 0 2 4
5 0 0 2 0 5
1 5 6 4 5 0

The edges of Minimum Cost Spanning Tree are


1 edge (1,6) =1

2 edge (4,5) =2

3 edge (2,3) =3

4 edge (4,6) =4

5 edge (2,6) =5

    Minimum cost = 15
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/Kruskal).
