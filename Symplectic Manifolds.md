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

We can then extend the above ideas to manifolds. If we have a 2-[[Differential Forms|form]] on a [[Manifolds|manifold]] $M$, i.e. a section $\omega$ of $\wedge^2 (T^*M)$ which is nondegenerate at each point, then we call $\omega$ a symplectic form, and say that $M$ is a symplectic manifold. Similarly we can take a section $g$ of the space of all symmetric 2-forms on $T^*M$; we then  call $g$ a "Riemannian metric" and $M$ a Riemannian manifold. Each of these gives us an isomorphism $g^\#, \omega^\#$ between $T_pM$ and $T^*_pM$ at each point. 

More precisely, we define a symplectic form to be a 2-form $\omega$ which is closed (i.e. $d\omega = 0$) and nondegenerate (which turns out to be equivalent to $\omega^n$, the [[Differential Forms#Wedge Product|wedge product]] of $\omega$ with itself $n$ times, being nonzero). If $\omega$ is also exact, i.e. the exterior derivative of a 1-form, we call it an exact symplectic form. 

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

# Hamiltonian Mechanics
## Hamilton's Equations
Suppose that we have a system with energy described by a potential $U$. Then Hamilton's equations say that, for a particle with position $x$ and momentum $p$ (both vectors), we have $\dot{x}  = p/m, \dot{p} = -\nabla U$. We define the Hamiltonian, which is the total energy, by $H(x, p) = \frac{1}{2}mv^2 + U(x) = \frac{1}{2m}p^2 + U(x)$. Then Hamilton's equations can be rewritten $\pd{H}{x} = \nabla U, \pd{H}{p} = p/m$. In other words $\dot{x} = \pd{H}{p}, \dot{p} = -\pd{H}{x}$. 

For a system with many degrees of freedom we get a system of equations for each coordinate, $\dot{x}^i = \pd{H}{p^i}, \dot{p}^i = -\pd{H}{x^i}$. 

Thus we have $\MatrixTwoTwo{0}{-1}{1}{0} (\dot{x}, \dot{p})^t = (\pd{H}{x}, \pd{H}{p})^t$ (and the suitable generalization to many degrees of freedom). The left-hand side is $i_X\omega$ where $\omega$ is the standard symplectic form and $X = (\dot{x}, \dot{p})^t$ is the tangent to the system's trajectory through phase space (space with coordinates for each position and momentum degree of freedom), while the right-hand side (thought of as a 1-form) is $dH$. 

We can then rewrite Hamilton's equations as $i_X\omega = dH$, where $X$ is the vector of positions and momenta. Again, we are working in phase space, which can be thought of as the cotangent bundle on configuration space (set of all possible positions of the system), with the standard symplectic form. (Also, recall that the interior multiplication $i_X\omega$ is, in this context, analogous to matrix-vector multiplication. We get back a 1-form, which in the example of Hamilton's equations above we treated as just a vector field $(\pd{H}{x}, \pd{H}{p})^t$. Cf. how a matrix can induce a bilinear form, by $A(v, w) = v^tAw$, and a linear map, by $A(v) = Av$. What it's generalizing here is applying the matrix which is, in block form, $\MatrixTwoTwo{0}{-1}{1}{0}$ to the vector of position and momentum coordinates.)

Given only the Hamiltonian, we can say that the evolution of the system is given by the flow along the vector field $X_H$, defined by $i_{X_H}\omega = dH$. This then gives us freedom to rewrite Hamilton's equations in many ways; for any coordinates $x^i$ on the configuration space, we can take the "conjugate momentum" $p_i = \pd{H}{\dot{x}^i}$ and recover Hamilton's equations from there. 
## Example: The Pendulum
For example, take a pendulum, with a mass $m$ attached to a rigid rod of length $l$. The configuration space is the circle, so the corresponding phase space is $T^*(S^1)$. We use an angle $\theta$ measured from the vertical, as usual. The Hamiltonian is $H = \frac{1}{2}mv^2 + U$ where $U = -gml\cos(\theta)$ (here we use coordinates with $U = 0$ at the horizontal line passing through the point from which the pendulum hangs). Substituting $v^2 = (l\dot{\theta})^2$ we get $H = \frac{m}{2}l^2 \dot{\theta}^2 - mgl\cos(\theta)$, so the conjugate momentum is $p_\theta = \pd{H}{\dot{\theta}} = ml^2 \dot{\theta}$. Thus another form for $H$ is $H = \frac{1}{2ml^2}p^2 - mgl\cos(\theta)$. 

With all this set up, Hamilton's equations become $\dot{\theta} = \pd{H}{p} = \frac{p}{ml^2}, \dot{p} = -\pd{H}{\theta} = -mgl\sin\theta$. 

We can then look at $\ddot{\theta}$, is $\frac{1}{ml^2}\dot{p}$; substituting our expression for $\dot{p}$ we get $\ddot{p} = -\frac{g}{l}\sin\theta$. 
## Abstract Hamiltonian Systems
We can abstract all of the above to get the notion of a "Hamiltonian system". This is a symplectic manifold $(M, \omega)$ ($M$ will stand in for the phase space) along with a smooth function $H: M \to \R$. For our purposes we will let $H$ be anything, and do not put any physically-inspired conditions on it. 

This gives us a "Hamiltonian vector field" $X_H$, defined as above by $i_{X_H}\omega = dH$, and a flow $F_t$ generated by $X_H$. (The reason such a vector field should exist is that $\omega$, as a nondegenerate bilinear form, defines an isomorphism between the tangent bundle and cotangent bundle; thus there exists a unique vector field which $\omega$ maps to $dH$.)
### Conservation of Energy and Gibbs-Liouville
We then have that the Hamiltonian flow is along curves of constant $H$; thinking of the Hamiltonian as the total energy, this tells us that energy is conserved. It is also a symplectic flow, i.e. preserves $\omega$, i.e. $F_t: M \to M$ is a symplectomorphism. Finally, we have the Gibbs-Liouville theorem: the Hamiltonian flow preserves the volume form $\omega^n$. 

Proof: 

For the first fact, we look at $\frac{d}{dt}H(F_t(p)) = X_H(H) = dH(X_H)$ (using the pairing between 1-forms and vector fields). But $dH(X_H) = i_{X_H}dH = i_{X_H}(i_{X_H}\omega) = \omega(X_H, X_H) = 0$. 

For the second fact, we need to know how $\omega$ changes along $X_H$; this suggests looking at the Lie derivative $L_{X_H}\omega$, which by Cartan's formula is $(i_{X_H}d + di_{X_H})\omega$. Since $\omega$ is closed, $d\omega = 0$, and the first term drops out; we are left with $di_{X_H}\omega = d(dH) = 0$. 

For the last fact, we look at $L_{X_H}(\omega^n) = L_X\omega \wedge (\omega^{n-1}) + \omega \wedge L_X(\omega) \wedge (\omega^{n-2}) + \dots$ by the product rule, but each of those terms goes to $0$ because $L_X\omega = 0$, by the above. 
## Poisson Brackets
We call any function of position and momentum, i.e. any function on phase space, an observable. Each observable $f$ gives us a vector field $X_f$ using Hamilton's equations, $i_{X_f}\omega = df$. Since our work above allowed $H$ to be any function, our results hold for any observable, using its corresponding vector field $X_f$; the flow along $X_f$ conserves $f$, $\omega$, and $\omega^n$. 

The Poisson bracket of two functions $f, g$ is defined by $\{f, g\} = X_f(g)$. That is, we differentiate $g$ along the curves of constant $f$. In the "nice" local coordinates $x^i, y^i$ given by Darboux's theorem, we have $\{f, g\} = \sum \pd{f}{x^i}\pd{g}{y^i} - \pd{g}{x^i}\pd{f}{y^i}$.

The Poisson bracket can act as a Lie bracket operation, turning the space of functions on a symplectic manifold into a Lie algebra. Proof: we have $\{f, g\} = X_f(g) = dg(X_f) = i_{X_f}dg = i_{X_f}(i_{X_g}\omega) = \omega(X_f, X_g) = -\omega(X_g, X_f)$; we can then run the argument in reverse to get $\{f, g\} = -\{g, f\}$. Thus the Poisson bracket is antisymmetric. Linearity is also easy. 

Furthermore, the map sending $f$ to $X_f$ is a Lie algebra homomorphism (using the Poisson bracket for the Lie algebra structure on functions, and the standard Lie bracket on vector fields). In other words $X_{\{f, g\}} = [X_f, X_g]$.  ...... fill in proof later .... this 

Finally, for the Jacobi identity, we have $d\omega(X, Y, Z) = X(\omega(Y, Z)) + Y(\omega(Z, X)) + Z(\omega(X, Z)) - \omega([X, Y], Z) - \omega([Y, Z], X) - \omega([Z, X], Y)$. Substituting $X, Y, Z = X_f, X_h, X_g$ we get the Jacobi identity...

## Poincare Recurrence Theorem
....

Consider a Hamiltonian system with a compact phase space: formally, we take a compact symplectic manifold $M$ with symplectic form $\omega$ and Hamiltonian $H$. Take any point $p \in M$. Then for any neighborhood $U$ of $p$, and any time $T > 0$, there exists a time $t > T$ and point $y \in U$ such that $\phi_t(y) \in U$. (Intuitively speaking, there is some trajectory near $p$ which will come close to $U$ infinitely many times.)

Proof: recall that the volume of $U$ is given by $\int_U \omega^n$, which is positive ($\omega^n$ is an orientation form). We also have that the volume of $F_t(U)$ is equal to the volume of $U$, by the Gibbs-Liouville theorem above. Since our manifold is compact, it has finite volume, i.e. $\int_M \omega^n$ is finite. 

Thus, for any time $T$, the sets $F_T(U), F_{2T}(U), F_{3T}(U), \dots,$ cannot be disjoint, else our manifold would have infinite volume. Say that $F_{kT}(U), F_{(k+m)T}(U)$ intersect; let $x$ be a point in their intersection. Then, letting $y = (F_{kT})^{-1}(x)$ and $z = F_{(k+m)T}^{-1}(x)$, we have $y \in U$, $z \in U$, and $z = F_{mT}(y)$. Thus $y$ is a point in $U$ which, after time $mT$, returns to $U$.


## Symplectic and Hamiltonian Vector Fields
A vector field $X$ on a symplectic manifold is called symplectic of $L_X\omega = 0$, and Hamiltonian if $i_X\omega = df$ for some $f$. ....

Result... letting $\operatorname{SVect}(M)$ be the set of all symplectic vector fields, the sequence $0 \to H^0(M) \to C^{\infty}(M) \to^\alpha \operatorname{SVect}(M) \to^\beta H^1(M) \to 0$ is exact. Here $\alpha(f) = X_f$, $\beta(X) = [i_X\omega]$. 

Proof... this shows that every symplectic vector field is Hamiltonian when $H^1(M) = 0$. 

## Constants of Motion
Under a Hamiltonian flow, a function $f$ evolves to $f_t(x) = f(F_t(x))$, so $\dot{f}_t = X_{\dot{H}}f = \{f, H\}$. Thus taking the Poisson bracket of a quantity with the Hamiltonian gives the infinitesimal time-evolution of that quantity. We say that $f$ is a "constant of motion" of a system if $f_t$ (as a function of $t$) is constant, in other words if $X_{\dot{H}}f = 0$ or $\{f, H\} = 0$. 

For example, $\dot{H} = \{H, H\} = 0$, which is another way of stating the conservation of energy. 

Let $V$ be the set of all constants of motion; then $V$ is a Lie subalgebra of $C^\infty(M)$, meaning in particular that the Poisson bracket of two constants of motion is another constant of motion. The fact that it is a subspace is easy: if $f, g \in V$ then $X_H(af + bg) = aX_Hf + bX_hg = 0$. For brackets, we have $\frac{d}{dt}\{f, g\} = \{\{f, g\}, H\}$ by the result above; by the Jacobi identity this is equal to $-\{\{g, H\}, f\} - \{\{H, f\}, g\} = -\{0, f\} - \{0, g\} = 0 - 0 = 0$. Thus $\{f, g\} \in V$. 

### Noether's Theorem
Let $G$ be a Lie group with Lie algebra $\mathfrak{g}$. A "left action of $G$ on $M$" is a smooth map $G \times M \to M$ which is also a group action, i.e. $g(h(p)) = (gh)p$ (using the notation for group actions where we just multiply elements of $M$ by elements of $g$). Any such action gives us a map from the Lie algebra to vector fields on $M$, by sending $B \in \mathfrak{g}$ to $B_* = \frac{d}{dt}\exp(tB)|_{t=0}$. 

For example, the orthogonal group acts on $\R^n$ by left multiplication. The Lie algebra if the set of skew-symmetric matrices, $B^t = -B$. The Lie algebra action induced by the group action is $B_*X = \frac{d}{dt}(e^{tB}X)|_{t=0} = BX$. 

A symmetry of a Hamiltonian system is a Lie group action which preserves $H$ and $\omega$, i.e. $B_*H = 0$ and $L_{B_*}\omega = 0$. Let $\mathfrak{g}(M)$ be the set of all vector fields such that those two equations hold. 

We can now state Noether's theorem: let $G$ be a symmetry of a Hamiltonian system; if $H^1(M) = 0$ then there is a surjective Lie algebra map $V \to \mathfrak{g}(M)$, i.e. from the set of all constants of motion to the set of all vector fields satisfying the above conditions. This is just the map $\alpha$ sending $f \to X_f$ described above. 

Proof ... uses the exact sequence from above, along with the fact that $B_*$ is a symplectic vector field