Lucas numbers = Fibonacci numbers with initial conditions $L_0 = 2, L_1 = 1$. 

Original Fibonacci polynomials sequence: $F_n(x) = xF_{n-1}(x) + F_{n-2}(x), F_0 = 1, F_1 = x$. E.g. $F_2(x) = x^2 + 1$. Setting x = 1 gets the Fibonacci numbers. Generalized version of the Binet formula exists. Zeros (all complex) have an exact expression in terms of cos. Generalizations: try different initial conditions, or replace $xF_{n-1}$ with $x^kF_{n-1}$ for some fixed k. E.g. $G_n(x) = x^kG_{n-1}(x) + G_{n-2}(x), G_0 = -1, G_1 = x-1$. Again x = 1 gets Fibonacci numbers. Irrational roots, no known closed form. We do know that, when k = 1, maximum roots of $G_n$ converge to 3/2 as n gets large. At k = 2, converge to $\sqrt{2}$. Looking for general form of convergence of maximum roots. That is, for k >= 3, max roots converge to roots of a polynomial of a known form. 

Possible research questions: find asymptotic (or closed-form) results on roots of sequences defined by similar recurrrences; roots of derivatives and integrals of the polynomials; 

Alternate generalization: add together previous j terms instead of just the last two terms. For the Fibonacci numbers generalized in this way, we get characteristic polynomials with real roots that follow an apparent pattern (one near 2, one near -1). Indeed they do converge to 2 and -1. This is for even degree--odd degree has only one real root. We can also find explicit forms for the rest when we divide by (x - r_1)(x-r_2) where r_1, r_2 are the roots. Finding these explicit forms leads to some combinatorial identities, provable by computer (see WZ algorithm).

Evaluating $F_n(x)$ at $x = 2, 4, 6, 8, 10$: gives denominators of convergents of continued fractions to $\sqrt{2}, \sqrt{5}, \sqrt{10}, \sqrt{17}, \sqrt{26}$ respectively. Conjecture: this is true in general: for even x, $F_n(x)$ gives the denominators for $\sqrt{(\frac{x}{2})^2 + 1}$. Really this just rephrases the idea that the denominators follow the recurrence $d_{n+2} = xd_{n+1} + d_n$. 
## Min Roots of Zach Polynomials
Min roots of Zach polynomials:
0, 0, -1.00000000000000, -1.25992104989487, -1.44224957030741, -1.55113351807125, -1.62648314456429, -1.67886767135454, -1.71729005087941, -1.74607602713470, -1.76826241187848, -1.78568844831189, -1.79963234515200, -1.81095741433463, -1.82028121526710, -1.82804749500408, -1.83458460656037, -1.84013845004082, -1.84489660800428, -1.84900395169480, -1.85257388225269, -1.85569614403210, -1.85844252122871, -1.86087097372916, -1.86302871417529, -1.86495451060870, -1.86668043581012, -1.86823320734384, -1.86963522538617, -1.87090538319745, -1.87205970565228, -1.87311185615562, -1.87407354209839, -1.87495484138223, -1.87576446710239, -1.87650998341156, -1.87719798258954, -1.87783423108347, -1.87842379057952, -1.87897111886667, -1.87948015425658, -1.87995438655261, -1.88039691696223, -1.88081050887809, -1.88119763108397, -1.88156049464982, -1.88190108454759, -1.88222118683371, -1.88252241209452, -1.88280621573048, -1.88307391555695, -1.88332670711963, -1.88356567705758, -1.88379181479315, -1.88400602278393, -1.88420912553536, -1.88440187754238, -1.88458497030295, -1.88475903852551, -1.88492466563446, -1.88508238866287, -1.88523270260930, -1.88537606432458, -1.88551289598577, -1.88564358820655, -1.88576850282694, -1.88588797541956, -1.88600231754492, -1.88611181878389, -1.88621674857242, -1.88631735785996, -1.88641388061078, -1.88650653516498, -1.88659552547395, -1.88668104222332, -1.88676326385501, -1.88684235749861, -1.88691847982108, -1.88699177780296, -1.88706238944821, -1.88713044443410, -1.88719606470688, -1.88725936502827, -1.88732045347751, -1.88737943191283, -1.88743639639625, -1.88749143758493, -1.88754464109197, -1.88759608781947, -1.88764585426621, -1.88769401281211, -1.88774063198155, -1.88778577668715, -1.88782950845586, -1.88787188563866, -1.88791296360526, -1.88795279492500, -1.88799142953517, -1.88802891489749, -1.88806529614399, -1.88810061621284, -1.88813491597513, -1.88816823435313, -1.88820060843070, -1.88823207355656, -1.88826266344080, -1.88829241024516, -1.88832134466761, -1.88834949602160, -1.88837689231025, -1.88840356029608, -1.88842952556635, -1.88845481259446, -1.88847944479761

Max roots: 
## Combinatorial Proof for Zach's Identity
Identity for Zach's polynomials $Z_n(x)$, where $Z_n(x)$ is defined by the recurrence $Z_{n} = xZ_{n-1} + Z_{n-3}$ with initial conditions $Z_0 = 1, Z_1 = x, Z_2 = x^2$. :

$Z_n(x) = \sum_k x^{n-3k}\binom{n-2k}{k}$. 
N.B. we consider x to be an integer at first, and then extend to all real values of x at the end. 

Both sides count the number of ways to tile a $1 \times n$ board with monominos (coming in x colors) and triominos (i.e. $1 \times 3$ tiles). First, we prove this for the LHS, or more precisely for the recurrence defining the LHS. For the initial conditions, we can tile the empty board in 1 way, the 1x1 board in x ways (choose one of x monomino colors), and the 1 x 2 board in x^2 ways (choose one color for each monomino). For the recurrence, given an n-square board, we can place a monomino at the start (x ways) and then cover the rest ($Z_{n-1}$ ways) for $xZ_{n-1}$ ways, or place a triomino at the start (1 way) and cover the rest ($Z_{n-3}$ ways). Summing these (disjoint, exhaustive) cases gets $Z_n = xZ_{n-1} + Z_{n-3}$. 

Now for the RHS. This counts the number of ways to tile the n-board, broken into cases based on the number of triominos. Suppose that we place k triominos. 

First, a lemma: there are $\binom{n-2k}{k}$ ways to tile a n-board with k triominos and n-3k (uncolored) monominos. Proof: consider a map that sends $1 \times n$ boards tiled with monominos and k triomonos to $1 \times (n - 2k)$ boards tiled with the numbers 1 and 3. So it works as follows (see picture). This map does have the set of $1 \times (n - 2k)$ boards as its codomain: the original board has 3k of its tiles filled with triominos and n - 3k filled with monominos; the new board has n-3k filled with 1s and k filled with 3s, for n - 3k + k = n - 2k tiles total. It also has an inverse in the obvious way (handwave handwave), and so is a bijection. Thus there are as many tilings of the n board with triomonos and monominos as there are tilings of the n - 2k board with 1s and 3s. There are $\binom{n-2k}{k}$ such tilings of the n - 2k board (choose k of the tiles to be 3s, and fill the rest with 1s), and so there are $\binom{n-2k}{k}$ tilings of the n-board with monominos and k triominos. 

Now, using the lemma: to tile the n-board with k triominos, we first choose where to place the triomonos and monominos: by the lemma, there are $\binom{n-2k}{k}$ ways to do this. Then we go over each of the $n - 3k$ monominos and assign them each a color: there are $x^{n - 3k}$ ways to do this. So there are $\binom{n-2k}{k}x^{n - 3k}$ ways to place k triominos on the n-board and fill the rest with monominos in x colors. Summing over all k (these being disjoint and exhaustive cases) gives the RHS. 

Thus the LHS and RHS count the same thing and so must be equal--at least for nonnegative integer values of x, which was implicitly assumed when talking about "x colors of monominos". But the fact that the identity holds for all integer values of x means that it must hold for all real values of x (since a polynomial of degree d is completely determined by its values at d+1 points, and we in fact know the values at infinitely many points). So the identity is valid in general. 


Generalization: let $r > 1$ be an integer. Take a sequence of polynomials defined by initial conditions $F_i = x^i$ for $0 \leq i \leq r - 1$ and the recurrence $F_n = xF_{n-1} + yF_{n - r}$. Then $F_n = \sum_k \binom{n - (r-1)k}{k}x^{n - rk}y^k$. As before, we prove this by showing that both the recurrence and the explicit formula count the number of ways to tile an n-board with monominos in x colors and "r-ominos" in y colors. For the recurrence, note that to tile a board, we can place 1 of x monominos at the start and then fill the remaining n-1 tiles, or place 1 of y r-ominos at the start and fill the remaining n-r tiles. For the explicit formula: as before, we can prove the lemma that there are $\binom{n-(r - 1)k}{k}$ ways to fill the board with k r-ominos and fill the rest with monominos; then once we've placed them, there are $x^{n - rk}y^k$ ways to assign colors to the monominos and r-ominos, and summing over all k gets the RHS. 

Letting $F_r(t)$ be the ogf of the sequence generated by $F_i = x^i$ for $0 \leq i \leq r - 1$ and $F_n = aF_{n-1} + bF_{n - r}$: $F_r(t) = \frac{1}{1 - at - bt^r}$. 

Generating function for basic general bivariate case (i.e. $M_n(x)$ where $M_0 = a, M_1 = bx + cy + d, M_n = xM_{n-1} + yM_{n-2}$): $\frac{(b - a)xt + cyt + dt + a}{1 - xt - yt^2}$ 

## More identities
$Z_{2n+1} = Z_nZ_{n+1} + Z_{n-1}^2 + Z_{n-2}Z_n$. Proof: consider tiling a 2n+1 board; split into cases based on whether a triomino overlaps between the first n and last n+1 squares, and if so, how it overlaps. 
## General 3-variable Fibonacci polynomials
Consider the sequence $F_n = xF_{n-1} + yF_{n-2} + zF_{n-3}$ with initial conditions $F_0 = 1, F_1 = x, F_2 = x^2 + y$. (These are equivalent to the initial conditions $F_0 = 1, F_i = 0$ for all $i < 1$.) 
Identity for the general 3-variable third-order case: $F_{n + m + 1} = xF_nF_m + yF_{n-1}F_m + yF_nF_{m-1} + zF_nF_{m-2} + zF_{n-1}F_{m-1} + zF_{n-2}F_m$ 
or $F_{n+m+1} = F_n(xF_m + yF_{m-1} + zF_{m-2}) + yF_{n-1}F_m + zF_{n-1}F_{m-1} + zF_{n-2}F_m$ which, applying the recurrence, becomes $F_{n+m+1} = F_nF_{m+1} + yF_{n-1}F_m + zF_{n-1}F_{m-1} + zF_{n-2}F_m$
$F_{2n+1} = xF_n^2 + 2yF_{n-1}F_n + 2zF_nF_{n-2} + zF_{n-1}^2$ 

"transition matrix" form of 3-variable case:
$A = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ z & y & x \end{bmatrix}$ 
This is the matrix of the linear map $\mathbb{R}^3 -> \mathbb{R}^3$ which sends $(a, b, c)$ to $(b, c, cx + by + az)$ and so sends $(F_n, F_{n+1}, F_{n+2})$ to $(F_{n+1}, F_{n+2}, F_{n+3})$. From this we can rederive the characteristic polynomial $-t^3 + xt^2 + yt + z$. N.B. result says that the numerical sequence generated by plugging (x, y, z) into $F_n$ converges (to 0) iff eigenvalues of the transition matrix all have magnitudes less than 1. 

Some decent bounds on x, y, and z for convergence: let $r_1, r_2, r_3$ be the eigenvalues; note that we have $\det A = z, \text{trace} A = x$, so $z = r_1r_2r_3$ and $x = r_1 + r_2 + r_3$. From this we can get some necessary (though not sufficient) conditions on $x$ and $z$ in order for convergence to happen: if $|r_i| < 1$ for all i then $|z| < 1$ and $|x| < 3$, since $|z| = |r_1r_2r_3| <= |r_1||r_2||r_3| < 1$ and $|x| = |r_1 + r_2 + r_3| <= |r_1| + |r_2| + |r_3| < 3$. Also, as can be seen by expanding $(t-r_1)(t-r_2)(t-r_3)$ and looking at the coefficient on the linear term, $y = -(r_1r_2 + r_2r_3 + r_1r_3)$. So $y < 3$ also. (N.B. this is using Vieta's formulas.)

Lagrange's upper bound on roots: for a polynomial $a_0 + a_1x + ... + a_nx^n$, the magnitudes of all roots are bounded by $\max{\{1, \sum_{i = 0}^{n-1}|\frac{a_i}{a_n}|}\}$. In particular for the char. poly. $t^3 - xt^2 - yt - z$, we have an upper bound of $\max\{{1,|x| + |y| + |z|\}}$. So if $|x| + |y| + |z| \leq 1$ then the roots will all be bounded above by 1 and so convergence will happen. In particular if $|x| < 1/3, |y| < 1/3, |z| < 1/3$ then we necessarily have convergence. 

## Ideas
New directions: matrix representations, roots (incl. bounds on both real and complex roots--note such-and-such theorem relating bounds to eigenvalues), identities, closed forms, looking at the coefficients, continued fraction representations, relations with other "special" polynomials, generating functions

Consider tiling other sorts of shapes (e.g. T shape)

For convergence of min roots of Zach polynomials:
Part 1: conjectures: $Z_n(x) \geq 0$ when $x \geq 0$ for all n, $Z_{2n}(x) > 0$ for $x < -3$, $Z_{2n+1} < 0$ for $x < - 3$. Prove this part using the reduction formulas. 

Part 2: prove $F_n(x)$ always has real root in $(-2, -1)$. Try e.g. proving $F_n(-1) \cdot F_n(-2) < 0$. 

Part 3: let $g_n$ be min real root of $F_n$. Prove $g_{2n}$ increases as n increases, $g_{2n+1}$ decreases. Then show $g_n$ is bounded. Bounded + monotonic (for the even and odd sequences respectively) implies there's a limit. Then, just need to prove that the limit is $-17/9$. 

## Max Roots of Zach Polynomials
### When the Zach Polynomials have a Root at Zero
For all $n$, $Z_{3n}$ is not divisible by $x$ (in particular, it has a remainder of 1 when divided by $x$), $Z_{3n+1}$ is divisible by $x$ but not by any higher power of $x$, $Z_{3n+2}$ is divisible by $x^2$ but not any higher power of $x$. 

Proof: by induction. Base cases $Z_0 = 1, Z_1 = x, Z_2 = x^2$ are obvious. For the inductive step, we break into 3 cases, each with a slightly different inductive hypothesis. 

0 mod 3 case: suppose the result holds for $Z_k$ for all $k < 3n$. Note that $Z_{3n} = xZ_{3n-1} + Z_{3n-3}$. By the inductive hypothesis, $Z_{3n-3}$ has a remainder of 1 when divided by $x$, so $Z_{3n-3} = xq(x) + 1$ for some polynomial $q$. So $Z_{3n} = x(Z_{3n-1} + q(x)) + 1$; thus $Z_{3n}$ has a nonzero remainder $1$ when divided by $x$ and so is not divisible by $x$. 

1 mod 3 case: suppose the result holds for $Z_k$ for all $k < 3n+1$. Note that $Z_{3n+1} = xZ_{3n} + Z_{3n-2}$. By the inductive hypothesis, $Z_{3n-2} = xq(x)$, since $3n - 2 \equiv 1 \pmod{3}$, so $Z_{3n+1} = x(Z_{3n} + q(x))$. Thus $Z_{3n+1}$ is divisible by $x$. For it to be divisible by a higher power of $x$, either $Z_{3n} + q(x)$ is the zero polynomial (impossible--these are of different degree), or $Z_{3n}$ and $q(x)$ are both divisible by $x$, but by the inductive hypothesis, $Z_{3n}$ is not divisible by $x$. 

2 mod 3 case: Proceeds in essentially the same way as the above case. Suppose the result holds for $Z_k$ for all $k < 3n+2$. We have $Z_{3n+2} = xZ_{3n+1} + Z_{3n - 1}$. By the inductive hypothesis, $Z_{3n+1} = xq_1(x)$ and $Z_{3n-1} = x^2q_(x)$. So $Z_{3n+2} = x^2q_1(x) + x^2q_2(x) = x^2(q_1(x) + q_2(x))$ So $Z_{3n+2}$ is divisible by $x^2$. Further, it cannot be divisible by a higher power of $x$: for that to happen, either $q_1(x) + q_2(x)$ is the zero polynomial (impossible since those are of different degree) or $q_1(x)$ and $q_2(x)$ must be divisible by $x$ (which, if true, would contradict the inductive hypothesis that $Z_{3n+1}$ and $Z_{3n-1}$ are divisible by $x$ and $x^2$, respectively, but not by any higher powers of $x$). 

Corollary 1: $Z_n$ has a root at zero if and only if $n$ is not divisible by 3. So the sequence $m_n$ of maximum roots of $Z_n$ will look like $m_0, 0, 0, m_3, 0, 0,...$ where $m_0, m_3,...$ are nonzero. 

Corollary 2: $Z_n(0) = 1$ whenever $n$ is divisible by 3. 

### The Zach Polynomials Are Positive for All Positive Values of x
In other words: for all $n$, and for all $x > 0$, $Z_{n} > 0$. Proof: this follows from the fact that the $Z_n$ polynomials have all their coefficients nonnegative, and at least one nonzero coefficient. The former can be proven inductively, using the fact that the sum and product of polynomials whose coefficients are nonnegative is another polynomial whose coefficients are nonnegative. The latter can be proven from the stronger statement that the $Z_n$ polynomials are monic, which itself follows inductively. 

Corollary: The sequence of maximum real roots is bounded above by 0. Using the other result above, the max real root equals 0 if and only if $n$ is not divisible by 3. 

Golden numbers: char eqn. = $t^2 - xt - 1$. This has roots $\frac{x + \sqrt{x^2 + 4}}{2}$ and $\frac{x - \sqrt{x^2 + 4}}{2}$. 

### Cases Mod 6
0 mod 6: no root at 0, even degree.
1 mod 6: root at 0, odd degree. 
2 mod 6: double root at 0, even degree.
3 mod 6: no root at 0, odd degree.
4 mod 6: root at 0, even degree.
5 mod 6: double root at 0, odd degree.

3 mod 6 must have a negative real root (since f(0) = 1, no positive real root, and f(-infinity) = -infinity). 
4 mod 6: factoring out x leaves an odd-degree monic polynomial with all coefficients nonnegative; this must have a root for some negative real x.
5 mod 6: factoring out x^2 gives same situation as above. 
