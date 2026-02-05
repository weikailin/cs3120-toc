---
layout: home
title: CS3120 Theory of Computation (UVA)
nav_exclude: true
permalink: /:path/
seo:
  type: Course
  name: Theory of Computation
---


UVA CS 3120 Theory of Computation (Wei-Kai Lin)
----------------------------------------
This is the course website of CS 3120 (also called Discrete Mathematics and Theory 2), instructed by Prof. Lin. The meetings are [Tuesdays and Thursdays at **9:30 - 10:45pm** Spring 2026](https://hooslist.virginia.edu/ClassSchedule/ClassHistory?subject=CS&catalogNumber=3120) and in Olsson 120.

{: .highlight }
**Another section of the same course:**
Prof. Pettit also teaches this course in this Spring 2026. The two sections use **different textbooks** and proceed with slightly **different topics** although the overall goals are similar. The workload of this section shall be similar to the other section, but it is up to the staff's discretion.


## Recent Announcements

### Class 7: DFA to Regular Expressions
(Feb 5, 2026)

We applied Pumping Lemma to show a few languages are not regular (i.e., some problems and functions can not be computed using DFA).
Then, we proved that for every DFA, we can construct an equivalent regular expression. 
Slides are [here](assets/pdf/cs3120-class7-ink.pdf).
HW 3 is coming soon.

### Class 6: Regular Expressions vs DFA
(Feb 3, 2026)

We finished Midterm 0 (yay~)!
After that, we showed the powerful theorem, DFAs and Regular Expressions are equivalent, and its applications.
They are positive results, and we went on with negative results and Pumping Lemma.
Slides are [here](assets/pdf/cs3120-class6-ink.pdf).
Quiz 3 is posted on Gradescope.

### Class 5: Regular Expressions
(Jan 29, 2026)

We talked about the syntax and evaluation of regular expressions. Then, we stated the equivalence between regular expressions and finite automata. We also reviewed the materials of Midterm 0 briefly.
Slides are [here](assets/pdf/cs3120-class5-ink.pdf).
Homework 2 is coming soon.

### Class 4: Cantor's Theorem, Finite Automata
(Jan 27, 2026)

We proved Cantor's Theorem, and then we introduced finite automata as the beginning of the next module.
Slides are [here](assets/pdf/cs3120-class4-ink.pdf).
Quiz 2 is posted on Gradescope.

### Class 3: Infinity
(Jan 22, 2026)

We defined Infinity, countable, and showed there are uncountable sets.
Slides are [here](assets/pdf/cs3120-class3-ink.pdf).
Quiz 1 is posted on Gradescope.
[Homework 1 is posted](assets/pdf/cs3120-hw1.pdf).

We skipped a proof of the following theorem. Here is it.

#### Theorem: If a set $$S$$ is countably infinite, then $$\card{S} = \card{\N}$$.

1. We will prove that $$\card{S} \le \card{\N}$$ and $$\card{S} \ge \card{\N}$$ holds, which implies $$\card{S} = \card{\N}$$ by (Cantor-)Schröder–Bernstein Theorem.
2. We have $$\card{S} \le \card{\N}$$ by $$S$$ is countable.
3. It remains to prove that $$\card{S} \ge \card{\N}$$. That is, we want to show a surjective function $$g: S \to \N$$. Such $$g$$ is constructed (or described) below. 
    1. By $$S$$ is Dedekind infinite, there exists a strict subset $$T\subsetneq S$$ such that $$\card{S} = \card{T}$$.
    6. By $$\card{S} = \card{T}$$, there is a bijection $$f: S \to T$$.
    7. Let $$U_0 = S$$, and let $$U_i = \{f(x) \mid x \in U_{i-1} \}$$ for all natural numbers $$i > 0$$. That is, $$U_i$$ is the set of elements that are mapped from $$U_{i-1}$$ by $$f$$. Note that $$U_1 = T$$.
    5. By strict subset, there exists $$a_0 \in T, a_0 \notin S$$. 
    8. Let $$a_i = f(a_{i-1})$$ for all natural numbers $$i > 0$$. We have $$a_i \in U_i$$ for all $$i \in \N$$ by definition of $$U_i$$ and $$a_i$$ (an induction is needed to be strictly formal).
    9. Let $$g$$ to be the partial function that maps $$a_i$$ to $$i$$ (there may exists an element in $$S$$ that is not mapped to anything, so it is partial). This is the construction of $$g$$
4. It remains to argue $$g$$ is surjective.
5. Clearly, each $$i\in\N$$ is mapped from (or receives) exactly one element in $$S$$.
6. We want to argue that $$a_i \neq a_j$$ for all $$i\neq j$$, which implies that each element in $$S$$ is mapped to at most one natural number and that $$g$$ is surjective.
7. We claim that $$a_i \notin U_{i+1}$$ for all $$i \in \N$$.
8. Because $$U_{j+1}\subseteq U_j$$ for all $$j\in\N$$, the claim implies $$a_i \notin U_j$$ for all $$i < j$$.
9. Given that $$a_j \in U_j$$, the claim implies $$a_i \neq a_j$$ for all $$i < j$$. 
    1. To prove the claim, assume for contradiction, there exists $$a_i \in U_{i+1}$$ for some $$i$$ (for some $$S$$, bijection $$f$$, element $$a_0$$). Let $$k$$ be the smallest natural number satisfying such Property.
    2. We have $$k > 0$$ as $$a_0 \notin U_1$$.
    3. Since $$f$$ is a bijection, we have a unique $$f^{-1}(a_k) = a_{k-1}$$. 
    4. Since $$f$$ is a bijection and $$f$$ maps from $$U_k$$ to $$U_{k+1}$$, $$f$$ is also a bijection between $$U_k$$ and $$U_{k+1}$$.
    5. By $$a_k \in U_{k+1}$$ and $$f$$ is bijective between $$U_k$$ and $$U_{k+1}$$, we have $$f^{-1}(a_k) \in U_k$$.
    6. But $$f^{-1}(a_k) = a_{k-1} \in U_k$$ means $$k-1$$ also satisfy the Property, contradicting that $k$ is the smallest. This concludes the claim and the theorem.

### Class 2: Cardinality
(Jan 20, 2026)

We talked about why study theory, infinite binary strings, and cardinality. 
Slides are [here](assets/pdf/cs3120-class2-ink.pdf).
Quiz 1 is coming in 24 hours.

### Class 1: Definitions
(Jan 15, 2026)

We talked about constructive definitions, natural numbers, binary strings, and sets. 
Slides are [here](assets/pdf/cs3120-class1-ink.pdf).
Homework 0 is [posted](

https://colab.research.google.com/drive/1F4idQXXtNHKJ1MWNKlg4U66Z2o1YgK1f?usp=sharing), which shall be submitted to Gradescope.

### Class 0: Goals and grading
(Jan 13, 2026)

We talked about Karatsuba's multiplication and grading.
Slides are [here](assets/pdf/cs3120-class0-ink.pdf). Quiz 0 is posted on Gradescope.


<!-- {: .announce-title}
> Class 27: Reductions, Review, and Gödel's Incompleteness
> 
> We reviewed the template of reductions by showing the reduction from 3SAT to Maximum Independent Set. We also birefly reviewed the big ideas in this course: counting, reductions, code as data. We wrapped up this course with Gödel's Incompleteness Theorem.
> 
> Slides are [here](assets/pdf/cs3120-class27-ink.pdf).
> 
> Apr 29, 2025

{: .announce-title}
> Class 26: Cook-Levin Theorem
> 
> We proved Cook-Levin Theorem by reducing from any problem in NP to CircuitSAT and by recuding from CircuitSAT to 3SAT. We also talked about some other NP-Complete problems and about the need for P $$\neq$$ NP in cryptography.
> 
> Thanks to Abhishek for pointing out a bug in my slides: BinPacking is easy and computable in polynomial time when there is only one bin. However, for two or more bins of the same size, it becomes NP-Complete to compute whether we can pack all items into the bins. See [this note](https://ac.informatik.uni-freiburg.de/lak_teaching/ws11_12/combopt/notes/bin_packing.pdf) for the definition and reduction.
> 
> Slides are [here](assets/pdf/cs3120-class26-ink.pdf).
> 
> Apr 24, 2025

{: .announce-title}
> Class 25: P vs NP vs EXP, NP-Complete
> 
> We compared class NP to the two classes P and EXP, with a brief definition of class co-NP. We then defined the class of NP-Complete (functions), a first step when human got to understand P vs NP. In the coming Thursday, we will prove Cook-Levin Theorem, which gives the first NP-Complete problem.
> 
> Slides are [here](assets/pdf/cs3120-class25-ink.pdf).
> 
> Apr 22, 2025

{: .announce-title}
> Class 24: Reductions, and class NP
> 
> We introduced some hard problems, including LonggestPath, CircuitSAT, and 3-SAT. Then, we defined the complexity class NP, and we showed that the mentioned hard problems are in NP. The class NP is a big idea in CS. Instead of grouping problems by their computation time, NP groups problems by their **verification time**. At very high level, problems in NP are those "easy to verify" when the instance holds. That includes many problems we know of, and the concept opened many areas in CS.  
> 
> Slides are [here](assets/pdf/cs3120-class24-ink.pdf).
> 
> Mikhail asked about the *complement* of problems in NP. That is defined as the class co-NP: 
> $$
> co-NP = \{F : F \text{ is a Boolean function and } NOT(F(x)) \in NP \}.
> $$
> We have $$P \subseteq NP$$ and $$P \subseteq co-NP$$, but it is a [long open question](https://en.wikipedia.org/wiki/Co-NP) whether $$NP = co-NP$$. 
> 
> Apr 17, 2025

{: .announce-title}
> Class 23: Complexity, and class P
> 
> We introduced time complexity of Turing machines, and then we defined the class of polynomial-time computable functions.
> Slides are [here](assets/pdf/cs3120-class23-ink.pdf).
> 
> [Problem Set 10](assets/pdf/cs3120-ps10.pdf) is now released. You can find the Overlead link in the PDF.
> 
> Apr 15, 2025

## Older announcements:
- [Module 1: Introduction and Math Background](0-intro.md)
- [Module 2: Boolean Circuits](1-circuit.md)
- [Module 3: Finite Automata](2-dfa.md)
- [Module 4: Computability](3-tm.md)
 -->
### Tentative syllabus posted
(Jan 9, 2026)

Please take a look at [the syllabus](syllabus.md) although it could change later.


