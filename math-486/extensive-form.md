Consider the following game, called "Five."

Two players take turns. The first player calls "1." The second player calls either "1" or "2". Then, the first player calls "1", "2", or "3". This continues indefinitely.

The winner is the player who makes the cumulative total equal to exactly 5. A player is not allowed to make the total go over 5. He or she wins from the other player an amount equal to whatever his last call was.

(Note the customary rule is to let players be named by roman numerals.)

Here's an example:
- Player 1: 1
- Player 2: 1
- Player 1: 2
- Player 2: 1

Observe how player 2 is required to play "1", as per the rules. As a result, player 2 wins $1 from player 1. 

This kind of analysis is part of what we know as "extensive form", or the "Kuhn tree", of the game. This is a diagram that shows all the possible paths the game could take.

For example, 
![[Drawing 2022-08-29 11.26.43.excalidraw]]

Here, we have drawn out every possible way the game can play out. The tuples at the leaves of the tree represent the payouts for each player playing the game, such that $(x, y)$ is that $x$ is the payout for player 1 and $y$ is the payout for player 2.

Additionally, we may label each vertex of the tree (including leafs/terminal endings, as well as the root). In the graph above, for example, we might label elements left-to-right, then top-to-bottom. (Although not shown, the set of all vertices is $V = \{O, A, B, C, \ldots, M\}$, where $O$ is the root.)

## Formal definition

Formally, to specify an $n$-person game in extensive form, we need:
1. A player set $N = \{1, \ldots, n\}$. Note that when $n$ is small, Roman numerals are used for the set.
2. A rooted directed tree, which is to say that each edge has a direction to it. (In the example above, the edges are from left to right; the direction in which time is going.) Additionally, some root, the "starting state", must exist. The tree consists of:
	- A set of vertices (or nodes) $V$ that correspond to possible "positions" in the game. There are two types of nodes:
		- non-terminal nodes, where a particular player (or "chance") has to make a move. Because we have labeled left-to-right, it holds we can state that the set of non-terminal nodes in our example is $V_{NT} = {O, A, \ldots, G}$.
		- terminal nodes, where the game has ended and an $n$-dimensional payoff vector is assigned. We can state that the set of non-terminal nodes in our example is $V_T = \{H,\ldots,M\}$. 
	- A set of directed edges $E$, which correspond to the possible moves in the game.
3. A payoff function $h : V_T \rightarrow \mathbb{R}^n$  which assigns to a terminal vertex a payoff vertex.
4. A set of [[Information|information]] sets $\{V_{ij}, \ldots\}$ for a player $i$ (where $j$ refers to which information set it is for a given player), for which:
	1. each $V_{ij}$ consists only of nodes at which it is player $i$'s turn to move.
	2. Player $i$ cannot distinguish which among the nodes of $V_{ij}$ the game is at, when it is their turn to move.
	3. At each of nodes of $V_{ij}$, player $i$ has the same moves available to them. Otherwise, they could distinguish among the nodes.
		- This extends from 4.2, but in [[Information#Matching Pennies|the matching pennies game]], if player 2 could only flip tails if player 1 had also flipped tails, then player 2 would actually know where they are in the extensive form. In turn, this violates the idea of an information set.
	4. No path through the tree can pass through $V_{ij}$ more than once. 

There are also other components, which will be discussed later on.

The fundamental idea is that a path through the tree represents a possible play of the game, like our "1-1-2-1" play in the example above.
