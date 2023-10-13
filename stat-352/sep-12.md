# Section 2.4

Friday recitation shall be moved to SEM 326.

Consider the following table:

|                    | Center | Edge | Total |
| ------------------ | ------ | ---- | ----- |
| Low contamination  | 514    | 68   | 582   |
| High contamination | 112    | 246  | 358   |
| Total              | 626    | 314  | 940   |

where center and edge refers to the location of a wafer in the sputtering tool.

Let's say that we want to find the probability that the wafer is from the center of the sputtering tool and contains high levels of contamination. Note the term "and" - this indicates a set intersection, or $P(C \cap H)$. This would be $\frac{112}{940} \approx 0.119$.

What if that said "or" instead? Then, we would have $P(C \cup H)$, or $\frac{514+112+246}{940} \approx 0.928$.

This is a demonstration of the union or addition rule, in which $P(A\cup B) = P(A) + P(B) - P(A\cap B)$. You can see why we would subtract the intersection, to avoid counting the same things twice.

Consider a case where we draw a card from a standard 52-card deck. Then what is the probability the the card is an ace or a club? We count the aces separately, and then the clubs separately. We avoid counting the ace of clubs twice. This gives us $13 + 4 - 1$, or $16/52$.

There are cases where you may prefer the intuitive or the formulaic approach.

By definition, if $A$ and $B$ are mutually exclusive such that $P(A \cap B) = 0$ and so $A \cap B = \varnothing$, then it holds that you do not need to subtract the intersection. By extension, for a collection of mutually exclusive events, such that $E_i \cap E_j = \varnothing$ for all pairs, then the probability of the union of those events is simply the sum of each individual probability.

That is, if $E_1, E_2, \ldots, E_k$ are mutually exclusive, then $P(E_1 \cup E_2 \cup \ldots \cup E_k) = P(E_1) + P(E_2) + \cdots+ P(E_k)$.

For example, letting $X$ be the pH of a sample, then
$P(6.5 \leq X \leq 7.8)$ is equal to the individual probabilities of any subintervals.

## Section 2.5
There are certain events that are conditional, such that $B$ is augmented if $A$ occurs.

For example, $P(B|A)$ is the probability of an event B under the knowledge that the outcome will be in event A. This is also known as the **conditional probability** of B given A (which is to say, A has occurred). Note how the order of B and A are significant.

For example, consider the following table:

|                    | Has surface flaw ($F$) | Does not | Total |
| ------------------ | ---------------------- | -------- | ----- |
| Is defective ($D$) | 10                     | 18       | 28    |
| Not defective      | 30                     | 342      | 372   |
| Total              | 40                     | 360      | 400   |

If we are told to find the probability of $D$ given that a part has a surface flaw, we restrict our sample space to just the set of 40 elements with a surface flaw. Then, $P(D|F) = \frac{10}{40}$.

Observe how we do not even consider the other 360 parts, because $F$ has not occurred and so the conditional does not hold.

For $P(F|D)$, we restrict our sample space to just the 28 defective parts. Then, we have $P(F|D) = \frac{10}{28}$.

To find the probability of D given that a part is not a surface flaw - that is, $P(D|F')$, we restrict our sample space to the set of 360 elements, and the calculation is $\frac{18}{360}$.

There also exists a formula approach, where $P(A) \gt 0$:
$$P(B|A) = \frac{P(A \cap B)}{P(A)}$$
where $P(A\cup B$) and $P(A)$ can be simplified to the number of outcomes in both sets, respectively.

## Section 2.6
We can rearrange the conditional probability formula so that we have
$$P(A\cap B) = P(B|A) \times P(A)=P(A|B)\times P(B)$$
This is actually the multiplication rule.

> [!example]
> There are 5 green and 7 red balls in a bag. Two balls are selected one by one without replacement. Find the probability that the first ball is green and the second is red.

Let $G$ be the event that the first ball is green, and $R$ is the event that the second ball is red.

Interestingly, this is $P(G) \times P(R|G)$. It then holds that this is actually equal to $P(G\cap R$), though it may be less clear than what we have used in the past. Think of this as grabbing two balls at the same time, rather than two separate balls. Then, $P(G \cap R)$ represents the probability of grabbing both a green and a red ball, equivalent to grabbing a green ball and then a red ball.

Note how grabbing a red ball and then a green ball is also $P(G \cap R)$, despite it representing a different event. This is because the underlying probabilities remain the same, as well as the individual terms multiplied together in the multiplication rule.

For example, if there is a likelyhood of 0.9 for a part to pass the first stage, and 0.95 to pass the second stage, then we simply multiply these values together to find the probability of passing both stages.

![[Sep 12 2022-09-12 13.53.05.excalidraw]]

Observe that this is true because $B \cap A$ and $B \cap A'$ are mutually exclusive.

So for any two events $A$ and $B$, 
$$P(B) = P(B \cap A) + P(B\cap A') = P(B|A) \times P(A) + P(B|A') \times P(A')$$

For example, information about chip contamination is shown below.
| Probability of failure | Level of contamination | Probability of Level |
| ---------------------- | ---------------------- | -------------------- |
| 0.1 = F given H                    | High                   | 0.2 = $P(H)$                  |
| 0.005 = F given H'                 | Not high               | 0.8 = $P(H')$                    |

Let $F$ be product failure and $H$ be a high level of contamination.

For example, the probability of failure is equal to 0.024, equal to $P(F|H) \times P(H) + P(F|H') \times P(H')$. We can interpret this as a weighted average of the events.

## Section 2.7
Two events $A$ and $B$ are independent if any one of the following equivalent statements are true:
- $P(A|B) = P(A)$
- $P(B|A) = P(B)$
- $P(A \cap B) = P(A) \times P(B)$

The first two statements show that regardless of whether or not the given event occurs, the conditional event occurs with the same probability. This is most correlated with the intuitive definition of independence.

The final statement is often used to prove independence. Recall that
$$P(A|B) = \frac{P(A\cap B)}{P(B)}$$
so it holds that if they are independent, then $P(A|B) = P(A)$ so that
$$P(A) = \frac{P(A\cap B)}{P(B)}$$
and so $P(A \cap B) = P(A) \times P(B)$.

> [!tip]
> This has an important fact that follows from it - if two events are mutually exclusive and both have **nonzero** probability, then they are not independent. In the case where one event has zero probability, then it follows that any other event with that event is independent and mutually exclusive.

For example, consider sampling with replacement. Say we have two parts selected randomly from a bin of 50 parts - 47 nondefective, 3 defective - and assume that the second part is replaced before the next one is selected.

Then, what is the probability that the second part is defective given that the first part is defective?

Remember the important statement - this is with replacement. Again, we only focus on the state of the system after $A$ has occurred, that is, that the first part is defective. Then $P(B|A) = \frac{3}{50}$, because $A$ has already occurred, but $A$ has no bearing on the odds of getting another defective part, because the defective part was replaced.


