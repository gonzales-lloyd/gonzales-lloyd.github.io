Again, recall that the sample space is the set of all possible outcomes.

Let's suppose thta the recycle times of two cameras are recorded. Then, the extension of the positive real line $R$ is to take the sample space to be the positive quadrant of the plane.

Let $x$ be the recycle time of the first camera, and $y$ be the recycle time of the second camera. Then,
$$S = \{(x,y) | x \gt 0, y \gt 0\}$$
It holds that we can represent the sample space for this sample space as the first quadrant of the standard plane; that is,

![[August 31 2022-08-31 13.04.47.excalidraw]]

Also worth noting is that if the sole objective of the analysis is to consider only whether or not the cameras conform to the manufacturing specifications, then either camera may or may not conform. Allowing "y" to be "yes" and "n" to be no, then:
$$S = \{yy, yn, ny, nn\}$$
An **event** is a subset of the sample space of a random experiment. So for the sample space above, suppose that the subset of outcomes for which at least one camera conforms is denoted $E_1$. Then:
$$E_1 = \{yy, yn, ny\}$$
Now, let's say that if $E_2$ is the event that both cameras do not conform, then $E_2 = \{nn\}$.

The **union** of two events is the event that consists of all outcomes that are contained in either of the two events. (Note that it itself is an event.) We denote this $E_1 \cup E_2$. For example, if $E_1 = \{yy, yn\}$ and $E_2 = \{yn, ny\}$, then $E_1 \cup E_2 = \{yy, yn, ny\}$. (And again, recall that sets are only composed of unique elements.)

Similarly, the **intersection** of two events is the event consisting of all outcomes contained in both events. This is denoted $E_1 \cap E_2$.

The **complement** of an event is the set of outcomes in the sample space that are not in the event. We denote the complement of $E$ as $E'$. So for example:
$$S = \{yy, ny, yn, nn\}$$
$$E = \{yy, ny\}$$
$$E' = \{yn, nn\}$$
Also, the empty set/null set still exists: $\{yy, yn\} \ cap \{yn, ny\} = \varnothing$ 

Now, remember that sample spaces may be $S = \mathbb{R}^+$, the set of positive real numbers. So let $S = \{x | x \gt 0\}$. Then if $E_1 = \{x|10 \leq x \lt 12\}$ and $E_2 = \{x|11 \lt x \lt 15\}$, then:
- $E_1 \cap E_2 = \{x | 11 \lt x \lt 12\}$
- $E_1 \cup E_2 = \{x|10 \leq x \lt 15\}$
- $E_1' = \{0 \lt x \lt 10 \cup x \geq 12\}$

And of course, you can represent this on a number line.

You can combine intersections, unions, and complements as applicable.

If two events $A$ and $B$ exist such that $A \cap B = \varnothing$, then $A$ and $B$ are said to be **mutually exclusive**. That is to say, A cannot happen if B occurs, and vice versa.

Of course, there are various set properties:
- $(E')' = E$
- $(A \cup B) \cap C = (A \cap C) \cup (B \cap C)$
- $(A \cap B) \cup C = (A \cup C) \cap (B \cup C)$
- $(A \cup B) ' = A' \cap B'$
- $(A \cap B)' = A' \cup B'$

The second and third are distributive; the fourth and fifth are DeMorgan's laws

## Probability; counting techniques
Say you have 3 shirts and 2 pants. Then you can make 6 different outfits.

The multiplication rule is a simple where if we assume an operation can be described as a sequence of $k$ steps, where the number of ways to complete step $k$ is $n_k$, then the total number of ways to complete the operation is
$$n_1 * n_2 * \cdots * n_k*$$

So if we have a website that consists of four colors, three fonts, and three positions for an image, then we have 36 different possible designs.

A **permutation** of the elements is an ordered sequence of the elements. Letting $S = \{a, b, c\}$, then we have six different permutations: abc, acb, bac, bca, cab, and cba.

The number of permutations of $n$ different elements is $n!$ where $n! = n * (n-1) * (n-2) * \cdots * 2 * 1$ (the factorial).
- Note that $0! = 1$.
- Factorials, of course, can be simplified in certain ways (e.g, $6! = 6*5*4! = 6*5*4*3!$) which are helpful when needing to work with operations on factorials, such as the division of factorials.

The number of permutations of subsets of $r$ elements selected from a set of $n$ different elements is
$$P_r^n = n * (n-1)*\cdots(n-r+1) = \frac{n!}{(n-r)!}$$

Then if we want to find the permutations of two elements from the subset of three elements:

$$P^3_2 = \frac{3!}{(3-2)!} = 6$$
which is to say, the subsets of length 2 from {a, b, c} are ab, ac, ba, bc, ca, cb.

For example, say:
> [!example]
> A printed circuit board has eight different locations in which a component can be placed. If four different components are to be placed on the board, how many different designs are possible?

Well, we know that when we place the first component, it has 8 possible locations. Then, the second component has 7 locations, the third has 6, and the fourth has 5. Then, there are 1,680 possible designs (noting that regardless of where the first component is placed, there are always $7*6*5$ successive ways to place the remaining three components).

Note that this is a permutation because the components are different, so order does matter.

Formulaically,

$$P_4^8 = \frac{8!}{(8-4)!} = \frac{8*7*6*5*4!}{4!} = 1680$$
The number of permutations of $n = n_1 + n_2 + \cdots + n$ objects of which $n_1$ are of one type, $n_2$ are of a second type, and $n_r$ are of an $r$th type is
$$\frac{n!}{n_1!n_2! \cdots n_r!}$$
> [!example]
> How many different 6-digit numerals can be written using the digits 3, 3, 4, 4, 4, 5?

Note how 3 is repeated twice, 4 is repeated thrice, and 5 is only present once. Then, noting that $n=6$, and $n_1 = 2$, $n_2 = 3$, and $n_3 = 1$:
$$\frac{6!}{2!*3!*1!} = 60$$

Observe that the presence of repeated values means that 334445 and 334445 are indistinguishable, even if I say that I've swapped the 3s. This is why there are only 60 distinct possibilities, not $6!$.
> [!example]
> A hospital operating room needs to schedule three knee and two hip surgeries in a day. What is the number of possible sequences of three knee and two hip surgeries?

This amounts to 
$$\frac{5!}{2!*3!} = \frac{120}{12}=10$$
(which is to say, the rearrangement of two knee surguries has no effect.)

## Combinations
Another counting problem of interest is the number of subsets of $r$ elements that can be selected from a set of $n$ elements. Here, order is not important. These are called combinations.

In permutations, we stated that from $S = \{a, b, c\}$, that the subsets ab and ba were distinct.

In combinations, these are not distinct, and we only count this once.

The number of combinations, subsets of $r$ elements that can be selected from a set of $n$ elements, is denoted as $n \choose r$ (binomial notation) or $C_n^r$.

$$C_r^n = {n \choose r} = \frac{n!}{r!(n-r)!} $$

Think about how this relates to the past two formulas we've seen, for permuatations and repeating elements.

A combination is like picking a team of 3 people from a group of 10; a permutation is like picking a president, VP, and secretary from a group of 10.

In the combination case:
$${10 \choose 3} = \frac{10!}{3! *(10-3)!} = 120$$
And in the permutation case, this is simply $10*9*8 = 720$. Note how it does matter if we pick the same 3 people in this case, but not in the combination case.