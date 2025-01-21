# The Hessian
The basic idea behind Morse theory is that we can understand the topology of a manifold in terms of the smooth functions on it. 

Recall that, letting $f: M \to \R$ be a smooth function, a point $p \in M$ is a critical point of $f$ if $df(p) = 0$; in that case $f(p)$ is a critical value. At a critical point, it is useful to look at the second derivative, which in coordinates is the Hessian matrix; abstractly, we define it to be the map $Hf_p: T_pM \times T_pM \to \R$, with $Hf_p(X, Y) = X(Y(f))$. (More precisely we take $X_p(Y(f))$ where we abuse notation a bit and let $Y$ be a vector field which is equal to the given $Y$ at $p$.)
## Hessian as a Symmetric Bilinear Form
It follows from this definition that, at a critical point, $Hf_p$ is a symmetric bilinear form. Bilinearity is obvious; for symmetry, we have $Hf_p(X, Y) - Hf_p(Y, X) = XYf - YXf = [X, Y]f = df[X, Y]$; since $df_p = 0$ (by the fact that $p$ is a critical point) we have $Hf_p(X, Y) - Hf_p(Y, X) = 0$. Note however that this definition requires extending $X$ and $Y$ (which strictly speaking are just tangent vectors at $p$) to vector fields locally; we now check that this does not depend on the extensions. Suppose $\tilde{X}, \tilde{Y}$ are other extensions of the same vectors; then in the first place $(Hf)_p(\tilde{X}, \tilde{Y}) = \tilde{X}(\tilde{Y}f) = X(\tilde{Y}f)$ automatically, since we only need $X, \tilde{X}$ at $p$ (see previous paragraph). ....
## Diagonalizing the Hessian
### Nondegeneracy
Since $Hf_p$ is a symmetric bilinear form, we can diagonalize it by an orthogonal change of coordinates, with just $1, -1, 0$ on the diagonal. If $Hf_p$ is a nondegenerate form, or equivalently if the diagonal form has no zeroes on the diagonal, then we say that $p$ is a nondegenerate critical point. 
### The Index of a Function
We call the dimension of the maximal subspace on which $Hf_p$ is negative-definite the "index" of $f$ at $p$, and typically denote it by $\lambda$; in coordinates, this is simply the number of $-1$s on the diagonal. (Another way to put it is that the index is the maximal number of linearly independent vectors with $Hf_p(X, X) < 0$.)


A standard example is the "height function" on a torus...insert link...critical points have indices 2, 1, 1, 0.

## Morse Coordinates
Let $p$ be a nondegenerate critical point of a function $f$ with index $\lambda$; then there exist local coordinates centered at $p$ in which $f(x) = f(p) + (x^1)^2 + \dots + (x^{n-\lambda})^2 - (y^1)^2 - \dots - (y^\lambda)^2$. Intiutively, this just says that at a critical point, $f$ is locally approximated by its Hessian, and so is locally a quadratic form. 

This is analogous to Darboux coordinates for symplectic forms. In both cases we are able to take a linear algebra result, which in principle applies only to a single tangent space, and extend it to everywhere in a neighborhood on the manifold. The difference is that Morse coordinates only exist near nondegenerate critical points, while Darboux coordinates exist everywhere. 

Proof: choose arbitrary coordinates $x^i$ centered at $p$ and let $B = B(0, \epsilon)$ be a ball in these coordinates. For $x \in B$ we have $f(x) = f(p) + \int_0^1 \pd{df}{dt}(tx)dt = f(p) + \sum_i \int_0^1 \pd{f}{x^i}(tx)\frac{d(tx^i)}{dt}dt$; $d(tx^i)/dt$ is just $x^i$. Similarly $\pd{f}{x^i}(tx) = \pd{f}{x^i}(0) + \sum_j \int_0^1 \pd{}{x^j}(\pd{f}{x^i})(stx) \frac{d(stx)}{ds}ds$. But $\pd{f}{x^i}(0) = 0$ (since $p$, which is $0$ in these coordinates, is a critical point of $f$). (CLEAN UP NOTATION LATER) Thus $f(x) = f(p) + h_{ij}(x)x^i x^j$ where $h_{ij} = \int_0^1 \int_0^1 \pd{^2 f}{x^i \partial x^j}(stx)ds dt$. This is symmetric with $h_{ij}(0) = \frac{1}{2}Hf_p$. Thus after a linear change of variables, we can diagonalize $h_{ij}$ and get the coordinates we want, at least at the origin itself. After using a procedure from elsewhere in the notes (FIND IT LATER) we can apply further smooth changes of coordinates so that $h_{ij}(x)$ is diagonal for all $x$ close enough to $p$. 

Observe that, in these coordinates, $0$ is the only critical point. (Just differentiating it as a function of the $x^i, y^j$, we see that the result is $0$ only at $0$, which is $p$.) Thus nondegenerate critical points are isolated--we can always find a ball in which a given critical point is the only critical point. 


# Gradient Flows
Lemma: for $a \in \R$, let $M^a$ be the set of all $x \in M$ with $f(x) \leq a$. Then, if $a$ is not a critical value, then $f^{-1}(a)$ is a submanifold of $M$, and $M^a$ is a manifold with boundary. The first part follows from the regular value theorem. For the second part, if $f(x) < a$ then we can shrink a chart $M \to \R^n$ that contains $x$ to get a chart $M^a \to \R^n$ that contains $x$. If $f(x) = a$, then since $a$ is not a critical value, the differential is surjective, and we can use the local submersion theorem to get coordinates in which $f^{-1}(a)$ is the set of all points of the form $(0, x^2, \dots, x^n)$, and $M^a$ is the set of all points $(x^1 , \dots, x^n)$ with $x^1 \leq 0$. But that means these coordinates are a chart into the upper half-space, hence $M^a$ is a manifold with boundary, whose boundary is $f^{-1}(a)$. 

Now choose a Riemannian metric $g(X, Y) = \langle X, Y \rangle$ on $M$. Then $\nabla f$ is the vector field given by identifying $df$, at each point, with a tangent vector, using the isomorphism between a vector space and its dual given by the inner product. That is, we define $\nabla f$ such that $\langle \nabla f, X \rangle = df(X) = Xf$ for all vector fields $X$. 

Then, as in calculus, $-\nabla f$ is orthogonal to level sets of $f$ and points in the "direction of fastest descent" of $f$; its flow is called the "downward gradient flow" of $f$. 
## First Deformation Lemma
We then have the "first deformation lemma": if $f^{-1}([a, b])$ is compact and contains no critical points, then $M^b$ is diffeomorphic to $M^a$ (the downward flow pushes $M^b$ into $M^a$), and the inclusion $M^a \subseteq M^b$ is a homotopy equivalence. Proof: by assumption, $\nabla f \neq 0$ everywhere in $\ol{V} = f^{-1}([a, b])$. Thus we can choose an open set $U$ with $| \nabla f | > 0$ everywhere on $U$, such that $\ol{U}$ is compact. Now choose a bump function $\beta$ with $\beta \equiv 1$ on $\ol{V}$ and $\operatorname{supp}(\beta) \subseteq U$. Define $X = -\beta \cdot {1}{|\nabla f|^2} \nabla f$; this is the downward gradient vector field, normalized and restricted to $U$. Then $X$ has compact support, so its flow exists for all time. Letting $\phi_t$ be the flow of $X$, we have $\frac{d}{dt}f(\phi_t) = (Xf)_{\phi_t(x)} = \langle \nabla f, X \rangle_{\phi_t(x)}$. But by the definition of $X$, this equals $-\beta(\phi_t(x)) \frac{\langle \nabla f, \nabla f \rangle}{|\nabla f|^2} = -1$, whenever $\phi_t(x) \in f^{-1}([a, b])$. Thus, letting $x \in f^{-1}(b)$, we have $f(\phi_t(x)) = b - t$ for all $t$. At time $b - a$ it will reach $a$. Thus $\phi_{b-a}$ is a diffeomorphism $M^b \to M^a$. 

To turn this into a homotopy equivalence, define $r_t(x) = x$ if $x \in M^a$, and $\phi_{t(a - f(x))}(x)$ if $x \in M^b \backslash M^a$. This is a one-parameter family of diffeomorphisms $M^b \to M^a$. We have $r_0 = \operatorname{id}, r_t|_{M^a} = \operatorname{id}|_{M^a}$ for all $t$, and $r_1$ is a diffeomorphism $M^b \to M^a$. Letting $i$ be the inclusion $M^a \to M^b$ we have $r_1 \circ i = \operatorname{id}|_{M^a}$ and that $i \circ r_1|_{M^b}$ is homotopic to $i \circ r_0|_{M^a}$; but the latter is $\operatorname{id}$. Thus $i$ is a homotopy equivalence with homotopy inverse $r_1$. This implies, for instance, that $M^a$ and $M^b$ have the same [[de Rham cohomology]]. 

When you follow the gradient flow downward, the topology doesn't change as long as you don't hit a critical point; now we consider what happens when you do hit a critical point.


## Morse Functions
A "Morse function" is a smooth function $M \to \R$ such that all critical points are nondegenerate, and each level set $f^{-1}(a)$ has at most one critical point. Assuming $M$ is compact, this implies that the set of critical points and the set of critical values are both finite. This is because each critical point $p_\alpha$ has a Morse neighborhood (i.e. neighborhood in which Morse coordinates exist) in which it is the only critical point. Then the sets $U_\alpha, M \backslash \{p_\alpha\}$ form an open cover; it has a finite subcover which includes all the critical points. Since there is one open set in the subcover per critical point, there are finitely many critical points. 

On any manifold $M$, there exists a Morse function; indeed, any function can be "perturbed" into a Morse function, i.e. for any function $g$ and $\epsilon > 0$ there exists a Morse function $f_\epsilon$ with $\sup |g - f_\epsilon| < \epsilon$. 
## Second Deformation Lemma
Now we revisit gradient flows and look at what happens when we pass by a critical point . Let $p$ be a critical point with $c = f(p)$; choose a Morse coordinate neighborhood $U$ centered at $p$ so that $f(x, y) = c + |x|^2 - |y|^2$ (using $x, y$ as shorthands for the $x^i, y^j$ used in the definition of Morse coordinates). Choose an $\epsilon$ such that $f^{-1}([c - \epsilon, c + \epsilon])$ contains no critical points besides $p$, then choose a ball $B(p, 2r) \subseteq U$ so that $B$ includes some points with $f(q) < c - \epsilon$ and some with $f(q) > c + \epsilon$. 

... include diagrams? ... see also Milnor's book, pg 16-17

As before, we want to "push $M^{c + \epsilon}$ down", but now we want to keep it fixed in a neighborhood of $p$. First we prove the following lemma: $M^{c + \epsilon}$ is diffeomorphic (and homotopy-equivalent) to $M^{c - \epsilon} U H$, where $H$ is a neighborhood of $B^-$, which we define to be the set of all points $(0, y) \in B$ (i.e. where only the "negative" coordinates are nonzero).

Choose a bump function $\beta: \R \to \R$ such that $\beta(0) > \epsilon, \beta(t) >0$ for all $t > 2\epsilon$, and $-1 < \beta' \leq 0$; modify $f$ to $F(x, y) = f(x, y) - \beta(2|x| - |y|)$ for $x, y \in B$, and $F = f$ outside of $B$. Then $F^{-1}((-\infty, c + \epsilon]) = M^{c + \epsilon}$, and the critical points of $F$ are precisely the critical points of $f$ (proof in Milnor). Then we can apply the first deformation lemma to get that $M^{c + \epsilon}$ is diffeomorphic to $F^{-1}((-\infty, c - \epsilon])$; we claim that this is just $M^{c - \epsilon} \cup H$, $H$ defined as above. 

...again see diagrams...

Now we've deformed $M^{c+\epsilon}$ into $M^{c-\epsilon}$ plus the "handle" $H$. We can then do a deformation retraction of $B^-$ onto $H$....

This gives us the "second deformation lemma": if $f^{-1}([a, b])$ contains only one critical point with index $\lambda$, then $M^b$ is homotopy equivalent to $M^a$ with a $\lambda$-cell attached. 

...insert example with the height function on the torus...

This lets us show how to build $M$ as a CW complex (i.e. space built by gluing together k-cells). 

Thus every manifold is homotopy equivalent to a CW complex; we've proved it for compact manifolds, but in fact it holds in general. 