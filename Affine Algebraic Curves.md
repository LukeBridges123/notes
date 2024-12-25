# Definitions
For a given field $K$, "affine n-dimensional space" $\A^n$ is the set of all $n$-tuples $(x_1, \dots, x_n)$ with coordinates in $K$; we also denote it $A_K^n$ or $K^n$. 

In 2-dimensional space, a polynomial $p \in K[x, y]$ is called an algebraic curve. Similarly a single polynomial in $K[x, y, z]$ is called an algebraic surface, and more generally a polynomial in n variables gives an (n-1)-dimensional "hypersurface". (More precisely, we typically define a curve to be an equivalence class of polynomials, where if one polynomial is a scalar multiple of another they are equivalent.)

Each curve determines a set of points in the plane: the set of all $(x, y) \in \A^2$ with $f(x, y) = 0$. This is called the "zero locus" of $f$ and denoted $V(f)$. More generally, we can take several curves $f_1, \dots, f_n$ (or polynomials in more variables) and consider their "common zero locus"--the set of all points with $f_i(x, y) = 0$ for all $i$. Geometrically, this is the set of points where the $f_i$ all intersect. We denote it $V(f_1, \dots, f_n)$. 

Finally, we can consider arbitrary (not necessarily finite) sets of polynomials. The common zero locus of a set of polynomials is called an *affine variety*. 

Arbitrary intersections of varieties are also varieties: if $S, T$ are sets of polynomials, then $V(S) \cap V(T)$ is just $V(S \cup T)$, the common zero locus of all polynomials in $S$ and all polynomials in $T$. At least if we limit ourselves to finite sets of polynomials, finite unions of varieties are also varieties: the union of $V(f)$ and $V(g)$ is $V(fg)$, since $(fg)(p) = 0$ if and only if $f(p) = 0$ (so $p \in V(f)$) or $g(p) = 0$ (so $p \in V(g))$. By induction, the union of any finite number of curves is a variety. 

Since curves are (equivalence classes of) single polynomials, we can define the degree of a curve to be the degree of the corresponding polynomial. The notion of the degree of a variety (which may not, in general, be expressible as a single polynomial) is more subtle. 

# Reducibility and Components
An irreducible curve is a curve which is irreducible as a polynomial, i.e. cannot be factored into two non-units. If a curve $f$ is reducible, then we can factor it into a product of irreducible polynomials, $f = g_1^{a_1} \cdots g_n^{a_n}$. We say that $f$ can be decomposed into components $g_1, \dots, g_n$ with multiplicities $a_1, \dots, a_n$. If all of these multiplicities are $1$ then we say that $f$ is "reduced". 

The set of points of a reducible curve may be just a disjoint union of curves (as is the case for $(x^2 + y^2 - 1)(y - 2)$, the disjoint union of the unit circle and the line $y=2$), or its components might intersect (as is the case for $xy$, the union of the x-axis and y-axis, which intersect at $(0, 0)$.) Especially over fields which are not algebraically closed, a curve with multiple connected components may still be irreducible, as is the case for a hyperbola $x^2 - y^2 - 1$ with its two branches, or many elliptic curves (e.g. $y^2 - x^3 + 2x - 1$), which look like unions of a "closed loop" and a "branch of a hyperbola" but are not. A curve can also be empty (at least over a field which is not algebraically closed, e.g. the "imaginary circle" $x^2 + y^2 + 1$ over $\R$); since we define curves as polynomials, not as sets of points, two empty curves can still be distinct. 

## Curves are infinite, intersections are finite
Over an algebraically closed field, the zero locus of a non-constant curve $V(f)$ and its complement are both infinite. (For a constant curve $f = c$, either $V(f)$ is empty and its complement is all of $\A^2$, or vice versa.) Proof: we rewrite $f(x, y)$ as a polynomial in $x$ whose coefficients are polynomials in $y$ (assuming, without loss of generality, that $f$ contains nonzero powers of $x$; since it is not constant, it must contain nonzero powers of some variable). Then $f = p_n(y)x^n + p_{n-1}(y)x^{n-1} + \dots + p_0(y)$, where $p_n$, at least, is nonzero. There are infinitely many points in the base field $K$ (since it is algebraically closed), only finitely many of which are roots of $p_n(y)$. Hence there are infinitely many values of $y$ for which $f$ is a non-constant polynomial in $x$, and (since $K$ is algebraically closed) for each such $y$ there exists an $x$ with $f(x, y) = 0$. Thus $V(f)$ is infinite. But for a fixed $y$ with $p_n(y) \neq 0$, there are only finitely many roots of the corresponding polynomial in $x$, so there are infinitely many points where $f(x, y) \neq 0$ as well. 

On the other hand, two curves without a common component intersect in finitely many points. 

As before, we think of $f, g$ as polynomials in $x$ whose coefficients are polynomials in $y$, but now we regard the coefficients as being elements of the field of rational functions $K(y)$. Thus $f, g \in (K(y))[x]$. By the general result about polynomials with coefficients in a field, $(K(y))[x]$ is a principal ideal domain. Note also that $\gcd(f, g) = 1$, even when we think of them as elements of $(K(y))[x]$....

We thus have $(f) + (g) = 1$, so there exist polynomials $a, b \in (K(y))[x]$ with $af + bg = 1$. Clearing denominators of the coefficients in $K(y)$ gets $a'f + b'g = h$ where $a', b' \in K[x, y]$ and $h \in K[y]$ is nonzero. .....

If $p \in V(f, g)$ then $h(p) = a'(p)f(p) + b'(p)f(p) = 0 + 0 = 0$. Thus elements of $V(f, g)$ have a y-coordinate which is a root of $h(y)$, so there are only finitely many possible $y$-coordinates of points in $V(f, g)$. We can repeat the same argument with the roles of $x, y$ interchanged to get that there are only finitely many possible $x$-coordinates of points in $V(f, g)$, which implies that $V(f, g)$ contains at most finitely many points. 


If we restrict our attention to reduced (not necessarily irreducible) curves over an algebraically closed field, then a set of points uniquely determines a curve, i.e. we can "recover" $f$ from $V(f)$. 
# Examples

# The Local Ring
At any point $p$, we define the "local ring" $\mathcal{O}_p$ to be the ring of rational functions $\frac{f}{g}$ with $f, g \in K[x, y]$ and $g(p) \neq 0$. In other words, it is the ring of two-variable rational functions over $K$ that are defined at $p$. 

The local ring is not a field (rational functions with $f(p) = 0$ do not have a multiplicative inverse in $\mathcal{O}_p$), but it is an integral domain. Note that, if the numerator does not vanish at $p$, then $f/g$ is a unit. 

$\mathcal{O}_p$ has a single maximal ideal, denoted $I_p$ and defined as the set of functions where the numerator vanishes at $p$. It is the kernel of the "evaluation map" $\phi(f/g) = f(p)/g(p)$, which is a ring homomorphism that is well-defined for $\mathcal{O}_p$ but not for arbitrary rational functions. To prove that this is maximal, suppose it is strictly contained in some other ideal $I$. Then $I$ must contain a function whose numerator does not vanish at $p$; but by the previous paragraph, these elements are units. Thus $I = (1)$ and so $I_p$ is not contained in any other non-unit ideal. To prove that it is the only maximal ideal, note that $I_p$ contains all non-unit elements of $\mathcal{O}_p$. Thus any non-unit ideal must be a subset of $I_p$. 



