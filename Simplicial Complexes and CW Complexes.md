# CW Complexes
An n-cell is an n-dimensional ball with boundary. A 0-cell is a point, a 1-cell is a closed interval or segment, a 2-cell is a closed disc, and so on. A CW complex is, roughly, found by gluing together cells of different dimensions.

To form a CW complex $X$ we start with its "0-skeleton" $X^0$, which is simply a discrete set of points. Then we attach 1-cells to these points, forming a "1-skeleton" $X^1$, which can be thought of as a graph. We continue inductively: given an $n-1$ skeleton $X^{n-1}$, we form an n-skeleton by taking n-cells $e_\alpha^n$ and attaching them via "attaching maps" $\phi_\alpha: \partial e^n_\alpha \to X^{n-1}$. (Recall that $\partial e_\alpha^n$ is just an $n-1$-sphere.) These tell you which points on the boundary of each n-cell will get identified to which points on the $n-1$ skeleton. $X^n$ is then equal to the disjoint union of $X^{n-1}$ and the $e_\alpha^n$, quotiented by the equivalence relation... Finally, we take $X = \cup_n X^n$. 

Typically we will work with finite-dimensional complexes, where we stop adding $m$-cells for $m \geq n$. In principle, though, we can continue this process forever and end up with an infinite-dimensional complex consisting of cells of arbitrarily large dimension. 

Many familiar spaces can be constructed as CW complexes. If we take two 1-cells and attach them at their endpoints we get the circle $S^1$; if we then attach two 2-cells, one on the top and one on the bottom, we get the sphere $S^2$. This is not the only way to do it. We can take a single point and a single 2-cell, and then collapse the whole boundary of the 2-cell to the single point. 

For a more complicated construction, take the torus $T$. The 0-skeleton $T^0$ is a single point, and $T^1$ is a wedge of 2 circles, joined at that single point. Then $T^2$ is a single 2-cell glued to the bouquet as follows...
## Fundamental Groups of Complexes
We now show how to find the fundamental group of an arbitrary CW complex. First we show that, in some sense, the fundamental group is "blind" to higher-dimensional cells. That is, if we obtain $Y$ from $X$ by attaching $n$-cells for a fixed $n > 2$, then the inclusion $X \to Y$ induces an isomorphism of fundamental groups. 

Proof: first we handle the simplest case of attaching a single 3-cell. Let $\phi$ be the map $S^2 \to X$ which attaches the 3-cell to $X$, so $Y = X \cup D^3 / (\phi(x) \cong x)$ for $x \in S^2$. Choose open and path-connected sets $A, B$ such that $A$ deformation retracts to $D^3$ and $B$ deformation retracts to $X$... then $A \cap B$ is $S^2$ which has a trivial fundamental group. By van Kampen's theorem, $\pi_1$ of the result is isomorphic to $\pi_1(A) * \pi_1(B) = \pi_1(D^3) * \pi_1(X) = \pi_1(X)$. 

### Fundamental Groups of Graphs
Let $X$ be a connected graph; then $\pi_1(X)$ is a free group. 

The idea is to find a maximal tree $T$ in $X$ (i.e. a subgraph of $X$, containing all vertices of $X$, which is a tree, i.e. contains no cycles). Then $T$ will be contractible, and $\pi_1(X)$ will be isomorphic to $\pi_1(X/T)$, where $X/T$ is $X$ with $T$ collapsed to a point. Once this is done you'll get a wedge of circles, whose fundamental group is free. 

To do this we will need the following intuitive lemma: let $A$ be a subcomplex of a complex $X$; if $A$ is contractible, then the quotient map $X \to X/A$ is a homotopy equivalence.

...

Now we handle attaching 2-cells to a wedge of circles...attaching a 2-cell is equivalent to adding a relation, i.e. setting a word to $1$. This is because the attaching map is a map $S^1 \to X^1$, i.e. loop in the 1-skeleton, so the image corresponds to a word...

This then gives us a way to realize any group as the fundamental group of a 2-dimensional complex. We just choose a presentation with generators $g_\alpha$ ($\alpha \in A$) and relations $r_\beta$ ($\beta \in B$). As the 1-skeleton we use the (possibly infinite) wedge $\vee_\alpha S^1$, which has fundamental group $\pi_1(X^1) = *_\alpha \Z$. Then for each relation $r_\beta$, add a 2-cell along the loops in $X^1$ corresponding to the word $r_\beta$. 