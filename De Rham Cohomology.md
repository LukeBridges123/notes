# Definition and Motivation
The idea behind de Rham cohomology is that the set of closed forms and the set of exact forms on a manifold $M$ are both vector spaces, with the latter being a subspace of the former. On the simplest manifolds, these are the same. In the more general case, we can get an idea of how much they differ by defining the quotient vector space $H_{dR}^p (M) = Z^p(M)/B^p(M)$, where $Z^p(M)$, $B^p(M$) are the spaces of closed and exact $p$-forms on $M$; this is called the "$p$th de Rham cohomology group" of $M$. Thus we get a sequence of abelian [[Groups|groups]] or [[Vector Spaces|vector spaces]] associated with our manifold. 

De Rham cohomology measures global properties of a manifold. All closed forms are locally exact, so a manifold locally has trivial de Rham cohomology. If we find that a manifold has nontrivial de Rham cohomology, that's something which does not follow solely from local properties of the manifold.

Another way to think of the de Rham cohomology is in terms of the sequence of maps $\Omega_M^0 \to^d \Omega_M^1 \to^d \Omega_M^2 \to^d \dots$. The closed forms are the ones whose exterior derivative is $0$ (i.e. the kernel of $d$ at the $p$th level) and the exact forms are the ones which are the exterior derivative of something (i.e. the range of $d$ at the $p-1$th level). This means that the kernel of one $d$ equals the range of the previous $d$. This sort of situation can be described more generally using the machinery of "exact sequences", described below.
# The Algebra of Cohomology Classes
The elements of $H^p(M)$ are equivalence classes called "cohomology classes". For each closed p-form $\omega$, its cohomology class $[\omega]$ is the set of all $p$-forms of the form $\omega + d\eta$ where $\eta$ is a $(p-1)$-form. We can add cohomology classes and multiply them by scalars, using the same sorts of operations that we usually use with quotient objects: $[\omega] + [\eta] = [\omega + \eta]$, and $a[\omega] = [a\omega]$. 

The direct sum of all de Rham groups, denoted $H^*(M) = \oplus_p H^p(M)$, is an algebra over the real numbers, with a unit; the multiplication operation is the wedge product.

We first observe that if $\omega, \eta$ are closed, then so is $\omega \wedge \eta$, since $d(\omega \wedge \eta) = d\omega \wedge \nu \pm \omega \wedge d\nu = 0 \pm 0 = 0$. We can then define $[\omega] \wedge [\eta] = [\omega \wedge \eta]$, since $\omega \wedge \nu$ is a closed form and has its own cohomology class. We do, however, need to show that this is well-defined, and doesn't depend on the choice of representative. Replace $\omega$ with a different representative $\omega + d\alpha$, and the same for $\eta$, $\eta + d\beta$. Then $[(\omega + d\alpha) \wedge (\eta + d\beta)] = [\omega \wedge \eta + d(\alpha \wedge \eta) + (-1)^p d(\omega \wedge \beta) + d(\alpha \wedge d\beta)]$; all of those $d$ terms go to $0$ in the quotient, so we're left with just $[\omega \wedge \eta]$. 

The unit is the class $[1]$ (thinking of 1 as a constant function, and thus as a 0-form.)

Note also that the wedge product of cohomology classes is called the "cup product" in more general cohomologies. 
## The Pullback
We can also pull back cohomology classes under maps, i.e. a map $F: M \to N$ induces a map $F^*: H^*(N) \to H^*(M)$. This preserves the degree of cohomology classes and has the property $(G \circ F)^* = F^* G^*$ and $I^* = I$ where $I$ is the identity map.

To prove this, we note first that closed forms pull back to closed forms (since, if $d\omega = 0$, then $d(F^*\omega) = F^*(d\omega) = 0$). Second, the pullback is constant on equivalence classes: $[F^*(\omega + d\eta)] = [F^*\omega + d(F^*\eta)] = [F^*\omega]$. Finally, it is an algebra homomorphism: $[F^*(\omega \wedge \eta)] = [F^*\omega \wedge F^*\eta] = [F^*\omega] \wedge [F^*\eta]$. 

The only properties of $F^*$ we used are that it is linear, sends $p$-forms to $p$-forms, and commutes with $d$. Thus any map with those properties induces a map between cohomology classes. 
## de Rham Cohomology as a Functor
Our results above show that the map from a manifold to its de Rham cohomology is a contravariant functor from the category of smooth manifolds (with smooth maps as morphisms) to the category of $\R$-algebras with unit (with algebra homomorphisms as morphisms). From a map $F: M \to N$ we get a map $F^*: H^*N \to H^*M$; the composition property $(G \circ F)^* = F^* G^*$ and identity property $I^* = I$ are just what we need for it to be a functor; and "contravariant" just means that it reverses the direction of morphisms ($F$ goes from $M$ to $N$, $F^*$ goes from $H^*N$ to $H^*M$, rather than $H^*M$ to $H^*N$). 

Some further basic properties of de Rham cohomology: $H^p(M) = 0$ for $p < 0$ and $p > \dim(M)$, because there are no nontrivial $p$-forms for such $p$. 

# Examples
## Balls, Convex Sets, Starlike Sets
Recall that, if $M$ is a "starlike" subset of $\R^n$--a set where there exists a "central" point $p$, such that for any other point $q$ in the set, the line from $p$ to $q$ stays in $M$--then all closed 1-forms on $M$ are exact. Thus we have $H^1(M) = 0$ for all such manifolds. For instance, $H^1(\R^2)$ is trivial, and the same holds for any $\R^n$. It also holds for an arbitrary manifold which is diffeomorphic to a ball.

The Poincare lemma for 1-forms (used above) can be generalized to show that any closed p-form on such a set is exact, so $H^p(M)$ is trivial for all nonzero $p$. 
## Disconnected Manifolds
If $M$ is disconnected, say with connected components $M_1, M_2, \dots$, then we have $H^*(M) = H^*(M_1) \oplus H^*(M_2) \oplus \dots$ (Bring in proof from homework)

## H^0 (M)
As a corollary of the above, $H^0(M) \cong \R^k$ where $k$ is the number of connected components of $M$. No nontrivial $0$-forms on a manifold are exact, so finding $H^0(M)$ reduces to finding all closed 0-forms. These are scalar functions with $df = 0$. On a connected manifold, the only such functions are constant functions, so $Z^0(M) \cong \R$ and $H^0(M) \cong \R$. For a manifold with $k$ connected components we get, by the result above, $H^0(M) \cong \R^k$. 

Alternatively, we can prove this from the fact that $Z^0(M)$ is, in general, the set of locally constant scalar functions. On manifolds, these can be characterized as the functions which are constant on each connected component. Such a function can be completely specified by giving its values on each connected component, and so we get an isomorphism $H^0(M) \cong \R^k$. 
## The Circle
We have $H^p(S^1) = \R$ if $p=0$ or $p=1$, and $H^p(S^1) = 0$ otherwise. We know from the results above that it's $\R$ for $p=0$ and $0$ for $p > \dim(S^1) = 1$. All that's left to show is $H^1(S^1) = \R$. 

Define a map $I$ from the set of closed 1-forms to $\R$ by $I(\omega) = \int_{S^1}\omega$. This is linear (because integration is linear) and surjective (since $I(td\theta) = 2\pi t$, so with the right choice of $t$ we can get any real number). Now we need to find the kernel. Suppose $I(\omega) = 0$. Then, since the integral of $\omega$ about the only closed loop of our space is $0$, $I$ must be exact. The converse holds as well. Thus $I$ is a surjective homomorphism from the set of closed 1-forms to $\R$, whose kernel is the set of exact forms, so by the first isomorphism theorem the quotient of the closed forms by the exact forms (i.e. $H^1(S^1)$) is isomorphic to $\R$. 

# An Axiomatic Characterization of de Rham Cohomology
The following axioms are (almost) sufficient to uniquely characterize de Rham cohomology. 

(1) $H^*(M)$ is a contravariant functor from manifolds to algebras.
(2) the de Rham cohomology $H^p$ of a single point is $\R$ if $p=0$, $0$ otherwise.
(3) de Rham cohomology is invariant under homotopy: if $F$ is homotopic to $G$ then $F^* = G^*$. 
(4) if $M$ is a disjoint union of components $M_\alpha$, then $H^*(M)$ is the direct sum $\oplus_\alpha H^*(M_\alpha)$. 
(5) (Mayer-Vietoris) if $M = U \cup V$ where $U, V$ are open subsets of $M$, then there exists a "long exact sequence" passing through the cohomology groups, $\dots \to H^p(M) \to H^p(U) \oplus H^p(V) \to H^p(U \cap V) \to H^{p+1}(M) \to \dots$ which we will describe below.

We did (1) and (4) above. (2) follows from our result about what $H^0(M)$ looks like, combined with the fact that the dimension of a point is $0$ (so $H^1, H^2,$ etc. don't exist here). (3) and (5)

# Homotopy Invariance

# de Rham Cohomology as a Topological Invariant
Diffeomorphic manifolds have isomorphic de Rham cohomologies. Let $F: M \to N$ be a diffeomorphism with inverse $G: N \to M$. Then $G \circ F = I_M, F \circ G = I_N$. Our induced maps then satisfy $G^* \circ F^* = (F \circ G)^* = I$, and the same for $F^* \circ G^*$. Thus $F^*$ is an isomorphism $H^*(N) \to H^*(M)$ with $G^*$ as its inverse. 

We can get the stronger result that any manifolds with the same "smooth homotopy type" have the same de Rham cohomology. We say that $M, N$ have the same homotopy type if there exist maps $F: M \to N, G: N \to M$ such that $F \circ G, G \circ F$ are both smoothly homotopic to the identity. We can repeat the same proof as above and then use the homotopy axiom ((3) above). 

Combining the results above with the "Whitney approximation theorem" (every continuous homotopy is homotopic to a smooth homotopy) we can say that any smooth manifolds with the same (continuous) homotopy type have the same de Rham cohomology. This means, for example, that homeomorphic manifolds have the same de Rham cohomology. 

# Tools From Homological Algebra
## Cochain Complexes
A cochain complex is a graded vector space $C^* = \oplus_p C^p$ with a sequence of linear maps $d: C^p \to C^{p+1}$ such that $d^2 = 0$. 

(A graded vector space is a vector space $C^*$ which is the direct sum of several vector spaces $C^p$, where to each element of $C^*$ we assign it an integer "degree" $p$ based on which of the $C^p$ it's from.)

We can then define the cohomology $H^*(C^*) = \oplus_p H^p(C^p)$ where $H^p = (C^p \cap \ker(d)) / d(C^{p-1})$. 

This is just an abstraction of the setup above, where $d$ maps $p$-forms to $p+1$-forms, and the $p$th de Rham cohomology is the quotient of the kernel of $d$ (closed forms) by the range of $d$ on the previous space (exact forms). 

A "cochain map" $f: C^* \to D^*$ is a linear map which preserves degree $(f(C^p) \subseteq D^p)$ and commutes with $d$, i.e. $(f \circ d_C = d_D \circ f)$. This induces a map $\overline{f}: H^*(C^*) \to H^*(D^*)$ by $\overline{f}([c]) = [f(c)]$, which is well-defined because $[f[c + d\alpha]] = [fc + d(f\alpha)] = [fc]$, using linearity and the fact that $f$ commutes with $d$.

## Exact Sequences
As a further abstraction of the above, we say that a (finite) sequence of vector spaces $V_i$ and linear maps $L_i: V_i \to V_{i+1}$, $\dots \to V_{i-1} \to^{L_{i-1}} \to V_i \to^{L_i} V_{i+1} \to \cdots$ is an "exact sequence" if $\ker(L_i) = \im(L_{i-1})$, which implies $L_i \circ L_{i-1} = 0$ (as in the case of the exterior derivative, and more generally cochain complexes), as well as that the cohomology $H^i = V_i \cap \ker(L_i) / L_{i-1}(V_{i-1})$ is always trivial (since the "numerator" and "denominator" are always equal). (This is analogous to the situation where every closed form is exact in de Rham cohomology). 

In an exact sequence, we have $\sum (-1)^i \dim(V_i) = 0$. This comes from using rank-nullity and the basic property of an exact sequence $\ker(L_i) = \im(L_{i-1})$, to turn that sum into a telescoping sum.

A *short exact sequence* is an exact sequence involving only 3 vector spaces, $0 \to A \to^L B \to^M C \to 0$. Since $\ker(L)$ is the image of the map $0 \to A$, $L$ is injective; since the kernel of the map $C \to 0$ is $\im(M)$, and is also clearly all of $C$, $M$ is surjective. 

When $A, B, C$ are cochain complexes and $L, M$ are cochain maps, we get induced maps between the cohomology classes $H^p(A) \to H^p(B) \to H^p(C)$ according to a certain diagram....

plus a "connecting homomorphism" $\delta: H^p(C) \to H^p(A)$. 

To define this, we first look at ....

take a $c \in C^p$ with $dc = 0$. Then there exists a (not necessarily unique) $b \in B^p$ with $M(b) = c$, since we have the surjective map $M: B^p \to C^p$. Now take $db$, which is in $B^{p+1}$. Then $M(db) = d(Mb) = dc = 0$, so $b$ comes from something in $A^{p+1}$. Hence there exists $a \in A^{p+1}$ with $L(a) = db$. 

Now, $L(da) = d(La) = ddb = 0$, and since $L$ is injective, we have $da = 0$. Hence $a$ is closed, and so we can take the equivalence class $[a] \in H^{p+1}(A)$, and define $\hat{\delta}(c) = [a]$. 

Now we check that this does not depend on which element of $C^p$ we chose to begin with. ..... all this means that we have a well-defined map $\delta$ on the cohomology classes, defined by $\delta([c]) = [\hat{\delta}(c)]$. 

## Zig-Zag Lemma
From the above, we get the fact that any short exact sequence induces a long exact sequence in cohomology: $H^{p-1}(A) \to H^{p-1}(B) \to H^{p-1}(C) \to H^p(A) \to H^p(B) \to \dots$  

Here the map from $H^p(A) \to H^p(B)$ at each level is $L^*$, the map in cohomology induced by the map $L: A \to B$ in the original short exact sequence; the same goes for the map $H^p(B) \to H^c(C)$. The maps from one "level" to another, $H^p(C) \to H^{p+1}(A)$, are the connecting homomorphism described above. 

The name comes from the diagram (see Tu, page 285) used to define the connecting homomorphism. 
# The Mayer-Vietoris Sequence
Suppose $M = U \cup V$ where $U, V$ are open. Then we have inclusion maps $i_U: U \to M, i_V: V \to M, j_U: U \cap V \to U, j_V: U \cap V \to V$. 

We then have pullback maps going in the opposite direction, $0 \to \Omega_M^* \to^i \Omega_U^* \oplus \Omega_V^* \to^j \Omega_{U \cap V}^* \to 0$. We define $i = (i_U^*, i_V^*)$ and $j(\omega, \eta) = j_U^*\omega - j_V^*\eta$. This is then a short exact sequence. 

Both $i, j$ are linear and commute with $d$; this follow from the corresponding properties of pullbacks. They also preserve degree, which again comes from the properties of pullbacks. Thus they are cochain maps on the cochain complexes $\Omega_M^*$, etc. 

Injectivity of $i$ follows from the fact that, if the restriction to $U$ and restriction to  $V$ of a form $\omega$ are $0$, $\omega$ is $0$ everywhere. $j \circ i = 0$ follows from...

As for surjectivity of $j$, we choose a partition of unity $\psi_U, \psi_V$ suboordinate to the cover $U, V$. 

This suffices to show that, for any $k$, the sequence $0 \to \Omega^k(M) \to^i \Omega^k(U) \oplus \Omega^k(V) \to^j \Omega^k(U \cap V) \to 0$ is a short exact sequence. Per the zig-zag lemma, we then get a long exact sequence in cohomology.

Explicitly, at each "level" we have a sequence $H^k(M) \to^i H^k(U) \oplus H^k(V) \to^j H^k(U \cap V)$. Here we abuse notation a bit to identify $i, j$ with the induced maps on cohomology classes, $i([\omega]) = [i(\omega)]$. Then we have the connecting homomorphism going from $H^k(U \cap V) \to H^{k+1}(M)$. 

In the most common uses of the Mayer-Vietoris sequence, most of the terms will be known to us (and will often be equal to $0$). The terms we want to find will usually be part of exact sequences with only a few terms, like $0 \to A \to B \to 0$, and we can then use the general properties of such sequences (e.g. that certain maps must be isomorphisms, surjections, etc.) to pin down the missing terms. See for instance the example of the $n$-sphere below. 

# More Complicated Examples
## The N-Sphere
The de Rham cohomology $H^k(S^n)$ of the n-sphere is $\R$ when $k=0$ or $k=n$, $0$ otherwise. 

We know that there are closed n-forms on the n-sphere which are not exact (example from homework--a form whose exterior derivative is the volume form on $\R^{n+1}$; using Stokes' theorem to show that the integral of such a form is nonzero). 

We can prove this by induction, using the Mayer-Vietoris sequence. We've already handled the 1-sphere/circle; suppose now that the result also holds for $S^{n-1}$. Let $U$ be the northern hemisphere (plus a bit of the southern hemisphere)--the points $(x_1, \dots, x_{n+1}) \in \R^{n+1}$ on the n-sphere with $x_{n+1} \geq -0.1$, say (the equator is at $x_{n+1} = 0$). Similarly, let $V$ be the southern hemisphere plus a bit of the northern hemisphere. Then $U \cup V = S^n$, $U$ and $V$ are both diffeomorphic to $\R^n$, and $U \cap V$, an "open strip" along the equator, is homotopic to $S^{n-1}$ (by a deformation retraction onto the equator). 

On a typical level of the sequence, we get $H^{p-1}(U \cap V) \to H^p(M) \to H^p(U) \oplus H^p(V) = H^{p-1}(S^{n-1}) \to H^p(S^n) \to H^p(\R^n) \oplus H^p(\R^n) \dots$ By assumption, if $1 < p < n$ then the first term is $0$, and we know the third term is as well, hence $H^p(S^n) = 0$. The lowest level $0 \to H^0(S^n) \to H^0(\R^n) \to H^0(\R^n) \to H^0(S^{n-1}) \to H^1(S^n) \to H^1(\R^n) \oplus H^1(\R^n) \to \dots$ becomes $0 \to \R \to \R^2 \to \R \to H^1(S^n) \to 0 \cdots$ which forces $H^1(S^n) = 0$. 

Finally, at the top level $H^{n-1}(\R^n) \oplus H^{n-1}(\R^n) \to H^{n-1}(S^{n-1}) \to H^n(S^n) \to H^n(\R^n) \oplus H^n(\R^n) \to H^n(S^{n-1}) \to 0$, we get $0 \to \R \to H^n(S^n) \to 0 \to 0 \to 0$ ($H^{n-1}(S^{n-1}) = \R$ coming from the induction hypothesis). In a 2-term exact sequence like $0 \to \R \to H^n(S^n) \to 0$, the middle map is an isomorphism, hence $H^n(S^n) = \R$, as desired. 
## Surfaces
Let $\Sigma_g$ be a standard surface of genus $g$ (i.e. orientable surface with $g$ holes). We have $H^0 = \R$ by connectedness, and $H^2 (\Sigma_g) = \R$ also (by a result mentioned below). 

To find $H^1(\Sigma_g)$, we first smoothly deform $\Sigma_g$ into the sphere with $g$ handles. (N.B. if we detach such a handle from the sphere, we get an "open cylinder" $S^1 \times (-1, 1)$.)

We start out by taking off all the handles; we get a sphere with $2g$ disjoint balls removed, say $B_i(p_i, 2\epsilon)$. Let $U$ be the union of all the $B_i$, and let $M$ be the sphere with smaller balls $B_i(p_i, \epsilon)$ removed. Then $U \cap M$ is a union of $2g$ annuli, which is homotopic to $2g$ copies of $S^1$. 

Then $\chi(U) = 2g$--$U$ has the homotopy type to $2g$ points, and for a union of finitely many points, the only nontrivial cohomology is $H^0$, which has dimension $2g$ in this case. As for $U \cap M$, it is (for similar reasons--it is the union of $2g$ things each homotopic to $S^1$)) $2g\chi(S^1)$, but $\chi(S^1) = 0$.

Thus $\chi(S^2) = \chi(U) + \chi(M) - \chi(U \cap M)$, so $\chi(M) = \chi(S^2) - \chi(U) + \chi(U \cap M) = 2 - 2g + 0 = 2 - 2g$. 

Now we consider gluing on the handles. Letting $H$ be the union of all the handles, we have $\sigma_g = M \cup H$. Since $H$ is a disjoint union of surfaces homotopic to the circle, its Euler characteristic is $0$. 

We have $\chi(\Sigma_g) = \chi(M) + \chi(H) - \chi(M \cap H) = 2 - 2g$. This then gives us $\dim(H^1(\sigma_g)) = 2g$.  

# Related Invariants
## Euler Characteristic
The Euler characteristic of a manifold $M$ is defined to be $\chi(M) = \sum (-1)^p \dim(H^p(M))$. For example, for the $n$-sphere, it is $2$ if $n$ is even and $0$ if $n$ is odd. 

There exists a recurrence for the Euler characteristic, which comes from the Mayer-Vietoris sequence. If $M = U \cup V$ for open $U, V$ then $\chi(M) = \chi(U) + \chi(V) - \chi(U \cap V)$. 

We first need a general result about exact sequences: if $0 \to V_1 \to \dots \to V_n \to 0$ is an exact sequence of vector spaces, then $\sum_i (-1)^i \dim(V_i) = 0$. (Put proof from homework here.)

Now take the long exact sequence induced by the Mayer-Vietoris sequence, $\dots \to H^p(M) \to H^p(U) \oplus H^p(V) \to H^p(U \cap V) \to H^{p+1}(M) \to \dots$ If we take the alternating sum of the dimensions and use $\dim(V \oplus W) = \dim(V) + \dim(W)$ we get $\dim(H^0(M)) - (\dim(H^0(U)) + \dim(H^0(V))) + \dim(H^0(U \cap V)) - \dim(H^1(m)) + (\dim(H^1(U)) + \dim(H^1(V)) - \dim(H^1(U \cap V)) + \dots$ 
Grouping terms we get (note: there was an unimportant reversal of all signs here) $(\dim(H^0(M) - \dim(H^1(M)) + \dots) - (\dim(H^0(U) - \dim(H^1(U)) + \dots) - (\dim(H^0(V)) - \dim(H^1(V)) + \dots) + (\dim(H^0(U \cap V)) - \dim(H^1(U \cap V)) + \dots$ in other words $\chi(M) - \chi(U) - \chi(V) + \chi(U \cap V)$. On the other hand, by the lemma above, our original alternating sum of dimensions was $0$. Thus $\chi(M) - \chi(U) - \chi(V) + \chi(U \cap V) = 0$ or $\chi(M) = \chi(U) + \chi(V) - \chi(U \cap V)$, as desired. 


...result: for compact, oriented manifold, $H^N(M) = \R$. 

# Misc. Applications
## Brouwer Fixed Point Theorem
First, a lemma.
Let $\ol{B}$ be the closed unit ball in $\R^{n+1}$. Then there exists no smooth map from $\ol{B}$ to its boundary (i.e. the $n$-sphere) which is the identity on the boundary. For, if there exists such a map $f$, then ... sequence of maps $\partial \ol{B} \to \ol{B} \to \partial \ol{B}$... (first is the inclusion map)...induces maps in cohomology, from $\R \to 0 \to \R$, which can't happen if $n > 1$...

Now we can state and prove the Brouwer fixed point theorem: every smooth map $f: \ol{B} \to \ol{B}$ has a fixed point, i.e. a point $p$ with $f(p) = p$. (In fact, this holds more generally for continuous maps.)

For example, in the 1-dimensional case, $\ol{B} = [0, 1]$; given a function $f$, we can consider $g(x) = f(x) - x$. Then $g(0) \geq 0$ and $g(1) \leq 0$, so by the intermediate value theorem we must have $g(x) = 0$ somewhere, so $f(x) = x$ somewhere. 

More generally, if $f$ has a no fixed point, then we can consider the ray going from $x$ to $f(x)$, which will intersect $\partial \ol{B}$ at some unique point $\phi(x)$. This ray is given by $x + tu$ where $u = (x - f(x))/||x - f(x)||$. (Again, this is well-defined because $x \neq f(x)$.)

We then have $1 = |x + tu|^2 = t^2 + 2t x \cdot u + |x|^2$, so $t = x \cdot u + \sqrt{1 - |x|^2 + (x \cdot u)^2}$. This means that $t$ depends smoothly on $x$, so $\phi(x)$ is a smooth function of $x$. It is also the identity on $\partial \ol{B}$. But by the previous lemma, there is no smooth map from $\ol{B}$ to itself which is the identity on the boundary. 

## Topological Invariance of Dimension
Using only the inverse function theorem and some basic theorems about differentials, we were able to prove that [[Manifolds#Invariance of Dimension|diffeomorphic manifolds have the same dimension]]. We can now prove the stronger result that homeomorphic manifolds have the same dimension, using the fact that the de Rham cohomology of "punctured" $n$-dimensional Euclidean space is different for different $n$.

If an $m$-dimensional manifold $M$ is homeomorphic to an $n$-dimensional manifold $N$, then about each point $p \in M$, there exists a neighborhood $U$ which is homeomorphic to $\R^m$ (using the charts on $M$) and homeomorphic to $\R^n$ (by composing the homeomorphism $M \to N$ with a chart on $N$). We can then compose the inverse of the homeomorphism $M \to \R^m$ and the homeomorphism $M \to \R^n$ to get a homeomorphism $f: \R^m \to \R^n$. This in turn gives us a homeomorphism from "punctured $m$-dimensional space", $\R^m \backslash \{0\}$, to "punctured $n$-dimensional space", $\R^n \backslash \{0\}$. By the topological invariance of de Rham cohomology, the two spaces have the same cohomology groups. But recall that $\R^m \backslash \{0\}$ has the homotopy type of $S^{m-1}$, so its cohomology groups are $H^0(S^{m-1}) = H^{m-1}(S^{m-1}) = \R$, $H^p(S^{m-1}) = 0$ otherwise; the same goes for $S^{n-1}$. The only way to ensure that the two spaces have the same de Rham cohomology is if $m=n$, so that $H^{m-1}(\R^m \backslash \{0\}) = H^{n-1}(\R^n \backslash \{0\})$. Thus if $M$ is homeomorphic to $N$, then $\dim(M) = \dim(N)$.
