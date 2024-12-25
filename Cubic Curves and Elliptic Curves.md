# Cubics with Genus 0
We first consider some "special" cubic curves, which are distinguished from the more typical elliptic curves by having singular points. These will turn out to be the cubics whose Riemann surface has genus 0; their most notable feature is that they have rational parameterizations.
## Semicubical Parabola
```desmos-graph
y^2 = x^3
```
The "semicubical parabola" has the equation $y^2 = x^3$. It has a sharp "cusp" at the origin: if we try to differentiate it implicitly we get $2yy' = 3x^2$ or $y' = \frac{3x^2}{2y}$, which clearly does not exist when $y = 0$; the same problem arises if we try differentiating with respect to $x$ instead. 

We can find by inspection the parameterization $(t^2, t^3)$. Alternatively, consider a line through the origin $y = tx$; we get $t^2x^2 - x^3 = 0$ or $x^2(x - t^2) = 0$, so there is an intersection of multiplicity $2$ at the origin and of multiplicity $1$ at $x = t^2$, whose corresponding y-coordinate is $t^3$. 
## Folium
```desmos-graph
x^3 + y^3 = 3xy
```
The "folium of Descartes" has the equation $x^3 + y^3 = 3axy$. This also has a singular point--here a point of self-intersection--at the origin. We can find a parameterization by the same strategy: substituting $y = tx$ we get $x^3 + t^3x^3 - 3atx^2 = 0$, or $x^2((1 + t^3)x - 3at) = 0$. This intersects the curve with multiplicity $2$ at the origin and multiplicity $1$ at $x = \frac{3at}{1 + t^3}$, $y = tx = \frac{3at^2}{1 + t^3}$. 

## Existence of Rational Parameterizations
Above, we used the same strategy for finding rational parameterizations that we used to find [[Quadratic Curves and Quadric Surfaces#Rational Parameterizations|rational parameterizations of conics]]: we picked a rational point, drew a line through it, and found that it intersected the curve in exactly one other point. This works because of Bezout's theorem. For a conic with no singular points, a line intersects the curve in 2 points; for a cubic with a singular point (of multiplicity 2), a line through that singular point can only intersect the curve in one more point. Thus we should expect to find rational parameterizations of cubics with a (rational) singular point, but not necessarily of other cubics. 
