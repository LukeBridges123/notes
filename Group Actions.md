$\newcommand{\Perm}{\text{Perm}}$
$\newcommand{\Stab}{\text{Stab}}$ 
# Definitions and Some Examples
Many groups are groups of functions (specifically bijections, often preserving some structure) acting on some set--think groups of permutations, isometries, automorphisms, and so on. We can abstract this out to the idea of a "group action" or "group operation" on some set. 

Let $S$ be a set, $G$ be a group; then an action of $G$ on $S$ is a function (say $*$) $G \times S \to S$ with the following properties:

$1 * s = s$ for all $s \in S$
$(gg')*s = g * (g' * s)$ for all $g, g' \in G, s \in S$

(The second can be thought of as an associativity condition, or as requiring that multiplication of group elements works like composition of functions on $S$. Indeed, we can think of this in terms of a homomorphism between $G$ and the group of permutations of $S$; we send an element $g$ to the function $m_g \in \Perm(S)$  given by $m_g(s) = g*s$, which is a permutation because it has an inverse, given by $m_{g^{-1}}$. )

Some examples: the symmetric group $S_n$ acts in the obvious way on the set $[n]$, and $M_n$ and $GL_n$ act on $\R^n$. $M_n$ also acts on certain subsets of the plane, e.g. the set of triangles, because an isometry sends triangles to triangles. 

## Orbits
Let $G$ act on $S$, and take $s \in S$. The orbit of $s$ under $G$ is defined to be the set of elements $s' \in S$ such that there exists some $g \in G$ with $s' = g * s$. In other words, it is the set of all points to which $s$ gets mapped by some permutation from the group action. 

This in fact determines an equivalence relation (where $s \sim s'$ if and only if $s' = gs$ for some $g \in G$, which happens if and only if $O_s = O_{s'}$) , and so determines a partition. 

If there is only one orbit--all elements of $S$ are in the same orbit--then the action is called "transitive". In other words, the group action is "powerful enough" that for any two elements $s, s' \in S$, there exists $g \in G$ such that $g$ sends $s$ to $s'$. For example, consider the action of $M_2$ on the set of triangles in the plane, and the action on the set of lines in the plane. $M_2$ does not act transitively on the triangles, since two triangles are in the same orbit iff they are congruent, but not all triangles are congruent, but it does act transitively on the lines: to send a line $L_1$ to $L_2$, if they are parallel, just translate $L_1$ over to $L_2$; if not, rotate $L_1$ around the point where it intersects $L_2$ until it is equal. 

## The Stabilizer
The stabilizer of an element $s \in S$ is the set of all $g \in G$ with $gs = s$. It is denoted $\Stab(s)$. At the very least this will include the identity in $G$, per part of the definition of a group action. It will be closed under the operation in $G$, since if $h, g \in Stab(s)$ then $(hg)s = h(g(s)) = hs = s$. Finally it will include inverses: if $gs = s$ and $g^{-1}s = s'$, then $g^{-1}(gs) = s'$ but $s' = g^{-1}(gs) = (g^{-1}g)s = 1s = s$, so $s' = s$ and so $g^{-1} \in \Stab(s)$. 

Example: take a square in the plane centered at the origin, with its vertices each touching one of the axes. Its stabilizer, the group of isometries fixing the square, will be isomorphic to $D_4$. (Here we consider $M_2$ as acting on the set of all squares.)

As before, let $G$ act on $S$, and take $s \in S$. The following two properties (reminiscent of properties of the kernel and of normal subgroups) hold:

If $g, h \in G$ then $gs = hs$ if and only if $g^{-1}h \in \Stab(s)$, or $h \in g \cdot \Stab(s)$. 
If $gs = s'$; then $\Stab(s') = g\Stab(s)g^{-1}$, the conjugation of $\Stab(s)$ by $g$. 

For the first, $gs = hs$ if and only if $g^{-1}hs = s$ or $(g^{-1}h)s = s$, so $g^{-1}h \in \Stab(s)$. This then happens if and only if $h \in g \cdot \Stab(s)$, multiplying both sides by $g$. 

For the second, let $gs = s'$. First take an arbitrary $x \in \Stab(s)$. Then $(gxg^{-1})s' = (gx)(g^{-1}s') = (gx)s = g(xs) = gs = s'$, so $gxg^{-1} \in \Stab(s')$. For the other direction, let $y \in \Stab(s')$; we want to show that there exists $x \in \Stab(s')$ with $y = gxg^{-1}$. This is the case if and only if $x = g^{-1}yg$, i.e. $g^{-1}yg \in \Stab(s)$. Doing the same computation as before works: $(g^{-1}yg)s = g^{-1}ys' = g^{-1}s' = s$, so $g^{-1}yg \in \Stab(s)$, as desired. 

# Acting on Cosets
We know that, if $H$ is a subgroup (not necessarily normal) of $G$, then the left cosets of $H$ partition $G$; we will denote this by $G/H$ even though this may not actually be a quotient group. $G$ acts naturally on these cosets by left multiplication: $g *(aH)$ is defined to equal $(ga)H$. This is a transitive action, since for any cosets $aH, bH$ we have $(ab^{-1})*bH = aH$. The stabilizer of $H$ (the subgroup itself, the coset of the identity) is $H$: certainly for any $h \in H$ we have $hH = H$, while if $gH = H$ then $g$ is congruent to the identity and so is in $H$. 

For example, take the subgroup $H = \langle y \rangle$ of $S_3$. We have the cosets $H, xH, x^2H$, which we'll call $C_1, C_2, C_3$ respectively. Now we consider how $S_3$ acts on these cosets. Left multiplication by any element of $S_3$ permutes the $C_i$, and so acts like a permutation on $3$ elements, i.e. an element of $S_3$. Left multiplication by $x$ sends $C_1, C_2, C_3$ to $C_2, C_3, C_1$ respectively, and left multiplication by $x^2$ sends them to $C_3, C_1, C_2$. In other words, $x$ corresponds to the permutation $(1, 2, 3)$, which is just $x$. Left multiplication by $y$ sends them to $C_1, C_3, C_2$: $y$ acts like the transposition $(2, 3)$. These two permutations together generate $S_3$. Recalling that we have a natural homomorphism from $S_3$ to permutations of the $C_i$ using the group action, now know that this is in fact an isomorphism--and thus an isomorphism from $S_3$ to itself. 

## Orbit-Stabilizer Theorem
Let $G$ act on a set $S$, and take an $s \in S$ with stabilizer $\Stab(s)$; there is a bijection between the cosets $G / \Stab(s)$ and the orbit of $s$. The bijection $\epsilon$  is defined like this: given a coset of the stabilizer $g\Stab(s)$, send that to $g*s$. This function is compatible with the action of $G$ on both sides, in the sense that for any $x$, letting $*_1$ be the standard action of $G$ on $G/\Stab(s)$ , and letting $*_2$ be the action of $G$ on $S$, we have $\epsilon(g *_1 a\Stab(s)) = g *_2 \epsilon(a\Stab(s))$. 

Assuming that $\epsilon$ is a well-defined function, the compatibility property falls out easily: $\epsilon(g*_1 a\Stab(s)) = \epsilon ((ga)\Stab(s)) = (ga)*_2 s = g*_2 (a *_2 s) = g*_2 (\epsilon(a\Stab(s)))$. But first we need to establish that it is actually well-defined. After all, $g\Stab(s)$ could just as well be written $h\Stab(s)$ for any $h$ congruent to $g$. But $h$ being congruent to $g$ means that there is some $e \in \Stab(s)$ such that $h = ge$. Thus $\epsilon(h\Stab(s)) = \epsilon(ge\Stab(s)) = \epsilon(g\Stab(s)) = gs$, so all these representations of a given coset give the same output for $\epsilon$. 

Now we show bijectivity. Surjectivity is easy: for any element $gs$ of the orbit of $s$, $g\Stab(s)$ gets mapped to $gs$. Then for injectivity, suppose $\epsilon(g\Stab(s)) = \epsilon(h\Stab(s))$. Then $gs = hs$, and we know from before that this happens if and only if $h \in g\Stab(s)$, which then means $g\Stab(s) = h\Stab(s)$. 

As an example, consider a dihedral group $D_5$ acting on the set $V$ of vertices of a regular pentagon. This is transitive, so the orbit of any vertex is all of $V$. The orbit-stabilizer theorem says that there is a bijection between $D_5 / \Stab(v)$ and $V$ for any $v \in V$. This is the case: $\Stab(v)$ consists of the identity and a reflection, which has order $2$, and by the counting formula $D_5 / \Stab(v)$ therefore has order $5$, as does $V$.

## The Counting Formula
As a generalization of the example above, we have the following. In general, for a subgroup $H$ of $G$, we have $|G/H| \cdot |H| = |G|$: number of cosets times order of subgroup equals order of parent group. Replacing $H$ with the stabilizer of an element $s$ of a set $S$ on which $G$ acts, we get $|G/\Stab(s)| \cdot |\Stab(s)| = |G|$ or, using the orbit-stabilizer theorem, $|O_s| \cdot |\Stab(s)| = |G|$. As a consequence, the order of the orbit divides the order of $G$, as does the order of the stabilizer. A related formula is that, since the orbits partition $S$, $|S| = |O_1| + \dots + |O_n|$ (where we label the orbits as $1, \dots, n$). 

As an example: what is the order of the group $G < SO_3$ of rotational symmetries of the dodecahedron? The dodecahedron has $12$ faces, and $G$ acts transitively on those faces. For each of those faces, the stabilizer has order $5$. Thus for any face $f$, $|G| = |O_f| \cdot |\Stab(f)| = 60$, so there are $60$ rotational symmetries of the dodecahedron. (Incidentally, we can do the same analysis on the icosahedron, where the stabilizer of each vertex has order $5$ (5-fold rotational symmetry around each vertex) and there are $12$ vertices. The symmetries of the icosahedron turn out to be isomorphic to the symmetries of the dodecahedron.)

# Acting on Subsets
Whenever $G$ acts on a set $S$, there's a natural way to define the action of $G$ on the subsets of $S$, in particular the subsets of a given size $n$. As with cosets, we act by left multiplication, sending a set $T$ to $gT$, the set $\{gt : t \in T\}$. Since left multiplication is a bijection, sets of size $n$ get mapped to other sets of size $n$. The stabilizer of $T$ will be the group elements that map $T$ to $T$--possibly shuffling around the elements, but always mapping them to elements within $T$. 

# Permutation Representations
Group actions let us find homomorphisms from an arbitrary group $G$ to $S_n$, called permutation representations of $G$. More generally we consider homomorphism from $G$ to $\Perm(S)$, the group of permutations of some arbitrary set (which may be finite, hence $\Perm(S)$ may not be a symmetric group in the usual sense). In fact there exists a bijection between the set of possible actions of $G$ on a set $S$, and the set of permutation representations of $G$ (in particular, representations of $G$ using $\Perm(S)$). A permutation representation of $G$ with $\Perm(S)$ naturally gives rise to a group action: letting $\phi$ be the homomorphism $G \to \Perm(S)$, take any $g \in G$, and let $\phi(g) = m_g$; now define $g * s$ to be $m_g(s)$. Conversely, given a group action, the function $m_g$ given by $s \to g*s$ is a permutation of $S$, and (using the defining properties of group representations, e.g. associativity) we can get that the function $g \to m_g$ is a homomorphism $G \to \Perm(S)$. 

When a permutation representation of $G$ is injective--equivalently, the only element of $G$ for which $m_g$ is the identity permutation is the identity element of $G$-- it lets us get an isomorphism from $G$ to $\im(\phi)$, which is then an isomorphism between $G$ and some group of permutations, a subgroup of $\Perm(S)$. When the permutation representation defined by a group action is injective--or in other words, the only $g$ such that $g*s = s$ for all $s \in S$ is the identity in $G$--the group action is called "faithful". 

## Cayley's Theorem
Not every group immediately seems to act on something. A group like $D_n$ or $S_n$ is defined in terms of functions on some underlying set, which provides an action of the group on that set, but with a group like $Z/nZ$, it's not so obvious what, if anything, it should act on. But we've already seen that a group can act on its cosets in different ways, and in fact a group can act on itself in many ways, for instance by left multiplication: define $g*h$ to be simply $gh$, for any $g, h \in G$, or by conjugation, letting $g*h$ be $ghg^{-1}$. Analyzing the first will lead us to Cayley's theorem, while analyzing the second will lead us eventually to the Sylow theorems.

Cayley's theorem is traditionally stated as follows: any finite group is isomorphic to some subgroup of $S_n$. Proof: the action of $G$ on itself by left multiplication is faithful, since $gh = h$ implies $g = 1$. (It is also transitive, incidentally.) Thus this action gives an isomorphism between $G$ and some subgroup of $\Perm(G)$. When $G$ is finite, $\Perm(G)$ is isomorphic to $S_n$ for some $n$, so $G$ is isomorphic to a subgroup of $S_n$. 

# Acting By Conjugation
The function $g*h = ghg^{-1}$ also defines an action: certainly $1*h = 1h1 = h$, and $(fg)h = (fg)h(fg)^{-1} = fghg^{-1}f^{-1} = f(g*h)f^{-1} = f*(g*h))$. 

As usual, we look at the stabilizers and orbits of the elements of $G$ under this action. The stabilizer of an element $x$ turns out to be the "centralizer" of $x$, denoted $Z(x)$: the set of all elements that commute with $x$ (since $gxg^{-1} = x$ implies $gx = xg$), and the orbit of $x$ is called the "conjugacy class" of $x$--the equivalence class of elements with $x' = gxg^{-1}$--and denoted $C(x)$.

Some basic properties: $Z(x)$ contains $x$ and contains, as a normal subgroup, the center $Z$ of the whole group. If $x$ is in the center, then its centralizer is the whole group; a corollary of this and the counting formula is that, in this case, the conjugacy class of $x$ is just $\{x\}$. As a special case of the general fact that the orbits under a group action partition the set, the conjugacy classes partition the group, and we have the counting formula $|G| = \sum |C|$, taken over all conjugacy classes $C$. This is called the "class equation" of a group. 

Some further properties of the class equation: every term on the RHS divides $|G|$ (by the first counting formula, $|G| = |O_x||\Stab(x)|$), at least one term is $1$ (as the conjugacy class of $1$ contains only itself), and in fact each element of the center contributes a $1$ to the RHS. These facts place some strong restrictions on what the class equation of a group can look like.

For example, in $S_3$ we have the conjugacy classes $\{1\}, \{x, x^2\}, \{y, xy, x^2y\}$ and class equation $6 = 1 + 2 + 3$. In any abelian group, say of order $n$, the class equation will be $n = 1 + 1 + \dots + 1$. 

## Groups of Order p^n
A $p$-group is a group whose order is a power of a prime number. We can use the class equation to prove some simple but useful facts about them.

For example: any $p$-group has a nontrivial center. Each term on the RHS of its class equation will be a power of $p$, including $p^0$. In fact we always have a $1$ in the class equation. If all the other terms in the class equation were positive powers of $p$, the RHS would be $1$ more than a multiple of $p$ and so would not be divisible by $p$. Thus there must be some more $1$s on the RHS. Each of these represents an element of the center: such elements have an orbit of order $1$, hence a stabilizer of order $|G|$, hence their centralizer is the whole group. 

As an application of this, we can prove that all groups of order $p^2$ are abelian. Let $G$ be such a group; the center of $G$ has order $1, p$ or $p^2$ by Lagrange's theorem, and we can eliminate $1$ by the above. If it's $p^2$ then $G$ is abelian. We will show that $|Z| = p$ is impossible. Suppose that $|Z| = p$; then there exists an element $x$ not in $Z$, which will have a centralizer that includes $Z$ and $x$ itself, and thus at least $p + 1$ elements. But this forces $Z(x)$ to have $p^2$ elements, the only option greater than $p$, meaning that $x \in Z$, contradiction our initial assumption that it is not. With a bit more work, this can be extended to prove that any group of order $p^2$ is isomorphic to $C_{p^2}$ or $C_p \times C_p$. Let $|G| = p^2$. If there exists an element with order $p^2$, then $G$ is cyclic, and we're done. Otherwise, pick elements $x, y$, both with order $p$, such that $x$ is not a power of $y$ and vice versa. Then $\langle x \rangle$ and $\langle y \rangle$ fit all the requirements for $G$ to be isomorphic to $\langle x \rangle \times \langle y \rangle$, and thus $C_p \times C_p$: they have trivial intersection, elements of $\langle x \rangle$ commute with elements of $\langle y \rangle$, $\langle x \rangle$ is normal, and the product set of the two subgroups is all of $G$. (The second and third of those follow from $G$ being abelian.)

## Acting by Conjugation on Subgroups
We can also define an action on the subgroups of $G$ by conjugation. 


# Sylow Theorems
Let $p^e$ be the largest power of $p$ dividing $|G|$, so $|G| = p^em$ where $m$ is not divisible by $p$. A Sylow $p$-subgroup is a subgroup of $G$ of order $p^e$. We assume from here on out that $e>0$, so $p$ will always be a divisor of $|G|$. 

The first Sylow theorem asserts that any group $G$ contains a Sylow $p$-subgroup.

The second says first that any two Sylow $p$-subgroups are conjugate to each other, i.e. if $H, H'$ are Sylow p-subgroups then there exists $g$ with $gHg^{-1} = H'$, and second that any p-subgroup is contained within a Sylow p-subgroup (i.e. the ones whose order is a maximal prime power). 

The third says that, letting $n_p$ be the number of Sylow p-subgroups, then $n_p|m$ (recall that $m = |G|/p^e$) and $n_p = 1$ (mod $p$). 
## Proofs
### Some Lemmas
We will need two lemmas, one about actions of a group on subsets of itself, one that's just combinatorics. 

The first is that, if $U$ is a subset of a group $G$, then the stabilizer of $U$ under the action of $G$ by left multiplication has an order that divides both $|G|$ and $|U|$. The first of those facts follows from $\Stab(U)$ being a subgroup. As for the second, note that the stabilizer $H$ acts on $U$--in the sense of acting on $U$'s elements. Thus $U$ is partitioned into orbits under this action, which are the right cosets $Hu$. All the right cosets have the same order $|H|$. Thus $U$ is partitioned into subsets all of order $H$, so $|H|$ divides $|U|$. 

The second lemma is that the binomial coefficient $\binom{n}{p^e}$, where $n = p^em$ and $p$ does not divide $m$, is not divisible by $p$. That is, the number of subsets of order $p^e$ in a set of order $n$ will not be divisible by $p$. 
### First Theorem
The proofs of all three theorems proceed by finding a "nice" set on which $G$ acts and trying to extract information about $G$ from this action. For the first theorem, let $S$ be the set of all subsets (not necessarily subgroups) of order $p^e$, and let $G$ act on $S$ by left multiplication. If a Sylow p-subgroup exists, it will be in $S$. Its stabilizer, under the action of $G$, must be the subgroup itself, and so must have order $p^e$. Conversely, if any element of $S$ has a stabilizer of order $p^e$, then that stabilizer will be a subgroup of order $p^e$ and so will be a Sylow p-subgroup. 

Let $N = |S|$. By the counting formula, $|S|$ is equal to the sum of the sizes of the orbits, and by the second lemma above, $N$ is not divisible by $p$. Thus there exists at least one orbit, say the orbit $O_U$ of a subset $U$, such that the size of the orbit is not divisible by $p$. By another counting formula, $p^em = |G| = |O_U||\Stab(U)|$. Since $|O_U|$ is not divisible by $p$, $|\Stab(U)|$ must be; indeed $|\Stab(U)|$ divides $p^em$ and $p^e$. From this we have that $|O_U| = m$ and so $|\Stab(U)| = p^e$, so $\Stab(U)$ is a Sylow p-subgroup.
### Second Theorem
This has two parts: any Sylow p-subgroups are conjugates of each other, and any p-subgroup is contained in a Sylow p-subgroup. We prove both of them at once. Let $K$ be a p-subgroup and let $H$ be a Sylow p-subgroup; we will show that $K$ is a subgroup of some conjugate of $H$. In the special case where $K$ is a Sylow p-subgroup, this means that $K$ is contained within a conjugate of $H$, but since this conjugate must itself be a Sylow p-subgroup, $K$ must be that conjugate, and so $K$ is a conjugate of $H$. Thus if we can prove the second part of the theorem in this way, we'll have proved the first part as well.

What we'd like is to find a set $S$ on which $G$ acts, for which the following are true: $p$ does not divide the order of $S$, the action is transitive, and there exists an element $c$ of $S$ whose stabilizer is $H$\*. If we restrict the action to $K$, we have a p-group acting on a set with order not divisible by $p$, so the orbits are all powers of $k$ while their sum is not, so at least one of the orbits must have order $1$, i.e. there must be an element with $kx = x$ for all $k \in K$. By transitivity, we have $x = gc$ for some $g \in G$, so in fact $kgc = gc$ for all $k \in K$. Note that we have $\Stab(x) = g\Stab(c)g^{-1}$. $K$ is a subgroup of $\Stab(c')$, while $\Stab(c) = H$ by assumption, so $K$ is a subgroup of $gHg^{-1}$. 

\* We do have such a set: namely the set of left cosets of $H$, $G/H$. There are $|G|/|H| = m$ cosets (not divisible by $p$), the action of $H$ on them is transitive, and the stabilizer of $H$ is $H$ so $c$ exists.

### Third Theorem
Now we consider the action of $G$ on the set of Sylow p-subgroups (call it $S_p$) by conjugation. The second theorem implies that this action is transitive, hence has only one orbit of order $|S_p|$. We have $|S_p| = |G|/|\Stab(H)|$ for any Sylow p-subgroup $H$. $H$ is a subgroup of $\Stab(H)$, so $p^e$ must divide $\Stab(H)$. We know then that $|S_p| = p^em/p^ek$ for some $k$, so $|S_p| = m/k$ and so $|S_p|$ divides $m$. 
## Consequences of the Sylow theorems
### Cauchy's theorem

### Classifying groups
Let $|G| = 15$; we will show that $G$ is cyclic. Since $15 = 3*5$, we know from the first Sylow theorem that it has subgroups of order $3$ and $5$, which then must be cyclic. There will only be $1$ 3-subgroup: by the third Sylow theorem, the number of 3-subgroups, $n_3$, must divide 5 (so equals 1 or 5) and must be congruent to 1 mod 3 (so in fact 1 is the only option). An identical argument proves that there is only one 5-subgroup. Let $H, K < G$ be the 3- and 5-subgroups respectively. $gHg^{-1}$ is also a 3-subgroup, so must be equal to $H$, and so is normal, and the same goes for $K$. (N.B. we aren't using the second Sylow theorem here, just the fact that conjugation is an automorphism of $G$, so sends $H$ to an isomorphic subgroup.) Thus $H$ and $K$ are both normal, their intersection is trivial, and their product set must be all of $G$ (as it includes at least 7 elements and is a subgroup), so $G$ must be isomorphic to the product $H \times K$, which is itself isomorphic to $C_{15}$. 