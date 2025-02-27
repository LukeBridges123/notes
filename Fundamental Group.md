# Definition
The fundamental group $\pi_1(X, x_0)$ is a group associated with any "pointed space", i.e. topological space $X$ with a "basepoint" $x_0$ singled out. It is the set of loops based at $x_0$, under the equivalence relation given by [[Homotopy]] of loops. The group operation is given by composition of loops: tracing out one loop, then another, gives you another loop. 

More formally, recall that a path is a continuous function $[0, 1] \to X$ (usually we will denote $[0, 1]$ by $I$ in what follows); a loop is a path with $f(0) = f(1)$. If $f(0) = x_0$ we say that the loop is based at $x_0$. Recall also that a homotopy of paths is a homotopy relative to $\{0, 1\}$ ("with endpoints fixed"); a homotopy of loops is the same ("with the basepoint fixed")--when deforming the loop, we always keep its start and end fixed at $x_0$. 

Then the homotopy of loops gives an equivalence relation on loops; thus for any loop $f$ based at $x_0$ we can speak of its equivalence class $[f]$. 

We can define an operation on loops based at $x_0$ as follows. Let $f: I \to X$ and $g: I \to X$ be two such loops; then let $fg: I \to X$ be given by $(fg)(t) = f(2t)$ if $0 \leq t \leq 1/2$, $(fg)(t) = g(2t - 1)$ if $1/2 \leq t \leq 1$. This is well-defined at $t = 1/2$ since $f(1) = g(0) = x_0$. Also, $(fg)(0) = f(0) = x_0$ and $(fg)(1) = g(1) = x_0$, so this composition gives another loop based at $x_0$. Essentially the same strategy gives us a way to compose paths: sticking together a path from $a$ to $b$ and a path from $b$ to $c$ in this way gives us a path from $a$ to $c$. 

The operation on loops has few nice algebraic properties--it is not associative, for example. But once we pass to equivalence classes, it does give a group operation. Define $[f][g] = [fg]$. We first check that this is well-defined by showing that it does not depend on the choice of representative for $[f]$ and $[g]$: if $f \simeq f'$ and $g \simeq g'$ then $fg \simeq f'g'$. We will do this for arbitrary paths, not just loops. Let $f$ be a path from $a$ to $b$ and $g$ be a path from $b$ to $c$. Let $F$ be a homotopy from $f$ to $f'$ and let $G$ be a homotopy from $g$ to $g'$. Now define a homotopy $H$ by: $H_t(s) = F_{t}(2s)$ for $0 \leq s \leq 1/2$; and $H_t(s) = G_t(2s - 1)$ otherwise. Note that this fixes $a, b, c$ for all values of $t$ (i.e. fixes both the "endpoints" and "midpoint"). 
## Verification of the Group Axioms
We now show that the operation on equivalence classes of loops based at $x_0$ given by $[f][g] = [fg]$ is associative, has an identity element, and is invertible. (Strictly speaking we need to check closure, but this follows automatically from the fact that the composition of two loops at $x_0$ is another loop at $x_0$, and the fact that the operation is well-defined on equivalence classes.)

The identity element is the homotopy class of the constant path given by $c(t) = x_0$ for all $t$. Then the claim is that $[f][c] = [fc] = [f]$ for all $f$, and the same for $[c][f]$. Thus we need to prove that $fc$ is homotopic to $f$. Explicitly, $(fc)(t) = f(2t)$ for $0 \leq t \leq 1/2$, $(fc)(t) = x_0$ for $1/2 \leq t \leq 1$. Observe that $fc$ is actually just a reparameterization of $f$: it is equal to $f \circ r$ where $r: I \times I$ is given by $r(t) = 2t$ for $0 \leq t \leq 1/2$, $r(t) = 1$ otherwise. By a lemma proved in [[Homotopy#Homotopy of Maps]], $f$ is homotopic to any reparameterization of $f$. Thus $f \simeq fc$ and so $[f] = [fc]$, as desired. Essentially the same argument shows that $[c][f] = [f]$. Thus $[c]$ is an identity element. 


For associativity, we need to show $([f][g])[h] = [f]([g][h])$ for all $f, g, h$. In other words $[(fg)h] = [f(gh)]$. The path on the left goes through $f$ for $t \in [0, 1/4]$, $g$ for $t \in [1/4, 1/2]$, and $h$ for $t \in [1/2, 1]$; the path on the right does the same for $f$ for $t \in [0, 1/2]$, $g$ for $t \in [1/2, 3/4]$, and $h$ for $t \in [3/4, 1]$. Thus the two paths go through the same points, just at different speeds, so we should expect one to be a reparameterization of the other. 

The inverse of $[f]$ is given by $[\ol{f}]$ where $\ol{f}$ is "$f$ run backwards": $\ol{f}(t) = f(1 - t)$. We have $(f\ol{f})(t) = f(2t)$ for $0 \leq t \leq 1/2$, $(f\ol{f})(t) = \ol{f}(2t - 1) = f(1 - 2t + 1) = f(-2t + 2)$ otherwise. .....

## Different Basepoints
It is false in general that $\pi_1$ does not depend on the choice of basepoint. If, for example, the space has multiple (path-)connected components, $\pi_1$ based in one component could be different from $\pi_1$ based in another. On the other hand, for points $x, y$ in the same path component, $\pi_1(X, x)$ is isomorphic to $\pi_1(X, y)$. 

Letting $\gamma$ be a path from $x$ to $y$, the isomorphism is given by "conjugation by $\gamma$". If $f$ is a loop based at $y$, then $B(f) = [\gamma^{-1}f\gamma]$ is a loop based at $x$. 

First we show that this is well-defined by showing that, if $[f] = [f']$, then $B(f) = B(f')$. Let $f_t$ be a homotopy from $f$ to $f'$. Then $\gamma^{-1}f_t \gamma$ is a homotopy from $\gamma^{-1}f\gamma$ to $\gamma^{-1}f' \gamma$. 

Next we show that $B$ is a homomorphism, i.e. $B(fg) = B(f)B(g)$. Note that $B(f)B(g) = [\gamma^{-1}f\gamma][\gamma^{-1} g \gamma] = [\gamma^{-1}f\gamma\gamma^{-1} g \gamma]$. $\gamma\gamma^{-1}$ is homotopic to a constant map, so $[\gamma^{-1}f\gamma\gamma^{-1} g \gamma] = [\gamma^{-1}f g \gamma]= B(fg)$. 

Finally, we show that this is invertible. The inverse $B^{-1}$ is given by "conjugation by $\gamma^{-1}$"...
# Examples
## The Circle
One of the simplest spaces with a nontrivial fundamental group is the circle, whose fundamental group is isomorphic to $\Z$. An isomorphism is given by sending $n$ to $[\omega_n]$ where $\omega_n$ is the path given by $\omega_n(s) = (\cos(2\pi n s), \sin(2\pi n s))$. (In other words $\omega_n$ goes around the circle $|n|$ times at constant speed. Switching the sign of $n$ changes the direction of the path, which is counterclockwise for positive $n$ and clockwise for negative $n$.) 

The proof involves "lifting" paths on the circle to paths in $\R$. $S^1$ is "covered" by $\R$ with covering map $p(s) = (\cos(2\pi s), \sin(2\pi s))$; see [[Covering Spaces]] for the relevant background. $p$ can be visualized by twisting the real line into an infinite helix above and below $S^1$; $p$ projects the helix down onto the circle. 

To verify that $p$ is a covering map, we look at small segments of the circle: sets of points of the form $(\cos(2\pi (s + h)), \sin(2\pi(s + h)))$ for all $|h| < \epsilon$. $p$ projects infinitely many open intervals $U_n = (n(s - h), n(s + h))$ onto such a segment; each is homeomorphic to the segment of a circle. 

$\omega_n$ lifts to a path in $\R$ in the sense that there exists a map $\tilde{\omega}_n$ with $p \circ \tilde{\omega}_n = \omega_n$. This path is given by $\tilde{\omega}_n(s) = ns$, which goes from $0$ to $n$ as $s$ goes from $0$ to $1$. 

...

We need to show that the map $\phi$ given by $\phi(n) = [\omega_n]$ is a bijective group homomorphism. 

First we show that it is a homomorphism. In particular $\phi(m + n) = [\omega_{m+n}] = [\omega_m][\omega_n]=\phi(m)\phi(n)$. Let $\tau_m: \R \to \R$ be the translation $\tau_m(x) = x + m$. Note first that $[\omega_{m+n}]$ is equal to $[p \circ \tilde{\omega}_{m+n}]$. On the other hand $\phi(m)\phi(n) = [\omega_m][\omega_n] = [\omega_m\omega_n]$, the homotopy class found by composing $\omega_m$ and $\omega_n$. This is equal to $[p\circ (\tilde{\omega}_m(\tau_m \circ \tilde{\omega}_n))]$: the path found by concatenating the lift of $\omega_m$ with a translated version of the lift of $\omega_n$, then projecting all that down to the circle. $\tilde{\omega}_m(\tau_m \circ \tilde{\omega}_n)$ is a path from $0$ to $m+n$ in $\R$, and since all paths in $\R$ with the same endpoints are homotopic, it is homotopic to $\tilde{\omega}_{m+n}$. Thus $[\tilde{\omega}_{m+n}] = [\tilde{\omega}_m(\tau_m \circ \tilde{\omega}_n)]$ (as equivalence classes of paths in $\R$). The projection map $p$ respects homotopy classes, so $[p \circ (\tilde{\omega}_{m+n})] = [p \circ (\tilde{\omega}_m(\tau_m \circ \tilde{\omega}_n))]$ Thus $\phi(m+n) = \phi(m)\phi(n)$, given our earlier characterizations of $\phi(m+n)$ and $\phi(m)\phi(n)$. 

Before we prove that $\phi$ is a bijection we will state two properties of covering spaces. Let $Y$ be a covering space of $X$ with covering map $p$. 

The first property is that any path $f$ in $X$ starting at $x_0$, and a point $\tilde{x}_0 \in p^{-1}(x_0)$, there exists a path (unique up to homotopy) $\tilde{f}$ in $Y$ which starts at $\tilde{x}_0$, and for which $p \circ \tilde{f} = f$. In other words, given base points $x_0$ and $\tilde{x}_0$ in $X$ and $Y$, there exists a unique lift of $f$ starting at $\tilde{x}_0$. 

The second is that, given a homotopy of paths $f_t$ in $X$ starting at $x_0$, and a point $\tilde{x}_0$ as before, there is a unique "lifted homotopy" $\tilde{f}_t$ between $\tilde{f}_0$ and $\tilde{f}_1$ starting at $\tilde{x}_0$. 

The first property tells us that, given any path in $S^1$ starting at $(1, 0)$, it will lift to a unique path in $\R$ starting at $0$. 

We now use these to prove that $\phi$ is surjective. Let $[f]$ be any loop in $S^1$ based at $(1, 0)$. By the above, there exists a unique lift of $f$ to a path $\tilde{f}$ in $\R$ with $\tilde{f}(0) = 0$. Since $f(1) = (1, 0)$ as well and $f(1) = p \circ \tilde{f}(1)$, $\tilde{f}(1)$ must be an integer $n$, since those are the only points in $\R$ that $p$ sends to $(1, 0)$. Thus $\tilde{f}$ is a path from $0$ to $n$, which is homotopic to any path from $0$ to $n$, including $\tilde{\omega}_n$. But then $[f] = [p \circ \tilde{\omega}_n] = [\omega_n]$. Thus any path $f$ is homotopic to a path $\omega_n$, and so any equivalence class $[f]$ is in the range of $\phi$ (equal to some $[\omega_n]$). 

Now we show that $\phi$ is injective. Suppose that $\phi(m) = \phi(n)$, so that $[\omega_m] = [\omega_n]$. Let $f_t$ be a homotopy from $f_0 = \omega_m$ to $f_1 = \omega_n$. Then $\omega_m, \omega_n$ lift uniquely (up to homotopy) to paths $\tilde{\omega}_m, \tilde{\omega}_n$ starting at $0$ with a unique "lifted homotopy" $\tilde{f}_t$ taking $\tilde{\omega}_m$ to $\tilde{\omega}_n$. Note however that $\tilde{f}_t$, as a path homotopy, fixes endpoints, so $\tilde{\omega}_m$ and $\tilde{\omega}_n$ have the same last endpoint, i.e. $\tilde{\omega}_m(1) = \tilde{\omega}_n(1)$, so $m = n$. 
## Product Spaces
The fundamental group respects products: if $X, Y$ are path-connected spaces then $\pi_1(X \times Y) = \pi_1(X) \times \pi_1(Y)$. For example, the fundamental group of the torus $S^1 \times S^1$ is equal to $\Z^2$, and more generally the fundamental group of the $n$-torus $S^1 \times \dots \times S^1$ ($n$ times) is $\Z^n$. Generators of $\pi_1(S^1 \times S^1)$ are given by circles along the lines that get glued together when constructing the torus from the square. 
# Induced Homomorphisms
Continuous functions between spaces induce group homomorphisms between those spaces' fundamental groups. That is, letting $q: X \to Y$ be continuous, say with $q(x_0) = y_0$, we get a map $q_*: \pi_1(X, x_0) \to \pi_1(Y, y_0)$ which is a group homomorphism, $q_*([f][g]) = q_*[f]q_*[g]$. This induced map is given by $q_*[f] = [q \circ f]$. 
## Functorality of the Fundamental Group
If $q: X \to Y$ and $p: Y \to Z$ are continuous, then $(p \circ q)_* = p_* \circ q_*$; furthermore, $\operatorname{id}_*$ (i.e. the map induced by the identity function $X \to X$) is the identity map $\pi_1(X) \to \pi_1(X)$. 

These are precisely the properties needed to make the fundamental group a (covariant) functor from the category of pointed topological spaces to the category of groups. 

It follows from these properties that, if $q$ is a homeomorphism, then $q_*$ is a group isomorphism. Thus $\pi_1$ is a topological invariant in the sense that homeomorphic spaces have isomorphic fundamental groups. 
## Homotopy Invariance of the Fundamental Group
The fundamental group is not only a topological invariant but a homotopy invariant, i.e. spaces which are homotopy equivalent have isomorphic fundamental groups. That is, if $q: X \to Y$ is a homotopy equivalence then $q_*$ is an isomorphism, for any choice of basepoint in $X$. 

Proof: let $p$ be a homotopy inverse of $q$, so $p \circ q \simeq \operatorname{id}$ and the same for $q \circ p$. Then $\operatorname{id} = (p \circ q)_* = p_* \circ q_*$, and similarly $\operatorname{id} = q_* \circ p_*$. Thus $p_*, q_*$ are inverses, so $q_*$ is an invertible homomorphism, i.e. an isomorphism. 

Again, note that this is really a general categorical property: a functor maps isomorphisms to isomorphisms.
## Induced Homomorphisms and Retractions
Induced homomorphisms give us a way to show that one space is not a retract of another. (That is, not only is it not a deformation retract, it is not even a retract in the more general sense.) If $A \subseteq X$ and there is a retraction $r: X \to A$, then letting $i$ be the inclusion map $A \to X$, $i_*$ is injective. 

Proof: if $r$ is a retraction then the restriction of $r$ to $A$ is the identity on $A$. Thus $r \circ i: A \to A$ is the identity (since $r$ fixes all points in $A$). By functorality, $r_* \circ i_*$ is the identity, so $i_*$ has a left inverse, which means $i_*$ is injective. 

This gives another way to show that $D^2$ does not retract onto $S^1$: there is no injective map from $\pi_1(S^1) = \Z$ to $\pi_1(D^2) = \{0\}$. A similar argument shows more generally that a space with a trivial fundamental group cannot retract onto a subspace with a nontrivial fundamental group. 

A more subtle way to apply this is with arguments like the following. Take the solid torus $X = S^1 \times D^2$ and let $A$ be a circle that bounds one of the discs. Then both $A$ and $S^1 \times D^2$ have fundamental group $\Z$, so arguments like the above break down. But note that, when we embed $A$ in $S^1 \times D^2$, it becomes contractible: we can shrink it to a point through the disc that it bounds. This means that, under the inclusion $i: A \to X$, all loops in $A$ get sent to trivial loops in $X$. But $\pi_1(A)$ includes nontrivial loops, so $i_*: \pi_1(A) \to \pi_1(X)$ is not injective. 

The general form of such arguments is: if a subspace $A \subseteq X$ is not contractible on its own, but becomes contractible when you embed it in $X$, the induced map $\pi_1(A) \to \pi_1(X)$ is not injective, and so $X$ does not retract onto $A$. 
# Van Kampen's Theorem
Van Kampen's theorem plays a similar role to the Meyer-Vietoris sequence in cohomology: it gives us a way to compute $\pi_1(X)$ by breaking $X$ into a union of spaces with simpler fundamental groups. 
## Factorization of Paths in a Union
As a preliminary lemma, let $X = A \cup B$ where $A, B$ are both open and path-connected, and $A \cap B$ is path-connected as well. Then any loop $f$ based at $x_0 \in A \cap B$ can be written as a product $[f] = [f_1][f_2]\cdots [f_k]$ of loops where each $f_i$ likes entirely in $A$ or entirely in $B$. 

Proof: start by decomposing $f$ into path segments. Say that $f$ is the concatenation of paths $\gamma_1, \dots, \gamma_k$ where the endpoints of each path are in $A \cap B$. For each $i$, pick a path $\delta_i$ going from the final endpoint of $\gamma_i$ to $x_0$ (this is possible since $A \cap B$ is path-connected). Then $f \simeq \gamma_1 \delta_1 \ol{\delta}_1 \gamma_2 \delta_2 \ol{\delta}_2 \dots \ol{\delta}_{k-1}\delta_k$ since each of the $\delta_i \ol{\delta}_i$ can be shrunk to a loop. But $\gamma_1 \delta_1$ is a loop in $A$, $\ol{\delta}_1 \gamma_2 \delta_2$ is a loop in $B$, and so on. Thus $[f]$ is a product of elements of $\pi_1(A)$ and $\pi_1(B)$. 
### Higher-Dimensional Spheres
This allows us to compute the fundamental group of $S^2$ and higher-dimensional spheres. Let $A$ be $S^n$ with the north pole removed and $B$ be $S^n$ with the south pole removed. For $n \geq 2$, $A \cap B$ will be path-connected, and so every element of $\pi_1(S^n)$ is a product of elements of $\pi_1(A)$ and elements of $\pi_1(B)$. Both of those groups are trivial, though, since $A, B$ are both homeomorphic to $\R^n$, so $\pi_1(S^n)$ is trivial. This breaks down for $S^1$, where removing two points leaves a disconnected set. 
## Wedge Sum
The "wedge sum" $A \vee B$ of two (disjoint) topological spaces is what you get when you "glue" $A$ and $B$ at one point. That is, you take the disjoint union of $A$ and $B$, pick points $x_0 \in A$ and $y_0 \in B$, and quotient by the equivalence relation $x_0 \cong y_0$. 

From here on out, let $x_0$ be the point where $A, B$ are joined. Intuitively we would expect that any loop in $A \vee B$ based at $x_0$ is a product of loops in $A$ based at $x_0$ and loops in $B$ based at $y_0$. Thus $\pi_1(A \vee B, x_0)$ is the set of all products of the form $f_1 f_2 \cdots f_n$ where all the $f_i$ are either elements of $\pi_1(A, x_0)$ or $\pi_1(B, y_0)$. 

### Free Product of Groups
The algebraic way to represent this situation is with the "free product" of groups. If $G_1, G_2$ are groups then we define their "free product" $G_1 * G_2$ to be the set of all words $g_1g_2\cdots g_n$ where: each $g_i$ is in $G_1$ or $G_2$; no $g_i$ is equal to the identity in $G_1$ or $G_2$; and subsequent elements $g_ig_{i+1}$ are not both in the same group. Intuitively these generators are "reduced words": strings of elements of $G_1, G_2$ where we have combined and cancelled as many elements as possible. The operation in $G_1 * G_2$ is given by concatenation of words and cancellation wherever possible. The identity is the "empty word". Inverses are given as you might expect: the inverse of $g_1g_2$ is $g_2^{-1}g_1^{-1}$, and so on for longer strings. 

For example, $\Z * \Z$ is the free group on two generators $\langle a, b \rangle$. 

This generalizes in the obvious way to free products of many groups. The free product of $n$ copies of $\Z$ is the free group on $n$ generators $\langle a_1, \dots, a_n \rangle$. 

The free product can also be described in terms of a universal property: if $G_1, G_2, H$ are groups for which there exist homomorphisms $f_1: G_1 \to H$ and $f_2: G_2 \to H$, then there exists a unique homomorphism $f: G_1 * G_2 \to H$ such that a certain diagram commutes... 
## Statement of Van Kampen's Theorem
Suppose $A, B, A \cap B$ are open, path-connected sets. Let $X = A \cup B$. Then, letting $x_0 \in A \cap B$, we have $\pi_1(X, x_0) = \pi_1(A) * \pi_1(B) / N$ where where $N$ is the set of products $(i_A)_*([\gamma]) (i_B)_*([\gamma])$ where $i_A, i_B$ are the inclusions of $A \cap B$ into $A$ and $B$, and $[\gamma] \in \pi_1(A \cap B)$.  ...

The most general form of Van Kampen's theorem is as follows. Let $X = \cup_\alpha A_\alpha$ where the $A_\alpha$ are path-connected open sets each containing a basepoint $x_0$. Suppose further that all intersections $A_\alpha \cap A_\beta$ are path-connected. Then the homomorphism $\phi: *_\alpha \pi_1(A_\alpha) \to \pi_1(X)$ is surjective. Furthermore, if all threefold intersections $A_\alpha \cap A_\beta \cap A_\gamma$ are path-connected, then the kernel of $\phi$ is the subgroup generated by products of the form... $\pi_1(X)$ is then the quotient of the free group by that subgroup. 
### Sketch of the Proof
Fix a basepoint $x_0 \in A \cap B$. The universal property of the free product implies that there is a homomorphism $\phi: \pi_1(A) * \pi_1(B) \to \pi_1(A \cup B)$ (all based at $x_0$), and the lemma about the factorization of paths (proved at the start of this section) implies that $\phi$ is surjective. The hard part is showing that $\ker(\phi) = N$. The rough idea is to show that factorizations become unique when we pass from $\pi_1(A) * \pi_1(B)$ to $\pi_1(A) * \pi_1(B) / N$. In particular, any factorizations of a path $[f]$ will be related by a sequence of two kinds of moves. We can combine adjacent elements $[f_i][f_{i+1}]$ if they both lie in $\pi_1(A)$ or both lie in $\pi_1(B)$, and if $[f_i]$ is in $\pi_1(A \cap B)$, we can regard it as either an element of $\pi_1(A)$ or an element of $\pi_1(B)$. .....

## Orientable Surfaces
Now we find the fundamental group of an orientable surface with arbitrary genus...

Write it as a quotient of a certain polygon...this in turn is the union of something homotopy equivalent to the boundary (a wedge of 4 circles) and a simply-connected bit that includes the center of the polygon...their intersection...

You end up with $\pi_1 = \langle a, b, c, d | [a, b][c, d] \rangle$. That is, take the free group on 4 generators, and add a relation $[a, b][c, d] = 1$ where $[a, b]$ and $[c, d]$ are commutators. More generally $\pi_1$ of a genus $g$ surface will be a free group on $2g$ elements $a_1, b_1, \dots, a_n, b_n$ with a relation given by the product of commutators $[a_i, b_i]$. We can show that these are not isomorphic by showing that their abelianizations ($\Z^{2g}$ for a genus $g$ surface) are not isomorphic; thus surfaces of different genus are not homeomorphic or more generally homotopy equivalent. 
# Applications
## Brouwer Fixed Point Theorem
The 2-dimensional version of the Brouwer fixed point theorem states that every map $h: D^2 \to D^2$ has a fixed point. To prove this, we suppose for a contradiction that there is no fixed point, i.e. $h(x) \neq x$ for all $x$. Define a map $r(x)$ as follows: draw a ray from $h(x)$ to $x$ (which must exist since $h(x) \neq x$); then let $r(x)$ be the point where the ray meets the boundary of the disc. $r$ is continuous, and $r(x) = x$ for all $x$ on the boundary. Thus $r$ is a retraction from $D^2$ to $S^1$. We can then use it to construct a homotopy from any loop in $S^1$ to the constant loop. ......

## Fundamental Theorem of Algebra
We now prove that any non-constant polynomial with complex coefficients has a complex root. Let $f(x) = x^n + a_{n-1}x^{n-1} + \dots + a_0$ and suppose $f$ has no root; we will show that $f$ is constant. Define $g_r(s) = \frac{re^{2\pi i s} / f(r) }{||(re^{2\pi i s} / f(r))||}$. This is well-defined since $f(r) \neq 0$, and gives a family of loops on $S^1$ (i.e. for each $r$, $g_r$ is a loop in $S^1$ based at $1 \in \C$). $g_0$ is a constant loop, and for any $r$, $f_r \simeq f_0$. Thus $[f_r] = 0$ for all $r$. 

Now fix $r$ so that $r > |a_1| + |a_2| + \dots + |a_n|$ (note that $|a_0|$ is omitted).....
## Topological Invariance of Dimension
We can prove a special case of the topological invariance of dimension ($\R^n$ is homeomorphic to $\R^m$ only if $n = m$) with the fundamental group: $\R^2$ is not homeomorphic to $\R^m$. 

Note first that a homeomorphism $\R^n \to \R^m$ induces a homeomorphism $\R^n - \{0\} \to \R^m - \{f(0)\}$. 

The special case $n=1$, $m$ arbitrary follows from the fact that $\R - \{0\}$ is disconnected while $\R^m - \{0\}$, for $m > 1$, is not.

Thus for $n = 2$ we can restrict our attention to $m > 2$. $\R^n - \{0\}$ is homeomorphic to $S^{n-1} \times \R$ (think polar coordinates), so a homeomorphism $\R^2 \to \R^m$ would induce a homeomorphism $S^1 \times \R \to S^{m-1} \times \R$, which would in turn induce an isomorphism $\Z \to \pi_1(S^{m-1} \times \R) \cong \pi_1(S^{m-1})$. But the fundamental group of the sphere is trivial except for $S^1$; thus such a homeomorphism is only possible when $m=2$. 