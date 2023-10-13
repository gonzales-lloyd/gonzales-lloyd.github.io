Recall that we were covering the Cournot duopoly model, which is a model of a duopoly in a market - better than a monopoly, but worse than perfect competition.

For example, we had a market in which the demand curve $D$ was $p = a -b(y_1+y_2)$. We had two firms in the market. Firm 1 chose a production rate $y_1$ in the interval $[0, \infty)$ and firm 2 chose a production rate $y_2$ in the interval $[0, \infty)$. In our case, the production costs $c_1$ and $c_2$ were equal to 0.

Then, we found that the payoff/profit functions for firm 1 was $\pi_1(y_1, y_2) = (a-b(y_1+y_2))*y_1$ - that is, price times quantity. (Since there's no production cost, we don't need to account for the fact that profit is actually equal to revenue minus costs; it's just equal to revenue.) Similarly, the payoff function for firm 2 was $\pi_2(y_1, y_2) = (a-b(y_1+y_2))*y_2$.

We want a Nash equilibrium of the game, in which they are both maximizing their profits against each other. Then, we want
$$\frac{\partial\pi_1}{\partial y_1}=\frac{\partial\pi_2}{\partial y_2}=0$$
which occurs when $y_1^* = \frac{a}{3b}$, and $y_2^* = \frac{a}{3b}$.

To "judge" a market, economists look at "total market output/consumption". From our calculations, we find that the total market consumption is equal to $\frac{2a}{3b}$. 

So the question is - how does $\frac{2a}{3b}$ compare with the total market output/consumption in an equivalent market, with the same demand curve and production costs, under:
- perfect competition?
- a monopoly?

(Note: we say output/consumption since everything produced is assumed to be consumed.)

Under perfect competition, the firms select a production level such that $P = MC$ - that is, the price is equal to the marginal cost of production. And since marginal cost of production is just the derivative of the cost of production, and since (in our model) the production cost is 0, the firms will act to set the price to 0.

In other words, they'll set their total productions $y_1, y_2, \ldots, y_k$ so that $p = a-b(\sum{y_k}) = 0$, and the total output will instead be $\frac{a}{b}$. You can see that this results in more production/consumption than under a duopoly, so we say that perfect competition is "better".

Under a monopoly, there is one firm that would try to maximize its own profit. This is what any firm does, but a monopolist has the ability to not worry about competition. Then, since they constitute the entire market's production, the price $p = a-b(y_1)$. Then, their profit function will be $\pi(y_1) = (a-b(y_1)) * y_1$. 

In turn, we end up with $\pi(y_1) = (a*y_1) - (b*y_1^2)$. Looking to maximze this, we have $\frac{\mathrm{d}\pi}{\mathrm{d}y_1} = a-2by_1$, and setting the derivative equal to 0 yields $y = \frac{a}{2b}$.

As we can see, the total market production in this monopoly is equal to $\frac{a}{2b}$, which is less than the total market production in the duopoly, which was $\frac{2a}{3b}$. We see that a monopoly is indeed "worse" than a duopoly.

## Why crooks don't confess
This is an introduction to repeated games. We return to the prisoners' dilemma. Here's its strategic form matrix again:
| $_I\text{\\}^{II}$ | C            | NC        |
| ------------------ | ------------ | --------- |
| **C**              | (-12•, -12•) | (0•, -24) |
| **NC**             | (-24, 0•)    | (-6, -6)  |

where we found that the NE was for both to confess, despite the fact that a better payoff exists where both don't confess. And indeed, we do get outcomes of (-6, -6) in real life, despite the two prisoners not having any means of communication or reason to trust.

So we think that there exist cases where the (NC, NC) outcome actually occurs. Perhaps the most well-known example is where a case goes unsolved, and the perpetrators of a crime are never found because nobody confesses.

There are a couple of explanations for why the (NC, NC) outcome does occur. One is that the players actually are able to make a binding contract, in which case we have a cooperative game. But this is not likely to be the situation here.

So in a game theoretical way, is there a way to explain a seemingly cooperative outcome in terms of a noncooperative behavior?

Our explanation is that the game is played repeatedly. That is - choices made in previous iterations of a game will affect what happens in future iterations. Perhaps the two prisoners have a long history of crime together, and this time, when they were caught and had to make the decision to confess or not confess, they had knowledge of the other player's tendencies. 

We might say that each crook thinks, "Well, if I play NC this time, then if the situation comes up again, my accomplice will get the message to play NC next time. Then, we might get (-6, -6) every time we're caught in the future."

This brings up the study of what happens in repeated games - that is, when the same game, called the **stage game**, is repeated $n$ times. $n$ may be infinity or a random variable. 

Let's pretend that we just play the prisoners' dilemma twice. Its extensive form looks like
![[Sep 26 2022-09-26 11.37.12.excalidraw]]

and it holds we can also make a strategic-form matrix of it.

Now, you might wonder if there exists a dominating strategy here. The answer is that there isn't. But in the $n=2$, neither player has a dominating strategy. Intuitively, you might guess that always confessing is  a dominating strategy. 

In fact, strategy 1 (see handout) for player 1 is not a best response againast player 2's strategy 6. Why is that? Here, player 2 hopes that player 1 doesn't confess on the first time. If player 1 confesses, then player 2 will confess on the second game. If player 1 doesn't confess, then player 2 won't confess on the second game. For player 2, this is a "tit-for-tat" or "punishment" strategy.

And of course, we can still find Nash equilibria in the strategic form. There are four NEs here - not one.

