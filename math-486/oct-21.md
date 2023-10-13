Prior to the advent of computers, programming referred to optimization problems in operations research. That's why dynamic programming, linear programming, and non-linear programming all refer to optimization problems from the 1930s and 1940s.

A linear program, or LP, is in max form if it is written:

max $c_1x_1 + \ldots + c_nx_n$

such that 
$a_{1,1}x_1 + \cdots a_{1,n}x_n \leq b_1$
$\vdots$ 
$a_{m, 1}x_1 + \cdots + a_{m,n}x_n \leq b_n$ 

for which $x_1, \ldots, x_n \geq 0$.

We wrote this in vector notation last time.

> [!warning]
> everything past this point is pretty much just a guess of what's happening
> 
> the good news is this is not required to learn



**????** In other words, this is the max (??) leq all values geq 0.

Also last time, we remarked that any maximization LP could be rewritten as a different LP in max form.

Now, suppose that we have a max linear program with equivalent LP in max form:

$$Z^{\star} = \max_{\underline{X} \in \mathbb{R^{n}}} \underline{C}^{T}\underline{X}$$
such that $A\underline{x} \leq \underline{b}$ and $\underline{x} \geq 0$.

with $n$ variables over $m$ constraints, then the dual linear program of the LP above is given by

$$W^{\star} = \min_{\underline{y} \in \mathbb{R}^n} \underline{b}^T \underline{y}$$
such that $A^{T} \underline{y} \geq \underline{C}$ and $\underline{y} \geq \underline{0}$.

By the duality theorem, it holds that if $Z^{\star}$ exists and is finite, then $W^{\star}$ also exists, with $W^{\star} = Z^{\star}$. 

We return to the matrix game. Assume that we are given an $m \times n$ matrix game $A$.

We can write player 1's min-max problem as the safety level for player 1, letting the maximizing mixed strategy be $p$ for player 1 and the minimizing mixed strategy be $q$ for player 2:

$$
\begin{align}
\underline{V} &= (\underline{p})(\underline{q}) \sum_{i=1}^{m}\sum_{j=1}^{n} a_{ij}p_iq_j\\
&= (\underline{p})(\underline{q}) \sum_{i=1}^{m}\sum_{j=1}^{n} a_{ij}p_iq_j\\
&= (\underline{p}) \min_{j=1,\ldots,n} \sum_{i=1}^{m} a_{ij}p_i

\end{align}
$$

We can allow the summation to simplify because remember that the $q_j$s are all unit vectors, noting that $\underline{q} = (1, 0, \ldots, 0)$.

Now, it turns out that this can be expressed as the linear program 

$\max \underline{p}$  
such that
$p_1 + \ldots + p_m = 1$
$p_1, \ldots, p_m \geq 0$

where $\underline{p}$ is applied to 
$$\left(\min_{j=1,\ldots,n}\sum_{i=1}^{m}a_{ij}p_i\right)$$

We now define a new variable $p_0$, where we allow 
$$p_0 =\left(\min_{j=1,\ldots,n}\sum_{i=1}^{m}a_{ij}p_i\right)$$
Then, player 1's maximin problem becomes

$\underline{V} = \max p_0, p_1, \ldots, p_m$ 

such that
$$p_0 =\left(\min_{j=1,\ldots,n}\sum_{i=1}^{m}a_{ij}p_i\right)$$
$p_1 + p_2 \ldots + p_m = 1$
$p_1, p_2, \ldots, p_m, \geq 0$

The problem lies in the fact that the first constraint is nonlinear. But everything else *almost* comprises an LP - and we want an LP, since we have a variety of algorithms that solve these questions really quickly.

Now, suppose that we loosen the contraints by only requiring that 
$$p_0 \leq \sum_{i=1}^{n}a_{ij}p_{i}$$

or all $j$, instead of the "original" $p_0 =\left(\min_{j=1,\ldots,n}\sum_{i=1}^{m}a_{ij}p_i\right)$. 

Now, a tautology is that if $p_0$ is a minimum over the summation (in the original expression), then obviously it is less than (or equal to) each of the individual terms. 

So consider the fact that

$$\underline{V} = \max_{p_0, p_1, \ldots, p_m}$$
such that 
$$p_0 \leq \sum_{i=1}^{m} a_{ij}p_{i}\,\text{for}\, j=1,\ldots,n$$
(that is, $p_0$ is smaller than every individual element in the sum)
$$p_1 + \cdots + p_n = 1$$
$$p_1, \ldots, p_n \geq0$$

Since the objective function here is to maximize $p_0$, and $p_0$ only occurs in constraint 1, we notice that the optimal $p_0$ will occur at 

$$p_0 = \min_{j=1, \ldots, n} \sum_{i=1}^{m}a_{ij}p_{i}$$
Therefore, our "almost-a-linear-program" LP and the above LP are equivalent, in that the same result of $p_0, \ldots, p_n$ will yield the same value of $\underline{V}$.

---

In conclusion, the problem of finding minimax strategies for player 1 can be phrased as an LP,

$$\underline{V} =\max_{p_0, \ldots, p_m} p_0$$
such that 
$$p_0 - \sum_{i=1}^{m}a_{ij}p_i \leq 0 \,\text{for}\, j = 1, \ldots, n$$
$$p_1 + p_2 + \cdots + p_n = 1$$
$$p_1, \ldots, p_n \geq 0$$
with $p_0$ unrestricted.

---

## Proof of the minimax theorem
Again, the minimax theorem states that if a two-person zero-sum game has a finite number of pure strategies for both players, then $\underline{V} = \overline{V}$; that is, the game has a value.

One proof is Owen's proof of the minimax theorem, on p.2.29 of Shapley.

Another proof is that we can switch the roles of the players to write

$$\overline{V} = \min_{q_0, q_1, \ldots, q_n} q_0$$
such that
$$q_0 - \sum_{j=1}^{n}a_{ij}q_j \geq 0 \text{ for } i = 1, \ldots, n$$

$$q_1 + q_2 + \ldots +q_n = 1$$
$$q_1, \ldots, q_n \geq 0$$
and $q_0$ is unrestricted.

It can be shown that this linear program is in fact the dual linear program to the linear program we found for player 1 earlier. By the duality theorem, their optimal objective function values are the same - $\underline{V} = \overline{V}$. 

Proving the minimax theorem is often said to be one of the shining applications of the duality theorem.

---

## Bimatrix games - Chapter 3

Here, we consider two person games in strategic form, but we no longer assume the zero-sum property. Thus, when we specify such a game, we have to specify two quantities per cell. 

We can take the prisonners' dilemma, which we know to not be zero-sum.

Its strategic form 

| $_I\text{\\}^{II}$ | C            | NC        |
| ------------------ | ------------ | --------- |
| **C**              | (-12, -12) | (0, -24) |
| **NC**             | (-24, 0)    | (-6, -6)  |

is often written as the two matrices 
$$A = 
\left[\begin{matrix}
-12 & 0 \\
-24 & -6 \\
\end{matrix}\right]$$
and
$$B = 
\left[\begin{matrix}
-12 & -24 \\
0 & -6 \\
\end{matrix}\right]$$
