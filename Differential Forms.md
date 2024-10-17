$\newcommand{\pd}[2]{\frac{\partial #1}{\partial #2}}$ 
# Cotangent Vectors and the Cotangent Bundle
Let $M$ be a manifold with tangent bundle $TM$. Now, for each tangent space $T_pM$ for $p \in M$, consider its dual vector space $(T_pM)^*$. We can then construct a "cotangent bundle" $T^*M$ in exactly the same way as the tangent bundle, by taking the disjoint union of the duals of every tangent space, $\cup_p (T_pM)^*$.

The fact that this is, indeed, a vector bundle of rank $\dim(M)$ over $M$ can be proven in much the same way as the corresponding fact for $TM$. 
# 1-Forms
Sections of the tangent bundle are vector fields; sections of the cotangent bundle are called *1-forms* or *covector fields*.  

Recall that, in local coordinates $x^i$ on an open set $U$, we have sections $\frac{\partial}{\partial x^i}$ of $TM$ which form a basis of the tangent bundle everywhere that those coordinates are defined. It follows that, if we take the dual basis $(\frac{\partial}{\partial x^i})^*$, we should get sections of the cotangent bundle that form a basis of $T^*M$ locally. We denote these dual basis vectors by $dx^i$. Recall that, by the definition of the dual basis, these are given by $(dx^i)(\frac{\partial}{\partial x^j}) = \delta_{ij}$. Then any 1-form can be written as $\omega = \sum_i  w_i(x) dx^i$ for some coefficient functions $w_i(x)$. 

Now we can define a local trivialization of $T^*M$ by, for all $p \in U$ $(p, \omega(p)) \to (p, \omega_1(p), \dots, \omega_n(p)) \in U \times \R^n$, which works much like the local trivialization for vector fields. We then also have that a 1-form $\omega$ is smooth if and only if its coefficients $\omega_i(x)$ are smooth. 

These coordinate expressions make it easy to construct 1-forms on $\R^n$. For example, $e^t dt$ is a 1-form on $\R$, $xydx + \sin(xy)dy$ is a $1$-form on $\R^2$, and so on. 

Define $\Omega^1_M$ to be the set of all 1-forms on a manifold $M$, i.e. the set of all sections of the cotangent bundle. Like the set of all vector fields on $M$, this is an infinite-dimensional vector space over $\R$--linear combinations of 1-forms are also 1-forms--and a module over $C^\infty(M)$, with $f\omega$ defined by $(f\omega)(p) = f(p)\omega(p)$. 

Cotangent vectors define linear maps from $T_pM$ to $\R$; 1-forms define linear maps (linear over $C^\infty(M)$) from the set $X(M)$ of all vector fields on $M$ to $C^\infty(M)$. Given a 1-form $\omega$, define $\phi_\omega: X(M) \to C^\infty(M)$ by $(\phi_\omega(X))(p) = \omega_p(X_p)$.  (That is, $\phi_\omega(X)$ is a smooth function on $M$, which takes in a point $p$ and returns $\omega_p(X_p)$.) To show linearity, we have $\phi_\omega(aX + bY) = \omega(aX + bY) = a\omega(X) + b\omega(Y) = a\phi_\omega(X) + b\phi_\omega(Y)$. Also, $\phi_\omega(fX) = \omega_p(f(p)X_p) = f\omega(X) = f\phi_\omega(X)$. 

Similarly, linear maps in the sense above define 1-forms on $M$. Given $\phi$ with the properties above and local coordinates $x^i$, define functions $\omega_i$ by $\omega_i = \phi(\frac{\partial}{\partial x^i})$, and a 1-form (on $U$) $\omega$ as $\sum_i \omega_i dx^i$. Then for each $X = \sum_k X^k \frac{\partial}{\partial x^k}$, we have $\omega(X) = \sum_i \sum_k \omega_i X^k dx^i (\frac{\partial}{\partial x^k})= \sum_i \sum_j \omega_i X^k \delta_{ik}=\sum_i X^i \omega_i$. This in turn is equal to $\sum_i X^i \phi(\frac{\partial}{\partial x^i})$. The $X^i$ are smooth functions, and we assumed that $\phi$ is $C^\infty(M)$-linear, so we get $\phi(\sum_i X^i \frac{\partial}{\partial x^i}) = \phi(X)$. All this was in a single coordinate patch, but in fact it defines a unique map on that coordinate patch, and this uniqueness implies coordinate independence--doing the same procedure with a different basis would give us the same map. This then implies that everything works fine on the overlaps between charts, so we have a 1-form $\omega$ defined on all of $M$. 

## Differentials as 1-Forms
Recall that the differential of a function $M \to \R$ is defined by $df(X) = Xf$. This is $C^\infty(M)$-linear since $df(aX + bY) = (aX + bY)f = adf(X) + bdf(Y)$ and $df(gX) = (gX)f = g(Xf) = gdf(X)$ for all $a, b \in \R$ and $g \in C^\infty(M)$. The result above then implies that $df$ is a 1-form.

We can then write $df$ in the basis $dx^i$ given by local coordinates. If $f: \R^n \to \R$ is a smooth function then $df(\frac{\partial}{\partial x^i}) = \frac{\partial}{\partial x^i}f = \frac{\partial f}{\partial x^i}$. Thus $df = \sum_i \frac{\partial f}{\partial x^i}dx^i$. 

For example, $d(x^3) = 3x^2 dx$; $d(e^{xy}) = ye^{xy}dx + xe^{xy}dy = (e^{xy})(ydx + xdy)$; and so on for any function $\R^n \to \R$. Differentiating a coordinate function $x^i$ gets us a basic 1-form $dx^i$, defined by $dx^i (X)= X(x^i)$; so, for example, $dx^i (\frac{\partial }{\partial x^k}) = \delta_{ik}$. Thus the differentials of the $x^i$ are the dual basis to the basis $\frac{\partial}{\partial x^i}$ of the tangent space, justifying our use of $dx^i$ for the dual basis vectors earlier. 

## Pullbacks of 1-Forms
Recall that, given a map $F: M \to N$, functions $N \to \R$ get "pulled back" to functions $M \to \R$ by the rule $F^*f = f \circ F$. $F$ also pulls back 1-forms, inducing a map: $F^*: T^*N \to T^*M$ by the rule $(F^*\omega)(X) = \omega(F_*X)$, i.e. we apply the pushforward of $F$ to $X$ and then apply $\omega$ to that. 

Now we try to write this in coordinates, say $x^i$ on $M$ and $y^i$ on $N$. Let $F(x^1, \dots, x^n)$ have components $(F^1(x^1, \dots, x^n), \dots, F^m (x^1, \dots, x^n))$. Then $F^*\omega$, as a 1-form on $M$, will have an expression in terms of $dx^i$. First consider $F^*(dy^j)$. This is equal to $\sum_{i=1}^n \pd{y^j}{x^i}dx^i$. To see this, note that $F^*(dy^j)(\pd{}{x^k}) = dy^j(F_*\pd{}{x^k}) = dy^j(\sum_{i=1}^n \pd{y^i}{x^k}dx^i)=$.......

## Computations with 1-Forms
Some of the most commonly useful properties of 1-forms, the $d$ operator, and the pullback are as follows:
(a) $d(af + bg) = adf + bdg$ 
(b) $d(fg) = g \cdot df + f \cdot dg$ 
(c) $F^*(a\omega + b\gamma) = aF^*\omega + bF^* \gamma$
(d) $F^*(f\omega) = (F^*f) \cdot (F^*\omega)$
(e) $(G \circ F)^*(\omega) = F^*G^*\omega$

(a) and (c) follow from our earlier results....

## Integrating 1-Forms
....
....
....
Formally, we define integration of a 1-form as follows. Given a curve $C$, choose a parameterization $\gamma: [a, b]$. Pull back the 1-form by $\gamma$ to get a 1-form on $\R$, $\gamma^*\omega = f(t)dt$ for some function $f(t)$. The integral of $\omega$ over $c$ is then defined as $\int_a^b f(t)dt$. 

For example, let $\omega = xydx + \frac{x^2}{2}dy$ and consider integrating it on the section of the parabola $y=x^2$ from $(0, 0)$ to $(2, 4)$. We first parameterize the curve by $\gamma(t) = (t, t^2)$ with $t \in [0, 2]$. Then $\gamma^*\omega = t \cdot t^2 dt + \frac{t^2}{2}d(t^2) = t^3 dt + \frac{t^2}{2} \cdot 2t \cdot dt = 2t^3 dt$. We then have $\int_C \omega = \int_0^2 2t^3 = \frac{t^4}{2}|^2_0 = 8$. 

### Invariance Under Reparameterizations
In order for this definition in terms of parameterizations to make sense, we need the integral to not depend too much on parameterizations. We can reasonably expect that the direction or orientation of the parameterization matters: this is the case even when integrating functions, where $\int_a^b f(x)dx = -\int_b^a f(x)dx$. To formalize this, let $\gamma: [a, b] \to M$ be a parameterization of a curve $C$, and suppose further that $\gamma'(t)$ is nonzero for all $t \in [a, b]$. We can specify the orientation of a curve by declaring one of its endpoints $p_0$ to be the "starting point"; we can then say that $\gamma$ is a "positive parameterization" of $C$ if $\gamma(a) = p_0$, and a "negative parameterization" of $C$ if $\gamma(b) = p_0$. This can be generalized to closed curves, but we will ignore those for now.

An "oriented reparameterization" of a curve with parameterization $\gamma: [a, b] \to M$ is a smooth map $\phi: [c, d] \to [a, b]$ with $\phi(c) = a, \phi(d) = b$, and $\phi'(t) > 0$ for all $t$. Since its derivative is everywhere positive, it is monotonically increasing, and that plus smoothness implies it is a diffeomorphism. 

Now we can prove the following: integrals are preserved under oriented reparameterizations. Proof: let $C$ be parameterized by $\gamma(t)$, and let $t = \phi(s)$ where $\phi$ is an oriented reparameterization. We can use the change-of-variables formula $\int_a^b f(t)dt = \int_c^d f(\phi(s))\frac{d\phi}{ds}ds$. Writing $\omega = f(t)dt$, we have $\phi^*\omega = f(\phi(s)) dt = f(\phi(s))d(\phi(s)) = f(\phi(s)) \frac{d\phi}{ds}ds$. We can then rewrite the change of variables formula as $\int_a^b \omega = \int_c^d \phi^*\omega$. 

Now consider $\int_C \omega$. If we evaluate this using the parameterization $\gamma \circ \phi$ we get $\int_c^d (\gamma \circ \phi)^* \omega = \int_c^d \phi^*(\gamma^*\omega)$, using the chain rule for pullbacks from above. The change-of-variables formula says this is equal to $\int_a^b \gamma^*\omega$, which is $\int_C \omega$ evaluated using the parameterization $\gamma$. Thus changing the parameterization does not affect the value of the integral. 

### Closed and Exact 1-Forms
An 1-form $\omega$ is called *exact* if there exists a function $f$ with $\omega = df$. Integrals of exact 1-forms are special. We have $\int_C df = \int_a^b \gamma^*(df) = \int_a^b d(\gamma^*f) = \int_a^b d(f \circ \gamma) = \int_a^b \frac{d(f \circ \gamma)}{dt} dt = (f \circ \gamma)|_a^b = f(\gamma(b)) - f(\gamma(b))$. Thus, for exact 1-forms, we can simply apply the fundamental theorem of calculus. 

If $\omega$ is exact on some open set $U$, $\omega = df$, then $f$ is unique up to a constant. Suppose that $\omega = df$ and $\omega = dg$; then let $c = g(x_0) - f(x_0)$, for some $x_0 \in U$. Now take another $x \in U$ and choose a path $C$ with $\gamma(a) = x_0, \gamma(b) = x$, and $\gamma'(t) \neq 0$ for all $t$. Then $\int_C df = f(x) - f(x_0)$, while $\int_C dg = g(x) - g(x_0)$; but $\int_C df = \int_C dg$< so $f(x) - f(x_0) = g(x) - g(x_0)$ for any $x$, or $f(x) - g(x) = f(x_0) - g(x_0) = c$. 

$f$ is sometimes called a *potential* for $\omega$, as in physics. 

Now we look for criteria implying that a given 1-form is exact. One way to do this is in coordinates. Let $\omega = \sum_i \omega_i(x) dx^i$ in some local coordinates $x^i$; then, if $\omega = df$, we have $\omega_i(x) = \pd{f}{x^i}$ Thus $\pd{\omega_i}{x^j} = \pd{^2 f}{x^i\partial x^j} = \pd{\omega_j}{x^i}$. This gives us one necessary condition for $\omega$ to be exact: we need $\pd{\omega_i}{x^j} = \pd{\omega_j}{x^i}$ for all $i, j$ in any coordinates. We call 1-forms satisfying this condition *closed*; thus any exact 1-form is closed. 
#### Poincare Lemma
There is a partial converse to this, given by the following theorem, a special case of the "Poincare lemma". Let $B(p, r)$ be a ball, either in $\R^n$ or in coordinates on some manifold. Then, on $U$, every closed 1-form is exact. Proof: without loss of generality we can, for convenience, let $p$ be the origin. For any point $x$ in the ball, consider the line $L$ from $0$ to $x$, parameterized by $\gamma(t) = tx$, and let $f(x) = \int_L  \omega$. Then $f(x) = \int_0^1 \sum_j \omega_j(tx)d(tx^j)$. Since $x^j$ is fixed we have $d(tx^j) = x^jdt$; thus $f(x) = \int_0^1 \sum_j \omega_j(tx) x^j dt$. Now we have $\pd{f}{x^i} = \int_0^1 \sum_j (\pd{\omega_j}{x^i}t x^j + \omega_j(tx)\pd{x^j}{x^i})dt = \int_0^1 \sum_j (\pd{\omega_j}{x^i}t x^j + \omega_j(tx)\delta_{ij})dt$, by differentiating under the integral sign and using the product rule. If we use the fact that $\omega$ is closed to turn $\pd{\omega_j}{x^i}$ into $\pd{\omega_i}{x^j}$, this works out to $\int_0^1 [(\sum_j t \pd{\omega_i}{x^j}x^j) + \omega_i(tx)]dt$. But this is equal to $\int_0^1 \frac{d}{dt}[t\omega_i(tx)]dt=t \omega_i(tx) |_0^1 = \omega_i(x)$. Thus $\omega = \sum \omega_i(x)dx = \sum \pd{f}{x^i}dx^i = df$, so $\omega$ is exact.

The proof generalizes to any "star-shaped" set, i.e. any set such there exists a "central" point $p$ such that, for any other point $q$, the line segment from $p$ to $q$ is contained in the set. 

In fact, we can generalize further. We can first prove that closedness and exactness are preserved when pulling back by diffeomorphisms, i.e. if $F$ is a diffeomorphism then $\omega$ is closed/exact if and only if $F^*\omega$ is closed/exact. ......

It then follows that the Poincare lemma holds on any set which is diffeomorphic to a ball. 

### Integrating Exact Forms
Another important characterization of exact forms is that they are the forms whose integrals depend only on the position of the endpoints, or whose integrals around closed curves are $0$. More precisely, a form $\omega$ is exact if and only if $\int_{C_1}\omega = \int_{C_2}\omega$ where $C_1, C_2$ are any curves with the same endpoints (i.e. same start and same end, hence same orientation), or $\int_L \omega = 0$ for any closed curve or loop $L$. 

Proof: the first implication follows from $\int_C \omega = \int_C df = f(b) - f(a)$ where $a, b$ are the endpoints of the curve; clearly this depends only on the endpoints, and will thus be the same for any curve with endpoints $a, b$. This implies that the integral about any loop is $0$: let $a$ be the start (and end) point of the loop, and let $b$ be any other point; then let $C_1$ be the section of the loop going from $a$ to $b$ (in the direction in which the loop is oriented), and let $C_2$ be the rest (going from $b$ to $a$). Then $\int_L \omega = \int_{C_1}\omega + \int_{C_2}\omega = (f(b) - f(a)) + (f(a) - f(b)) = (f(b) - f(b)) + (f(a) - f(a)) = 0$. Conversely, if the integral on a curve about any loop is $0$, then for any two curves $C_1, C_2$ between endpoints $a$ and $b$, consider $\int_{C_1}\omega + \int_{-C_2} \omega$, where we use $-C_2$ to represent $C_2$ with the opposite orientation (from $b$ to $a$). On one hand, this equals $\int_L\omega$, where $L$ is the closed curve obtained by concatenating $C_1$ and $C_2$, and by assumption this equals $0$. On the other hand, it equals $\int_{C_1}\omega - \int_{C_2}\omega$. Thus $\int_{C_1}\omega - \int_{C_2}\omega = 0$ or $\int_{C_1} \omega = \int_{C_2}\omega$. 

The tricky part is showing that the second condition (integral depends only on endpoints) implies that $\omega$ is exact. First we will need the fact that any closed form is "locally exact"....

....

