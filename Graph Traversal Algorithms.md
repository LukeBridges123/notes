
# Representations of Graphs
We first consider the different ways to represent graphs in a program. The main ones are *adjacency lists* and *adjacency matrices*. In the first case, we have a list of vertices, where each entry $x$ points to a list of all the vertices that have an edge coming in from $x$. In the second case, we have a matrix whose $i, j$ entry is $1$ if vertex $i$ is adjacent to vertex $j$ and $0$ otherwise. (In multigraphs, we can generalize this to letting the $i, j$ entry equal the number of edges between the two.)

There are tradeoffs in time and space complexity between the two representations. Below, we let $V$ be the number of vertices, $E$ be the number of edges, and $d$ be the maximum degree of all the vertices. 

Testing whether two vertices are adjacent takes $O(1)$ time in an adjacency matrix (we just need to access a single entry in the matrix) and $O(d)$ time in an adjacency list (we have to look through all the vertices adjacent to the given vertex). Finding the degree of a given vertex takes $O(d)$ time in an adjacency list and $O(V)$ in an adjacency matrix (we have to go across the whole row/column and count all the ones). 

An adjacency list consumes $O(V + E)$ memory: $O(V)$ to store the "outer" list, and $O(E)$ to store all the sublists. In contrast the adjacency matrix uses $O(V^2)$ space. For sparse graphs, where $E$ is much smaller than $V$, the space taken by the adjacency list reduces to $O(V)$--much less than for the adjacency matrix. For dense graphs, on the other hand, $E \approx V^2$, so adjacency lists and matrices are asymptotically the same; matrices will have a bit less overhead and tend to work better in practice, though. 

Inserting or deleting a new edge between existing vertices takes $O(1)$ time in an adjacency matrix (just need to access and mutate a single matrix entry) and $O(d)$ in an adjacency list (especially for deletion--in general, deleting from an n-item list takes $O(n)$ time). 

As we will see below, the standard graph traversal algorithms, BFS and DFS, take $O(V+E)$ time in an adjacency list and $O(V^2)$ time in an adjacency matrix. 
# Depth-First Search
## Description
Intuitively speaking, depth-first search moves through a graph like this. Starting from some vertex $a$, pick one neighboring vertex, say $b$, and move there. If there's nowhere left to go, backtrack to $a$ and look at the other vertices connected to it; otherwise, pick some vertex $c$ connected to $b$ and start exploring from there. 

More precisely, every time depth-first search reaches a node, it adds it to a stack. If a node turns out to be a "dead end" (only connected to already-visited nodes), it pops that node from the stack (the node it's currently visiting will always be on top of the stack) and returns to whatever is next on the stack. This stack can be implemented explicitly or handled via recursion.

Searching in this way starting from a vertex $v$ will not always reach every vertex in the graph. Thus, we often wrap dfs in an "outer" function that loops over all nodes and calls dfs on each unvisited one.

In the code below, we use a graph ADT where each vertex stores a list of its neighbors (as in an adjacency list) and has an additional field, "status", which we assume is set to "unvisited" by default. Some applications of DFS, especially in directed graphs, will need to distinguish between nodes that are merely "visited", which we haven't finished exploring, and nodes that are "finished", i.e. we've called dfs() on that node and done all the exploring that's possible. The "previsit" and "postvisit" functions are optional; what they are, and if the exist, depends on the application. 

```
def dfs_outer(graph):
	for node in graph.vertices:
		if node.status == "unvisited":
			dfs_inner(node)

def dfs_inner(node):
	node.status = "visited"
	previsit()
	for other_node in node.adj:
		if node.status == "unvisited":
			dfs_inner(other_node)
	postvisit()
	node.status = "finished"
```
## Complexity
We'll end up calling the dfs_inner procedure once on each node, but only once, since we only call it on unvisited nodes, and once we call it on a node we set that node to "visited". Thus we do at least $O(V)$ steps, just from visiting each node. The other work we do is, for each node, loop once over all its adjacent nodes, which is the same as looping over all edges incident to the node. For any edge $(u, v)$, we'll look at it at most twice: once when visiting $u$, once when visiting $v$. Thus, added across all runs of dfs, those loops take $O(E)$ steps total. Depth-first search therefore takes $O(V+E)$ steps. 
## The Search Tree and Previsit/Postvisit Numbers
One way to make use of the "previsit" and "postvisit" functions is to assign numbers to each node, representing when we started and finished exploring that vertex. That is, we maintain a variable (say "clock") outside of the scope of our DFS calls, and in each node we store two numbers, pre($v$) and post($v$); calling previsit() on a node sets pre($v$) to the current clock value, then increments the clock, and calling postvisit() does the same for post($v$). 

An useful property of previsit and postvisit numbers is that, for any vertices $u, v$, the intervals \[pre(v), post(v)\] and \[pre(u), post(u)\] are either disjoint, or one is contained within the other. If we encounter $v$ while exploring from $u$, we'll finish exploring $v$ before we finish exploring $u$, so we'll have pre(u) < pre(v) < post(v) < post(v), so $v$'s interval will be contained in $u$'s. If we encounter $u$ from $v$, it'll be the other way around. If $u$ is not reachable from $v$ and $v$ is not reachable from $u$, then we'll finish exploring one before even starting to explore the other, so we'll have pre(v) < post(v) < pre(u) < post(u) or pre(u) < post(u) < pre(v) < post(v). 


Now consider the set of all edges $(u, v)$ where, while doing DFS on $u$, we call DFS on $v$. That is, $v$ is adjacent to $u$, and we explore $v$ as part of our exploration of $u$. (Intuitively, these are the edges that we "walk over while exploring the graph".) The set of all such edges forms a tree (or, in the case of a graph with multiple connected components, a forest) which includes all vertices in the graph. For these edges, we have pre(u) < pre(v) < post(v) < post(u); we call them "tree edges". 

The edges $(u, v)$ that we don't cross can be classified similarly. If pre(u) < pre(v) < post(v) < post(u), but we don't cross $(u, v)$, then we call it a "forward edge". If pre(v) < post(v) < pre(u) < post(u), then we fully explore from v (without finding u) before starting the exploration of u; we call these "cross edges". If pre(v) < pre(u) < post(u) < post(v), then we explore u from v and then find an edge back to v; we call these "back edges".
## Applications
### Cycle Detection
Depth-first search can be used to detect cycles in graphs. The case of directed graphs is especially important. The idea is that, if we ever find ourselves trying to visit a node whose status is "visited", but not "finished"--in other words, if we find a back edge while doing depth-first search--we have found a cycle. Conversely, if there is a cycle in our graph, we will find a back edge. 

To prove this, suppose first that we discover a back edge while doing depth-first search. Concretely, this means that, starting at a vertex $v$, we go through a sequence of connected vertices $v \to v_1 \to v_2 \to \dots \to v_n$, and then at $v_n$ discover an edge leading to $v$. But this is a cycle starting and ending at $v$, so our graph contains a directed cycle. For the other direction, suppose our graph has a cycle $v \to v_1 \to \dots \to v_n \to v$. We may suppose, without loss of generality, that $v$ is the first vertex in the cycle that we visit. Then, since $v_n$ is reachable from $v$, we'll go to it while exploring from $v$ (i.e. after we've set $v$ to "visited", but before we've set it to "finished"). Then, while exploring from $v_n$, we'll notice the back edge $v_n \to v$. 
### Topological Ordering
In a directed graph with no cycles, we have a natural [[Partially ordered sets|partial order]] on the vertices. If $a, b$ are distinct vertices, then either there is a directed path from $a$ to $b$, from $b$ to $a$, or neither, but not both; if there is a path from $a$ to $b$ we say that $a < b$. A "topological sort" or "linearization" is a way of listing the vertices such that, if $i < j$ (as numbers), $v_i < v_j$ (as vertices, in the sense above). This is used in many applications. For example, if we have a set of tasks to be completed, such that some tasks are prerequisites for others, we can represent this as a directed graph, with an edge from $u$ to $v$ if $u$ is a direct prerequisite for $v$. As long as there are no "circular dependencies", where we need to complete $u$ before completing $v$ but need to complete $v$ before completing $u$, the graph representation will be a DAG. If we want to check for such cyclic dependencies, we could run the cycle detection algorithm above. If we want to find a way of completing all the tasks--i.e. a list of all the tasks, such that a task always comes after its prerequisites--we use a topological sort. 

To find such an ordering, all we have to do is run a DFS (computing postvisit numbers along the way) and then order tasks in descending order of their postvisit number. 

The reason this works is that, if $b$ is reachable from $a$ in a directed acyclic graph, $b$ will have a lower postvisit number than $a$. To prove this, it suffices to show that, if there is a directed edge from $a$ to $b$, $b$ will have a lower postvisit number than $a$. When we first encounter that edge (at $a$), $b$'s status will either be "unvisited" or "finished": if it were "visited", then we'd have a back edge, contradicting the assumption that our graph has no directed cycles. In the first case, our exploration starting from $b$ will be part of our exploration starting from $a$, and the former must finish before the latter, meaning that $b$'s postvisit number will be less than $a$'s. In the second case, we've already finished exploring from $b$ (and have given it a postvisit number) before starting our exploration from $a$, so $b$ again has a smaller postvisit number than $a$. 

If $a, b$ are not directly linked by an edge, but there exists a directed path $a \to v_1 \to \dots \to v_n \to b$, we have that $b$'s postvisit number is less than $v_n$'s ,which is less than $v_{n-1}$'s, ... which is less than $v_1$'s, which is less than $a$'s. Thus $b$'s postvisit number is less than $a$'s. 

When actually doing the topological sort, we don't need to keep track of the postvisit numbers explicitly. Instead, we can just use the depth-first search code above, except that a) we keep a list of vertices, outside the scope of the dfs call and b) we modify postvisit() to add its node to the front of the list. Thus, nodes get added to the front of the list in the order in which they get fully explored, so in the resulting list, they're sorted in reverse order of when they got fully explored. 

# Breadth-First Search
## Description
Breadth-first search is what we get when we take DFS and replace the stack with a queue. At each step, we pop a node from the queue, add all of the unvisited vertices adjacent to it to the queue, and repeat. 

Notice that, if we start at a vertex $v$, the first things we'll add to the queue are the nodes at a distance of $1$ away from $v$. Then we'll add the nodes connected to the first of those nodes; considering only the ones that we haven't visited yet, these will have a distance $2$ from $v$. But unlike in depth-first search, before we start working on those distance-2 nodes, we'll have to work through all of the distance-1 nodes, since those were added to the queue first. 

What all this means is that, in breadth-first search, we first visit all the nodes at a distance 1 from the start, then all the nodes at a distance 2 from the start, and so on. We can thus use BFS to calculate distances in graphs (at least if the edges are unweighted). 

In the code below, we make the same assumptions about the graph ADT as in the DFS code above, except that we allow graph nodes to have a "distance" field, which we will use to store distances from the given node (and to keep track of which nodes we have visited).

```
def bfs(graph, v):
	for node in graph:
		node.distance = inf
	queue = deque()
	queue.append(v)
	v.distance = 0

	while len(queue) != 0:
		node = queue.popleft()
		for other_node in node.adj:
			if other_node.distance == inf: # means we haven't seen this node yet
				other_node.distance = node.distance + 1
				queue.append(other_node)
```
Unlike DFS, we don't wrap this in an outer loop that tries to visit all vertices, since in most applications of BFS we're only interested in the search starting from a given node. We could, if we wished, still do this if we wanted to use BFS to (for example) find connected components.

## Complexity
As with DFS, BFS takes $O(V+E)$ time on a graph with $V$ vertices and $E$ edges. We need to do a constant amount of work for each vertex (initializing its distance, pushing it to the queue, etc.), so we get $O(V)$ steps from that, and a constant amount of work for each edge (each edge $(u, v)$ gets checked at most twice, when we loop over all the vertices adjacent to $u$ and again when we do the same for $v$). This makes it linear in the size of an adjacency-list representation.

## Applications

### Distances from Multiple Sources
Suppose that, in a graph, we have a subset of the vertices which are "marked" in some way. We want to know, for each vertex in the graph, how far it is from the nearest marked node. 

In his case, we can use a slight modification of BFS; all we need to change is that, when initializing distances, instead of doing:
```
queue = deque()
queue.append(v)
v.distance = 0
```
we do:
```
queue = deque()
for node in graph.vertices:
	if marked(node):
		queue.append(v)
		v.distance = 0
```
Now, when we do breadth-first search with the queue initialized like this, we first handle all the marked nodes, then all the nodes that are distance 1 from *some* marked node, and so on. 

