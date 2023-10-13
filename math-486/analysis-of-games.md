The question is - given a game in extensive or strategic form, can we analyze it? What should a player do - that is, what strategy should they take? We have a few solution concepts. One is *strategic equilibrium*, or **Nash equilibrium**. 

> [!note] sidenote
> The first name was used by Shapley, and is rarely used. The second name was named after John Nash, and is more frequently used.
> 
> A movie was made about John Nash, *A Beautiful Mind*, an Oscar-winning movie. A book was also made about the guy by Sylvia Nasar.
> 
> In 1950, Nash went to Princeton for his mathematics PhD, where we went with other soon-to-be famous mathematicians, including Shapley, Shubik, Scarf, and Gillies. It was there Nash would develop the foundations for game theory, with the other mentioned (graduate student) mathematicians developing game theory. Nash's thesis would be on the Nash equilibrium.
>
> In 1944, John Von Neumann and Morganstern (an economic professor at Princeton) would publish the first book on game theory.
> 
> In 1953, Nash would graduate and work at MIT. He would continue to publish landmark game theory papers, concurrent with his groundbreaking work in geometry, eventually becoming tenured. Then (in 1959) he began showing clear signs of mental illness, and ultimately struggled with his academic work for 30 years. Towards the later years, his schizophrenia went into remission, and ended up with the Nobel Prize in economics for the Nash equilbrium.

There are two classes of games.

In **cooperative games**, we assume that players may make binding contracts. For example, if one player plays a given strategy, then another player may also agree to play a given strategy. A specific example is that if player I agrees to play strategy A, and player II agrees to play strategy B, they may split the payout of the game as they see fit.

The question, then, becomes the contents of the contract - how exactly should we define our strategies, and how should we split the payoffs?

In **noncooperative games**, we assume that players are unable or unwilling to make binding contracts. Arms negotation, as Regan put it, has the principle of "trust but verify" - there is no way to make truly binding contract between countries.

In this case, the goal is to give incentives to your opponent so that they do what you want them to do.

For now, we will focus on noncooperative games. Noncooperative game theory has been much more studied, because their practical applications (e.g. in economy) are typically greater in number. Literature focuses on non-cooperative games.

The Nash equilibrium is the most well-known and used concept in noncooperative game theory. A **pure strategic equilibrium**, or PSE, or **(pure strategy) Nash equilibrium**, or PSNE. The term PSE is used in the textbook due to Shapley's avoidance of Nash's name, though PSNE (or just Nash equilibrium) is more widely used.

A PSE/PSNE is a set of strategies $\{S_1^*, S_2^*, \ldots, S_n^*\}$ such that no player can - by switching their own strategy - can improve their own expected payoff. For example, if we have a 40-person game, then each individual person has no way to improve their own standing by changing how they play; that is, everyone is playing the best possible responses.

Formally, if $\mathscr{S}_i$ is the set of all (reduced) strategies for player $i$ $h_i(S_1, \ldots, S_n)$ that equals the payoff to player $i$ if player 1 plays strategy $S_1$, player 2 plays strategy $S_2$, and player $n$ plays strategy $S_n$.

Then, $\{S_1^*, S_2^*, \ldots, S_n^*\}$ is a PSNE if:
- $S_i^* \in \mathscr{S_i}$for $i = 1, \ldots, n$.
- $h_i(S_1^*, S_2^*, \ldots, S_n^*) \geq h_i(S_1^*, S_2^*, \ldots, S_{i-1}, S_i, S_{i+1}, \ldots, S_n^*)$ for all $S_i \in \mathscr{S}_i$ (that is, all $i = 1, \ldots, n$.)

> [!danger]
> PSNEs are **sets** of strategies. A given payoff for a certain Nash equilibrium is not a PSNE in itself. $\left<ac, bd\right>$ could be a PSNE; $(0,-1)$ is **not**.

For example, consider Five. Recall its [[Strategic Form#Five|strategic form]] and extensive form. 

Suppose that player I and II consider the strategies 1 and B (O-1 B-1 C-1 G-1 and A-1 D-2 E-1), such that their payoff is $(-2,2)$.

Is this a realistic outcome? No, because player I improves his own payoff by switching his own strategy from 1 to 5 (O-1 B-3 C-1 yielding $(3, -3)$) against player II's current strategy of B, yielding a payoff of 3 instead of -2.

In other words, the strategies 1-B is not a PSNE because 1 is not the best response for player I against player II's B.

Consider the strategy A-5; this is also not a PSNE, because A is not a best response against player I's 5. Strategy 5 is the best response against player II's A, but strategy C is the best response against player I's  5.

An equivalent definition of PSNE is that $(S_1^*, \ldots, S_n^*)$ is a PSNE if simultaneously,
- $S_1^*$ is player I's best response against $S_2^*, \ldots, S_n^*$.
- $S_2^*$ is player II's best response against $S_1^*, S_3^*, \ldots, S_n^*$.
- $S_n^*$ is player III's best response against $S_1^*, S_2^*, \ldots, S_{n-1}^*$. 

This is a little complicated because of the simultaneous conditions. Focusing on the two player case, $(S_1^*, S_2^*)$ is a PSNE if **simultaneously**:
- $S_1^*$ is a best response for player I against player II's $S_2^*$
- $S_2^*$ is a best response for player II against player I's $S_1^*$.

To find a PSNE in the two-player case, we may make up what's called a table of best responses. Still talking about the game of five, we make a two-column table:

| Player I's reduced strategy | Player II's best response |
| --------------------------- | ------------------------- |
| 1                           | B                         |
| 2                           | B                         |
| 3                           | A, B, C                   |
| 4                           | A, B                      |
| 5                           | C                         |
| 6                           | C                         |

We can do the same thing for player II's reduced strategies:

| Player II's reduced strategy | Player I's best response |
| ---------------------------- | ------------------------ |
| A                            | 5, 6                     |
| B                            | 5, 6                     |
| C                            | 2, 4, 6                  |

So by inspection, we see that the only pair of strategies which are best responses against each other are 6 and C.  Then, 6-C is the unique PSNE in this game.

Intuitively, following the extensive form, you can see that player I is pretty much guaranteed to win every time, unless they play irrationally/unoptimally. If you were player I, you have some winning option regardless of player II's first move. If you were player II, you would have to reduce your losses (because you have no winning payouts).

The result 6-C agrees with our intution about how the game should be played - player II has to try their best to cut their losses, given the assumption player I plays optimally.

Now, an important thing to note is that it becomes much easier to find a Nash equilibrium by observing the strategic form of a 2-player game. We simply look at the payoff that is simultaneously a maximum payoff for player I in their column and a maximum payoff for player II in their row (assuming that each column corresponds to one of player II's strategies, and each row is one of player I's strategy).

## Prisoners' Dilemma
The important thing to take away from this is that "stable" does not mean "good". A Nash equilibrium may exist, but the result is that neither benefits.

Consider this siutation: Two accomplices to a robbery are apprehended. The district attorney does not have sufficient evidence to convict unless one (or both) of them confess. The DA takes each prisoner separately and offers each of them the following deal:
- If you confess and the other does not, you get full immunity and the other guy gets 24 months in jail. Let us refer to this as the "immunity for testimony" case.
- If you both confess, both of you get 12 months in jail. Refer to this as the "two plea bargains" case.
- If neither of you confess, both of you get 6 months in jail. Refer to this as the "Held on a lesser charge" case.

There is no communication between the prisoners themselves.

Let us first consider the extensive form for this game.
![[Analysis of games 2022-09-12 11.16.51.excalidraw]]

At its core, the structure of this game is the same as Matching Pennies, but with different payoffs. The strategic form matrix is 

| $_I\text{\\}^{II}$ | C            | NC        |
| ------------------ | ------------ | --------- |
| **C**              | (-12•, -12•) | (0•, -24) |
| **NC**             | (-24, 0•)    | (-6, -6)  |

where the • indicates "best response". You can see that the Nash equilibrium here is for both of them to confess. 

Something to note here is that confessing is what we refer to as a **dominating strategy** for both player I and player II. That is, it is a best response for player I no matter what strategy player II chooses. Likewise, it is a best response for player II no matter what strategy player I chooses.  

(You can see that this is true because column 1 has best response marked for both of player II's vector entries, and row 1 also has best response marked for both of player I's vector entries).

Hence, the Nash equilibrium $\left<C, C \right>$ is a special "strong" form of NE called a dominating strategy Nash equilibrium. 

Now, despite this stability, we can see that there exists a payoff that is better for both players. Despite the fact that $\left<C, C \right>$ is a very strong form of the Nash equilbrium, we can see that $\left<NC, NC \right>$ pays off more for both players. This is a bit of a paradox.

The prisoners' dilemma (or more accurately, all games isomorphic to the prisoners' dilemma) is often used as an explanation for situations in which two parties end up with relatively low payoffs, even though there was an option which would have given both higher payoffs.

## Arms Race
Take an arms race, as an example. Both the USA and the USSR would be better off if they hadn't both escalated the arms race. In essence, there are two strategies (for the sake of simplifcation) - to either escalate or be pacifist.

Let $E$ be escalate, and $P$ be pacifist. Then, we define an arbitrary strategic form matrix as:
| $_{USA}\text{\\}^{USSR}$ | E            | P        |
| ------------------ | ------------ | --------- |
| **E**              | (-20•, -20•) | (50•, -100) |
| **P**             | (-100, 50•)    | (0, 0)  |

considering that:
- If both escalate, global stability is maintained at the expense of developing those weapons.
- If both remain pacifist, the status quo is maintained.
- If one escalates while the other is pacifist, one country will lose political control (and perhaps get blown up). The other country effectively becomes the sole global power.

Here, the payoffs, in an ordinal sense, are isomorphic to those of the prisoners' dilemma. Thus, the dominating strategy PSNE is for both countries to escalate.

## Price War
Consider another example - there exist two companies in an economic market engaged in a price war. Both companies have two strategies - to charge high prices for their products or charge low prices.

Let $H$ be to charge high prices, while $L$ is to charge low prices. Then, we define its strategic form matrix as: 
| $_{I}\text{\\}^{II}$ | H          | L          |
| -------------------- | ---------- | ---------- |
| **H**                | (20, 20)   | (-50, 50•) |
| **L**                | (50•, -50) | (0•, 0•)   |

- If both raise their prices, they both get rich.
- If only one raises, the one with lower prices claims the market.
- If neither raise their prices, nothing happens.

Again, we have a dominating strategy PSNE, $\left<L, L \right>$. Such an outcome is theoretically good for the consumers, but not for the companies.

So far, the PSNE concept has seemed to be a reasonable solution when applied to games like Five and the prisoners' dilemma. It gives believable outcomes. However it can be argued that this is due to:
- the presence of dominating strategies in the prisoners' dilemma.
- the presence of perfect information in Five.

There is a problem with the concept of pure strategy Nash equilibria in games without perfect information and without dominating strategies.

## Battle of the Sexes
Let us consider another game - the Battle of the Sexes. Here, a husband and wife want to go out together (in 1930s Spain, Madrid). The husband wants to go to the bullfights while the wife wants to go to the opera. Both think that having each other's company is more important than where they go. 

The husband would rather go to the bullfights than the opera, but would rather go to the opera with his wife than go to the bullfights alone. The other case applies. 

Additionally, they are unable to coordinate their actions. They essentially have to go to the place they intend to go to, and hope that the other person is there. That is, neither the husband nor the wife has any way of knowing whether or not the other goes to the opera or the bullfights.

(Go to September 14's notes!)