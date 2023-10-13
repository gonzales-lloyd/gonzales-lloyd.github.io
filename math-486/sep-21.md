Recall that we talked about migration games, where the player set was $N = \{1, \ldots, n\}$ of animals, occupying a set of territories $\mathscr{T} = \{T_1, \ldots, T_l\}$. In terms of strategies, each animal chooses a territory to live in.

Then, we defined $h(i, t, k)$ as the payoff to animal $i$ if it lives in territory $T_t$ with $k$ animals, including itself.

A competitive migration game (CMG) $h(i, t, k)$ is assume to be nonincreasing in $k$ for all $i$ and $t$. That is - no matter which animal you are and where you go, the more animals are there, the worse it is for you. There are some things to note:
- It is important to note that for the same population $k$ and perhaps the same animal $i$, changing $t$ may not produce the same payoffs. Perhaps one territory sucks for everybody.
- Additionally, changing $i$ for some territory $t$ and population $k$ may not produce the same payoff.
- However, the identities of the players do not factor into the payoff, such that $k$ strictly considers population, not the actual values of $i$ present in a certain territory.

Our theorem is that any CMG has a PSNE. We see from the extensive form that it is both complicated and lacks perfect information. So if you think about it, it should be quite surprising that an imperfect game with such complexity has a PSNE.

The proof uses induction on $n$, the number of players in the game. 

---
Math induction is a method for proving things in mathematics, especially in discrete mathematics. The idea is that we a property $P$ which is parameterized by a nonnegative integer $n$. We want to prove that the property is true for all such $n$. To do this, we need to do two things:
- Prove that the property is true when $n=0$ (or some other constant, the base step)
- Prove that if assuming the property is true for $n = N -1$, where $N$ is arbitrary, then the property is true for $n=N$. This is the inductive step (which may also be written as proving that if the property is true for $n=N$, it is also true for $n = N+1$.), and the assumption itself that the property is true for $n = N -1$ is called the **inductive hypothesis.**

A simple example is where we prove that for any nonnegative integer $n$, we have $1 + 3 + 5 + \cdots + (2n+1) = (n+1)^2$ - that is, the sum of the $n$ odd numbers starting from 1 is equal to $(n+1)^2$. We may denote this as $*$.

If $n=0$, then the expression becomes $1 = (0+1)^2$, which is true. So the base case is true.

We now assume that $*$ is true for $n = N-1$ - that is, 
$$1 + 3 + 5 + \cdots + (2(N-1)+1)=(N-1+1)^2 = N^2$$
and try to show that $*$ is true for $n=N$, or
$$1+3+5+ \cdots + (2N+1) = (N+1)^2$$
Notice that we can expand this to be 
$$\underbrace{1+3+5+ \cdots +(2(N-1)+1)}_{\text{Inductive hypothesis}} + (2N+1) = (N+1)^2$$
and given that we have assumed our inductive hypothesis, we may simplify this to be
$$N^2 + (2N +1) = (N+1)^2$$
which can be demonstrated to be a true statement, so the proof is complete.

There are a few variations on the above definition of mathematic induction:
- in the base step, we may prove the property for any particular value of $n$, commonly $n=1$ or $n=2$.
- in the inductive step, we may instead use $n = N+1$.
- in the inductive step, we may instead state that "if the property is true for $n = 1, 2, 3, \ldots$ *and* $N-1$, it must be true for $n=N$." This often takes more steps.

---

Moving back to our proof that all CMGs have PSNEs:

If $n=1$, then animal 1 simply needs to choose whatever territory $T$ that they feel is best. This is, of course, what would actually happen. This is a Nash equilibrium because they have no incentive to move anywhere else, given that they have been placed in the best territory to live alone in (in that animal's opinion). Then, this is also a PSNE in this one-player game.

Now, suppose that the theorem is true for all CMGs in which there are $N-1$ players and any arbitrary number $l$ for the number of territories. This is the inductive hypothesis, or what we are allowed to assume. We now want to show that this implies that any CMG with $N$ players has a PSNE.

Suppose that we have a CMG with $N$ animals and $l$ territories. By the inductive hypothesis, we can place animals $A_2, \ldots, A_N$ into the territories so we form a PSNE in this $N-1$player game.

Now, suppose that this PSNE places $k_t$ animals in territory $t$, where $t = 1, \ldots, l$ and so $k_1 + k_2 + \cdots + k_l = N-1$.  For example, perhaps we have a PSNE in which 
- 3 animals (2, 8, 7) are in $T_1$
- 2 animals (3, 6) are in $T_2$
- no animals are in $T_3$
- ...
- 4 animals (5, 9, 10, 12) are in $T_l$

So what do we do with $A_1$? Let $A_1$ go into whatever territory $t^*$ they like, given that they know the value of  $k_t$ for all territories $t$. $A_1$ will choose the territory $t$ which maximizes $h(1, t, k_t+1)$. 

This now gives us a new arrangement of animals. The question here is - is this a PSNE? Suppose that $A_1$ chooses territory $T_1^*$. Then the animals who have already chosen any other territory have no incentive to move, as they already chose their best response ahead of time. So these animals are happy. It's only $t_1^*$ in which animals will not be happy. 

Formally: any animal not in $T_1^*$ is still playing a best response against all the other players. The only possible players not playing a best response are the other animals in $T_1^*$.

Pretend we pick one of the animals in $T_1^*$, called $A_2$, and let them choose their favorite territory, given the $k_t$s. An important thing to note here is that if $A_2$ has left, then the $k_ts$ for all $t$ is exactly the same as it was before, since $A_1$ moved into $A_2$'s previous territory. And because the number has gone back down to what it was before, the other animals in $T_1^*$ have no incentive to leave.

$A_2$ will again solve the optimization problem that $A_1$ did, finding whatever maximizes $h(2, t, k_t+1)$, moving to $T_2^*$.  And again, the animals in $T_2^*$ may not be playing a best response, but all the animals not in $T_2^*$ will still be playing a best response against everyone else. The only possible players now not playing a best response are the other animals in $T_2^*$. So is this a PSNE?

Pretend we now allow $A_3$ to choose their favorite territory, given the $k_t$s for all $t$. You can see that this continues for some time, so the question is now - does there exist a point at which this process stops, and so we can call this a PSNE?

The answer is yes. In a worst-case scenario, every animal will move once. But no animal will ever be the "mover" more than once, because they will have already solved the best response for $h(n, t, k_t+1)$. Then, if any new animal moves to their territory after another leaves, they will have already found the best territory for $k_t + 1$.

As a result, the procedure must terminate at a PSNE in $n$ iterations or fewer. A case in which the procedure runs for fewer than $n$ iterations is where perhaps the new animal chooses to go to an empty territory, at which point nobody is happy with them moving there, so a PSNE exists given the assumption of the inductive hypothesis.

In turn, we have found a PSNE in the $N$-player case.

Of note is that the proof above suggests a natural process by which the animals might arrange themselves to form a PSNE. That is, there appears to be some process by which animals, exhibiting greedy behavior, will allow a system to settle into a PSNE.

---
We now move to the applications of Nash equilibria in economics, in a branch called oligopoly theory.

Monopolies are where there is 1 producer in a market. The opposite of a monopoly in a market is perfect competition, in which there are an infinite number of producers, which is considered very good (for the consumers), which is what we care about. In US history, agriculture was perhaps the closest to perfect competition we had, because of all the small farms and lack of large farms.

In between these, we have oligopolies. This is where we have some small numbers in a market - perhaps we have duopolies and triopolies, for 2 and 3 producers each. Perhaps there exist quadopolies and quintopolies.

Before the car market was filled with imports in the US, we had three producers - Ford, GM, and American Motors. That was a triopoly in the automotive industry. That's perhaps bad, because these three could get together and collude to harm consumers.

Now, we generally consider monopolies bad, and perfect competition good, where oligopoly in between is "good" if it's closer to perfect competition than not.

The Cournot duopoly model explains this.

