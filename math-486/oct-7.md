Last time, we found that there indeed did not exist any saddle points for the following matrix game:

|       | a   | b   |
| ----- | --- | --- |
| **1** | 2   | -1  |
| **2** | -2  | 3   |

So we instead turned to mixed strategies, where a player assigns each of their pure strategies a probability. We noted here that $\underline{V} = -1$ by playing strategy 1, and $\overline{V} = 2$ by playing stategy a. Notice that these are not the same, so there exists no value for this game. (sidenote: notice both $\underline{V}$ and $\overline{V}$ are relative to player 1.)

We considered the mixed strategy for player 1, the vector $p = (0.5, 0.5)$. Then, we considered player II's mixed strategy over their two pure strategies expressed in terms of $q$ (where the probability of playing strategy a is $q$), and plotted $q$ against player 1's expected payoff:

![[Oct 5 2022-10-05 11.52.18.excalidraw]]

And we found that the absolute worst that could happen to player 1 playing $p = (0.5, 0.5)$ is that player 2 will play $q=1$, or exclusively play pure strategy a, and therefore yield an expected payoff of 0.

## A range of mixed strategies for player 1
But what about other possible values of $p$? Suppose player 1 instead chooses $p_2 = (0.75, 0.25)$. Then player 2 again chooses $q$ such that their probabiltiy vector is $(q, 1-q)$. 

Then, the expected payoff (for player 1) is
$$(0.75*q*2) + (0.75*(1-q)*-1)+(0.25*q*-2)+(0.25*(1-q)*3)$$
where each term represents the probability that both players select a specific outcome multiplied by the payoff of that outcome. We find that the combination of these terms is simply $q$. We can again do a similar graph of $q$ versus player 1's expected payoff, which you can imagine is simply a straight line with slope 1. And so the worst case is that player 2 plays $q=0$, or plays strategy b all the time, and player 1 gets an expected payoff of 0.

Suppose player 1 now plays $p_3 = (1,0)$ and player 2 again uses $(q, 1-q)$. 

Then we find that the expected payoff is simply
$$(q*2) + ((1-q)*-1) = 3q-1$$
and graphing it gives us![[Oct 7 2022-10-07 11.17.34.excalidraw]]

Similarly, we can also let $p_4 = (0, 1)$, in which case we find that player 1's expected payoff becomes $3-5q$:

![[Oct 7 2022-10-07 11.20.32.excalidraw]]

Now, consider if we graph all of these together:

![[Oct 7 2022-10-07 11.22.21.excalidraw]]

Notice how all of these intersect at the point $(0.5, 0.5)$. Furthermore, notice how each of player 1's mixed strategies "rotate" about this point, so that all possible mixed strategies contain this point, but the slopes may be different. 

Intuitively, you can see how mixed strategies with the steepest slopes contain the lowest worst-case values; $p_4 = (0,1)$ and $p = (1, 0)$ both give the possibility for a -2 to occur. But notice how the other strategies $p_1 = (0.5, 0.5)$ and $p_2 = (0.75, 0.25)$ only have a worst-case of 0.

So intuitively, the $p$ which maximizes the minimum payoff will be the one where the graph is a horizontal line, still passing through $(0.5, 0.5)$. And noting that such a line is "between" $p_1$ and $p_2$ in rotational terms, we expect such a strategy $p = (p, 1-p)$ where $0.5 \lt p \lt 0.75$ (that is, player 1 plays strategy 1 with probability between 0.5 and 0.75).

## Equalizing strategies

So the question becomes: for which value of $p$ does the minimum value of the expected payoff become maximized - that is, what $p$ do we need for player 1's expected payoff to be 0.5, no matter what player 2 does?

Qualitatively, the answer to this is that the we want a value of $p$ for which the graph of expected payoffs against $q$ is a horizontal line, such that the value of $p$ makes the expected payoff for player 1 the same regardless of what player II does.

We now move to a definition:

> [!tip] Equalizing strategy
> In a two-person zero-sum game, an **equalizing strategy** is a mixed strategy for a player such that no matter what (mixed or pure) strategy the other player chooses, the expected payoff is still the same. 

Note that here, the equalizing strategy for player 1 is also the minimax solution.

To find the equalizing strategy for player 1 in our example, consider the general strategy $(p, 1-p)$.

Then, consider that we want to find some $p$ for which the expected payoff for player 1 using $(p, 1-p)$ against $q = (1, 0)$ is equal to the expected payoff for player 1 using $(p, 1-p)$ against $q = (0,1)$. Such a strategy is "rotationally" between these two strategies, and generates a horizontal line.

Consider that the expected payoff for $(p, 1-p)$ against $(1, 0)$ is
$$p*2 + (1-p)*-2$$
and against $(0, 1)$ is
$$p*-1+(1-p)*3$$
So solving for
$$(p*2) + ((1-p)*-2) = (p*-1)+((1-p)*3)$$
we find that $p = \frac{5}{8}$.

Then, the equalizing (and minimax) strategy for player 1 is $(p_1, p_2) = (\frac{5}{8}, \frac{3}{8})$. WIth these weights on player 1's pure strategies, player 1 gets an expected payoff of +0.5 no matter what player 2 does.

## Not all minimax strategies are equalizing

It's important to note that it just so happens the equalizing strategy is equal to the minimax strategy. (It also happens to be closely related to a Nash equilibrium.) But **not all equalizing strategies are minimax strategies** - it just so happens that the nature of this zero-sum game works out for us so that the two solutions are the same.

Consider the following matrix game:

|       | a   | b   |
| ----- | --- | --- |
| **1** | 4   | 4  |
| **2** | 5  | 7   |

We can easily see that $p = (1,0)$ is equalizing for player 1, because there is nothing player 2 can do to avoid a payoff of 4 against strategy 1.

But we can clearly see that if player 1 wants to minimize their maximum loss, they would choose strategy 2, where the minimum payoff is 5, instead of strategy 1, where the minimum payoff is 4. (It just so happens that player 1 always "wins" with a positive payoff here, but player 1 would still rather guarantee +5 rather than +4.)

It also follows that not all minimax strategies are equalizing. Player 1's payoff varies depending on how frequently player 2 plays strategy a or b against player 1's strategy 2. $p = (0,1)$ is a minimax solution, but is not equalizing.

## For player 2
Moving back to the matrix game from earlier:

|       | a   | b   |
| ----- | --- | --- |
| **1** | 2   | -1  |
| **2** | -2  | 3   |

Suppose we now apply the same concepts for player 2 instead of player 1. Then they have a general strategy $(q, 1-q)$, and we want to find $q$ such that the expected payoff for player 2 using this strategy is the same whether player 1 uses $p = (1, 0)$ or $p = (0, 1)$. (Again, note that these are "rotationally" the same about the point $(0.5, 0.5)$, and we chose it to make the math easier).

We will "invert" the payoffs in the matrix to denote that this is what player 2 "wins", rather than what player 2 loses. (Though the solution is still the same.) So we have

$$\begin{align}
-\left[(q*2) + ((1-q) * -1)\right] &= -\left[(q*-2) + ((1-q) *3)\right] \\
3q-1 &= 3-5q \\
q &=\frac{1}{2}
\end{align}$$

and so we find that player 2's equalizing strategy here is to play $(q_1, q_2) = (0.5, 0.5)$. This guarantees that player 2 loses $0.5$ no matter what player 1 does.

## Conclusion
So player 1 has a mixed strategy $p = (\frac{5}{8}, \frac{3}{8})$ which guarantees a payoff of at least (exactly) 0.5, no matter what player 2 does.

Additionally, player 2 has a mixed strategy $q = (\frac{1}{2}, \frac{1}{2})$, which guarantees that they lose no more than -0.5, no matter what player 1 does. 

So the minimax solution here is $S_{I} = (\frac{5}{8}, \frac{3}{8})$, and $S_{II} = (\frac{1}{2}, \frac{1}{2})$, and the value of this game is $\frac{1}{2}$.

(homework is not due Monday.)