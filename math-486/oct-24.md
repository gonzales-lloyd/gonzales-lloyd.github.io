No study guide for midterm; you may bring in a note sheet of one page. It covers everything from homework 5 up to linear programming. 
## An overview of bimatrix games
We started talking about bimatrix games, which were two-person games without the zero sum hypothesis. We can briefly compare matrix and bimatrix games:

**Matrix games:**
- Two players.
- The zero sum hypothesis holds; that is, $a_{ij} + b_{ij} = 0$ where $a$ represents the payoff for player I given that pure strategies $i$ and $j$ are played by player 1 and player 2 respectively (based on their indices in the matrix).  A similar case holds for player 2, where $b$ is their payoff.
- It is impossible for player 1 and player 2 to cooperate because their interests are diametrically opposed (that is, they're completely different from each other).
- The existence of a Nash equilbrium immediately implies the existence of a minimax solution (that is, if a game has a value, it has a Nash equilibrium).

**Bimatrix games:**
- Two players.
- The zero sum assumption is not made here.
- There are two cases with respect to cooperation:
	- where player 1 and player 2 cannot or will not consider cooperation.
	- where player 1 and player 2 can consider cooperation - the realm of cooperative game theory. We saw this in the prisoners' dilemma.
- The conclusion that a Nash equilibrium implies a minimax solution does not necessarily hold.

Suppose we have the following strategic form:

|     | a        | b       | c       |
| --- | -------- | ------- | ------- |
| 1   | (1, -1)  | (1, 2)  | (2, -1) |
| 2   | (-2, 3)  | (-1, 2) | (3, -1) |
| 3   | (-3, -1) | (2, 3)  | (4, 4)  |

Analyzing the game, we find that player 1 can play strategy 1 - that is, $p^{\star} = (1, 0, 0)$ - guaranteeing a payoff of at least 1, no matter what strategy (mixed or pure) player 2 plays.

Also, consider the case where player 1 plays any mixed strategy $\underline{p}$ with $p_1 \lt 1$: they then guarantee a payoff less than 1 if player 2 plays strategy A. 

Since we're thinking about worst-case scenarios, then $p_1 \not\lt 1$, so that we need $p_1 = 1$. (That is, if we don't exclusively play $p_1 = 1$, then there exists a worst-case that is worse than a payoff of 1. It just so happens here that strategy A is that worst case; it's not that we're "excluding" strategy C from our analysis.)

Therefore, we can conclude that player 1's unique minimax strategy is $p^{\star} = (1, 0, 0)$ with $V_{I} = 1$, where $V_{I}$ is the safety level for player 1. 

> [!note] sidenote
> Notice we can't use $\underline{V}$ and $\overline{V}$ anymore, since we use these to imply what player 1 can guarantee and what player 2 can guarantee against player 1; but remember that because we're in a bimatrix game where the zero sum hypotehsis no longer holds, a guarantee of $V_{I} = 4$ in one matrix doesn't tell us anything about what player 2 can guarantee in the other matrix. So we have to use safety levels for both players represented as $V_I$ and $V_{II}$.

For player 2, we find that by playing strategy B, or $q^{\star} = (0, 1, 0)$, they guarantee an expected payoff of at least 2, no matter what strategy (again, mixed or pure) player 1 plays.

Also, consider the case that player 2 plays any mixed strategy with $q_2 \lt 1$. Then, player 1 playing strategy 1 will guarantee a payoff (for player 2) that's less than 2. This makes it clear that there exists a worst-case scenario that's worse than what we currently have with $q_2 = 1$, which means that only $q_2 = 1$ is a minimax strategy for player 2.

In turn, $q^{\star} = (0, 1, 0)$ is our minimax strategy.

So, do the minimax strategies constitute a Nash Equilibrium? No - if the two players play $p^{\star}$ and $q^{\star}$, then there exists a profitable deviation. For example, player 1 has a profitable deviation by playing strategy 3 against player 2's minimax strategy of playing strategy B.

But notice that if the two players play strategies 3 and C instead, they both get the highest payoff on the boards of 4 each; this constitutes a Nash equilibrium (since they're both getting the highest payoffs at the same time), but neither pure strategy 3 nor pure strategy C is minimax.

## Finding minimax strategies in bimatrix games
So how do we find minimax and Nash equilibria in bimatrix games?

First, something to note about minimax strategies is that the minimax strategy and safety level doesn't depend upon the other player's payoffs. If we had the strategic form above and had no idea what player 2 was getting at any given payoff, that wouldn't change our minimax strategy. That's not the case for Nash equilibria - it depends on us knowing the other player's payoffs.

In other words - the minimax strategy and safety level for either player does not depend on the other player's payoffs. You can find minimax strategies for a player by looking at just their own matrix and using two-person zero-sum game theory for that matrix.

For example, if we wanted to find the minimax strategy and safety levels for the bimatrix game $AB =$

|     | a       | b       |
| --- | ------- | ------- |
| 1   | (1, -1) | (3, 1)  |
| 2   | (0, 1)  | (2, -4) |

then for player 1, their matrix looks like

|     | a   | b   |
| --- | --- | --- |
| 1   | 1   | 3   |
| 2   | 0   | 2    |

where we can readily see that there exists a saddle point for this $2 \times 2$ matrix (assuming the zero sum hypothesis), which is 1-a. That is, player 1 maximizes their minimum payoff by playing strategy 1 here, which in turn gives player 1 a lower bound of $V_{I} = 1$.

It's a little trickier for player 2. If we want to use the theory from two-person zero sum games, we have to represent the matrix as $-B$ - that is, the matrix representing the amounts that player 2 loses, which is what the matrix reflects in TPZSGs. (If we used the values from the bimatrix game as-is, it would imply that player 2 is "paying" (or losing) `-1/1/1/-4`, which is not actually the case - we know this is what they win.)

So $-B =$

|     | a   | b   |
| --- | --- | --- |
| 1   | 1   | -1  |
| 2  | -1  | 4    |

and since player 2 wants to minimize their payoff to player 1 (pretending this is a zero-sum game) - that is, player 2 wants the smaller values - then we apply the separated diagonals case for $2 \times 2$ games to find player 2's minimax strategy, which happens to be $q^{\star} = \left(\frac{5}{7}, \frac{2}{7}\right)$, yielding a value of $\frac{3}{7}$ for this matrix game.

Now, remember that this is the amount that player 2 can guarantee to lose no more than. That is, they can't win more than $-\frac{3}{7}$ - the safety level.

Then, in this game:
- player 1's minimax strategy in $A$ is to play strategy 1. 
- player 1's safety level is the safety level $\underline{V}$ in $A$.
- player 2's minimax strategy in $-B$ is to play $q^{\star} = \left(\frac{5}{7}, \frac{2}{7}\right)$. 
- player 2's safety level is $-\overline{V}$ in $-B$. 

Now, there are a few things to note:
- You can still apply all the original concepts of solving two-person zero-sum games in the individual matrices. That includes domination, the formulas, linear programming, and so on.
- You could also transpose player 2's payoff matrix to get a matrix where player 2 is maximizing instead of minimizing; this is equivalent to inverting the payoffs in the matrix to show what player 2 loses instead of wins.

## Finding Nash equilibria in bimatrix games
In 1950, Nash put forward the theorem that every bimatrix game with a finite number of pure strategies for each player contains at least one Nash equilibrium using **mixed strategies**. We already found that no Nash equilibrium existed for Matching Pennies, assuming you only use pure strategies.

It is worth noting that Nash proved a more general theorem, which is that any $n$-player game (where $n \gt 2$ is fine) with a finite number of pure strategies contains at least one mixed strategy Nash equilibrium. The proof is relatively complicated, using fixed point theory from analysis/topology. It states that a function $F$ will have at least one point $x$ for which $F(x) =x$ under some conditions on $F$.

Another remark: In TPZSGs, we saw that almost every matrix game contains a unique essential submatrix, containing a unique set of minimax strategies and therefore a unique Nash equilibrium. ("Almost every" in the probability sense, where the probability is 100% but the opposing outcome does exist with probability 0%.)

But in bimatrix games, it is **not** true that almost every game has a unique Nash equilibrium.



