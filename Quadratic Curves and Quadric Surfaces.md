
# Classification of Quadratic Curves
The general quadratic polynomial in $2$ variables can be written as $ax^2 + bxy + cy^2 + dx + ey + f$. We will show that, by transforming the coordinates by rigid motions (equivalently, by a suitable choice of orthogonal axes), we can transform this into one of the following forms:

$ax^2 + by^2 = c$, with $a, b > 0$ (ellipse)
$ax^2 - by^2 = c$, with $a, b > 0$ (hyperbola)
$y = ax^2$ (parabola)
$y^2 = ax^2$ (two lines)
$ax + by + c = 0$ (line)
$x^2 = 0$ (single point)
$ax + b = 0$ (single point)
$x^2 = a$ with $a \neq 0$ (two points)

First we rewrite the polynomial in matrix form. The "quadratic form" part $ax^2 + bxy + cy^2$ can be rewritten as $X^t AX$ where $X$ is the column vector $(x, y)^t$ and $A$ is the matrix $\MatrixTwoTwo{a}{b/2}{b/2}{c}$. Similarly, letting $B = (d, e)^t$, we have $dx + ey = B^tX$. By the spectral theorem, there exists an orthogonal matrix $P$ such that $PAP^t$ is diagonal. Thus, when we make the change of coordinates $X' = (x', y')^t = P^t X$, we get (abusing notation to reuse $a, b,$ etc. for the new coefficients and $x, y$ for the new variables) $ax^2 + by^2 + cx + dy + e = 0$. Now consider a few cases. 

First, suppose that $a, b$ are both nonzero. Then we can eliminate the $cx + dy$ terms by "completing the square", i.e. making the substitutions $x = x' - \frac{c}{2a}, y = y' - \frac{d}{2b}$, to get (abusing notation once again--we will keep doing this throughout, always choosing the first few letters as our coefficients) $ax^2 + by^2 - c = 0$. When $c = 0$ this is the degenerate case of two lines. Otherwise we get $ax^2 + by^2 = c$. When $a, b, c$ all have the same sign, this is an ellipse. When $a, b$ are both positive but $c$ is negative, or vice versa, the locus is empty, but it still in some sense has the form of the ellipse. When $a, b$ have opposite signs, this is a hyperbola. 

Now suppose that one of $a, b$ is nonzero: without loss of generality, say $a$ is nonzero. Then in the equation $ax^2 + dx + ey + f = 0$, we can eliminate $d$ by completing the square to get $ax^2 + by + c = 0$, but can't eliminate $b$ in the same way. If $b = 0$ then we get $ax^2 + c = 0$ which has either two roots or, if $c = 0$, a double root, in which case the locus consists of one or two points. If $b \neq 0$ then we can rearrange to get a parabola $y = ax^2 + b$, and a further translation of $y$ reduces this to $y = ax^2$. 

Suppose finally that, in $ax^2 + by^2 + cx + dy + e = 0$, $a, b$ are both equal to $0$. Then our equation has the form $ax + by + c =0$, which is either a line, a single point, or empty. 

# Classification of Quadric Surfaces
