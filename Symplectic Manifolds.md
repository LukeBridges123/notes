# Preliminary Results on Bilinear Forms
Recall that a bilinear form on a vector space $V$ can be thought of in several ways: as a map $V \times V \to \R$ which is linear in each argument, as a linear map $V \to V^*$, as the direct sum of a symmetric form and an alternating form, etc. A nondegenerate bilinear form is one which (as a map $V \to V^*$) is an isomorphism; equivalently, if $A(v, w) = 0$ for all $w$ then $v = 0$.

For a bilinear form $A$, denote by $A^\#$ the linear map $V \to V^*$ induced by it. By choosing bases of $V, V^*$, we can represent it as a matrix, which will be nonsingular if and only if $A$ is nondegenerate. 

In this matrix representation, every (real) symmetric bilinear form is diagonalizable, in the sense that we can choose a basis for $V$ such that, using that basis (and using its dual basis for $V^*$), the matrix is diagonal. Indeed, we can put it in a diagonal form where each entry is $\pm 1$ or $0$. If $A$ is the zero map, then clearly it is diagonalizable; otherwise, choose vectors $v, w$ with $A(v, w) \neq 0$. If $A(v, v) \neq 0$ then, by properly scaling $v$ (say $v' = \lambda v$) we can get $A(v', v') = \pm 1$. (This is because $A(\lambda v, \lambda v) = \lambda^2 A(v, v)$, so with the right choice of $\lambda$ we can scale $A(v, v)$ by any nonnegative factor.) If $A(v, v) = 0$ but $A(w, w) \neq 0$ then we can do the same thing with $w$. Otherwise we consider $A(v + w, v + w)$; this expands out to $A(v, v) + A(v, w) + A(w, v) + A(w, w) = A(v, w) + A(w, v) = 2A(v, w) \neq 0$. Thus we once again have a vector $x$ which we can scale to get $A(x', x') = \pm 1$. 

In any case, we get a vector, say $v_1$, with $A(v_1, v_1) = \pm 1$. We then proceed by induction. Define a map $\phi$ by $\phi(w) = A(v_1, w)$. This is linear and surjective (because nonzero, $\phi(v_1) = A(v_1, v_1) \neq 0$), so its kernel is an $n-1$-dimensional subspace of $V$. (We can think of it as the "orthogonal complement" of $v_1$.) Restricting $A$ to $\ker(\phi)$ gives us a symmetric, bilinear form on this $n-1$ dimensional subspace, which by induction we can diagonalize. 

In the case of skew-symmetric forms, a similar argument implies that the matrix can be put in a block form, where the diagonal consists of zeros or the matrix $\MatrixTwoTwo{0}{-1}{1}{0}$; in other words, a matrix with zeros on the diagonal, a certain number of $-1$s above the diagonal, and the same number of $1$s below it. 

A symmetric form is nondegenerate if and only if there are no zeroes on the diagonal in its diagonalized form; a skew-symmetric form is nondegenerate if the diagonal consists entirely of blocks $\MatrixTwoTwo{0}{-1}{1}{0}$ and not of any "lone zeroes". 

This implies that there nondegenerate skew-symmetric forms exist if and only if $V$ has even dimension, since that's the only way for it to be made of $2 \times 2$ blocks like the above. 

An inner product is a positive-definite symmetric bilinear form; this is equivalent to its diagonal form being the identity. Diagonalizing the matrix of an inner product is equivalent to choosing an orthonormal basis. 
# Symplectic Forms and Symplectic Manifolds
A symplectic vector space is a vector space $V$ with a nondegenerate skew-symmetric bilinear form; that is, a nondegenerate element of $\wedge^2 V^*$.

We can then extend the above ideas to manifolds. If we have a 2-form on a manifold $M$, i.e. a section $\omega$ of $\wedge^2 (T^*M)$ which is nondegenerate at each point, then we call $\omega$ a symplectic form, and say that $M$ is a symplectic manifold. Similarly we can take a section $g$ of the space of all symmetric 2-forms on $T^*M$; we then  call $g$ a "Riemannian metric" and $M$ a Riemannian manifold. Each of these gives us an isomorphism $g^\#, \omega^\#$ between $T_pM$ and $T^*_pM$ at each point. 

More precisely, we define a symplectic form to be a 2-form $\omega$ which is closed (i.e. $d\omega = 0$) and nondegenerate (which turns out to be equivalent to $\omega^n$, the wedge product of $\omega$ with itself $n$ times, being $0$). If $\omega$ is also exact, i.e. the exterior derivative of a 1-form, we call it an exact symplectic form. 

For example, on $\R^{2n}$, say with coordinates $x^1, \dots, x^n, y^1, \dots, y^n$, we have a "standard symplectic form" given by $dx^1 \wedge dy^1 + \dots + dx^n \wedge dy^n$. This is an exact form, since it is the derivative of $\sum_i x^i dy^i$. 

For an n-dimensional manifold $M$, its tangent bundle $T^*M$ has dimension $2n$, and has a standard exact symplectic form, which we can construct as follows.

Recall that each point in $T^*M$ is of the form $(p, \phi)$ where $p \in M, \phi \in (T_pM)^*$. Define a 1-form $\alpha$ on $T^*M$ by $\alpha_{(p, \phi)}(X) = \phi_p(\pi X)$ where $\pi$ is the projection map. Then set $\omega = -d\alpha$. This is automatically an exact 2-form. 

To see more explicitly how this works, pick local coordinates $x^1, \dots, x^n$; these give us local coordinates on $T^*M$ $x^1, \dots, x^n, \xi_1, \dots, \xi_n$, where $\phi = \sum \xi_i dx^i$. In these coefficients we have $\alpha = \sum_i a_i dx^i + b_i d\xi^i$ and $X = \sum_k A^k \pd{}{x^k} + B^k \pd{}{\xi^k}$. Then $\alpha(X) = \sum_i a_i dx^i(X) + b_i d\xi^i (X) = \sum_i a_i(\delta_{ik}A^k) + b_i (\delta_{ik}B^k) = \sum_i a_iA^i + b_iB^i$. On the other hand, by definition (fill in calculation) $\alpha(X) = A^i \xi_I$. Thus $\alpha = \sum_i \xi_i dx^i$ (compare to $\sum_i x^i dy^i$ above). Then $\omega = -d\alpha = \sum_i dx^i \wedge d\xi^i$ (again, compare to $\omega = \sum_i dx^i \wedge dy^i$ above). 

A more complicated example is the "Fubini-Study" form, a symplectic form on $\C P^n$.... (end up with every smooth complex projective variety being a symplectic manifold)

Some further definitions: a symplectic submanifold is a submanifold where the restriction of the symplectic form $\omega$ is still a symplectic form. A symplectomorphism is a diffeomorphism $f: M \to N$ where, if $\omega, \eta$ are the symplectic forms on $M, N$, then $f^*\eta = \omega$. 

## Darboux's Theorem
Above, we found a normal form for skew-symmetric forms on a vector space. This extends to a local expression for symplectic forms: on a symplectic manifold $M$ with symplectic form $\omega$, about each point $p$, there exists local coordinates where $\omega = dx^1 \wedge dx^2 + \dots + dx^{2n-1} \wedge dx^{2n}$. 

(In other words, a symplectic manifold is locally symplectomorphic to $\R^{2n}$ with the standard symplectic structure.) 

Proof: first choose local coordinates where $p = (0, \dots, 0)$. (I.e. a chart $\phi: U \to \R^n$ where $\phi(p) = 0$.) Let $\omega_1 = (\phi^{-1})^*\omega$; this will be a symplectic form in a neighborhood of $0$. We just need to find a local diffeomorphism of $\R^n$ that transforms $\omega_1$ into the standard form $\omega_0$, i.e. $F^*\omega_1 = \omega_0$. 

First, we can apply linear changes of coordinates to ensure $\omega_1(0) = \omega_0(0)$. Then, since $\omega_1, \omega_0$ are both closed, we have $d(\omega_1 - \omega_0) = 0$, so by local exactness there exists a 1-form $\alpha$ in some neighborhood of $0$ with $\omega_1 - \omega_0 = d\alpha$. By further translations we can assume $\alpha(0) = 0$. 

Now set $\omega_t = \omega_0 + td\alpha = (1 - t)\omega_0 + t\omega_1$. This gives us a 1-parameter family of symplectic forms (by shrinking the neighborhood of $0$ under consideration, we can ensure that $\omega_t$ is nondegenerate for all $t$...compactness argument...)

Now, *if* the theorem is true, then for each $t$ there exists a local diffeomorphism $F_t$ with $F_t^*\omega_t = \omega_0$. Differentiating with respect to $t$ we get $\frac{d}{dt}(F_t^*\omega_t) = 0$. The left-hand side is the Lie derivative $F_t^*(L_{V_t}\omega + d\alpha)$ where $V_t = \frac{d}{dt}F_t$. By the Cartan formula we have $L_{V_t}\omega_t = i_{V_t}d\omega_t + d(i_{V_t}\omega_t) =  d(i_{V_t}\omega_t)$. Substituting that into $0 = F_t^*(\dots)$ and using the fact that $d$ commutes with pullbacks we get $dF_t^*(i_{V_t}\omega_t + \alpha) = 0$. 

If we can find a vector field $V_t$ satisfying that identity, then we can run that reasoning in reverse and prove the truth of the theorem. 

Define a time-dependent vector field by $i_{V_t}\omega_t = -\alpha$; let $F_t$ be the flow of $V_t$. Then $V_t(0) = 0$ for all $t$, so $F_t(0) = 0$ for all $t$. But this means $dF_t^*(i_{V_t}\omega_t + \alpha) = dF_t^*(0) = 0$ for all time...