# Definition of a Lie Group
A Lie group is a group which is also a manifold, where the basic operations of the group are smooth. That is, given a group $G$ with some manifold structure, we require that the maps $(G \times G) \to G$ and $G \to G$ given by $a, b \to ab$ and $a \to a^{-1}$ are smooth. 

# Examples
## Vector Spaces

## General Linear Group

## Special Linear Group

## Orthogonal Group
We know that the orthogonal matrices--the linear maps that preserve lengths and angles, or equivalently the real matrices that satisfy $A^tA = I$--form a group, a subgroup of $GL_n(\R)$. Now we prove that they form a submanifold of $GL_n$ as well, using the regular value theorem.

Define a map from the set of all $n \times n$ real matrices to the set of symmetric $n \times n$ real matrices by $f(A) = A^tA$. This is a map into the symmetric matrices, since $A^tA$ is symmetric: $(A^tA)^t = A^t A^{tt} = A^tA$. It is also smooth, since the entries of $f(A)$ are polynomials of the elements of $A$. Then $O(n)$ is a level set of $f$, namely $O(n) = f^{-1}(I)$.

Now we check that $I$ is a regular value. We start by looking at the differential $Df_A(B)$ where $A$ is an orthogonal matrix and $B$ is any matrix. Equivalently, this is $\frac{d}{dt}f(A + tB)$ evaluated at $t = 0$. This equals $\frac{d}{dt}((A + tB)^T(A + tB))$, or $\frac{d}{dt}(A^TA + t(A^TB + B^TA) + t^2B^TB)$, which in turn equals $A^TB + B^TA + 2tB^TB$, and evaluating at $t=0$ gets $A^TB + B^TA$.  

Now consider $(Df)_A(C)$ where $C = \frac{1}{2}AS$ for some symmetric $S$. Then $(Df_A)(c) = \frac{1}{2}(A^TAS + (AS)^TA) = \frac{1}{2}(S + S^TA^TA) = \frac{1}{2}(S + S^T) = \frac{1}{2}(S + S) = S$. Thus for any symmetric matrix $S$, there exists a matrix $C$ with $(Df_A)(C) = S$, so the differential is surjective for any orthogonal $A$, and so $I$ is a regular value of $f$. By the regular value theorem, $O(n)$ is a closed, embedded submanifold of $\R^{n^2}$. It has dimension $n^2$ minus the dimension of the set of all symmetric matrices, $\frac{n(n+1)}{2}$, i.e. $n^2 - \frac{n(n+1)}{2} = \frac{n(n-1)}{2}$. 

The smoothness of the group operations is inherited from $SL_n(\R)$. Thus $O(n)$ is a Lie group. 