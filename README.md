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
This is the course website of CS 3120 (also called Discrete Mathematics and Theory 2), instructed by Prof. Lin. The meetings are [Tuesdays and Thursdays at **12:30 - 1:45pm** Spring 2025](https://louslist.org/sectiontip.php?Semester=1252&ClassNumber=19555) and in Rice Hall 130. (Clarification: the course of Prof. Floryan is [different](https://louslist.org/sectiontip.php?Semester=1252&ClassNumber=16064).)

{: .highlight }
**Another section of the same course:**
[Prof. Floryan also teaches this course in Spring 2025](https://louslist.org/sectiontip.php?Semester=1252&ClassNumber=16064). The two sections use different textbooks and proceed with slightly different topics although the overall goals are similar. The workload of this section shall be similar to the other section, but it is up to the staff's discretion.


## Recent Announcements

{: .announce-title}
> Class 24: Reductions, and class NP
> 
> We introduced some hard problems, including LonggestPath, CircuitSAT, and 3-SAT. Then, we defined the complexity class NP, and we showed that the mentioned hard problems are in NP. The class NP is a big idea in CS. Instead of grouping problems by their computation time, NP groups problems by their **verification time**. At very high level, problems in NP are those "easy to verify" when the instance holds. That includes many problems we know of, and the concept opened many areas in CS.  
> 
> Slides are [here](assets/pdf/cs3120-class24-ink.pdf).
> 
> Mikhail asked the complement of problems in NP. That is defined as the class co-NP: 
> $$
> co-NP = \{F : F \text{ is a Boolean function and } NOT(F(x)) \in NP \}.
> $$
> We have $$P \subset NP$$ and $$P \subset co-NP$$, but it is a [long open question](https://en.wikipedia.org/wiki/Co-NP) whether $$NP = co-NP$$. 
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

{: .announce-title}
> Class 22: Rice's Theorem
> 
> We recapped reductions. Then, we discussed semantic properties of Turing machines and introduced Rice's Theorem. It extremely powerful and shows many uncomputable functions at once! Slides are [here](assets/pdf/cs3120-class22-ink.pdf).
> 
> Apr 10, 2025

{: .announce-title}
> Class 21: Kolmogorov Complexity
> 
> Today, Alice showed a metric of information in a string: Kolmogorov complexity. It is everywhere whenever we human write anything, but it is a big idea that built on the concept of computation. Alice's slides is [here](assets/pdf/cs3120-class21.pdf). My slides will be posted on Thursday together with other slides.  
> 
> Apr 8, 2025

{: .announce-title}
> Class 20: Halting problem, and reduction
> 
> We showed that Halting Problem is uncomputable through a reduction from $$ACCEPTS$$. Also, we discussed Church-Turing Thesis. Slides are [here](assets/pdf/cs3120-class20-ink.pdf).
> 
> Apr 3, 2025
> 
> Update (Apr 3): [Problem Set 9](assets/pdf/cs3120-ps9.pdf) is now released. You can find the Overlead link in the PDF.

{: .announce-title}
> Class 19: Universal Turing Machines and Uncomputability
> 
> We showed that there are universal Turing machines. Using universal Turing machines, we proved that the boolean function $$ACCEPTS$$ is uncomputable. Slides are [here](assets/pdf/cs3120-class19-ink.pdf).
> 
> Apr 1, 2025

{: .announce-title}
> Class 18: Computability
> 
> We discussed more about some potential variants of Turing machines and how Turing addressed them. We then informally introduced the "computable numbers" and more generally computable functions. Slides are [here](assets/pdf/cs3120-class18-ink.pdf).
> 
> Mar 27, 2025
> 
> Update (Mar 27): [Problem Set 8](assets/pdf/cs3120-ps8.pdf) is now released. You can find the Overlead link in the PDF.

{: .announce-title}
> Class 17: Turing Machines
> 
> We concluded DFAs and regular expressions with the Cloudflare outage. With that, we formally introduced Turing machines. Historically, there were multiple models of computation, and Alan Turing showed that they are all equivalent to Turing machines. 
> 
> Slides are [here](assets/pdf/cs3120-class17-ink.pdf). PS7 is now posted and due next Tuesday.
> 
> Mar 25, 2025

## Older announcements:
- [Module 1: Introduction and Math Background](0-intro.md)
- [Module 2: Boolean Circuits](1-circuit.md)

{: .announce-title}
> Tentative syllabus posted
> 
> The enrollment is starting soon. Please take a look at [the syllabus](syllabus.md) if you have any questions (and be forgiving if something changes later).
> 
> Oct 27, 2024.



<!-- 
Welcome to CS 6222, Cryptography!
----------------------------------------

Cryptographic primitives are applied almost everywhere on the network, for instance, encryption and authentication are necessary. In this course, we will start from the theoretic foundations that consolidates our belief in cryptography, and then we will visit some essential protocols as well as recent advances in cryptography. A major theme of this course is "provable security," that is, to define the desired security and then to rigorously prove the security is achieved. Hence, students are expected to be familiar with algorithms and mathematical proofs.

Please send me an email if you have questions.

Prerequisites
---------
[CS 3120 Discrete Mathematics and Theory 2](https://uvatoc.github.io/) or equivalent course is necessary.
Also, Probability (APMA 3100) is good-to-have.

This course requires DMT2 (CS3120) because it heavily relies on the concepts such as reductions, decision problems, NP-complete and computation models like Turing machines, and some ideas from complexity. The concepts are covered in DMT2 (and sometimes partly in DSA2, CS3100). Because they are required in both BSCS and BACS, they are used directly as preliminary knowledge in the course.
Also, reading and writing formal math proofs is necessary.

Classroom
---------

**Days and Times:** Tueday/Thursday 11:00am -- 12:15pm (2024)

**Location:** Rice Hall 340 ![UVA Engineering](assets/images/uva-eng.png){:style="vertical-align: middle;"}

Instructor and TA Information
------------------------------

**Instructor:** Wei-Kai Lin [(audio)](https://www.name-coach.com/wei-kai-lin-4568fe92-7831-4780-a68c-361f76dee197), email: wklin-course (at virginia dot edu)

Office Hours and TA
------------

See [Canvas](https://canvas.its.virginia.edu).

Course Work
--------------

The course work consist of the following.

- (50%) Written homework 
- (15%) Scribe notes (this weight may change according to number of students)
- (20%) Final project (presentation and report)
- (15%) Final exam, written
- (10%, bonus) Quizzes and other

The final grade will follow the [CS Department guidelines](https://uvacsadvising.org/policies.html#cs-department-grading-guidelines).

We will use the [Canvas](https://canvas.its.virginia.edu) website to manage homework, exam, and grades. Please also use the discuss page on Canvas if you have course related questions.

### Homework

The homework submissions shall be PDF and typeset in Tex/Latex (template will be provided).

Every student shall submit homework individually. You are free to discuss with other students in this class, but in that case, you shall add an **Acknowledgement** paragraph explicitly. Similarly, you are allowed to make use of published material as long as you cite it properly with a **References** section. In any case, it is a violation if you copy text directly, or if you are unable to explain your solution orally.

Specifically, the purpose of homework (and this course) is to compare and understand security definitions and to rigorously prove or argue the security. Hence, when working on homework, the following approaches are listed from **the more preferred** to **less preferred**:

1. Using in-class materials, including lecture notes, textbook sections that are covered, or office hours.
2. Discussing with students in this class (must acknowledge it)
3. Referring to other published literature, including textbook sections that are not yet covered (must reference it)
4. Using ready-made solutions, including asking other people, using generative AI, finding solutions in previous courses in any school (let's try to avoid this)

For example, you wrote your own answer, then you searched for the problem and and then edited your answer. In this case, you should reference (cite) or acknowledge it. In general, internalize your answer and no direct copying, so that you can explain it orally. Edit history (such as Overleaf or Github) is recommended.

There may be additional rules for some homework questions.

### Scribe notes

We will ask students to scribe lecture notes and typeset in Latex (template will be provided). The notes will be posted publicly on this website. There will be roughly 22 lectures, and for each lecture we will ask at most 2 students to scribe collaborately. The notes shall be submitted in 1 lecture week (that is before the next two lectures). Depending on the number of studenets, we may increase the weight of scribing and reduce the weight of final exam.

### Final exam

The time is the same as [UVA schedule](https://registrar.virginia.edu/exam-schedule-fall-2024): Monday, December 16, 2024 9:00AM-12:00PM
(Potential alternative: Monday, December 9)

This will be in person and written one.
No collaboration is permitted on the exams. 
Students may construct a one-page (letter-size, two-sided) reference sheet for use 
during the exam, but all other resources are forbidden (no internet, textbook, other humans, magnification instruments, etc.).

### Final Project

The final project is to read research papers in the area of cryptography, to write a 2-page summary, and then to present the topic in class. In addition to summary, you are encouraged to ask novel questions or to propose novel solutions.

The project is by a group of at most two. Both students in the group get the same grade. Each group is required to submit the authors and the research topic in an 1-page proposal (4%) at mid-semester. The summary (8%) is due at the end of the semester, and the last two to five lectures will be the presentation (8%).

### Honor System

The goal of this course is to define and prove security. Ideally, all your course works shall be based on the materials given in the classroom and references. You are encouraged to read other materials, but searching for **ready-made solutions is discouraged** because it hurts the goal. Similarly, please try not to ask for solution from people out of this class, and please try not to use generative AI.

It is a violation if any of the following cases happens:
 - You copied text directly (from any source).
 - You used any material or discussion without acknowledgement or citation.
 - You are unable to explain your work orally.

Everyone is required to follow the [Honor Codes of UVA](https://honor.virginia.edu/academic-fraud) and avoid [plagiarism](https://honor.virginia.edu/plagiarism-supplement). You are recommended to use a version control system, such as Overleaf or git, so that your thought process justifies the authenticity.

Please also read [detailed policies](uva_support.md) on the use of AI, accommodations, and supports.

Course Outline
--------------

Textbooks:
- Rafael Pass and abhi shelat.
  A Course in Cryptography. 
  \[Ps\] for short.

  Available here:
  [http://www.cs.cornell.edu/courses/cs4830/2010fa/lecnotes.pdf](http://www.cs.cornell.edu/courses/cs4830/2010fa/lecnotes.pdf)


- Jonathan Katz and Yehuda Lindell.
  Introduction to Modern Cryptography.
  \[KL\] for short.

  Online access in UVA library:
  [https://search.lib.virginia.edu/sources/uva_library/items/u10203454](https://search.lib.virginia.edu/sources/uva_library/items/u10203454)

Lecture notes will be provided on this website, so the textbooks are optional.

### Syllabus (tentative)

In the first half, we focus on the necessary properties behind cryptographic primitives,
including computational indistinguishability, pseudo-randomness, and one-wayness,
and we show the direct implications such as encryption and authentication.
In the second half, we move on to more applications as well as recent progresses in cryptography.
The tentative topics are listed below.

1.  Introduction and scope. Logistics. Preliminaries.  
    Match-making. Security definition.
2.  Shannon's definition. One-time pads. Limitation of information theoretic approach.
3.  Efficient computations and efficient adversaries
4.  Private-key encryption, computational indistinguishability 
5.  Pseudo-random generators (PRG)
6.  CPA-secure encryption, pseudo-random functions (PRF)
8.  One-way functions (OWF).
10. Prime Number Theorem. Factoring problem.
11. OWF from factoring assumption. 
9.  Strong OWF from weak OWF (hardness amplification). Universal OWF.
12. Hard-core predicates. PRG from hard-core bits.
13. PRG from any OWF. 
7.  Message authentication codes (MAC). 
14. Digital signature. Identification. 
15. Collision-resistant hash functions. Birthday attack. 
16. Zero-Knowledge proofs, commitment. 
17. Oblivious RAM. 
18. Public-key encryption. Trapdoor permutations.
19. Homomorphic encryption, Fully homomorphic encryption (FHE). 
20. Garbled circuits. Oblivious transfer (OT). Secure two-party computation. 
21. Secret-sharing. Secure multi-party computation. 
22. Private information retrieval (PIR).

Additional Course Material
---------------

\[CS6222 Introduction to Cryptography (UVA, Fall 2023)\]
[https://weikailin.github.io/cs6222-fa23/](https://weikailin.github.io/cs6222-fa23/)

\[Barak\]
An Intensive Introduction to Cryptography.
[https://intensecrypto.org/public/index.html](https://intensecrypto.org/public/index.html)

\[Goldreich\]  
The Foundations of Cryptography.
[https://www.wisdom.weizmann.ac.il/~oded/foc-book.html](https://www.wisdom.weizmann.ac.il/~oded/foc-book.html).  
[online access in UVA library](https://search.lib.virginia.edu/sources/uva_library/items/u8631726).

\[Vadhan\]
Pseudorandomness.
[https://people.seas.harvard.edu/~salil/pseudorandomness/pseudorandomness-published-Dec12.pdf](https://people.seas.harvard.edu/~salil/pseudorandomness/pseudorandomness-published-Dec12.pdf)

Mike Rosulek.
The Joy of Cryptography. 
[https://joyofcryptography.com/](https://joyofcryptography.com/)

David Evans, Vladimir Kolesnikov and Mike Rosulek.
A Pragmatic Introduction to Secure Multi-Party Computation.
[https://securecomputation.org/main/](https://securecomputation.org/main/) -->