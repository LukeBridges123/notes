$\newcommand{\C}{\mathbb{C}}$
$\newcommand{\R}{\mathbb{R}}$
# Trigonometric Polynomials and Trigonometric Series
Power series are to polynomials what Fourier series are to trigonometric polynomials, so we start there. A trigonometric polynomial is a function of the form $g(x) = \sum_{-N}^N c_me^{imx}$ . $g$ will be real-valued for all real $x$ if and only if $c_m = \ol{c_{-m}}$ for all $m$. This is a polynomial in powers of $e^{ix}$, which is $\cos\theta + i\sin\theta$. We can also write this as $a_0 + \sum_{n=1}^N a_n\cos(nx) + b_n\sin(nx)$.  

Take $k \in -N, \dots, N$, and consider the integral $\frac{1}{2\pi} \int_{-\pi}^{\pi} \sum_{-N}^N g(x)e^{-ikx}$. (Note that, when integrating a function $\R \to \C$, we just integrate the real and complex parts separately and add them together.) This is equal to $\frac{1}{2\pi}\sum_{-N}^N c_m \int_{-\pi}^\pi e^{imx}e^{-ikx}$. When $m = k$ that integral is equal to $\int_{-\pi}^\pi dx = 2\pi$. Otherwise we get $\int_{-\pi}^\pi e^{i(m - k)x}$; the antiderivative of this is also of the form $e^{inx}$ for some $n$, and so is periodic, with in particular $e^{in\pi} = e^{-in\pi}$, so that integral is just $0$. Thus everything except the $2\pi$ from the $e^{ikx}e^{-ikx}$ term, and so the integral of the whole sum is $c_m\frac{2\pi}{2\pi} = c_m$. Thus integrating a trigonometric polynomial against an exponential lets you recover the coefficient of that exponential in the polynomial. 

Now let $f$ be an integrable function with period $2\pi$. The Fourier series of $f$ is $\sum_{n = -\infty}^{\infty}c_ne^{inx}$, where the coefficients $c_n$ are equal to $\frac{1}{2\pi}\int_{-\pi}^{\pi} f(x)e^{-inx}dx$. Alternatively we can define $a_0 = \frac{1}{2\pi} \int_{-\pi}^\pi f(x)dx$, and for $n \geq 1$, define $a_n = \frac{1}{\pi} \int_{-\pi}^\pi f(x)\cos(nx)dx$, and $b_n$ is the same but with $\sin(nx)$. Then the Fourier series of $f$ is $a_0 + \sum_{n=1}^\infty a_n\cos(nx) + b_n\sin(nx)$. 

# Fourier Series and Orthogonality
The trigonometric polynomials of "degree" at most $N$ form a finite-dimensional complex vector space, where $\langle f, g \rangle = \int_{-\pi}^\pi f(x)\ol{g(x)}dx$ is an inner product. There, the normalized "monomials" $\frac{1}{2\pi}e^{inx}$ where $-N \leq n \leq N$ form an orthonormal basis, as $\langle e^{inx}, e^{inx} \rangle = \frac{1}{2\pi} \int_{-\pi}^\pi e^{inx}e^{-inx} = \frac{2\pi}{2\pi} = 1$, and we calculated earlier that when $n \neq m$, $\langle e^{inx}, e^{imx} \rangle = 0$. Then the formula for the coefficient on $e^{imx}$ is just a version of the fact that, for any orthonormal basis $e_1, \dots, e_n$, we have $v = \langle e_1, v \rangle e_1 + \dots + \langle e_n, v \rangle e_n$. 

.....

## Mean-Square Approximation and Bessel's inequality
A first hint as to why Fourier series are useful is that the partial sums of the Fourier series of $f$ are, in a certain sense, the "best" approximation of the $f$.

More formally: let $\phi_1, \phi_2 \dots,$ be an orthonormal system on $[a, b]$ and let $s_n(x) = \sum_{1}^n c_m \phi_m(x)$ where $c_m$ is the $m$th Fourier coefficient for the orthonormal system $\phi_m$. Consider also $t_n(x) = \sum_1^n \gamma_m \phi_m(x)$ where $\gamma_m$ is some arbitrary real number. Then for any choice of $t_n$, $\int_a^b |f - s_n|^2 \leq \int_a^b |f - t_n|^2$. This says essentially that, regardless of whether the approximation in this orthonormal system is "good" in an absolute sense, it will at least be the best approximation using that orthonormal system, where we measure "best" in terms of square deviation from $f$. 

As a corollary we have Bessel's inequality, that $\sum_{n=1}^\infty |c_n|^2 \leq \int_a^b |f(x)|^2$. 

Proof of the first part: omitting the limits of integration, consider $\int f \ol{t_n} = \int f \sum_1^n \ol{\gamma_m} \ol{\phi_m}(x)$. Interchanging the sum and integral we get $\sum \ol{\gamma_m} \int f \ol{\gamma_m}(x)$. But each of those integrals is just $c_m$, so we get $\sum_{m=1}^n \ol{\gamma_m}c_m$.

Now consider $\int |t_n^2| = \int t_n\ol{t_n}= \int \sum_{m=1}^n \gamma_m \phi_m(x) \sum_{k=1}^n \ol{\gamma_k}\ol{\phi_k}$. Each term in that product of sums will have a $\phi_m$ and a $\ol{\phi_k}$; the integral of that is $1$ if $m=k$ and $0$ otherwise, so we the integral as a whole is just $\sum_{m=1}^n \gamma_m \ol{\gamma_m}$. 

We can now look at the integral $\int |f - t_n|^2 = \int (f - t_n)(\ol{f - t_n}) = \int f\ol{f}-  \int f\ol{t_n} + \int \ol{f}t_n + \int |t_n|^2$.  The first term is $\int |f|^2$, the second is $\sum \ol{\gamma_m}c_m$, the third is $\sum \gamma_m \ol{c_m}$, and the fourth is $\sum \gamma_m \ol{\gamma_m}$. We claim that in fact this equals $\int |f|^2 + \sum |\gamma_m - c_m|^2 - \sum |c_m|^2$. That middle term is $\sum (\gamma_m - c_m)(\ol{\gamma_m} - \ol{c_m})$: if we expand that out we get the last three terms of the four above, plus an extra $\sum |c_m|^2$ which we subtract out. Note that this whole thing is minimized when $\gamma_m = c_m$ for all $m$, since that's what causes the middle term to drop out. Thus $\int |f - s_n|^2 \leq \int |f - t_n|^2$ for all $t_n$, as desired. 

Proof of Bessel's inequality: let $\gamma_m = c_m$ in $\int |f - t_n|^2 = \int |f|^2 + \sum |\gamma_m - c_m|^2 - \sum |c_m|^2$ and rearrange. Then we get $\int |f - s_n|^2 = \int |f|^2 - \sum |c_m|^2$ or $\sum c_m = \int |f|^2 - \int |f - s_n|^2 \leq \int |f|^2$. 

# The Dirichlet Kernel
Define the $n$th "Dirichlet kernel" $D_n(x)$ to be $\sum_{n=-N}^N e^{-inx} = e^{-iNx} + e^{-i(N-1)x} + \dots + e^{i(N-1)x} + e^{iNx}$. Note that if we take $(e^{ix} - 1)D_n(x)$ we get $e^{-i(N-1)x} +  e^{-i(N-2)x} + \dots + e^{iNx} + e^{i(N+1)x} - D_n(x) = e^{i(N+1)x} - e^{-iNx}$, as all the middle terms cancel. Thus $D_n(x) = \frac{e^{i(N+1)x} - e^{-iNx}}{e^{ix} -1}$. Alternatively, multiplying both sides of $(e^{ix} - 1)D_n(x) = e^{i(N+1)x} - e^{-iNx}$ by $e^{-ix/2}$ we get $(e^{ix/2} - e^{-ix/2})D_n(x) = e^{i(N+1/2)x} - e^{-i(N + 1/2)x}$. Note that the LHS is $2i\sin(x/2)D_n$ and the RHS is $2i\sin((N+1/2)x)$, so in fact $D_n(x) = \frac{\sin(N + 1/2)x}{\sin(x/2)}$. 

Now we go back to Fourier series for $2\pi$-periodic functions; the partial sums $s_n(x)$ are $\sum_{-N}^N c_n \frac{e^{inx}}{\sqrt{2\pi}}$ and the $c_n$ are $\int_{-\pi}^\pi f(t)e^{int}/\sqrt{2\pi}$. Interchanging the sum and integral we get $\frac{1}{2\pi}\sum_{-N}^N \int_{-\pi}^\pi f(t)e^{in(x - t)} dt$ We can interchange the sum and integral again: $\frac{1}{2\pi}\int_{-\pi}^\pi f(t) \sum_{-N}^N e^{in(x-t)}dt$. But that sum inside the integral is $D_n(x-t)$, so in fact the $n$th partial sum of the Fourier series is $\frac{1}{2\pi}\int_{-\pi}^\pi f(t)D_n(x-t)dt$. This is a convolution of $f$ and $D_n$. We can also make a change of variables to get $\frac{1}{2\pi} \int_{-\pi}^\pi f(x - t)D_n(t)dt$, which is sometimes simpler.  

# Lipschitz Condition and Pointwise Convergence
Here's one relatively straightforward condition for a function's Fourier series to converge to it: let $f$ be a $2\pi$-periodic satisfying the "Lipschitz condition", aka Lipschitz continuity:

there exists $M$, $\delta$ such that, for all $t \in (-\delta, \delta)$ we have $\frac{|f(x + t) - f(x)|}{|t|} \leq M$ 

Note that differentiability implies the Lipschitz condition, which in turn implies uniform continuity (and so continuity and integrability). 

Then $\lim_{N \to \infty} s_N(f, x) = f(x)$ for all $x \in \R$, i.e. the partial sums converge pointwise. 

Proof: first we need to find the integral $\int_{-\pi}^\pi D_n(x)dx = \int_{-\pi}^\pi \sum e^{inx}$. The integral of each of those terms for nonzero $n$ is $0$, while for $n = 0$ it's $2\pi$, so the original integral is $2\pi$. 

Now we go back to the quantity we hope will converge to $0$: $s_n(f, x) - f(x) = \frac{1}{2\pi} \int f(x - t)D_n(t)dt - f(x) = \frac{1}{2\pi} \int f(x - t)D_n(t)dt - \frac{1}{2\pi}\int f(x)D_n(t)dt$ (to rewrite $f$ as that integral, we just note that $f(x)$ can be pulled out of an integral which is being taken with respect to $t$, and once we do that, we're left with $\int D_n(t)dt = 2\pi$, and multiplying by $\frac{1}{2\pi}$ cancels that out). Thus $s_n - f = \frac{1}{2\pi} \int (f(x - t) - f(x))D_n(t)dt$. We will hopefully be able to control $f(x - t) - f(x)$ using Lipschitz continuity. Rewriting the Dirichlet kernel using its explicit formula we get $$\frac{1}{2\pi} \int \frac{f(x - t) - f(x)}{\sin(t / 2)}\sin((N + 1/2)t)dt$$ Call that fraction $g(t)$. Then we can rewrite the $\sin$ left over using trigonometric identities and expand out using linearity to get
$$\frac{1}{2\pi}\int g(t)\cos(t/2) \sin(Nt)dt + \frac{1}{2\pi}\int \sin(t/2) \cos(Nt)g(t)dt$$ Note that the integral on the right is the real part of the $n$th Fourier coefficient of $\sin(t/2)g(t) = f(x - t) - f(x)$. But Bessel's inequality implies that these Fourier coefficients go to $0$, since $f(x - t) - f(x)$ is square-integrable. So we've taken care of the second term and only have to handle the first. This is the imaginary part of the $n$th Fourier coefficient of $g(t)\cos(t/2)$. We can't directly interpret this in terms of a nice function like $f$, but we can show that it's bounded, hence square-integrable, hence we can repeat the same argument to show that it goes to $0$. This is where we really need the full strength of Lipschitz continuity, not just the fact that it implies continuity etc. We have $|g(t)\cos(t/2)| \leq \frac{|f(x - t) - f(x)|}{|\sin(t/2)|} \leq \frac{M|t|}{\sin(t/2)} \leq C$ for some constant $C$ (related to $M$, and to the fact that $\frac{\sin(t)}{t} > \frac{1}{2})$ for $t$ near $0$. 

# Fejer's Theorem
Instead of considering the partial sums of the Fourier series, consider an "averaged" version: $\sigma_N(f, x) = \frac{1}{N+1}\sum_{n=0}^N s_n(f, x)$. Or, letting $K_n(x) = \frac{1}{N+1} \sum_{n=0}^N D_n(x)$ (the "average" of the Dirichlet kernels) we can rewrite this as $\sigma_N = \frac{1}{2\pi} \int_{-\pi}^\pi f(x - t)K_N(t)dt$. 

Then we have the following theorem: if $f$ has period $2\pi$ and is continuous on $\R$, then $\sigma_N(f, x)$ converges uniformly to $f$. We will later see a corollary of this, about approximating functions by trigonometric polynomials. 

Proof: since $f$ is continuous on $[-\pi, \pi]$ it is bounded and uniformly continuous. Let $M$ be such that $\sup |f| \leq M$ and let $\epsilon > 0$. Then we have $\delta$ such that $|f(x - t) - f(x)| < \epsilon$ for all $t$ with $|t| < \delta$. Now choose $N$ such that $\frac{1}{N+1} < \epsilon$. Now we look at the difference $|\sigma_N(x) - f(x)| \leq |\frac{1}{2\pi} \int_{-\pi}^\pi f(x - t)K_N(t)dt - \frac{1}{2\pi} \int_{-\pi}^\pi f(x)K_N(t)dt|$ (using the same "multiply by $1$ in a fancy way" trick, which works since $\frac{1}{2\pi} \int_{-\pi}^\pi K_N(t)dt = 1$). Then we have that the original difference is at most $\frac{1}{2\pi} \int_{-\pi}^\pi |f(x - t) - f(x)|K_N(t)dt$. Now we split this integral into 3 pieces: the integral of the same integrand for $t < -\delta$, for $t > \delta$, and for $|t| < \delta$. For the last one, we have that $|f(x - t) - f(x)| < \epsilon$, so 

# Parseval's Identity
Define the norm of a $2\pi$-periodic function to be $||f|| = (\frac{1}{2\pi} \int_{-\pi}^\pi|f(x)|^2dx)^{1/2}$. Let $f, g$ have Fourier coefficients $c_n, \gamma_n$. 
