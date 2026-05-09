# 01_Sample Space and Probability

## Scope

Chapter 1 gives the language and basic tools for probability models:

- sample spaces, events, and set operations
- probability laws and basic consequences
- discrete and uniform models
- counting methods
- conditional probability and the chain rule
- total probability and Bayes' rule
- independence, mutual independence, and conditional independence

Main skill: translate a verbal random experiment into a precise model.

## 1. Sample Spaces and Events

### Basic Objects

- **Sample space** $\Omega$: all possible outcomes of an experiment.
- **Outcome** $\omega$: one element of $\Omega$.
- **Event** $A$: a subset of $\Omega$.
- **Impossible event**: $\varnothing$.
- **Certain event**: $\Omega$.

Examples:

- Coin toss: $\Omega=\{H,T\}$
- Two coin tosses: $\Omega=\{HH,HT,TH,TT\}$
- One die roll: $\Omega=\{1,2,3,4,5,6\}$
- Device lifetime: $\Omega=[0,\infty)$

The choice of $\Omega$ depends on the question. A sample space must be detailed enough to describe the event being computed.

### Event Operations

For $A,B\subseteq\Omega$:

- $A\cup B$: $A$ or $B$ occurs.
- $A\cap B$: both $A$ and $B$ occur.
- $A^c$: $A$ does not occur.
- $A\cap B^c$: $A$ occurs and $B$ does not.
- $A\cap B=\varnothing$: $A$ and $B$ are disjoint.

Key identities:

$$
(A^c)^c=A
$$

$$
(A\cup B)^c=A^c\cap B^c
$$

$$
(A\cap B)^c=A^c\cup B^c
$$

$$
A=(A\cap B)\cup(A\cap B^c)
$$

The last identity splits $A$ into two disjoint cases.

## 2. Probability Laws

A probability law assigns each event $A$ a number $P(A)$.

### Axioms

1. Nonnegativity:

$$
P(A)\ge 0
$$

2. Normalization:

$$
P(\Omega)=1
$$

3. Additivity for disjoint events:

If $A_i\cap A_j=\varnothing$ for $i\ne j$, then

$$
P\left(\bigcup_i A_i\right)=\sum_i P(A_i)
$$

### Consequences

$$
P(\varnothing)=0
$$

$$
P(A^c)=1-P(A)
$$

If $A\subseteq B$, then

$$
P(A)\le P(B)
$$

$$
0\le P(A)\le 1
$$

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B)
$$

$$
P(A\cup B)\le P(A)+P(B)
$$

More generally:

$$
P\left(\bigcup_{i=1}^n A_i\right)\le \sum_{i=1}^n P(A_i)
$$

## 3. Discrete Models

For finite or countably infinite $\Omega$, assign probability mass $p(\omega)=P(\{\omega\})$.

Requirements:

$$
p(\omega)\ge 0
$$

$$
\sum_{\omega\in\Omega}p(\omega)=1
$$

Event probability:

$$
P(A)=\sum_{\omega\in A}p(\omega)
$$

### Uniform Finite Model

If all outcomes are equally likely:

$$
P(A)=\frac{|A|}{|\Omega|}
$$

Use this only after checking equal likelihood.

## 4. Counting

Counting is mainly used with finite uniform models.

### Core Rules

Multiplication rule:

$$
n_1n_2\cdots n_r
$$

Permutations of $n$ distinct objects:

$$
n!
$$

Ordered selections of $k$ from $n$ without replacement:

$$
\frac{n!}{(n-k)!}
$$

Unordered selections of $k$ from $n$:

$$
{n\choose k}=\frac{n!}{k!(n-k)!}
$$

Useful identities:

$$
{n\choose k}={n\choose n-k}
$$

$$
{n\choose k}={n-1\choose k-1}+{n-1\choose k}
$$

### Counting Checklist

- Does order matter?
- Is replacement allowed?
- Are objects distinguishable?
- Are outcomes equally likely?
- Are numerator and denominator counted at the same level of detail?

## 5. Conditional Probability

For $P(B)>0$:

$$
P(A\mid B)=\frac{P(A\cap B)}{P(B)}
$$

Multiplication forms:

$$
P(A\cap B)=P(B)P(A\mid B)
$$

$$
P(A\cap B)=P(A)P(B\mid A)
$$

### Chain Rule

For events $A_1,\dots,A_n$:

$$
P(A_1\cap\cdots\cap A_n)
=P(A_1)P(A_2\mid A_1)\cdots P(A_n\mid A_1\cap\cdots\cap A_{n-1})
$$

Use it for sequential experiments.

### Conditional Probability as a New Probability Law

Conditioning on $B$ makes $B$ the effective sample space. For $P(B)>0$:

$$
P(A^c\mid B)=1-P(A\mid B)
$$

If $A_1$ and $A_2$ are disjoint:

$$
P(A_1\cup A_2\mid B)=P(A_1\mid B)+P(A_2\mid B)
$$

## 6. Total Probability

Events $A_1,\dots,A_n$ form a partition of $\Omega$ if:

- $A_i\cap A_j=\varnothing$ for $i\ne j$
- $A_1\cup\cdots\cup A_n=\Omega$
- conditioning terms have positive probability

Then:

$$
P(B)=\sum_{i=1}^n P(A_i\cap B)
$$

and

$$
P(B)=\sum_{i=1}^n P(A_i)P(B\mid A_i)
$$

Use total probability to split a problem into cases.

## 7. Bayes' Rule

If $A_1,\dots,A_n$ partition $\Omega$ and $P(B)>0$:

$$
P(A_i\mid B)=
\frac{P(A_i)P(B\mid A_i)}
{\sum_{j=1}^n P(A_j)P(B\mid A_j)}
$$

Two-event version:

$$
P(A\mid B)=
\frac{P(A)P(B\mid A)}
{P(A)P(B\mid A)+P(A^c)P(B\mid A^c)}
$$

Vocabulary:

- Prior: $P(A_i)$
- Likelihood: $P(B\mid A_i)$
- Evidence: $P(B)$
- Posterior: $P(A_i\mid B)$

Bayes' rule reverses conditioning: from $P(B\mid A)$ to $P(A\mid B)$.

## 8. Independence

### Two Events

$A$ and $B$ are independent if:

$$
P(A\cap B)=P(A)P(B)
$$

Equivalent forms, when denominators are positive:

$$
P(A\mid B)=P(A)
$$

$$
P(B\mid A)=P(B)
$$

### Independence vs. Disjointness

- Disjoint: $A\cap B=\varnothing$.
- Independent: $P(A\cap B)=P(A)P(B)$.
- If $P(A)>0$ and $P(B)>0$, disjoint events cannot be independent.

### Complements

If $A$ and $B$ are independent, then these pairs are also independent:

- $A$ and $B^c$
- $A^c$ and $B$
- $A^c$ and $B^c$

### Multiple Events

For three events, mutual independence requires all pairwise products:

$$
P(A\cap B)=P(A)P(B)
$$

$$
P(A\cap C)=P(A)P(C)
$$

$$
P(B\cap C)=P(B)P(C)
$$

and the triple product:

$$
P(A\cap B\cap C)=P(A)P(B)P(C)
$$

Pairwise independence does not imply mutual independence.

### Conditional Independence

$A$ and $B$ are conditionally independent given $C$ if $P(C)>0$ and:

$$
P(A\cap B\mid C)=P(A\mid C)P(B\mid C)
$$

Conditional independence and ordinary independence do not imply each other in general.

## 9. Problem Patterns

### Build a Model

1. Define the experiment.
2. Choose $\Omega$.
3. Define the target event.
4. Assign probabilities.
5. Compute with probability laws.

### Split into Cases

Use:

$$
P(B)=\sum_i P(A_i)P(B\mid A_i)
$$

Good partitions often come from type, source, first step, hidden state, or test result.

### Reverse a Conditional

Given $P(B\mid A)$ and asked for $P(A\mid B)$, use Bayes' rule.

### Sequential Experiment

Use the chain rule:

$$
P(A_1\cap\cdots\cap A_n)
=P(A_1)P(A_2\mid A_1)\cdots P(A_n\mid A_1\cap\cdots\cap A_{n-1})
$$

### Equally Likely Outcomes

If outcomes are equally likely:

$$
P(A)=\frac{\text{favorable outcomes}}{\text{possible outcomes}}
$$

Always check equal likelihood first.

## 10. Frequent Mistakes

- Using $P(A\cup B)=P(A)+P(B)$ when events are not disjoint.
- Treating disjoint events as independent.
- Assuming equal likelihood without justification.
- Confusing $P(A\mid B)$ and $P(B\mid A)$.
- Forgetting the denominator in Bayes' rule.
- Choosing a sample space that is too coarse.
- Mixing ordered and unordered counts.
- Thinking pairwise independence implies mutual independence.
- Forgetting that $P(A\mid B)$ requires $P(B)>0$.

## 11. Exam Checklist

Before solving:

- What is $\Omega$?
- What event is being asked for?
- Are outcomes equally likely?
- Is there a natural partition?
- Is this asking to reverse conditioning?
- Are events disjoint, independent, both, or neither?
- Is the experiment sequential?
- Does order matter?

Formulas to memorize:

$$
P(A^c)=1-P(A)
$$

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B)
$$

$$
P(A\mid B)=\frac{P(A\cap B)}{P(B)}
$$

$$
P(A\cap B)=P(A)P(B\mid A)=P(B)P(A\mid B)
$$

$$
P(B)=\sum_i P(A_i)P(B\mid A_i)
$$

$$
P(A_i\mid B)=
\frac{P(A_i)P(B\mid A_i)}
{\sum_j P(A_j)P(B\mid A_j)}
$$

$$
A \text{ and } B \text{ independent}
\iff
P(A\cap B)=P(A)P(B)
$$

