## Equivalent Definitions of Trees
A tree is any simple, undirected, connected (note that all three of these conditions are important) graph that meets one of the following equivalent conditions:
1. Is "minimally connected", in the sense that removing any edge turns it into a disconnected graph.
2. Has no cycles.
3. Has only one path between any two distinct vertices.
4. Has n vertices and n-1 edges. 
### Equivalence of being acyclic and being minimally connected
A graph G that has a cycle must not be minimally connected. Let A and B be two adjacent vertices in the cycle; removing the edge between them does not disconnect A and B, since you can still get between them using the rest of the edges in the cycle. So if a graph is minimally connected it must be acyclic.

Conversely, suppose that G is not minimally connected, so that there is some edge AB such that the graph G' obtained by removing AB is also connected. Then G' has a path from A to B, and combining this path with AB gives a cycle in G. 
### Equivalence of being acyclic and having unique paths 
Suppose that there are vertices A and B in G such that there are two distinct paths from A to B. These paths must diverge at one vertex $v_1$ and then join back up at another vertex $v_2$. (We suppose WLOG that they don't join back up before reaching $v_2$.) Then by joining the vertices and edges in A that go from $v_1$ to $v_2$, and the vertices and edges in B that go from $v_1$ to $v_2$, you get a cycle containing $v_1$ and $v_2$. 

Conversely, if a graph has a cycle, then that gives multiple paths between any distinct vertices in the cycle. 
### Tree iff connected and has n-1 edges
#### Lemma: all trees have leaves
Any tree must have at least 2 vertices ("leaves") with degree 1. Proof: the endpoints of any maximum-length path in the tree will be leaves; if an endpoint of the path isn't a leaf, it must not be a maximum-length path, since there will be at least one vertex adjacent to the endpoint which isn't yet in the path, and we can add that to increase the length. (The fact that we can do this stems ultimately from the fact that the tree has no cycles: if the "endpoint" was connected to multiple vertices in the path, we could use the endpoint and the relevant segment of the path to form a cycle; but since there are no cycles, this can't happen.)

We use this lemma to prove the equivalence of (4) with the other requirements to be a tree by induction. Certainly the trees on 1 and 2 vertices have 0 and 1 edge respectively. In general, given a tree on n vertices, one can take a leaf (which must exist, by the lemma above) and remove it to get a tree with n-1 vertices which must, by the induction hypothesis, have n-2 edges. Adding back on the leaf and its edge gives n-1 edges. 

The converse, that every connected simple undirected graph with n vertices and n-1 edges is a tree, can also be proven by induction. Base cases are trivial; for the induction step, note that any graph with n vertices and n-1 edges can of course be constructed by taking a graph with n-1 vertices and n-2 edges and adjoining a new vertex and edge. By the induction hypothesis, the old graph is a tree. When we adjoin the new edge and vertex, we must let the new edge be incident to the new vertex (else the new graph would be disconnected). This makes the new vertex a leaf (since it is connected to only one vertex, namely the other vertex incident to the new edge), and adding a leaf to a tree results in another tree. So any n-vertex, n-1-edge graph constructed by adjoining a new vertex and edge to a tree is a tree, and given that all n-vertex, n-1-edge connected graphs can be constructed this way, all such graphs are trees. 
#### Extension to forests
A forest is a graph whose connected components are all trees. A forest with n vertices and k connected components has n-k edges. Proof: let $a_1, \dots a_k$ be the number of vertices in each connected component. Since these are each trees, they will have $a_i - 1$ edges each. So there will be $(a_1 - 1) + \dots + (a_k - 1) = (a_1 + \dots + a_k) - k = n - k$ edges. 

## Cayley's Formula: Counting Labeled Trees
