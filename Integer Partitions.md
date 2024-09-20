## Definitions
A partition of n is a way of writing n as a sum of positive integers; more formally, it is a multiset whose elements sum to n. Note in particular that the order of the summands doesn't matter, distinguishing it from compositions of n, but it's standard to write the summands in weakly descending order (each term greater than or equal to the next one). The set of all partitions of n is denoted P(n), while the number of partitions is p(n). E.g. 3 + 1 + 1 is a partition of 5 which is considered "the same" as 1 + 3 + 1. Also let $P_k(n)$ and $p_k(n)$ be the set of all partitions of n into k parts; $P_{\leq k}(n)$ is the set of partitions into at most k parts. 
## Young/Ferrers Diagrams
We can represent the partition 3 + 1 + 1 like so:
ooo
o
o
This is a "Young diagram" for that partition; each summand k is represented as a row of k blocks or dots, and the rows are arranged one on top of the other in weakly decreasing order. We can take the conjugate or transpose of a diagram, interchanging rows with columns to get another partition of n. E.g. the conjugate of 4 + 2 + 1:
o o o o
o o
o
is 3 + 2 + 1 + 1:
o o o
o o
o 
o
Some partitions, like 3 + 1 + 1, are "self-conjugate", equal to their own transpose. 

As a point of notation, let a partition of n $\lambda = (\lambda_1, \lambda_2, ... \lambda_k)$, and let $\lambda^t = (\lambda_1^t, \lambda_2^t, ... \lambda_m^t)$ be its transpose. In general we can say that $\lambda_1^t$ is the number of summands in $\lambda$ which are at least 1, $\lambda_2^t$ is the number which are at least 2, and so on. E.g. 4 + 2 + 1 has 3 summands in total, 2 which are at least 2, 1 which is at least 3, and 1 which is at least 4, hence its conjugate is 3 + 2 + 1 + 1.

Young diagrams can be used to provide bijective proofs of identities involving partitions; for instance:
### Number of partitions with at most k parts = number of partitions into parts which are at most k
Proof: take conjugates. The conjugate of a partition with at most k parts is a partition whose largest element is at most k. 
## Partitions with Generating Functions
### Finding the Generating Function
First, consider the more restricted problem of finding the ogf of the number of partitions of n into parts of size at most k. This turns out to be $\prod_{i=1}^k \frac{1}{1-x^i}$. Proof: each of those factors expands out to $(1 + x^i + x^{2i} + \dots)$ so we have $(1 + x + x^2 + \dots)(1 + x^2 + x^4 + \dots)\cdots(1 + x^k + x^{2k} + \dots)$. To form a term in the overall sum, we pick a term from each of the factors and multiply them out. The exponent on the result will be the sum of the exponents of the component terms. So each individual $x^n$ term will be obtained by picking a term from the first factor (say $x^{j_1}$), a term from the second factor (say $x^{2j_2}$), and so on, such that $j_1 + 2j_2 + \dots + kj_k$ add up to $n$. There is a clear bijection between tuples of natural numbers $j_1, \dots, j_k$ with this property and partitions of $n$ into parts of size at most $k$ (namely, just associate such a tuple with a partition of $n$ into $j_1$ ones, $j_2$ twos, and so on). Thus the number of $x^n$ terms, and so the coefficient on $x^n$, will be the number of partitions into at most $k$ parts. 

The result works just as well as a generating function for the number of partitions of $n$ into at most $k$ parts, by the identity above.

This extends into a generating function for the number of all partitions of $n$, namely $\prod_{i \geq 1} \frac{1}{1-x^i}$. (In this case, the whole process of picking a term from each factor must involve picking terms that aren't 1 from only finitely many of the factors.)

### Partitions into Odd Parts = Partitions into Distinct Parts
The generating function for the number of partitions of $n$ into odd parts, using the reasoning above, is $$\prod_{i \geq 1} \frac{1}{1 - x^i}$$ where the product is taken only over odd $i$. As for partitions of $n$ into distinct parts, it is $$\prod_{i \geq 1}(1 + x^i)$$The idea being that, when picking sequences $j_1, j_2, \dots$ where $j_1 + 2j_2 + \dots$ adds to $n$, the condition that all the parts of the partition are distinct corresponds to the condition that each $j_i$ is 0 or 1, hence only $x^0$ and $x^i$ can show up in the $i$th factor. The second ogf can be made to look much more like the first using the identity $(1 + x^i)(1 - x^i) = (1 - x^{2i})$, which allows turning it into $$\prod_{i \geq 1}\frac{1-x^{2i}}{1-x^i}$$ The terms in the denominator with even $i$ are all cancelled by terms in the numerator and vice versa, so we are left with just $\prod_{i \geq 1}\frac{1}{1 - x^i}$ where the product is taken over odd $i$ only--exactly the same as the ogf for partitions into odd parts. Hence the generating functions for partitions into odd parts and partitions into distinct parts are the same, so the sequences must be equal; thus the number of partitions of $n$ into odd parts equals the number of partitions of $n$ into even parts.
