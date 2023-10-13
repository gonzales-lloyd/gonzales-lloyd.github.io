Briefly going back to October 3:

Suppose that there exist indices $i^*$ and $j^*$ in an $m \times n$ matrix game $A$ such that both of the following are true:
- $a_{i^*j^*} \leq a_{i^*j}$ for $j = 1, \ldots, n$ (This is a row minimum.)
- $a_{i^*j^*} \leq a_{i^*j}$ for $i = 1, \ldots, n$ (This is a column maximum.)

So on the left side of the matrix are labeled indices $1, 2, \ldots, i^*, \ldots, m$, and at the top, $1, 2, \ldots, j^*, \ldots, n$. So then we have $a_{11}, a_{12}, \ldots, {a_{1j^*}, \ldots, a_{1n}}$ in row 1, and so on. We also have $a_{i^*1}, a_{i^*2},\ldots, a_{i^*j^*}, \ldots$ on row $i^*$.
Then, the entry $a_{i^*j^*}$ is both a row minimum and a column maximum. That is to say, it is a saddle point of $A$. 

We had an example matrix game of 

| $_I\text{\\}^{II}$ | A   | B   | C   |
| ------------------ | --- | --- | --- |
| **1**              | 5   | 6   | 10  |
| **2**              | 3   | -2  | 2   |
| **3**              | 1   | 9   | -10 |

So note the following:
- Since $a_{i^*j^*}$ is a row minimum, player 1 can guarantee a payoff of at least $a_{i^*j^*}$ by playing $i^*$. 
- Since $a_{i^*j^*}$ is a column maximum, player 1 can guarantee that they don't lose any more than $a_{i^*j^*}$ by playing pure strategy $j^*$.

In conclusion, if a matrix game has a saddle point $a_{i^*j^*}$, then a minimax solution is $S_I = i^*$ and $S_{II} = j^*$. By extension, the value of the game (since both stand to lose/gain the same thing) is $V = a_{i^*j^*}$.

Additionally, in this case, it is easy to argue that the strategies $S_I, S_{II} = \{i^*, j^*\}$ constitute an NE. It's easy to see that each is a best response against the other - if player 1 plays $i^*$, then player 2 playing $j^*$ is a best response since this is the best payoff (or smallest loss) in a given row. If player 2 plays $j^*$, then player 1 playing $i^*$ is a best response since this is the best payoff in a given column.

This begs the question - do all matrix games have saddle points? If this is true, then it is easy to "solve" them, either through minimax solutions or NE solutions. The short answer is no - not every matrix game has a saddle point. 

We can easily demonstrate this in the $2 \times 2$ matrix game below:

|       | a   | b   |
| ----- | --- | --- |
| **1** | 2   | -1  |
| **2** | -2  | 3   |

We only have four values to check:
- a1 is a column max, but not a row min.
- a2 is a row min, but not a column max.
- b1 is a row min, but not a column max.
- b2 is column max, but not a row min.

So there exists no saddle point in this matrix game. Instead, we can try to find a value by finding $\underline{V}$ and $\overline{V}$, which are the safety levels of player 1 and player 2 respectively.

For player 1:
- by playing strategy 1, they guarantee a minimum gain of -1.
- by playing strategy 2, they guarantee a minimum gain of -2.

So by using minimax strategies, player 1's minimax strategy is to play strategy 1, with $\underline{V} = -1$.

And for player 2:
- by playing strategy a, they guarantee losing no more than 2 (so that their payoff is -2).
- by playing strategy b, they guarantee losing no more than 3 (so that their payoff is -3).

So by using minimax strategies, player 2's minimax strategy is to play strategy a, with $\overline{V} = +2$.

But since $\underline{V} \neq \overline{V}$, the game does not have a value using pure strategies. It turns out there exists a way to bridge this gap between $\overline{V}$ and $\underline{V}$ - this is where we allow the players to play mixed strategies. Mixed strategies are where we allow the players to place probability distributions over the set of their pure strategies.

For example, perhaps player 1 could consider a strategy such as "play strategy 1 with probability 0.5, and play strategy 2 with probability 0.5". This is a mixed strategy.

There's some terminology regarding strategies to discuss:
- Do we mean "full strategy" or "reduced strategy" when we say "strategy"?
- Do we mean "pure strategy" or "mixed strategy"?

Let $G$ be a game in which player $k$ has $m_k$ pure strategies. (It is not necessary that all players have the same number of pure strategies.) Then, a mixed strategy for player $k$ is a vector $\underline{x} = (x_i, \ldots, k_{m_k})$ satisfying:
- $x_i \geq 0$ for $i = 1, \ldots, m_k$ and
- $\sum_{i=1}^{m_k} x_i = 1$ 

The interpretation of this is that player $k$ plays pure strategy $i$ with probability $x_i$ for $i=1, \ldots, m_k$. (And clearly, the sum of all probabilities must be 1, and all probabilities are between 0 and 1, or nonnegative, for each pure strategy.)

We can think of playing some pure strategy $i$ as equivalent to playing the mixed strategy $\underline{x} = (0, \ldots, 0, \underbrace{1}_i, 0, \ldots, 0)$ .
In a sense, we can think of pure strategies as a special type of mixed strategies.

Note that we can think of mixed strategies in two ways. To see this, consider an example in which a player has two pure strategies and they consider a mixed strategy of $(\frac{1}{2}, \frac{1}{2})$. We can think of this either as:
- The game is played once. Before they play, they flip a coin; if it comes up heads, they play (pure) strategy 1, and if it comes up heads, they play strategy 2.
- The game is played many times, and half the time they play strategy 1, and half the time they play strategy 2. There exists no pattern governing when they play either (because then the other player could adjust their strategy to compensate, once they've recognized the pattern. At each point, the other player is unsure of what this player will do).

If at each game in case 1 we flip a coin, this is a similar way of modeling case 2.

We now return to the matrix game

|       | a   | b   |
| ----- | --- | --- |
| **1** | 2   | -1  |
| **2** | -2  | 3   |

where we found that player 1 could guarantee $\underline{V} = -1$. But suppose that player 1 considers a mixed strategy of $(0.5, 0.5)$. 
- If player 2 plays strategy a, player 1 can expect to win $0.5*2 +0.5*-2 = 0$.
- If player 2 plays strategy b, player 2 can expect to win $0.5*-1 + 0.5*-3 = 1$. 

So against player 2's pure strategies, player 1's mixed strategy of $(0.5, 0.5)$ guarantees an *expected* safety level of 0. This is better than the pure strategy safety level playing strategy 1, which was $\underline{V} = -1$.

But player 2 can also play a mixture of their strategies a and b, like $(q, 1-q)$ for $0 \leq q \leq 1$. This is a general mixed strategy. If so, then player 1, by playing $(0.5, 0.5)$, can expect to win:
$$(0.5*q*2) + (0.5*(1-q)*-1) + (0.5*q*-2) + (0.5*(1-q)*3)$$
which gives $1-q$. (Each term is composed of the probability that both players select a given payoff through the pure strategy they select).

We can make a graph of $q$ to player 1's expected payoff:

![[Oct 5 2022-10-05 11.52.18.excalidraw]]

So in this case, even still allowing for the case where player 2 can play any mixed strategy, then the worst case for player 1 is that player 2 lets $q=0$ (thus playing strategy a all the time) and so player 1 can still guarantee at least 0.

Thus, player 1's minimax payoff has improved from -1 to 0.