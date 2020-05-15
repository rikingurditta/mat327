# Topologies

Topology is the study of shapes.

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\lbrace #1 \rbrace}

\newcommand{\T}{\mathcal T}
\newcommand{\Ext}{\text{Ext}}
\newcommand{\B}{\mathcal B}
$$

## Topology

Let $X$ be a nonempty set. A **topology** $\T$ is a collection of subsets of $X$ such that:

1. $\emptyset, X \in \T$
2. Arbitrary unions: if $U_i \in \T$ then $\ds \bigcup_i U_i \in \T$
3. Finite intersections: if $U_1, ..., U_n \in \T$, then $U_1 \cap ... \cap U_n \in \T$

The sets that belong to $\T$ are called *open sets*.

A topology is a structure that we add to a set to help us study it by understanding which points are "close to" each other

### Examples

- trivial topology: $\T = \curlies{\emptyset, X}$
- discrete topology: $\T = P(X) = \curlies{\text{every subset of X}}$
- if $X = {1, 2, 3}$, we can construct $\T = \curlies{\emptyset, X, \curlies{1}, \curlies{2, 3} }$
- if $X = \R^n$, the usual notion of "openness" works

## Types of sets

If $\T$ is a topology on $X$, we call $(X, \T)$ a **topological space**, and

- an **open set** is an element of $\T$, so $S$ is open if $S \in \T$
- a **closed set** is one whose complement is open, so $S$ is closed if $S^C \in \T$
  - sets can be both open and closed
    - $\emptyset$ and $X$ are both open and closed in every topology
  - sets can also be neither open nor closed

Note that we can equivalently define $\T$ by deciding which subsets of $X$ are closed! Using De Morgan's laws, we can define a topology as a collection of subsets of $X$ such that:

1. $\emptyset, X \in \T$
2. Arbitrary intersections: if $U_i \in \T$ then $\ds \bigcap_i U_i \in \T$
3. Finite unions: if $U_1, ..., U_n \in \T$, then $U_1 \cup ... \cup U_n \in \T$

## A few constructions

Let $(X, \T)$ be a topological space and $A \subseteq X$

### Interior

The interior of a set $A$ is the "biggest" open set contained in $A$

The **interior** of $A$ is defined as

$$
A^O = \bigcup_{U \subseteq A,\ U \text{ is open}} U
$$

This is a union of open sets, so it is open

### Closure

The **closure** of $A$ is defined as

$$
\overline A = \bigcap_{A \subseteq U \subseteq X,\ U \text{ is closed}} U
$$

This is an intersection of closed sets, so it is closed

It is clear that

$$
A^O \subseteq A \subseteq \overline A
$$

### Exterior

The **exterior** of $A$ is defined as

$$
\Ext(A) = X \setminus \overline A
$$

This is the complement of a closed set, so it is open

### Boundary

The **boundary** of $A$ is defined as

$$
\partial A = X \setminus (A^O \cup \Ext(A))
$$

$A^O$ and $\Ext(A)$ are open so $A^O \cup \Ext(A)$ is open, so its complement  $\partial A$ is closed

## Bases

### Bases

Given a topology $\T$ on $X$, a subset $\B \subseteq \T$ is a **basis** for $\T$ if every open set in $\T$ is the union of sets in $\B$, i.e. for all $U \in \T$, then there are $B_i \in \B$ so that $\ds U = \bigcup_{i \in I} B_i$

Forgetting $\T$, we can say $\B$ is a basis for $X$ if:

1. $\ds \bigcup\B = X$
2. for all $B_1, B_2 \in \B$ and all $p \in B_1 \cap B_2$, there exists $B_3 \in \B$ such that $p \in B_3 \subseteq B_1 \cap B_2$

Bases are useful because we can use them to define topologies, so we don't have to describe every open set

We define a collection of subsets

$$
\T_\B = \curlies{U \subseteq X : U \text{ is the (arbitrary) union of some elements of } \B}
$$

Then $\T_\B$ is a topology. To prove this, we need to show that it satisfies the conditions on topologies:

1. $\emptyset, X$
   - $\emptyset$ is the union of no elements of $\B$, so $\emptyset \in \T_\B$
   - $X$ is the union of all elements of $\B$, so $X \in \T_\B$
2. Arbitrary unions
   - suppose a family of sets $T_i \in \T_\B$, then each $\ds T_i = \bigcup_{j \in J_i} B_j$ for some indexing set $J_i$, so if $\ds J = \bigcup_i J_i$ then $\ds \bigcup_i T_i = \bigcup_{j \in J} B_j$ which is the union of elements of $\B$, so $\ds \bigcup_i T_i \in \T_\B$
3. Finite intersections
   - it is enough to prove that an intersection of two elements  of $\T_\B$ is also in $\T_\B$, since we can construct a finite intersection by pairs of intersections (intersections are associative)
   - suppose $\ds U = \bigcup_i B_i,\ V = \bigcup_j B_j$
   - then $\ds U \cap V = \bigcup_i B_i \cap \bigcup_j B_j = \bigcup_{i, j}(B_i \cap B_j)$
   - we know each $B_i \cap B_j$ is in $\T_\B$ because it can be expressed as $\ds \bigcup_{p \in B_i \cap B_j} B_p$ where each $B_p \subseteq B_i \cap B_j$ and contains $p$ (possible because of property 2 of bases)
   - thus, $U \cap V$ is the union of sets in $\T_\B$, so it is also an element of $\T_\B$

Thus, every basis $\B$ for $X$ is the basis of a topology $\T_\B$ for $X$

#### Example

A metric space is a pair $(M, d)$ where $M$ is a set and $d: M \times M \to \R_{\geq 0}$ is a distance function, i.e.

1. $d(x, x) = 0$
2. $d(x, y) = d(y, x)$
3. $d(x, z) \leq d(x, y) + d(y, z)$ (triangle inequality)

We can define "open balls"

$$
B_\epsilon(p) = \curlies{x \in M : d(x, p) < \epsilon}
$$

and a basis using them:

$$
\B = \curlies{B_\epsilon(p) : \epsilon \in \R^+ \text{ and } p \in M}
$$

##### The usual topology of $\R^n$

This, constructed in $\R^n$ with Euclidean distance, is the usual topology that we are used to.

##### The trivial metric

The trivial metric on any space is the one with distance function

$$
d(x, y) = \begin{cases} 0 & x = y \\ 1 & x \neq y \end{cases}
$$

If $\epsilon > 0$, then this the open ball topology on the space is the same as the discrete topology!

### Local bases

Given $p \in X$, a basis $\B_p$ around $p$ is a collection of open sets such that $\forall U$ where $p \in U$, there is a $B \in \B$ so that $p \in B \subseteq U$

#### Countability

$(X, \T)$ is **first countable** if there exists a countable basis around each point

- "Things that are not first countable are very bad." - Malors Espinosa

$(X, \T)$ is **second countable** if $\T$ has a countable basis

(There is something kind of in between first and second countability (compact spaces), but some machinery is required to understand them)

##### Second countable implies first countable

Suppose $(X, \T)$ is second countable, then there is a basis $\B = \curlies{B_1, B_2, B_3, ...}$

let $p \in X$ be any point, let $U \subseteq X$ be an open set where $p \in U$

since $\B$ is a basis, $U$ can be written as a union of elements of $\B$, so

$$
U = \bigcup_{i = 1}^\infty B_i
$$

then there must be an $i \in \N$ so that $p \in B_i$

then $\B_p = \curlies{B \in \B : p \in B}$ is a local basis around $p$, and it is a subset of $\B$ so it is countable

### Comparing bases

#### When do two bases generate the same topology?

$\B_1$ and $\B_2$ generate the same topology if for all $B \in \B_1$, there are sets $B_i \in \B_2$ so that $\ds B = \bigcup_i B_i$, and vice versa interchanging $\B_1$ and $\B_2$.

To prove this, suppose for every $B \in \B_1$, there are $B_i \in \B_2$ so that $\ds B = \bigcup_i B_i$

Let $U \in \T_{\B_1}$, then $\ds U = \bigcup_j B_j$ where each $B_j \in \B_1$

Then $\ds U = \bigcup_j \bigcup_{i \in I_j} B_i$ which is a union of elements of $\B_2$, so $U \in \T_{\B_2}$

Therefore, $\T_{\B_1} \subseteq \T_{\B_2}$

Doing the same thing but replacing $\B_1$ with $\B_2$, we can find that $\T_{\B_2} \subseteq \T_{\B_1}$, therefore $\T_{\B_1} = \T_{\B_2}$