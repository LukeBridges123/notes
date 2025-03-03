# Projective Spaces and Homogenous Coordinates
Over any field $K$, we define the $n$-dimensional projective space to be the set of all 1-dimensional subspaces of $K^{n+1}$. One way to think of these spaces is as the quotient of $K^{n+1}$ by the equivalence relation $v \cong \lambda v$ for any nonzero scalar $\lambda \in K$. Another is to consider the plane of points $(x_1, \dots, x_{n+1})$ with $x_{n+1} = 1$. Then most subspaces (thought of as lines through the origin) can be identified with a point in that plane. The exceptions are the subspaces parallel to that plane--the ones with $x_{n+1} = 0$ for all points in the space. We note in passing that we may also use the notation $(x_1 : \dots : x_{n+1})$ for a point in projective space. 

We typically think of this plane as a way of embedding the n-dimensional affine space $\A^n$ in n-dimensional projective space $\mathbb{P}^n$. In other words the map $(x_1, \dots, x_n, 1 ) \to (x_1, \dots, x_n)$ gives such a correspondence. Usually we specifically identify these points (the ones whose last coordinate is nonzero) with the affine n-space, calling them the "affine part" of projective space, and call the rest (the ones whose last coordinate is nonzero) "points at infinity"; observe that the points at infinity form a projective space of dimension $n-1$. However, there is of course nothing special about the last coordinate. We can more generally define an "affine patch" consisting of all the points where a given coordinate $x_i$ is nonzero. 

# Projective Transformations


















# Projective Spaces as Manifolds
## N-Dimensional Real Projective Space
The "real projective space" $\R P^n$ is given by the set of all lines through the origin in $\R^{n+1}$. This is a quotient of $\R^{n+1}\backslash \{0\}$ by the equivalence relation that identifies all vectors which are nonzero scalar multiples of each other. Thus the equivalence class of a vector $v$ is the span of $v$. We can then use the quotient topology on this set of equivalence classes. 

First we show that, in this topology, $\R P^n$ is locally Euclidean. (Throughout, we use $[x^0, \dots, x^n]$ to represent the equivalence class of $(x^0, \dots, x^n)$ in $\R^{n+1}$.) We will start by finding some open sets, and we'll then go on to define charts on those sets. Take an open set $\tilde{U}_k$ defined as all the points in $\R^{n+1}$ with a nonzero $x^k$ coordinate. (Thus it's the whole space minus a hyperplane perpendicular to the $x^k$ axis, passing through the midpoint of that axis.) Now let $U_k$ be the image of that under the quotient map. ; this is open if and only if $\pi^{-1}(U_k) = \pi^{-1}(\pi(\tilde{U}_k))$ is open, by the properties of quotient maps. We claim that $\pi^{-1}(\pi(\tilde{U}_k)) = \tilde{U}_k$, which is open. Let $x$ be in that set on the left-hand side; then $\pi(x) \in \pi(\tilde{U}_k)$, so there exists $y \in \tilde{U}_k$ with $\pi(x) = \pi(y)$. Thus $x = ty$ for some nonzero scalar $t$. Since $y \in \tilde{U}_k$ it has a nonzero $x^k$ coordinate, and so does $x$, since it's a scalar multiple of $y$. Thus $x \in U_k$. Conversely, let $x \in \tilde{U}_k$; the fact that it is in $\pi^{-1}(\pi(\tilde{U}_k))$ follows from basic set theory. Thus $\pi^{-1}(\pi(\tilde{U}_k)) = \tilde{U}_k$ and so $\tilde{U}_k$ is open.

Now define charts $\phi_k$ on the $U_k$ by $\phi_k([x^0, \dots, x^k]) = (x^0/x^k, \dots, x^{k-1}/x^k, x^{k+1}/x^k, \dots, x^n/x^k)$. That is, we remove the $x^k$ coordinate and divide everything else by $x^k$, which we can do since $x^k$ is nonzero. This is well-defined, in the sense that using any other representative for the equivalence class (which must be of the form $[tx^0, \dots, tx^k]$) gets us the same result. For each coordinate of the result is then of the form $(tx^i)/(tx^k) = x^i/x^k$, which is the same as before. We claim that $\phi_k$ is a homeomorphism. Continuity follows from (something about quotient mappings; since $\phi \circ \pi$ is continuous $\phi$ must be as well). Its inverse is given by $(y^1, \dots, y^n) \to [y^1, \dots, 1, \dots, y^n]$, with a $1$ in the $k$th coordinate slot. Under the forward map a point $[x^0, \dots, x^n]$ gets mapped to $(x^0/x^k, \dots, x^{n+1}/x^k)$, with the $k$th coordinate removed and that in turn gets mapped by the inverse to $[x^0/x^k, \dots, 1, \dots, x^{n+1}/x^k]$. But this is the same equivalence class as the equivalence class you get by multiplying all of those numbers by $x^k$, namely $[x^0, \dots, x^k, \dots, x^{n+1}]$, which is where we started. The other direction works similarly, and so this is an inverse. Finally, we check that the inverse $\psi_k$ is continuous. This is because $\psi_k = \pi \circ \tilde{\psi_k}$ where $\tilde{\psi_k}$ is the corresponding map on representatives of equivalence classes, and both of those maps are continuous. Thus $\phi_k$ is a homeomorphism to $\R^n$, and all the charts $(U_k, \phi_k)$ cover $\R P^n$ (since we've excluded the point $(0, \dots, 0)$, every point has at least one nonzero coordinate, and so is in at least one of the $U_k$), so $\R P^k$ is at least a topological manifold.
### Real Projective Line
An alternative way to think of the real projective line $\R P^1$ is through stereographic projection. Take the ordinary line, place a circle on top of it (so that the "bottom" or "south pole" of the circle is tangent to the line), and for any point on the line, draw another line from it to the "north pole". This will intersect the circle in exactly one other place, which is the point on the circle associated with that point on the ordinary, non-projective line. A horizontal line drawn at the north pole does not intersect the ordinary line anywhere; it corresponds to the "point at infinity" on the projective line. Thus, when we turn the ordinary line into the projective line by completing it with a point at infinity, we get a circle. 
## Complex Projective Space
The complex projective space $\C P^n$ is defined similarly to real projective space: the set of all complex lines through the origin in $\C^{n+1}$, or equivalently the quotient of $\C^{n+1} - \{0\}$ by the equivalence relation that identifies two vectors if they are complex scalar multiples of each other. 

We can put charts on $\C P^n$ in a way that's also similar to what is done for $\R P^n$. Once again, one uses coordinates $[z^0, \dots, z^n]$ (where this has the same coordinates as $[\lambda z^0 ,\dots, \lambda z^n]$ for any nonzero complex $\lambda$), and defines charts on the set $U_i$ of points whose $i$th coordinate is nonzero by $\phi_i([z^0, \dots, z^n]) = (\frac{z^0}{z^i} , \dots, \frac{z^{i-1}}{z^i}, \frac{z^{i+1}}{z^i}, \dots, \frac{z^n}{z^i})$. The proof that these define an atlas on $\C P^n$ proceeds similarly. 

Just like how $\R P^n$ can be thought of as the $n$-sphere with antipodal points identified, which is the same as quotienting it by a certain group action of $\Z/2\Z$ on the points of the sphere, $\C P^n$ can be thought of as a quotient of the $2n+1$ sphere by an action of the circle group $S^1$. 

### The Riemann Sphere
Like with the real projective line, stereographic projection shows that the "complex projective line" (the projective completion of $\C$, which we would usually think of as the complex *plane*) is equivalent to a sphere, with the north pole as a point at infinity. This is called the *Riemann sphere*. 