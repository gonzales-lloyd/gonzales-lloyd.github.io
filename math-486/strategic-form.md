The conversion from extensive form to strategic form is something we'll talk about next. In a two-player game, we list in a tabular matrix form the reduced stratgies along with their resulting payouts. (Though you can do this with full strategies.)

Usually, this means each row and column represents a specific player's strategy, and the intersection of those strategies has a payout tuple in the relevant cell. Such a construction is referred to as the strategic form of the game.

Recall the [[Information#Matching Pennies|Matching Pennies]] game. Its extensive form was
![[Information 2022-08-31 11.24.26.excalidraw]]

and we defined our strategies as
- for player 1, at $V_{11} = \{O\}$, play heads. 
- for player 1, at $V_{11} = \{O\}$, play tails.
- for player 2, at $V_{21} = \{A, B\}$, play heads.
- for player 2, at $V_{21} = \{A, B\}$, play tails.

Then, let's define the strategic form for this game.

![[Strategic Form 2022-09-07 11.07.00.excalidraw]]

Neither the strategic form nor the extensive form is better overall. But let's consider the advantages of using the strategic form over the extensive form:
- We'll find it easier to analyze a game when it is in strategic form, especially with respect to the Nash equilibrium.
- A table is a matrix (strictly speaking, it's a "bimatrix"), which means that we can apply linear algebra to it.

And the extensive form has advantages as well:
 - You can see the dynamic structure of a game. You know who makes what move when, where chance moves come in, where payouts happen, who knows what at a given moment, etc. You lose this information in a table.
 - Extensive form can be used to model games with more than two players. Strategic form games are restricted to two players. (Of course, you can do n-dimensional arrays to represent n players, but that can be challenging to look at.)

## Five
Let's take another look at [[Extensive Form|Five]], with its [[Strategy#Reduced strategies|reduced strategies]]. Remember that player 1 has six strategies, while player 2 has three strategies. This yields a 6x3 matrix (noting that player 1 dictates the number of rows, player 2 dictates the number of columns):
![[Strategic Form 2022-09-07 11.18.12.excalidraw]]

Note that the strategies are written in order as described in the reduced strategy page. Also note how individual outcomes are not uniquely represented in this table; specific outcomes may appear more than once due to how strategies work.

Also important to note is that in games with chance moves, we place expected payoffs instead. This is because even if you know the exact strategies that both players are taking, the element of chance means that you only have a probability distribution instead. Therefore, you write down the expected payoff as a vector (or a tuple) such that the probabilities create a weighted payoff.

Sidenote: in a game where there is a 50% chance for a payoff of (-1, 1) and a 50% chance of (1, -1), then the expected payoff is (0, 0).

Let's now consider [[Chance Moves|Five with a die]]. There are actually 24 strategies for player 1, and 9 strategies for player 2. For simplicity, let's just have two strategies for player 1, and one strategy for player 2:
![[Strategic Form 2022-09-07 11.29.14.excalidraw]]

Let's consider player 1's $A$ strategy.

There exists a 1/3 chance that the game takes the path O-A-E-M, a 1/2 chance that O-A-F is played, and a 1/6 chance that O-A-G is played. Weighting all of the payoffs together yields
$$\frac{1}{3}(-1, -1)+\frac{1}{2}(2, -2) + \frac{1}{6}(2, -2)=(1, -1)$$
so we would place the vector $(1, -1)$ in the element.

Likewise, the only difference in the $B$ strategy is that there exists a 1/6 chance O-A-G-O is played, in which case the calculation becomes
$$\frac{1}{3}(-1, -1)+\frac{1}{2}(2, -2) + \frac{1}{6}(-1, 1)$$
and some fractional component comes out.

> [!note]
> I refer to the root node as $O$, but it is actually the numerical value zero. This is distinguished in extensive form as the script letter $\mathscr{O}$.

