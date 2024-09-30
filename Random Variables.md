$\newcommand{\var}{\operatorname{Var}}$ 
# Statistics of Random Variables
## Expected Value
The expected value, or mean, of a discrete random variable $X$ with probability mass function $p$ is defined as $E(X) = \sum_x xp(x)$, with the sum taken over all possible values $x$ that $X$ can take. Similarly, for a continuous variable with pdf $p$, we have $E(X) = \int p(x)dx$. Heuristically, if you draw from a random variable $N$ times, the expected value is what the mean of those sampled values will tend towards as $N$ gets larger. 

The most important fact about the expected value is that it is linear: $E(aX) = aE(X)$ and $E(X + Y) = E(X) + E(Y)$, for any $X, Y$--regardless of independence. The first follows immediately from the definition of $E(X)$. As for the second, can argue for it from the heuristic idea of what the expectation is like. If we draw from $X + Y$ a total of $N$ times, the mean of these samples is $\frac{1}{N}\sum_{i=1}^N x_i + y_i = (\frac{1}{N}\sum_i x^i)+\frac{1}{N}(\sum_i y^i)$. For large $N$ those terms will tend towards $E(X)$ and $Y(X)$. Since $E(X + Y)$ is, intuitively, the large-$N$ limit of the left-hand side, and it is equal to the large-$N$ limit of the right-hand side, we have $E(X+Y) + E(X) + E(Y)$. We can also prove this formally from the definition of expectation. We have $E(X+Y) = \sum_{i, j} (x_i + y_j)p(x_i \cap y_j) = \sum_{i, j} x_ip(x_i \cap y_j) + \sum_{i, j}y_j p(x_i \cap y_j)$. The first term is equal to $\sum_i x_i \sum_j p(x_i \cap y_j)$, but that inner sum is equal to $p(x_i)$, hence we get $\sum_i x_i p(x_i) = E(X)$. By much the same argument the second term is equal to $E(Y)$. Thus $E(X+Y) = E(X) + E(Y)$. The case of continuous random variables can be proven similarly. 

We can identify a constant $b$ with the random variable which always takes the value $b$, and can thus identify the random variable $X + b$, given by $p(X + b = a + b) = p(X = a)$, with the sum of the random variables $X$ and $b$. We then have $E(X + b) = E(X) + E(b) = E(X) + b$. Thus "translating" a random variable "translates" the expectation. As a special case of this, letting $E(X) = \mu_X$, we have that $X - \mu_X$ "has the same shape as $X$, but with a mean of $0$", since $E(X - \mu_X) = E(X) - \mu_X = \mu_X - \mu_X = 0$. 

More generally, for any finite set of random variables, $E(X_1 + \dots + X_n) = E(X_1) + \dots + E(X_n)$. As a special case of this, when the $X_i$ are independent and identically distributed, we have $E(X_1+ \dots + X_n) = nE(X_1)$. 

When $X, Y$ are independent, we have $E(XY) = E(X)E(Y)$. This is because $E(XY) = \sum_{i, j}x_iy_jp(x_i \cap y_j) = \sum_{i, j} x_iy_j p(x_i)p(y_j)$, by the independence of $X$ and $Y$. This is then equal to $(\sum_i x_ip(x_i))(\sum_j y_j p(y_j)) = E(X)E(Y)$. 

## Variance
If $X$ is a random variable with $E(X) = \mu$, then the variance of $X$, denoted $\sigma_X^2$ or $\var(X)$, is defined as $E((X - \mu)^2)$--the mean squared deviation from the mean. 

If $X, Y$ are independent, then $\var(X + Y) = \var(X) + \var(Y)$. To prove this, let $\mu_X, \mu_Y$ be the expectations of $X$ and $Y$. Since $E(X+Y) = \mu_X + \mu_Y$, we have $\var(X+Y) = E((X + Y - \mu_X - \mu_Y)^2)$. This is then equal to $E(((X - \mu_X) + (Y - \mu_Y))^2) = E((X - \mu_X)^2 + 2(X - \mu_X)(Y - \mu_Y) + (Y - \mu_Y)^2)$ By linearity this equals $E((X - \mu_X)^2) + 2E((X - \mu_X)(Y - \mu_Y)) + E((Y - \mu_Y)^2) = \var(X) + \var(Y) + 2E((X - \mu_X)(Y - \mu_Y))$ Since $X, Y$ are independent, so are $X - \mu_X$ and $Y - \mu_Y$, so that last term is equal to $2E(X - \mu_X)E(Y - \mu_Y) = 2(E(X) - \mu_X)(E(Y) - \mu_Y) = 0$. Thus the last term drops out and we have just $\var(X+Y) = \var(X)+\var(Y)$.  Once again, this generalizes to sums of many random variables. If $X_1, \dots, X_n$ are all independent then $\var(X_1 + \dots + X_N) = \var(X_1) + \dots + \var(X_n)$. Similarly if they are independent and identically distributed then $\var(X_1 + \dots + X_n) = n\var(X_1)$. 

With the expected value, we have $E(aX + b) = aE(X) + b$; with the variance, we have simply $\var(aX + b) = a^2 \var(X)$. The rule $\var(aX) = a^2 \var(X)$ follows by the following calculation: by definition $\var(aX) = E((aX - E(aX))^2)$; letting $\mu = E(X)$, we have $E(aX) = aE(X) = a\mu$; thus $\var(aX) = E((aX - a\mu)^2) = E(a^2(X - \mu)^2) = a^2 E((X - \mu)^2) = a^2 \var(X)$. Similarly, since $E(X + b) = E(X) + b$, we have $\var(X + b) = E(((X + b) - (\mu + b))^2) = E((X - \mu)^2) = \var(X)$. 

It is sometimes more convenient to use the following identity for the variance: $\var(X) = E(X^2) - \mu^2$. To prove this, we have $\var(X) = E((X - \mu)^2) = E(X^2 - 2\mu X + \mu^2) = E(X^2) - 2\mu E(X) + \mu^2$; then, since $E(X) = \mu$, that middle term is equal to $-2\mu^2$, so we get $\var(X) = E(X^2) - 2\mu^2 + \mu^2 = E(X^2) - \mu^2$. 

The variance of a biased coin--a random variable that equals $1$ with probability $p$ and $0$ with probability $1-p$--is $p(1-p)$. This can be calculated from the identity above. We know that, in this case, $\mu = p(1) + (1-p)(0) = p$, so $\mu^2 = p^2$. We also have $X^2 = X$, because $1^2 = 1$ and $0^2 = 0$, so $E(X^2) = E(X) = p$. Thus $\var(X) = p - p^2 = p(1 - p)$. 
## Standard Deviation
The standard deviation of $X$, denoted $\sigma_X$, is defined to be the square root of the variance. All the identities for the variance translate immediately into identities for the standard deviation. 

For independent variables $X_1, \dots, X_n$, letting $X = X_1 + \dots + X_n$, we have $\sigma^2_X = \sigma^2_{X_1} + \dots + \sigma^2_{X_n}$, so $\sigma_X = \sqrt{\sigma^2_{X_1} + \dots + \sigma^2_{X_n}}$. In the special case where the $X_1$ are i.i.d we have $\sigma_X = \sqrt(n \sigma^2_{X_1}) = \sqrt{n}\sigma_{X_1}$. Similarly, since $\var(aX + b) = a^2 \var(X)$, we have $\sigma_{aX + b} = a\sigma_X$. 

# Sampling From Random Variables
## The Distribution of Sample Means

## The Distribution of Sample Variances
### Bessel's Correction
### Sample Standard Deviations
