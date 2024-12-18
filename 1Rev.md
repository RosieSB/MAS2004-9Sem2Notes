---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Revision of MAS107

This module will build directly on the work you have done in MAS107. In particular, it is important that you can recall definitions and results about sequences of real numbers, as we will be using them in many of the proofs and problems to come. When reviewing lecture notes before and after classes, it may help to have a copy of your MAS107 notes to hand, so that you can refresh any details that you need.

## Sequences and convergence

````{prf:definition} Convergence
:label: seqconv
Recall that a sequence $(x_n)$ is said to *converge* to limit $l\in\mathbb{R}$ if for all $\varepsilon>0$ there exists a number $N\in\mathbb{N}$ such that

$$
|x_n-l| < \varepsilon \hspace{2em} \text{ for all } n\geq N.
$$

In other words, for any given tolerance $\varepsilon$, the numbers $x_n$ will eventually lie within $\varepsilon$ of $l$. We write $x_n\rightarrow l$ as $n\rightarrow\infty$.
````

````{prf:definition} Cauchy sequence
:label: Cauchy
A sequence $(x_n)$ is *Cauchy* if for all $\varepsilon>0$ there is an $N\in\mathbb{N}$ such that 

$$
|x_n-x_m|<\varepsilon \hspace{2em} \text{ for all } m,n\geq N.
$$


A sequence being convergent means its terms are getting "closer and closer" to its limit $l$. Being Cauchy says that the terms are getting "closer and closer" to one another. In fact, being convergent is strictly stronger than being Cauchy: if $A\subseteq\mathbb{R}$ and $(x_n)$ is a sequence in $A$, then

$$
(x_n) \text{ converges to a limit $l\in A$ } \hspace{1em} \mathbb{R}ightarrow \hspace{1em} (x_n) \text{ is a Cauchy sequence}.
$$

The converse statement doesn't hold: $(x_n)$ being Cauchy does not imply that it converges to a limit in $A$. For example, let $A:=(0,1)$ and $x_n=\frac{1}{n}$, for $n\in\mathbb{N}$. Then, *viewed as a sequence in* $A$, $(x_n)$ does not converge. However, if we instead view it as a sequence in $\mathbb{R}$, we know that $x_n\rightarrow 0$ as $n\rightarrow\infty$. Since $(x_n)$ converges as a sequence in $\mathbb{R}$, it must be a Cauchy sequence.

A set $A\subseteq\mathbb{R}$ is called *complete* if every Cauchy sequence in $A$ converges to a limit in $A$. Therefore, for complete sets, being Cauchy is equivalent to convergence. The set $\mathbb{Q}$ of all rational numbers is not complete, but the set $\mathbb{R}$ of all reals is.

In MAS107, you saw how $\mathbb{R}$ is constructed from $\mathbb{Q}$ by including the limits of all rational Cauchy sequences.

## Logic and quantifiers

Analysis, like all areas of pure mathematics, is interested in proving things carefully and rigorously. This requires technical arguments, and in order to communicate unambiguously, we will need to use formal language such as quantifiers.

There are two important quantifiers used by mathematicians:

- Universal quantifier: $\forall$, "for all"
- Existential quantifier: $\exists$ "there exists"

Understanding mathematical statements involving quantifiers takes continual practice. A key advantage of studying analysis is there will be plenty of opportunity for this.

````{prf:example}
:label: quant1 
{prf:ref}`seqconv` can be expressed more succincly using quantifiers:
$$
x_n\rightarrow l \; \text{ iff } \;\forall\varepsilon>0\; \exists N\in\mathbb{N} \;\text{ s.t. }\forall n\geq N\; |x_n-l|<\varepsilon.
$$

In words: 

"$x_n$ converges to $l$ if and only if for all $\varepsilon>0$, there exists $N\in\mathbb{N}$ such that for all $n\geq N$ we have $|x_n-l|<\varepsilon$".
````

**Exercise:**
Express {prf:ref}`Cauchy` in terms of quantifiers.


### Negation

The *negation* of a mathematical statement is its logical opposite. When negating statements involving quantifiers, the roles of $\forall$ and $\exists$ trade places, while all other parts of the statement are replaced with their logical opposites.

For example, consider the definition of disjoint sets.

$$
A, B\subseteq\mathbb{R}	 \; \text{ are disjoint \; iff }\;\; \forall x\in A, \; x\notin B.
$$

The negation is

$$
A, B\subseteq\mathbb{R}	 \; \text{ are }\textbf{not}\text{ disjoint iff }\;\; \exists x\in A, \text{ s.t } x\in B.
$$

For an example involving longer statements, consider again the definition of convergence:

$$
x_n\rightarrow l \; \text{ iff } \;\forall\varepsilon>0\; \exists N\in\mathbb{N} \;\text{ s.t. }\forall n\geq N\; |x_n-l|<\varepsilon.
$$

The negation of this is

$$
x_n\not\rightarrow l \; \text{ iff } \;\exists\varepsilon>0\; \;\text{ s.t. }\forall N\in\mathbb{N} \;\exists n\geq N\;\;\text{ s.t. } |x_n-l|\geq\varepsilon.
$$

That is, $x_n\not\rightarrow l$ if and only if there is some $\varepsilon>0$ for which, no matter how large we choose $N$, there is an even larger $n$ for which $|x_n-l|\geq\varepsilon$. You can think of this as "$|x_n-l|\geq\varepsilon$ infinitely often".

## Inequalities

Inequalities are the primary tool of analysts. Here is a reminder of two important ones.

### The triangle inequality

```{prf:theorem}
:class: note
:label: tri
For all real numbers $a$ and $b$,

$$
|a+b| \leq |a|+|b|.
$$
```

Note that the triangle inequality holds in higher dimensions, too. If $\textbf{a}$ and $\textbf{b}$ are vectors in $\mathbb{R}^n$, then the vectors $\mathbf{a}$, $\mathbf{b}$ and $\mathbf{a}+\mathbf{b}$ form sides of a triangle.

If the vertices of this triangle are $P$, $Q$ and $R$, then the triangle inequality is just saying that it is a shorter distance to walk from $P$ to $R$ directly than it would be to walk there via the point $Q$.

```{image} ../MAS2004-9Sem2Notes/figs/tri_ineq.png
:alt: Triangle with vertices $P$, $Q$ and $R$, and edges $\overrightarrow{PQ}=\mathbf{a}$, $\overrightarrow{QR}=\mathbf{b}$ and $\overrightarrow{PR}=\mathbf{a}+\mathbf{b}$. It is always shorter to travel directly from $P$ to $R$ than it is to go via $Q$. In other words, $|\mathbf{a}+\mathbf{b}|\leq|\mathbf{a}|+|\mathbf{b}|$.
:class: bg-primary mb-1
:width: 600px
:align: center
```


The following corollary of the triangle inequality will also be frequently useful.

**Corollary 0.2.6.**
For all $a,b\in\mathbb{R}$,

$$
\Big||a|-|b|\Big| \leq |a-b|.
$$

*Proof.*
Since the statement is symmetric in $a$ and $b$, we can assume without loss of generality that $|a|>|b|$. By the triangle inequality,

$$
|a| = |(a-b) +b| \leq |a-b| +|b|,
$$

and so

$$
|a|-|b|\leq |a-b|.
$$

Since we're assuming $|a|>|b|$,

$$
\Big||a|-|b|\Big| \leq |a|-b|,
$$

and so we are done.