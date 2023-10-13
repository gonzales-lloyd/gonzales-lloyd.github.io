As a reminder - before using the formulas for $p^{\star}$,  $q^{\star}$, and $V$, make sure that you have separated diagonals - that is, you have case 2 for which no saddle points exist.

But note that in a case like
$$
\left[
\begin{matrix}
2 & 2\\
1 & 4
\end{matrix}
\right]
$$

you have both case 1 and case 2. Notice how the case of separated diagonals and saddle points hold, in that both 2s are column maximums and are tied for row minimum.

We can see that the diagonal consisting of 2 and 4 "weakly" dominates the diagonal of the 2 and the 1.

So far, we have two ways to find minimax solutions. In fact, in this case, the two methods yield *different* minimax solutions. Later, we'll find out how to blend these two solutions.

So how do we solve two-person zero-sum games which are larger than $2 \times 2$? We know how to solve all $2 \times 2$ games - they all either fall under case  1 or case 2 (or both). We now move onto a study on how to solve larger matrix games, such that they are still two-person and zero-sum games.

In the book, there exists a graphical method for $2 \times n$ and $m \times 2$ games. These are two-person zero-sum games where one player has two strategies, and the other (in general) has any number of strategies. You can see how this would be rectangular in nature, where the size of one side is 2. You might also expect that any procedure that applies to $2 \times n$ matrices also applies to $m \times 2$ games, given one is just "rotated" or transposed.

Such a procedure exists and is described in section 3 of chapter 2; it will not be covered in class and will not be tested on, but is worth reading.

## Domination
Sometimes, large matrix games can be reduced in size by deleting rows and columns which are obviously bad for the player who would choose them.

> [!note] Definition
> Let $A$ be a matrix corresponding to a two-person zero-sum game. Then, the $i$th row of matrix $A$: 
> - **strictly dominates** the $k$th row if $a_{ij} \gt a_{kj} \,\forall\, j = 1, \ldots, n$
> - **weakly dominates** the $k$th row if $a_{ij} \geq a_{kj} \,\forall\, j = 1, \ldots, n$
> 
> and similarly, the $j$th column: 
> - **strictly dominates** the $l$th column if $a_{ij} \lt a_{il} \,\forall\, i = 1, \ldots, m$
> - **weakly dominates** the $l$th column if $a_{ij} \leq a_{il} \,\forall\, i = 1, \ldots, m$

For example, suppose that we have the matrix game

|     | **a**   | **b**   | **c**   | **d**   |
| --- | --- | --- | --- | --- |
| **1**   | 1   | -3  | 2   | 1   |
| **2**   | 2   | -1  | 3   | 4   |
| **3**   | 5   | 4   | -1  | 0    |

Then it holds that row 2 *strongly dominates* row 1.

Suppose that player I considers any strategy $p^{\star} = (p_1^{\star}, p_2^{\star}, p_3^{\star})$ in which $p_1^{\star} \gt 0$ for this example. Could this strategy still be minimax/optimal? The answer is no.

We can prove this by supposing that $p^{\star}$ was optimal, such that $p^{\star}$ guarantees a payoff of at least $V$ no matter what player II does. But now consider a perturbed strategy $\hat{p}$, where $\hat{p} = (0, p_1^{\star}+p_2^{\star}, p_3^{\star})$. That is, every time player I contemplates playing strategy 1, they are forced to play strategy 2 instead.

Notice that for any strategy $q$ (which is a mixture of a/b/c/d), $\hat{p} pays off a greater expectation than our supposed $p^{\star}$ does. Therefore, $\hat{p}$ guarantees a payoff more than $p^{\star}$.

But this is a contradiction; no strategy should exist that guarantees more than the value of the game. Therefore, $p^{\star}$ cannot have been optimal/minimax.

So we conclude that in any minimax strategy $p^{\star}$, $p^{\star} = 0$. But if it holds that any minimax strategy never plays strategy 1, we may as well go ahead and move strategy 1 from consideration, just considering the game

|       | **a** | **b** | **c** | **d** |
| ----- | ----- | ----- | ----- | ----- |
| **2** | 2     | -1    | 3     | 4     |
| **3** | 5     | 4     | -1    | 0     |

instead.

Furthermore, notice that column C dominates column D for player II. (All outcomes for strategy C are better regardless of what player I does, in that player II always pays less to player I).

Then, we can remove column D, so we have

|       | **a** | **b** | **c** |
| ----- | ----- | ----- | ----- |
| **2** | 2     | -1    | 3     |
| **3** | 5     | 4     | -1    |

But notice something important: column C did not dominate column D in the original game, since  $(1, C) \gt (2, C)$; there was a possibility that player II had to pay more if player II played strategy 1. Column C only dominated column D after we eliminated strategy 1 for player I.

Additionally, we can see that strategy B here (strictly) dominates strategy A. Removing strategy A, we instead have

|       | **b** | **c** |
| ----- | ----- | ----- |
| **2** | -1    | 3     |
| **3** | 4     | -1    |

and we're back to a $2 \times 2$ game, which we know how to handle. In this case, we have separated diagonals. Omitting the details, we find that we have $p^{\star} = \frac{5}{9}$  , $q^{\star} = \frac{4}{9}$, and $V = \frac{11}{9}$. So the solution for this smaller $2 \times 2$ game is 
- $S_{I}^{\bigstar} = \left(\frac{5}{9}, \frac{4}{9}\right)$
- $S_{II}^{\bigstar} = \left(\frac{4}{9}, \frac{5}{9}\right)$
- $V = \frac{11}{9}$

But what's the solution for the original game? We simply just allow the strategies that were dominated/eliminated to be played with a probability of 0, such that the full solution is
- $S_{I}^{\bigstar} = \left(0, \frac{5}{9}, \frac{4}{9}\right)$
- $S_{II}^{\bigstar} = \left(0, \frac{4}{9}, \frac{5}{9}, 0\right)$
- $V = \frac{11}{9}$

Suppose we now want to solve (find the minimax solution) for

|     | **a**   | **b**   | **c**   |
| --- | --- | --- | --- |
| **1**   | 4   | 3   | 3   |
| **2**   | 5   | 2   | -1    |

We'll solve this in two separate ways.

First, notice that C *weakly dominates* B. Then, eliminating B, we have

|     | **a**   | **c**   |
| --- | --- | --- |
| **1**   | 4   | 3   |
| **2**   | 5   | -1    |

and we're left with a saddle point for which the cell containing 3 is a saddle point; it's a row minimum and a column maximum. So for the $2 \times 2$ game, we have a solution of $p = (1, 0)$ and $q = (0, 1)$. Therefore, a minimax solution to the original game is
- $S_{I}^{\bigstar} = (1, 0)$
- $S_{II}^{\bigstar} = (0, 0, 1)$
- $V = 3$

But now, look at the original game. Note that the middle-top cell containing 3 is *also* a saddle point. Hence, another minimax solution is
- $S_{I}^{\bigstar} = (1, 0)$
- $S_{II}^{\bigstar} = (0, 1, 0)$
- $V = 3$

(And you could also see that either way, player II caps their payoff to player I at 3 - the value has not changed. You could also take any mixed strategy using b/c.)

The moral behind this example is that if we eliminate strategies using **weak** domination, you may lose minimax strategies. That is, if the problem asks you to find all minimax strategies, you cannot use this approach if it entails weak domination. If you just need one pair of minimax strategies, then you can get away with weak domination.

## Symmetry
We also have another trick for solving larger games: symmetry.

Suppose we have the identity matrix to solve:
$$
\left[
\begin{matrix}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 1
\end{matrix}
\right]
$$
It's not $2 \times 2$, so we can't use those approaches. There are also no dominating rows or columns. But we do have a lot of symmetry here. 

But the "logical" thing to try here is to play all your strategies with probability $\frac{1}{3}$. Then, if the other player (player II) plays any strategy, player I gets an expected payoff of $\frac{1}{3}$ no matter what player II does. This is an equalizing strategy.

The same argument holds for player II, who also has an equalizing strategy of equal value. Therefore, symmetry gave us a minimax solution of
- $S_{I}^{\bigstar} = (\frac{1}{3}, \frac{1}{3}, \frac{1}{3})$
- $S_{II}^{\bigstar} = (\frac{1}{3}, \frac{1}{3}, \frac{1}{3})$
- $V = \frac{1}{3}$
