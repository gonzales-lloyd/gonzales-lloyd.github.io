## Overview
Let us move back to the use of Nash equilibria in Oligopoly theory.

Our goal here is to show, using game theory (in particular, the concept of Nash equilibria), that oligopoly (specifically duopoly) is in between the "badness" of monopolies and the "goodness" of perfect competition.

## Basic economics: Demand and supply curves
Let's talk about markets, specifically demand and supply curves. When the price of a good goes up, the less is demanded in the market. Pretend that you have coffee that you can buy at $5.00 a can. That coffee sells a certain amount in the market, and due to some factors, suppose that it goes up to $8.00 a can. Then, the amount demanded by the market will go down; they'll switch to something else. Some people will drink less, or they'll switch to tea, but in general, if the price of something goes up, people will want less of it.

Economists have a way of modeling this. Noting that the price is the independent variable and demand is the dependent variable, we might normally put the price on the $x$-axis. But economists do it the other way around, so you have
![[Sep 23 2022-09-23 11.12.01.excalidraw]]

Now, if the price goes up, then suppliers are going to want to produce more. But because nobody's buying it, the price will likely go down.

But say that the price goes down. The consumers would love that, but the producers don't want to produce it at that price. Then, it's going to go up. 

Eventually, the price will end up at what we call an equilibrium price, where the value of $Q$ at that point is known as the equilibrium quantity. In an efficient market, the equilibrium point would represent the quantity produced and sold, as well as the price it's sold at.

## Setup
Suppose that we have a market supplied entirely by two firms - that is, a market representing a duopoly. 
- Firm 1 has some output level $y_1 \geq 0$.
- Firm 2 has some output level $y_2 \geq 0$.

We can treat this as a two-player game in which the output levels are the strategies for the players. This is different from the other games we've considered so far because the strategies are continuous, not discrete; there are an infinite number of possible output levels, so they have a continuum of strategies rather than a finite set. 

But the concept of Nash equilibria still applies, if you can find a case where both firms are playing best responses against each other. (That idea being that there may exist a set of strategies - one for each player - which are best responses against each other.) (Remember optimization from calculus? It comes back here, because of that continuous set of strategies.)

This is known as as the Cournot duopoly model, named after a French economist predating the idea of game theory.

Notice that the supply/demand model is practically a one-to-one function between the quantity of market demand to price. So we can think of the price as a function of amount produced, where $p(q)$ is the price at which $q$ can be sold. Notice that $\frac{\mathrm{d}p}{\mathrm{d}q} \lt 0$ for all $q$; in other words, if you want to sell more, you're going to have to charge less. 

## Function definitions
In our model, note that $q = y_1 + y_2$. There exist two other parameters:
- $c_1(y_1)$, which is the cost for firm 1 to produce $y_1$;
- $c_2(y_2)$, which is the cost for firm 2 to produce $y_2$.

Then in general, $\frac{\mathrm{d}c_1}{\mathrm{d}y_1} \geq 0$ for all $y_1$, and $\frac{\mathrm{d}c_2}{\mathrm{d}y_2} \geq 0$ for all $y_2$. That is to say, the more you make, the greater the cost to produce that amount. (Not at a per-unit level, but overall.)

In general, profit is equal to revenues minus costs. But notice that beause the revenue depends on the price you can sell it at, which in turn is $q = y_1 +y_2$ and is therefore dependent to the other firm's output level.

For firm 1, let us define the profit function as
$$\begin{align}
\pi_1(y_1, y_2) &= (\mathrm{price})*(y_1) - (c_1*y_1)\\
&= p(y_1+y_2) *y_1 - (c_1*y_1)
\end{align}$$
where $p(y_1+y_2)$ is the price as a function of the two firms' output levels. Then for firm 2, their profit function is
$$\begin{align}
\pi_2(y_1, y_2) &= (\mathrm{price})*(y_2) - (c_2*y_2)\\
&= p(y_1+y_2) *y_2 - (c_2*y_2)
\end{align}$$

and we call $\pi_1$ and $\pi_2$ **payoff functions**. This is the continuous version of our payoffs that we are more familiar with.

## Finding the NE
We will now look for Nash equilibria in the game - that is, the output levels $y_1^c$ and $y_2^c$ such that *both* of the following are true:
- $\pi_1(y_1^c, y_2^c) \geq \pi_1(y_1, y_2^c)$ for all $y_1 \geq 0$
- $\pi_2(y_1^c, y_2^c) \geq \pi_2(y_1^c, y_2)$ for all $y_2 \geq 0$

In other words, that means that the best responses produce a profit for firm 1 greater than or equal to any other of firm 1's response against firm 2's $y_2^c$. The same goes for firm 2, as well. That is to say, $y_2^c$ is a best response against $y_1$, and vice versa.

Assuming that the functions $\pi_1$ and $\pi_2$ are well-behaved, we can find $y_1^c$ and $y_2^c$ by setting
$$\frac{\partial \pi_1}{\partial y_1}(y_1^c, y_2^c)=\frac{\partial \pi_2}{\partial y_2}(y_1^c, y_2^c)=0$$
such that we find the maxima of the functions. If we wanted to, we could move towards the second derivative test to assert that they are maxima, but simpler cases exist.

In the simplest case, let's pretend that the the demand curve is given by
$$p = a-b(y_1+y_2)$$
such that in this case, the demand curve is a straight line:
![[Sep 23 2022-09-23 11.43.19.excalidraw]]

which is easier to analyze. Then we note that the production cost function is
- $c_1(y_1) = 0$ for all $y_1$
- $c_2(y_2) = 0$ for all $y_2$
which is similar to producing air, which is free to produce, but the market still demands it because it's needed.

Then we have 
$$\begin{align}
\pi_1(y_1, y_2) &= \underbrace{(a - by_1 - by_2)}_\text{The price function for firm 1}*y_1-\underbrace{0}_\text{Production cost}\\

&= ay_1 -by_1y_2-by_1^2
\end{align}$$
and the same for firm 2:
$$\begin{align}
\pi_2(y_1, y_2) &= (a - by_1 - by_2)*y_2-0\\

&= ay_2 -by_1y_2-by_2^2
\end{align}$$
and we now move to calculate the partial derivatives:
$$\frac{\partial \pi_1}{\partial y_1} = a-2by_1 -by_2$$
$$\frac{\partial \pi_2}{\partial y_2} = a-2by_2 -by_1$$
and note that in the first case, the partial derivative equals 0 when $y = \frac{a-2by_1}{b}$, and in the second case, the partial derivative equals 0 when $y = \frac{a-2by_2}{b}$.

Note that we have to equations in two unknowns, which solves when $y_1 = y_2 = \frac{a}{3b}$.

Then we note that that the Nash equilibrium in this example is $y_1^c = \frac{a}{3b}$ and $y_2^c = \frac{a}{3b}$. This is our expectation when we have the given market with all of the other assumptions we've made.