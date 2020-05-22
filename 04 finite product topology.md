# The (Finite) Product Topology

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}

\newcommand{\T}{\mathcal T}
\newcommand{\Ext}{\text{Ext}}
\newcommand{\B}{\mathcal B}
$$

## The (Finite) Product Topology

Let $X_1, ..., X_n$ be topological spaces.

Let $\B_{X_1 \times ... \times X_n}$ be the collection of subsets of $X_1 \times ... \times X_n$ given by:

$$
\B_{X_1 \times ... \times X_n} = \curlies{ U_1 \times ... \times U_n : U_i \subseteq X_i \text{ is open} }
$$

Then $\B_{X_1 \times ... \times X_n}$ is a basis for $X_1 \times ... \times X_n$, and we call the topology it generates the **Product Topology**.

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

### Projections

We can define some canonical maps, called **projections**:

$$
\begin{align}
\pi_i: &\ X_1 \times ... \times X_n \to X_i \\
&\ (x_1, ..., x_n) \mapsto x_i
\end{align}
$$

Projections are continuous, because if $U_i \subseteq X_i$ is open, then $\pi_i^{-1}(U_i) = X_1 \times ... \times X_{i-1} \times U_i \times X_{i+1} \times ... X_n$ which is open.

## Continuity and projections (Characteristic property of product spaces)

Let $X_1, ..., X_n$ be topological spaces.

*Part 1:*

The product topology on $X_1 \times ... \times X_n$ satisfies $(P_P)$: For any topological space $Y$, a map $f: Y \to X_1 \times ... \times X_n$ is continuous if and only the components $f_i = \pi_i \circ f$ are continuous for each $i \in \curlies{1, ..., n}$.

![image-20200522121523770](/Users/rikin/Documents/School Stuff/2019-2020/mat327/notes/product characteristic property.png)

*Part 2:*

The product topology on $X_1 \times ... \times X_n$ is the only topology that satisfies the characteristic property.

**Proof.**

*Part 1:*

($\Rightarrow$) Suppose $X_1 \times ... \times X_n$ have the product topology.

Let $f: Y \to X_1 \times ... \times X_n$ be continuous. Then each $f_i = \pi_i \circ f : Y \to X_i$ is continuous because it is a composition of continuous functions.

($\Leftarrow$) Suppose each $f_i$ is continuous.

We can prove that $f$ is continuous by proving that the preimage of each basis element of $X_1 \times ... \times X_n$ is open.

Suppose $B \in \B_{X_1 \times ... \times X_n}$, then $B = U_1 \times ... \times U_n$ where each $U_i$ is open.

$$
\begin{align}
f^{-1}(B) &= \curlies{y \in Y : f(y) \in U_1 \times ... \times U_n} \\
&= \curlies{y \in Y : f_1(y) \in U_1, ..., f_n(y) \in U_n} \\
&= \bigcap_{i=1}^n f_i^{-1}(U_i)
\end{align}
$$

This is an intersection of open sets as each $f_i$ is continuous, so it is open. Thus, $f^{-1}(B)$ is open for each $B \in \B_{X_1 \times ... \times X_n}$, so $f$ is continuous.

*Part 2:*

Suppose a topology $\T'$ on $X_1 \times ... \times X_n$ satisfies $(P_P)$.

Claim: $\pi_i : (X_1 \times ... \times X_n, \T') \to (X_i, \T_i)$ is continuous:

Consider $id_{X_1 \times ... \times X_n} : (X_1 \times ... \times X_n, \T') \to (X_1 \times ... \times X_n, \T')$

This is continuous, so by $(P_P)$, each $\pi_i$ is continuous.

![image-20200522123045215](/Users/rikin/Documents/School Stuff/2019-2020/mat327/notes/product char property part 2 proof.png)

Now, we will prove that $\T'$ is the product topology.

![image-20200522123514080](/Users/rikin/Documents/School Stuff/2019-2020/mat327/notes/product char property part 2 proof diagrams.png)

Because the projection $\pi_i : (X_1 \times ... \times X_n, \T') \to (X_i, \T_i)$ is continuous, the identity $id: (X_1 \times ... \times X_n, \T') \to (X_1 \times ... \times X_n, \T_{prod})$ is continuous.

The projection $\pi_i : (X_1 \times ... \times X_n, \T_{prod}) \to (X_i, \T_i)$ is always continuous, so the inverse identity $id^{-1}$ is also continuous.

Identity functions are only homeomorphisms when both spaces have the same topology, so $\T' = \T_{prod}$.

> "In the beginning, they look like black magic!" - Malors, on diagrams

## The product topology is nice

### Associativity of products

If $X_1, X_2, X_3$ are topological spaces, then taking product spaces is associative:

$$
(X_1 \times X_2) \times X_3 = X_1 \times (X_2 \times X_3)
$$

(if each product has its product topology)

**Proof.**

![image-20200522125325392](/Users/rikin/Library/Application Support/typora-user-images/image-20200522125325392.png)

$f_{12}$ and $f_3$ are continuous if and only if $f$ is continuous if and only if $f_1$ and $f_{23}$ are continuous.

> "We want to use diagrams in a way that makes things more clear." - Malors
