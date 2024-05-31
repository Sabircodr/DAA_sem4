## Program: Graph Coloring using Backtracking

### Description
This program implements a solution to the m-coloring problem using backtracking. The m-coloring problem involves assigning colors to the vertices of a graph such that no two adjacent vertices have the same color, using at most m different colors. The program checks if it is possible to color a given graph with m colors.

### Code
```c
//Write a program for M-Colouring Problem using Backtracking Algorithm.
#include <stdbool.h>
#include <stdio.h>

#define V 4

bool isSafe(int v, int graph[V][V], int color[], int c) {
  for (int i = 0; i < V; i++)
    if (graph[v][i] && c == color[i])
      return false;
  return true;
}

bool graphColoring(int graph[V][V], int m, int color[], int v) {
  if (v == V)
    return true;

  for (int c = 1; c <= m; c++) {
    if (isSafe(v, graph, color, c)) {
      color[v] = c;
      if (graphColoring(graph, m, color, v + 1))
        return true;
      color[v] = 0;
    }
  }
  return false;
}

int main() {
  int graph[V][V] = {{0, 1, 1, 1}, {1, 0, 1, 0}, {1, 1, 0, 1}, {1, 0, 1, 0}};
  int m = 3;
  int color[V] = {0};

  if (!graphColoring(graph, m, color, 0)) {
    printf("Solution does not exist\n");
    return 1;
  }

  printf("Solution exists. The assigned colors are:\n");
  for (int i = 0; i < V; i++)
    printf("Vertex %d ---> Color %d\n", i, color[i]);

  return 0;
}
```

### Output
```
Solution exists. The assigned colors are:
Vertex 0 ---> Color 1
Vertex 1 ---> Color 2
Vertex 2 ---> Color 3
Vertex 3 ---> Color 2
```

### Explanation
- **isSafe**: This function checks if it is safe to color vertex `v` with color `c`. It returns `false` if any adjacent vertex has the same color `c`.
- **graphColoring**: This is the main backtracking function that tries to assign colors to vertices. It returns `true` if all vertices are colored successfully.
- **main**: The `main` function initializes the graph, the number of colors, and the color array. It then calls the `graphColoring` function to attempt to color the graph. If successful, it prints the colors assigned to each vertex.

> [!TIP]
> ### Try it Out
> You can try running this program online by clicking [here](https://replit.com/@SabirMallick/MColor).
