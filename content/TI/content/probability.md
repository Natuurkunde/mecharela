(sec:probability)=
# Probability theory

(sec:combinatorics)=
## Combinatorics

```{index} combinatorics
```
*Combinatorics* is the subfield of mathematics perhaps most close to your first mathematical experience, as it is about how to count things. After a fashion, addition and multiplication are basic combinatorics techniques: If you have five fingers on each hand, the total number of fingers you have is ten, and if you make a grid of four by five, the total number of grid points will be twenty. Likewise, the total number of possible four-digit codes is $10^4$, and the total number of possible license plates with four letters and two numbers would be $26^4 \cdot 10^2$, assuming all letters are usable.

The reason why calculating the number of possible codes or license plates is easy, is because the individual slots are filled in independently, and all can sample from the same range. Things get a bit more interesting if we impose some restrictions. Again, cases are best illustrated by examples, from which the general rule becomes clear quickly. For completenes, I've included the license plate example.

1. The number of possible four-digit codes is $10^4$; the number of possible combinations of $n$ objects that each can be selected from $k$ elements is $k^n$.
1. The number of possible one-on-one matches between six people is $15$. The first person can be matched to each of the other five. This matching already covers a match between the first and second person, so there are four more matches for the second, and so on. Note that the total number of matches  is the sum, so you get $5 + 4 + 3 + 2 + 1 = 15$. We get this number as the number of dots in the upper triangle of a $6 \times 6$ square, which is $6 \cdot 5 / 2$; if we'd include the diagonal, we add $6$, and thus would get $6 \cdot 7 / 2 = 21$, see {numref}`fig:combinatorics`(a). For $n$ people, the number of possible matches is thus

$$
\frac12 n (n-1).
$$

1. The number of ways (as in, order in which they appear) four people can be listed is $24$. For the first person, there are four choices. Once you've selected one person to go first, you have three choices left for the second, then two for the third, and one for the fourth spot, so you get $4 \cdot 3 \cdot 2 \cdot 1 = 4! = 24$ options, see {numref}`fig:combinatorics`(b). For $n$ people you get

$$
n! = n \cdot (n-1) \cdot (n-2) \cdot \ldots \cdot 2 \cdot 1
$$

```{index} permutations
```
possibilities. We call $n!$ the number of *permutations* of $n$. 
1. Extending the idea of permutations, the number of *arrangements* of three students to be selected from a group of twenty is $20 \cdot 19 \cdot 18 = 6840$. The number of arrangements of $k$ elements from a group of $n$ objects is known as a partial permutation or $k$-permutation, and can be calculated as

$$
n\mathrm{P}k = n \cdot(n-1) \cdot \ldots \cdot (n-k+1) = \frac{n!}{(n-k)!}.
$$

$n\mathrm{P}k$ is short for '$n$ permute $k$'.

```{index} combination
```
1. In many cases, we will only be interested in which three students get picked from the group of twenty, and not the order in which they are selected. We can easily account for that by realizing that there are $3! = 6$ orders in which the three students are picked, which all give the same group. Therefore, the number of possible groups of three students that can be chosen from a total group of twenty is $0 \cdot 19 \cdot 18 / 3! = 1140$. The number of ways of choosing $k$ elements from a group of $n$ objects is known as a *combination*, and can be calculated as

$$
n\mathrm{C}r = \binom{n}{k} = \frac{n!}{(n-k)! k!}.
$$

```{index} bionmial coefficient
```
$n\mathrm{C}k$ is short for '$n$ choose $k$'; the notation with $n$ above $k$ in parentheses is known as the *binomial coefficient*. You may have encountered the binomial coefficients in the *binomial theorem*, which gives the expansion of a polynomial term of power $n$:

$$
(x + y)^n = \sum_{k=0}^n \binom{n}{k} x^k y^{n-k}.
$$ (binomialformula)

The binomial coefficients satisfy a recursion relation

$$
\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k},
$$

which is the basis for arranging them in Pascal's triangle, where each number is the sum of the two directly above it (counting empty spaces as zeros), cf. {numref}`fig:combinatorics`(c). 

```{figure} images/combinatorics.svg
:name: fig:combinatorics
Combinatorics. (a) The number of ways of making one-on-one matches between six people equals the number of orange dots, which we can easily calculate as $6 \cdot 5 / 2 = 15$. If we include 'self-matches', we also count the purple dots on the diagonal, and the number of options becomes $6 \cdot 7 / 2 = 21$. (b) Permutations: The number of ways of arranging three different items equals $3! = 6$. (c) Pascal's triangle of binomial coefficients.
```

Note that when doing calculations in combinatorics, 'and' usually comes with a product, and 'or' with a sum (see {numref}`pb:andorcombinations`).

(sec:probabilities)=
## Probabilities

Probability theory is the subfield of mathematics that deals with random (or *stochastic*) events. Simple examples of such events include coin flips, dice throws, and radioactive decays. The outcome of an individual event cannot be predicted, but in many cases, the probability of a given outcome can be calculated from a (stochastic) model of the system. For example, the outcome of a coin flip can be predicted to be $50\%$ heads and $50\%$ tails based on a 'fair coin' model, and the remaining number of radioactive particles after the passing of a known amount of time can be calculated based on an exponential decay model.

In a system where there is a finite number of possible states, and each state is equivalent, the probability of getting a certain state can be calculated easily:

$$
P(A) = \frac{\text{number of cases in which $A$ is true}}{\text{total number of cases}}.
$$ (probdef)

For example, the probability of throwing a six with a (fair) dice is $1/6$, and the probability that a randomly selected letter from the alphabet will be a vowel is $5/26$. 

```{index} stochastic variable
```
In most cases, we'll be interested in the probability of a mathematical variable being equal to or larger than some other number, i.e., a probability of the form $X = a$, where $X$ could be the outcome of the throw of a die, and $a$ a specific value. We call $X$ a *stochastic variable*; identifying the proper stochastic variable is a key step in any probability problem.

From the definition in equation&nbsp;{eq}`probdef` it is immediately clear that the probability is a number between zero and one. A probability zero indicates that something is impossible; a probability one means that it is certain to happen<sup>[^1]</sup>.

The notion of probability introduced in equation&nbsp;{eq}`probdef` can be extended to continuous cases. For example, if we're given a circle with radius&nbsp;$1$, and asked to find the probability that a randomly selected point inside that circle has a distance to the center of no more than $\frac12$, the answer is the total area of all points that satisfy this condition over the total area of the whole circle (i.e., all possible points). In the notation with a stochastic variable, let $X$ be the distance to the center of our randomly selected point, then

$$
P\left(X \leq \frac12\right) = \frac{\pi \cdot \left(\frac12\right)^2}{\pi \cdot 1^2} = \frac14.
$$

Note that for a continuous stochastic variable, the probability that it is exactly equal to a specified value is always zero, as there are infinitely many other options.

(sec:vasemodel)=
### Worked example: Vase model

A useful (thought) experiment to think about probabilities is the *vase model*. We consider a (non-transparent) vase containing a number of balls of identical size but with different colors. We can then ask what the probability is that a blind draw of balls from the vase will yield a given combination of balls. We'll illustrate with a few specific cases.
1. Suppose the vase contains ten red and five blue balls. You draw two balls from the vase. The probability that both are red is the *product* of the probabilities that the first ball is red, and that the second ball is red:

$$
P(\text{two red balls}) = \frac{10}{15} \cdot \frac{9}{14} = \frac37.
$$

1. If we draw two balls from the same vase, the probability that one is red and one is blue is different, for two reasons: (1) after we've drawn a red ball, there are still five blue balls left, and (2) we did not specify which ball we draw first. Therefore:
```{math}
\begin{align*}
P(\text{one red and one blue ball}) &= P(\text{first a red and then a blue ball}) + P(\text{first a blue and then a red ball}) \\
&= \frac{10}{15} \cdot \frac{5}{14} + \frac{5}{15} \cdot \frac{10}{14} = \frac{5}{21} + \frac{5}{21} = \frac{10}{21}.
\end{align*}
```
1. If, after having drawn the first ball, we write down its color, but then place it back, and draw again, the probability of getting red twice changes:

$$
P(\text{two red balls with replacement}) = \frac{10}{15} \cdot \frac{10}{15} = \frac49.
$$

1. We now add three green balls to the vase. If we again draw two balls, without replacing them, we can calculate the probability that they are both not red in two ways: (1) we calculate the probabilities of two green, two blue, and a blue and a green one, and add them up, or (2) we calculate the probability of drawing a 'not red' ball, which is one minus the probability of drawing a red ball:

$$
P(\text{two balls which are not red}) = \left(1 - \frac{10}{18}\right) \cdot \left(1 - \frac{10}{17}\right) = \frac{8}{18} \cdot \frac{7}{17} = \frac{28}{153}.
$$

1. In the same setting as above, with ten red, five blue, and three green balls, the number of getting a red, blue and green ball if we draw three balls can be calculated as
```{math}
\begin{align*}
P(\text{one red, one blue, and one green ball}) &= 3! \, \cdot \, P(\text{first a red, then a blue, and then a green ball})  \\
&= 6 \cdot \frac{10}{18} \cdot \frac{5}{17} \cdot \frac{3}{16} = \frac{25}{136}.
\end{align*}
```

You may have noticed the general pattern: irrespective of whether we replace a drawn ball or keep it out of the vase, we can calculate the probability of any combination using the following general formula:
```{math}
:label: vaseformula
\begin{align*}
P(\text{combination}) &= (\text{number of ways the combination can be made}) \\
& \hspace{2cm} \times  P(\text{one specific order of the combination}).
\end{align*}
```

(sec:probabilityaxioms)=
### Probability axioms

\setcounter{axiom}{0}
Mathematicians like to formulate basic assumptions in terms of axioms. The (almost) universally accepted ones for probability theory are due to the Russian mathematician Andrey Kolmogorov, who formulated them in 1933. In modern language, to set up the axioms, we need the notion of a *sample space*&nbsp;$\Omega$, which is the collection of all possible outcomes of an experiment. We also have the notion of an event&nbsp;$E$, which is the actual outcome (plus, in formal mathematics, the collection $F$ of all events, known as the event space). Finally, for every event, we define a probability $P(E)$. Together, the combination $(\Omega, F, P)$ is known as a probability space, if they satisfy the following three axioms:
```{prf:axiom}
:label: axiom:nonnegativeprobability
The probability of an event is a non-negative number:

$$
P(E) \geq 0 \qquad \forall E \in F.
$$

```

```{prf:axiom} unitarity
:label: axiom:probabilityunitarity
The probability that at least one event in the entire sample space will occur is one:

$$
P(\Omega) = 1.
$$

```

```{prf:axiom} $\sigma$-additivity
:label: axiom:probabilityadditivity
The probability of any countable collection of disjoint (i.e., non-overlapping, or mutually exclusive) events $E_1, E_2, \ldots$ is the sum of the individual probabilities of these events<sup>[^2]</sup>:

$$
P\left( \bigcup_{i=1}^\infty E_i \right) = \sum_{i=1}^\infty P(E_i).
$$

```

Based on these three axioms, we can immediately prove that the probability function $P(E)$ has to satisfy some other properties.

```{prf:lemma}
:label: lemma:emptysetprobability
The probability of the empty set is $0$.
```

```{prf:proof}
Because $\emptyset \cup \emptyset = \emptyset$ and $\emptyset \cap \emptyset = \emptyset$, we have (by {prf:ref}`axiom:probabilityadditivity`):

$$
P(\emptyset) = P(\emptyset \cup \emptyset) = P(\emptyset) + P(\emptyset) = 2 P(\emptyset),
$$

which can only be true if $P(\emptyset) = 0$.
```

```{prf:lemma} monotonicity
If $A \subseteq B$, then $P(A) \leq P(B)$.
```

```{prf:proof}
Let $E_1 = A$ and $E_2 = B \backslash A$ (i.e. the part of $B$ that is not in $A$). Then $E_1 \cap E_2 = \emptyset$ and $E_1 \cup E_2 = B$, and by {prf:ref}`axiom:probabilityadditivity` and&nbsp;{prf:ref}`axiom:nonnegativeprobability` we have

$$
P(B) = P(E_1) + P(E_2) \geq P(E_1) = P(A).
$$

```

```{prf:lemma} complement rule
:label: lemma:complementrule
The probability of the complement of $A$, $A^\mathrm{C} = \Omega \backslash A$, is one minus the probability of $A$ itself:

$$
P(A^\mathrm{C}) = P(\Omega \backslash A) = 1 - P(A).
$$ (complementrule)

```

```{prf:proof}
Because $A \cap A^\mathrm{C} = \emptyset$ and $A \cup A^\mathrm{C} = \Omega$, we have by {prf:ref}`axiom:probabilityadditivity` and&nbsp;{prf:ref}`axiom:probabilityunitarity`

$$
P(A) + P(A^\mathrm{C}) = P(\Omega) = 1,
$$

which proves equation&nbsp;{eq}`complementrule`.
```

Note that the complement rule implies that every probability is bound from above to $1$; combining with the non-negativity axiom then gives that $0 \leq P(E) \leq 1$ for any event&nbsp;$E$.

{prf:ref}`axiom:probabilityadditivity` only gives us the sum of the probabilities of disjoint sets; using what we have proven so far, we can extend the rule to a sum rule for any two sets, known as the addition law of probability.
```{prf:theorem} addition law of probability
:label: thm:probabilityaddition
Let $A, B \subset \Omega$ be two subsets of the sample space, then

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B).
$$ (probabilityaddition)

```

````{prf:proof}
We first note that $B \backslash A = B \backslash (A \cap B)$ and $B$ can be decomposed in disjoint sets as $B = \left[B \backslash (A \cap B)\right] \cup (A \cap B)$. Therefore, by {prf:ref}`axiom:probabilityadditivity`:
```{math}
\begin{align*}
P(B) &= P\left(B \backslash (A \cap B)\right) + P(A \cap B) \\
P(A \cup B) &= P(A) + P(B \backslash A) = P(A) + P\left(B \backslash (A \cap B)\right) = P(A) + P(B) - P(A \cap B),
\end{align*}
```
which is equation&nbsp;{eq}`probabilityaddition`.
````

### Conditional probability
Stochastic events need not occur in vacuum: they may depend on each other. Therefore, the probability of $A$ could depend on a measured outcome of $B$, that is, if you have knowledge of $B$, that knowledge will affect the probabilities you can get for $A$. A simple example is the probability that the sum of two dice throws gives $12$. Without prior knowledge, this probability is $1/36$. However, if you know the value of one of the dice, the probability either becomes $1/6$ (if the first dice is a $6$) or $0$ (if the first dice has any other value).

The conditional probability of $A$ *given* a known value of $P(B) > 0$, written as $P(A | B)$, is given by the ratio of the probability that both $A$ and $B$ occur to the probability of $B$ itself<sup>[^3]</sup>

$$
P(A | B) = \frac{P(A \cap B)}{P(B)}.
$$ (conditionalprobability)

If $A$ and $B$ are *independent*, then $P(A \cap B) = P(A) \cdot P(B)$, and the conditional probability of $A$ given $B$ is just the same as the probability that $A$ happens.

Conditional probabilities are the foundations of Bayes theorem and Bayesian statistics.

(sec:probabilitymeasures)=
## Probability measures

```{index} probability distribution, mean
```
While it is impossible to predict the outcome of the throw of a single dice, it is easy to calculate the expected sum of the throw of a million dice, because each of the possible outcomes will occur $1/6$th of the time. Dividing by the one million dice (or one million throws of the same dice), we get the mean value of the throw of a dice, which is $3.5$, a number you will never get from a single throw. Given the probability of every possible outcome (the *probability distribution*, which we'll discuss in much more detail in {numref}`sec:discreteprobabilitydistributions` and&nbsp;{numref}`sec:continuousprobabilitydistributions`), we can calculate the *mean* value of the measurement of any stochastic variable&nbsp;$X$, denoted either $\langle X \rangle$ (usually by physicists) or $E(X)$ (usually by mathematicians):

$$
E(X) = \langle X \rangle = \sum_{k=1}^\infty x_k P(X = x_k),
$$ (discretemean)

```{index} expectation value
```
where the $x_k$ are the possible outcomes, and $P(X = x_k)$ denotes the probability that the outcome is $x_k$; the sum is of course finite if the number of possible outcomes is finite. Note that the mean is not necessarily the most likely outcome (as we've seen with the dice example, it may not even be a possible outcome). The most likely outcome is simply the one for which $P(X)$ has a maximum. Instead, the mean is the *expectation value*, i.e., the value you, on average, expect to get.

For a continuous stochastic variable, the sum in equation&nbsp;{eq}`discretemean` converges to an integral in the usual manner, and we have

$$
E(X) = \langle X \rangle = \int_{-\infty}^\infty x \, P(X=x) \mathrm{d}x.
$$ (continuousmean)

Note that while $P(X = x)$ itself is zero, $P(X = x) \mathrm{d}x$ is the probability that $X$ has a value in the range $[x, x + \mathrm{d}x]$, which in general is not zero. Naturally, the integral in&nbsp;{eq}`continuousmean` can be extended to multiple dimensions for a vector-valued stochastic variable&nbsp;$X$.

```{index} median
```
In many cases, the mean is a useful quantity to approximate the value of a stochastic variable. However, there are also many examples where it falls short, especially when there are significant outliers (values much larger or smaller than the typical value). A common example is the distribution of wealth or income. In such cases, people often use the *median*: the value $x$ for which $P(X \leq x) = P(X \geq x) = \frac12$.

Note that the mean is a linear function, and that the mean of a constant is just that constant. We have $\langle a X + b Y + c \rangle = a \langle X \rangle + b \langle Y \rangle + c$, for any constants $a$, $b$ and $c$ and stochastic variables $X$ and $Y$.

```{index} variance
```
While the mean gives us an indication of where the average of a distribution lies, it does not tell us how broad the distribution is around that mean. A measure for the spread of a distribution is its *variance*: the square of the average deviation of the mean (we need the square, as on average, you are exactly as often below the mean as above, so $\langle X - \ev{X} \rangle X \rangle} = 0$):

$$
\sigma^2(X) = \langle \left(X - \ev{X}\right)^2 \ranglee\right)^2}.
$$ (variance)

Because the mean is a linear function, we can expand the square in equation&nbsp;{eq}`variance`, giving us an alternative way to calculate the variance:

$$
\sigma^2(X) = \langle \left(X - \ev{X}\right)^2 \ranglee\right)^2} = \langle X^2 - 2 X \ev{X} + \ev{X}^2 \rangle+ \langle X \rangle^2} = \langle X^2 \rangle - 2 \langle X \rangle \langle X \rangle + \langle X \rangle^2 = \langle X^2 \rangle - \langle X \rangle^2.
$$ (variance2)

Note that the last two terms in equation&nbsp;{eq}`variance2` are different: the mean of the square is not the square of the mean, unless the spread is zero.

The variance is not linear. In particular, the variance of a constant is zero, and the variance of a constant&nbsp;$a$ times a stochastic variable&nbsp;$X$ is $\sigma^2(aX) = a^2 \sigma^2(X)$.

```{index} standard deviation
```
Instead of the variance, you will often encounter its square root, known as the *standard deviation*, 

$$
\sigma(X) = \sqrt{\sigma^2(X)}.
$$ (standarddeviation)

While the mean and the standard deviation are by far the most common measures you will encounter for probability distributions, there are others, dealing with increasingly subtle effects. All of them are functions of the *moments* of the distribution. The $n$th moment is defined as

$$
\langle X^n \rangle = \sum_{k=1}^\infty x_k^n P(X = x_k)
$$

(with the same extension to continuous variables as the mean). The *standardized moment* is the $n$th moment about the mean:

$$
\mu_n(X) = \langle (X - \ev{X})^n \rangle\rangle)^n}.
$$

```{index} skewness
```
The mean is often denoted by $\mu$, especially for continuous variables. The second standardized moment is the variance, the third is known as the *skewness*, a measure for the asymmetry of the distribution around the mean.

(sec:discreteprobabilitydistributions)=
## Discrete probability distributions

A discrete probability distribution is a function which gives the probability of each outcome for every possible outcome of an event involving a discrete stochastic variable $X$. By virtue of the unitarity {prf:ref}`axiom:probabilityunitarity`, any discrete probability distribution $P(X)$ is normalized:

$$
\sum_{k=1}^\infty P(X = x_k) = 1,
$$

where the $x_k$ indicate the possible outcomes.

```{index} cumulative distribution function
```
The function $f(x) = P(X = x)$ is sometimes referred to as the *probability mass function*. The *cumulative distribution function* $F_X(x)$ is defined as the probability that the value of $X$ is smaller than or equal to $x$:

$$
F_X(x) = P(X \leq x).
$$ (discreteCDF)

(sec:discreteuniformdistribution)=
### Uniform distribution

The simplest discrete probability distribution is the *uniform distribution*: every outcome is equally likely. If there are $N$ elements in the set of outcomes, each element has probability $1/N$. The mean in this case is simply the mean of all possible outcomes, and the variance the variance of the possible outcomes.

(sec:binomialdistribution)=
### Binomial distribution

```{index} binomial distribution
```
The *binomial distribution* is the distribution of the vase model with replacement. If there are $N$ balls, a fraction $p$ of which are red, then the probability to draw a red ball is $pN / N = p$. If we draw $n$ balls, counting and replacing after each draw, the probability of getting $k$ red balls is given by

$$
f(x) = P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}.
$$ (binomialdistribution)

Note that the stochastic variable&nbsp;$X$ here is the total number of red balls. We say that $X$ follows a binomial distribution with parameters&nbsp;$n$ and $p$, denoted $X \sim \mathcal{B}(n, p)$. In a slightly more abstract context, the binomial distribution describes a system in which we do $n$ experiments which can yield a binary (typically 'yes' or 'no') answer, with the probability that each answer is 'yes' is $p$. The distribution then tells us the probability that $k$ of the answers are 'yes'.

Calculating the mean and the variance of the binomial distribution is a straightforward exercise ({numref}`pb:binomialdistribution`), the answers are $np$ for the mean and $np(1-p)$ for the variance. It is also not difficult to show that the sum of two independent binomially distributed stochastic variables, $X \sim \mathcal{B}(n, p)$ and $Y \sim \mathcal{B}(m, p)$ is also binomially distributed, as $X+Y \sim \mathcal{B}(n+m, p)$.

(sec:geometricdistribution)=
### Bernoulli and geometric distribution

```{index} Bernoulli distribution
```
In many cases, there are only two possible outcomes of an experiment, which can be labeled in any way you like (red and blue, false and true, down and up, no and yes, failure and success). Irrespective of the qualitative label, we can always assign one outcome the value $0$ and the other the value $1$, and let $p$ be the probability of getting $1$. The resulting stochastic variable follows the *Bernoulli distribution*, which is a special case of the binomial distribution with $n=1$.

Things get more interesting if we make multiple *Bernoulli trials*, i.e. repeated attempts of the same experiment with the binary (either $0$ or $1$) outcome and fixed value of $p$. In particular, we will be interested in how many attempts we need to make to get the first success. For example, we can ask how many times must you throw a dice before you get a six. Here, we assign six the value 'success' and all other outcomes count as a 'failure'; therefore, in this example $p=1/6$.

```{index} geometric distribution
```
The number of trials you need to get a success follows the  *geometric distribution*. Unfortunately, there are two conventions, either just counting the number of failures before the first success (with possible outcomes $0, 1, 2, 3, \ldots$) or also including the first success itself (with possible outcomes $1, 2, 3, \ldots$). Taking the second convention, the probability that it takes $k$ attempts to get a success can easily be calculated as

$$
P(X = k) = (1-p)^{k-1} p.
$$ (geometricprobabilitydist)

The geometric distribution has mean $1/p$ and variance $(1-p)/p^2$. The geometric distribution can be generalized to count up to multiple successes; this more general distribution is known as the *negative binomial distribution* (which, unsurprisingly, also has multiple conventions).

(sec:hypergeometricdistribution)=
### Hypergeometric distribution

```{index} hypergeometric distribution
```
The binomial distribution, and by extension the Bernoulli and geometric distributions, originate in the vase model with replacement, resulting in a constant probability $p$ for a certain event. We can also describe a sampling from a population (like the balls in a vase) without replacement; the resulting distribution is known as the *hypergeometric distribution*. If there are $N$ balls in the vase, $K$ of which are red, the probability that $n$ draws without replacement give you $k$ red balls is given by

$$
P(X = k) = \frac{\binom{K}{k} \binom{N-K}{n-k}}{\binom{N}{n}}.
$$ (hypergeometricprobabilitydist)

The mean and variance of the hypergeometric distribution are $K n/N$ and $K (n/N) (N-K)/N (N-n)/(N-1)$, respectively. While it's good to know that this distribution exists, we will fortunately not encounter it often.

(sec:Poissondistribution)=
### Poisson distribution

Our final example of a discrete distribution does appear a lot. It deals with a slightly different setting than the ones we encountered so far: we now assume that events happen with a given constant rate $r$, with the events still independent from each other. Examples include radioactive decay and the number of meteorites striking the Earth. The probability that $k$ events then happen in a fixed time interval $\Delta t$ is then given by

$$
P(k \text{ events in interval } \Delta t) = \frac{(r \Delta t)^k e^{-r \Delta t}}{k!}.
$$

You will usually see the Poisson distribution expressed in terms of the parameter $\lambda = r \Delta t$, in which the probability mass function simply reads

$$
P(X = k) = \frac{\lambda^k e^\lambda}{k!}.
$$ (Poissondist)

We indicate that a stochastic random variable $X$ follows a Poisson distribution with parameter $\lambda$ by writing $X \ \sim \mathcal{P}(\lambda)$. A peculiar property of the Poisson distribution is that its mean and variance are equal, they're both $\lambda$. Moreover, the sum of two independent Poisson-distributed random variables with parameters $\lambda_1$ and $\lambda_2$ is again Poisson-distributed with parameter $\lambda_1 + \lambda_2$.

(sec:continuousprobabilitydistributions)=
## Continuous probability distributions

## Problems
```{exercise} Four-symbol codes.
:label: pb:andorcombinations
:class: dropdown
1. How many ways are there to make a code of either four digits or four letters?
1. How many ways are there to make a code of four symbols, where each symbol can be a number or a letter?
```

```{exercise}
:label: pb:binomialdistribution
:class: dropdown
We consider a stochastic variable $X$ which is equal to the number of positive outcomes of an set of $n$ experiments, each of which has a probability $p$ of yielding a positive outcome.
1. From the vase model, derive the expression&nbsp;{eq}`binomialdistribution` for the probability distribution of $X$.
1. Find the mean of $X$.
1. Find the variance of $X$.
1. Show that the sum of two independent binomially distributed stochastic variables, $X \sim \mathcal{B}(n, p)$ and $Y \sim \mathcal{B}(m, p)$ is also binomially distributed, as $X+Y \sim \mathcal{B}(n+m, p)$.
```

````{exercise} Bernoulli distribution
:label: pb:bernoullidistribution
:class: dropdown
If a random variable can only take the values $0$ and $1$ (which can represent any two-state system, in particular 'yes' and 'no' answers), and the probability of getting $1$ is $p$, then the variable follows the *Bernoulli distribution*, which is a special case of the bionomial distribution with $n=1$. The Bernoulli distribution with $p=1/2$ is the distribution with the lowest excess kurtosis. The kurtosis is the fourth standardized moment, measuring the 'tailedness' of the distribution, defined as
```{math}
:label: kurtosis
\mathrm{Kurt}(X) = \langle \left(\frac{X-\mu}{\sigma}\right)^2 \rangle = \frac{(\langle X-\mu)^4 \rangle}{((\langle X-\mu)^2 \rangle)^2} = \frac{\mu_4}{\sigma^4},
```
where $\mu$ and $\sigma$ are the distribution's mean and standard deviation, respectively. The excess kurtosis is simply the kurtosis minus three. Find the (excess) kurtosis of the Bernoulli distribution for arbitrary&nbsp;$p$, and show that for $p=1/2$ the excess kurtosis equals $-2$.
````

[^1]: Note that this statement applies only to the case where the total number of cases is finite. Things change if the total number of possibilities is infinite. For example, if you draw a random real number, the outcome could be exactly $42$, but the probability of getting exactly $42$ is zero, because there are infinitely many possibilities. Inversely, the probability of not getting any integer is $1$, but it is still possible that a random draw will result in an exact integer.

[^2]: In the mathematics literature, this property is known as $\sigma$-additivity; is in general a possible property of a function $\mu$ which takes a set as its argument and gives a number as output, i.e. a function $\mu$ which maps sets to numbers.

[^3]: Note that this is not a new axiom, but simply an application of the rule given in equation&nbsp;{eq}`probdef`.

