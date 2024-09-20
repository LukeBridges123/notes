## Reduction of a System of Linear Equations to a Single, Higher-Dimensional Linear Equation
Say you have a system of n linear equations in m unknowns over field $\mathbb{F}$: 
$a_1^1x_1 + ... + a_m^1x_m = y_1$ 
...
$a_1^nx_1 + ... + a_m^nx_m = y_n$ 
(Here coefficients are denoted with superscripts to represent which equation they're in and subscripts to represent what variable they're attached to.)

It becomes convenient to represent this in terms of a single equation involving a linear map. Instead of asking "what assignment of values to each of the m variables will satisfy all n equations?", think of a linear map $L: \mathbb{F}^m -> \mathbb{F}^n$ which is equivalent to the original in the sense that, for any $x_1, ... x_m$ that satisfy the original system, the vector $(x_1, ... x_m$) will satisfy the equation $L(x) = (y_1, ... y_n)$; then answering "what assignment of a (vector in $F^m$) value to x will satisfy the equation $L(x) = (y_1, ... y_n)?$" will answer the original question.  In particular, we'd like to write down this map as a matrix $A$ with respect to the standard basis of $F^m$ and solve the "matrix-vector equation" $Ax = y$ for fixed $y = (y_1, ... y_n)$. To find such a matrix, we need only know how $L$ acts on each of the standard basis vectors $e_1, ... e_m$. In particular, feeding $e_i$ into $L$ corresponds to setting $x_i$ to 1 and all other variables to 0, so that $L(e_i) = (a_i^1, ... a_i^n)$. Therefore, column $i$ of $A$ should be filled with the coefficients attached to $x_i$. Doing this for all standard basis vectors gives a matrix whose $j$th row is simply filled with the coefficients of $a_1^jx_1 + ... + a_m^jx_m = y_j$, i.e. a matrix that looks as if you had simply written down the equations and erased everything except the coefficients. Hence we can turn a system of linear equations into an equation $L(x) = y$, which can be represented as a matrix-vector equation using the coefficient matrix as below:

## Existence and Uniqueness of Solutions
A benefit about converting systems of linear equations into single linear maps is that results about dimension, injectivity, and surjectivity can be applied to give necessary (and sometimes sufficient) conditions for the existence and uniqueness of solutions to systems of linear equations. 

First, some general results about linear equations of the form $L(x) = y$, where $L$ is a map between arbitrary vector spaces V and W and $y$ is fixed. If a solution $x_0$ exists, then all solutions are of the form $x_0 + z$ where $z \in$ null($L$). Vectors of this form are indeed solutions, because $L(x_0 + z) = L(x_0) + L(z) = y + 0 = y$. Furthermore, if $x_1$ is also a solution, then we can say $x_1 = x_0 + (x_0 - x_1)$. $x_0 - x_1$ is in null($L$), since $L(x_0 - x_1) = L(x_0) - L(x_1) = y - y = 0$. So we can say that $x_1 = x_0 + z$ with $z \in$ nulI($L$) by setting $z = x_0 - x_1$. So, as desired, any solution is of the form $x_0 + z$, and everything of the form $x_0 + z$ is a solution. The upshot of this is that the question of whether solutions to $L(x) = y$, if they are exist, are unique, reduces to the question of whether null($L$) = $\{0\}$, or equivalently, of whether $L(x) = 0$ has a unique solution (it always has *a* solution, given that x = 0 works), or equivalently, of whether $L$ is injective. Also, existence of solutions $L(x) = y$ reduces to asking whether $y \in$ range($L$), since the equivalence of "y is in the range of $L$" and "L(x) = y admits a solution" follows essentially from the definition of range; thus $L(x) = y$ always has a solution iff $L$ is surjective.

Thus, the rank-nullity theorem and various theorems about dimension and in/surjectivity can be applied here. See "corollaries about dimension, injectivity, and surjectivity" in [[Linear Maps]] for the results being applied here. For instance, if dim(V) > dim(W), then solutions to $L(x) = y$, when they exist, will never be unique, as $L$ has a nontrivial nullspace. If dim(V) < dim(W), then solutions to $L(x) = y$ do not exist for all y, since dim(range(L)) < dim(W) and so L is not surjective. To more directly apply this to systems of linear equations, note that solving a homogenous system of equations (where all constant terms equal 0) is equivalent to solving $L(x) = 0$; for a certain linear map; when there are more variables than equations, $L$ in the equivalent linear equation $L(x) = 0$ is a linear map $F^m -> F^n$ with $m > n$, so $L$ is not injective, therefore null($L$) contains nonzero vectors, therefore the original homogenous system admits solutions beyond the trivial one of setting all variables equal to 0. In an inhomogenous equation (not all constants are 0) with more equations than variables, not all sets of values for the constant terms will have solutions, because in the corresponding linear equation $L(x) = y$ with $L: F^m -> F^n$, we have $n < m$, so $L$ is not surjective, so not all values of $y$ admit solutions, so not all sets of constants in the original system admit solutions. 

All of the above gives a plan for solving general linear equations and systems of linear equations: given $y$, somehow compute $x$ such that $L(x) = y$ (perhaps just looking for a single solution, perhaps finding the range of $L$ and then expressing $y$ in it), then to check uniqueness, solve $L(x) = 0$. But to do this, one needs a concrete algorithm for solving linear systems and general linear equations; this is Gaussian elimination/ row reduction.
## Gaussian Elimination