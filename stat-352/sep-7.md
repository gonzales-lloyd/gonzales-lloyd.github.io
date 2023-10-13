Last time, we looked at permutations and combinations.  Permutations are concerned about the order of the set, while combinations are not.  An example of a combination is to choose 3 desserts from a menu of 10, while a permutation is listing your three favorite desserts from a menu of 10.  

The first is $10 \choose 3$, which is equal to $\frac{10!}{3!7!} = 120$. 

The second can be proven in a relatively intuitive way - we have 10 choices for the first one, 9 for the second, and 8 for the last.  So that's simply $P_3^{10} = \frac{10!}{(10-3)!} = 720$.

> [!example]
> A printed circuit board has eight different locations in which a component can be placed.  If five identical components are to be placed, how many different designs are possible?  

Intuitively, we can see that we would have 8 locations for the first component, 7 for the next, and so on. This is a combination problem, because order is not important (compared to a permutation problem, where order does matter.)

Note how the components are identical; if we place A in the first position and B in the second position, it's the same as putting A in the second position and B in the first position.  

So this is ${8 \choose 5} = \frac{8!}{3!5!} = 56$.

> [!example]
> A bin of 50 parts contains 3 defective parts and 47 nondefective parts.  A sample of 6 parts is selected without replacement.  How many different samples are there of size 6 that contain exactly 2 defective parts?  

This is a combination, because the order in which parts are picked does not matter.  When we get defective parts, we treat them as identically defective relative to the other defective parts in the sample - they're not distinct in how they're defective, or otherwise treated differently.  

Let's say for a moment that we only have 3 defective parts.  How many ways are there for us to get 2 defective parts?  That's $3 \choose 2$.

Let's also say for a moment that we just have 47 nondefective parts.  How many ways are there for us to get 4 nondefective parts (equivalent to getting 2 defective parts in the full problem)? That's $47 \choose 4$.

How do we change this into a meaningful value?  We can actually apply the multiplication rule here.  The odds of getting two defective parts (and thus four nondefective parts) is equal to the combined odds of getting two defective parts and four nondefective parts.  

This gives us:
$$\frac{3!}{2!1!}\times \frac{47!}{4! 43!}=535095$$

> [!note] why is using multiplication rule necessary?
>Note that if we took the odds of getting four defective parts alone, rather than multiplying it with the odds of also getting two defective parts, it would fail to consider the fact that there are several ways to get 2 defective parts from the set of 3 defective parts.
>
> While it is true that getting four defective parts implies getting two defective parts, we want to know all of the possible subsets that yield 2 defective parts. From a set of three defective parts, you'll note there are three distinct pairs of defective parts, each of which must be treated differently.


## Section 2.3
Probability is used to quantify the likelihood, or chance, that an outcome of a random experiment will occur.  For example, we might say that the chance of rain is 30%, a quantification of our feeling about the possibility of rain.  

The likelihood of an outcome ranges from the interval $[0,1]$, where 1 is certain and 0 is that it will not occur.  

The probability of an outcome is interpreted as the limiting value of the proportion of times the outcome occurs in $n$ repetitions of the random experiment as $n$ increases beyond bounds.  If we toss a fair coin a large number of times, it should come up heads half the time.  

For example, we might assign 0.2 to the probability that a given digital pulse has a corrupted pulse.  We might interpret this as implying that if we analyze many pulses, 20% will be corrupted.  

We usually denote probability as $P$, where $A, B, C$ are events and $P(A)$ is the probability of event $A$ occurring.   

When a sample space consists of $N$ possible outcomes that are equally likely, the probability of each outcome is $1/N$.

By extension, if a procedure has $n$ different simple events that are equally likely, and if event $A$ can occur in $s$ different ways, then $P(a) = \frac{s}{n}$. An example is the likelihood of rolling evens on a 6-sided die.  

> [!example]
> Assume that 30% of the laser dids in a batch of 100 meet the minimum requirements of a customer.  If a diode is selected randomly, what is the probability that the selected laser diode meets the customer's requirements?  

We've assigned a probability of 0.01 to each of the 100 outcomes. Because the event in question $E$ contains 30 outcomes of 0.01 probability each, then we conclude that $P(E) = 0.3$.

In such discrete sample spaces, we simply take the sum of its constitutent outcomes to find the probability of the overall event.

Then if we have an experiment with outcomes (a, b, c, d) with probabilities (0.1, 0.3, 0.5, 0.1), then if $A$ is the event $\{a, b\}$ and $B$ is the event $\{b, c, d\}$ and $C$ is the event $\{d\}$, then:
- $P(A) = P(a) + P(b) = 0.1 + 0.3 = 0.4$
- $P(A \cup C) = P(a) + P(b) + P(d) = 0.5$
- $P(A \cap B) = P(b) = 0.3$
- $P(C') = P(a) + P(b) + P(c) = 0.9$ 


> [!example]
> From a bin of 50 parts, 6 are chosen without replacement. The bin contains 3 defective parts and 47 nondefective. What is the probability that exactly 2 defective parts are selected in the sample?

This is similar to the question above, but note the difference in language - the number of possible *distinct* subsets or samples with 2 defective parts, versus the overall probability that we get 2 defective parts.

Our sample space is the set of all possible subsets of 6 parts being selected. The event is $A$, the subsets of 6 parts which contain 2 defective parts. Then the probability of A occuring is equal to the nubmer of ways in which $A$ can occur over the total outcomes in $S$.

We know that the number of ways A can occur is equal to 535,095, as found earlier. 

The total number of outcomes is equal to $50 \choose 6$, or about 15,890,700. The probability would then be 535095/15890700.

> [!example]
> Using the same conditions as above, what is the probability that no defective parts are in the sample?

Now, the event in question (previously A) is the set of all subsets where no defective parts are chosen, also equivalent to choosing 6 nondefective parts - that is, ${3 \choose 0} * {47 \choose 6}$. This works out to about 10,737,573.

As we found out earlier, there are 15,890,700 total possible samples, so dividing yields a probability of 0.676.

---
Let's talk about relative frequency. We can approximate probability by performing an empirical test of a procedure, where the relative frequency of event $A$ is equal to the number of times $A$ occurred over the number of times that the procedure was repeated. 

For example, in ten coin flips, we know that the probability of getting heads is 0.5; but the relative frequency of heads might actually be 0.7.

There are some axioms of probability that are fairly intuitive:

- $P(S) = 1$, where $S$ is the sample space
- $0 \leq P(E) \leq 1$ for any event $E$
- For two events $E_1$ and $E_2$ with $E_1 \cap E_2 = \varnothing$ (the two are disjoint events or mutually exclusive), then $P(E_1 \cup E_2) = P(E_1) + P(E_2)$

These axioms ensure that the probabilities assigned in an experiment can be interpreted as relative frequencies. It has some implications that follow:
- $P(\varnothing) = 0$
- $P(E') = 1 - P(E)$ for any event $E$
- If $E_1$ is in $E_2$, then $P(E_1) \leq P(E_2)$

## Section 2.4
Joint events are generated by applying basic set operations to individual events. These include:
- Unions of events, like $A \cup B$
- Intersections of events, like $A \cap B$
- Complements of events, like $A'$

