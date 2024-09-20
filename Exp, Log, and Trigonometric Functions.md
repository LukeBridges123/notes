# The Exponential
Define $E(z) = \sum \frac{z^n}{n!}$; by the ratio test this converges absolutely for all real numbers, and indeed all complex numbers.

## e^xe^y = e^(x+y)
If we take $E(z)E(w)$ we get, by the convolution rule for the products of series, $\sum_{n = 0}^\infty (\sum_{i = 0}^n \frac{z^i}{i!}\frac{w^{n-i}}{(n-i)!}) = \sum_{n = 0}^\infty \frac{1}{n!}\sum_{i=0}^n \frac{n!}{i!(n-i)!}z^iw^{n-i} = \sum_{n=0}^\infty \frac{(z+w)^n}{n!} = E(z+w)$. Thus $E(z+w) = E(z)E(w)$, as we expect from the exponential. 

## E(x) is positive
We must have $E(z)E(-z) = E(0) = 1$ for all $z$. We already know that $E(z)$ is positive for all nonnegative real $z$, just by looking at the power series; if $z$ is nonnegative then $E(-z)$ must be positive as well, else $E(z)E(-z)$ could not equal $1$.

## The Derivative
We have $\frac{E(z + h) - E(z)}{h} = E(z)\frac{E(h) - 1}{h} = E(z)(\frac{1}{h}(h + h^2/2 + h^3/3! + \dots ) = E(z)(1 + h/2 + h^2/3! + \dots))$. The limit as $h$ goes to $0$ of this is clearly $1$, hence the derivative of $E(z)$ is $E(z)$. 

## Relating This to Other Definitions of Exponentiation
Having already defined $e$ to be $1 + \frac{1}{2!} + \frac{1}{3!} + \dots$ we see that $E(1) = e$. Similarly, defining exponentiation to natural number powers as repeated multiplication, we get $E(n) = E(1 + \dots + 1)$ (with $n$ ones) $= E(1) \cdots E(1)$ ($n$ times) = $e^n$; extending to negative integers and rational numbers in the usual way works as expected. Finally we can define $e^x$ for arbitrary real $x$ to be $\sup\{e^p \mid p < x, p \in \Q\}$, which then is $\sup\{(E(p)) \mid p < x, p \in \Q\}$  since $e^p$ and $E(p)$ agree for rational $p$; this supremum is then $E(x)$, by the continuity and monotonicity of $E$. Thus $e^x$, defined in this sense, is equal to $E(x)$. 

# The Logarithm
Since $E(x)$ is increasing (hence injective) it has an inverse on its whole range, $(0, \infty)$, called $L$. This will be differentiable and increasing since $E$ is differentiable and increasing. By the inverse function theorem we have $L'(y) = \frac{1}{y}$, so $L(y) = \int_1^y \frac{1}{x}dx$, which we just call $\log(y)$ or $\ln(y)$. All the standard properties of $\log$ follow from the corresponding properties of $E$. For example, since $E(x)E(y) = E(x+y)$ we have 