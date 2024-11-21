## Multiplication and Addition Principles
Let A and B be disjoint sets; then $|A \cup B| = |A| + |B|$. Proof: just count the elements. Note that this only applies for disjoint sets, for which just adding the cardinalities doesn't double-count any elements. For unions of sets more generally, the inclusion-exclusion principle is needed.

Let A and B be arbitrary sets; then |A x B| = |A||B|. Proof: arrange the elements of |A x B| in a table in the obvious way; this will have |A| rows and |B| columns, for |A||B| elements total.

## Permutations: Ordered, No Repetition
A *permutation* of a set can be defined as a linear ordering of the elements of the set: so, e.g., the permutations of the set $\{a, b, c\}$ are abc, acb, bac, bca, cab, cba. The number of permutations of an n-element set is n!: there are n choices for the first element of a permuation, n-1 for the second, and so on, for a total of $n(n-1)...(2)(1) = n!$ permutations. In the case where, instead of finding permuations of the whole set, one wants to find all the permutations of only k elements with $k \leq n$, then there are $n(n-1)...(n - k + 1) = n! / (n - k)!$ such "k-permutations". 

## Lists: Ordered, With Repetition

## Subsets: Unordered, No Repetition

When working with subsets, where order doesn't matter, the rules are of course a bit different from those for lists. Suppose we want to find the number of k-element subsets of an n-element set. We might start out by listing all of the k-permutations of that subset, of which there are n! / (n-k)!. However, these permutations include the same subsets repeated many times, with the only difference being the arrangement of the elements, which of course doesn't matter for sets. In particular, for each k-element subset, our list of k-permutations includes all possible permutations of that subset: in other words, for every subset, it includes k! permutations of that subset. This means that the number of k-permutations is equal to k! multiplied by the number of subsets. So, to find the number of subsets, we must divide the number of k-permutations by k!, getting $\frac{n!}{k!(n-k)!}$. Numbers of this form, denoted $\binom{n}{k}$ or "n choose k", are the [binomial coefficients](Binomial%20and%20multinomial%20coefficients.md). N.B. the notation $\binom{S}{k}$ where S is a set is sometimes to denote the set of all subsets of S of size k.

## Permuting a Multiset: Ordered, Limited Repetition


## Choosing a Multiset from a Set: Unordered, Unlimited Repetition
Say we have a set of n elements $\{a_1, ... a_n\}$ and we wish to create a multiset of size k from it, in the sense that, when constructing the multiset, we can choose elements from the set repeated as many times as we'd like (subject, of course, to the restriction that we end up with k things total). For instance, one situation in which this might come up is sampling with replacement, e.g. if a lottery draws k integers from $[n]$, allowing repetition but not taking into account the order in which the numbers are drawn, how many tickets are possible?

First note that this problem can be reduced to counting solutions to a Diophantine equation; if $b_i$ is the multiplicity of $a_i$ in the multiset we choose, then $b_1 + ... + b_n = k$, so the number of valid ways to assign multiplicities to the elements of the set (and thus the number of ways to create a multiset from the elements of the set) is just the number of nonnegative integer solutions to this equation. Furthermore, by the technique of "stars and bars", the number of solutions to this is equal to the number of ways to place k "stars" and n - 1 "bars" among a total of n + k - 1 "slots", i.e. equal to $\binom{n + k - 1}{k}$. These numbers are sometimes called "n multichoose k" and denoted $(\binom{n}{k})$. 

For example, there are $\binom{3 + 2 - 1}{2} = \binom{4}{2} = 6$ ways to choose a 2-element multiset from $[3]$: $\{1, 1\}, \{1, 2\}, \{1, 3\}, \{2, 2\}, \{2, 3\}, \{3, 3\}$. The stars-and-bars encoding of each is $**||, *|*|, *||*, |**|, |*|*, ||**$. 

