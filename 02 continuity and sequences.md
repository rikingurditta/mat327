# Continuity and Sequences

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\lbrace #1 \rbrace}

\newcommand{\T}{\mathcal T}
\newcommand{\Ext}{\text{Ext}}
\newcommand{\B}{\mathcal B}
$$

## Continuity

Let $X$ and $Y$ be topological spaces, and $f: X \to Y$. We say $f$ is **continuous** if for every open set $V \subseteq Y$, $f^{-1}(V) \subseteq U$ is open.

Why this definition?

- in short, because it wokrs without additional assumptions
- Related definition: Open functions
- let $X$ and $Y$ be topological spaces, and $f: X \to Y$. $f$ is **open** if it preserves openness, aka for all open sets $U \subseteq X$, $f(U) \subseteq Y$ is open.
  - (similarly, a **closed function** preserves closedness)
- This is not really what we want for continuity! It doesn't necessarily work out.

#### Proposition: $f: X \to Y$ is continuous iff for every closed $C \subseteq Y$, $f^{-1}(C) \subseteq X$ is also closed

($\Rightarrow$) Suppose $f$ is continuous, $C \subseteq Y$ is closed, then $C^C$ is open. Then $f^{-1}(C^C)$ is open. $f^{-1}(C^C)^C$ is closed, and $f^{-1}(C^C)^C = f^{-1}(C)$, so $f^{-1}(C)$ is closed.

($\Leftarrow$) Suppose for every closed set $C \subseteq Y$, $f^{-1}(C)$ is closed. Then we can do the previous proof in reverse to find that $f$ is continuous.

### Continuity and bases

If $f: X \to Y$ is a function and $\B$ is a basis for $Y$, then $f$ is continuous iff $f^{-1}(B)$ is open for every $B \in \B$.

($\Rightarrow$) Suppose $f$ is continuous. Then for each $B \in \B$, $B$ is open so $f^{-1}(B)$ is open.

($\Leftarrow$) Suppose for every $B \in \B$, $f^{-1}(B)$ is open. Suppose $U \subseteq Y$ is open, then $\ds U = \bigcup_{i \in I} B_i \text{ where } B_i \in \B$. Then,

$$
f^{-1}(U) = f^{-1}\left(\bigcup_{i \in I} B_i\right) = \bigcup_{i \in I} f^{-1}(B)
$$

Thus, $f^{-1}(U)$ is the arbitrary union of open sets, so it is open. Since $U$ is arbitrary, this is true for every open $U$.

#### Example: metric spaces

Let $(X, d_X)$ and $(Y, d_Y)$ be metric spaces with their metric topologies, and $f: X \to Y$ be a map between them.

Using the proposition above, we know that $f$ is continuous iff the preimage of every open ball is open.

To specify a ball, we need to present a centre $y \in Y$ and a radius $\epsilon \in \R^+$

so $f$ is continuous iff for every ball $B_\epsilon(y) \subseteq Y$, $f^{-1}(B_\epsilon(y)) \subseteq X$ is open. $f^{-1}(B_\epsilon(y))$ is open if it is the union of open balls in $X$, aka if there is an open ball around every point in $f^{-1}(B_\epsilon(y))$.

Thus, $f$ is continuous iff for every $y \in Y$, $\epsilon \in \R^+$, and every point $x \in f^{-1}(B_\epsilon(y))$, there is a $\delta \in \R^+$ so that $B_\delta(x) \subseteq f^{-1}(B_\epsilon(y))$, aka $f(B_\delta(x)) \subseteq B_\epsilon(y)$.

## Sequences

**Definition.** Let $X$ be a topological space and $A \subseteq X$ be any subset. $p \in X$ is an **accumulation point** or **limit point** if every neighbourhood of $p$ has a point in $A$ different from $p$.

**Definition.** Let $X$ be a topological space and $x_1, x_2, x_3, ...$  be a sequence of points in $X$. $x \in X$ is **a limit** of the sequence iff for every neighbourhood $U$ of $x$ there exists an $N \in \N$ such that if $n \geq N$, then $x_n \in U$.

Note that $x$ is *a* limit, not necessarily *the* limit of the sequence, because a sequence may have multiple limits in some topological spaces.

#### Unique convergence in metric spaces

Let $(X, d)$ be a metric space, and $x_1, x_2, x_3, ...$ be a sequence with $x_i \to x$ and $x_i \to y$, then $x = y$.

**Proof.** Suppose $x \neq y$, then if $r = \vert x - y \vert / 2 \neq 0$, then $B_r(x)$ and $B_r(y)$ are disjoint.

If $x_i \to x$, then since $x \in B_r(x)$, there exists $N \in \N$ such that if $n \geq N$, then $x_n \in B_r(x)$, so $x_n \notin B_r(y)$.

Then it is clear that we cannot say that an infinite tail of the sequence can be contained in $B_r(y)$, so $x_i \not \to y$, which is a contradiction. Thus, $x = y$.

Note that this proof hinges on the ability to find disjoint open balls containing $x$ and $y$!

### Hausdorff spaces

A topological space $X$ is **Hausdorff** if for every $x, y \in X$ where $x \neq y$, we can find open sets $U, V \subseteq X$ where $x \in U$, $u \in V$, and $U \cap V = \emptyset$.

Limits are unique in Hausdorff spaces! This can be shown by slightly modifying the proof above for metric spaces.

Even though non-Hausdorff spaces seem pathological, they arise naturally in some areas (e.g. algebraic geometry).

##### In Hausdorff spaces, singleton sets, i.e $\curlies{p}$, are closed

If $X$ is Hausdorff, every $q \neq p$ has a neighbourhood disjoint of $p$, so $\curlies{p}^C$, the union of all of these, is open.

### Theorem about limits

Let $X$ be a first countable topological space, let $A \subseteq X$ be any subset and $x \in X$.

1. $x \in \overline A$ iff $x$ is a limit of a sequence of points in $A$
2. $x \in A^O$ iff every sequence in $X$ converging to $x$ is eventually in $A$
3. $A$ is closed in $X$ iff $A$ contains every limit of every convergent sequence of points in $A$
4. $A$ is open in $X$ iff every sequence in $X$ converging to a point of $A$ is eventually in $A$

**Proof of 1:**

($\Rightarrow$) We know $\overline A = A \cup \partial A$, so if $x \in \overline A$ then $x \in A$ or $x \in \partial A$.

Suppose $x \in A$, then $x$ is the limit of the sequence $x, x, x, ...$

Suppose $x \in \partial A$ but $x \notin A$, then since $X$ is first countable, there exists a nested countable basis at $x$: $U_1 \supseteq U_2 \supseteq U_3 \supseteq ...$ where each $U_i$ is open and contains $x$. Since $x \in \partial A$, for each $n \in \N$, $U_n \cap A \neq \emptyset$ , so we can construct a sequence $\curlies{x_n}$ by choosing each $x_n \in U_n \cap A$. Clearly this sequence converges consists of points in $A$ and converges to $x$.

($\Leftarrow$) Suppose $x \notin \overline A$, then $x \in \Ext(A)$, and $x_1, x_2, x_3, ...$ is a sequence of points in $A$.

$\Ext(A)$ is open and does not intersect $A$, so there is an open set $U \subseteq \Ext(A)$ where $x \in U$. For this $U$, there is no subsequence of $\lbrace x_n \rbrace$ that is eventually contained in $U$, so $\lbrace x_n \rbrace$ does not converge to $x$.

Note that this direction did not use first countability! So we know that limits of sequences in $A$ are always trapped in $\overline A$ in every topological space. However, the opposite direction is not true in general, and is pretty much a characterization of first countable spaces.

**Proof of 3:**

($\Rightarrow$) Suppose that $A$ is closed. If $x_n \to x$ with each $x_n \in A$, then by statement 1, $x$ is a limit of point of $A$

...

($\Leftarrow$) $A \subseteq \overline A$ so we only need to show that $\overline A \subseteq A$.

...

### Continuity and sequence convergence

Let $X$ and $Y$ be topological spaces with $X$ first countable and $f: X \to Y$. Then $f$ is continuous iff $x_n \to x$ implies that $f(x_n) \to f(x)$.

**Proof.**

($\Rightarrow$) Suppose $x_n \to x$ implies $f(x_n) \to f(x)$.

Let $C \subseteq Y$ be a closed set. We will use part 3 of the previous proof.

Let $a_1, a_2, ... \in f^{-1}(C)$ with $a_i \to a$. By hypothesis, $f(a_i) \to f(a)$. Moreover, $f(a_i) \in C$, so $f(a) \in \overline C = C$ since $C$ is closed. Thus, $a \in f^{-1}(C)$.

By part 3 the previous proof, we know that $f^{-1}(C)$ is closed. Therefore, $f$ is continuous.

## Homeomorphisms

Let $X$ and $Y$ be topological spaces, and $f: X \to Y$ a bijection between them. Then $f$ is a **homeomorphism** if both $f$ and $f^{-1}$ are continuous.

- There exist continuous bijections whose inverses are not continuous!
- e.g. if $f : (X, \T_{discrete}) \to (X, \T_{trivial})$ is the identity map, then $f$ is continuous but its inverse is not!

### Covers

Let $X$ be a topological space and $A = \lbrace A_\alpha \rbrace_{\alpha \in I}$ be a collection of subsets of $X$. Then $A$ is a **cover** of $X$ if

$$
X = \bigcup_{\alpha \in I} A_\alpha
$$

- If $A_\alpha$ is open for each $\alpha \in I$, then $A$ is an **open cover**. We similarly define a **closed cover**. Bases are an example of open covers.
- We care about covers because they sometimes help us to examine local properties.
- Given a cover $A = \lbrace A_\alpha \rbrace_{\alpha \in I}$ of $X$ and a subset $J \subseteq I$, $B = \lbrace A_\beta \rbrace_{\beta \in J}$ is a **subcover** if $B$ is also a cover of $X$.
- Given two covers $A = \lbrace A_\alpha \rbrace_{\alpha \in I}$ and $B = \lbrace B_\beta \rbrace_{\beta \in J}$, $A$ is a **refinement** of $B$ if for all $\alpha \in I$, there exists $\beta \in J$ such that $A_\alpha \subseteq B_\beta$.
- Notice that subcovers are refinements.