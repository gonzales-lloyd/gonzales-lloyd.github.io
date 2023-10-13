
## Finitely repeated prisoners' dilemma

Recall the extensive form of the prisoners' dilemma, repeated twice:
![[Sep 26 2022-09-26 11.37.12.excalidraw]]

Recall that the basic strategic form matrix of the stage game is 

| $_I\text{\\}^{II}$ | C            | NC        |
| ------------------ | ------------ | --------- |
| **C**              | (-12•, -12•) | (0•, -24) |
| **NC**             | (-24, 0•)    | (-6, -6)  |

And we noticed a few things:

First, always confessing is not a dominating strategy. Always confessing is not the best response against player II confessing as well - specifically, if the other player plays strategy 6. There is no dominating strategy here, unlike in the $n=1$ case.

> [!note] Dominating strategies
> As a reminder, a dominating strategy is a strategy for which it is the best response against all of the other player's strategies. A regular Nash equilibrium means that if each player individually locks their strategies, there is no way for the other player to improve their payoff.
> 
> In the case of a non-dominating strategy in a Nash equilibrium, this means that (for example) player II can move to another strategy. Their payoff won't improve (by definition in a Nash equilibrium), but it may be the case that the first player can improve their payoff in some way. As a result, the non-dominating strategy is not the best reponse against player II's, despite the fact player II has not improved their own payoff.
> 
> In the case of a dominating strategy, this means that player I's strategy maximizes their payoff for all of player II's possible strategies. Regardless of what player II does, player I will always be getting the best payoff against their strategy.

Second, there are four NEs here: 1-1, 1-2, 2-1, and 2-2. 

Note that these strategies are functionally equivalent, given that switching between player I's 1 and 2 strategies and player II's 1 and 2 strategies causes differences in irrelevant parts of the game. All four NEs result in C-C and C-C, ending up with the payoff of (-24, -24) or (-12, -12) per play.

This gives rise to an interesting theorem. 

Suppose that the prinsoners' dilemma is played $n$ times, with $n$ finite. Then:
- both players always confessing is an NE. 
- in any NE, the outcome path C-C; C-C; C-C; ... repeated $n$ times is traversed with an (average) payoff of (-12, -12) per play.

We can prove this by seeing that if either player plays NC at any point, it either makes no difference (if the other player's move means that the NC is never played) or they will lose more badly (their payoff falls from -12 to -24). 

The rigorous proof involves a proof by contradiction. 

Suppose that there did exist an NE whose outcome path an an NC play in it. We will show that this leads to a contradiction. 

If we have an NE with an NC play in the outcome path, there must be a period $T$ which is the last period (referring to each iteration of the repeated game) where this occurs, since $n$ is finite. That is to say - NC is played once, and then every successive period after that is all C-C. 

Suppose that $X$ is the information set where this occurs.  Consider the player who played NC at information set $X$. (If both players choose NC, just choose one of them.) They now consider a new strategy:
- In periods $1, \ldots, T-1$, they play the same strategy.
- In period $T$, they always play C.
- In period $T+1 , \ldots, n$, they always play C.

Consider the fact that since every play after period $T$ was C-C, they got a payoff of -12 each time. Now, compare this player's payoffs under the new strategy compared to the old strategy. 
- For periods $1, \ldots, T-1$, since they played the same strategy before $T$, they will have the same average/total payoff up to this point as before.
- For period $T$, a single play, switching from NC to C is guaranteed to help. (If the other player played C, then you would go from -24 to -12; if the other player played NC, you would go from -12 to 0.) This also means that the game takes a different branch.
- For periods $T+1, \ldots, n$, this guarantees that you will either have the same payoff as before or gain some payoffs, if the new branch involves the other player occasionally playing NC. There may be cases where you get a payoff of +0 instead of -12.

We have shown that the new strategy pays off more than the old strategy against the other player's fixed strategy. Therefore, the old strategy could not possibly be a best response. We have therefore demonstrated that the original strategy could not possibly be an NE.

Note that the argument takes into account the fact that $n$ was finite. If it were infinite, there's no way we could demonstrate that there existed a $T$ for which NC was played for the last time.

Also worth noting - we still don't know why in practice, crooks play NC-NC despite the fact that in a repeated game, C-C remains the Nash equilibrium.

## Infinitely repeated prisoners' dilemma
Consider what happens if the game is played an infinite number of times, for $n = \infty$. This is significant because that the crooks may be viewing their "long term" prospects for which a finite $n$ is not necessarily known.

We continue to know that always confessing is an NE, for which the payoff is (-12, -12) per period.

But let's consider a strategy in which we play NC in period 1 up until the period in which player II plays "C". Following that (period - because we're in an information set), we play "C" forever. This is a punishment strategy, where we begin by playing nice, but eventually punish the other player.

Suppose that player II does the same thing - play NC until the other player plays C. Now, if the players play these "abstract" strategies, then the outcome path will be NC-NC forever. Then, the average per-period payoff becomes (-6, -6). 

This brings the question: can either player deviate from their strategies (against the other player) and stand to benefit? If so, we don't have a Nash equilibrium. If not, we do have a Nash equilibrium.

The short answer is no - there is no way to deviate from the strategy, since there will be an infinite number of periods with (-12, -12) following your one (0, -24) period (and your prior finite moves will remain the same in terms of their payoffs of -6, -6.)