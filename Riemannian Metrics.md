# Definition
Riemannian metrics give a way of measuring distances, lengths, and angles on a manifold, by giving an inner-product structure at each tangent space. Once we have this, we can (for example) define "infinitesimal length elements", and integrate those along curves to get their length; then, given two points $p, q$, we can define the distance between them as the length of the shortest path between them. 

By "give an inner-product structure to each tangent space" we mean (smoothly) associate a positive-definite, symmetric bilinear form with each tangent space; in other words, a type 0, 2 tensor field which is positive-definite and symmetric at each point. Such a tensor field is called a "Riemannian metric". Thus, if $g$ is such a tensor field, then for any vector fields $X, Y$ we have $g(X, Y) = g(Y, X)$ and $g(X, X) \geq 0$, with equality achieved only if $X = 0$. 

A Riemannian manifold is then a manifold with a choice of metric $g$. 

This then lets us define the norm of a vector field as $|X| = \sqrt{g(X, X)}$. 

Locally, a metric looks like $g = \sum_{i, j} g_{ij} dx^i \otimes dx^j$. Here, $g_{ij} = g(\pd{}{x^i}, \pd{}{x^j})$. Thus, in coordinates, $g$ is a symmetric $n \times n$ matrix. 

# Examples
In $\R^n$, the standard dot product gives a Riemannian metric $g_0(X, Y) = X \cdot Y$, called the "Euclidean metric". As a tensor, this looks like $g_0 = \sum_i dx^i \otimes dx^i$. 

On any manifold, an immersion or embedding $f: M \to \R^N$ determines a "pullback metric" $g = f^*g_0$, by $(f^*g_0)(X, Y) = g_0(f_*X, f_*Y) = f_*X \cdot f_*Y$. 

Since any manifold can be embedded into Euclidean space, this then lets us show that any manifold has a Riemannian metric (certainly not a unique one)--just pick an embedding $f$ and use it to induce a metric as above. 

Note also that the Nash embedding theorem says that every metric comes from a pullback metric; more precisely, that any Riemannian manifold can be isometrically embedded into $\R^N$ for large enough $N$ (generally larger than the $N$ in the Whitney embedding theorem).
# Lengths and Distances
## Riemannian Manifolds as Metric Spaces
On any connected manifold with a Riemannian metric $g$, we get an induced metric defined by $d(p, q) = \inf_\gamma L(\gamma)$, where $\gamma$ ranges over all piecewise-smooth paths starting at $p$ and ending at $q$. We define $L(\gamma) = \int_a^b |\dot{\gamma}(t)|dt$, using the Riemannian metric to measure the norm $|\dot{\gamma}(t)|$. 

If $M$ is connected, it is path-connected, so paths between any two points exist. Clearly the length of the shortest path from $p$ to $q$ is the same as the length of the shortest path from $q$ to $p$, since we can take any path from one point to the other and reverse the direction. We have $d(p, q) \geq 0$ (since it's the $\inf$ of the nonnegative quantity $L(\gamma)$) and $d(p, p) = 0$ (since the path that just stays at $p$ has length $0$). Also, $d(p, q) > 0$ for $p \neq q$ ...

For the triangle inequality, we can concatenate any path from $p$ to $r$ and any path from $r$ to $q$ to get a path from $p$ to $q$ (recall that we only required our paths to be piecewise smooth)...

The topology determined by the metric is the same as the topology that the manifold has by definition, i.e. open sets according to the metric are the same as the open sets in the original topology.

Note also that the length of a path is independent of its parameterization. Thus we will typically, without loss of generality, use paths whose domain is $[0, 1]$. 

## Length and Energy
The length of a path (parameterized by $[0, 1]$) is $L(\gamma) = \int_0^1 |\dot{\gamma}(t)|dt$; the "energy" of a path is defined as $E(\gamma) = \int_0^1 |\dot{\gamma}(t)|^2 dt$. (Cf. the squared velocity that shows up in the formula for kinetic energy.)

## Geodesics
A *geodesic* from $p$ to $q$ is a path which is a critical point of $L$ (considered as a functional, i.e. a function mapping functions to real numbers). This turns out to be equivalent to being a critical point of $E$. A *minimal geodesic* is a geodesic which is a minimum (as opposed to a maximum or saddle) of $L$, which is again equivalent to being a minimum of $E$. 
### Examples
In $\R^n$ with the Euclidean metric, geodesics are just straight lines. 

On the unit sphere, geodesics are segments of great circles (curves like the equator that divide the sphere into two equal pieces). There will typically be two geodesics between any two given points, one minimal and one not (not including paths which go around the sphere multiple times). (For example, say you're at a point $p$ on the equator, and there's a point $q$ a few feet east of you, also on the equator. Then the eastward path along the equator is a minimal geodesic, while the westward path is also a geodesic, but not minimal.) 