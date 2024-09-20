# Fermat's Little Theorem
Fermat's Little Theorem, one of the most important theorems in number theory, can be stated as follows. Let p be a prime and let a be a natural number relatively prime to p. Then a^p-1^ ≡ 1 (mod p). An equivalent statement is: if p is a prime and a is relatively prime to p, then a^p^ ≡ a (mod p) It is a special case of Euler's Theorem(link).

Proof of the Theorem
--------------------
Before proving the theorem, we must prove a certain lemma about complete residue systems(link). It goes like this: let a be a natural number relatively prime to some prime p. Then the set {a, 2a, 3a, ... pa} forms a compete residue system mod p. To prove this, we first note that for any two distinct natural numbers x and y, with 1 <= x, y <= p, ax is not congruent to ay (mod p). Suppose without loss of generality that x > y. Then x - y is some natural number less than p, and therefore relatively prime to p (since p is prime), so p does not divide x - y. Since a is also relatively prime to p, a(x - y) is also not divisible by p: the multiplication by a does not introduce p into the prime factorization, so the result is still relatively prime to p, and thus not divisible by p. This means that ax is not congruent to ay (mod p), by the definition of congruence. Therefore, the set {a, 2a, 3a, ... pa} consists of p natural numbers, with no two being congruent to each other. Therefore, by a theorem in the article for complete residue systems, the set {a, 2a, 3a,... pa} is a complete residue system mod p.

A corollary of this is that each member of that set is congruent to a single member of the set {1, 2, 3, ... p}, which is also a complete residue system mod p. Clearly ap ≡ p (mod p), so we can further reduce this to saying that each member of the set {a, 2a, 3a, ... (p-1)a} is congruent to a single member of the set {1, 2, 3, ... (p-1)}. Now we can begin the proof proper. Because each member of the first set is congruent to a single member of the second and vice versa, we know by one of the basic properties of congruence that a * 2a * 3a * ... * (p-1)a ≡ 1 * 2 * 3 * ... * (p-1) (mod p), or in other words, (p-1)! * a^p-1^ ≡ (p-1)! (mod p). By another basic property of congruence, since (p-1)! is relatively prime to p, we can divide it from both sides of the congruence to get a^p-1^ ≡ 1 (mod p). 

Alternate Statement of the Theorem
----------------------------------
Another way of stating Fermat's Little Theorem is that, if a is any number and p is a prime, a^p^ ≡ a (mod p). This is equivalent to the first statement, in that it can be derived from the first statement and vice versa. To derive the second from the first, let's grant that a^p-1^ ≡ 1 (mod p) when a is relatively prime to p. Since congruence is preserved when multiplying both sides by a constant, this implies that a * a^p-1^ ≡ 1 * a (mod p), or a^p^ ≡ a (mod p). Alternatively, suppose that a is not relatively prime to p. Then a must be a multiple of p. In that case, a^p^ ≡ a (mod p), since a^p^ - a is just subtracting a multiple of p from a multiple of p, so the result will still be a multiple of p. This proves the second version from the first. To derive the first from the second, suppose that a^p^ ≡ a (mod p) for all integers a and primes p. If a is relatively prime to p, we can divide it from both sides of the congruence to get a^p-1^ ≡ 1 (mod p). This proves the first version from the second.

Alternate Proof Via the Binomial Theorem
----------------------------------------
We can also prove Fermat's Little Theorem, specifically the second version, using the Binomial Theorem. Note to self: get Latex installed properly since it'll be fairly notation-heavy.

Applications
------------

