Recall that given a game $G$, a subgame perfect NE is a set of full (not reduced) strategies $S_1, \ldots, S_n$ which is a PSNE even if resetricted to any subgame of $G$.

Every game with perfect information has a perfect NE that demonstrates a procedure which takes as input any extensive form game with perfect information and outputs a Nash equilibrium. This procedure is called backwards induction, or BI. (This also includes games with chance nodes - in this case, take the node with the higher expected payoff for the player that's making a decision.)

Let us consider Five. Begin at $G$, where the game is (effectively) already decided; its payoff is (1, -1). Then we would say that player I would play G-1. We would then effectively "eliminate" G, and would instead replace it with the payoff node (1, -1). 

Then, player II at node D has two decisions - to play 1 and get the newly-created payoff node (1, -1), or to play 2 and get (-2, 2). Then we say that player II would play D-2.

In essence, this process essentially solves every single subgame. At each last-decision node, such that the node causes the game to end, we replace that node with the decision that gives the current player the best outcome. We continue this repeatedly until we end up at the root of the tree, at which point we get a singular node with a payoff. (Note how this forces us to evaluate **all** the subgames, thus creating a full strategy rather than a reduced strategy.)

At each step, we record the optimal strategy for a given player. In our case, this gives us:
- for player I, G-1 B-3 C-2 O-1
- for player II, D-2 E-1 F-1 A-2

Thus, in conclusion, the perfect NE is the set of strategies above, with payoff (2, -2).

(By extension: if every perfect information game has a perfect NE, and all perfect NEs are NEs, then every perfect information game has an NE.)

We mentioned that perfect NEs are more "natural", though they may not necessarily happen in real life.

Let us now consider a nuclear holocaust. Here, the moral is that the perfect NE is not the "natural" NE that would occur in real life.

Suppose that in increasing world tensions, the USSR is considering a nuclear first strike against the USA. If they do, they wipe out about 70% of the USA's industry and population, leaving the USA with a decision - should it strike back?

If the USA does, then mutually assured destruction occurs.

We basically have the following extensive form game:
![[Sep 19 2022-09-19 11.18.46.excalidraw]]

where the USSR is player I, and the USA is player II. We have three distinct outcomes;
- MAD, which means everybody dies. (-20, -20)
- The USSR dominates. (5, -10)
- Nothing happens. (5, -10)

Using backwards induction, we observe that the perfect NE is for the USSR to attack and the USA to not counterattack.

But another NE, which is not perfect, is for the USSR to not attack and for the USA to counterattack.

In this case, the non-perfect NE is the one that actually occurred. This shows that the perfect NE makes sense, but perhaps not always in real life.

Consider another example in Matching Pennies, which demonstrates that it is possible for a game to have no PSNEs. Again, its extensive form is
![[Information 2022-08-31 11.24.26.excalidraw]]

and its strategic form is
![[Strategic Form 2022-09-07 11.07.00.excalidraw]]

where player I's best responses are in the top-left and bottom-right corners, while player II's best responses are in the top-right and bottom-left corners.

Observe that there exists no NEs - or PSNEs, for that matter. No given set of strategies exist where both players are playing their best responses. Later, we will need to extend the theory of strategies to the idea of "mixed" strategies, which will be covered later on.

Now, remember that Nash equilibria are very widely used throughout game theory. We can use them to "solve" non-cooperate games, like the migration game of mathematical biology.

We have a player set $N = \{1, \ldots, n\}$ of animals. We also have a landscape $\mathscr{T} = \{T_1, \ldots, T_l\}$ of territories. We define the strategies for each of the players as the decision of the single territory they live in.

The payoffs for this game are dependent upon two factors:
- the number of other animals choosing to live in the same territory that another animal chooses. Animals living with other animals could be good or bad - perhaps lions want to stay together, but prey doesn't want to stay with the lions.
- Everything else - the weather, the resources available, the physical features of the territory, and so on.

Let us define $h(i, t, k)$ as the payoff to animal $i$ if it chooses to live in territory $T_t$, and there is a population of $k$ players living there, including itself.

A **competitive** migration game, or CMG, is a migration game in which $h(i, t, k)$ is nonincreasing in $k$ for all $i, t$. (Analogously: in a congestion game, if I choose to drive on the highway, then my payoff only goes down as more people choose to drive on it, as well.)

Consider that $A_1$ can choose to live in $T_1, T_2, \ldots, T_l$.. Then, the next animal, $A_2$, has a very large information set to choose from - they have $l$ nodes in their information set. $A_3$ has $l^2$ nodes in their information set, and so on. At $A_n$, there are $l^n$ terminal nodes. 

We now state a theorem here: any CMG has a PSNE. We might be able to develop a NE that describes a natural set of decisions that animals will take. 

We'll prove this by using mathematical induction on the parameter $n$. In mathematical induction, we suppose that we have a math statement or theorem which has a parameter $n$. Here, our theorem is that any CMG has a PSNE, and our parameter is the number of animals $n$.

One way to prove that a theorem is true for all $n$ is to do the following:
- Prove that it is true for $n=1$ (the base case - easy)
- Prove that if it is true for $n = N-1$, then it's true for $n=N$. (Or the opposite: if it's true for $n$, it should be true for $n+1$ as well.) This implies that it's true for $n=2$, which implies it's true for $n=3$, and so on.

