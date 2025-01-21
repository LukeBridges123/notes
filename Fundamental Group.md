# Definition
The fundamental group $\pi_1(X, x_0)$ is a group associated with any "pointed space", i.e. topological space $X$ with a "basepoint" $x_0$ singled out. It is the set of loops based at $x_0$, under the equivalence relation given by [[Homotopy]] of loops. The group operation is given by composition of loops: tracing out one loop, then another, gives you another loop. 

More formally, recall that a path is a continuous function $[0, 1] \to X$ (usually we will denote $[0, 1]$ by $I$ in what follows); a loop is a path with $f(0) = f(1)$. If $f(0) = x_0$ we say that the loop is based at $x_0$. Recall also that a homotopy of paths is a homotopy relative to $\{0, 1\}$ ("with endpoints fixed"); a homotopy of loops is the same ("with the basepoint fixed")--when deforming the loop, we always keep its start and end fixed at $x_0$. 

Then the homotopy of loops gives an equivalence relation on loops; thus for any loop $f$ based at $x_0$ we can speak of its equivalence class $[f]$. 

We can define an operation on loops based at $x_0$ as follows. Let $f: I \to X$ and $g: I \to X$ be two such loops; then let $fg: I \to X$ be given by $(fg)(t) = f(2t)$ if $0 \leq t \leq 1/2$, $(fg)(t) = g(2t - 1)$ if $1/2 \leq t \leq 1$. This is well-defined at $t = 1/2$ since $f(1) = g(0) = x_0$. Also, $(fg)(0) = f(0) = x_0$ and $(fg)(1) = g(1) = x_0$, so this composition gives another loop based at $x_0$. 
## Verification of the Group Axioms
The operation on paths has few nice algebraic properties--it is not associative, for example. But once we pass to equivalence classes, it does give a group operation. Define $[f][g] = [fg]$; then this is associative, has an identity element, and is invertible.


