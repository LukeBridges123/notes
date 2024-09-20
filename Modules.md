# Definitions
On a commutative ring $R$, we can define a structure like a vector space, called a module. An $R$-module $M$ is an abelian group (with operation $+$) with a scalar multiplication operation. More precisely this is a function $R \times M \to M$ satisfying a few axioms: for all  $a, b \in R, m, n \in M$, we have that $1m = m$ that $a(bm) = (ab)m$, that $(a + b)m = am + bm$, and that $a(m + n) = am + an$. If $R$ is a field then the module is just a vector space. 

$R$-module homomorphisms are defined just like linear maps: we must have $\phi(am + bn) = a\phi(m) + b\phi(n)$ for all $a, b \in R$ and $m, n \in M$. More formally it is just a group homomorphism where we also have $\phi(am) = a\phi(m)$. The same goes for submodules, which are defined analogously to subspaces: they are subgroups of $M$ that are closed under scalar multiplication. 

Any ring $R$ is an $R$-module over itself, and $R^n$ is an $R$-module with operations defined componentwise, just like for the vector space $F^n$. Note that considering a ring as a module over itself is a bit less trivial than considering a field as a vector space over itself. This is because submodules of $R$ are ideals of $R$ and vice versa, and we can have some interesting ideals, whereas for fields, the only ideals (and so the only subspaces) are $\{0\}$ and the whole field. 

Also like with vector spaces, we can form direct sums of modules, $M_1 \oplus M_2$, the set of ordered pairs of elements of $M_1$ and elements of $M_2$, with addition and scalar multiplication defined componentwise. We can in fact define the direct sum of an indexed collection of modules: elements of these then look like finite tuples $(m_1, \dots, m_n)$, or countable tuples $(m_1, m_2, \dots, m_n, \dots)$ or even uncountable "tuples"; however we require that all but finitely many of the components of a given tuple are zero. The "direct product" of modules is the direct sum with this restriction on the components removed; thus, for example, the direct sum of countably many copies of $\Z$ is isomorphic (as a module) to $\Z[x]$, while the direct product of countably many copies of $\Z$ is the module of all sequences of integers. For finite direct products and sums, this distinction does not matter. 

# Free Modules, Bases, Etc.
We call an $R$-module free if it's isomorphic to some direct sum of copies of $R$, $\oplus_{a \in A} R$ for some set $A$. This could be $R^n$, or $R^\infty$ where each sequence has only finitely many nonzero terms, and so on. Note that this is equivalent to having a basis: if there is a basis then we can use that to construct an isomorphism with $R^n$ (or the suitable infinite-dimensional generalization), and if there is such an isomorphism $\phi$, then we can use the images of the standard basis vectors in $R^n$, say $e_1, e_2, \dots$ as a basis, i.e. $\phi(e_1), \phi(e_2), \dots$ is a basis. If $R$ is a field then every module is free. 

Over arbitrary rings, however, we may not be able to find a basis. E.g. $\Z/10\Z$ is a module over $\Z$ but is not free. In a PID $R$, considered as a module over $R$, every ideal is a free module over $R$; we have an isomorphism $R \to I = (a)$ given by $f(x) = ax$. 

Analogously to finite-dimensional vector spaces, we have finitely generated modules, i.e. modules where there exists finitely many elements $m_1, \dots, m_n$  such that every element of the module is a linear combination of those elements. Note that unlike for vector spaces, finitely generated does not imply free. A module $M$ is finitely generated iff there exists a surjective homomorphism $R^n \to M$; we just map the $n$-tuple $(r_1, \dots, r_n)$ onto $r_1m_1 + \dots + r_nm_n$ where the $m_i$ are the generating set; this is clearly a homomorphism, and is surjective because the $m_i$ generate the module. If there exists, not just a surjective homomorphism, but an isomorphism, recall that this means the module is free. 

# Abelian groups and Z-modules
As an application of these ideas, we note that every abelian group can be given a $\Z$-module structure in a unique way. Of course every $\Z$-module is an abelian group, so what this basically shows is that "$\Z$-module" and "abelian group" are just different names for the same thing. Let $A$ be an abelian group with operation $+$; define the scalar multiplication $na$ to be $a + \dots + a$ ($n$ times) for positive $n$, $-a + (-a) + \dots + (-a)$ ($|n|$ times) for negative $n$, and $0$ if $n$ is $0$.  

# Polynomials and R-modules
If $M$ is an $R$-module and $\phi$ is a module homomorphism $M \to M$, there is a unique way to turn $M$ into a module over $R[x]$, such that $xm = \phi(m)$ and $rm$ (in the new scalar multiplication) equals $rm$ (in the old scalar multiplication). Proof: all we need to do is define scalar multiplication; now the scalars are polynomials, $r_0 + r_1x + \dots + r_nx^n$. What we do is define $p(x)m = r_0m + r_1\phi(m) + r_2\phi(\phi(m)) + \dots + r_n\phi^n(m)$. We then clearly have $xm = \phi(m)$; checking that it satisfies the scalar multiplication axioms is easy. 

Suppose that $R = \C$. Then a vector space $V$ over $\C$ with a linear map $T: V \to V$ is equivalent to a $\C[x]$-module. 

# Modules over Noetherian Rings
Every subspace of a finite-dimensional vector space is finite-dimensional; this need not be the case for finitely generated modules. We do however have the following theorem: if $R$ is Noetherian and $M$ is a finitely-generated $R$-module, then any $R$-submodule $N$ of $M$ is finitely generated. (When $R$ is non-Noetherian, we can have finitely generated modules with submodules that aren't finitely generated. Also note that a submodule of a module $M$ might have larger rank than $M$; compare to the situation in vector spaces, where subspaces always have dimension at most that of the parent space.)

Proof: since $M$ is finitely generated we have a surjective homomorphism $B: R^n \to M$. For any submodule $N$ there corresponds a submodule of $R^n$, namely $B^{-1}(N)$; call this $\ol{N}$. We just need to show that this submodule is finitely generated, using induction on $n$. When $n=1$, $\ol{N}$ is a submodule of $R$, i.e. an ideal of $R$, and since $R$ is Noetherian $\ol{N}$ must be finitely generated. 

Now for the induction step, suppose that this is true for $n$, i.e. every module over a Noetherian ring generated by $n$ elements has this property. Let $\pi$ be the map that projects an element $(r_1, \dots, r_{n+1})$ of $R^{n+1}$ to $(r_1, \dots, r_n)$ in $R^n$. Then $\pi(\ol{N})$ is a submodule of $R^n$ which is finitely generated by induction. Choose generators $v_1, \dots, v_k$ for $\pi(\ol{N})$, and corresponding elements $n_1, \dots, n_k$ in $\ol{N}$ which get mapped to $v_1, \dots, v_k$ respectively. Now let $\ol{n} \in \ol{N}$. We have $\pi(\ol{n}) = r_1v_1 + \dots + r_kv_k$ since $\pi(\ol{n}) \in \pi(\ol{N})$. Thus $\pi(\ol{n} - r_1\ol{n_1} - \dots - r_k\ol{n_k}) = 0$, by linearity. This difference is in the kernel of $\pi$, which is just all the vectors in $R^{n+1}$ with zeros except in their last entry. Thus $\ol{n} - \sum r_n \ol{n}_i$ is an element of $\ker(\pi)$ and $\ol{N}$, i.e. an element of their intersection. This is a submodule of $\ker(\pi)$, which is isomorphic to $R$, and so $\ker(\pi) \cap \ol{N}$ is isomorphic to a submodule of $R$, i.e. an ideal of $R$, which has generators $t_1, \dots, t_l$, and adding those onto the $n_i$ gives us generators for $N$.  

(something on free resolution of modules)

# Hilbert Basis Theorem
This says that if $R$ is a Noetherian ring then $R[x]$ is also Noetherian. 

Proof: let $I \subseteq R[x]$ be an ideal of $R[x]$. For any element $a_nx^n + \dots + a_0$ in $I$, look at its leading coefficient $a_n$. Let $J$ be the set of all leading coefficients of nonzero elements in $I$, as well as $0$. We claim that this is in fact an ideal. For if $a$ and $b$ are leading coefficients of $f(x), g(x) \in I$, then (supposing WLOG that $\deg(f(x)) \geq \deg(g(x))$ ) we have that $f(x) + x^{\deg(f) - \deg(g)}g(x)$ has leading coefficient $a + b$ and is in $I$. Thus $J$ is closed under addition. We can run a similar argument to show that $J$ is closed under multiplication by arbitrary elements of $R$. Since $J$ is an ideal of $R$ and $R$ is Noetherian, $J$ is finitely generated, say by $a_1, a_2, \dots a_m$. (Recall that this means any element of $J$ is of the form $\sum r_ia_i$ where $r_i$ are arbitrary elements of $R$, not necessarily in $J$ itself.) Each of those leading coefficients is the leading coefficient of some $f_i(x) \in I$. We hope to show that these $f_i$ generate $I$. Let $f(x) \in I$ be an element of minimal degree $d$. If $d \geq \max(\deg( f_i))$, letting $a$ be the leading coefficient of $f$, we have $a = r_1a_1 + \dots + r_ma_m$, and so $f$ has the same leading coefficient as $r_1x^{d - d_1}f_1(x) + \dots + r_mx^{d - d_m}f_m(x)$, letting $d_i$ be the degree of $f_i$. This however gives a contradiction: $f(x)$ minus that whole thing is still in $I$ but has degree strictly less than $d$, since subtracting that kills the leading term of $f$. This contradicts the supposed minimality of $d$. We'll have to expand our list of generators to make this work. 

Let $J_0$ be the leading coefficients of all $f \in I$ with degree $0$, ditto for $J_1$, and so on, all the way up to $J_{\max - 1}$ where $\max = \max(\deg(f_i))$. (With $0$ tacked onto all of these sets.) These are all finitely generated: we end up with, say, generators $a_{00}, a_{01}, \dots a_{0n_0}$ for $J_0$, and so on for each of the (finitely many) ideals here. Putting these all together, we still have finitely many generators $a_{ij}$, corresponding to the polynomials $f_{ij}(x)$ of which they are leading coefficients. We don't know exactly how many polynomials we have, but we certainly have finitely many, the $f_{ij}$ and the $f_i$ from before.

We claim that, putting all these together ($f_1, \dots, f_m, f_{00}, f_{01}, \dots f_{0n_0}, \dots, f_{\max - 1, 0}, \dots, f_{\max - 1, n_{\max - 1}}$)these are generators for $I$. As before, let $f$ be an arbitrary element of minimal degree $d$; now suppose for a contradiction that it is not in the "span" of all these generators....
# Modules over PIDs
We have the following "structure theorem" for modules over PIDs: if $M$ is a finitely generated module over a PID $R$, then $M$ is isomorphic to $R^r \oplus R/(a_1) \oplus \dots \oplus R/(a_k)$: a direct sum of $R^r$ and some quotients of $R$. (N.B. the $a_i$ can be assumed to be neither units nor $0$.) The $R^r$ part is called the "free" part, while the rest is called the "torsion". 
Note that the $r$ appearing here is unique, but the $a_i$ can be "split up" in various ways; there is not always one way to express it. For instance $\Z/6\Z$ is isomorphic to $\Z/2\Z \oplus \Z/3\Z$. The closest you can get to a "canonical" form for the torsion is to split it up into quotients by powers of irreducibles.
## Some Lemmas
We'll need three main things for the proof:

1) any $R$-module homomorphism from $R^m$ to $R^n$, or more generally between two free $R$-modules, is given by an $n \times m$ matrix $A$ with entries in $R$. The proof is exactly the same as for vector spaces.
2) A homomorphism $R^n \to R^n$ is invertible if and only if the determinant of its matrix $A$ is a unit in $R$. Proof: the implication "invertible implies determinant is a unit" works just like in linear algebra: we have $\det(AB) = \det(A)\det(B)$, so $\det(A^{-1})\det(A) = \det(AA^{-1}) = \det(I) = 1$,  so $\det(A)$ has an inverse, namely $\det(A^{-1})$. (Note that $\det(AB) = \det(A)\det(B)$ holds for any ring.) The converse follows like this: we have the formula from linear algebra $A^{-1} = \frac{1}{\det(A)}\text{adj}(A)$ where "adj(A)" is the "adjugate matrix", something made from determinants of the minors of $A$ in a certain way. As long as we can divide by $\det(A)$ this holds in any ring; so if $\det(A)$ is a unit, $A$ has an inverse given by this formula.
3) The facts above don't just hold for PIDs--this one does. Namely, if $a, b \in R$, then $(a) + (b) = (d)$ where $d = \gcd(a, b)$ (defining the greatest common divisor to be an element--unique up to multiplication by units--such that $d \mid a, d \mid b$, and if $c \mid a$ and $c \mid b$, then $c \mid d$ (the "greatest" part)). 
Now we move on to the proof.
## Proof part 1: using Smith normal form
Since $M$ is finitely generated, say with generators $m_1, m_2, \dots, m_n$, we have a surjective homomorphism $B: R^n \to M$. If this is also injective then we're done: $M$ is free, and so isomorphic to $R^n$. Otherwise, look at the kernel $K \subseteq R^n$. Recalling that $K$, as a submodule of a finitely generated module over a Noetherian ring, is also finitely generated, we have a surjective homomorphism $R^k \to K$. Composing this with the inclusion (kinda) map $K \to R^n$ we get a homomorphism $A: R^k \to R^n$. By the first isomorphism theorem, $M$ is isomorphic to $R^n / \ker(B) = R^n / \im(A)$. So, we'll want to study $R^n / \im(A)$, and we'll see that it's the torsion part described earlier.

A lemma: let $A$ be an $n \times m$ matrix with coefficients in $R$. Then there exist invertible $R$-matrices $S, T$ such that $SAT$ is diagonal, say with $d_1, d_2, \dots$ on the diagonal. ($S$ is $n \times n$, while $T$ is $m \times m$.) Note that since $A$ may be nonsquare we might get a "diagonal" matrix with some zero rows beneath it the diagonal part or zero columns to the right. 

Before we prove it, since it's a little annoying, let's see how it gets used in the proof. If $A$ is already diagonal with $d_1, d_2, \dots$ on the diagonal, and zero columns beside the diagonal part, then the image of $A$ consists of vectors with a multiple of $d_1$ in the first coordinate and so on. So $\im(A) = (d_1) \oplus (d_2) \oplus \dots$ Then $R^n / \im(A) = R / (d_1) \oplus R / (d_2) \oplus \dots \oplus R / (d_n)$. If you instead have zero rows, then we end up with $\im(A) = (d_1) \oplus (d_2) \oplus \dots \oplus (d_m) \oplus \{0\}^{n-m}$, and quotienting gets us a bunch of quotients $R / (d_i)$ direct summed to $R^{n - m}$. 

Now suppose that $A$ may not already be diagonal; we can diagonalize as $SAT = D$ for some diagonal $D$. Note that, since $T$ is invertible, $\im(AT) = \im(A)$; but $\im(SA) \neq \im(A)$: $S$ may take things in the image of $A$ outside of the image of $A$. But we can still say at least that $\im(SA)$ is isomorphic to $\im(A)$, since $S$ is (the matrix of) an isomorphism. Thus $\im(SAT)$ is isomorphic to $\im(A)$, and we can describe $\im(A)$ in terms of the image of its diagonalization $SAT$. We can then use the reasoning in the previous paragraph to describe $\im(A)$, and thus $M$, as a direct sum of things of the form $R/(d)$ and $R$. 

This gives us exactly the theorem we're looking for; all we have left to do is prove the theorem about diagonalization that we used along the way. 
## Proof part 2: proving Smith normal form
# Jordan Form Revisited
Let $V$ be a vector space over a field $F$, and let $T$ be a linear transformation. It turns out that we can turn $V$ into a module over $F[x]$, defining scalar multiplication by $x$ in terms of applying $T$. That is, for any $v \in V$ we define $xv = Tv$; more generally, for a polynomial $a_nx^n + \dots + a_1x + a_0$ we have $(a_nx^n + \dots + a_1x + a_0)v = a_nT^nv + \dots + a_1Tv + a_0v$. Then all the relevant axioms hold, in particular using the distributivity of matrix multiplication and the fact that polynomials of operators can be multiplied just like regular polynomials. 

Now $V$, considered as an $F[x]$ module, is finitely generated: the basis $v_1, \dots, v_n$ serves as a set of generators. However, it may not be a free module: these could be linearly dependent over $F[x]$. At any rate, since it is finitely generated, we can apply the structure theorem to get that $V$ (as an $F[x]$ module) is isomorphic to $F[x]/(f_1(x)) \oplus \dots \oplus F[x]/(f_k(x))$. (There is no free part $F[x]^r$ because $V$ is finite-dimensional....) In other words each element of $V$ can be viewed as a "vector" of polynomials $p_i \pmod{f_i(x)}$ --or rather elements of quotients of $F[x]$. Then applying $T$ gives us a vector of polynomials $xp_i \pmod{f_i(x)}$. $V$ is itself a free module over $F$, with a basis given by $v_1, \dots, v_n$, say, while that direct sum is also a free module over $F$. Say, for instance, that $f_i(x)$ has degree $d_i$: then $\{\ol{1}, \ol{x}, \dots, \ol{x^{d-1}}\}$ is a basis for $F[x]/(f_i(x))$, and gluing all those bases together gets us a basis for $\oplus_{i=1}^k F[x]/(f_i(x))$. In each of these quotients, the "multiplication by x" map is $F$-linear, and its matrix in the relevant basis is the companion matrix of $f_i$. If we direct-sum all these companion matrices we get the "rational canonical form" for $T$. 

The characteristic polynomial of $T$ is the product of all these $f_i$. Now consider the minimal polynomial $p$; if we multiply the element $(1, \dots, 1)$ of the $F[x]$ module by $p$ we should get $(0, \dots, 0)$ which implies that all of the $f_i$ divide $p$. Since $p$ is supposed to be the polynomial of least degree with this property, $p$ must be the least common multiple of the $f_i$. 

We can use the Chinese remainder theorem to shuffle things into the form $F[x]/(\pi_1(x)^{e_1}) \oplus \dots \oplus F[x]/(\pi_m(x)^{e_m})$ where all of the $\pi_i$ are irreducible. If $F$ is algebraically closed then everything splits completely into linear factors, and we can assume that each $\pi_i$ is of the form $(x - \lambda_i)$. Now consider what happens when we use, as a basis for $F[x]/((x - \lambda_i)^{e_i})$, the polynomials of the form $\ol{(x - \lambda)^j}$. We then get that, 