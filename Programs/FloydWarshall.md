## Program: Floyd Warshall Algorithm for Shortest Path

### Description
This program implements the Floyd Warshall algorithm, which is used to find the shortest distances between every pair of vertices in a weighted graph. It works for both directed and undirected graphs with positive or negative edge weights (but with no negative cycles).

The algorithm maintains a matrix `dist[][]` where `dist[i][j]` represents the shortest distance from vertex `i` to vertex `j`. It iteratively considers all vertices as intermediate vertices and updates the shortest paths accordingly.

#### The Graph
Let us create the following weighted graph:
```
          10
     (0)------->(3)
      |         /|\
    5 |          |
      |          | 1
     \|/         |
     (1)------->(2)
           3

        { 0, 5, INF, 10 },
        { INF, 0, 3, INF },
        { INF, INF, 0, 1 },
        { INF, INF, INF, 0 }
```



### Code
```c
#include <stdio.h>

#define V 4
#define INF 99999

void printSolution(int dist[][V]);
void floydWarshall(int dist[][V]) {
  int i, j, k;
  for (k = 0; k < V; k++) {
    for (i = 0; i < V; i++) {
      for (j = 0; j < V; j++) {
        if (dist[i][k] + dist[k][j] < dist[i][j])
          dist[i][j] = dist[i][k] + dist[k][j];
      }
    }
  }
  printSolution(dist);
}

void printSolution(int dist[][V]) {
  printf("The following matrix shows the shortest distances"
         " between every pair of vertices \n");
  for (int i = 0; i < V; i++) {
    for (int j = 0; j < V; j++) {
      if (dist[i][j] == INF)
        printf("%7s", "INF");
      else
        printf("%7d", dist[i][j]);
    }
    printf("\n");
  }
}

int main() {
  int graph[V][V] = {
      {0, 5, INF, 10}, {INF, 0, 3, INF}, {INF, INF, 0, 1}, {INF, INF, INF, 0}};
  floydWarshall(graph);
  return 0;
}
```

### Output
```
The following matrix shows the shortest distances between every pair of vertices 
      0      5      8      9
    INF      0      3      4
    INF    INF      0      1
    INF    INF    INF      0
```

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/FloydWarshall).
