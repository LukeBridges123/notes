# GCD and LCM
This page contains some miscellaneous results about the gcd that aren't found on the page about [the Euclidean Algorithm](Euclidean%20algorithm%20and%20extended%20Euclidean%20algorithm.md).
Lemma 1 for proof about LCM below: gcd(a, bc) <= gcd(a, b) * gcd(a, c). 
Proof: Let d = gcd(a, b) and e = gcd(a, c). Then au + bv = d and ax + cy = e for integers u, v, x, y. So d * e = (au + bv) * (ax + cy) = (au)(ax) + (au)(cy) + (bv)(ax) + (bv)(cy) = a(aux + ucy + bvx) + (bc)(vy) = d * e. Therefore, we can write gcd(a, b) * gcd(a, c) as a linear combination of a and bc, so gcd(a, bc) must divide gcd(a, b) * gcd(a, c), so gcd(a, bc) <= gcd(a, b) * gcd(a, c). 

Let d = gcd(a, b). Then lcm(a, b) = ab/d.
Proof: let k be an integer such that a|k and b|k. Since a|k, we have k = an for some integer n. Also, since b|k and (b/d)|b, it must be that (b/d) divides k. Furthermore, by Euclid's Lemma, since gcd(a, b/d) = 1, it must be that (b/d) divides n. So k = a * (b/d) * m for some positive integer m, or in other words, k = (ab/d) * m. Therefore, any positive integer which is divisible by both a and b must be of the form (ab/d) * m for some positive integer m. Since 1 is the least positive integer, it follows that (ab/d) * 1 is the smallest positive integer divisible by a and b, or in other words, lcm(a, b) = ab/d. 

