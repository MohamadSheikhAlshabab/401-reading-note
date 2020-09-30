# Implementation: Graphs [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read29.md)

## Graphs

 - A graph is a non-linear data structure that can be looked at as a collection of vertices (or nodes) potentially connected by line segments named edges.
 - Vertex - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
 - Edge - An edge is a connection between two nodes.
 - Neighbor - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
 - Degree - The degree of a vertex is the number of edges connected to that vertex.
 
## Directed vs Undirected

  - ![](https://sites.google.com/a/cs.christuniversity.in/discrete-mathematics-lectures/_/rsrc/1409480658489/graphs/directed-and-undirected-graph/dir.png)
- __Undirected Graphs__:
  - An Undirected Graph is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.

  
- __Directed Graphs (Digraph)__:
  - A Directed Graph also called a Digraph is a graph where every edge is directed.
  - Unlike an undirected graph, a Digraph has direction. Each node is directed at another node with a specific requirement of what node should be referenced next. 
  

  
## Complete vs Connected vs Disconnected

  - __Complete Graphs__: A complete graph is when all nodes are connected to all other nodes.
  - ![](https://upload.wikimedia.org/wikipedia/commons/9/9e/Complete_graph_K7.svg)
  
  - __Connected__: A connected graph is graph that has all of vertices/nodes have at least one edge.
  - ![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8c/2-edge_connected_graph.svg/500px-2-edge_connected_graph.svg.png)
  
  - __Disconnected__: A disconnected graph is a graph where some vertices may not have edges. 
  - ![](https://i1.wp.com/www.steveclarkapps.com/wp-content/uploads/2019/03/Screenshot-2019-04-30-at-15.15.11.png?w=812&ssl=1)
  
## Acyclic vs Cyclic

  - __Acyclic Graph__: An acyclic graph is a directed graph without cycles. A cycle is when a node can be traversed through and potentially end up back at itself.
  - A directed acyclic graph is also called a DAG. This can also be represented as what we know as a tree.
  - ![](https://hazelcast.com/wp-content/uploads/2019/08/diagram-DirectedAcrylicGraph-400x314.png)
  
  - __Cyclic Graphs__: A Cyclic graph is a graph that has cycles.A cycle is defined as a path of a positive length that starts and ends at the same vertex.
  - ![](https://study.com/cimages/multimages/16/directedgraphs.png)
  
## Graph Representation

  - 1 - Adjacency Matrix
  - 2 - Adjacency List
  
 - __Adjacency Matrix__: An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix.Each Row and column represents each vertex of the data structure. The elements of both the column and the row must add up to 1 if there is an edge that connects the two, or zero if there isn’t a connection.
  - ![](https://i.morioh.com/200822/53d59484.webp)
  
- __Adjacency List__:An adjacency list is the most common way to represent graphs. An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.Adjacency lists make it easy to view if one vertices connects to another.
- ![](https://www.oreilly.com/library/view/learning-javascript-data/9781788623872/assets/268857bd-bb32-4fa5-88c9-66d7787952e9.png)

## Weighted Graphs
  - A weighted graph is a graph with numbers assigned to its edges. These numbers are called weights.
  - When representing a weighted graph in a matrix, you set the element in the 2D array to represent the actual weight between the two paths.
  - If there is not a connection between the two vertices, you can put a 0, although it is known for some people to put the infinity sign instead.
  - ![](http://www.mathcs.emory.edu/~cheung/Courses/171/Syllabus/11-Graph/FIGS/Dijkstra/weight01.gif)
  - what a __weight matrix__ would look like:
  - ![](https://www.researchgate.net/publication/275467882/figure/fig2/AS:323133820162058@1454052514508/An-example-of-bipartite-graph-construction-a-Weight-matrix-of-edges-of-bipartite-graph.png)
  - Within adjacency lists, you must include both the weight and the name of the adjacent vertex.
  - ![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightList.PNG)

## Traversals
  - 1 - Breadth First
  - 2 - Depth First
  
## Real World Uses of Graphs
  - 1 - GPS and Mapping
  - 2 - Driving Directions
  - 3 - Social Networks
  - 4 - Airline Traffic
  - 5 - Netflix uses graphs for suggestions of products
