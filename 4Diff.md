(chap:diff)=
# Differentiation

## Introduction

The processes of *differentiation* and *integration* constitute the two corner--stones of the *calculus* which revolutionised mathematics (and its applications), starting from the groundbreaking work of Newton and Leibniz in the seventeenth century. In this chapter we will focus on understanding differentiation from a rigorous analytic viewpoint, using the knowledge that we have gained about limits of functions. Before we start this process let us remind ourselves what differentiation is for.

The geometric motivation for differentiation is to find the *slope* or *gradient* of the tangent to a curve at a point lying on it. If the curve is given by a formula $y = f(x)$, then the gradient of the tangent at the point $(x, y)$  appears to be well--approximated by the slope of a chord connecting the very nearby points $(x, y)$ and $(x + \Delta x, y + \Delta y)$. This slope is given by the ratio:

$$
\displaystyle\frac{\Delta y}{\Delta x} = \displaystyle\frac{f(x + \Delta x) - f(x)}{\Delta x}.
$$

But to get from the slope of the chord to the slope of the tangent, it seems that we must put $\Delta x = 0$. This
cannot be taken literally as it gives us the meaningless ratio $0/0$.

The dynamic motivation for differentiation is to find the *instantaneous rate of change* of  one quantity with respect to another. Let us assume that we are dealing with a physical quantity $F(t)$ that changes as a function of time $t$. For example $F(t)$ could be position of a moving particle at time $t$, in which case the required rate of change is the velocity. Or $F(t)$ could be the charge on a conductor at time $t$, in which case the rate of change is the current. Then over a very small time interval $\Delta t$, the average rate of change is:

$$
\displaystyle\frac{\Delta F(t)}{\Delta t} = \displaystyle\frac{F(t + \Delta t) - F(t)}{\Delta t},
$$

and we again want to understand what happens when $\Delta t = 0$.

Of course, we now know that we must solve both of these problems by taking a limit as $\Delta x$, or $\Delta t$, tends to zero.

As before we will study real-valued functions defined on some subset $A$ of the real numbers, $f:A\to \mathbb{R}$.

## Differentiation as a limit

````{prf:definition}
:label: def:diff
 Let $f:A\to\mathbb{R}$ be a function. We say that $f$ is *differentiable* at $a \in A$ if
$ \lim_{x \rightarrow a}\displaystyle\frac{f(x) - f(a)}{x - a}$ exists. In this case we write

$$
f'(a) = \lim_{x \rightarrow a}\displaystyle\frac{f(x) - f(a)}{x - a} = \lim_{h \rightarrow 0}\displaystyle\frac{f(a +h) - f(a)}{h},
$$

and we call $f'(a) \in \mathbb{R}$, the *derivative of $f$ at $a$*.}
We say that $f$ is *differentiable* on $S \subseteq A$ if it is differentiable at every point $a \in S$. Then the mapping $a \mapsto f'(a)$ defines a real-valued function which is called the der*ivative} of $f$, and denoted by $f'$. This has domain

$$
\text{Dom}\left(f'\right) = \{x \in A : f\ \text{is differentiable at $x$}\}.
$$
````

Note that this definition involves the limit at $a$ of the function

$$
x\mapsto\frac{f(x) - f(a)}{x - a},
$$

in the sense of {prf:ref}`functionlimit`. Or, equivalently, the limit at $0$ of the function $h\mapsto \displaystyle\frac{f(a +h) - f(a)}{h}$.

In applied mathematics, we may often write $y = f(x)$, and express the function $f'$ as $\frac{dy}{dx}$. Then $f'(a) = \left.\frac{dy}{dx}\right|_{x=a}$. In analysis, this notation is not so helpful; it is usually easier to work with $f'$.


We can of course, iterate the notion of differentiability in the usual way. Suppose that $a \in \text{Dom}\left(f'\right)$ and that $f'$ is differentiable at $a$, then we define the second derivative $f^{\prime \prime}(a)$ of $f$ at $a$ by

$$
f^{\prime \prime} (a) = \left(f'\right)'(a).
$$

More generally if $n\in\mathbb{N}$ with $n > 2$ we define the $n$th derivative of $f$ at $a$ by

$$
f^{(n)}(a) = (f^{(n-1)})'(a),
$$

whenever the limit on the right-hand side exists. We say that $f$ is *infinitely differentiable* or *smooth* at $a$ if $f^{(n)}(a)$ exists (and is finite) for all $n\in\mathbb{N}$. It is also sometimes useful to employ the notation $f(a) = f^{(0)}(a)$.

````{prf:example}
If $f:\mathbb{R}\to\mathbb{R}$ is given by $f(x) = c$, where $c$ in $\mathbb{R}$ is constant, it is easy to check directly from {prf:ref}`def:diff` that $\text{Dom}\left(f'\right)= \mathbb{R}$, and $f'(a) = 0$ for all $a \in \mathbb{R}$.
````

````{prf:example}
Let $f:\mathbb{R}\to\mathbb{R}$ be given by $f(x) = x^{n}$, where $n\in\mathbb{N}$ is fixed.
Use the Binomial Theorem to show directly from the definition that $f$ is differentiable at all $x\in\mathbb{R}$,
with  $f'(x) = nx^{n-1}$.
````

**Solution.**
Let $a, h \in \mathbb{R}$. Using the binomial theorem, we have

\begin{align*}
&\frac{f(a + h) - f(a)}{h} \\
&\qquad=  \frac{(a + h)^{n} - a^{n}}{h} \\
&\qquad=  \frac{a^{n} + na^{n-1}h + \frac{1}{2}n(n-1)a^{n-2}h^{2} + \cdots + nah^{n-1} + h^{n} - a^{n}}{h}\\
&\qquad=  na^{n-1} +\frac{1}{2}n(n-1)a^{n-2}h + \cdots + nah^{n-2} + h^{n-1}.
\end{align*}

Thus, using algebra of limits,

$$
\lim_{h\to 0}  \frac{f(a + h) - f(a)}{h}= na^{n-1},
$$

so $f'(x) = nx^{n-1}$ for all $x \in \mathbb{R}$, and $\text{Dom}\left(f'\right) = \mathbb{R}$.

Next we turn our attention to the relationship between differentiability and continuity.

````{prf:theorem}
:label: dcont
If $f:A\to\mathbb{R}$ is differentiable at $a \in A$ then $f$ is continuous at $a$.
````

**Proof.** Using the definition of continuity ({prf:ref}`defcont`), we need to show that $\lim_{x\rightarrow a} f(x) = f(a)$. For $x \neq a$, write

$$
f(x) - f(a) = \frac{f(x) - f(a)}{x - a}\cdot(x - a).
$$

Since $f$ is differentiable at $a$, $\displaystyle\lim_{x\rightarrow a} \displaystyle\frac{f(x) - f(a)}{x - a} = f'(a)$, and of course $\displaystyle\lim_{x\rightarrow a} (x - a) = 0$. Hence by algebra of limits ({prf:ref}`AOL2`),

$$
\lim_{x\rightarrow a} \frac{f(x) - f(a)}{x - a}\cdot(x - a) =  f'(a)\cdot 0=0.
$$

So $\displaystyle\lim_{x\rightarrow a}(f(x) - f(a))$ exists and equals zero, and the result follows, by algebra of limits again. 
<div align="right">□</div>


On the other hand, it is not true that every function that is continuous at $a$  is differentiable at $a$.

````{prf:example} 
Consider the function $f:\mathbb{R}\to\mathbb{R}$ given by $f(x) = |x|$. It is continuous at every point in $\mathbb{R}$. It is also easy to see that it is differentiable at every $x \neq 0$. Show that it is not differentiable at zero, by showing that the relevant left and right limits are different there. 
````

**Solution.**
We have

\begin{align*}
\lim_{h \rightarrow 0^-}\displaystyle\frac{f(0 + h) - f(0)}{h} 
&= \lim_{h \rightarrow 0^-}\displaystyle\frac{|h|}{h} = \lim_{h \rightarrow 0^-}\frac{-h}{h} = -1.\\
\lim_{h \rightarrow 0^+}\displaystyle\frac{f(0 + h) - f(0)}{h} 
&= \lim_{h \rightarrow 0^+}\displaystyle\frac{|h|}{h} = \lim_{h \rightarrow 0^+}\frac{h}{h} = 1.
\end{align*}

Thus the left and right limits are different and so $\lim_{h \to 0}\displaystyle\frac{f(0 + h) - f(0)}{h} $ does not exist.

Generalising the last example, we have the following definition.

````{prf:definition}
We say that the function $f:A\to\mathbb{R}$ has a *left derivative* at $a \in A$ if $f_{-}'(a) = \lim_{h \rightarrow 0^-}\displaystyle\frac{f(a +h) - f(a)}{h}$ exists, and that it has a *right derivative* at $a \in A$ if $f_{+}'(a) = \lim_{h \rightarrow 0^+}\displaystyle\frac{f(a +h) - f(a)}{h}$ exists.
````

````{prf:theorem}
:label: lrd
One can show that a function $f:A\to \mathbb{R}$ is differentiable at $a \in A$ if and only if both the left and right derivatives at $a$ exist and are equal. In this case

$$
f'(a) = f_{-}'(a) = f_{+}'(a).
$$

````

## Rules for differentiation

The results in this section should all be familiar from MAS106, but now we can make the proofs rigorous.

````{prf:theorem}
Let $f$ and $g$ be real-valued functions that are differentiable at $a \in \text{Dom}(f) \cap \text{Dom}(g)$. Then the following hold.

(i) For each $\alpha,\beta \in \mathbb{R}$, the function $\alpha f + \beta g$ is differentiable at $a$ and

$$
(\alpha f + \beta g)'(a) = \alpha f'(a) + \beta g'(a).
$$

(ii) (The Product Rule) The function $fg$ is differentiable at $a$ and

$$
(fg)'(a) = f'(a)g(a) + f(a)g'(a).

$$

(iii) (The Quotient Rule) If $g(a) \neq 0$ then $f/g$ is differentiable at $a$ and

$$
\left(\frac{f}{g}\right)'(a) = \frac{g(a)f'(a) - f(a)g'(a)}{g(a)^{2}}.
$$
````

**Proof.**
(i) We have

$$
\frac{ (\alpha f + \beta g)(a+h)- (\alpha f + \beta g)(a)}{h}=
\alpha \frac{f(a+h)-f(a)}{h}+\beta\frac{g(a+h)-g(a)}{h}
$$

and, taking limits as $h$ goes to $0$, the result follows from the algebra of limits ({prf:ref}`AOL2`).

(ii) For all $h \neq 0$,

\begin{align*}
&\displaystyle\frac{(fg)(a + h) - (fg)(a)}{h}\\
&= \frac{f(a + h)g(a + h) - f(a)g(a + h)}{h} + \frac{f(a)g(a + h) - f(a)g(a)}{h}\\
&= \left(\frac{f(a+h) -f(a)}{h}\right)g(a + h) + f(a)\left(\frac{g(a + h) - g(a)}{h}\right). 
\end{align*}

The result follows by taking limits as $h \rightarrow 0$ and using {prf:ref}`def:diff` and the algebra of limits, together with the fact that at $a$, $g$ is differentiable, hence continuous by {prf:ref}`dcont`, and so $\lim_{h \rightarrow 0}g(a + h) = g(a)$.
3. First observe that by Problem 18, there exists $\delta > 0$ such that $g(x) \neq 0$ for all $x \in (a - \delta, a + \delta)$. Consider $h \in \mathbb{R}$ such that $|h| < \delta$. Then


\begin{align*}
& \frac{1}{h}\left(\left(\frac{f}{g}\right)(a + h) - \left(\frac{f}{g}\right)(a)\right) \\
&= \frac{1}{h}\left(\frac{f(a+h)g(a) - f(a)g(a + h)}{g(a)g(a + h)}\right)\\
&= \frac{1}{g(a)g(a+h)}\left( \frac{f(a+h) - f(a)}{h}g(a) - f(a)\frac{g(a + h) - g(a)}{h}\right), 
\end{align*}

and the result follows by algebra of limits, taking the limit as $h$ goes to $0$, using the fact that (as above), $\lim_{h \rightarrow 0}g(a + h) = g(a)$. 
<div align="right">□</div>


````{prf:theorem} Chain rule
:label: chain
Let $f, g$ be real-valued functions such that the range of $g$ is contained in the domain of $f$. Suppose that $g$ is differentiable at $a$ and that $f$ is differentiable at $g(a)$. Then $f \circ g$ is differentiable at $a$ and

$$
(f \circ g)'(a) = f'(g(a))g'(a).
$$

````

**Proof.** For $x\in \text{Dom}(g)$,  we consider

$$
\frac{(f \circ g)(x) - (f \circ g)(a)}{x-a} = \frac{ f(g(x)) - f(g(a))}{x-a}.
$$

We would like to write this as

$$
\frac{ f(g(x)) - f(g(a))}{g(x) - g(a)}\frac{g(x) - g(a)}{x-a},
$$

but that only makes sense when $g(x)\neq g(a)$.
To overcome this problem, we introduce the function $Q:\text{Dom}(f)\to \mathbb{R}$ defined by

$$
Q(y) = 
\begin{cases} 
\frac{f(y) - f(g(a))}{y-g(a)} & ~\mbox{if}~y\neq g(a),\\
f'(g(a))& ~\mbox{if}~y=g(a). 
\end{cases}
$$

We claim that

$$
\frac{ f(g(x)) - f(g(a))}{x-a}=Q(g(x))\frac{g(x) - g(a)}{x-a},
$$

for all $x\in \text{Dom}(g)$. Indeed, for $x$ such that $g(x) \neq g(a)$, this is clear because the factors of $g(x)-g(a)$ cancel. And for $x$ such that $g(x)=g(a)$, both sides are zero.

So we need to study

$$
\lim_{x\to a} Q(g(x))\frac{g(x) - g(a)}{x-a}.
$$

Since $g$ is differentiable at $a$, by {prf:ref}`dcont`, $g$ is continuous at $a$. Since $f$ is differentiable
at $g(a)$, $Q$ is continuous at $g(a)$. So $Q\circ g$ is continuous at $a$ and $\lim_{x\to a} Q(g(x))$ exists and
is equal to $Q(g(a))=f'(g(a))$. Using the algebra of limits, we then have
\begin{align*}
\lim_{x\to a} Q(g(x))\frac{g(x) - g(a)}{x-a}
&=\lim_{x\to a} Q(g(x))\lim_{x\to a}\frac{g(x) - g(a)}{x-a}\\
&=f'(g(a))g'(a),
\end{align*}
as required. 
<div align="right">□</div>


## Turning points and Rolle's theorem

````{prf:definition}
A function $f:A\to\mathbb{R}$ has a *local minimum* at $a \in A$ if there exists $\delta > 0$ such that $(a-\delta, a+\delta)\subseteq A$ and  $f(x) \geq f(a)$ for all $x \in (a-\delta, a+\delta)$.

A  function $f:A\to\mathbb{R}$ has a  *local maximum* at $a \in A$ if there exists $\delta > 0$ such that $(a-\delta, a+\delta)\subseteq A$ and $f(x) \leq f(a)$ for all $x\in (a-\delta, a+\delta)$.

A *turning point* (sometimes called an *extreme point*}) for $f$ is a point in its domain that is either a local minimum or a local  maximum.
````

It is important to distinguish carefully between local maxima and minima and global maxima and minima, when the latter exist. For example if $f:[a, b] \rightarrow \mathbb{R}$ is continuous, then we know by the extreme value theorem ({prf:ref}`thm:evt`) that it attains both its supremum and infimum on $[a, b]$. So these are the global maximum and minimum, respectively. But they are not necessarily turning points, because they might be at the endpoints of the interval $[a,b]$. And, of course, a local minimum/maximum need not be a global one.

````{prf:example}
Consider the function $f:[-3, 2] \rightarrow \mathbb{R}$ defined by

$$
f(x) = \begin{cases} x+2& ~\mbox{if}~x \in [-3, -1),\\  x^{2} & ~\mbox{if}~x \in [-1, 2].\\ \end{cases}
$$

Identify any turning points and the global maximum and minimum.
````

**Solution.**
Note that the function is continuous (by checking what happens at $x=-1$), so as above there is a global maximum and minimum. The global maximum is $4$, attained at $x = 2$. The global minimum is  $-1$, attained at $x = -3$. Neither of these is a turning point (because they are the endpoints of the interval: we cannot find a $\delta$ such that all points within distance $\delta$ are contained in the domain). There is a local minimum at $x = 0$ and a local maximum at $x=-1$. 


````{prf:theorem}
:label: ext1
If  $f:A\to\mathbb{R}$ is differentiable at $a \in A$ and $a$ is a turning point for $f$, then $f'(a) = 0$.
````

**Proof.** We suppose that $f$ has a local minimum at $a$.  So there exists $\delta > 0$ so that $(a-\delta, a+\delta)\subseteq\text{Dom}(f)$ and $f(x) \geq f(a)$ for all $x \in (a-\delta, a+\delta)$. Hence
\begin{align*}
&\displaystyle\frac{f(x) - f(a)}{x - a} \leq 0 \qquad \text{for all $x$ such that $a - \delta < x < a$,}\\
&\displaystyle\frac{f(x) - f(a)}{x - a} \geq 0 \qquad \text{for all $x$ such that $a < x < a + \delta$}.
\end{align*}

Taking one-sided limits as $x \rightarrow a$, we deduce that $f_{-}'(a) \leq 0$ and $f_{+}'(a) \geq 0$. But $f$ is differentiable at $a$, and so $f_{-}'(a)  = f_{+}'(a) = f'(a)$. We conclude that $f'(a) = 0$, as required.

The argument in the case of a local maximum is very similar. 
<div align="right">□</div>


A point where a differentiable function has derivative zero is sometimes called a *stationary* point. So {prf:ref}`ext1` says that turning points are stationary points. The converse to {prf:ref}`ext1` is false: not all stationary points are turning points.  Consider for example the familiar case of $f(x) = x^{3}$. Then $f'(0) = 0$ but $0$ is neither a local maximum nor a local minimum; it is what is called an *inflection point*}. We will not pursue the story of classifying stationary points further here. You have seen this before in MAS106, and it is revisited in one of the exercises. Instead we will use  {prf:ref}`ext1` to explore some new territory.

````{prf:theorem} Rolle's theorem
:label:  Roll
Let $f:[a,b]\to\mathbb{R}$ be a function that is continuous on $[a,b]$ and differentiable on $(a,b)$ with $f(a)=f(b)$. Then there exists $c\in(a,b)$ such that $f'(c) = 0$.
````

**Proof.** If $f$ is constant, the result is obvious, so assume that $f$ takes at least two distinct values. By {prf:ref}`thm:evt`, $f$ is bounded on $[a, b]$ and attains both its supremum and infimum. It cannot attain both of these at the end-points, as then they would be equal and $f$ would be constant. So there must be a $c\in (a,b)$ where either the supremum or infimum is attained. But then $c$ is a turning point, and so $f'(c) = 0$ by {prf:ref}`ext1`. 
<div align="right">□</div>


## The mean value theorem

The next result is a generalisation of Rolle's theorem and a very important result, with lots of interesting consequences.

````{prf:theorem} Mean value theorem
:label: mvt
If  $f:[a,b]\to\mathbb{R}$ is continuous on $[a, b]$ and differentiable on $(a,b)$, then there exists $c \in (a, b)$ such that

$$
f'(c) = \frac{f(b) - f(a)}{b - a}.
$$

````

**Proof.** Let  $\alpha = \frac{f(b) - f(a)}{b - a}$. Define $g:[a,b]\to\mathbb{R}$ by  $g(x) = f(x) - \alpha(x - a)$. Then $g$ is continuous on $[a, b]$, and differentiable on $(a, b)$, because $f$ is. You can check easily that $g(a) = g(b) = f(a)$, and so we may apply Rolle's theorem ({prf:ref}`Roll`) to deduce that there exists $c \in (a, b)$ such that $g^{\prime }(c) = 0$. But $g'(c)=f'(c)-\alpha$ and
hence $f'(c) = \alpha$, as required. 
<div align="right">□</div>


The mean value theorem gives a rigorous foundation to the "geometrically obvious'' assertion that a differentiable function $f$ on an interval $[a, b]$ must at some point attain a slope equal to the slope of the line through the endpoints $(a, f(a))$ and $(b, f(b))$ --- see {numref}`MVT`.

```{figure} ../MAS2004-9Sem2Notes/figs/MVT.png
---
height: 500px
name: MVT
---
A visual representation of the mean value theorem.
```

In analysis, for any statement connecting calculus to some geometric property of a curve, the mean value theorem is likely to feature in its proof. We investigate one example of this next.

````{prf:cor} Monotonicity revisited
Suppose that  $f:[a,b]\to\mathbb{R}$ is continuous on $[a, b]$ and differentiable on $(a, b)$.

[(i)]1. If $f'(x) \geq 0$ for all $x \in (a, b)$, then $f$ is monotonic increasing on $[a, b]$.
2. If $f'(x) > 0$ for all $x \in (a, b)$, then $f$ is strictly monotonic increasing on $[a, b]$.
3. If $f'(x) \leq 0$ for all $x \in (a, b)$, then $f$ is monotonic decreasing on $[a, b]$.
4. If $f'(x) < 0$ for all $x \in (a, b)$, then $f$ is strictly monotonic decreasing on $[a, b]$.
````

**Proof.** We'll just do the first of these, as the others are so similar.
Choose arbitrary $\alpha, \beta$ such that $a \leq \alpha < \beta \leq b$. By the mean value theorem ({prf:ref}`mvt`), there exists $c \in (\alpha, \beta)$ so that

$$
\frac{f(\beta) - f(\alpha)}{\beta - \alpha} = f'(c) \geq 0.
$$

Hence $f(\beta) \geq f(\alpha)$ and so $f$ is monotonic increasing, as required. 
<div align="right">□</div>


%\include{Redacted/inverses revisited.tex}

%\include{Redacted/CMVT.tex}

%\include{Redacted/L'Hop.tex}

%\include{Redacted/Taylor.tex}
