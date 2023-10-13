Continuing section 2.7:

> [!example]
> Two parts are selected randomly without replacement from a bin of 50 parts. The bin contains 3 defective parts and 47 nondefective parts. Let A and B denote the events that the first and second parts are defective, respectively.
> 
> What is the probability that the second part is defective?

Note that this is done *without replacement*. 

First, let's assume that the first part is defective; in other words, $P(B|A)$. In our first selection, we have 3 defective and 47 non-defective, choosing one defective part. Then, we select a defective part from 2 defective and 47 non-defective.

Calculating $P(B|A) = \frac{2}{49}$, since we are already given $A$. 

But we're not actually given whether or not $A$ occurred. So instead, we use the total probability rule:

$$P(B) = P(B|A) * P(A) + P(B|A')*P(A)$$
which is a weighted average of selecting $B$ based on the probability of the prior event $A$. Then, instead, we have
$$P(B) = \frac{2}{49}*\frac{3}{50}+\frac{3}{49}*\frac{47}{50}=\frac{3}{50}$$

Then we find that $P(B|A) \neq P(B)$, so $A$ and $B$ are not independent (that is, they are dependent).

Again, the events $E_1, E_2, \ldots, E_k$ are independent if and only if for any subset of these events, 
$$P(E_1 \cap E_2 \cap \cdots \cap E_k) = P(E_1) \times P(E_2) \times P(E_k)$$
In practice, we usually assume events are independent (or almost independent), to allow us to use this simpler rule.

> [!example]
> A series circuit has two devices that operate with 0.8 and 0.9 probability, such that they fail independently. What is the probability that the circuit operates?

This is a series circuit, which means that the circuit only operates if both devices operate. If we let $L$ be the event that the first device functions and $R$ be the event that the second device functions, then we need to find $P(L \cap R)$. 

Since they are independent, we can simply multiply them together to get 0.72. 

> [!example]
> A parallel circuit has two devices that operate with 0.95 and 0.9 probability, such that they fail independently. What is the probability that the circuit operates?

This is a parallel circuit, which means that the circuit operates if either of the devices operates. 

We can take the complement of the event - the probability neither device operates - and subtract that from 1. Let $T$ be the event that the first device (0.95) functions, and $B$ be the event that the second device (0.9) functions.

Since they are independent, we can use the multiplication rule such that we have
$$P(T' \land B') = P(T') * P(B') = 0.005$$
so the probability that either device operates is 0.995.

In general, when we see "at least one" in probability, we can find the probability that "none of them" exhibit the event in question, and then subtract that from 1. 

> [!example]
> Consider an advanced circuit containing three "subcircuits" connected in series:
> - a parallel circuit containing devices with probability 0.9, 0.9, 0.9 of operating
> - a parallel circuit containing devices with probability 0.95, 0.95 of operating
> - a single device with probability 0.99 of operating
> 
> What is the probability that the circuit operates?

We can simply solve for each individual subcircuit operating, then use the multiplication rule to determine the overall probability that the circuit operates. Again, note that parallel circuits work so long as at least one device operates, so a paralle circuit fails if all the devices fail.

We find that the probability the first subcircuit operates is 0.999, the second subcircuit probability is 0.9975, and the last subcircuit is just 0.99. We multiply these together to yield 0.987, the probability the circuit operates.


## Test 1 review
The test spans sections 2.1 to 2.7 and is 70 minutes long. It contains both multiple choice and free resposne questions.

You may use one front-and-back page of handwritten notes.

Calculator permitted.

> [!example]
> A digital scale is used that provides weights to the nearest gram. The sample space for this experiment is $S =\{0, 1, 2, 3, \ldots\}$. Let $A$ denote teh event that a weight exceeds 11 grams, let $B$ denote the event that a weight is less than or equal to 15 grams, and let $C$ denote the event that a weight is greater than or equal to 8 grams and less than 12 grams. Describe the following events:
> - $A \cap B$
> - $A'$
> - $(A \cup C)'$

Note how:
- A = {12, 13, 14, ...}
- B = {8, 9, 10, 11, ...}
- C = {0, 1, ..., 15}

Then:
- $A \cap B$ is {12, 13, 14, ...}
- $A'$ is {0, ..., 11}
- $A \cup C = \{8, 9, \ldots \}$ so $(A \cup C)' = \{0, \ldots, 7\}$.

> [!example]
> A wireless grage door has a code determined by the up or down setting of 12 switches. How many outcomes are possible?

This is simply $2^{12}$.

> [!example]
> New designs for a wastewater treatment tank have proposed three possible shapes, four possible sizes, three locations for input valves, and four locations for output valves. How many different product designs are possible?

Observe that all individual shapes, sizes, and valves, and locations are distinct. So we have $3*4*3*4 = 144$ designs.

> [!example]
> A committee will be formed from 3 managers and 4 engineers selected without replacement from 10 managers and 20 engineers. How many different selectoins are possible?

This is a combination, as the order of the individual selections don't matter - if they end up with the same 3 managers, we treat that as the same subcommittee.

So we simply calculate ${10 \choose 3} \times {20 \choose 4}$. 

> [!example]
> A lot contains 15 castings from a local supplier and 25 suppliers in the next state. Two castings are selected randomly, without replacement, from the list of 40. Let $A$ be the event that the first casting selected is from the local supplier, and let $B$ denote the event that hte second casting is selected from the local supplier. Then, what is:
> - $P(A)$
> - $P(B|A)$
> - $P(A \cap B)$

We find that $P(A) = \frac{15}{40}$.

$P(B|A) = \frac{14}{39}$.

$P(A \cap B) = P(B|A) * P(A) = \frac{14}{39} * \frac{15}{40}$

> [!example]
> Suppose that $P(A|B) = 0.2$, $P(A|B') = 0.3$, $P(B) = 0.8$. What is $P(A)$?

Apply the total probability rule, noting that $P(B') = 1 - P(B) = 0.2$:
$$P(A) = P(A|B) \times P(B) + P(A|B') \times P(B') = 0.22$$

> [!example]
> Suppose you implement a RAID 1 scheme that uses two hard drives each containing a mirror image of the other, with each hard drive failing at a 0.001 probability. What is the probability of data loss, assuming that data loss occurs if both drives fail within the same day and drive failures are independent?

This amounts to finding the probability that both hard drives fail in the same day, and since the events are independent, we simply multiply them together.

> [!example]
> Using the same conditions above, suppose you implement a RAID 0 scheme that splits the data over two hard drives. What is the probability of data loss, assuming that data loss occurs if at least one drive fails within the same day?

We simply solve for the likelihood that neither drive fails - $0.999 \times 0.999$ and then subtract that from 1. 


