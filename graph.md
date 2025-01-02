# Graph

# What are graphs?
A graph is a non-linear data structure comprising of nodes(vertices) and edges. Graphs are versatile and can model complex relationships.
<br>
Graphs can be classified into different types based on their characteristics:
1. Directed vs. Undirected graph :
   - In a directed graph,the edges have directions,meaning they point from one vertex to another.
   - In undirected graph, the edges does not have direction and represent a two-way connection.

2. Weighted vs. unweighted graph:
   -   In a weighted graph,edges have weights or costs associated with them,useful for representing distances and priorities.
   - In an unweighted graph,all are treated equally.

3. Cyclic vs. acyclic:
   - A cyclic graph contains atleast one cycle.( a path that starts and ends at the same vertex)   
   - An acyclic graph does not contain any cycle.

Graphs are widely used in various applications such as social networks,road maps,network routing,recommendation systems due to their felxibility in representing relationships.


# Graph Representation

Graph can be represented in two ways-
  - Adjacency matrix: 
    - Represented using v*v matrix,where v=no. of vertices.
  Range of vertices = 0 - (v-1)
  Example: If v=4,then range(numbering) = 0 -(4-1) = 0-3
<br>
  Therefore,vertices are = 0,1,2,3
    - When we represent undirected graph in the form of adjacency matirx,the matrix becomes symmetric in nature.
    - 2D array where matrix[i][j] represents edge between vertices i and j.
    - Space Complexity : O(v^2)
    - Even though some spaces are empty,still O(v^2) space is taken. Lot of space is wasted in such case,so adjacency matrix is rarely used.


  - Adjacency list:
    - Represented in the form of array or list where each index stores connected vertices. We take a node and store its connected nodes and to do this unordered_map is used in C++.

    Representation using unordered_map in C++-
    ``` C++
    unordered_map<int,vector<int>>adj;
    ```

    - Space complexity: O(V+E)

# Implementation og Graph using Adjacency list in C++:

```C++
// C++ Program to Implement a Graph Using Adjacency List
#include <iostream>
#include <list>
#include <map>
using namespace std;

class Graph {
    map<int, list<int> >
        adjList; // Adjacency list to store the graph

public:
    // Function to add an edge between vertices u and v of
    // the graph
    void add_edge(int u, int v)
    {
        // Add edge from u to v
        adjList[u].push_back(v);
        // Add edge from v to u because the graph is
        // undirected
        adjList[v].push_back(u);
    }

    // Function to print the adjacency list representation
    // of the graph
    void print()
    {
        cout << "Adjacency list for the Graph: " << endl;
        // Iterate over each vertex
        for (auto i : adjList) {
            // Print the vertex
            cout << i.first << " -> ";
            // Iterate over the connected vertices
            for (auto j : i.second) {
                // Print the connected vertex
                cout << j << " ";
            }
            cout << endl;
        }
    }
};

int main()
{
    // Create a graph object
    Graph g;

    // Add edges to create the graph
    g.add_edge(1, 0);
    g.add_edge(2, 0);
    g.add_edge(1, 2);

    // Print the adjacency list representation of the graph
    g.print();
    return 0;
}
```

# Implementation of Graph using Adjacency matrix in C++:
```C++
// C++ Program to Implement a Graph Using Adjacency Matrix
#include <iostream>
#include <vector>
using namespace std;

class Graph {
    // Adjacency matrix to store graph edges
    vector<vector<int> > adj_matrix;

public:
    // Constructor to initialize the graph with 'n' vertices
    Graph(int n)
    {
        adj_matrix
            = vector<vector<int> >(n, vector<int>(n, 0));
    }

    // Function to add an edge between vertices 'u' and 'v'
    // of the graph
    void add_edge(int u, int v)
    {
        // Set edge from u to v
        adj_matrix[u][v] = 1;
        // Set edge from v to u (for undirected graph)
        adj_matrix[v][u] = 1;
    }

    // Function to print the adjacency matrix representation
    // of the graph
    void print()
    {
        // Get the number of vertices
        cout << "Adjacency Matrix for the Graph: " << endl;
        int n = adj_matrix.size();
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                cout << adj_matrix[i][j] << " ";
            }
            cout << endl;
        }
    }
};

int main()
{
    // Number of vertices
    int n = 4;
    // Create a graph with 4 vertices
    Graph g(n);

    // Adding the specified edges in the graph
    g.add_edge(0, 1);
    g.add_edge(0, 2);
    g.add_edge(1, 3);
    g.add_edge(2, 3);

    // Print the adjacency matrix representation of the
    // graph
    g.print();
    return 0;
}


