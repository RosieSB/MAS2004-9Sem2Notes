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

# Limits of functions

## Functions on the real line

In this section, we revise some aspects of functions and look at some examples. This is mostly revision of material from MAS106.

We will be interested in functions $f:X\to Y$, where $X$ and $Y$ are some subsets of the real numbers $\mathbb{R}$ (perhaps the whole of $\mathbb{R}$). Recall that $f$ being a function from $X$ to $Y$ means that for each element $x\in X$, there is specified exactly one element $f(x)\in Y$, the *value* of the function $f$ on the element $x$.

The *domain* of $f$ is $X$, and we sometimes use the notation $\text{Dom}(f):=X$. The set $Y$ is called the *codomain* of $f$. The *range* (or *image*) of the function $f$ is the set

$$
\text{Range}(f)=\{y \in Y : y = f(x)~\mbox{for some}~x \in X\};
$$

that is, it is the set of *values* attained by the function.

It is important in this course that a function has a specified domain and codomain. In particular, giving a *formula*, like $\frac{1}{x}$, for example, is not giving a function, although it may be part of the information that specifies a function. We could give a function by, for example, saying $f:\mathbb{R}\setminus\{0\}\to \mathbb{R}$, given by $f(x)=\frac{1}{x}$. And this is a different function from $f:(0,1)\to \mathbb{R}$, also given by  $f(x)=\frac{1}{x}$.

Notice that we have used the *difference* of sets notation here: recall that if $X$ and $Y$ are arbitrary sets, then

$$
X \setminus Y = X \cap Y^{c} = \{x \in X : x \notin Y\}.
$$

If we have some formula in $x$ that we would like to use for the value $f(x)$ of a function, it is often useful to think about the largest domain $f$ could have, that is, the set of all  $x$ in $\mathbb{R}$ for which $f(x)$ makes sense as a real number. This will not include any $x \in \mathbb{R}$ for which we might be tempted to write "$f(x) = 0/0$" or "$f(x) = \pm \infty$".


````{prf:example} Polynomial functions
:label: poly
A *polynomial* is a function $f:X\to\mathbb{R}$  of the form

$$
f(x) = a_{0} + a_{1}x + \cdots + a_{n-1}x^{n-1} + a_{n}x^{n},
$$

where the *coefficients* $a_{0}, a_{1}, \ldots, a_{n}$ are in $\mathbb{R}$, and the *degree* $n$ is a natural number. Here, $X$ can be any subset of $\mathbb{R}$.
````

````{prf:example} Rational functions
:label: rational
A *rational function* is a function $f:X\to\mathbb{R}$  of the form $f(x) = \frac{p(x)}{q(x)}$, where $p$ and $q$ are polynomials.  The largest subset of $\mathbb{R}$ we can take as its domain $X$ is $\{x \in \mathbb{R} : q(x) \neq 0\}$.

For example, if  $f(x) = \displaystyle\frac{x^{2} + 5}{(x+1)(x-3)}$, the largest possible domain of $f$ is $\mathbb{R} \setminus \{-1, 3\}$.
````


````{prf:example} The sign function
:label: sgn
The *sign function* $\text{sgn}:\mathbb{R}\to \mathbb{R}$ is defined by

$$
\text{sgn}(x) = \left\{\begin{array}{c c} -1 & ~\mbox{if}~x < 0,\\
	0 & ~\mbox{if}~x = 0,\\
	1& ~\mbox{if}~x > 0. \end{array} \right.
$$

The range of this function is $\{-1, 0, 1\}$.
````

````{prf:example} Indicator functions
:label: indicatorfn
The *indicator function* of the closed interval $[a, b]$ is the function ${\bf 1}_{[a,b]}:\mathbb{R}\to\mathbb{R}$ given by

$$
{\bf 1}_{[a,b]}(x) = \left\{\begin{array}{c c} 1 & ~\mbox{if}~x \in [a, b],\\ 0& ~\mbox{if}~x \notin [a, b]. \end{array} \right.
$$

Similarly, we can define an indicator function of  an open interval, or an arbitrary subset of $\mathbb{R}$. The indicator function of $[0, \infty)$ is called the *Heaviside function* by engineers.
````

Other important functions are the functions $f:\mathbb{R}\to\mathbb{R}$, given by $f(x) = e^{kx}, f(x) = \sin(kx)$ and $f(x) = \cos(kx)$, where $k \in \mathbb{R}$.  In analysis, they are best defined as convergent power series --- see later.

**Pointwise operations.**<br>
Let $X,Y\subseteq\mathbb{R}$, and let $f:X\to\mathbb{R}$ and $g:Y\to\mathbb{R}$ be functions. Let $\alpha\in\mathbb{R}$. We define new functions, $f+g$, $\alpha f$, $fg$ and $\frac{f}{g}$ pointwise, but we need to be careful with domains. 

- *Pointwise sum.* 

$$
f+g:X\cap Y\to \mathbb{R}; \; (f+g)(x) := f(x) + g(x),
$$

- *Pointwise scalar multiplication.* 

$$
\alpha f:X\to \mathbb{R}; \; (\alpha f)(x):=\alpha f(x),
$$

- *Pointwise multiplication.* 

$$
fg: X\cap Y\to\mathbb{R}; \; (fg)(x):=f(x)g(x),
$$

- *Pointwise division.* Here, more care must be taken with domains: 

$$
\frac{f}{g}:\left\{x\in X\cap Y:g(x)\neq 0\right\} \to\mathbb{R}; \; \left(\frac{f}{g}\right)(x) := \frac{f(x)}{g(x)}.
$$


*Remarks.*

1. In each case, the domain is taken to be the largest subset of $\mathbb{R}$ for which the pointwise operation is defined.

2. Recall from Semester 1 the set ${\cal F}(\mathbb{R})$ of all functions from $\mathbb{R}$ to $\mathbb{R}$. The pointwise operations of addition and scalar multiplication turn $\mathcal{F}$ into a vector space over $\mathbb{R}$ (but it is not finite-dimensional). Pointwise multiplication gives $\mathcal{F}(\mathbb{R})$ the additional structure of an *algebra* over $\mathbb{R}$. These structural properties are important in higher analysis (e.g. functional analysis).

**Composition of functions.** <br>
The *composition* $g \circ f$ of two functions $f$ and $g$ is defined only when the codomain of $f$ is the same as the domain of $g$. Note that we are using the usual convention that $g\circ f$ means "$f$ first".

So, if $f:X\to Y$ and $g:Y\to Z$, then we have the composition $g\circ f: X\to Z$, given by

$$
(g \circ f)(x) = g(f(x)).
$$

Of course, the order of composition matters: we typically do not have $f \circ g = g \circ f$, even at points where both are defined. For example, if $f:\mathbb{R}\to\mathbb{R}$ is given by $f(x)=x+2$ and $g:\mathbb{R}\to\mathbb{R}$ is given by \$ g(x)=3x\$ then $g\circ f:\mathbb{R}\to\mathbb{R}$ given by $(g\circ f)(x)=3x+6$, whereas  $f\circ g:\mathbb{R}\to\mathbb{R}$ given by $(f\circ g)(x)=3x+2$.


## The limit of a function

We want to make rigorous the notion of $\lim_{x \rightarrow a}f(x)$, for a function $f:X \rightarrow \mathbb{R}$, and a point $a\in\mathbb{R}$. Note that $a$ may not be an element of the domain $X$, here (though it can be). You have already studied this in MAS106 and you should have good intuition for this situation. Here we will make the idea precise, using sequences.

First note that it only makes sense to consider the behaviour of $f(x)$ as $x\rightarrow a$ if there are points in the domain of $f$ that get arbitrarily close to $a$.

````{prf:definition} Limit point
:label: limitpt
Let $X\subseteq\mathbb{R}$. A real number $a$ is called a *limit point* of $X$ if there is a sequence $(x_n)$ in $X$ that converges to $a$ and satisfies $x_n\neq a$ for all $n\in\mathbb{N}$.

Equivalently, $a$ is a limit point of $X$ if any open interval containing $a$ has non-empty intersection with $X$.
````

````{prf:example}
(i) Let $X=(0,2)\cup\{3\}$. Then $0$ and $2$ are limit points of $X$, but $3$ is not.

(ii) A real number $a\in\mathbb{R}$ is a limit point of $[0,1]$ if and only if $a\in[0,1]$.

(iii) More generally, given $a<b$, then $[a,b]$ is the set of all limit points for any of the intervals $(a,b)$, $(a,b]$, $[a,b)$ and $[a,b]$.
````

````{prf:definition} Functional limit
:label: functionlimit
Let $f:X\to\mathbb{R}$ be a function, let $a\in\mathbb{R}$ be a limit point of $X$, and let $l\in\mathbb{R}$.

We say that $f$ *converges* to $l$ as $x\rightarrow a$, and write

$$
\lim_{x \rightarrow a}f(x) =l,
$$

if, for every sequence $(x_n)$ in $X\setminus\{a\}$ that converges to $a$, we have $\displaystyle\lim_{n\rightarrow\infty}f(x_n)=l$.
````

**Notes.**
1. We require that $a$ be a limit point of $X$ so that it to make sense to consider what happens to the values of the function as we approach $a$.
2. We must have convergence of $(f(x_n))$ to $l$ for *every* such sequence $(x_{n})$.
3. The real number $a$ may or may not be in the domain $X$.



````{prf:example}
Consider $f:\mathbb{R} \setminus \{-5, 3, 5\}\to \mathbb{R}$, given by

$$
f(x) = \frac{x - 5}{(x^{2} - 25)(x - 3)}.
$$

Investigate $\lim_{x \rightarrow a}f(x)$ for each $a\in\mathbb{R}$. (You will need to think about points in the domain and each of the three special points $-5, 3, 5$ separately.)

*Solution.*
It's helpful (but not necessary as part of the formal solution) to draw the graph of the function.



```{figure} ../MAS2004-9Sem2Notes/figs/(x-5),((x2-25)(x-3)).png
---
height: 300px
name: (x-5),((x2-25)(x-3)
---
Graph of $f(x) = \displaystyle\frac{x - 5}{(x^{2} - 25)(x - 3)}$.
```

Let's write $X=\mathbb{R}\setminus\{-5, 3, 5\}$, the domain of $f$. Note that every real number is a limit point of $X$. However, the most interesting limit points to consider are those that lie outside of $X$. This is because it is fairly easy to calculate limits at points in $X$. For example,

$$
\lim_{x \rightarrow 1}f(x) = -\frac{1}{12}=f(1).
$$

(Check this carefully, using the definition).

More generally, in this example, if you take the limit at a point $a \in X$, you always find that

$$
\lim_{x\rightarrow a} f(x) = f(a).
$$

This tells us that the function $f$ is *continuous* at these points. We will discuss the concept of continuity in more detail in [Chapter 3](#chap:cty).

The more interesting problem is to find out what happens at points that are *not* in $X$. Observe that

$$
f(x) = \frac{1}{(x+5)(x-3)}, \qquad \text{for all $x \in X$.}
$$

**To investigate the point $x = 5$:**<br>
Choose an arbitrary sequence $(x_{n})$ with $x_{n} \in X$ satisfying $\lim_{n \rightarrow \infty}x_{n} = 5$. Note that such sequences certainly exist, for example

$$
(x_{n} = 5 + \frac{1}{n}), (x_n=5 + 7/n^{2}), (x_n=5 - 108/n^{4})...).
$$

Then $f(x_{n}) = \displaystyle\frac{1}{(x_{n}+5)(x_{n}-3)}$ and $\displaystyle\lim_{n \rightarrow \infty}f(x_{n}) = \displaystyle\frac{1}{10.2} = \displaystyle\frac{1}{20}$, by the algebra of limits. So we conclude that

$$
\lim_{x \rightarrow 5}f(x) = \frac{1}{20}.

$$
Thus the limit exists at the point $x = 5$, even though $5$ is not in the domain of $f$.

**To investigate the point $x = -5$:**<br>
In this case, numerical experiments or considering the graph of the function may lead you to doubt that a limit exists. So consider the sequence $(y_{n})$, where $y_{n} = -5 + \frac{1}{n}$, for each $n\in\mathbb{N}$. Then $\lim_{n \rightarrow \infty}y_{n} = -5$, and we find that

$$
f(y_{n}) = \frac{1}{\frac{1}{n}\left(\frac{1}{n} - 8\right)} = \frac{n}{\frac{1}{n} - 8},
$$

and so $(f(y_{n}))$ diverges to $-\infty$. So we've found a sequence $(y_{n})$ such that (i) and (ii) of the definition are satisfied, but $(f(y_{n}))$ diverges. Hence we conclude that $f$ has no limit at $x = -5$.

**To investigate the point $x = 3$:** <br>
This is left as  an exercise. Again, $f$ has no limit at $x = 3$.

We note here that the function $f$ is not continuous at the points $a = -5, 3$ or $5$; indeed $f(a)$ is not defined when $a$ takes these values. We can *extend* $f$ to be a continuous function at $a=5$ by setting
$f(5)=\frac{1}{20}$. On the other hand, at $a=-5$ and at $a=3$, there is no value we could assign for $f(a)$
that would extend $f$ to a continuous function there.  We will return to all these issues of continuity in [Chapter 3](chap:cty).
````

````{prf:theorem} Algebra of limits
Suppose that $f:A \rightarrow \mathbb{R}$, $g :B \rightarrow \mathbb{R}$, and $a \in \mathbb{R}$ is such that $\lim_{x\rightarrow a} f(x) = l$ and $\lim_{x\rightarrow a} g(x) = m$, then

(i) $\displaystyle\lim_{x\rightarrow a} (f + g)(x) = l + m$,

(ii) $\displaystyle\lim_{x\rightarrow a} (fg)(x) = lm$,

(iii) $\displaystyle\lim_{x\rightarrow a} (\alpha f)(x) = \alpha l$, for all $\alpha \in \mathbb{R}$,

(iv) $\displaystyle\lim_{x\rightarrow a} \left(\displaystyle\frac{f}{g}\right)(x) = \displaystyle\frac{l}{m}$, if $m \neq 0$.
````

*Proof.* These all follow from the algebra of limits for sequences. For example, for (i), if $(x_{n})$ is an arbitrary sequence in $A\cap B$ with $x_n\neq a$ for all $n\in\mathbb{N}$ such that $(x_n)$ that converges to $a$, then

$$
\begin{align*} 
\lim_{n\rightarrow\infty} (f + g)(x_{n}) &= \lim_{n\rightarrow\infty} (f(x_{n}) + g(x_{n})) \\
&= \lim_{n\rightarrow\infty} f(x_{n}) + \lim_{n\rightarrow\infty} g(x_{n})\\
&= l + m, 
\end{align*}
$$
as required.
Here the first line uses the definition of a sum of functions and the second line uses algebra of limits (for real sequences). $\square$


From a geometric perspective, the idea of a limit is that as $x$ gets closer and closer to $a$, so $f(x)$ should get closer and closer to $l$. More insight to this is given by the following theorem, which establishes the important $(\varepsilon-\delta)$ criterion for existence of limits.

````{prf:theorem} $(\varepsilon-\delta)$ criterion
:label: ed
 Let  $f:X \rightarrow \mathbb{R}$, let $a\in\mathbb{R}$ be a limit point of $X$, and let $l\in\mathbb{R}$. The following are equivalent:

(i) $\lim_{x\rightarrow a} f(x) = l$.

(ii) Given any $\varepsilon>0$ there exists $\delta > 0$ such that whenever $x \in X$ with $0 < |x - a| < \delta$, then $|f(x) - l| < \varepsilon$.
````

````{prf:remark}
The $(\varepsilon-\delta)$ criterion is also frequently expressed in terms of quantifiers:

$\forall\varepsilon>0$, $\exists\delta>0$ s.t.~$\forall x\in X$, $0<|x-a|<\delta \; \Rightarrow \;|f(x)-l|<\varepsilon$.

Take some time to compare these two statements and check they are saying the same thing.
````

**Proof of {prf:ref}`ed`.** First assume that the $(\varepsilon-\delta)$ criterion holds and suppose $\varepsilon > 0$. So there exists $\delta > 0$ such that for all $x \in X$,

$$
0<|x - a| < \delta \Rightarrow |f(x) - l| < \varepsilon.
$$

Let $(x_{n})$ be an arbitrary sequence in $X\setminus\{a\}$ with limit $a$. Then since $x_n\rightarrow a$, there exists $N\in\mathbb{N}$, such that  $0<|x_{n} - a| < \delta$ for all $n\geq N$. But then, for all $n \geq N$, we have $|f(x_{n}) - l| < \varepsilon$, and so $\lim_{x\rightarrow a} f(x) = l$, as was required. We have established that $(i)\Rightarrow(ii)$.

Now we must establish the converse, namely if $f$ has limit $l$ at $a$, then the $(\varepsilon-\delta)$ criterion follows. In fact, we seek a proof by contrapositive[^contrapositive] , so we will assume that the $(\varepsilon-\delta)$ criterion fails, and then show that $f$ cannot have  limit $l$ at $a$.

[^contrapositive]:That is,  we use the fact that if $P$ and $Q$ are propositions, then $P \Rightarrow Q$ if and only if $\neg Q \Rightarrow \neg P$.

If the $(\varepsilon-\delta)$ criterion fails, then there exists $\varepsilon>0$ such that for all $\delta > 0$, there exists $x \in X$ with $0 < |x - a| < \delta$, but $|f(x) - l| \geq \varepsilon$.

Now for this $\varepsilon>0$, choose successively $\delta = 1, \frac{1}{2}, \frac{1}{3}, \ldots$ and construct a sequence $(x_{n})$ as follows:

$$
x_{1} \in X \text{ satisfies } 0<|x_{1} - a| < 1 \text{ and }|f(x_{1}) - l| \geq \varepsilon. \\
x_{2} \in X\text{ satisfies } 0<|x_{2} - a| < \frac{1}{2}\text{ and }|f(x_{2}) - l| \geq \varepsilon.
\vdots
x_{n} \in X\text{ satisfies }0<|x_{n} - a| < \frac{1}{n}\text{ and }|f(x_{n}) - l| \geq \varepsilon.
$$

Then $(x_n)$ is a sequence in $X\setminus\{a\}$ and by the sandwich rule, we have $\lim_{n\rightarrow\infty} x_{n} = a$. Also, by the above construction the sequence $(f(x_{n}))$ does not converge to $l$.

So we have shown that if the $(\varepsilon-\delta)$ criterion fails, then the function $f$ does not have limit $l$ at $a$. It follows that $(ii)\Rightarrow(i)$. $\square$


````{prf:theorem} Sandwich rule for functions
Suppose that $f:X\to\mathbb{R}$,  $g:Y\to\mathbb{R}$ and $h :Z\to \mathbb{R}$ and suppose that there exists an interval $(a, b) \subseteq X\cap Y\cap Z$ such that for all $x \in (a, b)$

```{math}
:label: sw1
f(x) \leq g(x) \leq h(x).
```

If for some $c \in (a, b)$ and $l\in\mathbb{R}$ we have

```{math}
:label: sw2
	\lim_{x \rightarrow c}f(x) = \lim_{x \rightarrow c}h(x) = l,
```

then $\displaystyle\lim_{x \rightarrow c}g(x)$ exists and is equal to $l$.
````

*Proof.* Let $(x_{n})$ be an arbitrary sequence that converges to $c$. 
Note that by taking $N \in \mathbb{N}$ sufficiently large, we can ensure that $x_{n} \in (a, b)$ for all $n\geq N$. Define sequences $(a_n)$, $(b_n)$ and $(c_n)$ by

$$
a_{n} = f(x_{n + N}), \hspace{1em} b_{n} = g(x_{n + N}), \hspace{1em} \text{and} c_{n} = h(x_{n + N}),
$$

for all $n\in\mathbb{N}$. By [](sw1), for all $n\in\mathbb{N}$,

$$
a_n \leq b_n \leq c_n, \hspace{2em}
$$

and by  [](sw2), $\displaystyle\lim_{n\rightarrow\infty}a_n = \lim_{n\rightarrow\infty}c_n = l$. Hence by the sandwich rule for sequences,

$$
\lim_{n\rightarrow \infty}c_n = \lim_{n\rightarrow \infty} g(x_n)= l,
$$

and we have established that $\displaystyle\lim_{x \rightarrow c}g(x)$ exists and is equal to $l$. $\square$


## Divergence

In the same setting as {prf:ref}`functionlimit`, we say that a function $f:X \rightarrow \mathbb{R}$ *diverges* at $x=a$ if $\lim_{x\rightarrow a} f(x)$ does not exist. 

There are some interesting types of behaviour involved here. For example, we say that the function $f$ *diverges to infinity* at $x = a$ and we write 

$$
\lim_{x\rightarrow a} f(x) = \infty
$$

if for every sequence $(x_{n})$, with $x_{n} \in X$, $x_n\neq a$, which satisfies $\lim_{n\rightarrow\infty} x_{n} = a$, we have $\lim_{n\rightarrow\infty} f(x_{n}) = \infty$, i.e. the sequence of real numbers $(f(x_{n}))$ diverges to infinity. 

The notion of *divergence to minus infinity* is defined similarly, and in that case we write $\lim_{x\rightarrow a} f(x) = -\infty$. For an example of divergence to infinity, consider e.g. $\lim_{x \rightarrow 0}\frac{1}{x^2}$. The details are left to you.

If convergence fails for a function $f:X\to\mathbb{R}$ at a point $a\in\mathbb{R}$, it may be that a weaker notion of convergence still applies, in which the direction of approach is restricted to one side at a time.

````{prf:definition} Marginal limits
Let $f:X\to\mathbb{R}$ and let $a\in\mathbb{R}$ be a limit point of $X$. We say that $f$ has *left limit* $l$ at a point $a\in\mathbb{R}$, and write

$$
\lim_{x\rightarrow a^-}f(x) = l
$$

if for all $\varepsilon>0$ there exists a $\delta>0$ such that $|f(x)-l|<\varepsilon$ whenever $0<x-a<\delta$.

We say $f$ has a *right limit* $l$ at $a$, and write,

$$
\lim_{x\rightarrow a^+}f(x) = l
$$

if for all $\varepsilon>0$ there exists a $\delta>0$ such that $|f(x)-l|<\varepsilon$ whenever $\delta<x-a<0$.
````

Equivalently, in terms of sequences,

- $\lim_{x\rightarrow a^-}f(x) = l$ if for any sequence $(x_n)$ in $X$ for which $x_n<a$ for all $n\in\mathbb{N}$ and $\lim_{n\rightarrow\infty}=a$, we have $\lim_{n\rightarrow\infty}f(x_n)=l$, for some $l\in\mathbb{R}$.

- $\lim_{x\rightarrow a^+}f(x) = l$ if for any sequence $(x_n)$ in $X$ for which $x_n>a$ for all $n\in\mathbb{N}$ and $\lim_{n\rightarrow\infty}=a$, we have $\lim_{n\rightarrow\infty}f(x_n)=l$, for some $l\in\mathbb{R}$.

The proof that these definitions are equivalent is very similar to that of Theorem [2](#ed), and is left to you to do as an exercise.

````{prf:example}
:label:indicatorlims
Heaviside's indicator function, $\textbf{1}_{[0,\infty)}$, as defined in {prf:ref}`indicatorfn`, has both left and right limits at the point $0$: one can check that $\lim_{x\rightarrow 0^-}=0$ and $\lim_{x\rightarrow 0^+}=1$. Since these limits disagree, there is no well-defined limit for this function at $x=0$. 
````

We also meet functions that diverge in different ways when approached from the left and from the right of a given point.

````{prf:example}
Consider $f: \mathbb{R} \setminus \{0\}\to \mathbb{R}$ given by $f(x) = \frac{1}{x}$. 

```{figure} ../MAS2004-9Sem2Notes/figs/1,x.png
---
height: 300px
name: 1/x
---
Graph of $f(x) = \frac{1}{x}$.
```
It is easily verified that $\lim_{x \rightarrow 0^-}f(x) = - \infty$, and $\lim_{x \rightarrow 0^+}f(x) =  \infty$.
````
