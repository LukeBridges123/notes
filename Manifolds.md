# Topological Manifolds
## Charts, Atlases, etc. 
Let $M$ be a topological space satisfying certain technical conditions (second-countable and Haussdorf)--we can, without too much loss of generality, just say a metric space. A *chart* on some open subset $U$ of $M$ is a homeomorphism from $U$ to some open subset of $\R^n$. If $\phi$ is a chart, then its inverse $\phi^{-1}$ is called a "parameterization" of $U$, and induces "curvilinear coordinates" on $U$. An *atlas* is a collection of charts on $M$, such that the domains cover $M$. A *topological manifold* of dimension $n$ is a topological space with an atlas (where all the codomains of the charts are in $\R^n$), i.e. a metric space such that every point has a neighborhood (open set containing that point) with a chart from that subset to $\R^n$. These are also called "$C^0$ manifolds", since the charts are $C^0$ bijections. 
## Examples
Lines, open intervals, and closed curves are 1-dimensional manifolds, though self-intersecting curves, curves with endpoints, and closed intervals are not. Planes and many surfaces (spheres, tori, single cones) are 2-manifolds, but some degenerate cases like 2 cones joined at their vertices, or two spheres touching at a point, are not. A cone does not, however, fit the definition of a *smooth* manifold, as explained below.

The obvious way to "improve" on the definition of a topological manifold would be to require the charts to be $C^r$ for some positive $r$, or $C^\infty$, but since the set $M$ is just some almost-arbitrary metric space it's not clear how we'd define derivatives for functions $M \to \R^n$. We will need additional structure as described below. 
# Smooth Manifolds

## C^k Atlases
While we can't directly ask whether the charts are differentiable, we can ask, on the overlap between the domains of two charts, whether the "change-of-coordinates" from one chart to another is differentiable. 

That is, say we have two overlapping open sets $U_1, U_2$ on a manifold, with corresponding charts $\phi_1, \phi_2$. $\phi_1$ maps $U_1 \to V_1$, with $V_1 \subseteq \R^n$ and $\phi_1^{-1}$ is the "parameterization" $V_1 \to U_1$. With suitable restrictions of the domains and codomains, we can consider the composition $\phi_2 \circ \phi^{-1}_1$--call it $\phi_{2, 1}$, say-- which goes from $V_1$ to $U_1 \cap U_2$ and from there to $V_2$, and is thus a function $V_1 \to V_2$, i.e. $\R^n \to \R^n$. We can then talk about whether this new function $\phi_{2, 1}$ is [[Differential Calculus in Rn|differentiable as a function on Euclidean space]]. 

This then lets us define a "$C^k$ atlas" to be an atlas where, for every pair of indices $\alpha, \beta$ with overlapping open sets, the corresponding "transition map" $\phi_{\beta, \alpha}$, which goes from $\phi_{\alpha}(U_\alpha \cap U_\beta)$ to $\phi_{\beta}(U_\alpha \cap U_\beta)$, is $C^k$. (When this condition holds for two given charts $\phi_\alpha, \phi_\beta$, we say that they are "$C^k$ related".)

Note that, if it is $C^k$, one of these transition maps is a $C^k$ diffeomorphism, i.e. has a $C^k$ inverse; the inverse of $\phi_{\beta, \alpha}$ is $\phi_{\alpha, \beta} = \phi_\alpha \circ \phi_\beta^{-1}$.

A "maximal" $C^k$ atlas is one which is not a proper subset of any other atlas. Any atlas is part of a unique maximal atlas. Let $A$ be an atlas, consisting of charts $\phi_\alpha$ where $\alpha$ ranges over some indexing set $I$. Then the corresponding maximal atlas $\ol{A}$ (should be a tilde, fix later?) can be constructed by throwing in all charts $U \to V$, where $U$ is an open subset of the manifold, that are $C^k$ related to some chart in $A$. 

## Definition of a Smooth Manifold
With all these preliminaries out of the way, an $n$-dimensional $C^k$ manifold is a topological space plus a maximal $C^k$ atlas. (The result about extending atlases to maximal atlases implies that, to specify a manifold, you only need to give a single atlas which need not be maximal; a maximal atlas will be uniquely determined by the given atlas.) This has as special cases $C^0$ manifolds, which are topological manifolds as discussed above, and $C^\infty$ or *smooth* manifolds. 

## Examples
$\R^n$ itself is an $n$-dimensional smooth manifold, as is any open subset $U$. You only need one chart, namely the identity map, and this is $C^\infty$ related to itself.

The circle $S^1$ is a one-dimensional smooth manifold. Say for concreteness that we're looking at the unit circle in $\R^2$. Then we can define charts using the coordinate $\theta$ on two overlapping "open sections" of the circle, neither of which covers the whole thing, and mapping those into the corresponding open intervals on $\R$. 

The sphere $S^2$ is a two-dimensional smooth manifold; charts can be defined using "stereographic projection" onto the plane to cover all but one point (at the "north pole"), and then doing the same thing about the south pole to cover everything but that point; those together cover the whole sphere, and are smoothly related. The same thing works for the $n$-sphere $S^n$, projecting onto a hyperplane in $\R^{n+1}$. 

Open subsets of $C^k$ manifolds are themselves $C^k$ manifolds--just restrict the relevant charts to that open subset to get a $C^k$ atlas.

If $M$, $N$ are $m$ and $n$ dimensional $C^k$ manifolds, then on their product topological/metric space $M \times N$, we can define a $C^k$ manifold structure that makes this into an $m + n$ dimensional manifold. Namely, we start with the set of all "products of charts", i.e. for all indices $\alpha, \beta$, we consider functions from $M \times N$ of the form $(x, y) \to (\phi_\alpha(x), \phi_\beta(y))$, and then we extend that to a maximal atlas. (This is maybe analogous to how, in order to form the product topology, you start with products of open sets and then  use those as a basis to get all open sets.)

## Quotient Manifolds

# Functions on Manifolds

## Smooth Functions on Manifolds
### From a Manifold to R
Take a manifold $M$ with a smooth atlas of functions $\phi_\alpha: U_\alpha \to V_\alpha \subseteq \R^n$. We define a function $M \to \R$ to be $C^k$ at a point $p$ if its "coordinate representation" $f \circ \phi_\alpha^{-1}$ is $C^k$ (as a function $\phi_\alpha(U_\alpha) \supset \R^n \to \R$) for some chart $\phi_a$ where $U_\alpha$ contains $\phi$. As a special case of this we have smooth functions $M \to R$: functions whose "coordinate representations" are smooth in some chart.

The compatibility of charts ensures that, if a function is smooth at a point in one chart, it is smooth at that point in all charts. For if $f$ is smooth at $p$ in $\phi_\alpha$, and $\phi_\beta$ is another chart whose domain contains $p$, then we have $f \circ \phi_\beta^{-1} = f \circ (\phi_\alpha^{-1} \circ \phi_\alpha) \circ \phi_\beta^{-1} = (f \circ \phi_\alpha^{-1}) \circ (\phi_\alpha \circ \phi_\beta^{-1})$; $f \circ \phi_\alpha^{-1}$ is smooth by hypothesis, and $\phi_\alpha \circ \phi_\beta^{-1}$ is smooth by compatibility of charts, so $f \circ \phi_\beta^{-1}$ is smooth. If the transition maps are not smooth, as may happen in topological manifolds that are not smooth manifolds, a function may "look smooth" in one chart but not in another chart. Effectively, the definition of $C^k$ functions on manifolds means that, in any choice of local coordinates $(x^1, \dots, x^n)$, the corresponding function $\R^n \to \R$ is $C^k$ in each local coordinate. 

We can then extend this from smoothness at a point to smoothness on a whole manifold in the obvious way: a function is smooth on $M$ if it is smooth at $p$ for every $p \in M$.

### From Manifolds to Manifolds
More generally, a map between manifolds $f: M \to N$ is $C^k$ if the following holds: there exist charts $\phi_\alpha$ on $M$ and $\psi_\beta$ on $N$, such that the composition $\psi_\beta \circ f \circ \phi^{-1}_\alpha$ is $C^k$ wherever they're defined. ($\phi_\alpha^{-1}$ takes you from $\R^n$ to $M$, $f$ takes you from $M$ to $N$, and $\psi_\beta$ takes you from $N$ to $\R^m$, so you get a function $\R^n \to \R^m$.) By much the same arguments as before, if this holds for one chart it holds in all other charts, because the transition functions between charts are smooth. 

We can then define a diffeomorphism of manifolds to be a smooth (in this new sense) function between manifolds with a smooth inverse. It then turns out that charts on smooth manifolds are diffeomorphisms onto their images. 

## Immersions, Submersions, etc.
Let $U$ be an open subset of $\R^n$, and consider a smooth map $f: U \to \R^m$. (Here we're just working in Euclidean space, but everything we say will generalize to arbitrary manifolds, once we have [[Tangent Spaces#Differentials and Tangent Spaces|the right definition of a differential]]. Basically all that's needed to extend our proofs to functions between manifolds is introduce coordinates, and then the proofs go through more-or-less the same. )

When $n = m$, the [[Differential Calculus in Rn#Inverse Function Theorem|inverse function theorem]] gives a connection between the rank of $Df$ and the invertibility of $f$: $f$ is locally a diffeomorphism iff $Df$ is invertible.

Now we look at the $n < m$ case, i.e. maps into a space of lower dimension. Define a *submersion at a point* $p \in U$ as a map where $Df_p$ is surjective (has maximal rank $l$) at $p$, and say that $f$ is a submersion if $Df_p$ is a submersion at all points in the domain. We then have the "local submersion theorem", which says that, if $f$ is a submersion at $p \in U$, then there exist local coordinates $\{x^1, \dots, x^n\}$ around $p$ and $\{y^1, \dots, y^l\}$ around $f(p)$ in which $f(x^1, \dots, x^l, \dots, x^n) = (x^1, \dots, x^l)$. In other words $f$ is, in these coordinates, just a projection onto the first $l$ coordinates; this projection is called the "standard submersion" and we say that $f$ is locally equivalent to the standard submersion.

To do this, we first translate everything in the domain and target so that $p$ is the origin in $\R^n$ and $q$ is the origin in $\R^m$, then use row reduction (equivalent to applying various [[Linear Maps|linear transformations]] to the coordinates) to make $Df_p = (I_m | 0)$, i.e. the first $m$ columns are the $m \times m$ identity matrix. 
Now extend $f$ to a map $\phi: U \to \R^m \times \R^{n - m}$ by $\phi(x^1, \dots, x^n) = (f(x^1, \dots, x^n), x^{m+1}, \dots, x^n)$. Now $D\phi$ looks like $\MatrixTwoTwo{I_m}{0}{0}{I_{n-m}} = I_n$, which is clearly invertible. By the inverse function theorem, $f$ is locally equivalent to the identity: $\phi(x^1, \dots, x^n) = (x^1, \dots, x^n)$. Looking only at the first $m$ coordinates, this shows that $f$ is locally equivalent to the standard submersion: $f(x^1, \dots, x^n) = (x^1, \dots, x^m)$, as desired. 

The $n > m$ case, where we map into spaces of a higher dimension, is similar. An *immersion at a point* and *immersion* are defined similarly to submersions, with the requirement that $Df$ have maximal rank (i.e. be surjective) be replaced with the condition that its kernel be $0$ (i.e. it is injective). Finally, an *embedding* is an immersion that is also a homeomorphism onto its image.
We then have a "local embedding theorem": if $f$ is an immersion at some point $p \in U$, then it is locally equivalent to the "standard embedding" $(x^1, \dots, x^n) \to (x^1, \dots, x^n, 0, \dots, 0)$. 

We can prove this with a similar strategy: we can, by making translations and linear transformations, get $Df$ in a form with the identity matrix $I_n$ on top of some rows of zeros. Now we augment $f$, considering a map $U \times \R^{m - n}$ defined by $\phi(x, z) = f(x) + z$. The differential of this is just the identity, and again applying the inverse function theorem we get that $\phi$ is locally equivalent to $\phi(x^1, \dots, x^l) = (x^1, \dots, x^l)$. In that case $f(x^1, \dots,x^n) = \phi(x^1, \dots, x^n, 0, \dots, 0) = (x^1, \dots, x^n, 0, \dots, 0)$, as desired. 


The above theorems are all special cases of the "constant rank theorem": if $(Df)_p$ has constant rank $r$ for all $p \in U$, then $f$ is locally equivalent to the "standard rank-$r$ map", $f(x^1, \dots, x^n) = (x^1, \dots, x^r, 0, \dots, 0)$, where that vector on the right-hand side has $m$ total entries. Note that this theorem has stronger assumptions: it needs constant rank on a whole neighborhood of $p$, while the inverse function theorem, local submersion theorem, and local embedding theorem only put conditions on $Df$ on a single point. This is because, if $Df$ is surjective at one point, it must be surjective on some neighborhood about that point, and the same goes for injectivity and bijectivity--assuming smoothness or at least continuous differentiability, anyway. 

## Invariance of Dimension
From the above, we can get a proof of the "smooth invariance of dimension": diffeomorphic manifolds have the same dimension, so manifolds with different dimensions cannot be diffeomorphic. Let $M, N$ be manifolds, say with dimensions $m, n$, and let $F: M \to N$ be a diffeomorphism. Then $DF$, in coordinates, is an $m \times n$ matrix, and by the inverse function theorem, it must be an invertible matrix, with $D(F^{-1}) = (DF)^{-1}$. But the only invertible matrices are square matrices, so $m = n$, and so $\dim(M) = \dim(N)$. 

Proving that homeomorphic manifolds have the same dimension [[De Rham Cohomology#Topological Invariance of Dimension|can be done, using the tools of de Rham cohomology]]. 
# Submanifolds
## Embedded Submanifolds
In general we can say that a submanifold of a manifold is a subset that is itself a manifold. But this turns out to be too general, and it is better to consider the following definition. A subset $S$ of an n-dimensional manifold $M$ is a k-dimensional "embedded submanifold" or "regular submanifold" if each point $p \in S$ has a neighborhood $U$ with local coordinates $x^1, \dots, x^n$ such that $S \cap U$ consists of all points of the form $(x^1, \dots, x^k, 0, \dots, 0)$. This is called a "local product chart" or "$S$-adapted chart".

Take for example the unit 2-sphere. If we modify the standard spherical polar coordinates $(\theta, \phi, r)$ to $(\theta, \phi, r-1)$, then these form an adapted chart on the sphere--the third coordinate will be $0$ for all the points with distance $1$ from the origin, i.e. all points in the 2-sphere. 
### Embedding Theorems
It's easy to prove that every smooth, compact manifold can be embedded in $\R^N$ for some sufficiently large $N$. Proof: for every $p \in M$, choose a chart $\phi_p: U_p \to \R^n$, and a "smooth bump function" $\beta_p$ with radius $r_p$ so that $B_{2r_p} \subseteq U_p$, $\beta_p = 1$ everywhere on $B_{r_p}(p)$, and $\beta_p = 0$ everywhere outside of $B_{2r_p}$. The chart domains $U_p$ give an open cover of $M$, and by compactness there exists a finite subcover $U_i$, with corresponding charts $\phi_i$, balls $B_i = B_{r_i}$, and bump functions $\beta_i$. (Say $i = 1, \dots, k$.)

Now define a function $f: M \to \R^N$, with $N = (n+1)k$, by $f(x) = (\beta_1(x), \dots, \beta_R(x), (\beta_1\phi_1)(x), \dots, (\beta_k\phi_k)x)$. (Note that by $\beta_1\phi_1(x)$ we mean the scalar-valued function $\beta_1(x)$ multiplied by the vector-valued function $\phi_k(x)$.) First we show that $f$ is injective. Say $f(p) = f(q)$, and let $i$ be an index with $p \in B_i$, so $\beta_i(p) = 1$; then $\beta_i(q) = 1$ as well, implying $q \in B_i$ as well......end up concluding $\phi_i(p) = \phi_i(q)$ and so $p = q$. Now we also show that $f$ is an immersion. Let $p \in B_i$; the matrix $(Df)_p$, whose entries are of the form $\frac{\partial f^k}{\partial x^l}$, has the submatrix $(\partial \phi_i / \partial x^l)$, which has rank $n$, since $\phi_i$ is a diffeomorphism. This is equal to the dimension of the domain, $Df$ is injective at $p$, so $f$ is a local immersion (by the local immersion theorem) from a compact manifold, and so its image is a closed, embedded submanifold of $\R^N$. 

This theorem gives an embedding into a rather large space, and only works for compact manifolds; the *Whitney embedding theorem* says that every $n$-dimensional smooth manifold embeds into $\R^{2n+1}$, and immerses in $\R^{2n}$. One can also show that this is the best one can do in general: $\R P^n$ cannot be embedded into $\R^{2n}$ or immersed into $\R^{2n-1}$, at least when $n$ is a power of $2$. 
## Immersed Submanifolds
### Compact Immersed Submanifolds
# Level Sets and Regular Values
Let $M$, $N$ be manifolds with dimensions $n, r$, and let $f: M \to N$ be smooth. The preimage of a single point in $N$, i.e. the set of all points $p \in M$ with $f(p) = q$ for some fixed point $q \in N$, is called the "level set of $f$ at $q$", or the "fiber of $f$ at $q$". If, furthermore, $Df_p$ has maximal rank/is surjective for all points $p$ in the level set, $q$ is called a "regular value" of $f$; otherwise it is a "critical value", and the points where $Df$ does not have full rank are called "critical points". 

Consider, for example, the "height function" on the torus, where you take a point on the torus and project to the $z$-axis. Each level set consists of one or two circles cut out from the torus, except at one of four points, where the level set is a single point or a figure-8; these are the four critical points of the function, and the corresponding z-values are the critical values. Clearly those level sets are not manifolds, and all the others are. The situation generalizes, as stated below.
## Regular Value Theorem
Theorem: given a smooth map $f$ as described above, the (nonempty) level set at a regular point $q$ is a closed, embedded submanifold of $M$, of dimension $n - r$.

For some intuition on the dimension, note that $f$, written in coordinates, has $r$ components, and setting $f$ constant imposes $r$ "constraints". If each of those constraints reduces the dimension of the manifold by 1, then imposing all constraints leaves you with $n-r$ dimensions.

Proof: that the level set is closed follows immediately from the fact that $\{q\}$ is closed and $f$ is continuous, so preimages under $f$ of closed sets are closed.

Let $S = f^{-1}(q)$. For each $p \in S$, the local submersion theorem guarantees that there exists a neighborhood $U$ of $p$ with local coordinates $(x^1, \dots, x^n)$ and a neighborhood $V$ of $q$ with local coordinates $(y^1, \dots, y^r)$ so that $f(x^1, \dots, x^n) = (x^1, \dots, x^r)$. Then $S \cap U$ is, in these coordinates, equal to the set of all points $(0, \dots, 0, x^{r+1}, \dots, x^n)$, since while using the local submersion theorem we can choose $p$ and $q$ to be the origin of their respective coordinate systems. Thus $(x^{r+1}, \dots, x^n)$ serve as local coordinates for $S \cap U$. Since this is true for all points in $S$, we have local coordinates/charts covering all of $S$, all with $n - r$ coordinates. Now we show that the transition functions are smooth. On overlaps between open sets in $S$, we have transition maps $\phi_{ab}$, etc.--but these are (restrictions of) the original manifold's transition functions (and since one of these transition functions always maps points in $S$ to points in $S$, the restriction is well-defined). Thus all the choices of local coordinates mentioned earlier in the proof form an atlas for $S$, and so $S$ is a manifold of dimension $n - r$. 

### Finding Manifolds as Level Sets
The regular value theorem gives another way to prove that $S^n$ is an n-dimensional manifold. Namely, define a map $f: \R^{n+1} \to \R$ by $f(x^1, \dots, x^{n+1}) = \sum (x^i)^2$; then $S^n = f^{-1}(1)$. The differential of $f$ is $(2x^1, \dots, 2x^{n+1})$, which has maximal rank $1$ everywhere on $\R^{n+1}$ except the origin. Since $S^n$ does not include the origin, $1$ is a regular value, as is every other positive real number. Thus $S^n$ is an n-dimensional manifold, and so the $n$-sphere with radius $r$  is also a manifold, by the same argument, for any $r > 0$. 

Similar arguments work for [[Quadratic Curves and Quadric Surfaces|zero sets of quadratic polynomials]] more generally. For example, the hyperbola $x^2 - y^2 = 1$ has differential $(2x, -2y)$ which is nonzero for all points in the hyperbola. Similar arguments can be applied to all of the nondegenerate quadric surfaces. However, some degenerate conics (e.g. a pair of intersecting lines) and quadrics (e.g. the double cone) are not manifolds--due, for instance, to the point where the two cones of the double cone meet. Cubics are not necessarily manifolds, since they may have cusps. 

We can regard the standard torus as a set in $\R^4$ defined as the set of all points $(x, y, z, w)$ with $x^2 + y^2 = 1$ and $z^2 + w^2 = 1$ (hence $S^1 \times S^1$). Define a map $\R^4 \times \R^2$ by $(x, y, z, w) \to (x^2 + y^2, z^2 + w^2)$, and then the torus becomes the preimage of $(1, 1)$. Again we can check the differential; it is the $4 \times 2$ matrix with $(2x, 2y, 0, 0)$ in the first row and $(0, 0, 2z, 2w)$ in the second. This has rank $2$ as long as at least one of $x, y$ and at least one of $z, w$ is nonzero, which is certainly true for the torus. Thus $(1, 1)$ is a regular value and the torus is a 2-dimensional manifold (an embedded submanifold of $\R^4$; or one can go further, noting that it's a subset of the closed ball around $0$ of radius $2$ in $\R^4$, which incidentally proves that the torus is compact). A similar argument works for the $n$-torus, considering it as an embedded submanifold of $\R^{2n}$. 

This sort of reasoning generalizes to show that the solution sets of other systems of equations form a manifold. If we have, for instance, a system of $m$ equations $f_i(x_1, \dots, x_n) = c_i$ in $n$ variables, we can define a map $\R^n \to \R^m$ by $(f_1(x_1, \dots, x_n), \dots, f_m(x_1, \dots, x_n))$, and see whether $(c_1, \dots, c_m)$ is a regular value. If so, the solution set of the system will be a manifold of dimension $n-m$. 

# Manifolds With Boundary
A closed disc is almost a manifold, except that, for points in the boundary, there aren't any good charts. We can fix this by, for points on the boundary, letting charts take their values in the "half-space" $H^n$ defined as the set of all points $(x^1, \dots, x^n) \in \R^n$ with $x^1 \leq 0$. The boundary of the half-space is the hyperplane $x^1 = 0$; in $H^2$, for instance, it's the x-axis. (Here we use the convention that $H^n$ is the "left half-space"; some authors use the "upper half-space" instead.)

As a minor technical point, we use the "relative topology" on the half-space, where open sets are open if they're the intersection of an open set in $\R^n$ with the half-space. 

Defining smoothness near boundaries is also difficult. We say that, if $U$ is an open set in the half-space, a map $U \to \R^n$ is smooth if there's a "smooth extension", i.e. an extension onto an open set $\hat{U} \subseteq \R^n$ with $U = \hat{U} \cap H^n$. 

From there, we define an n-dimensional manifold with boundary in the same way as an ordinary manifold, except that the charts have $H^n$ as their codomain, and the transition maps are required to be smooth in the sense above. We then have charts of two types: "interior" charts, whose range doesn't include any of the boundary points in the half-space, and "boundary" charts, whose range does. More formally, we say that the boundary of $M$ is defined as the set of all points $p$ for which there exists some chart mapping $p$ into the boundary; the interior is everything else.

As we would expect, the interior is open, while the boundary is closed. The interior is an ordinary manifold (without boundary). 

An important characterization of boundaries is that, if $M$ is an (oriented) n-dimensional manifold with nonempty boundary, then the boundary $\partial M$ is an (oriented) $n-1$ dimensional manifold with no boundary. Thus $\partial (\partial M)$ is empty. 

Proof: a manifold with boundary is still metrizable, like ordinary manifolds; its metric induces a metric on $\partial M$ which induces the relative topology on $\partial M$. We can then define charts on open sets on $\partial M$ as restrictions of charts on $M$. The range of each restricted chart will be the boundary of $H^n$, which is simply a copy of $\R^{n-1}$. These charts can serve as an atlas making $\partial M$ into an $n-1$-dimensional manifold. 

To get the induced orientation, pick some boundary charts $\phi_a, \phi_b$ on $U_a, U_b$ which overlap. We get a transition function $\phi_b \circ \phi_a^{-1}$ which is a diffeomorphism. Writing it in coordinates and looking at what's happening on the boundary....we get a matrix whose determinant is ... and since the determinant of the whole matrix is positive, the determinant of the differential of the restriction is positive as well. Thus if we started out with an oriented atlas (all transition functions have positive determinant), the atlas we construct on the boundary will also be oriented. 

We can sensibly define the tangent space along the boundary and vector fields on the boundary (as restrictions of sections of the tangent bundle to the boundary). 

A brief lemma about orientation forms: If $M$ is oriented by an $n$-form $\eta$, its boundary $\partial M$ is oriented by the ($n-1$)-form $i_N\eta$ where $N$ is an "outward-pointing vector field" along $\partial M$. 