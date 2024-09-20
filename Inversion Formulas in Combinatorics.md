These three theorems turn out to all be instances of the same idea: given a sequence $b_n$ expressed as some kind of sum of another sequence $a_n$, we can find a generating function $G(x)$ such that $B(x) = A(x)G(x)$ (letting $A(x)$, $B(x)$ be the generating functions of $a_n$ and $b_n$). Then we can multiply both sides by the reciprocal of $G(x)$ to get $a_n$ in terms of some sum or other function of the $b_n$s. 

## Ordinary Generating Functions
Say we have sequences $a_n$, $b_n$ with $b_n = \sum_{k=0}^n a_k$. Then $B(x) = \frac{A(x)}{1-x}$, so $B(x) - xB(x) = A(x)$. The LHS is $\sum_n b_nx^n - \sum_n b_nx^{n+1} = \sum_n (b_n - b_{n-1})x^n$, using the convention that $b_{-1} = 0$ to handle the first term. Thus $b_n - b_{n-1} = a_n$.

## Exponential Generating Functions: Binomial Inversion
Now suppose that $b_n = \sum_{k=0}^n \binom{n}{k} a_k$. This means, now letting $A(x)$ and $B(x)$ be exponential generating functions, that $B(x) = A(x)e^x$, so $A(x) = B(x)/e^x = B(x)e^{-x}$, where the coefficient of $\frac{x^n}{n!}$ on the RHS is  $\sum_{k=0}^n \binom{n}{k} b_k (-1)^{n-k}$. Thus $a_n = \sum_{k=0}^n \binom{n}{k}b_k(-1)^{n-k}$. 

## Dirichlet Generating Functions: Möbius Inversion

