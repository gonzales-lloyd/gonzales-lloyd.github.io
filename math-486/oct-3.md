We usually consider a two-player zero-sum game, or a matrix game, in strategic form.

Consider a game in which there exists two pure strategies for player 1, and three pure strategies for player 2.

| $_I\text{\\}^{II}$ | A            | B            | C   | 
| ------------------ | ------------ | ------------ | --- |
| **1**              | (2, -2) | (-3, 3)     | (0, 0)    |
| **2**              | (0, 0)     | (-1, 1) | (7, -7)     |

But because this is a zero-sum game, if we know the payoff of either player in any given scenario, we also know the payoff of the other player as well - it's just the negative of that.

So we often just write the values/amounts that player 2 pays to player 1 - that is, the payoff to player 1 in the given case. This is standard convention.

| $_I\text{\\}^{II}$ | A   | B   | C   |
| ------------------ | --- | --- | --- |
| **1**              | 2   | -3  | 0   |
| **2**              | 0   | -1  | 7   |

Thus, player I tries to get the outcome with the high numbers in them, while II is trying to have the outcome come to a cell with the low numbers in them.

Also by convention is that player 1 chooses the row, while player 2 chooses the columns; that is, each row reflects one of player 1's strategies, while each column reflects one of player 2's strategies.

We call such games **matrix games** because we can represent them in a single matrix. 

General two-person games in strategic form without the zero-sum hypothesis are called bimatrix games because it takes two matrices to represent them. (We'd be breaking up each element in our regular strategic-form games so that we have an actual matrix, with only one number per cell - not tuples/vectors.)

In general, matrix games are a special subclass of bimatrix games. 

It turns out that there exists a solution concept for predicting the outcome of a noncooperative game, the **minimax solution**. 

We already know one solution concept in strategic-form games, the Nash equilbrium. And in certain games, we have perfect Nash equilibria. Nash equilibria were based on stability, such that no player had any incentive to change.

But minimax solutions are motivated by a different viewpoint. Suppose we have

| $_I\text{\\}^{II}$ | A   | B   | C   |
| ------------------ | --- | --- | --- | 
| **1**              | 5   | 6   | 10  |
| **2**              | 3   | -2  | 2   |
| **3**              | 1   | 9   | -10 |

Pretend that you're player 1. You think to yourself: "I am a pessimist. So let me consider the worst that can happen to me in this game. " This is how many people or organizations think when considering risk vs. reward, such as in military operations.

So you think, "If I play: 
- strategy 1, the worst that can happen is that player 2 plays A and I get +5. 
- strategy 2, then the worst that can happen is that player 2 plays B and I get -2. 
- strategy 3, then the worst that can happen is that player 3 plays C and I get -10.

So to play safest, I need to "max my min(imum)", so I'll play 1. Then, we say that Player 1's minimax strategy, or "optimal strategy" as stated by Shapley, is to play strategy 1, which guarantees him his **safety level payoff** of $\underline{V} = 5$. (Note that $V$ in this case is not a vector, but a scalar. This is normally underlined to denote that this is a lower bound for the payoff, but I can't get the underline to work.)

Similarly, for player II, the same logic applies:
- Playing A, the worst is that player 1 plays strategy 1 and player 2 loses 5.
- Playing B, the worst is that player 1 plays strategy 3 and player 2 loses 9.
- Playing C, the worst is that player 1 plays strategy 1 and player 2 loses 10.

So player 2's minimax strategy is to play strategy A, which guarantees she loses no more than 5. Then, her safety level of $\overline{V} = 5$. (Notice the upper bar for player 2. This is always the case - we will later prove that $\underline{V} \leq \overline{V}$.)

So in this game, we see that simultaneously:
- player 1 has a strategy that guarantees he will win at least $\underline{V} = 5$.
- player 2 has a strategy where they can lose no more than $\overline{V} = 5$

And so we might conclude that the "right" payoff in this scenario is that player 1 wins 5 from player 2. Then, we conclude that the result of the game "should be" that player 2 pays player 1 a payoff of 5. So the value of the game is +5.

Formally, we let $G$ be a two-person, zero-sum game. Let $\underline{V}$ be the  maximum amount that player 1 can guarantee to themselves (by playing a minimax strategy). Similar, let $\overline{V}$ be the minimum amount that player 2 can guarantee to lose no more than (also by playing a minimax strategy). Then, if $\underline{V} = \overline{V} = V$, we say that $V$ is the value of the game, though this may not always happen.

So we define a **minimax solution** of a two-person zero-sum game as a pair of minimax strategies, one for each player, together with the value of the game (assuming a value exists).  (Note the difference between minimax solutions and minimax strategies.)

So far, we have by no means shown that a value always exists in an arbitrary given TPZSG. In the example above, note that the minimax strategies $S_I = A$ and $S_{II} = 2$ also constitute a Nash equilibrium. Despite the fact the approaches are different - eliminating incentives to deviate as opposed to selfishly minimizing losses - they're the same here.

So can we construct a class of matrix games on which we can perform a similar analysis? The answer to this question is actually yes.

Suppose that there exist indices $i^*$ and $j^*$ in an $m \times n$ matrix game $A$ such that both of the following are true:
- $a_{i^*j^*} \leq a_{i^*j}$ for $j = 1, \ldots, n$ 
- $a_{i^*j^*} \leq a_{i^*j}$ for $i = 1, \ldots, n$ 

On the left side of the matrix are labeled indices $1, 2, \ldots, i^*, \ldots, m$, and at the top, $1, 2, \ldots, j^*, \ldots, n$. So then we have $a_{11}, a_{12}, \ldots, {a_{1j^*}, \ldots, a_{1n}}$ in row 1, and so on. We also have $a_{i^*1}, a_{i^*2},\ldots, a_{i^*j^*}, \ldots$ on row $i^*$.
Then, the entry $a_{i^*j^*}$ is both a row minimum and a column maximum. That is to say, it is a saddle point of A. 

In calculus III, we looked at functions of two variables in continuous math (not discrete math).  So if you saw that in the $x$ direction, a function was hitting a minimum - perhaps $\frac{\partial f}{\partial x} = 0$ - but at the same time, in the $y$ direction, it was hitting a maximum, so that $\frac{\partial f}{\partial y} = 0$. So it's not the maximum or minimum of the whole function - it's a minimum and a maximum at the same time.

We call the saddle point because it's a good point to sit on, so you don't fall off.  

![[Pasted image 20221029211636.png]]

But the important fact is that the saddle point is both a minimum and a maximum in a calculus context, as well as in minimax solutions as well.