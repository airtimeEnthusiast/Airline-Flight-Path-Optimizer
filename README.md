# Airline-Flight-Path-Optimizer
This program finds the shortest airplane route can take between cities using [Dijistra Shortest Path](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm). 

## Program Description

### Algorithm Description
Dijkstra's algorithm derives the shortest path on a weighted, directed graph **G = (V,E)** by selecting, for each node/vertex, the adjacent node with the shortest path. This implementation uses a minimum-priority queue of nodes to estimate the shortest path between vertices based on their respective edges.
```
DIJKSTRA(G, w, s)
  INITIALIZE-SINGLE-SOURCE(G,s);
  S = ∅
  Q = G.V
  while Q != ∅
    u = EXTRACT_MIN(Q)
    S = S ∪ {u}
    for each node v ∈ G.Adj[u]
      RELAX(u,v,w)
```
Where *G* is a graph of nodes, *w* is a weight between nodes, *s* is the starting node. *V* is the number of nodes in the directed graph *G*
- Line 1 initializes the graph.
- Line 2 intializes the shortest path estimation set to empty
- Line 3 intializes all the nodes in V into the min-priority queue *Q*
- Lines 4-8 extract and add the vetex into the shortest path estimation set *S*
- Lines 7-8 relax each edge and reducing the distance between source *u* and destination *v*

### Graph Class
Contains a minimum heap structure to organize a collection of nodes and functions to compute the djistra algorithm. 
```
class Graph
{
   private:
      int numOfNode;        //number of nodes in the graph
      MinHeap* cityHeap;    //a min-heap of departure City objects

   public:
      Graph(int numOfNode, MinHeap* cityHeap);
      int findOneCity(string aCityName);
      int weight(City u, City v);
      void destructor();
      void printGraph(int index);
      void initialize_single_source(string sourceCityName);
      void relax(City &u, City &v);
      void dijkstra(string sourceCityName);
      void printDijkstraPath(string sourceCityName);
};
```

## Example 
- Given a scenario where the starting point is Los Angeles, and the destinations are Washington and New York, the algorithm will determine which route is more optimized based on the values of the edges between the nodes. 
- In this case, the edge between Los Angeles and New York is relaxed since it is more optimal to traverse through Washington, as the total weight of the edges is less than a direct traversal.
<p align="center">
  <img src="images/example.svg?raw=true" alt="example"/>
</p
<p align="center">
  <img src="images/example_output.png?raw=true" alt="example output width="100"/>
</p>

[Source Code](https://github.com/airtimeEnthusiast/DijkstraShortestPath)

## Example 2
- Given a more complex scenario where the starting point is Seattle, and the desired destination is Washington.
- The edges between **Seattle, Salt Lake, Santa Fe, Austin, Dallas, Atlanta, and Washington** is relaxed and the most optimal to traversal.
<p align="center">
  <img src="images/example2.png?raw=true" alt="example"/>
</p
  
- Some more expensive alternative paths:

| Path    | Total Weight |
| -------- | ------- |
| Seattle, New York, Chicago, Denver, Dallas, Atlanta, Washington | $3885    |
| Seattle, New York, Chicago, Denver, Santa Fe, Austin, Dallas, Atlanta, Washington| $4512 |

<p align="center">
  <img src="images/example_output2.png?raw=true" alt="example output width="100"/>
</p>

[Source Code](https://github.com/airtimeEnthusiast/DijkstraShortestPath)

