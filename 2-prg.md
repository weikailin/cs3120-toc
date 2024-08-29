---
layout: page
title: 2. Pseudo-Randomness
nav_order: 2
nav_exclude: false
---

$$
\newcommand{\RF}{\mathsf{RF}}
\newcommand{\PRF}{\mathsf{PRF}}
\newcommand{\Enc}{\mathsf{Enc}}
\newcommand{\Dec}{\mathsf{Dec}}
\newcommand{\Gen}{\mathsf{Gen}}
\newcommand{\Expr}{\mathsf{Expr}}
\newcommand{\state}{\mathsf{state}}
$$
{: .d-none}

Indistinguishability and Pseudo-Randomness
==========================================

Recall the perfectly secure encryption, OTP. 
That is, we bitwise-XOR our message with a uniform random string.

$$
m \oplus k, ~ |m| = |k|.
$$

OTP is inefficient because the long random string must be shared between Alice and Bob in advance.
Suppose that we have a (mathematical, deterministic) function 
that can extends a short truely random string to a long "random-looking" string.
We can use the seemingly random to encrypt messages as in OTP, yet it is efficient.

Is that possible?
How to formally define "random-looking"?

Let $$g$$ be the above function with short input $$x$$ and long output $$g(x)$$.
We want Alice and Bob share the same $$g(x)$$ to decrypt correctly, so $$g$$ must be deterministic. 
Mathematically, we have def for the distance between two probability distributions.
However, for any $$|g(x)| \gt |x|$$, the input / output distributions are far.
The point is "random-looking" at best.

$$
m \oplus g(s), ~ |m| = |g(s)|, \text{ but } |s| \ll |m| = |g(s)|.
$$

We will introduce computational indistinguishability, and then define pseudo-random generator (PRG) and pseudo-random function (PRF).
Prior to that, we need to define efficient algorithms (to model honest procedures) and adversaries.

Efficient Computation and Efficient Adversaries
------------------

We want to provide "efficient computation" to the honest users.

#### **Definition:** Deterministic Algorithm

{: .defn}
> An algorithm $$\cA$$ is defined to be a deterministic Turing Machine with input and output as bit strings, $$\bit^\ast$$.

Recall that a Turing Machine is by definition *uniform*, that is, 

- The description length of $$\cA$$ is constant for all inputs (no matter how long it is).

Also notice that the definitiona of algorithm here is different from some algorithm textbooks, e.g.,
we do not require an algorithm to halt in finite time (unless explicitly specified, see next).

#### **Definition:** Polynomial Running-Time

{: .defn}
> $$\cA$$ runs in time $$T(n)$$ if $$\forall x \in \bits$$, 
> $$\cA(x)$$ halts within $$T(|x|)$$ steps. 
> $$\cA$$ runs in *polynomial time* if there exists a constant $$c$$ such that $$\cA$$ runs
> in time $$T(n) = n^c$$.

#### **Definition:** Efficient Computation

{: .defn}
> We say an algorithm is *efficient* if it runs in polynomial time.

Justification of poly time:

- Indep of computation models (TM, circuit, ...)
- Closed under compositions of algorithms
- From human experience: many poly-time algorithms are improved later to cubic time, but many super-polynomial time algorithm/problems are unclear if we can solve in polynomial time.

As discussed in perfect secrecy, we need randomized algorithms to construct encryption (and more generally crypto).

#### **Definition:** Randomized (or Probabilistic) Algorithm

{: .defn}
> A *randomized* algorithm $$\cA$$, also called a *probabilistic* polynomial-time Turing Machine
> and abbreviated as PPT, is a deterministic algorithm equipped with an extra random tape. 
> Each bit of the random tape is uniformly and independently chosen.
> 
> We denote the computation by $$y \gets \cA(x ; r)$$ but sometimes omit $$r$$. 
> When we say a randomized algorithm runs in time $$T(n)$$, 
> the running time shall be $$\le T$$ for all $$(x,r)$$.

As an example, we define efficient and correct encryption.

#### **Example:** Efficient Private-key Encryption.

{: .defn}
> $$(\Gen, \Enc, \Dec)$$ is called an *efficient private-key encryption scheme* w.r.t. message space $$\cM$$ if:
> 1. $$k \gets \Gen(1^n)$$ is PPT s.t. for every $$n \in \N$$, it samples $$k$$.
> 2. $$c \gets \Enc_k(m)$$ is PPT s.t. $$k, m \in \cM$$, outputs $$c$$.
> 3. $$m \gets \Dec_k(c)$$ is PPT s.t. $$c, k$$, outputs $$m \in \cM \cup\bot$$.
> 4. Correctness: $$\forall n \in \N$$, $$m \in \cM$$,
> 
> $$
> \Pr \left[k \gets \Gen(1^n) : \Dec_k(\Enc_k(m)) = m \right] = 1.
> $$

Note: the notation $$1^n$$ means the string of $$n$$ copies 1's, it is called the *security parameter*.
The purpose is to instantiate the "security" of the scheme, e.g., $$n$$-bit key.
We write unary $$1^n$$ (but not $$n$$ as binary) because "poly-time" is defined by the input length.

### Adversaries: Non-Uniform

Next we want to model adversaries with a stronger capability than honest.

#### **Definition:** Non-Uniform PPT

{: .defn}
> A *non-uniform* PPT machine (abbreviated nuPPT) $$\cA$$ is a sequence
> of algos $$\cA = \set{\cA_1, \cA_2, \dots}$$ s.t.:
> - $$\cA_i$$ computes on inputs of length $$i$$, and
> - exists a polynomial $$d$$ s.t. the description size $$|A_i| \lt d(i)$$ 
>   and the time $$\cA_i$$ is also less than $$d(i)$$. 
> We write $$\cA(x)$$ to denote the computation $$\cA_{|x|}(x)$$.
> 
> Alternatively, an nuPPT algo can be defined as a *uniform* PPT $$\cA$$ that
> takes an additional *advice* string of poly length $$d(i)$$ for each input length $$i$$.

Purpose: 
non-uniform gives adv extra power and models many real scenario, 
e.g., Eve may have a list of known (plain, cipher) pairs.

Discuss: the advice may not be computable in poly time 
(if poly-time, then no need to take advice as input). NU is closed under reduction.


Computational Indistinguishability
------------------------

Key Idea:
If we have no way to show the difference, then we are satisfied. We call it indistinguishability.

Example: Turing test, when a machine and a human is indistinguishable in *every* human's prompts, we call it AI.
- [Turing 1950, Computing machinery and intelligence](https://link.springer.com/chapter/10.1007/978-1-4020-6710-5_3)
- [Wigderson 2022, Imitation game](https://www.youtube.com/watch?v=JZH1AT1kdK8)

Observation: they are *not* the same, not even close in any sense; 
however, the distinguisher "another human" can not tell the difference due to a limited power.

Concept: we say a distribution is pseudorandom if for *every* efficient algorithm,
it can not be distinguished from a (truely) uniform distribution.

We will formalize the concept asymptotically.

#### **Definition:** Ensembles of Probability Distributions

{: .defn}
> A sequence $$\set{X_n}_{n\in\N}$$ is called an *ensemble* if for each $$n \in \N$$, 
> $$X_n$$ is a probability distribution over $$\bits$$.
> (We often write $$\cX = \set{X_n}_n$$ when the context is clear.)

E.g., supposing $$X_n$$ is a distribution over $$n$$-bit strings for all $$n\in\N$$, $$\set{X_n}_{n\in\N}$$ is an ensemble.

#### **Definition:** Computational Indistinguishability

{: .defn}
> Let $$\cX = \set{X_n}_n$$ and $$\cY = \set{Y_n}_n$$ be ensembles 
> where $$X_n, Y_n$$ are distributions over $$\bit^{\ell(n)}$$ for some polynomial $$\ell(·)$$. 
> We say that $$\cX$$ and $$\cY$$ are *computationally indistinguishable*
> (denoted by $$\cX \approx \cY$$) 
> if for all NUPPT $$D$$ (called the “distinguisher”), there exists a negligible function $$\eps$$
> such that $$\forall n \in \N$$,
> 
> $$
> \Big| \Pr[t \gets X_n, D(t) = 1] − \Pr[t \gets Y_n, D(t) = 1] \Big| \lt \eps(n).
> $$

Note: /
- "=1" is a convention in literature
- "absolute" is not necessary due to "for all D"

This definition requires the two distributions to pass *all efficient* statistical tests,
which include the following.
- Roughly as many 0 as 1.
- Roughly as many 01 as 10.
- Each sequence of bits occurs with roughly the same probability.
- Given any prefix, guessing the next bit correctly happens with roughly the same probability.

#### **Lemma:** Closure Under Efficient Operations

{: .theorem}
> If the pair of ensembles $$\set{X_n}_n \approx \set{Y_n}_n$$, 
> then for any NUPPT $$M$$, $$\set{M(X_n)}_n \approx \set{M(Y_n)}_n$$.

{: .proof}
> (By standard reduction) 

Examples:

1. $$M$$ ignores its input. Clearly, $$M(X_n) \equiv M(Y_n)$$ for all $$n$$.
2. $$M$$ is identity, i.e., its output is exactly the input. $$\set{M(X_n) = X_n}_n \approx \set{M(Y_n)=Y_n}_n$$.
3. $$M$$ outputs the first half of the input, 
   i.e., $$M(x) := x[1, ..., |x|/2]$$.

#### **Lemma:** Hybrid Lemma

{: .theorem}
> Let $$X^{(1)}, X^{(2)}, ..., X^{(m)}$$ be a sequence of probability distributions. 
> Assume that the machine $$D$$ distinguishes $$X^{(1)}$$ and $$X^{(m)}$$ with probability $$p$$. 
> Then there exists some $$i \in \set{1, ..., m - 1}$$ s.t. 
> $$D$$ distinguishes $$X^{(i)}$$ and $$X^{(i+1)}$$ with probability $$p/(m-1)$$.

{: .proof}
> By triangular inequality. 
> Namely, fixing any $$D$$, for any $$i,j \in [m]$$, define 
> 
> $$
> d(i,j) := \card{ \Pr_{t\gets X^{(i)}}[D(t)=1] - \Pr_{t\gets X^{(j)}}[D(t)=1] }.
> $$
> 
> Then, we have
> 
> $$
> \begin{align*}
> d(1,m) \le d(1,2)+d(2,3)+ ... +d(m-1, m).
> \end{align*}
> $$
> 
> Hence, given that $$d(1,m) = p$$, we have that $$d(i,i+1) \ge p/(m-1)$$ for some $$i\in[m-1]$$.

Notice that this lemma applies to distributions, *not ensembles*.
Fortunately, it implies the following.

#### **Corollary:**

{: .theorem}
> For any ensembles $$\cX, \cY, \cZ$$, if $$\cX \approx \cY$$ and $$\cY \approx \cZ$$,
> then it follows that $$\cX \approx \cZ$$.

{: .proof}
> (left as exercise)

**Discuss**{: .label}
If the number of hybrid distributions (between two ensembles) depends on 
the size $$n$$ (of the distributions in the ensembles), the above corollary is tricky.
Consider two ensembles $$\cX = \set{X_n}_n, \cY=\set{Y_n}_n$$, and suppose that
the machine $$D$$ distinguishes $$\cX, \cY$$ w.p. $$p(n)$$ (that depends on $$n$$),
and then suppose that the sequence $$(X_n = X_n^{(1)}, ... , X_n^{(m(n))} = Y_n)$$
consists of $$m(n)$$ distributions such that $$m$$ depends on $$n$$.
Then, we *can not* define $$m(n)$$ ensembles between $$\cX$$ and $$\cY$$ due to the dependence 
(i.e., the length of the sequence depends on $$n$$).
This is indeed the case when we have many hybrids, e.g., going from $$(n+1)$$-bit PRG to $$2n$$-bit PRG.
There are two ways to treat this case, the formal one and the more popular one.
In the formal way, we assume for contra that exists $$D$$ and $$p(n)$$ s.t. 
for inf many $$n\in\N$$, $$D$$ distinguishes $$(X_n, Y_n)$$ w.p. at least $$p(n)$$;
we then construct a reduction $$B$$ such that *guesses* an index $$j \in [m(n)-1]$$ 
and hoping that $$j = i$$, where $$i$$ is the index given by hybrid lemma, 
so that $$B$$ runs $$D$$ to distinguish and solve the challenge specified by the $$j$$-th hybrid.
The popular way is less rigorous but more intuitive:
we just claim that the two distributions $$X_n^{(j)}, X_n^{(j+1)}$$ are "indistinguishable"
for each $$j, n$$, and thus $$X_n, Y_n$$ are "indistinguishable";
this is informal because fixing any $$j$$ means that $$n$$ is also fixed and $$X_n, Y_n$$ are two distributions (not ensembles), 
but indistinguishability is defined asymptotically on ensembles.

Example:
Let $$\cX, \cY, \cZ, \cZ'$$ be ensembles.
Suppose that $$(\cX, \cZ) \approx (\cX, \cZ')$$ and $$(\cY, \cZ) \approx (\cY, \cZ')$$.
Does $$(\cX, \cY, \cZ) \approx (\cX, \cY, \cZ')$$?

#### **Lemma:** Prediction Lemma

{: .theorem}
> Let $$\set{X^0_n}_n$$ and $$\set{X^1_n}_n$$ be two ensembles where $$X^0_n, X^1_n$$ are 
> probability distributions over $$\bit^{\ell(n)}$$ for some polynomial $$\ell(\cdot)$$, 
> and let $$D$$ be a NUPPT machine that distinguishes between $$\set{X^0_n}_n$$ and $$\set{X^1_n}_n$$
> with probability $$\ge p(·)$$ for infinitely many $$n \in \N$$.
> Then there exists a NUPPT $$A$$ such that
> 
> $$
> \Pr[b \gets \bit, t \gets X^b_n : A(t) = b] \ge \frac{1}{2} + \frac{p(n)}{2}
> $$
> 
> for infinitely many $$n \in \N$$.

{: .proof}
> Remove the absolute value in the def of comp. ind. by negating the distinguisher $$D$$,
> and then standard probability. 

Note: the converse the easier to prove. Hence, prediction and distinguishing is essentially equivalent.

Pseudo-Random Generator 
------------------------

#### **Definition:** Pseudo-random Ensembles.

{: .defn}
> The probability ensemble $$\set{X_n}_n$$, where $$X_n$$ is a probability distribution
> over $$\bit^{l(n)}$$ for some polynomial $$l(\cdot)$$, is said to be pseudorandom 
> if $$\set{X_n}_n \approx \set{U_{l(n)}}_n$$,
> where $$U_m$$ is the uniform distribution over $$\bit^m$$.

Note:
- this definition says that a pseudorandom distribution must pass 
  **all** efficiently computable tests that the uniform distribution would have passesd.
- it is hard to check or prove if a distribution is pseudorandom 
  (due to the "for all" quantifier from comp. ind.)

#### **Definition:** Pseudo-random Generators.

{: .defn}
> A function $$g : \bit^\ast \to \bit^\ast$$ is a *Pseudo-random Generator (PRG)* 
> if the following holds.
> 1. (efficiency): $$g$$ can be computed in PPT.
> 2. (expansion): 
>    $$|g(x)| \gt |x|$$
> 3. The ensemble $$\set{x \gets U_n : g(x)}_n$$ is pseudorandom.

We sometimes say that the expansion of PRG $$g$$ is $$t$$ 
if $$|g(x)| - |x| \ge t$$ for all $$x$$.

Example: if $$g: \bit^n \to \bit^{n+1}$$ for all $$n$$ is a PRG, then $$g$$ is a OWF.
(proof left as exercise, why expansion is necessary?)

#### **Example:** Existence of PRG implies $$NP \neq P$$

{:.theorem}
> Suppose that $$g: \bits \to \bits$$ is a PRG.
> Then, the language $$L := \set{g(s) : s \in \bits} \in NP$$ and $$L \notin P$$.

{:.proof}
> It is direct to see $$L \in NP$$.
> To see $$L \notin P$$, suppose for contradiction, there exists a polynomial time algorithm $$A$$
> that decides $$L$$, then $$A$$ can easily break the pseudorandomness of $$g$$, a contradition.

This is indeed the case for all cryptographic objects:
$$NP \neq P$$ is necessary for the objects to exist.
Since $$NP \neq P$$ is long open, cryptography is built on **assumptions**.
Ideally, even we can not prove or disprove $$NP \neq P$$, we want the "win-win" scenario:

- If $$NP = P$$, then we can solve all $$NP$$ problems efficiently in polynomial time.
  This is a world called Algorithmica, but we do not have cryptography.

- Otherwise $$NP \neq P$$, then there exist some hard problems in $$NP$$ 
  that can not be solved in polynomial time.
  Ideally, we want to utilize the hard problems to build cryptographic objects
  (so that any polynomial-time adversary can not break).

This explained why cryptography needs assumptions, but **what is a good assumption?**
Ideally, the minimal assumption would be $$NP \neq P$$, or equivalently, $$SAT \notin P$$.
Unfortunately, we do not know how to build crypto assuming only $$NP \neq P$$.
So far, cryptography is build on factoring, RSA, ..., we will discuss more on them.
Notice that we still have the win-win w.r.t. the assumptions, e.g.,
either we can solve factoring in polynomial time (which would solve a century-old problem),
or we have cryptography.

Here, PRG is the assumption that gives us encryption.
It is currently an abstract object, but 
later we will show how PRG connects cryptography and other assumptions.

It also partly explains why we still can have crypto even when 
we can use quantum computers to break factoring, RSA, and 
other number-theoretic assumptions:
there are other problems in $$NP$$ that still resist quantum algorithms.
It is interesting to observe that the thousand-year seek of secure encryption 
is deeply rooted in complexity (e.g., DES, MD5, Enigma, ... are broken).

Also notice again that the discussion is asymptotic for all problem sizes,
and that some real-world cryptographic constructions are not asymptotic
and thus they do not fit in
(e.g., AES and SHA are defined only for 128, 256, and 512)

#### **Lemma:** Expansion of a PRG

{:.theorem}
> Let $$g:\bit^n \to \bit^{n+1}$$ to be a PRG for all $$n \in\N$$. 
> For any polynomial $$\ell(n) \gt n$$, define $$g': \bit^n \to \bit^{\ell(n)}$$ as follows:
> 
> $$
> g'(s) \to b_1 b_2 ... b_{\ell},
> $$
> 
> where 
> $$\ell := \ell(|s|)$$, 
> $$x_0 \gets s, x_{i+1} \| b_{i+1} \gets g(x_i)$$. Then $$g'$$ is a PRG.

{:.proof-title}
> Proof, warmup:
> 
> Suppose that $$\ell = 2$$, no expansion, but we want to show pseudorandomness.
> Define distributions 
> 
> $$
> H^0_n := g'(s), H^1_n := U_1 \| g(s)[n+1], H^2_n := U_2
> $$
> 
> for $$n \in \N$$, and define $$\cH^i := \set{H^i_n}_n$$ for $$i=0,1,2$$.
> Since $$g'(s) = g(s)[n+1] \| g(g(s)[1...n])[n+1]$$, by $$g(s) \approx U_{n+1}$$ and closure,
> we have $$\cH^0 \approx \cH^1$$.
> By $$g(x)$$ is pseudorandom and closure, $$g(U_n)[n+1] \approx U_1$$, which implies $$\cH^1 \approx \cH^2$$.
> By the corollary of hybrid lemma, we have $$\cH^0 \approx \cH^2$$.

{:.proof-title}
> Proof of PRG Expansion
> 
> It is slightly tricky when $$\ell$$ depends on $$n$$.
> Define the prefix $$h$$ and last bit $$s$$ of iterating $$g$$ as:
> 
> $$
> h^i(x) := \begin{cases}
>   g(x)[1...n] & i = 1,\\
>   g(h^{i-1}(x))[1...n] & i > 1
> \end{cases}
> $$
> 
> and
> 
> $$
> s^i := s^i(x) := \begin{cases}
>   g(x)[n+1]  & i=1,\\
>   g(h^{i-1}(x))[n+1] & i \gt 1.
> \end{cases}
> $$
> 
> We have $$g'(x) = s^1 \| s^2 \| ...s^{\ell}$$, and we want to prove it through Hybrid Lemma.
> Given $$n$$, define hybrid distributions $$H_0 := g'(x)$$, $$H_{\ell} := U_{\ell}$$,
> and define $$H_i$$ for $$i = 1,...,\ell-1$$ as 
> 
> $$
> H_i := U_i \| s^{1} \| ...s^{\ell(n)-i},
> $$
> 
> where $$U_i$$ denotes sampling an $$i$$-bit string uniformly at random.
> Observe that for each $$i=0,1,...,\ell-1$$, $$H_i$$ and $$H_{i+1}$$ differ by a $$g(x)$$, that is,
> 
> $$
> \begin{align*}
> H_{i+1} & = U_{i} \| U_1 \| s^{1} \| ...s^{\ell-i-1}, \text{ and } \\
> H_{i} & = U_{i} \| s^{1} \| s^{2} \| ...s^{\ell-i} \\
> & = U_{i} \| g(x)[n+1] \| s^{1}(g(x)[1...n]) \| ...s^{\ell-i-1}(g(x)[1...n])
> \end{align*}
> $$
> 
> for all $$i = 0, 1, ..., \ell$$.
> 
> Assume for contra (AC), there exists NUPPT $$D$$, poly $$p(n)$$ s.t. for inf many $$n\in\N$$,
> $$D$$ distinguishes $$\set{x\gets\bit^n : g(x)}_n$$ and $$U_{\ell(n)}$$ w.p. at least $$1/p(n)$$.
> The intuition is to apply Hybrid Lemma so that there exists $$j^\ast$$ 
> such that $$H_{j^*}, H_{j^\ast+1}$$ are distinguishable, 
> and thus by Closure Lemma $$g(x)$$ is distinguishable from uniform.
> 
> We prove it formally by constructing $$D'$$ that aims to distinguish $$g(x)$$.
> Given input $$t \in \bit^{n+1}$$, $$D'$$ performs:
> 1. Samplable $$i \gets \set{0,...,\ell-1}$$ (where $$\ell \gets \ell(n)$$)
> 2. $$t_0 \gets U_i$$, $$t_1 \gets t[n+1]$$, and $$t_2 \gets s^1(t[1...n]) \| s^2(t[1...n]) \| ...s^{\ell-i-1}(t[1...n])$$
> 3. output $$D(t_0 \| t_1 \| t_2)$$
> 
> To show that $$D'$$ succeed with non-negl prob., we partition the event as follows:
> 
> $$
> \begin{align*}
> & \Pr_{t\gets U_{n+1}, i} [D'(t) = 1] - \Pr_{x\gets U_n, i} [D'(g(x)) = 1] \\
> =& \sum_{j=0}^{\ell-1} \Pr_{t, i} [D'(t) = 1 \cap i=j] - \Pr_{x, i} [D'(g(x)) = 1 \cap i=j] \\
> =& \sum_{j=0}^{\ell-1} \left(\Pr_{t, i} [D'(t) = 1 | i=j] - \Pr_{x, i} [D'(g(x)) = 1 | i=j]\right) \cdot \Pr[i=j] \\
> =& \frac{1}{\ell} \cdot \sum_{j=0}^{\ell-1} \Pr_{t, i} [D'(t) = 1 | i=j] - \Pr_{x, i} [D'(g(x)) = 1 | i=j] \\
> \end{align*}
> $$
> 
> where the random variable $$i \gets \set{0,1,...,\ell-1}$$ is sampled exactly the same as in $$D'$$. 
> 
> Notice that conditioned on $$i = j$$ for any fixed $$j$$, the distribution $$t_0 \| t_1 \| t_2$$ (given to $$D$$)
> is identical to 
> 
> $$
> \begin{cases}
> H_{j+1} & \text{if } t \gets \bit^{n+1}\\
> H_{j}  &  \text{if } x \gets \bit^n, t \gets g(x).
> \end{cases}
> $$
> 
> That implies 
> 
> $$
> \begin{align*}
> \Pr_{t,i} [D'(t) = 1 | i=j] = \Pr[t' \gets H_{j+1} : D(t') = 1], \\
> \Pr_{x,i} [D'(t) = 1 | i=j] = \Pr[t' \gets H_{j} : D(t') = 1].
> \end{align*}
> $$
> 
> We thus have the summations cancelling out,
> 
> $$
> \begin{align*}
> & \Pr_{t\gets U_{n+1}, i} [D'(t) = 1] - \Pr_{x\gets U_n, i} [D'(g(x)) = 1] \\
> =& \frac{1}{\ell} \cdot \sum_{j=0}^{\ell-1} \Pr_{t'\gets H_{j+1}} [D(t') = 1] - \Pr_{t' \gets H_j} [D(t') = 1] \\
> =& \frac{1}{\ell} \cdot \left(\Pr_{t'\gets H_\ell} [D(t') = 1] - \Pr_{t' \gets H_0} [D(t') = 1]\right) \\
> \ge& \frac{1}{\ell} \cdot \frac{1}{p(n)},
> \end{align*}
> $$
> 
> where the last inequality follows by (AC).
> That is, $$D'$$ distinguishes $$g(x)$$ w.p. at least $$\frac{1}{\ell(n)p(n)}$$, contradicting $$g$$ is a PRG.

**Discuss**{:.label}
In the above, we proved it formally and preserved the uniformity (if $$D$$ is a uniform TM, then $$D'$$ is also uniform). 
We did not apply Hybrid Lemma (and no triangular ineq), nor did we use Closure Lemma.
Alternatively after (AC), one may apply Hybrid Lemma which claims that exists $$j^\ast$$
s.t. $$H_{j^\ast}$$ is distinguishable from $$H^{j^\ast+1}$$ w.p. at least $$1/(\ell p)$$,
and then hardwire $$j^\ast$$ into $$D'$$ in order to distinguish $$g(x)$$.
This would make $$D'$$ **non-uniform** because $$j^\ast$$ would depend on each $$n$$ 
and we would not have an efficient way to find $$j^\ast$$.

We proved in the above that a PRG with 1-bit expansion is sufficient to build any poly-long expansion.
We have not yet give any candidate construct of PRG (even 1-bit expansion), 
but it is useful to firstly see what we can achieve using PRGs.

Example:
Now suppose that we have a PRG $$g$$ with $$n \mapsto \ell(n)$$ expansion for any poly $$\ell$$.
We can construct a *computationally* secure encryption by 
sampling key $$k$$ as an $$n$$-bit string and then bitwise XORing $$g(k)$$ with the message.
That $$m \oplus g(k)$$ encrypts one message.
We can encrypt more messages by attaching to each message a sequence number,
such as $$(m_1 \oplus g(k)[1...n], 1), (m_2 \oplus g(k)[n...2n], 2)$$, and so on.

What's the downside of the above multi-message encryption?

Pseudo-Random Functions 
------------------------

In order to apply PRGs more efficiently, 
we construct a tree structure and call the abstraction pseudo-random functions (PRFs).
We begin with defining (truly) random function.

#### **Definition:** Random Functions

{: .defn}
> A random function $$f: \bit^n \to \bit^n$$ is a random variable sampled uniformly 
> from the set $$\RF_n := \set{f : \bit^n \to \bit^n}$$.

We can view a random function in two ways.
In the combinatorial view, any function $$f: \bit^n \to \bit^n$$ is described by
a table of $$2^n$$ entries, each entry is the $$n$$-bit string, $$f(x)$$.

$$f(0000...00),f(0000...01), ...,f(1111...11)$$

In the computational view, a random function $$f$$ is a data structure that on any input $$x$$,
perform the following:
1. initialize a map $$m$$ to empty before any query
2. if $$x \notin m$$, then sample $$y \gets \bit^n$$ and set $$m[x] \gets y$$
3. output $$m[x]$$

In both views, the random function needs $$2^n \cdot n$$ bits to describe,
and thus there are $$2^{n2^n}$$ random functions in $$\RF_n$$.

Note: the random function $$F\gets \RF_n$$ is also known as *random oracle* in the literature.

Intuitively, a *pseudo-random* function (PRF) shall look similar to a random function.
That is, indistinguishable by any NUPPT Turing machine that is *capable of interacting with the function*.

#### **Definition:** Oracle Indistinguishability

{:.defn}
> Let $$\set{\cO^0_n}_{n\in\N}$$ and $$\set{\cO^1_n}_{n\in\N}$$ be ensembles 
> where $$\cO^0_n, \cO^1_n$$ are probability distributions over functions.
> We say that $$\set{\cO^0_n}_{n}$$ and $$\set{\cO^1_n}_{n}$$ are *computationally indistinguishable*
> if if for all NUPPT machines $$D$$ that is given oracle accesses to a function, 
> there exists a negligible function $$\eps(\cdot)$$ such that for all $$n\in\N$$,
>   
> $$
> \Pr[F\gets\cO^0 : D^{F(\cdot)}(1^n) = 1] - \Pr[F\gets\cO^1 : D^{F(\cdot)}(1^n) = 1] \le \eps(n).
> $$

Note: $$D^{f(\cdot)}$$ denotes that the TM $$D$$ may interact with the function $$f$$ 
through black-box input and output, while each input-output takes time to read/write 
but computing $$f$$ takes 0 time.

It is easy to verify that oracle indistinguishability satisfies “closure under efficient operations”, 
the Hybrid Lemma, and the Prediction Lemma.

Also notic that we can transform a distribution of oracle functions to 
a distribution of strings using an efficient oracle operation, 
and in that case, the oracle indistinguishability is translated into the comp. indistinguishability
of strings (see CPA-secure encryption below).

#### **Definition:** Pseudo-random Functions (PRFs)

{:.defn}
> A family of functions $$\set{f_s: \bit^{|s|} \to \bit^{|s|}}_{s \in \bits}$$
> is *pseudo-random* if
> 
> - (Easy to compute): $$f_s(x)$$ can be computed by a PPT algo that is given input $$s,x$$.
> - (Pseudorandom): $$\set{s\gets \bit^n : f_s}_n \approx \set{F \gets \RF_n : F}_n$$.

Note: similar to PRG, the seed $$s$$ is not revealed to $$D$$ (otherwise it is trivial to distinguish).

#### **Theorem:** Construct PRF from PRG [Goldreich-Goldwasser-Micali 84]

{:.theorem}
> If a pseudorandom generator exists, then pseudorandom functions exist.

We have shown that a PRG with 1-bit expansion implies any PRG with poly expansion.
So, let $$g$$ be a length-doubling PRG, i.e., $$|g(x)| = 2 |x|$$.
Also, define $$g_0, g_1$$ to be 

$$
g_0(x) := g(x)[1...n], \text{ and } g_1:= g(x)[n...2n],
$$

where 
$$n := |x|$$ is the input length.

We define $$f_s$$ as follows to be a PRF:

$$
f_s(b_1 b_2 ... b_n) := g_{b_n} \circ g_{b_{n-1}} \circ ... g_{b_1}(s).
$$

That is, we evaluate $$g$$ on $$s$$, but keep only one side of the output depending on $$b_1$$,
and then keep applying $$g$$ on the kept side, and then continue to choose the side by $$b_2$$, and so on.

This constructs a binary tree. 
The intuition is from expanding the 1-bit PRG,
but now we want that any sub-string of the expansion can be efficiently computed.
(We CS people love binary trees.)
Clearly, $$f_s$$ is easy to compute, and we want to prove it is pseudorandom.

{:.proof}
> There are $$2^n$$ leaves in the tree, too many so that we can not use the
> "switch one more PRG to uniform in each hybrid" technique as in expanding PRG.
> The trick is that the distinguisher $$D$$ can only query $$f_s$$ at most polynomial many times
> since $$D$$ is poly-time.
> Each query correspond to a path in the binary tree, and there are at most 
> polynomial many nodes in all queries.
> Hence, we will switch the $$g(x)$$ evaluations from root to leaves of the tree
> and from the first query to the last query.
> 
> Note: switching *each instance* of $$g(x)$$ (for each $$x$$) is a reduction
> that runs $$D$$ to distinguish *one instance* of $$g(x)$$; 
> therefore, we switch *exactly one* in each hybrid.
> 
> More formally, assume for contra (AC), there exists NUPPT $$D$$, poly $$p$$ s.t.
> for inf many $$n\in\N$$, $$D$$ distinguishes $$f_s$$ from RF (in the oracle interaction).
> We want to construct $$D'$$ that distinguishes $$g(x)$$.
> We define hybrid oracles $$H_i(b_1 ... b_n)$$ as follows:
> 
> 1. the map $$m$$ is initialized to empty
> 2. if the prefix $$b_1 ... b_i \notin m$$, then sample $$s(b_{i} b_{i-1} ... b_{1}) \gets \bit^n$$ 
>    and set $$m[b_i ... b_1] \gets s(b_{i} b_{i-1} ... b_{1})$$
> 3. output $$g_{b_n} \circ g_{b_{n-1}} \circ ... g_{b_{i-1}}(m[b_{i} ... b_{1}])$$
> 
> Notice that $$H_i$$ is a function defined using the computational view.
> 
> Let $$\PRF_n := \set{f_s : s \gets \bit^n}$$ be the distribution of $$f_s$$ for short.
> We have $$H_0 \equiv \PRF_n$$ and $$H_n \equiv \RF_n$$, 
> but there are still too many switches between $$H_i, H_{i+1}$$.
> The key observation is that,
> given $$D$$ is PPT, we know a poly $$T(n)$$ that is the running time of $$D$$ on $$1^n$$,
> and then we just need to switch at most $$T(n)$$ instances of $$g(x)$$.
> That is to define sub-hybrids $$H_{i,j}$$,
> 
> 1. the map $$m$$ is initialized to empty
> 2. if the prefix $$b_1 ... b_i b_{i+1} \notin m$$, 
>    then depending on the "number of queries" that are made to $$H_{i,j}$$ so far, including the current query,
>    do the following:
>    sample $$s \gets \bit^n$$, set 
>    
>    $$
>    m[b_{i+1} b_i ... b_1] \gets 
>    \begin{cases}
>      \bit^n   & \text{number of queries} \le j \\
>      g_{b_{i+1}}(s)     & \text{otherwise}
>    \end{cases},
>    $$
>    
>    and set
>    
>    $$
>    m[\overline{b_{i+1}} b_i ... b_1] \gets 
>    \begin{cases}
>      \bit^n   & \text{number of queries} \le j \\
>      g_{\overline{b_{i+1}}}(s)     & \text{otherwise}
>    \end{cases}.
>    $$
>    
> 3. output $$g_{b_n} \circ g_{b_{n-1}} \circ ... g_{b_{i}}(m[b_{i+1} ... b_{1}])$$
> 
> We have $$H_{i,0} \equiv H_i$$. 
> Moreover for any $$D$$ runs in time $$T(n)$$, we have $$H_{i,T(n)} \equiv H_{i+1}$$
> (their combinatorial views differ, but their computational views are identical for $$T(n)$$ queries).
> Now we have $$n \cdot T(n)$$ hybrids, so we can construct $$D'(t)$$:
> 
> 1. sample $$i \gets \set{0,1,...,n-1}$$ and $$j\gets\set{0,...,T(n)-1}$$ uniformly at random
> 2. define oracle $$O\_{i,j,t}(\cdot)$$ such that is similar to $$H\_{i,j}$$ but 
>    "injects" $$t$$ to the map $$m$$ in the $$j$$-th query if the prefix $$b\_1 ... b\_i b\_{i+1} \notin m$$.
>    (This is constructable and computable only in the *next step* when queries come from $$D$$.)
> 3. run and output $$D^{O\_{i,j,t}(\cdot)}(1^n)$$, that is running $$D$$ on input $$1^n$$ 
>    when providing $$D$$ with oracle queries to $$O\_{i,j,t}$$
>
> It remains to calculate the probabilities, namely, 
> given (AC), $$D'$$ distinguishes $$g(x)$$ from uniformly sampled string w.p. $$\ge \frac{1}{nT(n)p(n)}$$,
> a contradiction.
> The calculation is almost identical to [the proof of PRG expansion](#lemma-expansion-of-a-prg) and left as an exercise.

Secure Encryption Scheme
------------------------

Perfect secrecy considers that the adversary gets the ciphertext *only* (but nothing else).
However, there are other natural adversarial models in practical scenarios.

- Known plaintext attack: The adversary may get to see pairs of form $$(m_0, \Enc_k(m_0)) ...$$
- Chosen plain text, CPA: 
  The adversary gets access to an *encryption oracle* before and after selecting messages.
- Chosen ciphertext attack, CCA1:
  The adversary has access to an encryption oracle and to a decryption oracle *before*
  selecting the messages. ["lunch-time attack", Naor and Young]
- Chosen ciphertext attack, CCA2:
  This is just like a CCA1 attack except that the adversary also has access to 
  decryption oracle *after* selecting the messages. 
  It is not allowed to decrypt the challenge ciphertext however. [See Rackoff and Simon, Crypto 1991.](https://link.springer.com/chapter/10.1007/3-540-46766-1_35)

We formalize CPA-security next (but leave CCA1/CCA2 later in authentication).

#### **Definition:** Chose-Plaintext-Attack Encryption (CPA)

{: .defn}
> Let $$\Pi = (\Gen, \Enc, \Dec)$$ be an encryption scheme.
> For any NUPPT adversary $$A$$, for any $$n\in\N, b\in\bit$$, 
> define the experiment $$\Expr_b^{\Pi, A}(1^n)$$ to be:
> 
> {: .defn}
>> Experiment $$\Expr_b^{\Pi, A}(1^n)$$:
>> 
>> 1. $$k \gets \Gen(1^n)$$
>> 2. $$(m_0, m_1, \state) \gets A^{\Enc_k(\cdot)}(1^n)$$
>> 3. $$c \gets \Enc_k(m_b)$$
>> 4. Output $$A^{\Enc_k(\cdot)}(c, \state)$$
> 
> Then we say $$\Pi$$ is CPA secure if for all NUPPT $$A$$,
> 
> $$
> \left\{\Expr_0^{\Pi,A}(1^n)\right\}_n \approx
> \left\{\Expr_1^{\Pi,A}(1^n)\right\}_n.
> $$

Note: the experiment $$\Expr$$ is often equivalently described as 
"the adversary $$A$$ interacts a challenger $$C$$, 
where $$C$$ performs all other steps that are not belong to $$A$$ 
(such as $$\Gen$$, $$\Enc$$, and answering the queries to $$\Enc_k(\cdot)$$)".

Compared to Shannon/perfect secrecy, what are the differences?
- comp. bounded
- orcale before
- orcale after
- choose $$m$$

Suppose that we have a secure encryption even without CPA oracle but the key is shorter than the message.
Can we get a PRG/PRF? Can we get a OWF?

#### **Theorem:** CPA-Secure Encryption from PRF

{: .theorem}
> Let $$\PRF = \set{f_s : \bit^{|s|} \to \bit^{|s|}}_{s\in\bit^\ast}$$ be a family of PRFs.
> Then the following $$(\Gen, \Enc, \Dec)$$ is a CPA-secure encryption scheme.
> 
> - $$\Gen(1^n)$$: sample and output $$k \gets \bit^n$$.
> - $$\Enc_k(m)$$: given input $$m \in \bit^n$$, sample $$r \gets \bit^n$$, and then output
>   
>   $$
>   c := m \oplus f_k(r) ~\|~ r.
>   $$
>   
> - $$\Dec_k(c)$$: given input $$c = c' \| r' \in \bit^{2n}$$, output 
> 
>   $$
>   m := c' \oplus f_k(r').
>   $$

The correctness and efficiency of the construction follows from PRF directly.
It remains to prove CPA security.

{: .proof}
> To show $$\Expr_0$$ and $$\Expr_1$$ are comp. ind., we define hybrid experiments $$H_0, H_1$$ as follows.
> 
> {: .defn}
>> Hybrid $$H_b^{A}(1^n)$$:
>> 
>> 1. $$F \gets \RF_n$$, and then let $$O_F$$ to be the following oracle:
>>    
>>    $$
>>    O_F(x) := x \oplus F(r) \| r,
>>    $$
>>    
>>    where $$r \gets \bit^n$$ is sampled uniformaly.
>> 2. $$(m_0, m_1, \state) \gets A^{O_F(\cdot)}(1^n)$$
>> 3. $$r \gets \bit^n, c \gets m_b\oplus F(r) \| r$$
>> 4. Output $$A^{O_F(\cdot)}(c, \state)$$
> 
> By oracle indistinguishability of $$\PRF$$ and $$\RF$$ and closure under efficient operations, 
> we have 
> $$\set{\Expr_0^{\Pi, A}(1^n)}_n \approx \set{H_0^{A}(1^n)}_n$$ and
> $$\set{\Expr_1^{\Pi, A}(1^n)}_n \approx \set{H_1^{A}(1^n)}_n$$.
> (Notice that $$\PRF$$ and $$\RF$$ are oracle ind., but $$\Expr$$ and $$H$$ are comp. ind. of strings.)
> 
> Hence, it suffices to prove that the ensembles $$H_0$$ and $$H_1$$ are ind.
> They seem to be indentically distributed (as in OTP).
> However, there is a difference: $$A$$ gets oracle accesses to $$O_F$$ 
> (before and after choosing $$m_b$$), and $$O_F$$ could sample the same $$r$$ in the cipher $$c$$
> and in another oracle accesses.
> Fortunately, hitting the same $$r$$ twice in polynomial time happens with negligible probability.
> 
> We formally prove $$\set{H_0^{A}(1^n)}_n \approx \set{H_1^{A}(1^n)}_n$$ next.
> Define $$R$$ to be the set 
> 
> $$
> R := \set{r \in \bit^n : r \text{ is sampled when } A^{O_F(\cdot)}},
> $$
> 
> and let $$r$$ be the random variable sampled for the cipher $$c$$.
> We want to show that $$|\Pr[H_0^A(1^n)=1] - \Pr[H_0^A(1^n)=1]|$$ is negligible for all NUPPT $$A$$.
> Let $$H_0$$ and $$H_1$$ be the events for short.
> 
> $$
> \begin{align*}
> \Pr[H_0]
> & = \Pr[H_0 \cap r \in R] + \Pr[H_0 \cap r \notin R] \\
> & \le \Pr[r \in R] + \Pr[H_0 | r \notin R] \cdot \Pr[r \notin R] \\
> & = \gamma + \Pr[H_0 | r \notin R] \cdot (1 - \gamma),
> \end{align*}
> $$
> 
> where 
> $$\gamma := |R| / 2^n$$.
> We also have $$\Pr[H_0 | r \notin R] = \Pr[H_1 | r \notin R]$$,
> thus
> 
> $$
> \begin{align*}
> \Pr[H_0]
> & \le \gamma + \Pr[H_1 | r \notin R] \cdot (1 - \gamma)\\
> & = \gamma + \Pr[H_1 \cap r \notin R]\\
> & \le \gamma + \Pr[H_1].
> \end{align*}
> $$
> 
> Given that $$|R|$$ is polynomial in $$n$$ for any NUPPT $$A$$, 
> it follows that $$\gamma$$ is negligible in $$n$$, which concludes the proof.

Notice that we could have constructed an efficient CPA-secure encryption from PRG, 
but using a PRF significantly simplified the construction and the proof.

