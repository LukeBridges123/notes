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

Now consider $\int_C \omega$. If we evaluate this using the parameterization $\gamma \circ \phi$ we get $\int_c^d (\gamma \circ \phi)^* \omega = \int_c^d \phi^*(\gamma^*\omega)$. The change-of-variables formula says this is equal to $\int_a^b \gamma^*\omega$, which is $\int_C \omega$ evaluated using the parameterization $\gamma$. Thus changing the parameterization does not affect the value of the integral. 

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

# Integrals of N-Forms in Euclidean Space
As another important special case before we move onto integration of arbitrary forms, consider integrating an $n$-form $f(x^1, \dots, x^n)dx^1 \wedge \dots \wedge dx^n$ on a subset $D$ of $\R^n$. We just define this to be $\int_D f(x^1, \dots, x^n)dx^1\dots dx^n$, using an ordinary Riemann integral. 

....

## Change of Variables
Let $f, D$ be as above .... classical change-of-variables formula....

In the case of an n-form $\omega$ we have $\int_A \phi^*\omega = \int_A (\phi^* f) \cdot \phi^*(dx^1 \wedge \dots \wedge dx^n)$; that second factor is $dy^1 \wedge \dots \wedge dy^n$ multiplied by the Jacobian determinant of $\phi$ (in the relevant coordinates). 

....

## Orientations
Letting $\phi$ be a diffeomorphism between subsets of $\R^n$, we say that it is "orientation-preserving" if $\det(d\phi)$ is positive, and "orientation-reversing" if $\det(d\phi)$ is negative. For example, the reflection on one coordinate $R_1(x^1, x^2 \dots, x^n) = (-x^1, x^2, \dots, \ x_n)$ is orientation-reversing: since it is a linear map, we have $d R_1 = R_1$, and so $\det(dR_1) = \det(R_1) = -1 \cdot 1 \cdots 1 = -1$. 

Combined with our reasoning above, this implies that the integral of an n-form over a domain does not depend on how you parameterize that domain, except that the sign changes under an orientation-reversing reparameterization. 

# Integrals of N-Forms over Arbitrary Manifolds
## Orientations
We define an *oriented atlas* to be one where all transition functions are orientation-preserving in the sense above. An *orientable manifold* is a manifold with an orientable atlas. An *orientation of a manifold* is just the choice of a maximal oriented atlas (so, we add in all charts that are orientation-preserving). 

A more practical way to deal with orientations is given by the following result. A manifold is orientable if and only if there exists an $n$-form which is nowhere zero. 

For one direction, let $\phi_\alpha$ be an oriented atlas. On an open set $U_\alpha$, define an n-form $\eta_\alpha = dx^1 \wedge \dots \wedge dx^n$ (in the local coordinates). Then we use a partition of unity $\psi_\alpha$ subordinate to $\{U_\alpha\}$ to combine all of these into a single n-form $\eta = \sum \psi_\alpha \eta_\alpha$. We need to make sure that this is nowhere $0$, and in particular that, on overlapping charts $\alpha, \beta$, the $\eta_\alpha, \eta_\beta$ don't cancel each other out. Argument with transition maps .... so $\eta_\alpha$ is a positive multiple of $\eta_\beta$. 

For the other direction, .....

On orientable manifolds, it makes sense to say that two n-forms $\eta, \eta'$ are *equivalent* if $\eta = f\eta'$ where $f$ is an everywhere-positive function. .....

For example, the standard volume form $dx^1 \wedge \dots \wedge dx^n$ gives an orientation of $\R^n$, and of any open subset of $\R^n$. On the 2-sphere, we have an orientation form $\eta$ given by $dr \wedge \eta = dx \wedge dy \wedge dz$. $\eta$ is simply the contraction $i_{\pd{}{r}}(dx \wedge dy \wedge dz)$. This generalizes to other embedded submanifolds. Say we have coordinates $x^1, \dots, x^n$ on the whole space, and a submanifold defined by the vanishing of $x^1, \dots, x^k$. Then by taking contractions of $dx^1 \wedge \dots \wedge dx^n$ we can get an orientation form. 

The classic example of a non-orientable manifold is the Mobius strip ....we can parameterize the "core circle" (the curve that moves through the middle of the whole strip), and consider a vector field $X$ orthogonal to that core circle .... 

## Definition of the Integral
Let $M$ be an oriented, n-dimensional manifold, and let $\omega$ be a compactly supported n-form on $M$. (The "compactly supported" condition is so that we don't have to deal with improper integrals.) We define $\int_M \omega$ by choosing an oriented atlas $\phi_i : U_i \to \R^n$, a partition of unity $\beta_i$ suboordinate to $U_i$, and saying that $\int_M \omega = \sum_i \int_{U_i} \beta_i \omega$. Each of those integrals $\int_{U_i}\beta_i \omega$ is defined as before: we pull back by $\phi_i$, and $\int_{U_i} \beta_i \omega = \int_{\phi_i(U_i)}(\phi_i^{-1})^*\omega$. This is now an integral over a subset of $\R^n$, which we can handle as before. 

First we handle a few technical points. We want to show first that it makes no difference which oriented atlas and partition of unity we choose, as long as we don't reverse the orientation of $M$, in which case the integral changes sign. 

For the first of those facts, let $\hat{\phi_j}, \hat{\beta_j}$ be another atlas and partition of unity, satisfying the same conditions as $\phi_i, \beta_i$. Then, since the sum of the $\hat{\beta_j}$ is $1$, we have $\int_{U_i}\beta_i \omega = (\sum_j \hat{\beta_j})\int_{U_i}\beta_i \omega = \sum_j \int_{U_i} \hat{\beta_j}\beta_i \omega$. Define $\omega_{ij} = \hat{\beta_j}\beta_i \omega$. The sum we just wrote is then equal to $\sum_j \int_{U_i}\omega_{ij}$. But $\int_{U_i} \omega_{ij} = \int_{\phi_i(U_i \cap \hat{U_j})} (\phi_i^{-1})^* \omega_{ij}$, by definition (we can restrict the domain like that because $U_i \cap \hat{U_j}$ is the support of $\omega_{ij}$). This is then equal to .... (fill in from Tu 23.4)

Now we prove the second fact. If $\phi_i$ is an oriented atlas for a given orientation of $M$, we can compose it with a reflection $R_1$ of the first coordinate in $\R^n$ to get an oriented atlas for the opposite orientation. (Any oppositely-oriented atlas can be obtained in this way.) We then have $\phi_i^*\omega = f_i dx^1 \wedge \dots \wedge dx^n$ and $(R \circ \phi_i)^*\omega = -f_i dx^1 \wedge \dots \wedge dx^n$. Integrating these, we then get $\int (-f_i dx^1 \wedge \dots \wedge dx^n) = -\int f_i dx^1 \wedge \dots \wedge dx^n$, so changing the orientation flips the sign of the integral. 

## Integrals with Parameterizations
The above definition is not very useful for computation. Usually we are given manifolds in terms of parameterizations, not charts (and certainly not partitions of unity). 

We can use parameterizations to compute an integral $\int_M \omega$ as follows. First, divide $M$ into parts, each parameterized by a function $\psi_i: D_i \to M$ over domains in $\R^n$, such that the images cover $M$ and overlap only on sets of measure $0$. Then, letting $\eta$ be the orientation form, write $\phi_i^*\nu = \pm f_i dx^1 \wedge \dots \wedge dx^n$, where each $f_i$ is positive everywhere. Then $\int_M \omega = \sum_i \int_{D_i}\psi_i^*\omega$. 

## Examples
First consider $\int_{S_1} xdy$, with $S_1$ oriented using the form  $\eta = ydx - xdy$. We parameterize by $\psi(\theta) = (\cos\theta, \sin\theta)$. Now we pull back the orientation form; we get $\sin(\theta)d\cos\theta - \cos\theta d\sin\theta = -\sin^2(\theta) - \cos^2\theta d\theta = -d\theta$. We then take $\int_{S_1}\omega = \int_{[0, 2\pi]}\phi^*(xdy) = \int_{[0, 2\pi]} \cos\theta d(\sin\theta) = -\int_0^{2\pi}\cos^2\theta d\theta$, with that minus sign coming from the orientation we calculated earlier. Finally, we just compute this to be $-\pi$.

Now we look at an integral over a surface. We let $M$ be the set of all points $(x, y, z)$ with $z = 1$ or $x^2 + y^2 = z^2$, and $x > 0, 0 \leq z \leq 1$. This defines part of a cone.  Then take $\omega = z^2 dy \wedge dz$. 

The way we've defined $M$ suggests breaking it up into two parameterized parts, $M_1$ defined by $(x, y, z) \in M$ and $z = 1$, and $M_2$ defined to be everything else. $M_1$ is just a semicircle, which we can define in the plane by $D_1: x^2 + y^2 \leq 1, x \geq 0$; then we can parametrize $\phi_1: D_1 \to M_1$ by $\phi_1(x, y) = (x, y, 1)$. Pulling back our form turns $dz$ into $0$, so $\int_{M_1}\omega = 0$. The other part we can parameterize by $\phi_2(x, y, z) = (x, y, \sqrt{x^2 + y^2})$. Pulling back our orientation form $dx \wedge dy$ gets us just $dx \wedge dy$ again, so the "right" orientation will be $dx \wedge dy$. Finally, we pull back $\omega$ itself. We get $(x^2 + y^2)dy \wedge d((x^2 + y^2)^{1/2}) = (x^2+y^2)dy \wedge \frac{x}{(x^2+y^2)^{1/2}}dx = x\sqrt{x^2+y^2}dy \wedge dx$. Thus $\int_{M_2}\omega = \int_{D_1}\phi^*\omega = \int_{D_1}x(x^2+y^2)^{1/2}dy \wedge dx = -\int_{D_1}x(x^2 + y^2)^{1/2}dxdy$. Now we can evaluate this with standard techniques from calculus. We get $-\int_{-1}^1 \int_0^{\sqrt{1 - y^2}}x(x^2 + y^2)^{1/2}dxdy$. We get $-\int_{-1}^1 \frac{1}{3}(x^2 + y^2)^{3/2} |_0^{\sqrt{1 - y^2}}dy = \frac{1}{3}\int_{-1}^1 (1 - |y|^3) dy = -\frac{2}{3}\int_0^1 1 - y^3 dy$, which is then equal to $-\frac{1}{2}$.  