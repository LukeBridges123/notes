# The Metric Space of Linear Operators
Let $L(\R^n, \R^m)$ be the set of all linear operators $R^n \to R^m$. We can then define a norm on operators by $||A|| = \sup_{x \in R^n, |x| \leq 1} |Ax|$; equivalently, $\sup_{x \in R^n, x \neq 0} |Ax|/|x|$. This is the "maximum stretch" given by $A$, and for a Hermitian operator will be equal to the eigenvalue with largest absolute value. This possesses all the defining properties of a norm and induces a metric, $d(A, B) = ||B - A||$; we also have the inequality $||BA|| \leq ||B||||A||$. Proof: let $x \in R^n$ with $|x| \leq 1$. Then $|BAx| = |B(Ax)|$. This is at most $||B||(|Ax|)$ which is in turn at most $(||B|| \cdot ||A||)|x|$; thus $||BA|| \leq ||B|| \cdot ||A||$. 

All this implicitly relies on $||A||$ actually being well-defined, and in particular $||A||$ being finite. Letting $e_1, \dots, e_n$ be the standard basis and letting $x \in \R^n$ be such that $|x| \leq 1$, we have $x = \sum_i c_ie_i$; due to the condition on $|x|$ all of the $c_i$ will be such that $|c_i| \leq 1$. Then $Ax = \sum_i c_iAe_i$ and $|Ax| = |\sum_i c_iAe_i| \leq \sum_i |c_iAe_i| \leq \sum_i |Ae_i|$. Thus $||A||$ is bounded by $\sum_i |Ae_i|$. 

## Continuity of Linear Operators

# The Total Derivative

## Continuous Differentiability
Associated with a differentiable function $f: E \to \R^m$, where $E \subseteq \R^n$ is some open set, is a function $f': E \to L(\R^n, \R^m)$. If this is continuous we say that $f$ is continuously differentiable. We then have the following criterion for continuous differentiability:

$f$ is continuously differentiable if and only if the partial derivatives $D_jf_i$ exist and are continuous on $E$ (where $1 \leq i \leq m$ and $1 \leq j \leq n$). 

For one direction, assume $f$ is continuously differentiable. Note that, for all $x \in E$, we have $D_jf_i(x) = (f'(x)e_j) \cdot u_i$ (using $u_i$ as a basis for the range and $e_j$ as a basis for the domain). ,,,,....

For the other direction, let $x \in E$, and let $A$ be the matrix of partials $D_jf_i$. Then we have $f(x + h) - f(x) - Ah = (f_1(x + h) - f_1(x), \dots, f_m(x+h) - f_m(x)) - (\nabla(f_1) \cdot h, \dots, \nabla(f_m) \cdot h)$. We know that, for a function $\R^n \to \R$, if the all the partial derivatives exist (i.e. if the gradient exists) then 

## Derivative Rules


# Inverse Function Theorem
## Contraction Mappings
In any metric space $X$, define a "contraction" to be a function such that there exists a constant $c$ with $d(\phi(x), \phi(y)) \leq cd(x, y)$ for all $x, y$. Any contraction is uniformly continuous. In a complete metric space, any contraction has a unique fixed point: that is, there exists a unique $x \in X$ with $\phi(x) = x$. 

For uniqueness, say $x_1, x_2$ are both fixed points of $\phi$. Then $d(x_1, x_2) \leq d(\phi(x_1), \phi(x_2)) \leq cd(x_1, x_2)$ and since $c < 1$ this is impossible if $d(x_1, x_2)$ is positive. Thus $d(x_1, x_2) = 0$ and so $x_1 = x_2$. 

Now we handle existence. Let $x_0$ be any point in $X$, and define $x_n$ recursively as $\phi(x_{n-1})$. We can then get a recurrence for the distance between successive points: $d(x_{n+1}, x_n) = d(\phi(x_n), \phi(x_{n-1})) \leq cd(x_n, x_{n-1})$. Thus the distance between successive points decreases by a factor of $c$ each time. This implies that the sequence $(x_n)$ is Cauchy: we have $d(x_{n+1}, x_n) \leq c^n d(x_0, x_1)$, hence if $n < m$, we have $d(x_n, x_m) \leq \sum_{i=n+1}^m d(x_i, x_{i-1}) \leq d(x_0, x_1)(c^n + c^{n+1} + \dots + c^{m-1}) \leq d(x_0, x_1) \frac{c^n}{1 - c}$. As $n$ increases, that last term in the chain of inequalities goes to $0$, and so does $d(x_n, x_m)$. Thus $(x_n)$ is Cauchy, and by the completeness of $X$ converges to some point $x$. Note by the continuity of $\phi$ that $\phi(x) = \lim_{n \to \infty} \phi(x_n) = x$, so $x$ is a fixed point. 

## In 1 Dimension
The 1-dimensional special case of the inverse function theorem is as follows: let $f$ be a function where $f'(a)$ is invertible, which in 1d just means that $f'(a) \neq 0$. Then there is a neighborhood $B_r(a)$ about which $f$ has an inverse.
## In n Dimensions
The more general version: let $E \subseteq R^n$ and let $f: E \to \R^n$ be a continuously differentiable function. If $f'(a)$ is invertible, for some $a \in E$, then (letting $b = f(a)$) we have:

a) There exist open sets $U, V \subseteq \R^n$ such that $a \in U, b \in V$, $f$ is injective on $U$, and $f(U) = V$ (in other words $f$ is an invertible $U \to V$); thus there exists $g: V \to U$ with $g(f(x)) = x$ for all $x \in U$ 
b) $g$ is continuously differentiable 

Some facts from linear algebra that we'll need: if $A$ is an invertible operator, and $B$ is such that $||B - A|| \cdot ||A^{-1}|| < 1$, then $B$ is invertible as well. The space $\Omega$ of invertible operators in $L(\R^n)$ is open, and the function that sends $A$ to $A^{-1}$ is continuous. 

Onto the proof: we can assume without loss of generality that $a = b = 0$ (just by making translations) and that $f'(a) = I$. Or note that, letting $h(x) = A^{-1}(f(x + a) - f(a))$, $h$ has derivative $A^{-1}A = I$ and $h(0) = 0$, and if we prove the theorem for $h$ it will follow for $f$ and vice versa. 

Since $f'$ is continuous at $0$, there exists $\rho > 0$ such that $||f'(x) - I|| < \frac{1}{2}$ for all $x \in B_\rho(0)$ . Let $U = B_\rho(0)$ and let $V = f(U)$. Now letting $y \in V$, we will look for a point $x \in U$ with $f(x) = y$. In other words we have $y - f(x) = 0$ or $x = x + (y - f(x))$; letting $\phi(x) = x + y - f(x)$ our problem reduces to finding a fixed point of $\phi$. We claim that $\phi$ is a contraction. This is because $\phi'(x) = I - f'(x)$, so for all $x \in U$ we have $||\phi'(x)|| \leq ||I - f'(x)|| \leq 1/2$, and so for all $x_0, x_1$ we have $||\phi(x_0) - \phi(x_1)|| \leq \frac{1}{2}|x_0 - x_1|$. 

# Implicit Function Theorem
Say $x = (x_1, \dots, x_n) \in \R^n, y = (y_1, \dots, y_m) \in \R^m$; we will use $(x, y)$ for the point $(x_1, \dots, x_n, y_1, \dots, y_m) \in \R^{n+m}$. As a preliminary, note that for any linear transformation $A: R^{n+m} \to R^n$, there exist corresponding linear transformations $A_x: \R^n \to \R^n$ and $A_y: \R^m \to \R^n$ with $A(h, k) = A_x(h) + A_y(k)$: just define $A_x(h) = A(h, 0)$ and $A_y(k) = A(0, k)$ and then the result follows by linearity. From this fact we can get a "linear version" of the implicit theorem: suppose $A_x$ is invertible; then letting $k \in \R^m$ and $h = -(A_x)^{-1}A_yk$ we have $A(h, k) = A_x(h) + A_y(k) = A_x(-A_x)^{-1}A_y(k) + A_y(k) = -A_y(k) + A_y(k) = 0$. That is, given the equation $A(h, k) = 0$, we can, for any fixed $k$, solve this equation for $h$ in terms of $k$, as long as $A_x$ is invertible. 

Now we can state the general, "nonlinear" version of the implicit function theorem. Let $f$ be a continuously differentiable function from an open set $E \subseteq \R^{n+m}$ to $\R^n$. Say that $f(a, b) = 0$ for some $(a, b) \in E$. Let $A = f'(a, b)$ and assume that the corresponding $A_x$ is invertible; this will be the $n \times n$ matrix of partial derivatives with respect to the $x_i$. Then 

a) there exist open sets $U \subseteq \R^{n+m}, W \subseteq \R^m$, with $(a, b) \in U$ and $b \in W$, such that for all $y \in W$ there exists a unique $x$ such that $(x, y) \in U$ and $f(x, y) = 0$. 

b) letting $g$ be the function that associates a unique $x$ to each $y$, i.e. $g(y) = x$, then $g$ is also continuously differentiable $W \to \R^n$. We also have $g(b) = a$, $f(g(y), y) = 0$ for all $y \in W$, and $g' = -(A_x)^{-1}A_y$. 

(So $U$ is the region of the domain in which it is "locally" possible to solve for $x$ in terms of $y$.)