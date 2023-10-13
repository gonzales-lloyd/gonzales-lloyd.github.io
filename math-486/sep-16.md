This starts off at September 16, which lacks the notes from September 14's recording.

Consider that Five and the prisoners' dilemma have a Nash equilibrium that gives a sensible outcome. This is because both have a dominating strategy.

But what if we have a game without perfect information and no dominating strategies? The Battle of the Sexes was one such game, as was Matching Pennies. Here, the players have no way to coordinate their actions, nor do they have a dominating strategy.

So there are a few problems, but it still holds that the Nash Equilibrium was a reasonable solution concept. If somehow the players get the idea that if they both know separately they'll go to the bullfights, then they'll go to the bullfights together. But that doesn't know if they know separately they'll go to the bullfight and the opera.

This brings in the idea of an arbitrator putting these ideas in their heads. But perhaps the couple went to the opera last time, so they both come to the conclusion they'll go to the bullfight this time.

So long as people have the idea of the Nash equilbrium in their head, the PSNE will indeed happen. That's one possibility.

The other is the doover assumption, where players can adjust their strategies until everybody plays a best response against each other. Then you're done. We had an example of this last time, where the company engaged in a price war and adjusted their pricing strategies.

Let us come up with another example. Recall the game we played in the first day of class - where everybody picks a number between 0 and 100, and the person that comes closest to 80% of the average wins $5. Ties are split and invalid values thrown out.

In class, the average was 46.325, so the 80% line was about 37. The closest bids were at 35. There are actually three PSNEs here:
- Everybody bids 0 - there's no way to deviate here.
- Everybody bids 1. The 80% line becomes 0.8, so there exists no way to deviate (you could only go to 0).
- Everybody bids 2, in which case the 80% line becomes 1.6. You can't move off of 2 without losing.

3 and above are not PSNEs. Considering the fact that we didn't get close to the PSNE, there are a few reasons.
- There was no perfect information.
- There was no dominating strategy - the "correct" strategy depends on everybody else.
- There was no arbitrator. Nobody planted the idea of bidding something in particular in our heads, we just got the papers and put our bids down.
- There was no do-over; you couldn't change your bid after the fact.

But the most important: in many economic situations, players **do not necessarily act rationally**. This is because:
- Some games are too tough to "figure out" an optimal strategy for. You can figure out Five, but not this game without prior knowledge.
- Sometimes rules are difficult to understand. 
- Players may not take the game seriously, particularly if the stakes are low.
- And more.

Here's an interesting example. Consider the extensive form game below and find its PSNEs:
![[Disjoint 2022-09-16 11.21.55.excalidraw]]

Let's first consider the strategy $S_I^* = B$ and $S_{II}^* = a$. In this case, the payoff would be (6, 3).
- If player I decides to deviate to A, then their payoff goes from 6 to 0. Then there's no incentive to deviate.
- If player II decides to deviate to b, then their payoff goes from 3 to 3. There's no incentive to deviate either. 

Then, we can safely conclude that $(B, a)$ is a pure strategy Nash equilibrium. However, it is a very irrational one. If you're player II, you're probably not looking at playing $a$. If you ever got the chance to play, you would certainly pick $b$ instead of $a$, winning 5 instead of 0.

To suggest that player II would ever play $a$ is irrational if the game ever got to node $X$. As a result, $S_I^* = A$ and $S_{II}^* = b$ is a much more "natural" PSNE. Again, neither strategy has any incentive to change here.

So we've encovered an idea here. A more "natural" PSNE would not only be a Nash equilibrium for the whole game, but would restrict ourselves to the "subgame" starting at node $X$. That is to say, if the game started at $X$, it would not be a Nash equilibrium for player II in the one-player game. They're not playing their best response.

The idea is that we can find PSNEs for which "subgames" also have that as a Nash equilibrium. Such a PSNE is called a subgame-perfect equilibrium, known as an SPE. We may also call it a perfect Nash equilibrium.

In the example above, (A, b) is a perfect Nash equilibrium, while (B, a) is a Nash equilibrium, but is not perfect. We have found a special class of Nash equilibria - a refinement of game theory, as academics would call it.

Now, an important thing to note are differences in terminology.
| Shapley                           | Quint                                  |
| --------------------------------- | -------------------------------------- |
| SE (strategic equilibrium)        | NE (Nash equilibrium)                  |
| PSE (pure strategic equilibrium)  | PSNE (pure strategic Nash equilibrium) |
| SPE (subgame-perfect equilibrium) | perfect NE/perfect pure-strategy NE    |

Normally, we would agree with our textbook, but game theory at large uses the terminology on the right.

## Subgames
Keep the subgame starting at node $X$ in mind as we move forward.

Semi-formally, then given a game $G$ (a game tree with payoffs, moves, etc.) in extensive form, a subgame of $G$ is a subset $G'$ of $G$ such that
- it begins at one of $G$'s single noted information sets, or SNISs.
- all of the successors to the SNIS, as well as the SNIS itself, make up $G'$.
- if a vertex $V \in G'$, then any other vertex in an information set with $V$ in $G$ must belong to $G'$ and also to $V$'s information set in $G'$.

What exactly does the third condition mean?
![[Disjoint 2022-09-16 11.42.34.excalidraw]]

Intuitively, $G'$ is not a subgame. It satisfies the first two conditions, but not the third condition. This is because one of player III's information set vertex is not present in the subgame, despite some other vertices in the information set being present in the subgame. We need all the vertices in the information set for this to be a subgame.

A remark: for any extensive form game $G$, $G$ is a subgame of itself. 

Another definition: Given a game $G$, a subgame perfect equilibrium, or perfect NE, is a set of strategies $(S_1, \ldots, S_n)$ which is a PSNE even if restricted to any subgame of $G$. Note that the strategies must **not** be reduced strategies because it is necessary to check every subgame, even those which can be precluded by earlier moves. This is one such case where full strategies are necessary.

A theorem: every perfect NE is an NE. This follows because $G$ itself is one of the subgames you have to check. 

You may be wondering if perfect information has anything to do with perfect NEs. The answer is yes - another theorem is that every game with perfect information has a perfect NE (which is not necessarily unique). We have seen games, like Matching Pennies, without an NE. The proof is that we use something called backwards induction.





