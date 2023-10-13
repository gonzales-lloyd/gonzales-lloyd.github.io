## Symmetry and domination
Consider the following example:

|     | a   | b   | c   | d   |
| --- | --- | --- | --- | --- |
| **1**   | 1   | 1   | 1   | 1   |
| **2**   | 4   | 3   | 2   | 8   |
| **3**   | 8   | 4   | 3   | 2   |
| **4**   | 2   | 8   | 4   | 3   |
| **5**   | 3   | 2   | 8   | 4    |

An interesting property about this game is that we can combine domination using symmetry.

For example, we might immediately notice that strategy 1 is dominated (for player 1) by all the other strategies. This gives us the game

|     | a   | b   | c   | d   |
| --- | --- | --- | --- | --- |
| **2**   | 4   | 3   | 2   | 8   |
| **3**   | 8   | 4   | 3   | 2   |
| **4**   | 2   | 8   | 4   | 3   |
| **5**   | 3   | 2   | 8   | 4    |

You might notice that there's a 4, 3, 2, and 8 in each row and each column. And it turns out that the strategies $S_{I}^{\bigstar} = (0.25, 0.25, 0.25, 0.25)$ and $S_{II}^{\bigstar} = (0.25, 0.25, 0.25, 0.25)$ are minimax strategies for this game. Intuitively, you can see that if there's a 4, 3, 2, and 8 in all the columns and rows, you have an equal chance of getting any of those four values across all the strategies.  Adding up your expected value gives you $V=\frac{4+3+2+8}{4} = \frac{17}{4}$.


## Domination by mixed strategies
> [!warning]
> This is not in the book. You may see it referred to as "mixed domination".

Suppose we want to solve

|       | a   | b   |
| ----- | --- | --- |
| **1** | 3   | 3   |
| **2** | 1   | 6   |
| **3** | 6   | 1    |

In this case, note that neither player has a dominated strategy. We also don't see symmetry in this example

But notice that strategy 1 is dominated by a 50-50 cominbation of playing strategies 2 and 3. Against strategy A or strategy B, the mixed (equalizing) strategy $(0, 0.5, 0.5)$ gives you an expected payoff of 3.5:

$$
% an abuse of cases
E(S_{I}) =\begin{cases}
0.5*1 + 0.5*6 = 3.5 \,\text{against A}\\
0.5*6 + 0.5 *1 = 3.5 \,\text{against B}
\end{cases}
$$
whereas the pure strategy $(1, 0, 0)$, or playing strategy 1 all the time, always gives you a payoff of 3.

More formally, if we have $p = (p_1, p_2, p_3)$, then the mixed strategy $(0, p_2+\frac{1}{2}p_1, p_3+\frac{1}{2}p_1)$ always yields a higher expected payoff than $p$, no matter what player 2 does. (That is, playing $p_2$ and $p_3$ combined, equally often as you play $p_1$, it'll always be better.)

Hence, any minimax strategy will have $p_1 = 0$, so that we can eliminate strategy 1 for player 1.

We then end up with 

|       | a   | b   |
| ----- | --- | --- |
| **2** | 1   | 6   |
| **3** | 6   | 1    |

which you can see does exhibit symmetry, so we can reasonably assume the minimax solution is for both players to play their pure strategies half the time and the value is 3.5.

Indeed, if we use our solution concept for $2 \times 2$ matrix games, noting that this is the case of separated diagonals, we find $p^{\star} = 0.5$ and $q^{\star} = 0.5$, where $V = 3.5$.

Thus, we've shown that it's possible for strategies to dominate other strategies, even if they're mixed, and remove the dominated strategies as necessary.

One issue with mixed domination is that it's often difficult to spot. In general, if you can see quick "50-50" or "$\frac{2}{3}, \frac{1}{3}$" domination, then use it. We'll also talk about $\epsilon$-domination, which is another option. But otherwise, don't spend lots of time looking for mixed dominations.

## $\epsilon$-domination

Suppose we have

|       | a   | b   |
| ----- | --- | --- |
| **1** | 3   | 4   |
| **2** | 3   | 2   |
| **3** | 4   | 1    |

and we want to find all minimax solutions.

Notice that strategy 1 weakly dominates strategy 2. However, the problem with applying weak domination is that it's possible we'll lose some minimax solutions.

But consider that we have a $1-\epsilon, \epsilon$ mixture over strategies 1 and 3. That is, we heavily weight strategy 1, but have a nonzero weight on strategy 3. We can see that this strongly dominates strategy 2:
- The only case where strategy 1 doesn't strongly dominate strategy 2 is if player 1 plays strategy 2. 
- Although strategy 3 suffers if player 2 plays strategy B, it is still better than strategy 1 if player 1 plays strategy A.
- The loss of value from playing strategy 3 in the event strategy B is played is **less** than the gain in value from playing strategy 3 in the event strategy A is played, in combination with playing strategy 1 with probability $1 - \epsilon$.
- Playing $(1 - \epsilon, 0, \epsilon)$ means that we have *slightly* more than 3 against strategy A, and slightly less than 4 (but greater than 2) against strategy B.

In turn, we can remove strategy 2 without worrying about losing any minimax solutions, since we've found a case where it's possible to always beat any mixed strategy that plays strategy 2 at all. In turn, this gives us

|       | a   | b   |
| ----- | --- | --- |
| **1** | 3   | 4   |
| **3** | 4   | 1    |

which gives us the case of separated diagonals for $2 \times 2$ matrix games. We find that $p^{\star} = \frac{3}{4}$, $q^{\star} = \frac{3}{4}$, and $V = \frac{13}{4}$. Overall, the minimax solution is
- $S_{I}^{\bigstar} = (0.75, 0, 0.25)$
- $S_{II}^{\bigstar} = (0.75, 0, 0.25)$
- $V = \frac{13}{4}$.

## Structure of the solution set
Shapley laid the groundwork for this in 1948 - he was one of the earliest people to introduce game theory as a distinct concept, and the 1948 publication is his first publication. (He actually continued to publish works well into the 2000s.)

In many of the matrix games we've analyzed so far, 
- We start with some large matrix game to solve.
- We eliminate many of the pure strategies using domination, including mixed domatinon
- We end up with a small "square" submatrix, which we can solve either because it's a $2 \times 2$ matrix or because it exhibits symmetry.

Then, we conclude that the solution to the original game is just the solution to the submatrix, including probabilities of 0 for the eliminated pure strategies. 

In the previous example, we found that we shrunk 

|       | a   | b   |
| ----- | --- | --- |
| **1** | 3   | 4   |
| **2** | 3   | 2   |
| **3** | 4   | 1    |

down to 

|       | a   | b   |
| ----- | --- | --- |
| **1** | 3   | 4   |
| **3** | 4   | 1    |

and a little earlier, we turned a $5 \times 4$ matrix game into a symmetric $4 \times 4$ matrix game.

We call the small square submatrix the **essential submatrix** of the original game. 

> [!abstract] Essential submatrices
> An **essential submatrix** of a matrix game $A$ is a submatrix of $A$ that satisfies the following properties:
> 1. it is square, with dimensions $k \times k$
> 2. it is considered a game in itself, with unique equalizing minimax strategies for each player
> 3. these equalizing strategies, extended by 0s if necessary, are minimax strategies for $A$ itself

Regarding condition 2 - the essential submatrix does not need to have unique minimax strategies, but it does need to have unique *equalizing* minimax strategies.

Also: consider an essential submatrix for which $k = 1$, so that a single cell comprises the entire essential submatrix. Then this means it is the *only* strategy involved in the full mixed strategy for the entire game $A$, meaning that a pure strategy was the "solution" for the original game $A$. Then, it holds that this is just a saddle point of $A$.

Third, note that every matrix game contains at least one essential submatrix. 

Fourth, it is possible for a matrix game to have more than one essential submatrix, such as 
$$A = \left[\begin{matrix}
1 & 5 \\
4 & 4 \\
\end{matrix}\right]$$
