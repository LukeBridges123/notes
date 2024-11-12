# Breadth-First Search
In the simplest case, where our graph is unweighted (and may be undirected or directed), we can find distances and shortest paths using [[Graph Traversal Algorithms#Breadth-First Search|breadth-first search]]. See the linked article for more details.
# Dijkstra's Algorithm
Now suppose that our graph (which again may be either undirected or directed) has weights on the edges, and we wish to find distances (or shortest paths) from one vertex $v$ to all other vertices. As long as our graph has no negative-weight edges, we can do this with Dijkstra's algorithm, which is essentially a form of [[Dynamic Programming|dynamic programming]].
## Description
We can think of Dijkstra's algorithm as involving a set of "known" vertices, such that for each known vertex $u$, we know the distance from $v$ to $u$, and know that the shortest path must only involve other known vertices. At each step, we find the vertex $u$ not in the known set which is closest to the known set, and can then add it to the known region. If we keep doing this until every vertex reachable from $v$ is in the known set, we'll have distances from $v$ to every reachable vertex.

Concretely: for each vertex $u$ we keep track of a value $d(u)$, initially set to infinity, which represents the length of the shortest path from $v$ to $u$ that stays within the known region, with $d(u)$ being infinity if no such path exists. (Once a vertex is in the known region, $d(u)$ will just be its distance from $v$.) We keep all the vertices *not* in the known region in a priority queue which sorts them by $d(u)$. At each step, we remove the vertex $u$ with the least distance from the queue. For each vertex $u'$ adjacent to $u$, we set $d(u') = \min(d(u'), d(u) + w(u, u'))$ where $w(u, u')$ is the weight of the edge between $u$ and $u'$. (This is because the shortest path from $v$ to $u'$ through the known region either uses only vertices already in the known region, in which case it has length $d(u')$, or passes through the new vertex $u$, in which case it's the length of the shortest path from $v$ to $u$, $d(u)$, plus the weight of the edge from $u$ to $u'$.) We update the priority queue accordingly so that we can find the new closest vertex, and then repeat. 

The main step in need of justification here is the one where we take the vertex with the least $d(u)$ and add it to the known region. How do we know that $d(u)$, the distance of the shortest path that stays within the known region, is the right distance from $v$ to $u$? In particular, how do we know that the shortest path doesn't pass through some vertex $u'$ not in the known region? 

This is because the distance of such a path would be $d(u') + d(u', u)$, where $d(u', u)$ is the length of the shortest path from $u'$ to $u$. But $d(u') \geq d(u)$ (by our assumption that $u$ is the vertex closest to the known region) and $d(u', u) \geq 0$ (by our assumption that the graph has no negative edges). Thus $d(u') + d(u', u) \geq d(u)$, so taking a detour through $u'$ would never make the path shorter. 

Thus, at each step, we correctly find the distance from $v$ to $u$ for one more vertex $u$. This guarantees that our algorithm is correct, i.e. that once we're done we'll know the correct distance for all vertices. 

## Code

## Complexity

