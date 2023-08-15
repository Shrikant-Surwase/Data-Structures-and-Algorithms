# Graph 
A Graph is a non-linear data structure consisting of vertices and edges.
<br/>
## Tree v/s Graph
Trees are the restricted types of graphs, just with some more rules. Every tree will always be a graph but not all graphs will be trees.
Two Ways of representations: <br/>

## Representation:
1)Adacency Matrix  <br/>
2)Adjacency List

## Comparison between Adjacency Matrix and Adjacency List: <br/>

| Action |Adjacency Matrix |Adjacency List | 
| :---         |     :---:      |          ---: |       
|Adding Edge| O(1)    | 	O(1)   | 
| Removing an edge     | O(1)       | O(N)     |
| Initializing     | O(N*N)       | O(N)     |

## Adjacency Matrix Initialization code:
```C++
#include<bits/stdc++.h>
using namespace std;

class Graph{
    private:
    int numVertex;
    vector<vector<int>>adjacencyMatrix;
    public:
    Graph(int num){
        numVertex=num;
        adjacencyMatrix.resize(numVertex+1,vector<int>(numVertex+1,0));
    }
    void addEdges(int src, int dest){
        if(src >= 0 && src < numVertex+1 && dest >=0 && dest<numVertex+1){
            adjacencyMatrix[src][dest]=1;
            adjacencyMatrix[dest][src]=1;
        }
    }
    void printGraph(){
        cout<<"adjacencyMatrix:"<<endl;
        for(int i=1; i<numVertex+1; i++){
            for(int j=1; j<numVertex+1; j++){
                cout<<adjacencyMatrix[i][j]<<" ";
            }
            cout<<endl;
        }
    }
};

int main(){
    Graph g(5);
    g.addEdges(1,2);
    g.addEdges(2,3);
    g.addEdges(3,4);
    g.addEdges(4,5);
    g.addEdges(1,5);
    g.printGraph();
}
//Output:
adjacencyMatrix:
0 1 0 0 1 
1 0 1 0 0 
0 1 0 1 0 
0 0 1 0 1 
1 0 0 1 0
```
## Adjacency List Initialization code:
```C++
#include <bits/stdc++.h>

using namespace std;

class Graph {
public:
    Graph(int numVertices) : numVertices(numVertices) {
        adjacencyList.resize(numVertices);
    }

    void addEdge(int source, int destination) {
        adjacencyList[source].push_back(destination);
        // For an undirected graph, add the reverse edge as well
        // adjacencyList[destination].push_back(source);
    }

    void printGraph() {
        for (int i = 0; i < numVertices; ++i) {
            cout << "Vertex " << i << " -> ";
            for (int neighbor : adjacencyList[i]) {
                cout << neighbor << " ";
            }
            cout << endl;
        }
    }

private:
    int numVertices;
    vector<vector<int>> adjacencyList;
};

int main() {
    int numVertices = 5;
    Graph graph(numVertices);

    graph.addEdge(0, 1);
    graph.addEdge(0, 4);
    graph.addEdge(1, 2);
    graph.addEdge(1, 3);
    graph.addEdge(1, 4);
    graph.addEdge(2, 3);
    graph.addEdge(3, 4);

    graph.printGraph();

    return 0;
}
//Output:
Vertex 0 -> 1 4 
Vertex 1 -> 2 3 4 
Vertex 2 -> 3 
Vertex 3 -> 4 
Vertex 4 -> 

```

# Breadth First Search (BFS) algorithm:
## Algo:
Starting from the root, all the nodes at a particular level are visited first and then the nodes of the next level are traversed till all the nodes are visited.

To do this a queue is used. All the adjacent unvisited nodes of the current level are pushed into the queue and the nodes of the current level are marked visited and popped from the queue.

```C++
// C++ code to print BFS traversal from a given
// source vertex

#include <bits/stdc++.h>
using namespace std;

// This class represents a directed graph using
// adjacency list representation
class Graph {

	// No. of vertices
	int V;

	// Pointer to an array containing adjacency lists
	vector<vector<int> > adj;

public:
	// Constructor
	Graph(int V){
	    	this->V = V;
	adj.resize(V);
	}

	// Function to add an edge to graph
	void addEdge(int v, int w){
	    	adj[v].push_back(w);
	}

	// Prints BFS traversal from a given source s
	void BFS(int s){
	    vector<bool>visited(V,false);
	    visited[s]=true;
	    queue<int>q;
	    q.push(s);
	    while(!q.empty()){
	        s = q.front();
	        q.pop();
	        cout<<s<<" ";
	        for(auto i: adj[s]){
	            if(!visited[i]){
	                visited[i]=true;
	                q.push(i);
	            }
	        }
	    }
	}
};



// Driver code
int main()
{
	// Create a graph given in the above diagram
	Graph g(4);
	g.addEdge(0, 1);
	g.addEdge(0, 2);
	g.addEdge(1, 2);
	g.addEdge(2, 0);
	g.addEdge(2, 3);
	g.addEdge(3, 3);

	cout << "Following is Breadth First Traversal "
		<< "(starting from vertex 2) \n";
	g.BFS(0);

	return 0;
}

```




