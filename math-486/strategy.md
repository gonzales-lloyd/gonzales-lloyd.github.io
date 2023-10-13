We've generally talked about how to analyze a game, but we haven't talked about how to play the game itself.


## Pure, full strategies
A (pure, full) **strategy** is a system that tells a player what to do at each of his information sets. 

Let's consider [[Information#Matching Pennies|Matching Pennies]]. In the game, player 1 has two strategies:
 - At information set $V_{11} = \{O\}$, player 1 can play heads.
 - At information set $V_{11} = \{O\}$, player 1 can play tails.

For player 2, they also have two strategies:
- At information set $V_{21}$, player 2 can play heads.
- At information set $V_{21}$, player 2 can play heads.

Let's consider "Five". What would be an example of a strategy for player 1?

Player 1 has four information sets; we need to tell him what to do at each of those. (Note that we're just considering a notion of a strategy for now; this isn't necessarily a smart/winning strategy, and does not reveal innate advantages.)
- At $V_{11}$, say "1".
- At $V_{12}$, say "3".
- At $V_{13}$, say "1".
- At $V_{14}$, say "1".

Since each information set contains exactly one node - that is, there is perfect information - we can associate each information set with a particular node and abbreviate this by stating
$$O-1, B-3, C-1, G-1$$
This allows us to avoid referring to information sets when we only really need to refer to a specific choice at a single node.

Note that:
- Even though there is only one choice at $G$, we still need to specify it. Player 1 may only have one move, but we still need to say what that is so the math works out.
- Even though player 1's choice at $B$ precludes the game from ever reaching $G$ -  we'd never reach $G$ from $B$ - because of the notion of a full strategy, we must still specify it. This is notable when we talk about reduced strategies.

We can list, in full, player 1's possible strategies:
- O-1, B-1, C-1, G-1
- O-1, B-1, C-2, G-2
- O-1, B-2, C-1, G-1
- O-1, B-2, C-2, G-1
- O-1, B-3, C-1, G-1 (listed above)
- O-1, B-3, C-2, G-1

Note that we can determine the number of possible strategies by multipying out the total number of possible choices across all their information sets. We will never be at both B and C in a single game, but that still needs to be defined in a full, pure strategy. 

Recall that player 1's information sets consist of the nodes O, B, C, and G; respectively, there are 1, 3, 2, and 1 choices at each, so there are 6 possible strategies.

As for player 2, note how their information sets consists of the nodes A, D, E, and F. Respectively, there are 2, 2, 1, and 1 choices at each, so there are 4 possible strategies:
- A-1, D-1, E-1, F-1
- A-1, D-2, E-1, F-1
- A-2, D-1, E-1, F-1
- A-2, D-2, E-1, F-1

Note that the third and fourth strategies are considered different strategies, even though they are *not* operationally distinct. In other words - playing "2" at node A means that D is never reached, and so functionally, they will play out the same way. The concept of operationally distinct strategies will become important when we move to **reduced strategies**, which is the opposite of a full strategy. 

(And the opposite of a pure strategy is a mixed strategy.)

For it to be not operationally distinct, your own strategy must be the one that prevents the game from reaching a future move of your own. Just because player 2 prevents you from reaching a certain node does not mean several of player 1's strategies become non-operationally distinct.

>[!tip]
> In general, a player $i$ has a total of
> $$\prod_{\{V_{ij}, \ldots\}} t_{ij}$$
> strategies, where $t_{ij}$ is the number of moves possible from each information set $V_{ij}$.

In general, the selection of strategies by the players in a game together with the outcome of any chance moves completely determines the outcome of the game. In other words - if you know the strategies of all the players, and you know exactly how all chance moves will play out, you can determine the final outcome of the game.

So let's say that in Five, the two players' strategies are:
- for player 1, O-1, B-1, C-1, G-1
- for player 2, A-1, D-1, E-1, F-1

Then using the Nash tree, we can "highlight" each path that the strategies take. Then, the contiguous path from the root to a leaf represents the outcome of a given game. This would represent the play "1-1-1-1-1" with the payoff (1, -1).


## Reduced strategies
So, considering the strategy and game above, let's ask:
- Why should we bother specifying to do at node D if player 2 will call A-2 in a given strategy?
- Why should we distinguish between the strategies A-2, D-1, E-1, F-1 and A-2, D-2, E-1, F-1?

So a **reduced** strategy, again, tells a player what to do at each information set. However, if a strategy at an early information set precludes the player from ever reaching one of his later information sets, the rule for the later information set is excluded.

Then, let's think about the reduced strategies for player 1 in Five.
- O-1, B-1, C-1, G-1 (Note how B and C are specified, because it is out of player 1's control if either B or C is reached.)
- O-1, B-1, C-2, G-1
- O-1, B-2, C-1 (If B-2 is played, it is impossible for the game to ever reach G.)
- O-1, B-2, C-2
- O-1, B-3, C-1
- O-1, B-3, C-2

Observe how we have only omitted redudnant information compared to our full strategies; there are still 6 strategies.

Consider player 2's strategies.
- A-1, D-1, E-1 (Note how F is impossible if A-1 is played.)
- A-1, D-2, E-1
- A-2, F-1 (Note how D and E are impossible if A-2 is played.)

Observe that not only have we omitted redundant information, but have actually reduced the number of strategies from 4 to 3. This is because of the number of subnodes from the nodes we have excluded. 

Let us go back to [[Information#Matching Pennies|Matching Pennies]]. Note that the strategies and reduced strategies are the same, because no "early" move by a player precludes a later information set for that player. (The tree only has depth 3 including the root; both players make exactly one move, so there are no additional moves to make "impossible.")

That is to say, when some player only has one information set, then the set of strategies and the set of reduced strategies are the same.  In general, the number of reduced strategies is always less than or equal to the number of full strategies.

Let us also consider Five with a Die. There are 24 full strategies for player 1, which can be shown by using the product formula as shown earlier. There are also 16 full strategies for player 2.

Of note is that there are 24 reduced strategies for player 1, but only 9 reduced strategies for player 2. **Exercise: why?**


