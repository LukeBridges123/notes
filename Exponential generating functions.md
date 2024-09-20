## Wilf rules for egfs
All of the rules for manipulating ogfs have analogous rules for egfs; the main difference is that shifting sequences is done with differentiation and the product rule changes.
### Rule 1: Shifted Sequences
Given $A(x) = a_0 + a_1x + \frac{a_2}{2}x^2 + \frac{a_3}{6}x^3 + \dots$, we have $A'(x) = a_1 + a_2x + \frac{a_3}{2}x^2 + \dots$ so $A'(x)$ is the egf of $a_{n+1}$. This generalizes: the egf of $a_{n+k}$ is the kth derivative of $A(x)$, $D^k(A(x))$. So e.g. letting $F(x)$ be the egf of the Fibonacci numbers, it must satisfy the differential equation $F'' = F' + F$. 
### Rule 2: Polynomials in n
This rule carries over unchanged from its equivalent for ogfs: if $A(x)$ is the egf of $a_n$ and $p(n)$ is a polynomial in $n$, then the egf of $p(n)a_n$ is $p(xD)A(x)$. Note that this makes shifting by 1 and multiplying all terms by $n$ almost equivalent for egfs, the only difference being that multiplying terms by $n$ requires applying $xD$ instead of $D$. 
### Rule 3: Products of 2 egfs
Let $A(x) = \sum_n \frac{a_n}{n!}x^n, B(x) = \sum_n \frac{b_n}{n!}x^n$. Then the coefficient of $\frac{x^n}{n!}$ in $A(x)B(x)$ is $\sum_{k=0}^n \binom{n}{k} a_kb_{n-k}$. Proof: using the standard product rule for ogfs, we get that the coefficient of $x^n$ in $A(x)B(x)$ is $$\sum_{k=0}^n \frac{a_k}{k!}\frac{b_{n-k}}{(n-k)!}$$ Multiplying the numerator and denominator by $n!$ gets: $$\sum_{k=0}^n \frac{n!}{n!}\frac{a_k}{k!}\frac{b_{n-k}}{(n-k)!} = \frac{1}{n!}\sum_{k=0}^n \frac{n!}{k!(n-k)!}a_kb_{n-k} = \frac{1}{n!}\sum_{k=0}^n \binom{n}{k} a_kb_{n-k}$$ So $A(x)B(x) = \sum_n (\sum_{k=0}^n \binom{n}{k}a_kb_{n-k})\frac{x^n}{n!}$, and the coefficient on $x^n/n!$ is exactly as stated above. 
### Rule 4: Products of many egfs
Repeating the argument above for, say, $A(x)B(x)C(x)$ gets a coefficient of $$\sum_{i, j, k = n} \frac{n!}{i!j!k!}a_ib_jc_k = \sum_{i, j, k = n} \binom{n}{i, j, k}a_ib_jc_k$$ And so on for more egfs. So such products can be expected to contain multinomial, rather than binomial, coefficients.
### Rule 5: Partial sums
Exponential generating functions don't have a direct analogue to rule 5 for ogfs due to products working differently. The closest analogue is that the egf of $\sum_{k=0}^n \binom{n}{k} a_k$ is $A(x)e^x$. Such sums show up when working with, for instance, [[Cycles and Inversions in Permutations|derangements]] and [[Set Partitions|Bell numbers]], as well as the [[Inversion Formulas in Combinatorics|binomial inversion]] formula.
## Recurrences with egfs
### Linear Recurrences
