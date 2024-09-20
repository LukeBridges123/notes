## Principle of Inclusion-Exclusion
Let $S$ be a set with $|S| = N$; also let $P = \{p_1, ... p_r\}$ be a set of properties, not necessarily possessed by any of the objects in $S$. Let $e_j$ be the number objects in $S$ which satisfy exactly $j$ properties from $P$. Finally, let $N(p_i)$ be the number of objects that satisfy property $p_i$, $N(p_ip_j)$ be the number of objects that satisfiy both $p_i$ and $p_j$, and so on; also have $N_0$ count the number of objects that satisfy none of the properties from $P$.  With all this terminology, the principle of inclusion-exclusion can be stated as follows: $N = N_0 + \sum_{i=1}N(p_i) - \sum_{i < j}N(p_ip_j) + \sum_{i < j < k}N(p_ip_jp_k) + ... + (-1)^{r+1}N(p_1...p_r)$.

Alternate notation: call the set of objects in $S$ which satisfy none of the properties $e_0$, and use $N_0$ to instead denote the total number of objects in $S$ (say, which satisfy at least 0 of the properties). For $\omega \in S$, let $P(\omega) \subseteq P$ denote the properties satisfied by $\omega$. As an additional bit of notation, let $N(\supseteq T)$ count the number of objects that have at least the properties in $T$. Then define $N_k = \sum_{|T| = k}N(\supseteq T)$, i.e. where $T$ ranges over all size-k subsets of $P$. (So, $N_k$ is the number of objects satisfying at least k properties, potentially counted multiple times according to how many sets of k properties they show up in.) Then $N_k = \sum_{|T| = k}\sum_{\omega \in S, T \subseteq P(\omega)} 1$, and the sum interchanges to $\sum_{\omega \in S}\sum_{|T| = k, T \subseteq P(\omega)}1$, which equals $\sum_{\omega \in S}\binom{|P(\omega)|}{k}$. Now let $e_j$ be the number of elements in $S$ that have exactly j properties. Suppose that $|P(\omega)| = j$; then $\omega$ contributes to $N_k$ $\binom{j}{k}$ times, meaning $N_k = \sum_{j \geq k}\binom{j}{k}e_j$. Now let $N(x) = \sum_k N_kx^k$; so $N(x)$ is the generating function of the sequence $N_0, N_1, ...$. By the previous, we know $N(x) = \sum_k\sum_j\binom{j}{k}e_jx^k$. We can interchange the order of summation to get $\sum_je_j\sum_k\binom{j}{k}x^k$ = $\sum_je_j(1+x)^j$. Letting $E(x)$ be the generating function $\sum_ke_kx^k$, we see that $N(x) = E(1+x)$, or $E(x) = N(x-1)$. Note that we have $e_0 = E(0) = N(-1) = \sum_kN_k(-1)^k$. And this is actually the statement of the principle of inclusion-exclusion. Note also that the general method here gives you a way of finding how many objects satisfy exactly 1, 2, etc. of the properties once you know how many satisfy at least 1, 2, etc. -- just plug (x-1) into $N(x)$, expand, and simplify. 

We can generalize: what is $e_k$ for arbitrary k? Naturally it must be $[x^k]E(x) = [x^k]N(x-1) = [x^k]\sum_jN_j(x-1)^j = \sum_jN_j[x^k](x-1)^j$ (that last step by the linearity of the extraction operator). Then using the binomial theorem this is $\sum_jN_j[x^k]\sum_i\binom{j}{i}(-1)^{j-k} = \sum_jN_j\binom{j}{k}(-1)^{j-k}$.  

## Applications
### Derangements
Let $S = S_n$ and let $p_i$ be the property that a permutation fixes i. For any i, we have $N(p_i) = (n-1)!$, $N(p_ip_j)$ = (n-2)!, and so on. By inclusion-exclusion, the number of derangements is then $n! - \sum_iN(p_i) + \sum_{i<j}N(p_ip_j) + ... + (-1)^nN(p_1p_2...p_n)$. For each one of those sub-sums (say one with k indices, representing k fixed points) there are $\binom{n}{k}$ ways to choose the indices, and $(n-k)!$ permutations per set of indices. So we get: $n! - (\binom{n}{1}(n-1)!) + (\binom{n}{2}(n-2)!) + ... + (-1)^n\binom{n}{n}(n-n)!$ = $\sum_k\binom{n}{k}(n-k)!$ = $\sum_{k = 0}^n \frac{n!}{k!(n-k)!}(n-k)!(-1)^k$ = $n!\sum_{k=0}^n\frac{(-1)^k}{k!}$. 

### Counting surjections + Stirling numbers of the second kind
We can prove an explicit formula for the Stirling numbers of the second kind: $m!S(n, m) = \sum_{k=0}^m\binom{m}{k}k^n(-1)^{n-k}$. Along the way, we also count the number of surjections between two finite sets (which also solves equivalent problems like counting the number of length-n words over an m-symbol alphabet where all symbols show up at least once in the word). Proof: consider surjections from $[n] -> [m]$.  We can first partition $[n]$ into m blocks to determine what the fibers of each element look like, then assign each block to an element of $[m]$ to determine which fibers go with which elements. There are $S(n, m)$ ways to choose the blocks and $m!$ ways to match up blocks with elements of $[m]$; this gives the LHS, $m!S(n, m)$. As for the RHS, let $S$ be the set of all functions $[n] -> [m]$; we need to sieve out the ones that aren't surjections. Let $p_i$ be the property that $i$ is not in the range of a given function. Using inclusion-exclusion, the number of surjections is then equal to $m^n - \sum_jN(p_j) + \sum_{j<k}N(p_jp_k) ... = m^n - \binom{m}{1}(m-1)^n + \binom{m}{2}(m-2)^n...$  = $\sum_k\binom{m}{k}(m-k)^n(-1)^k$, and by symmetry of the binomial coefficients this equals $\sum_k\binom{m}{m-k}(m-k)^n(-1)^k = \sum_k\binom{m}{k}k^n(-1)^{n-k}$. So $k!S(n, m) = \sum_{k=0}^m\binom{m}{k}k^n(-1)^{n-k}$, and dividing both sides by $k!$ turns this into a formula for the Stirling number $S(n, m)$. 
