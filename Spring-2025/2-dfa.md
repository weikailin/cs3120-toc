---
layout: page
title: "Module 3: Finite Automata"
nav_order: 12
nav_exclude: false
---

{: .announce-title}
> Class 16: From Regular Expressions to NFA to DFA
> 
> We introduced a generalization of DFA, called nondeterministic finite automata or NFA. Using the idea of "parallel universe," we defined NFA and its evaluation. Then, using NFA as an intermediate step, we showed how to construct NFA from any regular expression and how to construct DFA from any NFA. This completes the proof of DFA-Comp = Reg-Fun. We skipped some steps and details (such as concatenating two NFAs), but the big idea is working with nondeterminism. 
> 
> Slides are [here](assets/pdf/cs3120-class16-ink.pdf). PS7 is coming soon.
> 
> Mar 20, 2025

{: .announce-title}
> Class 15: From DFA to Regular Expressions
> 
> We showed that for every DFA there is a regular expression such that matches the same strings. Mikhail pointed out a bug in my slides and also showed a fix. In the textbook, [Section 6.4.2](https://introtcs.org/public/lec_05_infinite.html#regdfaequivsec) shows the same proof without my bug (notice that $$F^t_{v,w}$$ includes strings that may go through $$v$$ or $$w$$). Slides are [here](assets/pdf/cs3120-class15-ink.pdf).
> 
> Mar 18, 2025

{: .announce-title}
> Class 14: Limitations of Regular Expressions
> 
> We proved some functions (or languages) cannot be computed by regular expressions (and thus DFAs). Slides are [here](assets/pdf/cs3120-class14-ink.pdf).
> 
> Mar 4, 2025

{: .announce-title}
> Class 13: Evaluating Regular Expressions
> 
> We defined both the syntax and the evaluation (matching) of regular expressions. Then, we claimed that the complexity class of regular expressions is identical to the complexity class of DFAs. We haven't yet proved the claim, but it is a powerful theorem! The slides are [here](assets/pdf/cs3120-class13-ink.pdf).
> 
> PS6 is a programming assignment, posted on [Google Colab](https://colab.research.google.com/drive/1BpXmEzkzhle0YWTcWs3L9HOAUvF3Af16?usp=sharing).
> 
> Feb 27, 2025

{: .announce-title}
> Class 12: Deterministic Finite Automata and Regular Expressions
> 
> We went over the definition of DFA and its evaluation. Then, we introduced regular expressions. Both DFA and regular expressions are intesively used everyday in CS. The slides are [here](assets/pdf/cs3120-class12-ink.pdf).
> 
> PS5 is a written assignment, given in [PDF](assets/pdf/cs3120-ps5.pdf) and [Overleaf template](https://www.overleaf.com/read/wqcqvybwfqcy#3ef453).
> 
> Feb 20, 2025
