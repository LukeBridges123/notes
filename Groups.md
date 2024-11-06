# Definition and Basic Properties
Latex commands go here:
$\newcommand{\MatrixTwoTwo}[4]{\begin{pmatrix} #1 &#2\\ #3 &#4 \end{pmatrix}}$
$\newcommand{\R}{\mathbb{R}}$
$\newcommand{\im}{\text{Im}}$ 
A group $G$ is a set equipped with an associative binary operation such that there is an identity element and all elements have inverses. 

A few immediate consequences of these axioms:
## A Consequence of Associativity
The associativity of the group operation gives us a unique way to define the product of $n$ elements $[a_1 \cdots a_n]$. More formally, we'd like the following to hold for our product: 
(i). $[a] = a$
(ii). $[a \cdots b] = a \cdot b$ (where, on the right, you just have the group operation)
(iii). for any $i$ with $1 \leq i < n$, $[a_1 \cdots a_n] = [a_1 \cdots a_i] \cdot [a_{i+1} \cdots a_n]$. 

We define the product recursively, and prove that it works inductively. The product of 1 or 2 elements is already given by (i) and (ii). For more elements, assuming we have properly defined a product of less than $n$ elements for any $n$, we define the product of $n$ elements as $[a_1 \cdots a_n] = [a_1 \cdots a_{n-1}] \cdot [a_n]$. Clearly this satisfies the $i = n-1$ case of (iii). To show that (3) holds for any other $i$, note that we have $[a_1 \cdots a_{n-1}] \cdot [a_n] = ([a_1 \cdots a_i] \cdot [a_{i+1} \cdots a_{n-1}]) \cdot [a_n]$, by the inductive hypothesis that property (iii) holds in general for products of $i-1$ elements. Then by associativity and again using the inductive hypothesis, the RHS equals $[a_1 \cdots a_i] \cdot ([a_{i+1} \cdots a_{n-1}] \cdot [a_n])$, which then equals $[a_1 \cdots a_i] \cdot [a_{i+1} \cdots a_n]$. To prove uniqueness, note that given any two products of $n$ elements satisfying the three properties, we can get $[a_1\cdots a_n] = (a_1 \cdot (a_2 \cdot (a_3 \cdots)\cdots)$ i.e. it's equal to the product of those elements parenthesized to the right. So any such product will equal the "fully parenthesized" product of $n$ elements, so any such product will assign the same value to $[a_1\cdots a_n]$ as the $[a_1 \cdots a_{n-1}] \cdot [a_n]$ product defined earlier. 
## Some Properties of Identities and Inverses
The identity element is unique, since if $e, e'$ are two identity elements, then $e = ee' = e'$. Inverses are unique, in the sense that if $b \cdot a = b' \cdot a = a \cdot b = a \cdot b' = e$ (so that both $b$ and $b'$ are left inverses of $a$), then $b = b'$, as can be seen by starting with $b \cdot a = e$, multiplying both sides on the right by $b'$ to get $(b \cdot a) \cdot b' = b'$, then using associativity and the fact that $ab' = e$ to get $b(ab') = b'$ or $be = b'$ or $b = b'$. Any element with a left inverse and a right inverse is invertible, and its left and right inverses are the same: if $ba = ac = e$, then $b(ac) = b$, but $(ba)c = b$, so $c = b$. Finally we have the "cancellation law": if $ab = ac$ then $b = c$, and the same for if $ba = ca$. Since $a$, being an element of the group, is invertible, we have $a^{-1}(ab) = a^{-1}(ac)$, so $(a^{-1}a)b = (a^{-1}a)c$, and so $b = c$. Note that all of these proofs, especially of the cancellation law and the uniqueness of inverses, relied on associativity, and properties like the cancellation law may not hold for a non-associative binary operation, even when inverses and an identity exist.

In finite groups, the existence of inverses can be deduced from the cancellation law (along with associativity and closure). If $a$ is an element of a finite group, then by the pigeonhole principle its powers $a, a^2, a^3, \dots$ must repeat eventually, say $a^m = a^n$ with $n < m$. Then we can write $a^{m-n} \cdot a^{n} = a^n$ and cancel $a^n$ from both sides to get $a^{m-n} = 1$. Thus $a \cdot a^{m-n-1} = 1$, so $a^{m-n-1}$ is an inverse of $a$. 
# Subgroups
A subgroup (as with a subspace of a vector space) is a subset $S$ of a group $G$, inheriting the operation from $G$, which is a group with respect to that operation. Associativity automatically holds; closure, the existence of an identity, and existence of inverses may not hold for an arbitrary subset and must be checked. (The existence of the identity is only in there to exclude the empty set; for a nonempty set, it follows from closure and the existence of inverses.)

The "trivial" subgroup (consisting only of the identity) and the "parent" group itself are automatically subgroups. Whether there are nontrivial proper subgroups depends on the group. 

## Examples
As a subset of the multiplicative group of complex numbers, we have the "circle group" $S^1$, equal to the unit circle in the complex plane, i.e. all the complex numbers with norm $1$. Multiplication then corresponds to addition of angles. 
### Subgroups of GL_n
Some subgroups of $GL_n(\mathbb{R})$: $SL_n(\mathbb{R})$ (matrices with determinant 1), $O_n(\mathbb{R})$ (orthogonal matrices or isometries), $SO_n(\mathbb{R})$ (orthogonal matrices with determinant 1, i.e. orientation-preserving isometries). For complex matrices the equivalents of $O_n$ and $SO_n$ are the "unitary" and "special unitary" groups $U_n$ and $SU_n$. 

For example, closure of $SL_n(\mathbb{R})$ follows from $\det{AB} = \det{A}\det{B} = 1 \cdot 1 = 1$. Similarly if $A$ has determinant 1 then so does its inverse: $I = AA^{-1}$, so $\det{AA^{-1}} = \det{I} = 1$, or $\det{A}\det{A^{-1}} = \det{A^{-1}} = 1$. And of course the identity has determinant 1. 
### Subgroups of additive group of integers
For any subgroup $S$ of $\mathbb{Z}^+$, we have $0 \in S$, $a + b \in S$ whenever $a, b \in S$, and $-a \in S$ whenever $a \in S$. 

It turns out that the only subgroups of $\mathbb{Z}^+$ are the groups of all multiples of an integer $a$, denotes $\mathbb{Z}a$. On one hand, these are all subgroups: 0 is a multiple of $a$ for any $a$, if $b, c \in \mathbb{Z}a$ then $b + c = ma + na = a(m + n) \in \mathbb{Z}a$, and if $n$ is a multiple of $a$ so is $-a$. 

On the other hand, any subgroup of the integers equals $\mathbb{Z}a$ for some $a$. In particular, $a$ is either $0$ or the smallest nonzero element of the subgroup. Proof: let $S$ be the subgroup. If $S$ is the trivial group, we're done. Otherwise, it must contain at least one positive integer (since if contains a negative integer, it also contains that integer's positive additive inverse). By well-ordering there is a smallest positive element $a$. By closure, all the multiples of $a$ are in $S$. (This is true even though closure under multiplication isn't guaranteed by the group axioms, since you can just keep adding $a$ to itself and use induction.) So $\mathbb{Z}a \subseteq S$. For the other direction, taking any $b \in S$, let $b = na + r$ with $0 \leq r < a$. If $r \neq 0$ then by closure, $(na + r) - na = r$ is in $S$, but $r < a$, contradicting our assumption that $a$ is the smallest positive element of the subgroup. So $b = na$, and $S \subseteq \mathbb{Z}a$. Thus $S = \mathbb{Z}a$. 

#### Bezout's lemma
Now define a subgroup $\mathbb{Z}a + \mathbb{Z}b$, the subgroup generated by $a$ and $b$--that is, all integers $n = ka + lb$. This must consist of multiples of some integer $d$: $\mathbb{Z}a + \mathbb{Z}b = \mathbb{Z}d$. $d$ turns out to equal $\gcd(a, b)$. That is, $d$ divides both $a$ and $b$, any divisor of $a$ and $b$ divides $d$. Also, there exists $r, s$ such that $ra + sb = d$. The last part is obvious from how $d$ was defined. The first part follows from the fact that $a$ and $b$ are elements of $\mathbb{Z}d$, given that they are certainly expressible as linear combinations of $a$ and $b$. As for the second part, letting $e$ be a divisor of $a$ and $b$, so that $a = me$ and $b = ne$, we have $ra + sb = rme + sne = e(rm + sn) = d$, so $e|d$. This gives a form of Bezout's lemma, that $\gcd(a, b)$ can be expressed as a linear combination with integer coefficients of $a$ and $b$. As a corollary, $a$ and $b$ are relatively prime if and only if there exist integers $r, s$ with $ar + bs = 1$, which implies $\mathbb{Z}a + \mathbb{Z}b = \mathbb{Z}$. 
#### Euclid's lemma
We can also get Euclid's lemma as a corollary--if $p$ is prime and. $p|ab$, then $p|a$ or $p|b$. Assuming WLOG that $p$ does not divide $a$, then we have $gcd(a, p) = 1$, so there exist integers $r, s$ with $ar + ps = 1$; thus $bar + bps = b$. Then $p|bar$, by the assumption that $p|ab$, while clearly $p|bps$, so $p|(bar + bps)$ and thus $p|b$. 

#### Intersections of subgroups
$\mathbb{Z}a \cap \mathbb{Z}b$ is the set of all integers which are multiples of $a$ and $b$. This is also a subgroup of $\mathbb{Z}^+$, so it equals $\mathbb{Z}m$ for some positive integer $m$. $m$ turns out to be the least common multiple of $a$ and $b$, i.e. $a|m$ and $b|m$, and any integer divisible by both $a$ and $b$ will be divisible by $m$. The first thing follows directly from how $m$ was defined. As for the second, certainly any element of $\mathbb{Z}a \cap \mathbb{Z}b$ will be a multiple of $a$ and $b$, but also, by definition of $m$, any element of $\mathbb{Z}m$ is a multiple of $m$, and $\mathbb{Z}a \cap \mathbb{Z}b = \mathbb{Z}m$. As a corollary, letting $a, b$ be positive, we have $\gcd(a, b) \cdot \text{lcm}(a, b) = ab$. Set $d = \gcd(a, b)$, $m = \text{lcm}(a, b)$. We know $a/d$ is a positive integer, so $\frac{ab}{d}$ is as well, and is divisible by $b$; in the same way, $\frac{b}{d}$ is a positive integer, so $\frac{ab}{d} = \frac{b}{d} \cdot a$ is divisible by $a$ as well. This means $\frac{ab}{d} \in \mathbb{Z}m$, i.e. $m|\frac{ab}{d}$, so $md|ab$. We can now go in the other direction, showing $ab|md$, which would establish $ab = md$. Given that there exist integers $r, s$ with $ra + sb = d$, we have $mra + msb = md$. Since $b|m$, we have $ab|mra$, and by the same logic, $ab|msb$. Thus the RHS, and thus the LHS as well, are divisible by $ab$, so $ab|md$. Combining the two results, we get $ab = md$. 

# Cyclic Groups
Given a group $G$ and an element $x \in G$, let the *cyclic subgroup of G generated by x* consist of $1$, all powers of $x$, and all powers of $x^{-1}$. (Using multiplicative notation) This is denoted $\langle x \rangle$. We know from before that any subgroup of $Z^+$ is cyclic. For more examples: the subgroup of $\mathbb{R}^x$ generated by $-1$ consists just of $1, -1$ and is isomorphic to $S_2$. 
## Order of Cyclic Subgroups and Order of Group Elements
Let $\langle x \rangle$ be a cyclic subgroup of $g$, and let $S$ consist of all integers with $x^k = 1$. Then:

(i) S is a subgroup of $\mathbb{Z}^+$
(ii) $x^r = x^s$ with $r \geq s$ if and only if $x^{r-s} = 1$ if and only if $r - s \in S$
(iii) if $S \neq \{0\}$ then $S = \mathbb{Z}n$ for some $n > 0$, and $1, x, x^2, \dots, x^{n-1}$ are the distinct elements of $\langle x \rangle$; thus $\langle x \rangle$ has 0order $n$. 

For (i), $x^0 = 1$ by definition so $0 \in S$, if $x^k \in S$ then $x^{-k} = (x^k)^{-1} = 1^{-1} = 1$, so we have inverses, and if $n, m \in S$ then $x^{n+m} = x^nx^m = 1 \cdot 1 = 1$, so $n+m \in S$, so we have closure too. 

For (ii), we prove the implications in a circle. $x^r = x^s$ implies $x^{r-s} = 1$ since multiplying both sides on the right by $x^{-s}$ gets $x^{r}x^{-s} = x^{s}x^{-s}$ or $x^{r-s} = x^{s - s} = 1$. That then implies $r - s \in S$ by definition of $S$. Finally, $r - s \in S$ means $x^{r-s} = 1$, and multiplying both sides by $x^s$ gets $x^r = x^s$, as desired. 

For (iii), by (i) we know that $S$ is a subgroup of $\mathbb{Z}^{+}$, and we already know that any such subgroup, if nonempty, is $\mathbb{Z}n$ for some positive $n$. Thus $x^m = 1$ if and only if $m = nk$ for some integer $k$. We show first that every element of $\langle x \rangle$ is one of $1, x, \dots, x^{n-1}$, and second that these elements are all distinct. Letting $k = qn + r$, with $0 \leq r < n$, we have $x^k = (x^n)^qx^r = 1^qx^r = x^r$, so $x^k = x^r$ with $0 \leq r < n$. Then, supposing that we had $x^r = x^s$ with $0 \leq s < r < n$, we would have, by (ii), that $n|r - s$, a contradiction; thus none of the elements in $1, x, \dots, x^{n-1}$ are equal. 

We can now define the *order* of a group element to be the order of the cyclic subgroup it generates, or in other words, the smallest positive integer $n$ such that $x^n = 1$. If there is no such integer we say that $x$ has infinite order. 

Some simple facts about order: letting $x$ be of order $n$, and letting $k = pn + r$, we have $x^k = x^r$, $x^k = 1$ if and only if $r = 0$, and if $d = \gcd(k, n)$, then the order of $x^k$ is $\frac{n}{d}$. 

# Subgroups Generated by Multiple Elements
More generally, we have a notion of a subgroup generated by an arbitrary subset of a group. Letting $G$ be a group and $U \subseteq G$, ($U$ doesn't have to be a subgroup) the subgroup generated by $U$, denoted $\langle U \rangle$ is the smallest subgroup of $G$ that contains all the elements of $U$. We also say that $U$ generates $G$ if $\langle U \rangle = G$. 

Some examples: the *Klein four group* can be thought of as a subgroup of $GL_2(\mathbb{R})$ consisting of $\begin{pmatrix} ± 1 & 0 \\ 0 & ± 1 \end{pmatrix}$. It contains a subgroup generated by $\begin{pmatrix} -1 & 0 \\ 0 & 1\end{pmatrix}$, and another generated by the matrix with the matrix with $1$ in the upper left and $-1$ in the lower right. It is not cyclic, but is generated by those two matrices. 

The *quaternion group* consists of 8 elements, $± 1, ± i, ± j, ± k$. These, too, can be thought of as two-by-two matrices $1 = \MatrixTwoTwo{1}{0}{0}{1}, i = \MatrixTwoTwo{i}{0}{0}{-i}, j = \MatrixTwoTwo{0}{1}{-1}{0}, k = \MatrixTwoTwo{0}{i}{i}{0}$. 

# Homomorphisms
Let $G, G'$ be groups; a function $f: G \to G'$ is a homomorphism if, for all $x, y \in G$, we have $f(xy) = f(x)f(y)$. 

## Kernel
Let $\phi: G \to G'$ be a homomorphism with kernel $K$; then the following are equivalent:
(1) $\phi(a) = \phi(b)$ 
(2) $a^{-1}b \in K$
(3) $b \in aK$ 
(4) $bK = aK$. 

For $1 \to 2$, multiplying both sides of (1) by $\phi(a^{-1})$ gives $\phi(a^{-1})\phi(b) = \phi(a^{-1})\phi(a) = \phi(a^{-1}a) = \phi(1)$, so $\phi(a^{-1}b) = \phi(1) = 1$, or $a^{-1}b \in K$. 

For $2 \to 3$, if $a^{-1}b \in K$ then $b = a(a^{-1}b)$, hence $b = ak$ where $k \in K$, so $b \in aK$. (Alternatively just multiply both sides of $a^{-1}b \in K$ by $a$.)

For $3 \to 4$ if $b \in aK$ then $b = ak$ for some $k$ in the kernel, implying further that $bk' = akk'$ for all $k' \in K$. Since the kernel is a subgroup, we have $kk' \in K$ (say $kk' = k''$) , so $bk' \in aK$ for all $k'$. This means $bK \subseteq aK$. For the other way around,$b = ak$ implies $a = bk^{-1}$, and then we can run the same proof to get $aK \subseteq bK$. 

Finally, for $1 \to 4$, we know by (4) that there exist $k, k'$ with $ak = bk'$, and applying $\phi$ we get $\phi(ak) = \phi(bk')$ or $\phi(a)\phi(k) = \phi(b)\phi(k')$ or $\phi(a) = \phi(b)$. 

As a corollary, $\phi$ is injective if and only if it has a kernel of $\{1\}$. 

## Normal Subgroups
Letting $a, g \in G$, define the conjugate of $a$ by $g$ to be $gag^{-1}$. A *normal* subgroup is one that is closed under conjugation by arbitrary group elements, that is, $gNg^{-1}$ is a subgroup of $N$ for all $g \in G$. The kernel of a homomorphism is always a normal subgroup, and as we'll see the converse is true also. For the first direction, letting $\phi$ be a homomorphism with kernel $K$, we see for any $g \in G$ and $k \in K$ that $\phi(gkg^{-1}) = \phi(g)\phi(k)\phi(g^{-1}) = \phi(g)\phi(g^{-1}) = \phi(g)(\phi(g))^{-1} = 1$, so $gkg^{-1} \in K$ as well. 

As another example of a normal subgroup we have the *center* of $G$, denoted $Z(G)$, the set of all elements of $G$ that commute with all elements of $G$. That is, $Z(G) = \{x \in G | xy = yx \forall y \in G\}$. 

# Isomorphisms
A bijective homomorphism is called an isomorphism. 

# Cosets
## Congruence
Given a homomorphism $\phi: G \to G'$, define an equivalence relation on $G$ by $g_1 \equiv g_2$ iff $\phi(g_1) = \phi(g_2)$. This is called congruence. Note that this condition is equivalent to $g_1g_2^{-1} \in \ker(\phi)$, or $g_1 \in g_2K$ and $g_2 \in g_1K$, meaning $g_1K = g_2K$. Thus the equivalence classes of congruence are the cosets of the kernel of $\phi$. 

More generally, we can define a congruence relation using just cosets of an arbitrary subgroup, without a homomorphism entering the picture. Define $g_1 \equiv g_2$ iff $g_1H = g_2H$, for some $H \leq G$. Equivalently, $g_1 \equiv g_2$ iff there exists $h \in H$ with $g_1h = g_2$, or iff there exists $h' \in H$ with $g_2h' = g_1$, or iff $g_1g_2^{-1} \in H$. 

To check that this is an equivalence relation: for reflexivity, we have $g \equiv g$ because $gg^{-1} = 1 \in H$. For symmetry, if there exists $h \in H$ with $g_1h = g_2$ (so $g_1 \equiv g_2$), then $g_1 = g_2h^{-1}$ and $h^{-1} \in H$, so $g_2 \equiv g_1$. For transitivity, if there exists $h, h' \in H$ with $g_1h = g_2, g_2h' = g_3$, then $g_2 = g_1h^{-1}$, so $g_1h^{-1}h' = g_3$, and $h^{-1}h' \in H$, so $g_1 \equiv g_3$. This then implies that, given a subgroup $H$, the cosets of $H$ form a partition of the group. 
## Index of a Subgroup; Lagrange's Theorem
We can get an even better result out of the fact that the cosets partition the group. First note that, for any $a$, $|H| = |aH|$. This is because we have a bijection $f: H \to aH$ given by $f(h) = ah$, which is bijective because it has an inverse given by $f^{-1}(h) = a^{-1}h$. Thus all the cosets of $H$ have the same order as $H$ and so the same order as each other. Define the *index* of $H$, $[G : H]$, to be the number of left cosets of $H$ using elements of $G$. Since all the cosets have the same size and partition the group, it must be that $$|G| = |H|[G:H]$$or, the order of $H$ times the index of $H$ is the order of $G$; this is called the *Counting Formula*.As an immediate corollary we have Lagrange's theorem: the order of a subgroup divides the order of the group. 

A further corollary is that, for any homomorphism, the order of the kernel and image both divide $|G|$. In fact, bearing in mind that the number of elements in the range equals the number of cosets of $K$, we have $|G| = |\ker(\phi)|\cdot|\im(\phi)|$ (even though range($\phi$) isn't even part of $G$. 

As an example, this implies that $A_n = \frac{1}{2}|S_n|$, since in the sign homomorphism we have a kernel of $A_n$ and a 2-element range $\{1, -1\}$. 

The indices of nested subgroups, $K \leq H \leq G$, obey the following identity: $[G:K] = [G:H][H:K]$. If we restrict to $G$ being finite, then $[G:K] = \frac{|G|}{|K|} = \frac{|G|}{|H|} \cdot \frac{|H|}{|K|} = [G:H][H:K]$. 

Besides the usual left cosets we can also define right cosets $Hg$ similarly: the set of all $g' \in G$ with $g' = hg$ for some $h \in H$. This defines another equivalence relation along the same lines as congruence. We might then ask when right $H$-congruence is the same as left $H$-congruence. We have:

Given $H \leq G$, all of the following are equivalent:

(1) $H$ is a normal subgroup of $G$.
(2) for all $g \in G$, $gHg^{-1} = H$
(3) for all $g \in G$, $gH = Hg$
(4) Every right coset is a left coset 

Note that $gHg^{-1}$ is defined as $\{g' \in G | g' = ghg^{-1}, h \in H\}$. 

For $1 \to 2$, since $H$ is closed under conjugation, we have $gHg^{-1} \subseteq H$ for any $g$; for the other direction, since $g^{-1}Hg \subseteq H$ as well, we can then multiply on both sides to get $H \subseteq gHg^{-1}$; thus $H = gHg^{-1}$. $2 \to 1$ is trivial. For $2 \to 3$,  multiplying both sides of $H = gHg^{-1}$ on the right by $g$ gets $Hg = gH$, and doing the same argument in reverse shows $3 \to 2$. $3 \to 4$ is trivial. Then for $4 \to 3$, suppose that for all $g$, there exists $g'$ with $gH = Hg'$. This means in particular that $g \in Hg'$. Note also that the right cosets partition $H$, so $Hg'$ must be the only right coset containing $g$. But $Hg$ contains $g$, so we must have $Hg' = Hg$, and so $gH = Hg$. 

Some more facts related to normal subgroups:

(a) if $H \leq G$ then $gHg^{-1} \leq G$
(b) if there is only one subgroup $H \leq G$ of order $r$, then $H$ is a normal subgroup of $G$.

For (a), conjugation is an automorphism, so it maps subgroups to subgroups.

For (b), we know that if $H \leq G$ has order $r$ then so does $gHg^{-1} \leq G$. If $H$ is the only subgroup with order $r$ then they must be the same. 

# Correspondence Theorem
Take a homomorphism $\phi: G \to G'$, and let $H \leq G$; we can restrict $\phi$ to $H$, getting a homomorphism $\phi_H: H \to G'$. As some fairly trivial observations we have $\im(\phi_H) = \phi(H)$, $\ker(\phi_H) = H \cap \ker(\phi)$. Since $\im(\phi_H)$ is a subgroup of $G'$, its order divides the order of $G'$, and also of $H$ (since it's equal to $[H, \ker_H(\phi)]$). A consequence of this is that if $|H|, |G'|$ are coprime, then $\im(\phi_H)$ has order 1,  meaning $H$ just gets mapped to the identity in $G'$, meaning that $H \leq \ker(\phi)$. 

As an example of applying this: take the sign homomorphism, $S_n \to \{\pm1\}$; if $H$ is a subgroup of $S_n$ with odd order, then $\gcd(H, \{\pm 1\}) = 1$, meaning that $H$ is in fact a subgroup of the kernel, i.e. the alternating group. For instance, an odd-length cycle permutation generates a cyclic group of odd order, so that cyclic group must be a subgroup of $A_n$; thus all odd-length cycles are even permutations. 

Another related proposition: let $\phi: G \to G', H' \leq G'$; define $H$ to be $\phi^{-1}(H')$--the subset of elements of $G$ that map to $H'$. Also, let $K = \ker(\phi)$. Using this notation, we can say:

(1) $H \leq G$, and $H$ contains $K$
(2) if $H'$ is a normal subgroup of $G'$, then $H$ is a normal subgroup of $G$. 
(3) if $H$ is a normal subgroup of $G$, and $\phi$ is surjective, then $H'$ is a normal subgroup of $G'$. 

Proof:

For (1), we know that the identity of $G'$ is in $H'$, so $\phi^{-1}(1_{G'}) \subseteq H$, but that just means that $K \subseteq H$. This means also that $1_G \in H$ (giving us one of the conditions to be a subgroup); also, if $g_1, g_2 \in H$, then $\phi(g_1), \phi(g_2) \in H'$, which means (since $H'$ is a subgroup) that $\phi(g_1)\phi(g_2) \in H'$, or (since $\phi$ is a homomorphism) that $\phi(g_1g_2) \in H'$, and that means, by definition of $H$, that $g_1g_2 \in H$. This gives us closure. Then for inverses, if $\phi(g) \in H'$ then $(\phi(g))^{-1} \in H'$, but that equals $\phi(g^{-1})$, so $g^{-1} \in H$ as well.

For (2), let $g \in G, h \in H$. Then since $H'$ is normal and $\phi(h) \in H'$, $\phi(g)\phi(h)\phi(g^{-1}) \in H'$, or $\phi(ghg^{-1}) \in H'$, meaning $ghg^{-1} \in H$, as desired. 

For (3), suppose $\phi$ is surjective, and let $h' \in H', g' \in G'$ be arbitrary. Since $\phi$ is surjective there exists $h, g \in G$ with $\phi(g) = g', \phi(h) = h'$ (and $h \in H$ given how $H$ was defined). Since $H$ is normal, $ghg^{-1} \in H$, so $\phi(ghg^{-1}) \in H'$, or $\phi(g)\phi(h)\phi(g^{-1}) \in H'$, meaning that $g'h'(g')^{-1} \in H'$, as desired. 

As an example using (2), since the set of positive reals is a normal subgroup of the multiplicative group of reals, and the positive reals are the image, under the det homomorphism, of the matrices with positive determinant, the matrices with positive determinant are a normal subgroup (conjugation, i.e. change of basis, won't change the sign of the determinant).

All this leads us into the correspondence theorem itself: let $\phi: G \to G'$ be a surjective homomorphism; then there exists a bijection between the set of subgroups of $G'$, and the set of subgroups of $G$ that contain the kernel. 

This bijection is given by sending $H' \leq G'$ to $\phi^{-1}(H')$ (call it $H$), and sending $H \leq G$ to $\phi(H)$. 

Also, this correspondence satisfies the following properties: 

(1) $H$ is normal iff its corresponding subgroup $H'$ is normal 
(2) $|H'|\cdot|\ker(\phi)| = |H|$ 

We know from before that $\phi^{-1}(H)$ is a subgroup of $G$ containing $K$, and $\phi(H)$ is then a subgroup of $G'$, equal to $\im(\phi_H)$. That $H'$ is a normal subgroup of $G'$ if and only if $H$ is a normal subgroup of $G$ again follows from what we know (here the assumption of surjectivity was necessary). All we have left to show is that $\phi$ is a bijection, and that property (2) above holds. 

For (2), this follows from the counting formula.  $H' = \im(\phi_H)$, and $|\im(\phi_h)| = [H : K]$; but by the counting formula, $|H| = [H : K] \cdot |K| = |\im(\phi_H)| \cdot |K|$ .
# Product Groups
Given any two groups $G_1, G_2$, we can define a group structure on the product $G_1 \times G_2$ by $(g_1, g_2)(g_1', g_2') = (g_1g_1', g_2g_2')$. This has an identity (consisting of the pair $(1_{G_1}, 1_{G_2})$), inverses in the same way, etc. 

We then have natural homomorphisms $G_1 \to G_1 \times G_2$, $G_2 \to G_1 \times G_2$ (called the inclusion maps, say $i_1$ and $i_2$), and then in the other direction (called the projection maps, say $p_1, p_2$. ) $i_1$ is defined by $i_1(g_1) = (g_1, 1_{G_2})$ (and much the same for $i_2$), and then $p_1$ is defined as $(g_1, g_2) = g_1$, and ditto for $p_2$. The inclusion maps are injective, and the projection maps are surjective, for obvious reasons. 

Cyclic groups of composite order can be naturally decomposed into products of smaller cyclic groups. Namely, letting $n, m$ be coprime, then $C_{nm}$ is isomorphic to  $C_n \times C_m$. 

Proof: let $C_n = \langle x \rangle, C_m = \langle y \rangle$; we now claim that $C_n \times C_m = \langle (x, y) \rangle$, so that $C_n \times C_m$ is cyclic. (That $C_n \times C_m$ has $nm$ elements is clear, so as long as we can prove that it's cyclic, we'll know that it's isomorphic to $C_{nm}$.) We can show this by proving that the order of $(x, y)$ is $nm$. Certainly $(x, y)^{nm} = (x^{nm}, y^{nm}) = ((x^n)^m, (y^m)^n) = (1, 1)$. More generally, for a power $(x, y)^r$, take $r = pn + l = qm + k$; so $(x, y)^r = (x^{pn + l}, y^{qm + k})$ Suppose that this equals $(1, 1)$; then $l = k = 0$, so $r$ is divisible by both $n$ and by $m$, and since those are coprime, $r$ must be divisible by $nm$. Thus $nm$ is the least integer with $(x, y)^r = (1, 1)$, so $(x, y)$ has order $nm$, as desired. 

## Finding Groups Isomorphic to a Product Group
Given two subgroups $H \leq G, K \leq G$, we might want to know when $G$ is isomorphic to $H \times K$. To do this, we use a map $f: H \times K \to G$ defined by $(h, k) \to hk$, and then look for when $f$ is an isomorphism.

(1) $f$ is injective iff $H \cap K = \{1\}$. 
(2) $f$ is a homomorphism iff, for all $h \in H, k \in K, hk = kh$ -- all the elements of $H$ commute with all the elements of $K$. 
(3) if $H$ is normal, then $H \cdot K \leq G$, defining $HK$ to be the set of all products with one element from $H$, one element from $K$. (Note that $H \cdot K$ will be the image of the product map $f$ defined above.)
(4) $f$ is an isomorphism iff $H$ and $K$ are normal subgroups, their intersection is trivial, and $H \cdot K = G$. (This then gives us the condition we're looking for.)

Put note here on why if $H \times K$ and $G$ are isomorphic, this map must be an isomorphism.

For (1), take $g \in H, g \in K$. $g^{-1} \in H$ as well, so $(g^{-1}, g) \in H \times K$. But taking $f(g^{-1}, g)$ we get $g^{-1}g = 1$. Assuming $f$ is injective, and using the fact that $f(1, 1) = 1$, we know $(g^{-1}, g) = (1, 1)$, meaning that $g = 1$. For the other direction, suppose $H \cap K = 1$. Take $h, k, h', k'$ with $f(h, k) = f(h', k')$, or $hk = h'k'$. This means $h^{-1}h' = k(k')^{-1}$; since $h^{-1}h' \in H, k(k')^{-1} \in K$, and since by assumption the intersection is trivial, we have $h^{-1}h' = k(k')^{-1} = 1$. Thus $h' = h, k' = k$, so $f$ is injective.

For (2), suppose $f$ is a homomorphism, so $f(h_1, k_1)f(h_2, k_2) = f((h_1, k_1) \cdot (h_2, k_2)) = f((h_1h_2, k_1k_2)) = h_1h_2k_1k_2$. Conversely $f(h_1, k_1)f(h_2, k_2) = h_1k_1h_2k_2$. Thus $h_1h_2k_1k_2 = h_1k_1h_2k_2$. Then we can cancel to get $h_2k_1 = k_1h_2$ for arbitrary $h_2 \in H, k_1 \in K$. Running the argument in reverse gets the other implication

For (3), suppose $H$ is normal in $G$, and take $H \cdot K$, the set of all products of the form $hk$. Clearly this will have the identity (since $1 \in H, 1 \in K$). For closure and inverses, we need the normality of $H$. For closure, take $h_1k_1 \cdot h_2k_2$; we want to show that it equals $h'k'$ for some $h', k'$. We can conjugate by elements of $K$: insert a $k_1^{-1}k_1$ between $h_2$ and $k_2$ to get $h_1(k_1h_2k_1^{-1})k_1k_2 = h_1h_3k_1k_2$ and certainly $h_1h_3 \in H, k_1k_2 \in K$. For inverses....

For (4), suppose $f$ is an isomorphism; the injectivity of $f$ implies that $H \cap K$ is trivial and the surjectivity of $f$ implies that the image of $f$, i.e. $H \cdot K$, is $G$. Now to show that $H$ and $K$ are normal, consider the inclusion map $i_1: h \to (h, 1)$, which has an image in $H \times K$ isomorphic to $H$. But that image is normal in $H \times K$: given $(h_1, 1) \in H \times K$, if we conjugate by $(h_2, g_2)$ we get $(h_2, g_2)(h_1, 1)(h_2^{-1}, g_2^{-1}) = (h_2h_1h_2^{-1}, g_2g_2^{-1}) = (h_2h_1h_2^{-1}, 1)$, which is of the form $(h, 1)$ for some $h \in H$. Thus the image of $H$ is a normal subgroup in $H \times K$; since $f$ is an isomorphism, which takes normal subgroups to normal subgroups, and it takes the image of $H$ to $H$, $H$ must be a normal subgroup of $G$. We can repeat the same argument to show that $K$ is normal.

For the other direction, bijectivity follows from the fact that $H \cap K$ is trivial and $H \times K = G$. What we need now is to show that $f$ is a homomorphism. By (2) we can instead show that all elements of $H$ commute with all elements of $K$...

# Quotient Groups
Recall that, given a subgroup $H$ of $G$, we naturally have the equivalence relation of congruence, given by $g \sim g'$ if and only if $g, g'$ are in the same coset of $H$. 

Given a normal subgroup $N$, we can put a group structure on the cosets of $N$. Notation: if $C$ is a coset $aN$ we denote it $[C]$ or $\bar{a}$, and the set of all such cosets is $G/N$. 

Theorem: let $N$ be a normal subgroup of $G$; then we can define an operation on $G/N$ such that the map $a \to \bar{a}$ is a surjective homomorphism with kernel $N$. As a consequence, every normal subgroup is the kernel of a homomorphism. (This map $\pi: G \to G/N$ is called the "canonical" quotient map.)

Proof: first we need to show that the operation actually turns $G/N$ into a group. Take $aN, bN, cN \in G/N$. We know that, assuming $N$ is normal, $aN \cdot bN = abN$ (where $A \cdot B$ is the set of all products of an element of $A$ and an element of $B$). We can rewrite $aN \cdot bN$ as $a(Nb) \cdot N$. By normality, $Nb = bN$, so this gives $ab(N \cdot N)$, but $N \cdot N = N$, so we get $abN$. We can now define an operation on cosets by $[aN] \cdot [bN] = [abN]$. This satisfies associativity ($(aN \cdot bN) \cdot cN = abN \cdot cN = abcN = aN \cdot (bN \cdot cN)$), identity ($aN \cdot N = (a1)N = aN$), and inverses $(aN \cdot a^{-1}N = aa^{-1}N = N)$. Also, $\pi$ is a homomorphism, as $\pi(a \cdot b) = \overline{ab} = [abN] = [aN] \cdot [bN] = \bar{a} \cdot \bar{b} = \pi(a) \cdot pi(b)$. (In fact, we could have proven that $G/N$ is a group using only the fact that $\pi$ is "multiplicative": if we have a surjective function $\phi: G \to S$ with the main homomorphism property, $\phi(ab) = \phi(a)\phi(b)$ and $G$ is a group, then $S$ is a group and $\phi$ is a homomorphism.) All we need now is that $N$ is the kernel. Certainly $N \subseteq K$, since anything in $N$ gets mapped to $[N] = \bar{1}$ which is the identity in $G/N$. Conversely anything that gets mapped to $\bar{1}$ must be congruent to $\bar{1}$ and thus be in $N$, so $K \subseteq N$ and so $K = N$. 

## First Isomorphism Theorem
Let $\phi: G \to G'$ be a surjective homomorphism with $\ker(\phi) = K$ (which is then a normal subgroup of $G$). There exists a unique isomorphism $\bar{\phi}: G/K \to G'$ such that $\bar{\phi} \circ \pi = \phi$. 

Proof: we already know that the fibers of $\phi$ are the cosets of $K$; this gives us a bijection between $G/N$ and the fibers of $\phi$. Define $\bar{\phi}(\bar{a}) = \phi(a)$. We then have $\bar{\phi}(\pi(a)) = \bar{\phi}(\bar{a}) = \phi(a)$, which takes care of one of the conditions. What we need to show now is that $\bar{\phi}$ is an isomorphism and that it is the only isomorphism satisfying the relevant property. That $\bar{\phi}$ is a homomorphism is easy to get: $\bar{\phi}(\bar{a}\bar{b}) = \bar{\phi}(\overline{ab}) = \phi(ab) = \phi(a)\phi(b) = \bar{\phi}(\bar{a}) \cdot \bar{\phi}(\bar{b})$. The surjectivity of $\bar{\phi}$ follows from the surjectivity of $\phi$. Now to prove that $\bar{\phi}$ is injective, suppose we have $\bar{a}, \bar{b} \in G/N$ with $\bar{\phi}(\bar{a}) = \bar{\phi}(\bar{b})$; then $\phi(a) = \phi(b)$, which means $a = bk$ for some $k \in K$. This then implies $a \in bK$ or $\bar{a} = \bar{b}$, so $\bar{\phi}$ is injective. We now have everything except uniqueness. Suppose $\bar{\psi}$ is another isomorphism with $\bar{\psi} \circ \pi = \phi$. Then $(\bar{\psi} \circ \pi)(a) = (\bar{\phi} \circ \pi)(a)$ for all $a$, 

