# Linear diophantine equations
Linear Diophantine Equations
----------------------------
A Diophantine equation is an equation with integer unknown(s). A linear Diophantine equation is one whose unknowns are not being raised to any power; the most common is ax + by = c, where a, b, and c are integer constants and x and y are integer unknowns. One solves a linear Diophantine equation by finding the integer values for x and y (or, as will be seen, infinite family of values) that make the equation true. This raises the question of when linear Diophantine equations have solutions, how to find a solution, and how to use one solution to find more.

Existence of Solutions + Finding a Solution
-------------------------------------------
A linear Diophantine equation of the form ax + by = c has solutions x and y if and only if gcd(a, b)|c. The proof of this is as follows. Suppose that gcd(a, b) does not divide c. Then, since ax + by will always be a multiple of gcd(a, b), while c is not a multiple of gcd(a, b), ax + by will never equal c for any integer values of x and y. It follows that, if the equation does have solutions, it must be the case that gcd(a, b)|c. Now suppose that gcd(a, b) divides c, in other words, c = d * gcd(a, b) for some integer d. Using the extended Euclidean algorithm, one can find numbers x and y such that ax + by = gcd(a,b). Then one can multiply x and y by d to get the numbers xd and yd such that axd + byd = gcd(a, b) * d = c. So if a linear Diophantine equation has solutions, gcd(a, b)|c, and if gcd(a,b)|c, then the linear Diophantine equation has solutions.

Note also that this gives a method for finding a solution to a linear Diophantine equation. Begin by using the Euclidean algorithm to find gcd(a, b). Then check if gcd(a, b) divides c. If it doesn't, then the equation has no solutions, so you can stop right there. If it does, go back to what you did for the Euclidean algorithm, and use it for the extended Euclidean algorithm. You will now have gcd(a, b) expressed as a linear combination of a and b: ax + by = gcd(a, b). Since gcd(a,b)|c, c = gcd(a, b) * k where k is an integer. Multiplying x and y by k will get you the numbers x' = xk and y' = yk such that ax' + by' = c.

Using One Solution to Find All
------------------------------
Suppose you have numbers x~0~ and y~0~ such that ax~0 ~+ by~0~ = c.  How to find numbers x and y such that x~0 ~+ x and y~0 ~+ y are also solutions? This means looking for numbers such that a(x~0 ~+ x) + b(y~0~ + y) = c. We can distribute this out to get ax~0 ~+ by~0 ~+ ax + by = c, and since  ax~0 ~+ by~0~ = c, our equation is equivalent to ax + by + c = c or ax + by = 0 or simply ax = -by. This gives us a better idea of what we are looking for: numbers x and y such that, when we add them to x~0 ~and y~0~, we will increment/decrement ax~0 ~by the same amount that we decrement/increment by~0~. The way to do this is x = k * (b/gcd(a,b)) and y = -k * (a / gcd(a,b)), where k is an arbitrary integer. To prove this, let f = gcd(a, b), and let a = fi and b = fj. Since ax = -by, b|ax, or b|(fi)x. Since b|(fi)x and b = fj, it must be the case that f|(fi)x and j|(fi)x. It is clear enough that f|(fi)x. Since j is relatively prime to both f and i, it must divide x. So x must be some multiple of j, or in other words, some multiple of (b/gcd(a,b)). So all solutions for x are provided by k * (b/gcd(a,b)). We can apply the same argument for y. 

Applications
Division in congruences
gcd(ka, kb) = k * gcd(a, b)

