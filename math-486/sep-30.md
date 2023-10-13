Recall our infinite variant of the prisoners' dilemma, where our stage game was 

| $_I\text{\\}^{II}$ | C            | NC        |
| ------------------ | ------------ | --------- |
| **C**              | (-12•, -12•) | (0•, -24) |
| **NC**             | (-24, 0•)    | (-6, -6)  |

and we found that:
- when $n = 1$, there exists a unique dominating strategy NE.
- when $n \gt 1$ for a finite $n$, there exists no dominating strategy NE, but multiple NEs all with C-C, C-C, ... with an average payoff (-12, -12). We demonstrated that no "NC" play exists in any NE for a finite Nash equilibrium.

When $n = \infty$, we found that always playing C-C was also a Nash equilibrium. But we also found the strategy of playing NC in period 1, then playing NC until the other player plays C. If both players played such a strategy, it would be an NE but with outcome path NC-NC, NC-NC, ... with average payoff (-6, -6).

We know this is an NE because neither player can deviate - any deviation with no effect on the outcome path would (of course) not improve the payoff. And any deviation that changes the outcome path would yield a payoff of 0 instead of -6 for one period, but you would then have an infinite number of (-12, -12) after that due to the "trigger strategies" of both players. This means that both players are playing best responses.

But we have yet another strategy - suppose one player plays NC, C, NC, ... as long as the other player's moves match. As soon as the other player's move doesn't match, play C forever. Although perhaps not "normal", the strategy is well-defined. Such a strategy would yield an outcome path of NC-NC, C-C, NC-NC, giving an average payoff of (-9, -9) indefinitely. 

We know that this is also an NE, because any such deviation would also give infinitely many (-12, -12) payoffs. 

We can reasonably conclude that there are a lot of average payoffs that could be possible, even if some of the strategies entailing these payoffs don't seem reasonable.

Let's consider a graph of player I's payoff versus player II's payoff. 

![[Sep 30 2022-09-30 11.20.36.excalidraw]]

The $x$-axis is player I's average payoff, and the $y$-axis is player II's average payoff. The points plotted, then, are the individual payoffs of the stage game.

We call the (triangular) green region formed by the payoffs as the **convex hull**, the set of all possible weighted averages of payoffs from a stage game. 

We call the blue region the individual rational set, the set of payoffs whereby each player gets at least as much as they could gain on their own. This is more significant in cooperative games, but it is also relevant here as well. Obviously, no player will settle for the (0, -24) average payoff. But they can (at minimum) guarantee a (-12, -12) payoff by playing C-C, and assuming they were to work together or have some strategy involving better payoffs, we can reasonably say that they would do such a thing.

The **Folk Theorem** is a theorem that states that any payoffs within the region within both the hull and the individual rational set can be obtained as the average payoffs from the $n = \infty$ prisoners' dilemma (as Nash equilibria).

In general, the intersection of the hull and the individual rational set can be obtained as average payoffs from an infinitely repated strategic form game. This is the red-shaded diamond-shaped region in the diagram.

(Nobody knows who stated the theorem, so like folk songs, we have a folk theorem.)

## Example of the folk theorem
Suppose that we claim the point (-5, -9) is in the the region ABCD described by the folk theoerem. We must now construct an NE in the $n = \infty$ case which gives (-5, -9) payoffs.

First, since (-5, -9) is one-sixths of the way from (-6, -6) to (0, -24), we can say that $(-5, -9) = \frac{5}{6}(-6, -6) + \frac{1}{6}(0, -24)$. 

We can attain the average payoff of $(-5, -9)$, then, if we get a payoff of (-6, -6) five times out of six, and (0, -24) one times out of six.

One way we can achieve this is through the sequence
$$\underbrace{\text{NC - NC}, \ldots, \text{NC - NC}}_\text{Repeated 5 times}, \text{C - NC}, \text{NC - NC}, \ldots$$
indefinitely.

A strategy for both players that achieves this is:
- for player I, to play five NCs and then a C. Should player II deviate from their "always NC" strategy, play C forever.
- for player II, play NC all the time. Should player I deviate from their "five-sixths NC" strategy, player C forever.

The "punishment" aspect is required to make this a Nash equilibrium to guarantee that neither player has any incentive to deviate. 

Of course, the fact is that you have six different possible NEs in a six-period cycle. But you could have infinitely many different cycle lengths that adhere to the average over time, so long as we get our desired average. (And you could also have infinitely many different NEs for each infinitely many cycle length, and so on.) So there are infinitely many  Nash equilibria in our red-shaded region given by the Folk theorem.

The Folk theorem holds when we consider:
- subgame perfect Nash equilibria.
- discounted payoffs (in which payoffs may vary over the course of repetitions - various resources online exist).
- games in which $n$ is a random variable

We will now move onto chapter II, which brings rise to the idea of matrix games. We will consider two-person-zero-sum-games, also known as matrix games. These are games where the number of players is 2, where the sum of the players' payoff under any outcome is 0. That is - whatever one player wins, the other player loses. 

Five, five-with-a-die, and matching pennies are examples. Non-examples include the prisoners' dilemma, because there exist situations that are better for both players. Similarly, battle of the sexes and the arms race are non-examples as well. 

IN short, any two-player game in which there exists a "winner" and a "loser" is likely such a matrix game.


