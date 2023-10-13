note: graphing calculator is allowed

We use statistics, rather than mathematical functions, to forecast the weather - a demonstration of Lorentz's butterfly effect.

Lagrange interpolation states that you can find a polynomial passing through all points of a given dataset. This is a deterministic, mathematical approach to the dataset; however, the polynomial may not fit the data well, and you may end up with unrealistic results when interpolating data.

But statistics takes a more reasonable approach regarding prediction generation. For example, with a set of data that approximately fits a positive trend, you might just be able to draw a line for your prediction function.

Now, a prediction function is not always perfect, and we describe the difference between a predicted value for a given input and the actual value as the **error**.

## Section 1.1 and 1.2
**Statistics** deals with the collection, presentation, analysis and use of dat ato make decisions, solve problems, and design products and processes.

**Variability** describes why successive observations of a system or phenomenon do not produce the exact same result. For example, your gasoline performance of the car vary with your car's condition, how you drive, the brand of the gasoline, and weather conditions. Some of these might be in your control, while other may not be.

Noise variables, such as the weather conditions, are uncontrolled variables. Our goal, then, is not to control these variables, but to understand how these variables affect the model.

Let's try to model gasoline performance, treating it as a random variable - which is to say, its values depend on chance.

A convenient way to think of a random variable, like $X$, is to use the model
$$X = \mu + \epsilon$$
where $\mu$ is a constant and $\epsilon$ is a random disturbance. If there were no disturbances, then $\epsilon = 0$ and our observations/variable would always be equal to the constant $\mu$. Then, we can try model such random conditions like the weather  through $\epsilon$.

How do we collect the data that's actually involved?

The **population** is the complete collection of all measurements or data that are being considered. Typically, this is the complete collection of data that we would like to make inferences about.

A **census** is a collection of data from every member of a population. A **sample** is a collection of data from a *subcollection* of members from a population. Typically, censuses are impractical, so samples are usually done instead.

A **retrospective study** uses either all or a sample of the historical data for a given process archived over time. Example cases include finding potential risk factors and diseases - in such cases, the data has already been collected. In these studies, some relevant data may be msising, the data may have been incorrectly recorded, or **outliers** otherwise exist.

Outliers are data points that are not typical of the rest of the data values.

In an **observational study**, the researcher observes the process or population, disturbing it as little as possible, and records the quantities of interest. A survey asking how many pets people have would be such an example.

In a **designed experiment**, the researcher makes deliberate or purposeful changes in the controllable variables of the system or process, observing the resulting data. Experiments are often designed to determine the effectiveness of a drug.

## Section 2.1
A **random experiment** is an experiment that can result in different outcomes, even though it is repeated in the same manner each time.

In general, we can describe a system as something that takes in an input, controlled variables, and noise variables and spits out some output.

The set of all possible outcomes of a random experiment is called its **sample space**, denoted $S$. For example, the sample space of tossing a single coin is $S = \{\mathrm{heads, tails}\}$.

Now, consider an experiment that selects a cell phone camera and records the recycle time of a flash, which is the time it takes for the camera to ready another flash. The possible values for this time depend on the resolution of the timer, as well as the minimum and maximum recycle times. 

Technically speaking, the sample space with no additional information would be $S = \{x | x \gt 0\}$. But let's say that instead we know all recycle times are between 2.5 seconds; then, $S = \{x|2 \lt x \lt 5\}$. (Note that it is assumed for intervals that $x \in \mathbb{R}$ .)

But if we change the objective of the analysis to consider only when the recycle time is low, medium, or high, the sample space becomes $S = \{\mathrm{low, medium, high}\}$. 

Or perhaps we change the objective of the analysis to just be whether or not a particular camera conforms to a minimum recylce-time specification, then the sample space just becomes either "yes" or "no."

In any case, just remember two things:
- The sample space is a set (of elements).
- You must know your objective to determine the sample space.

A sample space may contain two types of data - discrete and continuous. (Note that we deal with quantitative data here). 

A sample space is **discrete** if it contains of a finite or countable infinite set of outcomes (countably infinite is something like the set of all integers, or the set of all rationals up to one decimal point). An example might be the number of heads we get after tossing five coins.

A sample space is **continuous** if it contains an interval (which can be finite or infinite), of *real* numbers. An example might be the camera flash recycle time, assuming infinite precision (and therefore real numbers, not just the set of rational numbers)=.

The key point here is that continuous sample spaces only have *measurements* of their entire sample space.