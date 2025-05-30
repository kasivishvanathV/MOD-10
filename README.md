# CPP MODULE 10 :

# 10a :

# PROGRAM STATEMENT :
Write A C++ Program to represent the Adjacency Matrix

# ALGORITHM :
1. Initialize Matrix: Define a 2D array to represent the adjacency matrix for a graph of size n 
x n, where n is the number of vertices.
2. Input Edges: Take the number of vertices and edges as input, and for each edge (u, v), 
update the matrix entry at [u][v] (and [v][u] for undirected graphs) to 1 or the edge weight.
3. Fill Non-Edges: Set all other entries (non-edges) to 0 or a suitable default value for 
weighted graphs (e.g., INF for no connection).
4. Display Matrix: Traverse the matrix row by row and print the adjacency matrix.
5. End Program: Conclude after displaying the adjacency matrix representation of the graph

# PROGRAM :
NAME : V.Kasivishvanath
REG NO : 212222040073
```
#include<iostream>
using namespace std;
int vertArr[20][20]; 
int count = 0;
void displayMatrix(int v) 
{
 int i,j;
 for(i=0;i<v;i++)
 {
 for(j=0;j<v;j++)
 {
 cout<<vertArr[i][j]<<" ";
 }
 cout<<endl;
 }
}
void add_edge(int u, int v) 
{ 
 vertArr[u][v] = 1;
 vertArr[v][u] = 1;
 
}
int main() 
{
 int x=6,a,b;
 for(int i=0;i<6;i++)
 {
 cin>>a>>b;
 add_edge(a,b);
 }
 displayMatrix(x);
 return 0;
 return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/8f054660-a6c0-470d-b9f2-7de349534274)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 10b :

# PROGRAM STATEMENT :
Write A CPP Program to implement BFS using vectors and queue (use integer data)

# ALGORITHM :
1. Initialize Graph: Use a vector of vectors (std::vector<std::vector<int>>) to represent the 
adjacency list for a graph of double-type nodes.
2. Input Graph Data: Take input for the number of nodes and edges, and populate the 
adjacency list.
3. Perform BFS: Use a std::queue<int> to traverse the graph starting from a source node, 
marking visited nodes using a std::vector<bool>.
4. Process Nodes: Dequeue a node, process it (e.g., print it), and enqueue its unvisited 
neighbors, marking them as visited.
5. End Traversal: Repeat until the queue is empty, and then terminate the program after 
displaying the BFS traversal order.

# PROGRAM :
```
#include <bits/stdc++.h>
#define pb push_back
using namespace std;
vector<bool> v;
vector<vector<int> > g;
void edge(int a, int b)
{
 g[a].pb(b);
 g[b].pb(a);
}
void bfs(int u)
{
queue<int> q;
q.push(u);
v[u]=true;
while(!q.empty())
{
 int n = q.front();
 q.pop();
 cout<<n<<" ";
 
 for(auto i=g[n].begin();i!=g[n].end();i++)
 {
 if(!v[*i])
 {
 q.push(*i);
 v[*i] = true;
 }
 }
}
}
int main()
{
int n,a;
 cin>>n>>a;
 
 v.assign(n,false);
 g.assign(n, vector<int> ());
 int x,y;
 for(int i=0;i<a;i++)
 {
 cin>>x>>y;
 edge(x,y);
 }
 for(int i=0;i<n;i++)
 {
 if(!v[i])
 bfs(i);
 
 }
return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/66a46806-9718-414f-9a09-cc480b4a09aa)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 10c :

# PROGRAM STATEMENT :
Write A C++ Graph implementation using STL for competitive programming | (DFS of 
Unweighted and Undirected)

# ALGORITHM :
1. Initialize Graph: Use std::vector<int> to represent an adjacency list for the graph. For n 
vertices, create a vector of size n.
2. Input Graph Data: Take the number of vertices and edges as input, and populate the 
adjacency list for each edge (u, v) by adding v to u's list and u to v's list.
3. Implement DFS: Use a recursive function for Depth-First Search, taking the current node, 
the visited array, and the adjacency list as parameters.
4. Mark and Traverse: Mark the current node as visited and recursively call DFS for all 
unvisited neighbors.
5. Output Traversal: Start DFS from the source node and display the order of visited nodes 
upon traversal completion.

# PROGRAM :
```
#include <bits/stdc++.h>
using namespace std;
void addEdge(vector<int> adj[], int u, int v)
{
 adj[u].push_back(v);
}
void DFS(vector<int> adj[], int v, vector<bool> &vis)
{
 vis[v] = true;
 cout<<v<<" ";
 for(auto i :adj[v])
 {
 if(vis[i] == false)
 {
 DFS(adj, i , vis);
 }
 }
}
int main()
{ 
 int n ,a,b;
 cin>>n;
 vector<int>adj[n];
 vector<bool>visited(n,false);
 for(int i = 0 ;i < n ;i++)
 {
 cin>>a>>b;
 addEdge(adj,a,b);
 }
 DFS(adj, 1, visited);
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/46826165-f6da-45a8-b43c-ed8d57cdc3e9)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 10d :

# PROGRAM STATEMENT :
Write A C++ Program for Topological Sorting (using vector and algorithm STLs)

# ALGORITHM :
1. Initialize Graph: Use a vector of vectors (std::vector<std::vector<int>>) to represent the 
adjacency list of a directed graph, and a vector (std::vector<int>) for in-degree of each node.
2. Input Graph Data: Take the number of vertices and edges as input, populate the adjacency 
list, and update in-degrees for all nodes based on edges.
3. Identify Zero In-Degree Nodes: Use a queue (std::queue<int>) to store nodes with zero in￾degree and push them initially.
4. Perform Topological Sort: While the queue is not empty, dequeue a node, add it to the 
result, reduce the in-degree of its neighbors, and enqueue neighbors with zero in-degree.
5. Display Result: Output the nodes in topological order or indicate a cycle if the result size 
differs from the number of vertices.

# PROGRAM :
```
#include <iostream>
#include <vector>
#include <algorithm>
struct pair 
{
int a, b;
pair(int a, int b) : a(a), b(b) {}
std::ostream &print(std::ostream &out) const 
{
return (out << "(" << a << ", " << b << ")");
}
};
std::ostream &operator<<(std::ostream &out, const pair &p) 
{ 
 return p.print(out); 
 
}
struct topological_pair_comparator 
{
bool operator()(const pair &p, const pair &q) const 
{ 
 return p.a<q.a && p.b<q.b; 
 
}
} tpc;
std::vector<pair> pairs = 
{
 pair(1,1),
 pair(1,2),
pair(2,1),
pair(3,1),
pair(1,3),
pair(5,5),
pair(2,2),
pair(4,0)
};
int main() {
std::sort(pairs.begin(), pairs.end(), tpc);
for(const pair &p : pairs) std::cout << p << " ";
std::cout << std::endl;
return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/44e2a6d3-a14a-4ea6-9345-65a340f46170)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.
