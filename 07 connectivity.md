# Connectivity

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}

\newcommand{\T}{\mathcal T}
\newcommand{\Ext}{\text{Ext}}
\newcommand{\B}{\mathcal B}
$$

## Connectivity

Let $X$ be a topological space. We say $X$ is **disconnected** if there exist two nonempty disjoint open sets $U, V \subseteq X$ so that $X = U \cup V$.

If $X$ is not disconnected, then it is **connected**.

### Clopen subsets

$X$ is connected if and only if the only nonempty subset of $X$ that is both open and closed is $X$ itself.

**Proof.**

($\Rightarrow$) Suppose $X$ is connected. $X$ is a topological space so it is both open and closed.

($\Leftarrow$) Suppose $X$ is disconnected, then there are nonempty open disjoint subsets $U, V$ so that $U \cup V = X$.

Since $U^C = V$, $V^C = U$, and $U, V$ are open, $U, V$ are also closed.

### Images of connected spaces are connected

Let $X$ be a connected space and $f : X \to Y$ be a continuous map. Then $f(X) \subseteq Y$ is connected.

For example, if $Y = \R$ and $p, q \in X$ with $f(p) = a$ and $f(q) = b$. Then $f$ takes on all values $c \in (a, b)$ (this is the Intermediate Value Theorem).

As another example, every quotient of a connected space is connected.

![quotient spaces of square are connected.png](quotient spaces of square are connected.png)

### Properties of connected spaces

1. Suppose $X$ is a topological space and $U, V$ are disjoint open subsets of $X$. If $A$ is a connected subspace of $X$ contained in $U \cup V$ then $A \subseteq U$ or $A \subseteq V$.
2. If $X$ contains a dense connected subspace then $X$ is connected.
3. Suppose $X$ is a topological space and $A \subseteq X$ is connected. Then $\overline A$ is connected, and so is any subspace $B$ with $A \subseteq B \subseteq \overline A$.
4. Let $X$ be a topological space and $\curlies{B_\alpha}_{\alpha \in A}$ a collection of connected subspaces of $X$ with a point in common. Then $\ds \bigcup_{\alpha \in A} B_\alpha$ is connected.

**Proof.**

(1)

![connected subspace of disjoint open sets.png](connected subspace of disjoint open sets.png)

$A \cap U$ and $A \cap V$ are open in $A$.

$A = (A \cap U) \cup (A \cap U^C)$. Since $U$ and $V$ are disjoint and $A \subseteq U \cup V$, $A \cap U^C = A \cap V$.

Thus $A \cap U$ and $A \cap V$ are both open subsets of $A$ and are complements of each other, so they are clopen. SInce $A$ is connected, one of them must be empty, so either $A \cap U = A$ so $A \subseteq U$, or $A \cap V = A$ so $A \subseteq V$.

(4)

Let $\ds p \in \bigcap_{\alpha \in A} B_\alpha$

Suppose $U, V$ are disjoint open sets that disconnect $B = \ds \bigcup_{\alpha \in A} B_\alpha$. This means the sets

$$
U \cap B\text{ and } V \cap B
$$

are nonempty and disjoint, and their union is $B$, and

$$
U \cap V \cap B = \emptyset
$$

since $U$ and $V$ are disjoint.

Then each $B_\alpha \subseteq U$ or $B_\alpha \subseteq V$. However, $p \in B_\alpha$ for every $\alpha$, so $p \in U$ and $p \in V$. This contradicts $U$ and $V$ disconnecting $B$, so $B$ must be connected.

## Path-connectedness

Let $X$ be a topological space. A **path** (or **curve**) in $X$ is a continuous map $\alpha : [0, 1] \to X$.

(Since any interval $[a, b] \subseteq \R$ is homeomorphic to $[0, 1]$, an equivalent definition of a curve is a continuous map $\alpha : [a, b] \to X$.)

We say $\alpha$ is a path between $p \in X$ and $q \in X$ if $\alpha(0) = p$ and $\alpha(1) = q$.

A topological space $X$ is **path connected** if there exists a path between any two points in $X$.

### Path-connected spaces are connected

Let $X$ be a path connected space and suppose $U, V$ are open subsets that disconnect $X$.

Let $u \in U$ and $v \in V$, then let $\alpha$ be a path connecting $u$ and $v$.

$\alpha([0, 1]) \subseteq U \cup V = X$, and it is connected (because it is the image of $[0, 1]$ which is connected). By property (1) proved above, this means that either $\alpha([0, 1]) \subseteq U$ or $\alpha([0, 1]) \subseteq V$, which is a contradiction.

Thus $X$ is connected.

For example, $\R^n$ is connected, as given points $\mathbf x$ and $\mathbf y$ we can construct the path $\alpha(t) = t\mathbf x + (1 - t) \mathbf y$ where $t \in [0, 1]$.

$S^n$ is also connected as given points $\mathbf x$ and $\mathbf y$ we can construct the path $\alpha(t) = cos(t)\mathbf x + sin(t) \mathbf y$ where $t \in [0, 2\pi]$.

### Connected does not imply path connected

![topologists sine curve not path connected.png](topologists sine curve not path connected.png)

## Components

### Path-connected components

Let $X$ be a topological space and let $x, y \in X$.

We say $x \underset{p}{\sim} y$ if there is a path connecting $x$ and $y$.

The equivalence classes defined by this relation are called **path-connected components**.

### Connected components

Let $X$ be a topological space and let $x, y \in X$.

We say $x \underset{c}{\sim} y$ if these exists a connected set $U \subseteq X$ with $x, y \in U$.

The equivalence classes defined by this relation are called **connected components**.

