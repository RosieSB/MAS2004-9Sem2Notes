# 0. Introduction

These are the official lectures notes for [MAS2004 Analysis and Algebra](https://sites.google.com/sheffield.ac.uk/somasstudentintranet/programme-study-information/module-choice/somas-module-directory/somas-module-directory-202425/mas2004-analysis-and-algebra) Semester 2 and [MAS2009 Analysis](https://sites.google.com/sheffield.ac.uk/somasstudentintranet/programme-study-information/module-choice/somas-module-directory/somas-module-directory-202425/mas2009-analysis). 

The notes are produced with Jupyter Book, a package that uses Python and LaTeX to produce searchable maths notes that are [more accessible](https://abestshef.github.io/jupyter/Intro.html) than PDFs. 

If you have any issues using these notes, spot any errors, or would otherwise like help making best use of them, please get in touch by [emailing Rosie](mailto:r.j.shewellbrockway@sheffield.ac.uk).

## 0.1 Module overview

This semester, we will pick up where you left off in MAS107 last year, and look at some classical analysis topics. The main themes will be:

- *Functional Limits.* <br> How do we definite rigorously the notion of convergence to a limit for functions? This will underpin our work on continuity and differentiability.
- *Continuity.* <br> What does it mean to say that a function is continuous? What is the "right" definition, that will give us the theorems we want and and enable us to prove them rigorously?
- *Differentiability.* <br> What is the "right" definition of differentiability, and how is it related to that of continuity? We'll prove some beautiful theorems that connect the formal definition for the derivative to geometric properties of curves. %We'll also see how differentiability can be used to approximate functions by polynomials, using Taylor's theorem.
- *Sequences and series of functions.* <br> In MAS107, you studied sequences and series of real numbers. In [Chapter 4](chap:seq&seriesoffns), we focus on sequences and series in which each term is a function, rather than a number. This allows us to rigorously define important functions such as the exponential function, in terms of a uniformly convergent power series.
- *Integration.* <br> We give a formal treatment of the Riemann integral, in terms of areas under curves. We'll prove some more famous theorems, such as the fundamental theorem of calculus, which allows us to view integration as the opposite of differentiation.

## 0.2 Assessment

90\% of your grade will come from sitting an exam at the end of the module; the other 10\% will come from completing homework.

### Exam (90\%)

- MAS2009 Analysis: 1.5 hour written exam in January
- MAS2004 Analysis and Algebra: 2.5 hour written exam in May/June, on both Semester 1 and Semester 2 material

### Homework (10\%)

Each homework is "out of 1", in the sense that any reasonable attempt will receive 1 mark. So handing in a blank piece of paper might receive 0 marks, but anything that shows genuine effort will receive full credit.

Each piece of work will also receive constructive feedback that you can use to improve your understanding and your written mathematics.

(Note: MAS2004 has 10 homeworks over two semesters, so each homework counts for 1\% of the final grade. MAS2009 is only one semester long, so each homework is worth 2\%.)

This semester, there will be 4 pieces of written homework, and one midterm multiple choice quiz.

**Homework release schedule for Semester 1** <br>
| Task | Release date | Due date |
| :---: | :---: | :---: |
| Homework 1 | 11am Wednesday Week 2 | 5pm Tuesday Week 4 |
| Homework 2 | 11am Wednesday Week 4 | 5pm Tuesday Week 6 |
| Homework 3 | 11am Wednesday Week 6 | 5pm Tuesday Week 8 |
| Midterm online test | 11am Wednesday Week 7 | 5pm Tuesday Week 9 |
| Homework 4 | 11am Wednesday Week 9 | 5pm Tuesday Week 11 |

Written homework submission is via \href{https://students.sheffield.ac.uk/digital-learning/assessments/crowdmark}{Crowdmark}. A link for this will be provided with the release of each homework on Blackboard.

## 0.3. Recommended books

- **How to Think About Analysis, by Lara Alcock.**

This is a very readable and engaging book that aims to make learning analysis accessible for students are still meeting it for the first time. Rather than giving a formal treatment of the subject matter, which these notes will do, Lara's book is intended as a companion to a module such as this one, and prioritises the development of ideas and intuition over formalism.

Links: [Library](https://find.shef.ac.uk/permalink/f/15enftp/44SFD_ALMA_DS51268789000001441); [abebooks](https://www.abebooks.co.uk/9780198723530/Think-Analysis-Alcock-Lara-0198723539/plp); [goodreads](https://www.goodreads.com/book/show/24683010-how-to-think-about-analysis).

- **Understanding Analysis, by Stephen Abbott.**

This is a more traditional analysis textbook, as it is sometimes useful to see ideas presented in more than one way.

Links: [Library](https://find.shef.ac.uk/permalink/f/1lephdb/44SFD_ALMA_DS51360822510001441); [abebooks](-https://www.abebooks.co.uk/9781493950263/Understanding-Analysis-Stephen-Abbott-1493950266/plp); [goodreads](https://www.goodreads.com/book/show/26457662-understanding-analysis).



## 0.3 Frequently used symbols

| Symbol | Meaning |
| :---: | :---: |
| $\mathbb{N} := \{1,2,3,4,\ldots\}$ | the natural numbers |
| $\mathbb{N}_0 := \mathbb{N}\cup\{0\}$ | the non-negative integers |
| $\mathbb{Z} := \{\pm 1,\pm 2,\pm 3,\pm 4,...\}$ | the integers |
| $\mathbb{Q} := \left\{\frac{p}{q}:p\in\mathbb{Z},q\in\mathbb{N}\right\}$ | the rationals |
| $\mathbb{R}$ | the reals |
| $\subseteq$ | subset of |
| $\in$ | element of |
| $\notin$ | not an element of |
| $\forall$ | for all |
| $\exists$ | there exists |
| s.t. | such that |
| $f:X\to\mathbb{R}$ | a function $f$ from $X$ to $\mathbb{R}$ |
| $x\mapsto f(x)$ | $x$ maps to $f(x)$ |
| $\text{Dom}(f)$ | domain of $f$ |
| $\text{Range}(f)$ | range of $f$ |
| $[a,b]:=\{x\in\mathbb{R}:a\leq x\leq b\}$ | closed interval from $a$ to $b$ |
| $(a,b):=\{x\in\mathbb{R}:a<x<b\}$ | open interval from $a$ to $b$ |
| $\begin{array}{l} \mathbf{1}_A:\mathbb{R}\to\mathbb{R};\\ \mathbf{1}_A(x) := \left\{\begin{array}{lr} 1 & \text{ if }x\in A \\ 0 & \text{ if }x\notin A.\end{array}\right.\end{array}$ | indicator function for a set $A\subseteq{R}$ |
| $:=$ | defined to be equal to |
