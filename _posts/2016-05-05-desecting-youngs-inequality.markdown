---
layout: post
title:  "Desecting Young's Inequality!"
categories: Inequality
excerpt: Young's Inequality is used for a wide range of proofs. We're doing a step-by-step how it can be proofed (with Visuals).
---

<h2>Young's Inequality</h2>
<h3>Motivation</h3>
This semester i've applied for the course "Introduction to Topology". As always proofs built upon other proofs. I will desect some inequalities and their proofs, which are needed for topology. I begin with Young's Inequality which can be used to proof the Hoelder Inequality. The Minkowski Inequality depends on the latter and is used to show that the euclidian norm is a metric.

<h3 id="defyoung">Definition</h3>
Let $f: [0,\infty[ \rightarrow [0,\infty[$ be strictly monotonically increasing and unlimited with $f(0)=0$. This implies that the function is bijective (injective + surjective) and the inverse function $f^{-1}$ is defined. If the following property holds true $a,b \gt 0 $ Young's Inequality is:
\begin{eqnarray}\label{eq:young}
ab \leq \int_0^a f(x) dx + \int_0^b f^{-1}(y) dy
\end{eqnarray}

<h3>Proof</h3>
The next figure depicts how this can be proven visually. For $f(a) > b$ and $f(a) < b$ adding the area under the curves together
always results in a bigger area than that of the rectangle $ab$. If $f(a)=b$ the area is exactly equal to the rectangle area enclosed by a and b.
<figure>
<img width="350px" src="{{site.url}}/image/YoungVis.jpg" />
</figure>

<p>
First we need to describe the inverse function $f^{-1}(y)$ by x. So substitute $f^{-1}(y)=x$ in the second integral of above eq. Additionally mind $\frac{dy}{dx}= f'(x)$ and to adjust the interval of the integral.
</p>
\begin{eqnarray}\label{eq:finverse}
\int_0^b f^{-1}(y) dy = \int_0^{f^{-1}(b)} x f'(x) dx
\end{eqnarray}
<p>
Next follow it up with partial integration: $u = x, v' = f'(x), u' = 1, v = f(x)$.
\begin{eqnarray} \label{eq:fy}
\int uv' = uv | - \int u'v = x*f(x)|_0^{f^{-1}(b)} - \int_0^{f^{-1}(b)} 1*f(x) dx = f^{-1}(b)*b - \int_0^{f^{-1}(b)} f(x) dx
\end{eqnarray}
This allows us to rewrite eq. \ref{eq:young} by putting in eq. \ref{eq:fy} and fusing the integrals:
\begin{eqnarray}
	ab \leq \int_0^a f(x) dx + f^{-1}(b)*b - \int_0^{f^{-1}(b)} f(x) dx = \int_{f^{-1}(b)}^a f(x) dx + f^{-1}(b)*b
\end{eqnarray}
<p>
For $f(a)=b$ the area is exactly $ab$. The integral becomes 0, $f^{-1}(b)=a$ leaves us with $ab$.
</p>
<p>
For $f(a) > b$ we can take the integral from $f^{-1}(b)$ to $a$ and estimate the rest of the area that is in $ab$ by $\int_{f^{-1}(b)}^a f(x) dx = \int_{f^{-1}(b)}^a b dx = (a - f^{-1}(b)) b $. Note that $f^{-1}(b)$ is smaller than $a$, so the area is of course positive.
Because b is strictly monotonically increasing we can estimate that the area is even bigger than the proposed integral:
</p>
\begin{eqnarray}
ab = (a - f^{-1}(b)) b + f^{-1}(b)*b  \lt \int_{f^{-1}(b)}^a f(x) dx + f^{-1}(b)*b.
\end{eqnarray}
Analog follows $f(a) < b$ by
\begin{eqnarray}
ab = -b(f^{-1}(b)-a) + f^{-1}(b)*b  \lt - \int_a^{f^{-1}(b)} f(x) dx + f^{-1}(b)*b = \int_{f^{-1}(b)}^a f(x) dx + f^{-1}(b)*b.
\end{eqnarray}

<ol style="text-align:right;">
<li><a href="https://de.wikibooks.org/wiki/Beweisarchiv:_Analysis:_Ungleichungen:_Young'sche_Ungleichung">wikipedia.de</a></li>
</ol>
