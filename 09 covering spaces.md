# Covering Spaces

$$
\newcommand{\ds}{\displaystyle}
\newcommand{\curlies}[1]{\left\lbrace #1 \right\rbrace}

\newcommand{\T}{\mathcal T}
\newcommand{\Ext}{\text{Ext}}
\newcommand{\B}{\mathcal B}
\newcommand{\C}{\mathbb C}
$$

## The lifting problem

Consider the complex plane $\C$ with the following equivalence relation:

$$
z \sim w \text{ if } z - w = a + bi, \text{ where } a, b \in \Z
$$

The resulting space is homeomorphic to the torus

![torus equivalence relation on C.png](torus equivalence relation on C.png)

...

## Covering spaces

Let $E, X$ be topological spaces where $X$ is path-connected and $q: E \to X$ be a surjective continuous map between them. $q$ is a covering map and $E$ is a covering space of $X$ if for every point $x \in X$, there is an open neighbourhood $V$ of $x$ and a countable number of disjoint open sets $U_1, U_2, U_3, ... \subseteq E$ so that for each $U_i$, $q|_{U_i} : U_i \to V$ is a homemorphism.

(Note that $\curlies{U}_i$ being countable is not always required.)

 ![covering space curve local homeomorphisms.png](covering space curve local homeomorphisms.png)

### Lifting curves

Let $q: E \to X$ be a covering map, $x \in X$ any point, and $\alpha: [0, 1] \to X$, $\alpha(0) = X$ be any curve. Let $e \in E$ be a  point so that $q(e) = x$. Then there exists a *unique* curve $\tilde\alpha: [0, 1] \to E$ so that $q \circ \tilde \alpha = \alpha$ and $\tilde \alpha(0) = e$.

![lifting curve commutative diagram.png](lifting curve commutative diagram.png)

### Example: Root functions on $\mathbb C$

Consider $\C^* = \C \setminus \curlies 0$, and define

$$
\begin{align}
\rho_n:\ &\C^* \to \C^* \\
&z \mapsto z^n
\end{align}
$$

​	This map is not a bijection, but we can choose a "branch" of its inverse.

![c remove half line continuous square root.png](c remove half line continuous square root.png)

