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
Recall that the differential of a function $M \to \R$ is defined by $(df)_p(X_p) = X_p(f)$. (Strictly speaking it should be $X_p(f) \cdot \frac{d}{dt}$, but we use the identification between $\R$ and its tangent space.) This is $C^\infty(M)$-linear since $df(aX + bY) = (aX + bY)f = adf(X) + bdf(Y)$ and $df(gX) = (gX)f = g(Xf) = gdf(X)$ for all $a, b \in \R$ and $g \in C^\infty(M)$. The result above then implies that $df$ is a 1-form.

We can then write $df$ in the basis $dx^i$ given by local coordinates $x^i$. If $f: \R^n \to \R$ is a smooth function then $df(\frac{\partial}{\partial x^i}) = \frac{\partial}{\partial x^i}f = \frac{\partial f}{\partial x^i}$. Thus $df = \sum_i \frac{\partial f}{\partial x^i}dx^i$. 

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



# K-Forms
.....
.....
## Integrating over Surfaces
As motivation for how we're going to generalize 1-forms to higher dimensions, consider integrating some object $\phi$ over a surface. (What this object is, we will see as we go along.) As with 1-forms, we parameterize our surface by $\gamma(s, t)$; at each point we get tangent vectors $S = \gamma_*(\pd{}{s}), T = \gamma_*(\pd{}{t})$. 

.....

## Definition of a K-Form
....
something about constructions with the tangent and cotangent bundles
....

....
We then get the *exterior algebra bundle* $\wedge^* (T^*M)$, which assigns, to each point, the exterior algebra on the cotangent space at that point. As with 1-forms, we can get a local trivialization of this bundle by choosing local coordinates and writing all the elements of the exterior algebra in that basis. 

Sections of the bundle $\wedge^k (T^*M)$ are called differential $k$-forms. The set of all $p$-forms is denoted $\Omega_M^p$, and the set of all sections of the whole exterior algebra bundle is denoted $\Omega_M^*$. 

Much like the different ways to think of vector fields and 1-forms, general k-forms can be thought of in the following ways: sections of $\wedge^k(T^*M)$; as alternating multilinear maps on $p$-tuples of vector fields, $X(M) \times \dots \times X(M) \to C^\infty(M)$, which are $C^\infty(M)$-linear; and locally, like linear combinations of basic forms $dx^I$. 

## Operations on Forms
### Wedge Product
The wedge product on alternating forms can be extended into an operation on differential forms. That is, we have an operation $\wedge: \Omega_M^p \times \Omega_M^q \to \Omega_M^{p+q}$ which has all the properties of the wedge product on alternating forms: bilinearity, antisymmetry, etc. We do this by just taking the wedge product pointwise, $(\omega \wedge \eta)_p = \omega_p \wedge \eta_p$. 
### Pullback
We can also pull back differential forms by functions. Let $F: M \to N$ and let $\omega$ be a $p$-form on $n$. Then we can get a $p$-form on $M$, $F^*\omega$, defined in the following way.

For 0-forms (scalar-valued functions), we define it like before, $F^* f = f \circ F$. 

For exact 1-forms $df$, we again define it like before, $F^*(df) = d(F^* f) = d(f \circ F)$. 

For a wedge product $F^*(\omega_1 \wedge \dots \wedge \omega_p)$, we pull back each "factor" individually, $F^*\omega_1 \wedge \dots \wedge F^*\omega_p$. 

Finally, for arbitrary forms, we write them in a basis as a sum of wedge products of exact 1-forms, and then pull back each term, using the linearity of the pullback. 

### Exterior Derivative
The exterior derivative $d$ generalizes the differential operator on scalar functions to an operaton on differential forms. We can characterize it axiomatically as follows: $d$ is a linear map $\Omega_M^p \to \Omega_M^{p+1}$ such that: 

(a) on 1-forms, $d$ acts like the differential, so $d$ applied to $f$ is the 1-form $df$, defined as usual so that $df(X) = Xf$

(b) $d$ is a skew-derivation: $d(\omega \wedge \nu) = d\omega \wedge \nu + (-1)^p \omega \wedge d\nu$, where $\omega$ is a p-form

(c) $d$ is nilpotent: $d \circ d = 0$. 

There is a unique linear map satisfying all of these properties. 

Proof: note first that we only need to prove this in a single local coordinate system. Once we know it exists and, importantly, is unique on some chart $U$, standard arguments then show that $d$ is defined and works the same on the rest of the manifold. 

For any $p$-form $\omega$, write $\omega = \sum_I \omega_I(x) dx^I$. Then, whatever $d$ is, we must have $d\omega = \sum_I d(\omega_I(x) \wedge dx^I) = d(\omega_I(x)) \wedge dx^I + \omega_I(x) \wedge d(dx^I)$. That last term expands out into a bunch of terms, all of which have a factor of the form $d(dx^i)$; but that is $0$ (by the nilpotence of $d$) and so $d(dx^I) = 0$. Thus $d\omega  = \sum_I d\omega_I(x) \wedge dx^I$. We can then expand that out explicitly using the properties of the differential of a scalar function.

This whole argument shows uniqueness: we can get $d\omega  = \sum_I d\omega_I(x) \wedge dx^I$ just by applying the axioms, so anything that satisfies the axioms must have that value. 

To show existence, we can just define $d\omega$ by the formula we found above. We can then check that all the axioms hold. 

### Interior Multiplication
The contraction/interior multiplication operation on multilinear forms extends to an operation on differential forms: we define $(i_X(\omega))_p = i_{X_p}(\omega_p)$ for a vector field $X$, differential form $\omega$, and point $p$. 

The basic properties of interior multiplication--that it is a skew-derivation whose square is $0$--carry over to differential forms. We then also have that $i_X(\omega)$ is $C^\infty(M)$-linear in both arguments, and in particular that $i_{fX}(\omega) = fi_X(\omega)$ and $i_X(f\omega) = fi_X(\omega)$ for any smooth function $f$.
### Lie Derivative
The Lie derivative of a form in the direction of a vector field, $L_X(\omega)$, is defined in essentially the same way as the Lie derivative of a vector field, namely $\frac{d}{dt}F_{-t}^*(\omega_p)$ where $F_t$ is the flow generated by $X$. The Lie derivative of a k-form is another k-form.

This is then a derivation, i.e. it is linear with respect to $\omega$ and obeys the product rule $L_X(\omega \wedge \eta) = L_X\omega \wedge \eta + \omega \wedge L_X\eta$. It also commutes with the exterior derivative, $L_X(d\omega) = dL_X(\omega)$. 

These rules suffice to compute Lie derivatives of any forms given in coordinates. For a 0-form/scalar function $f$ we have $L_X(f) = Xf$. For a basic 1-form $dx^i$ we have $L_X(dx^i) = d(L_X(x^i)) = d(Xx^i)$. For a more general 1-form $\sum_i f_i dx^i$, linearity lets us compute this by computing $L_X(f_idx^i)$ individually for each $i$; the fact that $L_X$ is a derivation then makes this equal to $L_X(f_i)dx^i + f_iL_X(dx^i)$, which we already know how to handle. Finally, for $k$-forms, we use linearity and then the product rule for derivations to reduce the problem to taking Lie derivatives of 1-forms.

Some further results about Lie derivatives are Cartan's formula $L_X = di_X + i_Xd$, where $i$ is the interior multiplication operator, and.....