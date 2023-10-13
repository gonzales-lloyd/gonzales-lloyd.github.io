We move to an analysis of two-person zero-sum games, beginning with the $2 \times 2$ case. The general game is of the form


|       | A   | B   |
| ----- | --- | --- |
| **1** | a   | b   |
| **2** | c   | d   |

where a, b, c, and d refer to arbitrary values.

We can break this down into two cases.

The **first case** is where eIther: 
- $a \geq b \geq d$ 
- $b \geq a \geq c$
- $c \geq d \geq b$
- or $d \geq c \geq a$. 

Consider the scenario where $a \geq b \geq d$, or case (1a); then $b$ must be a saddle point, since it is a row minimum (relative to $a$) and is also a column maximum (relative to $d$). So it holds that the minimax solution for such a scenario is $S_{I}^{\bigstar} = (1, 0)$ (to play strategy 1, always) and $S_{II}^{\bigstar} = (0, 1)$ (to play strategy b, always). Then the value is simply equal to the value of the cell in the saddle point, which in this case is $V = b$.

We can also consider case (1b), where $b \geq a \geq c$. Then it holds that $a$ is a saddle point, because it is a row minimum relative to $b$ and a column maximum relative to $c$; so it must comprise a minimax solution, where player 1 always plays strategy 1 and player 2 always plays strategy a. In a similar manner, the value of the game $V = a$.

You can see how this follows for (1c) and (1d). Then $d$ is a saddle point in case (1c), and $c$ is a saddle point in case (1d); you can figure out the minimax solution from there. 

Additionally, notice that from our theorem from last class:
> [!tip] Theorem
> Suppose a two-person zero-sum game has a value. Then, $(S_{I}, S_{II})$ is a Nash equilbrium if and only if $S_{I}$ and $S_{II}$ are both minimax strategies.

then these are all Nash equilibria.

In general, we will call this first case the **saddle point case**. In general, this includes the case where $a = b = c =d$. This is necessary so that we distinguish it from case 2.

The **second case** is all cases where case 1 does not hold - that is, there exists no saddle point (**and** is not the scenario where all cells are equal value). Then, we say that one of case (2a) or case (2b) holds.

- Case (2a) is where $a \geq b$, $b \leq d$, $d \geq c$, **and** $c \leq a$. 
- Case (2b) is where the inequalities are switched - that is, $a \leq b$, $b \geq d$, $d \leq c$, **and** $c \geq a$.

It's worth proving the remark that if case 1 does not hold, then case (2a) or case (2b) must hold. 

We know that either $a \geq b$ or $a \leq b$ by both subcases in case 2. If $a \geq b$, and assuming that we are not in case 1, then the following hold:
- $a \geq b$ implies that $b \leq d$, else we would be in case (1a) .
- $b \leq d$ implies that $d \geq c$, else we would be in case (1c).
- $d \geq c$ implies that $c \leq a$, else we would be in case (1d).

These four inequalities comprise case (2a), so the subcase holds.

In a similar manner, if $a \leq b$ and we assume we are not in case 1, then:
- $a \leq b$ implies that $a \leq c$, else we would be in case (1b).
- $a \leq c$ implies that $c \geq d$, otherwise we would be in case (1d).
- $c \geq d$ implies that $d \leq b$< otherwise we would be in case (1c).

These four inequalities comprise case (2b), so the subcase holds.

We refer to case 2 as the case of **separated diagonals**. This is because either $a, d \geq b, c$ or $a, d \leq b, c$. We may call this the "no saddle point case", though we will find that it is possible for some games to fall in both case 1 and case 2 if certain cells have the same value. That said, case 1 and case 2 cover everything, albeit with some overlap.

> [!tip] Theorem
> Given the $2 \times 2$ matrix game of form
> $$\left[\begin{matrix}
> a & b\\
> c & d\\
> \end{matrix}\right]$$
> where rows represent one of player I's pure strategies and columns represent one of player II's pure strategies, suppose case (2a) or case (2b) holds, where no saddle point exists and it is **not** the case that $a = b = c = d$, then a minimax solution comprised of the strategies $(S_{I}^{\bigstar}, S_{II}^{\bigstar})$ is given by:
> $$S_{I}^{\bigstar} = (p^{\star}, 1-p^{\star})$$ 
> where 
> $$p^{\star} = \frac{d-c}{a-b-c+d}$$
> and
> $$S_{II}^{\bigstar} = (q^{\star}, 1-q^{\star})$$ 
> where 
> $$q^{\star} = \frac{d-b}{a-b-c+d}$$
> and the value is
> $$V = \frac{ad-bc}{a-b-c+d}$$ 

Once we have proven this theorem, we've solved $2 \times 2$ matrix games - finding the value where a saddle point exists is easy. Once we've figured out how to find the value in all other cases, we're done.

To prove this theorem, we first need to verify that $S_{I}^{\bigstar}$ and $S_{II}^{\bigstar}$ are valid mixed strategies - that is, $p^{\star} \in [0, 1]$ and $q^{\star} \in [0, 1]$. To do this, let us set 
- $X_1 = d-b$
- $X_2 = a-c$
- $Y_1 = d-c$
- $Y_2 = a-b$

To prove case (2a), we have $p^{\star} = \frac{Y_1}{Y_1+Y_2}$ with $Y_1 \geq 0$ and $Y_2 \geq 0$. Additionally, it *cannot* be the case that $a = b = c =d$, which implies that $Y_1 \gt 0$ or $Y_2 \gt 0$ - that is, either $Y_1$ or $Y_2$ is strictly positive so that we avoid the case where $p^{\star} = \frac{0}{0+0}$.

Together, this implies that $0 \leq p^{\star} \leq 1$. 

Then, we have $q^{\star} = \frac{X_1}{X_1+X_2}$. In a similar fashion, $X_1 \geq 0$ and $X_2 \geq 0$, and together with the assumption that we *do not* have $a =b = c =d$, then either $X_1 \gt 0$ or $X_2 \gt 0$ so that we do not have $q^{\star} = \frac{0}{0+0}$. Then this implies that $0 \leq q^{\star} \leq 1$. 

Thus, we have demonstrated that $p^{\star} \in [0, 1]$ and $q^{\star} \in [0, 1]$ in case (2a).

We now move to case (2b). Again, note that $p^{\star} = \frac{Y_1}{Y_1+Y_2}$. In contrast to case (2b), we have $Y_1 \leq 0$ and $Y_2 \leq 0$. Assuming we *do not* have $a = b = c =d$, then this implies that either $Y_1 \lt 0$ or $Y_2 \lt 0$. Yet again, this implies that $0 \leq p^{\star} \leq 1$.

In a similar manner, $q^{\star} = \frac{X_1}{X_1+X_2}$ where $X_1 \leq 0$ and $X_2 \leq 0$. Then assuming that all values are not equal, then we have $X_1 \lt 0$ or $X_2 \lt 0$, and so it hodls that $0 \leq p^{\star} \leq 1$. 

So, we have demonstrated that $p^{\star} \in [0, 1]$ and $q^{\star} \in [0, 1]$ in case (2b) as well.

It's important to note that if you apply such formulas to case 1, you will find a $p^{\star}$ and $q^{\star}$ outside $[0,1]$. (It just so happens that in the $2\times 2$ case, this implies a saddle point.)

We have now proven that $S_{I}^{\bigstar}$ and $S_{II}^{\bigstar}$ are, at minimum, valid mixed strategies expressed in terms of $p^{\star}$ and $q^{\star}$ as described above. We now move to prove that $S_{I}^{\bigstar}$ and $S_{II}^{\bigstar}$ are minimax strategies.

Then, we have

|       | $q$   | $1-q$   |
| ----- | --- | --- |
| $p^{\star}$ | a   | b   |
| $1-p^{\star}$ | c   | d   |

Suppose that player 1 plays $(p^{\star}, 1-p^{\star})$. We will allow player 2 to play any mixed strategy (not necessarily with $q = q^{\star}$), so that player 2 plays $(q, 1-q)$. 

Then we find that the expected payoff for player 1 is
$$p^{\star}*q*a+p^{\star}*(1-q)*b + (1-p^{\star})*q*c + (1-p^{\star})*(1-q)*d$$
which is just the probability of playing a given cell multiplied by its payoff, summed all together.

So substituting our assumption for $p^{\star}$ in, we have
$$\frac{d-c}{a-b-c+d}*q*a+\frac{d-c}{a-b-c+d}*(1-q)*b + (1-\frac{d-c}{a-b-c+d})*q*c + (1-\frac{d-c}{a-b-c+d})*(1-q)*d$$

which you can see leads to terms
$$\frac{dqa-cqa}{a-b-c+d}+\cdots$$

We can factor the denominator out of the expanded terms so that we have

$$\frac{1}{a-b-c+d}(dqa-cqa+db-dqb-cb+cqb+aqc-bqc+ad-aqd-bd+bqd)$$

And cancelling like terms $dqa$, $db$, $cqb$, and $aqc$ gives us

$$\frac{1}{a-b-c+d}(-cb+ad)=\frac{ad-bc}{a-d-c+d}$$
Notice how the all the terms with $q$ have cancelled out - the expected payoff is independent of whatever player 2 chooses for $q$!

Therefore, assuming that player 1 plays a mixed strategy with $p = p^{\star}$, such that they have $S_{I}^{\bigstar} = (p^{\star}, 1-p^{\star})$, they have an equalizing strategy with a guaranteed (expected) safety level payoff of $\frac{ad-bc}{a-d-c+d}$ no matter what player 2 does.

In a similar fashion, let's suppose that player 2 plays $(q^{\star}, 1-q^{\star})$ against player 1 playing any arbitrary strategy $(p, 1-p)$. Then player 2's expected payoff (which again, is just probabilities times payoffs) is:

$$p*q^{\star}*a+p*(1-q^{\star})*b + (1-p)*q^{\star}*c + (1-p)*(1-q^{\star})*d$$

and so we end up with the substitution

$$p*\frac{d-b}{a-b-c+d}*a+p*(1-\frac{d-b}{a-b-c+d})*b + (1-p)*\frac{d-b}{a-b-c+d}*c + (1-p)*(1-\frac{d-b}{a-b-c+d})*d$$

which expands into terms
$$\frac{pda-pba}{a-b-c+d}+\cdots$$
such that factoring out the denominator gives us
$$\frac{1}{a-b-c+d}(pda-pba+pab-pcb+dc-bc-pdc+pbc+ad-cd-pad+pcd)$$

Again, we'll find that all of the terms containing $p$ cancel out, so we've again demonstrated that the expected payoff does not depend at all on whatever player 1 picks for $p$. The expected payoff for player 2 is

$$\frac{1}{a-b-c+d}(-bc+ad)=\frac{ad-bc}{a-d-c+d}$$
no matter what player 1 does, assuming player 2 uses $q = q^{\star}$ in their mixed strategy.

The two conclusions above demonstrates that player 1 guarantees they lose no more than $V$ and player 2 pays no more than $V$, so that we clearly have a set of minimax strategies. This proves the theorem because the guaranteed payoffs match, and therefore we have a value in this matrix game.

Let's demonstrate this with our old matrix game where we plotted out lines:

|       | a   | b   |
| ----- | --- | --- |
| **1** | 2   | -1  |
| **2** | -2  | 3   |

Observe that we have "separated diagonals" in that the signs of 1a and 2b are the same, and 1b and 2a are the same. Furthermore, we have no saddle points, because the cells with value 2 and value 3 dominate the cells with -1 and -2.

We will use the formulas here, noting that $a = 2$, $b=-1$, $c=-2$, and $d=3$.

We have
$$p^{\star} = \frac{d-c}{a-b-c+d}=\frac{3-(-2)}{2-(-1)-(-2)+3}=\frac{5}{8}$$

$$q^{\star} = \frac{d-b}{a-b-c+d}=\frac{3-(-1)}{2-(-1)-(-2)+3}=\frac{1}{2}$$

and we find that the value $V$ of the game is
$$\frac{ad-bc}{a-d-c+d}=\frac{2*3-(-1)*(-2)}{2-(-1)-(-2)+3}=\frac{1}{2}$$

Therefore, the minimax solution is $S_{I}^{\bigstar} = (p^{\star}, 1-p^{\star}) = (\frac{5}{8}, \frac{3}{8})$,$S_{II}^{\bigstar} = (q^{\star}, 1-q^{\star}) = (\frac{1}{2}, \frac{1}{2})$ and the value is $V = \frac{1}{2}$. This is the same solution we got when manually figuring out the equalizing strategies.

