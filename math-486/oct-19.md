Wednesday, November 2 for the midterm.

We move back to our definition of essential submatrices.

> [!abstract] Essential submatrices
> An **essential submatrix** of a matrix game $A$ is a submatrix of $A$ that satisfies the following properties:
> 1. it is square, with dimensions $k \times k$
> 2. it is considered a game in itself, with unique equalizing minimax strategies for each player
> 3. these equalizing strategies, extended by 0s if necessary, are minimax strategies for $A$ itself

Also, note that:
- In the case $k=1$, the cell represents a saddle point in the original matrix $A$.
- Every matrix game contains at least 1 essential submatrix.
- It is possible for a matrix game to have more than one essential submatrix.

For example, take the game $A = \left[\begin{matrix}1&5 \\ 4&4\end{matrix}\right]$.

Suppose that we claim the following matrix is an essential submatrix:

|     | **a**   |
| --- | --- |
| **2**   | 4   |

To demonstrate this is indeed an essential submatrix:
- It is indeed square, $1 \times 1$.
- Trivially, it is a game in itself.
- $p = 1$, or playing strategy 2 all the time, and $q = 1$, or playing strategy A all the time, are unique equalizing minimax strategies.
- The corresponding strategy in $A$, $S_{I}^{\bigstar} = (0, 1)$ and $S_{II}^{\bigstar} = (1, 0)$, are minimax for $A$.

Additional, suppose we claim that $A$ itself is an essential submatrix. The first condition holds - in this case, it is square with $k = 2$.

Regarding the second condition, we can use the separated diagonals formula to find that $p = (0, 1)$ and $q = (\frac{1}{4}, \frac{3}{4})$. These are unique equalizing minimax strategies for the players.

> [!danger] Minimax strategies vs. equalizing minimax strategies
> It is important to note that there are many minimax strategies for $A$, but there exists only one pair of **equalizing** minimax strategies. Yes, it's true that both 4s in this game are saddle points, constituting minimax strategies. But they're not equalizing, which is why we use the case of separated diagonals here.
>
> As a sidenote, notice this falls in both case 1 and case 2 for $2 \times 2$ matrix games because of the equal-valued cells.

And of course, this vacuously holds - there is no extension to consider, since we've proved this for $A$ itself.

---
We have an interesting remark:

> [!note] Remark
> **Almost all** matrix games have exactly one essential submatrix. In other words, if we randomly generate the entries to the cells of a matrix, the probability that the resulting matrix game has exactly one essential submatrix is 100%, or 1. 

You may be wondering what we mean by "almost all" being equal to 100%. It's something that happens with 100% probability, but still might not happen. That is, the physical case in which it's possible still exists, but it occurs with 0% probability.

Suppose we pick a random number on the number line between 0 and 1. What is the probability we get exactly $\frac{\pi}{4}$? It's 0, but because $0 \leq \frac{\pi}{4} \leq 1$, it's still a physical possibility and is contained in the continuous sample space. On the other hand, getting $2$ is just flat out impossible - it is not contained in the continuous sample space. 

How do we validate this remark?

If no entry repeats in a $2 \times 2$ game - that is, no two cells are equal to each other - then there is only one essential submatrix.

Now, suppose that $a \sim \cup (0, 1)$, $b \sim \cup (0, 1)$, $c \sim \cup (0, 1)$, and $d \sim \cup (0, 1)$ random variables. Can we see that the probability is 100% that no entry repeats? Well, the probability that these match is 0% - there's an infinite set of numbers between 0 and 1; so it holds that no entry repeats 100% of the time.

Therefore, it is physically possible to have more than 1 essential submatrix, but it happens with probability 0. 

Another remark:
> [!note] Remark
> In the case where there exists more than one essential submatrix - which occurs 0% of the time - the set of all minimax strategies for a player is precisely the set of convex combinations (weighted averages) of their equalizing strategies from the essential submatrices, extended by 0s if needed.

For example, for the game $A = \left[\begin{matrix}1&5 \\ 4&4\end{matrix}\right]$, we noted that there are exactly two essential submatrices. One is

|     | **a**   |
| --- | --- |
| **2**    | 4    |

for which the **equalizing strategy in this essential submatrix** extended to $A$ is $S_{I} = (0, 1)$ and $S_{II} = (1, 0)$. This is equalizing for player I (but not for player II), and minimax strategies for both.

The other is $A$ itself, with $S_{I} = (0,1)$ and $S_{II} = (0.25, 0.75)$. Necessarily, as an essential submatrix, these are equalizing strategies for both players; and therefore equalizing strategies in $A$, as well. 

So importantly, the *set* of player 1's **minimax** strategies is just $\{(0, 1)\}$.

But the set of all **minimax** strategies for player 2 is the set of all weighted averages of $q^{\star} = (1,0)$ and $q^{\star \star} = \left(\frac{1}{4}, \frac{3}{4}\right)$. And of course, you can take an infinite number of weighted averages between these two points; they form a line segment when plotted that looks like

![[Oct 19 2022-10-19 11.36.08.excalidraw]]

such that the set of all minimax strategies for player 2 is the line segment $\overline{AB}$.

## Solving the general $m \times n$ matrix game and a proof of the minimax theorem

> [!info]
> The following section requires the knowledge of the theorey of linear programming, so students are not responsible for learning this. That said, MATH 487/687 and MATH 751 are discrete mathematics classes that address this theory.

We begin with a brief introduction to linear programming - enough to demonstrate the minimax theorem.

A linear program, abbreviated LP, is the problem of optimizing a linear (or *affine*, which means it doesn't go through the origin) function subject to linear constraints. 

For example, consider where we want to find the maximum of $x_1 + 2x_2$ such that the following hold:

$$
\begin{align}
x_1 &\leq 5\\
13x_1 -2x_2 &\geq 10 \\
5x_1 + 5x_2 &= 30
\end{align}
$$

and $x_1 \geq 0$ and $x_2$ unrestricted. (Original terminology on board was "unr.")

We refer to $x_1+2x_2$ as the **objective function**. Notice that the constraints have non-strict inequality; this is because this allows us to get a closed set, which is importnat.

Another example is finding the minimum of $x-5$ such that

$$
\begin{align}
y+z-x &\geq 5\\
6y+7z+x &= 8\\
y - x &= 9 \\
\end{align}
$$
where $x, y, z \geq 0$.

LPs are relatively easy to solve in that we have several good algorithms to solve them, including the simplex algorithm, the ellipsoid algorithm, and Karmarkar's method.

> [!note] Remark
> Any maximation LP can be recast as an equivalent linear program in what is referred to as **max form**; that is, a max LP in which all constraints are $\leq$ and all variables are nonnegative.

This looks like finding the maximum of $c^{T} x$ such that:

$$\begin{align}
Ax \leq b \\
x \geq 0
\end{align}$$

where
$x \in \mathbb{R}^n$, $c \in \mathbb{R}^n$, $b \in \mathbb{R}^m$, and $A$ is an $m \times n$ matrix. ($n$ is the number of rows, $m$ is the number of columns).

Now, suppose we have a linear program with an equivalent LP in max form.

