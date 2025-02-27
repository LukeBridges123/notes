# Definition
A "covering space" $Y$ of a topological space $X$ is a space with a continuous map $p: \tilde{X} \to X$ such that, for any point $x \in X$, there is an open neighborhood $U$ such that $p^{-1}(U)$ is a union of disjoint open sets $U_i$, each homeomorphic to $U$. We say that $U$ is an "evenly covered" neighborhood of $x$. 
....

Let $\tilde{X}$ be a covering space of $X$ with covering map $p$. Let $f: Y \times I \to X$ and suppose $\tilde{f}_0$ is a lift of $f_0 = f|_{Y \times \{0\}}$. Then there exists a unique lift $\tilde{f}: Y \times I \to \tilde{X}$ of $f$ (so that $p \circ \tilde{f} = f$).

The basic idea is to lift neighborhoods of a point $y_0 \in Y$, then find a way to "paste" those lifts together; for that, we will use compactness so that we only have to worry about finitely many neighborhoods. 

We can always find neighborhoods of the form $N_t \times (a_t, b_t)$ where $N_t$ is an open set in $Y$ (since these are a basis for the product topology, any neighborhood of $y_0 \times t$ will be a union of such sets). By the continuity of $f$ there exists an open neighborhood $U$ of $f(y_0, t)$ with $f(N_t \times (a_t, b_t)) \subseteq U$. In fact we can choose $U$ to be an evenly covered neighborhood. Since $y_0 \times I$ is compact, we can cover it with finitely many neighborhoods $N_{t_i} \times (a_{t_i}, b_{t_i})$. Let $N$ be the intersection of all the $N_{t_i}$ (which is an open set containing $y_0$) and choose a partition $0 = t_0 < t_1 < \dots < t_m = 1$ so that $f(N \times [t_i, t_{i+1}]) \subseteq U$ 

... One corollary of this is the "path lifting" property. Setting $Y$ to be a single point, $\tilde{f}_0$ is just a constant function, selecting a single point $\tilde{x}_0 \in p^{-1}(x_0)$. Then we get that there exists a unique lift of the path $f$ starting at $\tilde{x}_0$. 

Another is the path homotopy lifting property, which follows from setting $Y = I$...

# Examples
Cover of $S^1$ by $\R$...

finite-sheeted covers: define $p_n: S^1 \to S^1$ by $p_n(z) = z^n$...

In fact, these are the only possible (connected) covering spaces of $S^1$. It's easy to get coverings by disconnected spaces, but they aren't very interesting.


# The Galois Correspondence
There exists a correspondence between covering spaces of a space $X$ and subgroups of $\pi_1(X)$. 

One direction of this is that, if $p$ is a covering map $\tilde{X} \to X$, then the induced homomorphism $p_*$ is injective. Thus $\pi_1(\tilde{X})$ can be identified with a subgroup of $\pi_1(X)$. 

Proof: let $\tilde{f}_0 \in \ker(p_*)$; then $p \circ \tilde{f}_0$ is homotopic to a constant path. We can lift this homotopy to get a (unique) homotopy $\tilde{f}_t$ to a lift of the constant path. Clearly the constant path in $\tilde{X}$ is a lift of the constant path in $X$; uniqueness implies that $\tilde{f}_0$ is homotopic to a constant.

Note that, in general, loops in $X$ may not lift to loops in $\tilde{X}$. We have already seen this with the cover of $S^1$ by $\R$. ....

For the other direction, given a subgroup of $\pi_1(X)$, we must construct a cover of $X$ with that as its fundamental group. 

An especially important case is the trivial subgroup. In $S^1$ this is realized by the covering by $\R$. In the torus, we can cover by $\R^2$. $S^1 \vee S^1$ has a more complicated cover by an infinite graph. More generally, we want a simply connected cover of $X$. For completely general spaces, this is not always possible. To see what conditions we can add to make it possible, suppose that $\tilde{X}$ is a simply-connected covering space of $X$. Then each point $x \in X$ has a neighborhood $U$ which is homeomorphic to an open subset $\tilde{U}$ of $\tilde{X}$; any loops in $U$ will lift to trivial loops. But then we can use the homeomorphism $\tilde{U} \to U$ to show that these loops are trivial in $X$. Thus each point in $X$ has a neighborhood $U$, such that all loops in $U$ become trivial when embedded in $X$. (They do not have to be trivial in $U$ itself.) If this property holds, we say that $X$ is "semilocally simply-connected". ("Locally simply-connected" means that the space has a basis of simply-connected open sets. Manifolds and CW complexes are locally simply-connected.)

Thus we will limit ourselves to spaces which are semilocally simply-connected. In this case we have the following: if $X$ is path-connected, locally path-connected, and semilocally simply-connected, then $X$ has a simply connected covering space, or "universal cover".
## Universal Covers
If $\tilde{X}$ is a universal cover of $X$, then we have a bijection between points in $\tilde{X}$, and homotopy classes of paths based at a given point $\tilde{X}$. The idea is that paths in $X$ are homotopic iff their lifts in $\tilde{X}$ have the same endpoint. If $\tilde{a}(1) = \tilde{d}(1)$ for lifted paths $\tilde{a}, \tilde{d}$ then $\tilde{a}\tilde{d}^{-1}$ is the identity in $\pi_1(\tilde{X})$, so $ad^{-1} = 0$ in $\pi_1(X)$, so $a \simeq d$. Conversely, if $a \simeq d$, then $\tilde{a} \simeq \tilde{d}$, which can only happen if $\tilde{a}, \tilde{d}$ have the same endpoint. 

This then gives us an idea of how to construct a universal cover: simply *define* it as the set of homotopy classes of paths in $X$, then find the right topology on that. So, let $\tilde{X}$ be the set of all homotopy classes $[\gamma]$ where $\gamma$ is a path in $X$ starting at $x_0$. Define the covering map $p$ by $p([\gamma]) = \gamma(1)$. 

First we give a topology to $\tilde{X}$ by specifying a basis of open sets. Recall that a basis for a topological space $Y$ is a collection of open sets such that every point in $Y$ has a neighborhood in the basis, and if $y \in U_1 \cap U_2$ for $U_1, U_2$ in the basis, then there exists a neighborhood $U_3$ of $y$ in the basis with $U_3 \subseteq U_1 \cap U_2$. Every open set in $Y$ is a union of sets in the basis. 

Define a basis $B$ of $X$ as follows: $B$ is a collection of path-connected open sets $U \subseteq X$ such that $i_*: \pi_1(U) \to \pi_1(X)$ is trivial. (This is possible because $X$ is locally path-connected and semilocally simply connected.) For each $U \in B$ and path $\gamma$ starting at $x_0$, ending in $U$, define $U_{[\gamma]}$ to be the set of all $[\gamma\eta]$ where $\eta$ is a path in $U$ with $\eta(0) = \gamma(1)$. That is, $U_{[\gamma]}$ is the set of all "extensions" of $\gamma$ by paths contained in $U$. 

Note that $p(U_{[\gamma]}) \subseteq U$, since $\eta(1) \in U$. We want $p$ to be a bijection $U_{[\gamma]} \to U$. It is surjective because $U$ is path-connected: given any $\gamma$ ending in $U$ and $x_1 \in U$, we can always find a path $\eta$ from $\gamma(1)$ to $x_1$. Then $p([\gamma\eta]) = x_1$. For injectivity, suppose $\eta, \eta'$ are paths connecting $\gamma(1)$ to $x_1$. Then since the inclusion-induced map $\pi_1(U) \to \pi_1(X)$ is trivial, $[\eta][\eta']^{-1} = [1]$, so $\eta \simeq \eta'$. Thus $p$ is a bijection. 

Now we check that $p$ is continuous, giving $\tilde{X}$ the topology with basis $U_{[\gamma]}$. For $U \in B$, the preimage $p^{-1}(U)$ is the disjoint union, over all paths $\gamma$ from $x_0$ to $y_0 \in U$, of $U_{[\gamma]}$. Since the union of open sets is open, $p^{-1}(U)$ is open, and $p$ is continuous. Thus $p|_{U_{[\gamma]}}$ is a local homeomorphism, so $p: \tilde{X} \to X$ is a covering map. 

All that is left to show is that $\tilde{X}$ is simply connected. First we need to show that $\tilde{X}$ is path-connected. If $[\gamma]$ is a path in $X$, then any "sub-path" $\gamma_t$, where we restrict the domain of $\gamma$ to $[0, t]$, is also a path. Then the path $\tilde{\gamma}(t) = [\gamma_t]$ is a path through $\tilde{X}$. Then, to show that $\pi_1(\tilde{X})$ is simply-connected, let $f: I \to \tilde{X}$ be a loop based at $[1]$ (as a point in $\tilde{X}$). Projecting it down with $p$ gets a loop $\gamma$ in $X$, based at $x_0$. Now let $\gamma_t$ be the shortened path as before. Then the points $[\gamma_t]$ form a path in $\tilde{X}$ lifting the loop $\gamma$. ....
## Realizing Subgroups
The universal cover corresponds to the trivial subgroup of $\pi_1(X)$. Now we will construct a covering space $X_H$ with $\pi_1(X_H) = H$ for any subgroup $H$ of $\pi_1(X)$; it will be a quotient of the universal cover $\tilde{X}$. 

The equivalence relation on points in $\tilde{X}$ (which are homotopy classes of paths in $X$) is as follows: given paths $[a], [b] \in \tilde{X}$ with $a(1) = b(1)$, we say $[a] \cong [b]$ if and only if $[a\ol{b}] \in H$. .....

## Isomorphisms of Covering Spaces
We now turn to the question of the uniqueness of covering spaces realizing a given subgroup. It will turn out that covering spaces which are (in the right sense) isomorphic correspond to subgroups in the same conjugacy class. 

Before we do any of this, we will need a general lifting criterion for functions. Let $f: Y \to X$ be a continuous function and let $p: \tilde{X} \to X$ be a covering map. We want to know when we can find a lift $\tilde{f}: Y \to \tilde{X}$ with $p \circ \tilde{f} = f$. 

If such a lift exists, then $f_*(\pi_1(Y, y_0)) = (p \circ \tilde{f})_*(\pi_1(Y, y_0))$, so $f_*(\pi_1(Y, y_0)) \subseteq p_*(\pi_1(\tilde{X}, x_0))$. Thus we have a necessary condition for lifts to exist. We can see, for example, that $Y = [0, 1]$ meets this condition no matter what $X, \tilde{X}$ are, since $\pi_1(Y) = \{0\}$ in that case.

Now we can turn this into the desired criterion for the existence of lifts: if $Y$ is path-connected and locally path-connected, then given a continuous function $f: (Y, y_0) \to (X, x_0)$, it lifts to a function $\tilde{f}: (Y, y_0) \to (\tilde{X}, \tilde{x}_0)$ if and only if $f_*(\pi_1(Y, y_0)) \subseteq p_*(\pi_1(\tilde{X}, x_0))$. Thus the condition which we showed to be necessary is also sufficient. 

For the other direction, suppose $f_*(\pi_1(Y, y_0)) \subseteq p_*(\pi_1(\tilde{X}, x_0))$. Take $y \in Y$ and choose a path $\gamma$ from $y_0$ to $y$. Then $f \circ \gamma$, which is a path in $X$, has a lift starting at $\tilde{x_0}$. Now define $\tilde{f}(y) = \tilde{(f \circ \gamma)}(1)$, i.e. the endpoint of the lifted path. We show first that this is well-defined. If we pick another path $\gamma'$ from $y_0$ to $y$, we can lift $f \circ \gamma'$ in the same way. Now consider $f_*([\gamma \ol{\gamma'}])$. Since $[\gamma\ol{\gamma'}] \in \pi_1(Y)$ and  $f_*(\pi_1(Y, y_0)) \subseteq p_*(\pi_1(\tilde{X}, x_0))$, we have that $f_*([\gamma \ol{\gamma'}])$ is the image of some loop in $\tilde{X}$. Thus $(f \circ \gamma)\ol{(f \circ \gamma')}$ lifts to a loop in $\tilde{X}$ which implies...endpoints of lifts are the same...so $\tilde{f}(y)$, which is defined to be the endpoint of such a path, is the same no matter what path we choose.

Now we show that $\tilde{f}$ is continuous. Here we will begin to use the hypothesis of local path-connectedness heavily. Let $U$ be a neighborhood of $f(y)$ 


# Deck Transformations
An automorphism of a covering space (i.e. an isomorphism from a covering space to itself) is called a "deck transformation" or "covering transformation". If $p: \tilde{X} \to X$ is a covering space, then a deck transformation $f: \tilde{X} \to \tilde{X}$ is a map with $pf = p$. The deck transformations of a given cover form a group, $G(\tilde{X})$. 

For example, a deck transformation of the standard covering $\R \to S^1$ is a translation by an integer multiple of $2\pi$. We thus have $G(\R) = \Z$ in this case. For the n-sheeted cover $S^1 \to S^1$ we similarly have $G(\R) = \Z / n\Z$. 

A deck transformation is completely determined by its action on $p^{-1}(x_0)$ for a given point $x_0$. This is because of the unique lifting property...

When $G(\tilde{X})$ acts transitively on $p^{-1}(x)$, i.e. for any points $\tilde{x}, \tilde{x}' \in p^{-1}(x)$ there exists a deck transformation taking $\tilde{x}$ to $\tilde{x}'$, we call $\tilde{X}$ a "normal" or "regular" cover of $X$. Normal covers are especially "homogenous": they look the same around each lift $\tilde{x}$ of a point $x$. 

Normal covers correspond to normal subgroups. First we prove a lemma. Let $X$ meet the same conditions as in the Galois correspondence (locally path-connected, etc.). Then for $\tilde{x}_0, \tilde{x}_1 \in \tilde{X}$, there exists a covering transformation $f: \tilde{X} \to \tilde{X}$ mapping $\tilde{x}_0 \to \tilde{x}_1$ if and only if $p_*(\pi_1(\tilde{X}, \tilde{x}_0)) = p_*(\pi_1(\tilde{X}, \tilde{x}_1))$. That is, those subgroups of $\pi_1(X)$ must be not merely isomorphic but equal. 

Proof: we use the lifting criterion for general maps to "lift $p: (\tilde{X}, \tilde{x}_0) \to (X, x)$ to $p: (\tilde{X}, \tilde{x}_1) \to (X, x)$". This says that a lift (which is precisely the $f$ we want) exists if and only if $p_*(\pi_1(\tilde{X}, \tilde{x}_0)) \subseteq p_*(\pi_1(\tilde{X}, \tilde{x}_1))$ and the inverse exists if and only if $p_*(\pi_1(\tilde{X}, \tilde{x}_0)) \supseteq p_*(\pi_1(\tilde{X}, \tilde{x}_1))$. 

Now we show that a cover $p: \tilde{X} \to X$ is normal if and only if, for all $x \in X$ and $\tilde{x}_0, \tilde{x}_1 \in p^{-1}(x)$, we have $p_*(\pi_1(\tilde{X}, \tilde{x}_0)) = p_*(\pi_1(\tilde{X}, \tilde{x}_1)) = \gamma p_*(\pi_1(\tilde{X}, \tilde{x}_0)) \gamma^{-1}$ where $\gamma$ is a path from $\tilde{x}_1$ to $\tilde{x}_0$. ...

