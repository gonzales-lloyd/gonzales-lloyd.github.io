Last time, we noted two things:
- In general bimatrix games, a Nash equilibrium does not necessarily imply a minimax solution and vice versa.
- It's pretty easy to find minimax solutions in bimatrix games - just split the games, treat them as zero-sum games, and work accordingly.

Additionally, in bimatrix games, it is **not** true that the probability that a game has multiple Nash equilbria is zero. To show this, consider 

|     | a      | b      |
| --- | ------ | ------ |
| 1   | (a, b) | (c, d) |
| 2   | (e, f) | (g, h)       |

where $a, \ldots, h$ are independently identically distributed uniform random variables from 0 to 1. Then the probability that all of $a, b, g, h \gt \frac{1}{2}$ and all of $c, d, e, f \lt \frac{1}{2}$ is $\frac{1}{2^8} = \frac{1}{256}$. This is small, but nonzero.

Now, notice that because because the payoff $(a,b)$ is a maximum against both strategies 1b and 2a, its strategies (1a) consitute a Nash equilbrium. Likewise, $(g, h)$ is a maximum against both strategies 1b and 2a, so it is also a Nash equilibrium. And finally, it holds that both players can play their strategies half the time to yield an NE as well.

There are actually three NEs in this bimatrix game, demonstrating that there exists a nonzero probability for multiple NEs in a bimatrix game, unlike a matrix game.

---

We can find NEs in $m \times n$ bimatrix games for $m,n \leq 3$ (and we can find them for the general case as well, though we won't cover it in this class).

First, let's consider diagramming mixed strategies for a given player if the number of their pure strategies is less than or equal to 3.

If a player has two pure strategies, then their mixed strategies are of the form $(p_1, p_2)$ where $p_1 + p_2 = 1$ and $p_1, p_2 \geq 0$. Again, recall that we can graph this as 

![[Oct 26 2022-10-26 11.17.45.excalidraw]]

And since we have a line, we can graph this in one dimension instead:
![[Oct 26 2022-10-26 11.18.48.excalidraw]]

where the dashed line indicates the set of all strategies where $p_1 \leq \frac{1}{3}$; that is, pure strategy 1 is played less than or equal to one-thirds of the time.

Then it holds that every mixed strategy can be represented as a point in the line segment. Inequalities like $p_1 \leq \frac{1}{3}$ can be represented as subsegments of the entire line segment.

What about the case where somebody has three pure strategies? Then, their mixed strategies are of the form $p = (p_1, p_2, p_3)$, where $p_1+p_2+p_3 = 0$ and $p_1, p_2, p_3 \geq 0$.

We can diagram this on three axes as shown:
![[Oct 26 2022-10-26 11.22.23.excalidraw]]

and it holds that you can transfer this planar simplex to two dimensions:
![[Oct 26 2022-10-26 11.25.57.excalidraw]]

And it holds that all mixed strategies are represented by points on the simplex. Equations such as $p_1 + p_3 = \frac{1}{4} \implies p_2 = \frac{3}{4}$ are represented by line segments. Additionally, we can represent inequalities such as $p_1 + p_3 \geq \frac{1}{4}$ as two-dimensional regions within the simplex:

![[Oct 26 2022-10-26 11.31.01.excalidraw]]

Moving back to the problem, let us state a definition:

> [!info] Definition
> Given any (mixed)strategy $p$ for player 1, define $\mathcal{I}^*(p)$ as the set of pure strategies $*$ which maximize $\sum_{i=1}^{m}b_{ij}p_i$.
> 
> In other words, given any mixed strategy $p$ for player 1, $\mathcal{I}^*(p)$ is the set of best pure strategy responses for player 2 against $p$. Similarly, define $\mathcal{J}^*(p)$ as the set of best pure strategy responses for player 1 against mixed strategy $q$. 

> [!warning] Difference in notation
> Quint underlines/underbars $\underline{p}$ and $\underline{q}$ to denote it's a vector. I usually don't because that's tedious.
> 
> Additionally, Quint uses the cursive capital letters for I and J to denote the set of best responses against strategies $p$ and $q$. The closest symbols are with `\mathscr`, which gives us $\mathscr{I}$ and $\mathscr{J}$, which are pretty unrecognizable in my opinion, so I use `\mathcal` ($\mathcal{I}$ and $\mathcal{J}$) instead.

The idea here is that $(p^*,q^*)$ is a Nash equilibrium if, *simultaneously:*
- For every $i=1, \ldots, m$, **either** $p_i^{*} = 0$ or $i \in \mathcal{I}^*(q^*)$.
- For every $j=1, \ldots, n$, **either** $q_j^{*} = 0$ or $i \in \mathcal{J}^*(p^*)$.

That is to say, for every pure strategy in player 1's mixed strategy $p^*$, either i'm not playing it at all (so $p_i^{*} = 0$), or it's part of my best response against player 2's $q^*$, such that $i \in \mathcal{I}^*(q^*)$. This gives us a mathematical basis to find Nash equilibria in bimatrix games.

> [!info] Sidenote
> The $p_i^* = 0$ case is something we've demonstrated from time to time with regards to mixed strategy NEs; the idea is that if have a mixed strategy for which some pure strategy $p_i$ is played a nonzero amount of the time, but there exists a mixed strategy where $p_i = 0$ that improves my payoff, then I have some incentive to deviate. Therefore, any strategy for which $p_i \gt 0$ (in this specific case) is not a Nash equilibrium.

Let's consider the game

|     | a      | b       | c      |
| --- | ------ | ------- | ------ |
| 1   | (2, 1) | (1, 2)  | (3, 0) |
| 2   | (1, 4) | (3, -1) | (1, 1) |
| 3   | (3, 0) | (-1, 3) | (0, 1)       |

Suppose further that $p = (\frac{1}{3}, \frac{2}{3}, 0)$ and $q = (0, \frac{1}{2}, \frac{1}{2})$, which we've just picked at random. Then, 
$$\mathcal{J}^{*}(p) =
\begin{cases}
a \implies \frac{1}{3}*1+\frac{2}{3}*4+0*0 = 3 \\
b \implies \frac{1}{3}*2+\frac{2}{3}*-1+0*3 = 0 \\
c \implies \frac{1}{3}*0+\frac{2}{3}*1+0*1 = \frac{2}{3} \\
\end{cases}$$
so that we find the best response $\mathcal{J}^*(p)$  is for player 2 to play pure strategy A, with an expected payoff of 3 against $p$.

Applying similar logic for player 1, we end up with $\mathcal{I}^*(q)$ is for player 1 to play either pure strategy 1 or 2, which both have an expected payoff of 2 against $q$.

So does either combination of the strategies in $\mathcal{I}^*(q)$ and $\mathcal{J}^*(p)$ constitute a Nash equilibrium?

We now check conditions 1 and 2 from our definition above: that is, $p$ is a best response against $q$, and $q$ is a best response against $p$. And remember - a strategy is a best response if all the pure strategies involved in the mixed strategy are either in $\mathcal{I}^*$ or aren't played at all.

So checking strategy $p_i$ for $i = 1, 2, 3$:
- $p_1 \neq 0$, but $p_1 \in \mathcal{I}^*(q)$.
- $p_2 \neq 0$, but $p_2 \in \mathcal{I}^*(q)$.
- $p_3 = 0$.

So $p$ is a best response aginast $q$. We now move to checking that $q$ is a best response against $p$:
- $q_1 = 0$.
- $q_2 \neq 0$, but also $q_2 \not \in \mathcal{J}^*(p)$. That is, whenever you're playing strategy B, there's always a better option.

And we find that $q$ is not a best response against $p$ because player 2 is playing B a nonzero amount of the time. For player 2 to improve their payoff, they should be switching to pure strategy A whenever they play strategy B.

But Nash showed that there is a NE in all these bimatrix games - so there must be some systematic way to find them.