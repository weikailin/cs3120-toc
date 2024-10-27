---
layout: page
title: Syllabus
nav_order: 0
nav_exclude: false
---

Syllabus
========

{: .highlight }
This syllabus is not yet finalized, and is subject to change until distributed on the first day of class.

<!-- 
This shall be similar to [https://github.com/uvatoc/uvatoc.github.io/blob/master/src/content/syllabus.md?plain=1] 
and [https://cs121.boazbarak.org/syllabus/]

Mark's is good but differ in coursework 
[https://markfloryan.github.io/dmt2/courselogistics/index.html]
 -->

## Overview

**Course Description:** The goal of this course is to understand the
fundamental limits on what can be efficiently computed in our
universe and other possible (or imaginary) universes. These limits
reveal deep and mysterious properties about information,
communication, and computing, as well as practical issues about how
to solve problems.

Two fundamental questions about any problem are:
 
 1. _Can it be solved using a machine of a certain type?_ (computability)
 2. _How much does it cost to solve it?_ (complexity)
 
We explore these questions by developing abstract models of computing
machines and reasoning about what they can and cannot compute
efficiently. A main goal of this course is for you to understand how
theoretical computer scientists reason about these questions, and
connecting that theory to practical questions about computing.  We
will also look at some applications in cryptography that take
advantage of problems being hard to solve, and what can be done when a
problem cannot be solved or is too expensive to solve.

**Course Objectives:** Students who complete the course will:

- Improve their [mathematical thinking skill and
  habits](https://medium.com/@jeremyjkun/habits-of-highly-mathematical-people-b719df12d15e),
  including thinking precisely about definitions, stating assumptions
  carefully, critically reading arguments, and being able to write
  convincingly.
- Be able to understand both finite and infinite formal models of computation and to reason about what they can and cannot compute.
- Understand both intuitively and formally what makes some problems either impossible or too expensive to solve with a computer, and what can be done in practice when an unsolvable or intractable problem is encountered.
- Reason formally about the cost of computation, and be able to prove useful bounds on the costs of solving problems, including showing that certain problems cannot be solved efficiently.
- Learn about some interesting aspects of theoretical computer science, and why understanding them matters even if you are only interested in building practical computing systems.

<a name="meetings"></a>
**Class Meetings:** The full class meetings of the course are
  scheduled for Tuesdays and Thursdays, 12:30--1:45pm in Rice Hall 130. 

**Another section of the same course:**
[Prof. Floryan also teaches this course on Spring 2025](https://louslist.org/sectiontip.php?Semester=1252&ClassNumber=16064). The two sections use different textbooks and proceed with slightly different topics although the overall goals are similar. The workload of this section shall be similar to the other section, but it is up to the staff's discretion.

## Preparation

**Official Prerequisites:** To enroll in cs3120, students must have
  completed CS 3100 (DSA2) or CS 4102 (Algorithms) with a grade of C-
  or better.

**Expected Background:** We expect students entering cs3120 to be
  comfortable using proof techniques from DMT1 including
  proof-by-contradiction, using quantifiers, and induction. From DSA2,
  we expect students to have good understanding of the most common
  asymptotic operators (including ``big-$$O$$'' and $$\Theta$$)
  and how to use them to talk about algorithm costs, reductions, and
  understanding recursive definitions and problem solving.

**Programming:** We also expect students to be able to read and write short
programs. We will use the Python programming language for some
assignments in the class. It is not necessary to have previous
experience with Python, but you should have enough programming
experience to be able to pick up what you need to read and write short
Python programs on your own. If you do not satisfy the prerequisites,
you should meet with one of the instructors to discuss whether you
should take the class. 

## Course Staff

**Instructor:** The course is taught by [Wei-Kai Lin](https://weikailin.github.io/) (wklin-course@virginia.edu).
  Feel free to contact either of us with any
  questions about the course, computer science, or anything else you
  think we can help with (but please read the section below on
  communications to determine if it would be better to post a message
  in [*Ed Discussion*](https://edstem.org/us/courses/68988/discussion/) before emailing us).

**Office Hours:** The full office hours schedule is TBD.
<!-- available on the [course calendar](/schedule). -->

<!-- 
   <center>
   <div class="row" style="display:flex; width: 100%; flex-wrap: wrap; justify-content: center; padding: 0.5rem;">
   <div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/dave.jpg"><br>
<a href="https://www.cs.virginia.edu/evans">David Evans</a></br></div>

   <div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/mohammad.png"><br>
<a href="https://www.cs.virginia.edu/~mohammad/">Mohammad Mahmoody</a><br>
  </div>
  </div>
</center>

**Teaching Assisants:** 

   <center>
   <div class="row" style="display:flex; width: 100%; flex-wrap: wrap; justify-content: center; padding: 0.5rem;">

   <div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/leah.jpeg"><br>
Leah Baetcke</br></div>

<div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/adam.jpg"><br>
Adam Bornemann</br></div>


   <div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/johnson.jpeg"><br>
Catherine Johnson</br></div>

</div>


   <div class="row" style="display:flex; width: 100%; flex-wrap: wrap; justify-content: center; padding: 0.5rem;">

   <div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/ratik.jpeg"><br>
Ratik Mathur</br></div>

<div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/mei.jpeg"><br>
<a href="https://zihanmei.uvacreate.virginia.edu/index-creative-1.html">
Zihan Mei
</a></br></div>

   <div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/morrissey.jpeg"><br>
Gillian Morrissey</br></div>

</div>

   <div class="row" style="display:flex; width: 100%; flex-wrap: wrap; justify-content: center; padding: 0.5rem;">

   <div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/sosnkowski.png"><br>
Alexander Sosnkowski</br></div>

<div class="column small-9 medium-4" style="text-align: center; padding: 0.5rem;"><img class="img-circle" width=85% src="/images/Claire_Yoon.png"><br>
Claire Yoon</br>
</div>
</center>
 -->


## Learning Materials
    
**Textbook:** Boaz Barak, [_Introduction to Theoretical Computer Science_](https://introtcs.org/public/index.html).

This is an open textbook that is freely available from
[https://introtcs.org](https://introtcs.org) under a Creative Commons
license. In addition to costing
[$271.95](https://web.archive.org/web/20171023211340/http://www.cengage.com/c/introduction-to-the-theory-of-computation-3e-sipser/9781133187790)
less than the traditional textbook for this class, this book takes a
modern and innovative approach to introducing theory of computation
which has several advantages (and a few disadvantages) of the
traditional approach (which we will discuss some in class, and be
happy to elaborate on during office hours). We plan to follow the
organization and material in the textbook fairly closely, but will
also cover some topics that are not included, and present some of the
material in ways that are different from how it is presented in the
book.

In addition to the course textbook, a few readings will be assigned
from other (freely available) sources.

<!-- 
**Video Lectures:** Materials will include links to relevant (and
  maybe some irrelevant) videos that cover the material students are
  expected to learn in the course. These videos are mostly edited
  recordings of lectures from previous versions of this course, but
  also will include some additional videos and other materials.
 -->

## Communication

We will primarily use the course website for posting course materials,
and use the course Ed Discussion for interactive communications.

**Course Website:** We will post all course materials at
  [https://uvatoc.github.io](https://uvatoc.github.io).

**Course Calendar:** We will keep course deadlines, office hours, and
  other events on a [public google
  calendar](https://calendar.google.com/calendar/u/2?cid=MjkyZThkZGIzNWZiZmIwNzExMDI0MzVkYjI4MjI1NDdlZjg5MWFiNjZkZmQ3ZWIwMGUwNzVlMGVhNTRhNDViZEBncm91cC5jYWxlbmRhci5nb29nbGUuY29t). Students
  are expected to subscribe to this calendar and be aware of deadlines that are posted there.

<!-- 
**Ed Discussion:** We will use the course discord server for most other
  course communications (you will receive information on joining the
  server by email). We expect students to receive messages we send to
  the `#general` channel as well as any direct messages we send to you
  on discord. 
  https://edstem.org/us/courses/68988/discussion/

If you have questions about course materials or assignments that will
be relevant to other students, please ask them in the `#general`
channel. This will get the fastest response, since all of the course
staff and students will see your question there and be able to respond
to it. We are also working to setup channel for asking questions
anonymously, and will provide more details on this soon.

Although Discord enables "realt ime" communication, you should not
expect instant answers to questions there, but should expect a
response within 24 hours.

**Email:** Managing email for a large class like this is difficult,
  and you should use the course discord for questions about the course
  content that are relevant to all students. If you have personal
  questions or things to discuss with the course staff, please do this
  by emailing us ([evans@virginia.edu, mohammad@virginia.edu](mailto:evans@virginia.edu,mahmoody@virginia.edu)). 
 -->

## Assignments and Exams

**Problem Sets.** Most learning in this course is done by working to
  solve problems on your own and in collaboration with others. We will
  have a problem set due most weeks in the course (typically on
  Fridays at 9:59pm).  See the course calendar for specific due
  dates. Each problem set will include specific directions for how to
  submit your solutions, and we expect students to read and follow
  these carefully. Unless otherwise stated in the problem sets, you are allowed to discuss
  problems with others, but we require that you write up your solutions
  by yourself and understand everything in it. We trust and expect
  students to follow these policies vigilantly.

**Pre-reading and reflection.** 
This course (and actually many courses) encourages reading and thinking indepedently. Hence, pre-reading and reflection is required.
For each week, we will post some pre-reading material of the coming week at least on Monday afternoon (ideally the previous Friday). The materials may be a textbook section or an online video, but they shall be short and readable in 10-20 minutes. You shall read / watch them and submit a short summary, one paragraph at most, before the Tuesday meeting. The summary shall be submitted online and before the class.
After the Thursday in class meeting, you will be asked to reflect on the material of the past week, and you shall write a short reflection.

We require you to submit a total of 15 pre-reading summaries and reflections (counted together) during the semester. 
The total is capped at 15. This is class participation, so you get points as long as your submission is relevant to the course.
Because the timing of pre-reading and reclection are essential, we disallow late submission (unless pre-approved by the instructor). 
Ideally, your summaries and reflections will become your big picture of this course. Hence, even after you have already all 15 points, you are still encouraged to submit weekly.

<!-- 
**Quizzes.** We will have regular quizzes due most Wednesday at 9:59pm
  (and posted the day before). These quizzes are designed to be quick
  ways to check your understanding, and will be (mostly) automatically
  graded. Quizzes will be done on your own, without using any resources.
 -->

**Exams.** We will have two exams in the course:

- **Midterm Exam**: In class on **Thursday, 6 March 2023**.
- **Final Exam**: **Friday, 2 May, 2:00pm - 5:00pm**.

No collaboration is permitted on the exams. Students may construct a
one-page (letter-size, two-sided) reference sheet for use during the
exam, but all other resources are forbidden (no internet, textbook,
other humans, magnification instruments, etc.). We will provide
detailed guidelines on what to expect on each exam, but you should
expect them to focus on the most important concepts covered in the
course with problems that you should be well perpared to solve if you
understand the problems from the problem sets well.

**Extensions and Late Submissions.** Extensions will be granted to
individual students on a case-by-case basis. We are more likely to
respond positively to an extension request if it is made well before
an assignment is due and provides a reasonable justification for the
extension. To request an extension, use this form:

   [TBD cs3120 Extension Request Form]
   
We are sympathetic to situations where a traumatic late event prevents
you from being able to complete an assignment, and appreciate you
bringing these to our attention even if the deadline has passed.

If you find that you will be unable to make one of the scheduled
exams, contact the course instructors immediately.

## Grading

We encourage students to spend your energy focusing on what you are
learning, instead of worrying about your grade. 

That said, we understand students are often stressed about grading and
understandably want to know how grades will be determined.  We aim to
grade in a way that is useful (provides students with accurate measure
of how well they understood what they should), motivating (encourages
the behaviors we prefer, including hard but not obsessive work), fair
(assigned higher grades to more deserving students), robust (arbitrary
small perturbations do not have a material impact on someone's grade),
and low stress (for both students and the course staff).

For this reason, we choose not to prescribe a singular mathematical
formula for quantitatively assigning letter grades but do provide a
formula that can be used to compute a _lower bound_ on the grade you
receive in the course:

| Item                      | Standard Weighting                          |
|---------------------------|---------------------------------------------|
|Pre-reading and reflection     | 15%     |
|Problem Sets (10 expected, the weight of individual assignment varies) | 50%     |
|Midterm Exam               | 15%     |
|Final Exam                 | 20%     |

<!-- 
<center>
<table class="grades" style="width:85%;">
<thead>
<tr>
<th width="60%">Item</th>
<th width="40%">Standard Weighting</th>
<tbody>
<tr><td>Problem Sets (10 expected)</td><td style="text-align:center;"><b>42%</b> (but with later assignments counting more)</td></tr>

<tr><td>Quizzes (9 expected, with one make-up)</td>
<td style="text-align:center;"><b>10%</b></td></tr>

<tr><td>Midterm Exam</td>
<td style="text-align:center;"><b>18%</b></td></br>

<tr><td>Final Exam</td>
<td style="text-align:center;"><b>30%</b></td>
</tbody>
</table>
</center>
 -->

With the exception of cases of academic dishonesty or inappropriate
behavior, we guarantee that you will a grade that is not below the
grade that would result from computing your score using the
percentages in the table, where your score for each item is the ratio
of the score you received to the target score for that item, and the
grading scale is based on the standard decades (e.g., 0.87 = B+, 0.9 =
A-, 0.93 = A).

This is a _minimum_ grade, though, and we generally want to assign a
grade that reflects the best possible interpretation of all you have
done during the semester. This means we consider your performance
throughout the course, and will examine grades using a variety of
different methods that weights different aspects differently and
rewards performance improvements, but also allows consistent
performance to make up for one slip-up.

An “A” grade means we are convinced that you can use the material in
this class to solve new problems and understand it well enough to
explain most concepts in the class. A “B” grade means we are convinced
that you understand the main ideas in this class well enough to be
well prepared for a follow-on course (i.e., one that has this as a
pre-requisite).

Although the material we cover is challenging, and the pace may seem
overwhelming at times, we are confident that all students who put
effort into this class and take good advantage of available help will
do well.

**Bonus Points.** We hope students will go beyond
the provided assignments and do other things to contribute to the
class as well as beyond. Hence, we give bonus points occasionally.
That includes (but not limited to) solving challenge problems in problem sets, 
reporting bugs in the course materials, and participating in class.
We will clearly make the bonus points in problems, but in some cases, 
it is up to the instructor's discretion.

## Honor Expectations

We believe strongly in the value of a community of trust, and expect
all of the students in this class to contribute to strengthening and
enhancing that community.

The course will be better for everyone if everyone can assume everyone
else is trustworthy. The course staff starts with the assumption that
all students at the university deserve to be trusted. 

To ensure that expectations are clear to everyone, all students are
required to read, understand, and sign the course pledge:
TBD
<!-- 
[https://uvatoc.github.io/pledge](https://uvatoc.github.io/pledge).
 -->

**Collaboration Policy:** We believe it is important for students to
learn by thinking about problems on their own, so it is expected that
each student studies the provided materials and attempts to solve the
problems on their own. After that, you are welcome to also discuss
problems on the problem sets with students and others.

Many problems in this course will be selected from problems used in
previous courses, as well as well known problems. The goal of these
problems is to lead students to develop understanding of the
underlying concepts by working through the problems themselves and in
discussions with others, and this goal would be defeated if you
instead use posted solutions to the problems (that includes generative AI such as ChatGPT). Other than using
solutions to the specific problems you are given, students are
encouraged to use any other resources they find helpful.
  
We aim to make the language describing the policy as clear
and unambiguous as possible, but if anything is ever unclear about
the stated policy for an assignment, please clarify with the course
staff. The penalty for policy violations will be considered on a
case-by-case basis, with a penalty commensurate the severity of the
offense.

## Additional Information

**Special Circumstances:** The University of Virginia strives to provide accessibility to all students. If you require an accommodation to fully access this course, please contact the Student Disability Access Center (SDAC) at (434) 243-5180 or `sdac@virginia.edu`. If you are unsure if you require an accommodation, or to learn more about their services, you may contact the SDAC at the number above or by visiting their website [https://studenthealth.virginia.edu/sdac](https://studenthealth.virginia.edu/sdac)

**Accommodations:** It is the University's long-standing policy and
  practice to reasonably accommodate students so that they do not
  experience an adverse academic consequence when serious personal
  issues conflict with academic requirements. Although University
  policy only recognizes religious accomodations, the course
  instructors believe they are many other valid reasons for
  accomdations that are at least as justifiable as ones for religious
  observance and consider family obligations, personal crises, and
  extraordinary opportunities to all be potentially valid reasons for
  accomodations.  Students who wish to request accommodations should
  submit their request to the instructor as far in
  advance as possible.

If you have questions or concerns about the University policy on
  academic accommodations for religious observance or religious
  beliefs, visit
  [https://eocr.virginia.edu/accommodations-religious-observance](https://eocr.virginia.edu/accommodations-religious-observance)
  or contact the University's Office for Equal Opportunity and Civil
  Rights (EOCR) at `UVAEOCR@virginia.edu` or 434-924-3200.

**Safe Environment:** The University of Virginia is dedicated to
  providing a safe and equitable learning environment for all
  students. To that end, it is vital that you know two values that we
  and the University hold as critically important:
 
  1. Power-based personal violence will not be tolerated. 
  2. Everyone has a responsibility to do their part to maintain a safe community on grounds (including in virtual environments).

If you or someone you know has been affected by power-based personal
violence, more information can be found on the UVA Sexual Violence
website that describes reporting options and resources available:
[https://www.virginia.edu/sexualviolence](https://www.virginia.edu/sexualviolence).
   
As your professors and as humans, know that we each care about you and
your well-being and stand ready to provide support and resources as we
can. As faculty members, we are responsible employees, which means
that we are required by University policy and federal law to report
what you tell us to the University's Title IX Coordinator. The Title
IX Coordinator's job is to ensure that the reporting student receives
the resources and support that they need, while also reviewing the
information presented to determine whether further action is necessary
to ensure survivor safety and the safety of the University
community. If you would rather keep this information confidential,
there are Confidential Employees you can talk to on Grounds (see
[https://eocr.virginia.edu/chart-confidential-resources](https://eocr.virginia.edu/chart-confidential-resources)). The
worst possible situation would be for you or your friend to remain
silent when there are so many here willing and able to help.

**Well-being:** If you are feeling overwhelmed, stressed, or isolated,
there are many individuals here who are ready and wanting to help. The
Student Health Center offers Counseling and Psychological Services
(CAPS) for all UVA students. Call 434-243-5150 (or 434-972-7004 for
after hours and weekend crisis assistance) to get started and schedule
an appointment. If you prefer to speak anonymously and confidentially
over the phone, Madison House provides a HELP Line at any hour of any
day: 434-295-8255.


<!-- 
 -->