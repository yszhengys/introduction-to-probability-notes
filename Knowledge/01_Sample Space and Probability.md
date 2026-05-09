# 01_Sample Space and Probability

## Scope

Chapter 1 builds the basic language of probability:

- sample spaces and events
- probability laws and their consequences
- discrete uniform models and counting
- conditional probability
- the total probability theorem and Bayes' rule
- independence of events

The main skill is translating a verbal random experiment into a precise probability model.

## 1. Sample Spaces and Events

### Sample Space

The **sample space** $\Omega$ is the set of all possible outcomes of an experiment.

Examples:

- One coin toss: $\Omega = \{H,T\}$
- Two coin tosses: $\Omega = \{HH,HT,TH,TT\}$
- Roll one die: $\Omega = \{1,2,3,4,5,6\}$
- Lifetime of a device: $\Omega = [0,\infty)$

Choosing $\Omega$ is part of modeling. The same real experiment can have different sample spaces depending on the question.

### Event

An **event** is a subset of the sample space.

If $\Omega = \{1,2,3,4,5,6\}$, then:

- "even roll" is $A = \{2,4,6\}$
- "roll at least 5" is $B = \{5,6\}$
- "roll 7" is $\varnothing$

### Set Operations

For events $A,B \subseteq \Omega$:

- Union: $A \cup B$ means $A$ or $B$ occurs.
- Intersection: $A \cap B$ means both $A$ and $B$ occur.
- Complement: $A^c$ means $A$ does not occur.
- Difference: $A \cap B^c$ means $A$ occurs but $B$ does not.
- Disjoint events: $A \cap B = \varnothing$.

Useful identities:

$$
(A^c)^c = A
$$

$$
(A \cup B)^c = A^c \cap B^c
$$

$$
(A \cap B)^c = A^c \cup B^c
$$

$$
A = (A \cap B) \cup (A \cap B^c)
$$

The last identity is often useful because it splits an event into two disjoint pieces.

## 2. Probability Laws

A **probability law** assigns a number $P(A)$ to each event $A$.

### Axioms

For events in $\Omega$:

1. Nonnegativity:

$$
P(A) \ge 0
$$

2. Normalization:

$$
P(\Omega) = 1
$$

3. Additivity for disjoint events:

If $A \cap B = \varnothing$, then

$$
P(A \cup B) = P(A) + P(B)
$$

For a finite or countable collection of disjoint events $A_1,A_2,\dots$:

$$
P\left(\bigcup_i A_i\right) = \sum_i P(A_i)
$$

### Immediate Consequences

Impossible event:

$$
P(\varnothing) = 0
$$

Complement rule:

$$
P(A^c) = 1 - P(A)
$$

Monotonicity:

If $A \subseteq B$, then

$$
P(A) \le P(B)
$$

Upper bound:

$$
P(A) \le 1
$$

Addition rule:

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

Union bound:

$$
P(A \cup B) \le P(A) + P(B)
$$

For many events:

$$
P\left(\bigcup_{i=1}^n A_i\right) \le \sum_{i=1}^n P(A_i)
$$

## 3. Discrete Models

In a finite or countably infinite sample space:

$$
P(A) = \sum_{\omega \in A} P(\{\omega\})
$$

Each outcome $\omega$ has a probability mass $p(\omega)$, where:

$$
p(\omega) \ge 0
$$

$$
\sum_{\omega \in \Omega} p(\omega) = 1
$$

Then:

$$
P(A) = \sum_{\omega \in A} p(\omega)
$$

### Uniform Finite Model

If all outcomes in a finite sample space are equally likely:

$$
P(A) = \frac{|A|}{|\Omega|}
$$

This formula is only valid when all elementary outcomes are equally likely.

## 4. Counting

Counting is used to compute probabilities in finite uniform models.

### Multiplication Rule

If a process has $r$ stages with $n_1,n_2,\dots,n_r$ choices at each stage, then the total number of outcomes is:

$$
n_1 n_2 \cdots n_r
$$

### Permutations

Number of ordered arrangements of $n$ distinct objects:

$$
n!
$$

Number of ordered selections of $k$ objects from $n$ distinct objects without replacement:

$$
\frac{n!}{(n-k)!}
$$

### Combinations

Number of unordered selections of $k$ objects from $n$ distinct objects:

$$
{n \choose k} = \frac{n!}{k!(n-k)!}
$$

Useful identities:

$$
{n \choose k} = {n \choose n-k}
$$

$$
{n \choose k} = {n-1 \choose k-1} + {n-1 \choose k}
$$

### Ordered vs. Unordered

Ask:

- Does order matter?
- Is replacement allowed?
- Are all outcomes equally likely?
- Is the sample space being counted at the same level of detail as the event?

## 5. Conditional Probability

Conditional probability updates the probability of $A$ after learning that $B$ occurred.

If $P(B) > 0$:

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$

Equivalent multiplication rule:

$$
P(A \cap B) = P(B)P(A \mid B)
$$

Also:

$$
P(A \cap B) = P(A)P(B \mid A)
$$

### Chain Rule

For events $A_1,\dots,A_n$:

$$
P(A_1 \cap \cdots \cap A_n)
= P(A_1)P(A_2 \mid A_1)P(A_3 \mid A_1 \cap A_2)\cdots P(A_n \mid A_1 \cap \cdots \cap A_{n-1})
$$

This is often the easiest way to compute probabilities for sequential experiments.

### Conditional Probability Is a Probability Law

After conditioning on $B$, the new sample space is effectively $B$. The function $P(\cdot \mid B)$ obeys the same probability axioms:

$$
P(A^c \mid B) = 1 - P(A \mid B)
$$

$$
P(A_1 \cup A_2 \mid B) = P(A_1 \mid B) + P(A_2 \mid B)
$$

when $A_1$ and $A_2$ are disjoint.

## 6. Total Probability Theorem

A collection of events $A_1,\dots,A_n$ is a **partition** of $\Omega$ if:

- $A_i \cap A_j = \varnothing$ for $i \ne j$
- $A_1 \cup \cdots \cup A_n = \Omega$
- $P(A_i) > 0$ for the terms used in conditioning

If $A_1,\dots,A_n$ partition $\Omega$, then:

$$
P(B) = \sum_{i=1}^n P(A_i \cap B)
$$

Using conditional probability:

$$
P(B) = \sum_{i=1}^n P(A_i)P(B \mid A_i)
$$

Interpretation: compute the probability of $B$ by splitting into cases.

## 7. Bayes' Rule

If $A_1,\dots,A_n$ partition $\Omega$ and $P(B)>0$, then:

$$
P(A_i \mid B)
= \frac{P(A_i)P(B \mid A_i)}
{\sum_{j=1}^n P(A_j)P(B \mid A_j)}
$$

Two-event version:

$$
P(A \mid B)
= \frac{P(A)P(B \mid A)}
{P(A)P(B \mid A) + P(A^c)P(B \mid A^c)}
$$

Vocabulary:

- Prior: $P(A_i)$
- Likelihood: $P(B \mid A_i)$
- Evidence: $P(B)$
- Posterior: $P(A_i \mid B)$

Core idea: Bayes' rule reverses the direction of conditioning.

## 8. Independence

Events $A$ and $B$ are **independent** if:

$$
P(A \cap B) = P(A)P(B)
$$

If $P(B)>0$, this is equivalent to:

$$
P(A \mid B) = P(A)
$$

If $P(A)>0$, it is also equivalent to:

$$
P(B \mid A) = P(B)
$$

Interpretation: learning that one event occurred does not change the probability of the other.

### Independence vs. Disjointness

Disjoint means:

$$
A \cap B = \varnothing
$$

Independent means:

$$
P(A \cap B) = P(A)P(B)
$$

If $A$ and $B$ are disjoint and both have positive probability, they cannot be independent.

### Independence of Complements

If $A$ and $B$ are independent, then the following pairs are also independent:

- $A$ and $B^c$
- $A^c$ and $B$
- $A^c$ and $B^c$

### Independence of Multiple Events

Events $A_1,\dots,A_n$ are independent if every finite intersection factors into the product of probabilities.

For three events, independence requires:

$$
P(A \cap B) = P(A)P(B)
$$

$$
P(A \cap C) = P(A)P(C)
$$

$$
P(B \cap C) = P(B)P(C)
$$

and

$$
P(A \cap B \cap C) = P(A)P(B)P(C)
$$

Pairwise independence alone does not imply mutual independence.

### Conditional Independence

Events $A$ and $B$ are conditionally independent given $C$ if $P(C)>0$ and:

$$
P(A \cap B \mid C) = P(A \mid C)P(B \mid C)
$$

This does not generally imply ordinary independence.

Ordinary independence does not generally imply conditional independence.

## 9. Common Problem Patterns

### Pattern 1: Build the Model First

1. Define the experiment.
2. Choose $\Omega$.
3. Define the event of interest.
4. Assign probabilities to outcomes or events.
5. Compute using probability laws.

### Pattern 2: Split into Cases

Use total probability when the problem naturally has cases:

$$
P(B) = \sum_i P(A_i)P(B \mid A_i)
$$

Good partitions are usually based on information such as type, source, first step, hidden state, or test result.

### Pattern 3: Reverse a Conditional

If the problem gives $P(B \mid A)$ but asks for $P(A \mid B)$, use Bayes' rule.

### Pattern 4: Sequential Experiment

Use the multiplication rule:

$$
P(A_1 \cap \cdots \cap A_n)
= P(A_1)P(A_2 \mid A_1)\cdots P(A_n \mid A_1 \cap \cdots \cap A_{n-1})
$$

### Pattern 5: Equally Likely Outcomes

If outcomes are equally likely:

$$
P(A) = \frac{\text{number of favorable outcomes}}{\text{number of possible outcomes}}
$$

Check equal likelihood before using this formula.

## 10. Frequent Mistakes

- Using $P(A \cup B) = P(A)+P(B)$ when $A$ and $B$ are not disjoint.
- Treating disjoint events as independent.
- Assuming outcomes are equally likely without justification.
- Confusing $P(A \mid B)$ with $P(B \mid A)$.
- Forgetting the denominator in Bayes' rule.
- Choosing a sample space that is too coarse for the event being computed.
- Counting ordered outcomes in the numerator and unordered outcomes in the denominator.
- Believing pairwise independence automatically implies mutual independence.
- Forgetting that conditional probabilities require the conditioning event to have positive probability.

## 11. Exam Checklist

Before solving:

- What is the sample space?
- What is the event being asked for?
- Are outcomes equally likely?
- Is there a natural partition?
- Is the problem asking to reverse conditioning?
- Are the events disjoint, independent, both, or neither?
- Does the event involve a sequence of steps?
- Is order relevant in the counting?

Core formulas to memorize:

$$
P(A^c)=1-P(A)
$$

$$
P(A \cup B)=P(A)+P(B)-P(A \cap B)
$$

$$
P(A \mid B)=\frac{P(A \cap B)}{P(B)}
$$

$$
P(A \cap B)=P(A)P(B \mid A)=P(B)P(A \mid B)
$$

$$
P(B)=\sum_i P(A_i)P(B \mid A_i)
$$

$$
P(A_i \mid B)=
\frac{P(A_i)P(B \mid A_i)}
{\sum_j P(A_j)P(B \mid A_j)}
$$

$$
A \text{ and } B \text{ independent}
\iff
P(A \cap B)=P(A)P(B)
$$

