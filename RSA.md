# RSA
RSA is a public-key encryption system, i.e. it has a public key which senders use for encryption and a private key which the receiver uses for decryption. It must be computationally hard to compute a working private key given only the public key; in RSA, this difficulty comes from the difficulty of factoring large numbers.

How and Why RSA Works
---------------------
The basic scheme for RSA is as follows: the receiver picks two distinct primes p and q, and uses them to compute a "public modulus", n, an encrypting exponent, E, and a decrypting exponent, D. They make n and E publicly available, while keeping p, q, and D secret. If someone wants to send the receiver a message M (which must be an integer less than n), they find $W \equiv M^E$ (mod n) and send it to the reciever, who then finds $W^D$ (mod n) which, given the way that E and D were chosen, is equal to M.

How does all of this work? What we need are two numbers E and D such that $(M^{E)D} \equiv M$ (mod n). We can find them; the key observation on the way to this fact is that, by Euler's Theorem (link), if M is not divisible by p or q, M^(p-1)(q-1)^ ≡ 1 (mod n), since φ(n) = (p-1)(q-1).  A corollary of this is that M^k(p-1)(q-1) ^≡ 1 (mod n), for any natural number k, which implies that M^1 + k(p-1)(q-1) ^≡ M (mod n). At last, we have a route to the numbers E and D--find natural numbers such that ED = 1 + k(p-1)(q-1), or in other words, ED - k(p-1)(q-1) = 1. If we let E be an arbitrary natural number which is relatively prime to (p-1)(q-1), this becomes a linear Diophantine equation, which we can solve using the Extended Euclidean Algorithm to compute D. 

One minor detail has to be cleared up: the case where M is divisible by p or q. This is rare in actual practice, but even when it happens, it is still true that M^1+k(p-1)(q-1) ^≡ M (mod n). When pq|M, it's easy enough: M ≡ 0 (mod n), so M^a^ ≡ 0 (mod n) for any a, including a = 1 + k(p-1)(q-1). For the case where M is divisible by only one of p and q, suppose without loss of generality that p divides M but q does not divide M. Since M ≡ 0 (mod p), we have M^1+k(p-1)(q-1) ^≡ 0 ≡ M (mod p). As for q, since q is prime and M is relatively prime to q, we have (by Fermat's Little Theorem) M^(q-1)^ ≡ 1 (mod q). This implies that (M^(q-1)^)^k(p-1)^ ≡ 1 (mod q), or M^1+k(p-1)(q-1) ^≡ M (mod q). So we have, by the Chinese Remainder Theorem(link), that M^1+k(p-1)(q-1)^ ≡ M (mod pq).  

With all this in hand, it is possible to give a more detailed account of how RSA works. First, the receiver picks two primes, p and q. The primes should be large, so as to make the modulus n harder to easily factor. A random number generator combined with a fast primality test like the [Fermat test](Primality%20testing.md) suffices for this--the chance of accidentally generating a composite number as one of the "primes" is real but negligible. Then, the receiver computes (p-1)(q-1) and chooses a number E which is relatively prime to (p-1)(q-1). (Typically, a small odd prime like 3 or 17 is chosen; the smallness helps ensure that D ends up being large, which makes D harder to guess. E is tested with the Euclidean algorithm to make sure it is relatively prime to (p-1)(q-1); if not, another can be chosen.) Then, D is computed using the Extended Euclidean Algorithm with (p-1)(q-1) and E, and n is computed by just multiplying p and q. Now the receiver has all the keys, and can make available the public key (consisting of E and n). Anyone who wants to send messages to the receiver can encrypt them by taking their message M (a number or text encoded as a number), finding W = M^E^ (mod n), which can be done quickly through [repeated squaring,](Modular%20exponentiation%20by%20repeated%20squaring.md) and then sending the result to the receiver. The receiver then finds W^D^ = M^ED^ (mod n), which, given how E and D were chosen, is congruent to M (mod n). Thus the sender has retrieved the original message. 

Uses of RSA: Key Distribution and Digital Signatures
----------------------------------------------------
RSA could, in principle, be used to encrypt and send arbitrarily long messages. Any message sent through RSA needs to be shorter than the key. (This is so decryption can be unambiguous--there are infinitely many numbers congruent to a number mod n, so you need to pick one as the standard. "Smallest natural number congruent to...mod n" is a good standard.) However, by breaking up a long message into many smaller ones, you can still send arbitrarily large messages. The problem is that RSA takes a long time to encrypt long messages, making it impractical for this use. Instead, RSA is most often used to send the key for a faster symmetric encryption scheme. 

RSA can also be used as a digital signature algorithm, i.e. a way to verify that someone is who they claim to be. Suppose Alice wants to know that someone who claims to be Bob is, in fact, Bob. One way to do this would be to send Bob a message and have him "sign" it by encrypting it with his private key. Alice can then "verify" the signature by using Bob's public key to decrypt the signed message. If the result lines up with what Alice originally sent Bob, Alice knows that Bob has Bob's private key, which would imply that Bob is, in fact, Bob. 

Security of RSA and Possible Pitfalls
-------------------------------------
A message encrypted with an RSA public key is nonsense to anyone who lacks the private key. Generating the private key in the way that the receiver generated it requires having (p-1)(q-1), which of course requires having p and q. As such, an eavesdropper could generate a private key by factoring n and then going through the same steps that the receiver used to generate the private key. However, factoring is currently computationally hard (in exponential time) and it is generally believed that it will stay computationally hard on classical computers. As computing power grows, factoring takes less time, but choosing larger key sizes can help offset this; the current standard is to use 1024 or 2048-bit primes to generate 2048 or 4096-bit keys. Factoring can be done in polynomial time on a quantum computer, so the creation of large, usable quantum computers would make RSA insecure; but for now, quantum computing poses no real threat to RSA.  Besides the threat of factoring, it is also possible that there is a computationally easy way to get D without knowing p or q, but as of now, it appears that no such method has been found. 

Even though the *underlying algorithm* looks secure, there are some insecurities that can arise from improper use or implementation of RSA. One is the possibility of a "chosen-plaintext attack" against someone who misuses RSA digital signatures. Suppose that Eve intercepts a message to Bob that has been encrypted with Bob's public key. If Bob is willing to sign anything, Eve can just send him the encrypted message, and the signature will be the decrypted message, since the process used to sign is the same as the process used to decrypt. If Bob is a bit more canny, and is unwilling to sign things whose signature looks like text, Eve can still exploit him. The trick is to use a random number to scramble the message, while making sure that you have a way to reverse the scrambling. More specifically: suppose Eve has intercepted the ciphertext C ≡ M^E^ (mod n), and wishes to learn M without Bob knowing. She gets a random integer r, computes r^E^ (mod n), and then stores the multiplicative inverse of r (mod n) for later use (this can, of course, be computed with the Extended Euclidean Algorithm). Finally, she computes r^E^ * C (mod n) and asks Bob to sign it. When Bob signs it, he returns (r^E^ * C)^D^ ≡ r^ED^ * M^ED^ ≡ r * M (mod n). Bob suspects nothing, as this is not recognizably a piece of text; however, Eve can use it to retrieve M by simply multiplying it by the multiplicative inverse of r. The way to prevent chosen-plaintext attacks like this is to use a one-way hash function. If someone wants Bob to sign something, Bob hashes the message, signs the hash, and sends the signed hash. The receiver can verify the signature by applying the public key to the signed hash, then putting the original message through the hash function, and seeing if they line up. This way, signing and verifying still take place, but the verifier never knows what it looks like when the private key is applied to the message. 
