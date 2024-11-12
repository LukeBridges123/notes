# Definition and Motivation
The idea behind de Rham cohomology is that the set of closed forms and the set of exact forms on a manifold $M$ are both vector spaces, with the latter being a subspace of the former. On the simplest manifolds, these are the same. In the more general case, we can get an idea of how much they differ by defining the quotient vector space $H_{dR}^p (M) = Z^p(M)/B^p(M)$, where $Z^p(M)$, $B^p(M$) are the spaces of closed and exact $p$-forms on $M$; this is called the "first de Rham cohomology group" of $M$. 

De Rham cohomology measures global properties of a manifold. All closed forms are locally exact, so a manifold locally has trivial de Rham cohomology. If we find that a manifold has nontrivial de Rham cohomology, that's something which does not follow solely from local properties of the manifold.

Another way to think of the de Rham cohomology is in terms of the sequence of maps $\Omega_M^0 \to^d \Omega_M^1 \to^d \Omega_M^2 \to^d \dots$. The closed forms are the ones whose exterior derivative is $0$ (i.e. the kernel of $d$ at the $p$th level) and the exact forms are the ones which are the exterior derivative of something (i.e. the range of $d$ at the $p-1$th level). This means that the kernel of one $d$ equals the range of the previous $d$. This sort of situation can be described more generally using the machinery of "exact sequences".
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

(re: homotopy, two functions are homotopic if there is a ....)

(4) if $M$ is a disjoint union of components $M_\alpha$, then $H^*(M)$ is the direct sum $\oplus_\alpha H^*(M_\alpha)$. 
(5) (Mayer-Vietoris) if $M = U \cup V$ where $U, V$ are open subsets of $M$, then there exists a "long exact sequence" in $H^*(M)$, which we will describe below.

We did (1) and (4) above. (2) follows from our result about what $H^0(M)$ looks like, combined with the fact that the dimension of a point is $0$ (so $H^1, H^2,$ etc. don't exist here). 

For (3)...

# de Rham Cohomology as a Topological Invariant
Diffeomorphic manifolds have isomorphic de Rham cohomologies. Let $F: M \to N$ be a diffeomorphism with inverse $G: N \to M$. Then $G \circ F = I_M, F \circ G = I_N$. Our induced maps then satisfy $G^* \circ F^* = (F \circ G)^* = I$, and the same for $F^* \circ G^*$. Thus $F^*$ is an isomorphism $H^*(N) \to H^*(M)$ with $G^*$ as its inverse. 

We can get the stronger result that any manifolds with the same "smooth homotopy type" have the same de Rham cohomology. We say that $M, N$ have the same homotopy type if there exist maps $F: M \to N, G: N \to M$ such that $F \circ G, G \circ F$ are both smoothly homotopic to the identity. We can repeat the same proof as above and then use the homotopy axiom ((3) above). 

Combining the results above with the "Whitney approximation theorem" (every continuous homotopy is homotopic to a smooth homotopy) we can say that any smooth manifolds with the same (continuous) homotopy type have the same de Rham cohomology.