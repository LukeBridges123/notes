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