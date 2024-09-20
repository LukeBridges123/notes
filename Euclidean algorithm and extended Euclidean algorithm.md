# Euclidean algorithm and extended Euclidean algorithm
The Euclidean Algorithm is a method for computing the greatest common divisor of two numbers, which can also be used to express the greatest common divisor of two numbers as a linear combination of those two numbers. It is important in proofs related to [linear Diophantine equations](Linear%20diophantine%20equations.md).

The Euclidean Algorithm
-----------------------
First, a proof of the correctness of the Euclidean algorithm. Let a and b be integers, and without loss of generality suppose a >= b. One can use Euclidean division(link) to write a as a = bq~1~ + r~1~. It can be shown that gcd(a, b) = gcd(b, r~1~). First, let d be a number that divides both a and b and suppose that d does not divide r~1~. Then the sum bq~1~ + r~1~ would not be a multiple of d, and since a = bq~1~ + r~1~, a is not a multiple of d. But this contradicts our assumption that d divides both a and b. So any number which divides both a and b must divide r~1~. Second, let d be a number that divides both b and r~1~. Since d divides both b and r~1~, it divides their sum. Since a is equal to their sum, d divides a. So any number which is a common divisor of a and b is also a common divisor of b and r~1~, and vice versa. Therefore gcd(a, b) = gcd(b, r~1~). 

We can use this fact to create a process for calculating gcd(a, b). First use Euclidean division to get a = bq~1~ + r~1~. If r~1~ = 0, then b|a, so gcd(a, b) = b. Otherwise, since gcd(a, b) = gcd(b, r~1~), we can try again, writing b = r~1~q~1~ + r~2~. If r~2~ = 0, then r~1~ = gcd(b, r~1~) = gcd(a, b), so we have found gcd(a, b). Otherwise, we can keep repeating this process until we get a remainder of 0, at which point we know that we have gcd(a, b).

The Extended Euclidean Algorithm
--------------------------------
Suppose that the Euclidean Algorithm terminated in three steps. In other words, we calculated a = bq~1~ + r~1~ with r~1~ != 0, then b = r~1~q~2~ + r~2~, then r~1~ = q~2~r~2~ + 0, so gcd(a, b) = r~2~. How to represent r~2~ as a linear combination of a and b–in other words, how to find the numbers x and y such that ax + by = r~2~? Well, r~2~ = b - r~1~q~2~, and r~1~ = a - bq~1~, so r~2~ = b - (a - bq~1~)q~2~ = -q~2~a + b(1 + q~1~q~2~). The exact values aren’t important here; the important thing is that we have found values of x and y such that ax + by = gcd(a, b). One can generalize this to Euclidean Algorithms that proceed for arbitrary numbers of steps: give the gcd in whatever terms the algorithm most directly gives it in (generally, those of the second-to-last step), rewrite those terms in the terms of the previous step, and continue until you have gcd(a, b) in terms of a and b.

This idea of "going backwards" is fine for pencil and paper and for a proof of correctness, but insufficient for a computer implementation. To do this, we keep track of variables x~i~ and y~i~ that give us the most recent remainder as a linear combination of a and b. To derive formulas for these, suppose we have the following established. (These essentially state that we have done at least 2 steps of the algorithm, have the remainders of the most recent step and the one before it given in terms of x and y, and would like to find the remainder of the next step in terms of a and b.)
r~i-4~ = r~i-3~q~i-2~ + r~i-2~, and ax~i-2~ + by~i-2~ = r~i-2~
r~i-3~ = r~i-2~q~i-1~ + r~i-1~ and ax~i-1~ + by~i-1~ = r~i-1~
r~i-2~ = r~i-1~q~i~ + r~i~

How do we write r~i~ in terms of a and b? We know that r~i~ = r~i-2~ - r~i-1~q~i~, so we can substitute in the identities given for r~i-2~ and r~i-1~ to get:
r~i~ = ax~i-2~ + by~i-2~ - q~i~(ax~i-1~ + by~i-1~)
Distributing out the q~i~ and rearranging a bit gets:
r~i~ = ax~i-2~ - q~i~ax~i-1~ + by~i-2~ -q~i~by~i-1~
Factoring out a and b gets:
r~i~ = a(x~i-2~ - q~i~x~i-1~) + b(y~i-2~ -q~i~y~i-1~)
And this gives us the formula for x~i~ and y~i~ we were looking for. In other words, at the i^th ^step of the algorithm, with i > 2, we can find the needed x by taking the x from two steps ago, and subtracting from it the product of the quotient from the i^th^ step and the x from one step ago; the same goes for y. However, this doesn't establish what x and y should be for the first and second steps. To do this, suppose that a and b are positive integers, and suppose without loss of generality that a is greater than or equal to b. We should therefore have x~1~ = 1, x~2~ = 0, y~1~ = 0, y~2~ = 1. The numbers for the first step ensure that, if b = 0, the algorithm will correctly say that gcd(a, b) = a and give the relevant linear combination as simply a. The numbers for the second step ensure the same for the case where b divides a. The two sets of numbers working together ensure the correctness of the algorithm as a whole.



