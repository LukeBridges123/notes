# Cochain Complexes
A cochain complex is a graded vector space $C^* = \oplus_p C^p$ with a sequence of linear maps $d: C^p \to C^{p+1}$ such that $d^2 = 0$. 

(A graded vector space is a vector space $C^*$ which is the direct sum of several vector spaces $C^p$, where to each element of $C^*$ we assign it an integer "degree" $p$ based on which of the $C^p$ it's from.)

We can then define the cohomology $H^*(C^*) = \oplus_p H^p(C^p)$ where $H^p = (C^p \cap \ker(d)) / d(C^{p-1})$. 

This is just an abstraction of the setup in [[De Rham Cohomology]], where the exterior derivative $d$ maps $p$-forms to $p+1$-forms, and the $p$th de Rham cohomology is the quotient of the kernel of $d$ (closed forms) by the range of $d$ on the previous space (exact forms). 

A "cochain map" $f: C^* \to D^*$ is a linear map which preserves degree $(f(C^p) \subseteq D^p)$ and commutes with $d$, i.e. $(f \circ d_C = d_D \circ f)$. This induces a map $\overline{f}: H^*(C^*) \to H^*(D^*)$ by $\overline{f}([c]) = [f(c)]$, which is well-defined because $[f[c + d\alpha]] = [fc + d(f\alpha)] = [fc]$, using linearity and the fact that $f$ commutes with $d$.

# Exact Sequences
As a further abstraction of the above, we say that a (finite) sequence of vector spaces $V_i$ and linear maps $L_i: V_i \to V_{i+1}$, $\dots \to V_{i-1} \to^{L_{i-1}} \to V_i \to^{L_i} V_{i+1} \to \cdots$ is an "exact sequence" if $\ker(L_i) = \im(L_{i-1})$, which implies $L_i \circ L_{i-1} = 0$ (as in the case of the exterior derivative, and more generally cochain complexes), as well as that the cohomology $H^i = V_i \cap \ker(L_i) / L_{i-1}(V_{i-1})$ is always trivial (since the "numerator" and "denominator" are always equal). (This is analogous to the situation where every closed form is exact in de Rham cohomology). 

In an exact sequence, we have $\sum (-1)^i \dim(V_i) = 0$. This comes from using rank-nullity and the basic property of an exact sequence $\ker(L_i) = \im(L_{i-1})$, to turn that sum into a telescoping sum.

A *short exact sequence* is an exact sequence involving only 3 vector spaces, $0 \to A \to^L B \to^M C \to 0$. Since $\ker(L)$ is the image of the map $0 \to A$, $L$ is injective; since the kernel of the map $C \to 0$ is $\im(M)$, and is also clearly all of $C$, $M$ is surjective. 

When $A, B, C$ are cochain complexes and $L, M$ are cochain maps, we get induced maps between the cohomology classes $H^p(A) \to H^p(B) \to H^p(C)$ according to a certain diagram....

plus a "connecting homomorphism" $\delta: H^p(C) \to H^p(A)$. 

To define this, we first look at ....

take a $c \in C^p$ with $dc = 0$. Then there exists a (not necessarily unique) $b \in B^p$ with $M(b) = c$, since we have the surjective map $M: B^p \to C^p$. Now take $db$, which is in $B^{p+1}$. Then $M(db) = d(Mb) = dc = 0$, so $b$ comes from something in $A^{p+1}$. Hence there exists $a \in A^{p+1}$ with $L(a) = db$. 

Now, $L(da) = d(La) = ddb = 0$, and since $L$ is injective, we have $da = 0$. Hence $a$ is closed, and so we can take the equivalence class $[a] \in H^{p+1}(A)$, and define $\hat{\delta}(c) = [a]$. 

Now we check that this does not depend on which element of $C^p$ we chose to begin with. ..... all this means that we have a well-defined map $\delta$ on the cohomology classes, defined by $\delta([c]) = [\hat{\delta}(c)]$. 

# Zig-Zag Lemma
From the above, we get the fact that any short exact sequence induces a long exact sequence in cohomology: $H^{p-1}(A) \to H^{p-1}(B) \to H^{p-1}(C) \to H^p(A) \to H^p(B) \to \dots$  

Here the map from $H^p(A) \to H^p(B)$ at each level is $L^*$, the map in cohomology induced by the map $L: A \to B$ in the original short exact sequence; the same goes for the map $H^p(B) \to H^c(C)$. The maps from one "level" to another, $H^p(C) \to H^{p+1}(A)$, are the connecting homomorphism described above. 

The name comes from the diagram (see Tu, page 285) used to define the connecting homomorphism. 