We begin with a recap of concepts we've learned in the environment of mixed strategies.

> [!danger] On notation
> - The expression $S_{I}$ refers to a generic strategy.
> - The expression $S_{I}^*$ refers to an *assumed* Nash equilibrium strategy for player 1. (Formally speaking, it's one of the strategies that comprise the set of strategies composing a Nash equilibrium.)
> - The expression $S_{I}^{\bigstar}$ refers to an *assumed* minimax strategy for player 1.
>
> These have not been distinguished below, but they are different!!

Supose we have a two-person, zero-sum game represented by an $m \times n$ matrix $A$. Then, $\underline{V}$, which we've been calling the safety level for player 1, can be expressed as the maximum payoff over mixed strategies $p$ for player 1 over the minimum payoffs for the mixed strategies $q$ for player 2.

It turns out that we can express this mathematically as

$$\begin{align}
\underline{V} &= \min_{\substack{m \leq p}} \left(\max_{\substack{m \leq q}}\left(\text{expected payoff for player I under }(p, q)\right)\right)\\
&= \max_{\substack{p}} \left(\min_{\substack{q}}\left(\sum_{i=1}^{m} \sum_{j=1}^{n} p_i *q_j*A_{ij}\right)\right)
\end{align}$$

Denote this as $*$.

Any $p$ that attains the maximum in $*$ is called a minimax strategy for player 1.

We can also do the same thing for player 2.

Again, this is the minimum value over mixed strategy $q$ over the maximum value over mixed strategy $p$. That is,

$$\underline{V} = \min_{\substack{q}} \left(\max_{\substack{p}}\left(\sum_{i=1}^{m} \sum_{j=1}^{n} p_i *q_j*A_{ij}\right)\right)  $$

denoted $**$.

Any $q^*$ which attains the minimum in $**$ is called a minimax strategy for player 2. 

We now have the following lemma:
> [!tip] Lemma
> $$\underline{V} \leq \overline{V}$$
> for a two-person zero-sum game.

We can prove this lemma using a proof by contradiction. Suppose that on the contrary, $\underline{V} \gt \overline{V}$, and we have $p^*$ as a minimax strategy for player 1 and $q^*$ as a minimax strategy for player 2.

What happens, then, if $p^*$ and $q^*$ are played?

- a) Since $p^*$ is a minimax strategy for player 1, he must get a payoff of at least some $\underline{V}$.
- b) Since $q^*$ is a minimax strategy for player 2, she must lose no more than $\overline{V}$; in other words, player 1 must gain no more than $\overline{V}$.

Let us consider the amount $x$ that player 1 gets. Then, we have

- $x \geq \underline{V}$, from part (a)
- $\underline{V} \gt \overline{V}$, by assumption
- $\overline{V} \geq x$, by part (b)

which clearly yields a contradiction.

Now, if it turns out that $\underline{V} = \overline{V}$, we say that $V$ is the value of the game.

---
> [!tip] Theorem
> Suppose a two-person zero-sum game has a value. Then, $(S_{I}, S_{II})$ is a Nash equilbrium if and only if $S_{I}$ and $S_{II}$ are both minimax strategies.

We can prove this in the following manner.

Suppose that the value of a two-person zero-sum game is $V$. Then we must show two separate statements that imply the other is true:
- **Step 1:** We will show that if particular strategies $S_{I}^*$ and $S_{II}^*$ are minimax strategies, then $(S_{I}^*, S_{II}^*)$ is a Nash equilbrium.
- **Step 2:** We will show that if $(S_{I}^*, S_{II}^*)$ is a Nash equilbrium, then $S_{I}^*$ and $S_{II}^*$ are both minimax strategies.

We start with **step 1**. 

Suppose that $S_{I}^*$ and $S_{II}^*$ are minimax strategies. Then, the payoff for player 1 if $(S_{I}^*, S_{II}^*)$ is played must be $V$. Then, suppose that player 1 considers deviating away from $S_{I}^*$ against $S_{II}^*$. Because player 2 has guaranteed losing no more than $\overline{V} = V$ by playing $S_{II}^*$, there exists no strategy for which player 1 can expect to win more than $V$ by deviating. Therefore, player 1 cannot improve by deviation; that is, $S_{I}^*$ is a best response against $S_{II}^*$. The same argument holds for player 2, so it holds that $(S_{I}^*, S_{II}^*)$ is a Nash equilibrium.

We now move to **step 2**.

Suppose that $(S_{I}^{\bigstar}, S_{II}^{\bigstar})$ is a Nash equilibrium. What are the expected payoffs if these strategies are played?

Because this is a two-person zero-sum game, we can assume the payoffs are $(h, -h)$. Then, $h$ must be greater than or equal to $\underline{V} = V$, because we know that if player 1 were to switch to a minimax strategy, he would get a payoff of at least $\underline{V} = V$. Else, it would not be a best response, and therefore is not a Nash equilibrium strategy. (????)

The same holds for player 2. $-h$ must be at least $-\overline{V} = V$, because if player 2 were to switch to a minimax strategy, they would get a payoff of at least $-\overline{V}$.

So we have that $h \geq V$ and $-h \geq V \iff h \leq V$, so clearly $h = V$. Then, the NE $(S_{I}^{\bigstar}, S_{II}^{\bigstar})$ has an expected payoff of $(V, -V)$. But since player 2 cannot improve their payoff by deviating (since we assume a Nash equilibrium), player 1 is going to guarantee a payoff of at least $V$ by playing $S_{I}^{\bigstar}$.

So by definition, player 1 has maximized their minimum payoff (and guaranteed they lose no more than $V$, and therefore $S_{I}^{\bigstar}$ is a minimax strategy for player 1. The same holds for player 2; player 1 cannot improve their payoff by deviating against $S_{II}^{\bigstar}$, so player 2 has guaranteed that they lose no more than $V$ and $S_{II}^{\bigstar}$ is also a minimax strategy.

Then, we have proven that in a **two-person zero-sum game**, $\underline{V} = \overline{V} = V$ if and only if a Nash equilibrium in that game is composed of minimax strategies.

---

We will later prove the minimax theorem, originally proven by John von Neumann in 1932 before the concept of game theory was invented (with the first book in 1944 by Neumann and a coauthor). It states that all two-person zero-sum games with a finite number of pure strategies for both players have a value. 

Suppose that we have a two-person zero-sum game in which no value exists. Then, by the minimax theorem, such a game is one where both players have an infinite number of pure strategies. 

An example of such a game is "he who names the highest number wins." The idea is that if player 1 can somehow call a higher number than player 2 (and vice versa), they win. (We presume here that the game is only played once; if player 1 calls 1, and player 2 calls 2, player 2 immediately wins.) Calling the same number is a tie.

You can see how this yields an infinitely-large matrix, in which we have $\underline{V} = -1$ and $\overline{V} = 1$. There exists no way for either player to guarantee a "win", so there is no value here.

---

We move onto an analysis of 2-by-2 two-person zero-sum games. We will show how to find a minimax solution of any TPZSG in which both players have 2 pure strategies.

The general game is of the form
|       | a   | b   |
| ----- | --- | --- |
| **1** | a   | b   |
| **2** | c   | d   |

where a, b, c, and d refer to arbitrary values.