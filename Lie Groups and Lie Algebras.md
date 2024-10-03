# Definition of a Lie Group
A Lie group is a [[Groups|group]] which is also a [[Manifolds|manifold]], where the basic operations of the group are smooth. That is, given a group $G$ with some manifold structure, we require that the maps $(G \times G) \to G$ and $G \to G$ given by $a, b \to ab$ and $a \to a^{-1}$ are smooth. 

# Examples
## Vector Spaces

## General Linear Group

## Special Linear Group

## Orthogonal Group
We know that the [[Orthogonal Operators and Isometries|orthogonal matrices]]--the linear maps that preserve lengths and angles, or equivalently the real matrices that satisfy $A^tA = I$--form a group, a subgroup of $GL_n(\R)$. Now we prove that they form a submanifold of $GL_n$ as well, using the regular value theorem.

Define a map from the set of all $n \times n$ real matrices to the set of symmetric $n \times n$ real matrices by $f(A) = A^tA$. This is a map into the symmetric matrices, since $A^tA$ is symmetric: $(A^tA)^t = A^t A^{tt} = A^tA$. It is also smooth, since the entries of $f(A)$ are polynomials of the elements of $A$. Then $O(n)$ is a level set of $f$, namely $O(n) = f^{-1}(I)$.

Now we check that $I$ is a regular value. We start by looking at the differential $Df_A(B)$ where $A$ is an orthogonal matrix and $B$ is any matrix. Equivalently, this is $\frac{d}{dt}f(A + tB)$ evaluated at $t = 0$. This equals $\frac{d}{dt}((A + tB)^T(A + tB))$, or $\frac{d}{dt}(A^TA + t(A^TB + B^TA) + t^2B^TB)$, which in turn equals $A^TB + B^TA + 2tB^TB$, and evaluating at $t=0$ gets $A^TB + B^TA$.  

Now consider $(Df)_A(C)$ where $C = \frac{1}{2}AS$ for some symmetric $S$. Then $(Df_A)(c) = \frac{1}{2}(A^TAS + (AS)^TA) = \frac{1}{2}(S + S^TA^TA) = \frac{1}{2}(S + S^T) = \frac{1}{2}(S + S) = S$. Thus for any symmetric matrix $S$, there exists a matrix $C$ with $(Df_A)(C) = S$, so the differential is surjective for any orthogonal $A$, and so $I$ is a regular value of $f$. By the regular value theorem, $O(n)$ is a closed, embedded submanifold of $\R^{n^2}$. It has dimension $n^2$ minus the dimension of the set of all symmetric matrices, $\frac{n(n+1)}{2}$, i.e. $n^2 - \frac{n(n+1)}{2} = \frac{n(n-1)}{2}$. 

The smoothness of the group operations is inherited from $SL_n(\R)$. Thus $O(n)$ is a Lie group. 

# Lie Algebras
## Abstract Lie Algebras
....
## The Lie Algebra of a Lie Group
Associated with any $g \in G$ we have two diffeomorphisms, "left translation" $L_g$ and "right translation" $R_g$. These are given by $L_g(h) = gh$ and $R_g(h) = hg$. A vector field $X$ on $G$ is called "left-invariant" if $(L_g)_*X = X$ for all $X$. (Be careful here, because the two vector fields are being evaluated at different points here--we need $(L_g)_*X_h = X_{gh}$.) The set of all left-invariant vector fields on $G$ is called the Lie algebra of $G$, denoted $\mathfrak{g}$. This is a vector space, in the sense that linear combinations of left-invariant vector fields are also left-invariant vector fields. It is nonempty, because the zero vector field is left-invariant. Finally, it is a Lie algebra, in the sense of being closed under the bracket operation (the bracket of left-invariant vector fields is left-invariant). Let $X, Y$ be left-invariant. Then for any $g$, $(L_g)_*[X, Y] = [(L_g)_*X, (L_g)_*Y] = [X, Y]$, where we can use the naturality of brackets because $L_g$ is a diffeomorphism, and the second equality comes from the left-invariance of $X$ and $Y$.  
## Lie Algebra = Tangent Space at the Identity
Remember that these vector fields give derivations at each point: a point can thus act on vector fields, by $p(X) = X_p$ . As it happens, the "evaluation at the identity" map $\epsilon$ is a vector space isomorphism $\mathfrak{g} \to T_IG$, where $I$ is the identity element in the group. Thus $\dim(\mathfrak{g}) = \dim(G)$. Proof: additivity of $\epsilon$ follows from $\epsilon(X + Y) = (X + Y)_I = X_I + Y_I = \epsilon(X) + \epsilon(Y)$, and the same for scalar multiplication. Thus $\epsilon$ is linear. To show injectivity, we need $\ker(\epsilon) = \{0\}$, where $0$ here is the vector field which is $0$ everywhere. If $\epsilon(X) = 0$, then $X_I = 0$; but by left-invariance of $X$, we have $(L_g)_*(X_I) = X_{gI} = X_g = 0$ for all $g \in G$. Thus $X$ is zero everywhere, so the zero vector field is the only element of the kernel. For surjectivity, given a tangent vector $X_I \in T_IG$, define a vector field $X$ on $G$ by $X_g = (L_g)_*X_I$. Then this is left-invariant, because for any $h$, $(L_h)_*(X_g) = (L_h)_*(L_g)_*X_I = (L_{hg})_*X_I = X_{hg}$, with the last equality following from the definition of $X$. We also need to check smoothness of $X$; this follows from the smoothness of multiplication, which implies the smoothness of left multiplication $L_g$ and its differential $(L_g)_*$. 

## Linear Vector Fields
A linear vector field on $\R^n$ is one where, for all $x \in \R^n$, there exists a matrix $A$ with $X(x) = Ax$. These correspond to systems of linear differential equations, and we can find their integral curves by solving those systems. This is because the flow $\phi$ of such a vector field satisfies $\frac{d}{dt}(\phi_t(x)) = X(\phi(x)) = A(\phi(x))$. Formally, we have $\phi_t(x) = e^{tA}x_0$, thinking of the equation $\frac{d}{dt}(\phi_t(x)) = A(\phi(x))$ as analogous to $y' = ay$. To work with this more rigorously, we can define the [[Matrix Exponential|matrix exponential]] as a power series $e^{tA} = \sum_{k \geq 0} \frac{t^k}{k!}A^k$, and prove that $e^{tA}$ solves the differential equation $x' = Ax$. 