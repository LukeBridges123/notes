# Definitions
## The Riemann Integral
We work with bounded functions $f: [a, b] \to \R$. The definite integral of a function $f$, $\int_a^b f(x)dx$, is defined as follows. We consider partitions of the interval: a finite sequence $P$ of points $x_0, \dots, x_n$ with $x_0 = a, x_n = b$, and $x_i \leq x_{i+1}$ for all $i$. This divides $[a, b]$ into up to $n$ sub-intervals (up to, since we allow repeated points), with width $\Delta x_i = x_i - x_{i-1}$. Now we define the *upper* and *lower* sums; letting $M_i = \sup f(x)$ and $m_i = \inf f(x)$ for $x$ in $[x_{i-1}, x_i]$, we have the upper sum $u(P, f) = \sum_{i=1}^n M_i \Delta x$ and the lower sum $L(P, f) = \sum_{i = 1}^n m_i \Delta x_i$. Finally, we use these to define the upper and lower integrals: the upper integral $\overline{\int_a^b}f(x)dx$ is the infinimum, over all possible partitions of $[a, b]$, of $u(P, f)$, and the lower integral $\underline{\int_a^b}f(x)dx$ is the supremum, over all possible partitions, of $L(P, f)$. We hope, for sufficiently nice functions, that these will turn out to be the same. If so, we say that $f$ is Riemann integrable, and define $\int_a^b f(x)dx$ to be the upper integral (or the lower integral, since it's the same thing). 

## Riemann-Stieltjes Integral
Now we consider a generalization. Again take a partition $P$ of $[a, b]$, but now take a monotonically increasing bounded function $\alpha: [a, b] \to \R$ (the "weight" function). We define $\Delta \alpha_i$ to be $\alpha(x_i) - \alpha(x_{i-1})$ (the Riemann integral is when $\alpha$ is the identity function); upper sums $U(P, f, \alpha)$ are defined as $\sum_{i = 1}^n M_i \Delta \alpha_i$, and then lower sums, upper integrals $\overline{\int_a^b}f(x)d\alpha$, lower integrals, and integrability (when upper and lower integrals are equal) are defined analogously. 

# Properties of Upper and Lower Sums
The plan: we'll show that the lower sums get bigger and bigger, and the upper sums get smaller and smaller, as we chop up the interval more finely. Then we'll show that, in general, 

Given partitions $P, Q$ we say that $Q$ is a refinement of $P$ if $P \subseteq Q$, i.e. $Q$ contains all the dividing points of $P$ and potentially some more. Also, the union of $P$ and $Q$ is their "common refinement". 

We now have the following lemma: if $Q$ is a refinement of $P$ then we have an inequality for lower sums, $L(P, f, \alpha) \leq L(Q, f, \alpha)$, and for upper sums, $L(P, f, \alpha) \geq L(Q, f, \alpha)$. 

Proof: we do this sort of inductively. Say $Q = P \cup \{x'\}$ and say that $x_{i-1} \leq x' \leq x_i$ in $Q$. Let $w_1 = \inf_{[x_{i-1}, x']} f, w_2 = \inf_{[x', x_i]}, m = \inf_{[x_{i-1}, x_i]}f$. We must have $w_1, w_2 \geq m$. Now consider the difference $L(Q, f, \alpha) - L(P, f, \alpha)$. Everything going on outside of $[x_{i-1}, x_i]$ cancels out, so we're left with just $w_1(\alpha(x') - \alpha(x_{i-1})) + w_2(\alpha(x_i) - \alpha(x')) - m(\alpha(x_i) - \alpha(x_{i-1}))$. We can insert $-\alpha(x') + \alpha(x')$ into what's being multiplied by $m$ to get the equivalent expression $$w_1(\alpha(x') - \alpha(x_{i-1})) + w_2(\alpha(x_i) - \alpha(x')) - m(\alpha(x_i) - \alpha(x') + \alpha(x') - \alpha(x_{i-1}))  = $$$$(\alpha(x') - \alpha(x_{i-1}))(w_1 - m) + (\alpha(x_i) - \alpha(x'))(w_2 - m)$$ This is nonnegative since $w_1 \geq m, w_2 \geq m$ (hence those differences are nonnegative) and since $\alpha$ is monotonically increasing (hence the differences involving $\alpha$ are also nonnegative).

By repeatedly adding points to $P$ one at a time, we can get the same inequality for any refinement $Q$ of $P$. The inequality for upper sums is basically the same.

Another lemma: the lower integral is at most the upper integral. Proof: take partitions $P_1, P_2$ and take their common refinement $Q$. We have that $L(P_1) \leq L(Q) \leq U(Q) \leq U(P_2)$ (using the lemma above for the first and last inequalities, while the middle inequality follows directly from the definition of lower and upper sums). Thus we have $L(P_1, f, \alpha) \leq U(P_2, f, \alpha)$. This is true regardless of what we picked for $P_1$, so it is true for the supremum (over all partitions $P_1$) of the LHS. This is just the lower integral, so $\underline{\int}f d\alpha \leq U(P_2, f, \alpha)$. Then we can do the same thing with this new inequality, taking the infinimum over all partitions $P_2$ of the RHS, to get $\underline{\int} f d\alpha \leq \overline{\int} f d\alpha$, as desired. 

Now we get an alternate characterization of integrability for bounded functions, which will be useful for proving that continuous bounded functions are integrable. It is this: $f$ is integrable on $[a, b]$ if and only if, for all $\epsilon > 0$, there exists a partition $P$ with $U(P, f, \alpha) - L(P, f ,\alpha) < \epsilon$. In other words, we can make the upper and lower sums as close as we like by choosing the partition correctly. 

First we show that the new definition implies the old. We know $L(P, f, \alpha) \leq \underline{\int} f d\alpha \leq \overline{\int} f d\alpha \leq U(P, f, \alpha)$. If we can make $U$ arbitrarily close to $L$, then we can get the difference between the lower integral and upper integral arbitrarily small, i.e. the upper and lower integrals are epsilon-close for any epsilon, so they are just the same, and so $f$ is integrable on the old definition.

Now we go the other direction. Suppose $f$ is integrable on the old definition, and let $\epsilon > 0$. Then there exists a partition $P_1$ with $\int fd\alpha - L(P_1, f, \alpha) < \epsilon/2$, and similarly a partition $P_2$ with $U(P_2, f, \alpha) - \int fd\alpha < \epsilon/2$. (we drop the overlines and underlines because the upper and lower integral are the same here.) Letting $P$ be the common refinement of $P_1, P_2$ we have $U(P) \leq U(P_2) \leq \int f d\alpha + \epsilon/2 \leq L(P_1) + \epsilon \leq L(P) + \epsilon$. Thus $U(P) - L(P) \leq \epsilon$ as desired. 

Now we can use this new definition to prove that a continuous function $f$ on $[a, b]$ is Riemann integrable with respect to $\alpha$ on $[a, b]$. The key point here is that since $f$ is continuous on a compact set it is uniformly continuous there. 


# Fundamental Theorem of Calculus
## Part 1
Let $f$ be Riemann integrable on $[a, b]$, and define $F(x) = \int_a^x f(t)dt$ for $x \in [a, b]$; then $F$ is uniformly continuous on $[a, b]$, and if $f$ is continuous at $x_0 \in [a, b]$, then $F$ is differentiable at $x_0$, and $F'(x_0) = f(x_0)$. 

Proof. First we get uniform continuity of $F$. $f$ must be bounded to be integrable, so take $M$ with $|f(t)| \leq M$ on $[a, b]$. For any $x \leq y \in [a, b]$ we hen have $|F(x) - F(y)| = |\int_x^y f(t)dt| \leq M(y-x)$. Thus, given $\epsilon > 0$, setting $\delta = \epsilon/M$ implies that, if $|x - y| < \delta, |F(x) - F(y)| \leq M(\epsilon/m) = \epsilon$, so $F$ is uniformly continuous.

Now we handle the claim about points where $F$ is differentiable. Pick a point $x_0$ where $f$ is continuous, let $\epsilon > 0$, and pick $\delta > 0$ such that $|x - x_0| < \delta$ implies $|f(x) - f(x_0)| < \epsilon$ (guaranteed to exist by continuity). 

## Part 2
If $f$ is Riemann integrable on $[a, b]$, and if there is a differentiable function $F$ on $[a, b]$ with $F' = f$, then $\int_a^b f(x)dx = F(b) - F(a)$. 

Proof: let $\epsilon > 0$; since $f$ is integrable there exists a partition $P = x_0, \dots, x_n$ with $U(P, f) - L(P, f) < \epsilon$. By the Mean Value Theorem, on each $[x_{i-1}, x_i]$ there exists some $t_i$ with $\frac{F(x_i) - F(x_{i-1})}{x_i - x_{i-1}} = F'(t_i) = f(t_i)$ or $F(x_i) - F(x_{i-1}) = \Delta x_if(t_i)$. Thus the sum $\sum_i f(t_i) \Delta x_i = \sum_i (F(x_i) - F(x_{i-1}))$, which telescopes, leaving $F(b) - F(a)$. This is neither the upper nor lower sum, but it is between them. Thus for any partition $P$, $F(b) - F(a)$ is squeezed between the lower and upper sum, and is therefore equal to their common limit as we refine the partitions, and so $\int_a^b f(x)dx = F(b) - F(a)$. 

## Applying to Stieltjes Integrals
If $\alpha$ is monotonically increasing and differentiable with a Riemann-integrable derivative on $[a, b]$, and $f$ is bounded on $[a, b]$, then $f$ is integrable with respect to $\alpha$ if and only if $f\alpha'$ is Riemann integrable. If it is integrable, we have $\int_a^b fd\alpha = \int_a^b f(x)\alpha'(x)dx$. 

