As described in [[Chance Moves]] and [[Extensive Form]], note that at any stage of "Five" or "Five-with-a-die", when it is a player's turn to move, he/she knows exactly where he/she is on the tree.

That is to say, they know the complete history of the game (and its potential outcomes). We often say that such a game is a **perfect information** game.

That said, games without perfect information are still reasonable to consider.

## Matching Pennies
Matching Pennies is another two-player game that is well-referenced in literature.

> [!info] An aside
> This is similar to the game "odds and evens", where two players throw up either one finger or two fingers at the same time. One player wins if the sum is odd, and another wins if the sum is even.

In it, player 1 takes a penny, making it heads or tails without showing player 2. Then, player 2 does the same. Then, they simultaneously reveal their coins. If the pennies match, then player 1 wins $1 from player 2. Otherwise, player 2 wins $1 from player 1.

Let's consider the extensive form of such a game.

![[Information 2022-08-31 11.24.26.excalidraw]]

The circled nodes represent the "information set", in which player 2 does not know whether the game is at A or B when it is their turn to move. That is, the information set contains the possible states of the game based on the information you have. For player 2, they have no information about the state of the game (so they don't know where in the tree they are), so their information set consists of the nodes A and B. 

Thus, a larger information set means that there are more states that the game could be in at the time a player is to make a move.

Now, this allows us to extend the definition of the extensive form. 

We refer to an information set as $V_{ij}$, where $i$ is the (index of the) player to which the information set belongs to, and $j$ is the index of which information set for the player it is.

Then, in this game, $V_{11}$ refers to player 1's first information set. Here, it would be $V_{11} = \{O\}$.

For player 2's first information set, it would be $V_{21} = \{A, B\}$.

Now, it can be the case that an information set contains only one element. Consider the information sets for the game Five; our "circle" that we drew about two vertices in Matching Pennies would actually be many circles, and the circle would only encompass one node. Then:
- For player 1, $V_{11} = \{O\}$, $V_{12} = \{B\}$, $V_{13} = \{C\}$, and $V_{14} = \{G\}$.
- For player 2, $V_{21} = \{A\}$, $V_{22} = \{D\}$, $V_{23} = \{E\}$, and $V_{24} = \{F\}$.

> [!note]
> Observe how index $j$ simply counts up as we go from left to right, top to bottom, in the order that the vertices have been labeled.  The index $j$ reveals nothing about the depth of the node, not unless you actually figure out where $j$ refers to.

In a perfect information set game, it follows that the size of all information sets $V_{ij}$ is equal to 1 for all $i$ and $j$; that is, $|V_{ij}| = 1$ .