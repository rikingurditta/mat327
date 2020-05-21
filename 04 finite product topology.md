# The Finite Product Topology

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}

\newcommand{\T}{\mathcal T}
\newcommand{\Ext}{\text{Ext}}
\newcommand{\B}{\mathcal B}
$$

## The Finite Product Topology

Let $X_1, ..., X_n$ be topological spaces.

Let $\B_{X_1 \times ... \times X_n}$ be the collection of subsets of $X_1 \times ... \times X_n$ given by:

$$
\B_{X_1 \times ... \times X_n} = \curlies{ U_1 \times ... \times U_n : U_i \subseteq X_i \text{ is open} }
$$

Then $\B_{X_1 \times ... \times X_n}$ is a basis for $X_1 \times ... \times X_n$.

**Proof.**

1. Basis covers the space

   $X_1 \times ... \times X_n \in \B_{X_1 \times ... \times X_n}$, so $\ds \bigcup \B_{X_1 \times ... \times X_n} = X_1 \times ... \times X_n$

2. Points in intersections have basis elements surrounding them

Let $U = U_1 \times ... \times U_n$ and $V = V_1 \times ... \times V_n$ be elements of $\B_{X_1 \times ... \times X_n}$, then
$$
\begin{align}
U \cap V &= (U_1 \times ... \times U_n) \cap (V_1 \times ... \times V_n) \\
&= (U_1 \cap V_1) \times ... \times (U_n \cap V_n)
\end{align}
$$

Intersections of open sets are open, so $U \cap V$ is the product of open sets, so $U \cap V \in \B_{X_1 \times ... \cap X_n}$. Thus, every element in $U \cap V$ has an open ball around it contained in this intersection, $U \cap V$ itself.

Since $\B_{X_1 \times ... \times X_n}$ satisfies these two properties, it is a basis.

## Projections

We can define some canonical maps:

$$
\begin{align}
\pi_i: &\ X_1 \times ... \times X_n \to X_i \\
&\ (x_1, ..., x_n) \mapsto x_i
\end{align}
$$

### Continuity and projections (Characteristic property of product spaces)

Let $X_1, ..., X_n$ be topological spaces.

*Part 1:*

The product topology on $X_1 \times ... \times X_n$ satisfies $(P_P)$: For any topological space $Y$, a map $f: Y \to X_1 \times ... \times X_n$ is continuous if and only if $f_i = \pi_i \circ f$ is continuous for each $i \in \curlies{1, ..., n}$.

*Part 2:*

The product topology on $X_1 \times ... \times X_n$ is the only topology that satisfies the characteristic property.
