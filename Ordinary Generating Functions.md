## Formal Power Series

## Wilf Rules

### Rule 1: Shifted sequences
Given a sequence $a_n$ with ogf $F(x)$, the ogf of $a_{n+k}$ for a natural number $k$ is $\frac{F(x) - a_0 - a_1x \dots -a_{k-1}x^{k-1}}{x^k}$. Subtracting off those terms in the numerator leaves you with $a_kx^k + a_{k+1}x^{k+1} + \dots$ and then dividing by $x^k$ gives you $a_k + a_{k+1}x + a_{k+2}x^2 + \dots = \sum_n a_{n+k}x^n$, as desired.
### Rule 2: Polynomials in n
Again take a sequence $a_n$ and ogf $F(x)$, and suppose you have a polynomial in n, $p(n) = c_0 + c_1n + \dots + c_kn^k$ and want to find the ogf of the sequence $a_np(n)$. This turns out to be $p(xD)F(x)$ -- i.e., take the polynomial $p$, substitute the operator $xD$ (differentiate, then multiply by $x$) for $n$ (interpreting powers of the operator as iterated composition), then apply this to $F(x)$. To see how this works, first note that the application distributes out to $c_0F(x) + c_1xDF(x) + \dots + c_k(xD)^kF(x)$. We now deal with each of those terms individually, say $c_i(xD)^i$. Differentiating $\sum_n a_nx^n$ gets $\sum_n na_nx^{n-1}$, and then multiplying this by $x$ gets $\sum_n na_nx^n$. Repeating this $i$ times total gets $\sum_n n^i a_nx^n$. So, going back to $c_0F(x) + c_1xDF(x) + \dots + c_k(xD)^kF(x)$, this becomes $c_0\sum_n a_nx^n + c_1\sum_n na_nx^n + \dots + c_k\sum_k n^k a_n x^n = \sum_n(c_0 + c_1n + \dots c_kn^k)a_nx^k = \sum_n p(n)a_nx^n$, as desired.  
### Rule 3: Products of 2 ogfs
Let $A(x) = \sum_n a_nx^n$, $B(x) = \sum_n b_nx^n$. Then $A(x)B(x) = \sum_n (\sum_{k=0}^n a_kb_{n-k})x^n$. This is a theorem for polynomials and convergent power series, and can be taken as simply a definition of multiplication for formal power series. As motivation: in the product $(a_0 + a_1x + a_2x^2 \dots)(b_0 + b_1x + b_2x^2 \dots)$, when fully expanded, we expect to see terms of the form $a_ib_jx^{i+j}$ for every possible pair $(i, j)$. So terms with exponent $x^n$ will have coefficients of the form $a_kb_{n-k}$ for some $k$, and collecting all such terms gets $\sum_{k=0}^n a_kb_{n-k}$. Thus that sum will be the coefficient on $x^n$ in the product $A(x)B(x)$. 
### Rule 4: Products of many ogfs
Generalizing the above to products of any arbitrary (finite) number of power series, we get for 3 series $A(x)B(x)C(x) = \sum_{n}(\sum_{i + j + k = n} a_ib_jc_k)x^n$, and so on for when more series are involved. 
### Rule 5: Partial sums
As a special case of the above, $\frac{A(x)}{1-x} = \sum_n (\sum_{k=0}^n a_k )x^n$. So multiplying a power series by $\frac{1}{1-x}$ gives you the ogf of the partial sums of the sequence $a_n$. So e.g. $\frac{1}{(1-x)^2}$ is the ogf of the natural numbers (starting with 1), $\frac{1}{(1-x)^3}$ is the ogf of the triangular numbers, and so on. 
## Recurrences with ogfs
### Linear homogenous recurrences
Any linear homogenous recurrence, i.e. of the form $a_{n+k} = b_0a_n + b_1a_{n+1} + \dots + b_{n+k-1}a_{n+k-1}$ where the b's are constants, will have its ordinary generating function be a rational function, which can be found essentially just by using Wilf Rule 1 and doing some algebra. The denominator will be a degree-k polynomial and will be determined completely by the form of the recurrence itself (typically, $1 - b_{n+k-1}x - \dots - b_0x^k$ ) and the numerator will be determined by the initial condition. A partial fraction decomposition, when the denominator has no repeated roots, can put it into a form consisting of a sum of terms like $\frac{c_i}{1 - r_ix}$, which expands into $\sum_n c_i r_i^n x^n$, giving the "Binet form" $a_n = \sum_i c_i r_i^n$. Repeated roots in the denominator change the Binet form a bit, leading to coefficients on the $r_i^n$ that are polynomials in n. See [[Fibonacci Numbers]] for an example. 
### Linear inhomogenous recurrences
When a linear recurrence has coefficients or extra terms that are functions of $n$, e.g. $a_{n+1} = na_n$, this can be dealt with in more or less the same way as with homogenous recurrences, plus some use of Rule 2 to deal with the $n$'s. 
### Recurrences with two parameters
With a recurrence involving a two-variable function, say $f(n, k)$, there are several possible ogfs that could be used, e.g. $\sum_n f(n, k) x^n$ (fixed k), $\sum_k f(n, k) y^k$ (fixed n), and $\sum_{n, k}f(n, k)x^ny^k$ (two variables, necessitating a double sum). This can lead to completely different generating functions, e.g. $(1+x)^n$ for the binomial coefficients with fixed $n$ and $\frac{x^k}{(1-x)^k}$ for the binomial coefficients with fixed $k$. See [[Binomial and multinomial coefficients]] and [[Set Partitions]] for some examples. 
## More examples
See also [[Catalan Numbers]], [[Integer Partitions]], [[Cycles and Inversions in Permutations]].

## Combinatorial interpretation of products of ogfs
Say we have two ogfs $A(x) = \sum_n a_nx^n$ and $B(x) = \sum_n b_nx^n$, and that the sequences $a_n$ and $b_n$ have some combinatorial meaning, i.e. that $a_n$ counts some family of combinatorial objects indexed by a parameter n, or the number of ways to "build" some "structure" with elements from an n-element set, and the same for $b_n$. Then the coefficient of $x^n$ in $A(x)B(x)$, $\sum_{i=0}^n a_ib_{n-i}$, has a combinatorial interpretation too--it is the number of ways to split $[n]$ into two (possibly empty) intervals, 1 through i and i+1 through n, build a structure of type A with the first interval, and build a structure of type B with the second. 

Note the use of intervals here--for any n and i, we consider only one way of splitting $[n]$ into a set of size i and a set of size n-i. This contrasts with the product of [[Exponential generating functions]],  where we pick arbitrary subsets of sets i and n-i. The distinction here can be thought of as corresponding to a distinction between counting "unlabeled" and "labeled" structures. When we build an unlabeled structure on a set, the elements of the set don't matter, only the number of elements. Thus when splitting $[n]$ into two sets in order to build unlabeled structures on them, we want to ignore all the possible ways to do so and focus only on the different cardinalities that the sets in the pair can have. One way to do this is, for each pair of cardinalities (i and n-i) come up with a single "canonical" way of dividing n into sets with those sizes, and the division into intervals works for that.

See [[Catalan Numbers]] for an example of the combinatorial use of the product rule. 
## Combinatorial interpretation of compositions of ogfs

## Ogfs of some common sequences



