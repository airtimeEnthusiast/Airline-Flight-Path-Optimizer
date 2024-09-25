# Airline-Flight-Path-Optimizer
This program finds the shortest path an airplane can take between cities using [Dijistra Shortest Path](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm). 

### Example 



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


