---
layout: post
title:  "Introduction to Partial Differential Equations!"
categories: pde
excerpt: Basic definitions of PDEs are covered with a little bit of physical context and calculation.
---

<h2>Differential Equations</h2>
<h3>Motivation</h3>
<p>Since i wrote my bachelor thesis on the <a href="https://github.com/MeyerFabian/snow">simulation of snow</a> i'm interested in the field of partial differential equations and their numerical solutions. <a href="https://disney-animation.s3.amazonaws.com/uploads/production/publication_asset/94/asset/SSCTS13_2.pdf">Alexey Stomakhin et al.</a> proposed the material point method. </p>
They made use of a finite element solver to compute lagrangian particles in a uniform grid. The hybrid use of Lagrangian particles and a regular cartesian grid enables solving of partial differential equations. Therefore particles are transformed to the grid. The grid velocities can be updated with the calculation of gradients in an FEM-manner (finite element method). Finally grid node velocities are weight back to the particles to move them across the scene. This method is coupled with a constitutive model to cover the dynamic nature of snow. This includes collisions and breaking. In the next blog posts i try to understand and learn more about partial differential equations and what methods are generally used to solve them to dig deeper into the math around the material point method. Following image shows the Stanford-Bunny simulated by my bachelor thesis.

<figure>
<img width="800px" src="{{site.url}}/image/mpm.jpg" />
</figure>
<h3 id="def:diff">Definition</h3>
<p>
A <b>Differential Equation</b> is of form
\begin{eqnarray}\label{eq:differential}
y' + 2xy = 0;
\end{eqnarray}

where the equation consists of independent variables ($x$),
functions or dependent variables ($y$) and derivations ($y'$).
Equation (\ref{eq:differential}) is a <b>differential equation of order one</b>
or a <b>first-order differential equation</b> because its highest
derivate is of order one. Similiarly a <b>differential equation of ordner n</b>
is a differential equation with the highest derivate being of order n.
A commonly used notation for general differential equations is:
\begin{eqnarray}
F(x,y,y',...,y^{(n)})= F(x,y(x),y'(x),...,y^{(n)}(x)=0.
\end{eqnarray}
</p>
<h3>Example</h3>
<p>
A trivial solution for the equation (\ref{eq:differential}) is $y= C_1 * e^{-x^2}$. Where $C_1$ can be of any constant value. That this holds true can be easily shown:
\begin{eqnarray}
\frac{d}{dx}(C_1 * e^{-x^2})+C_1*2xe^{-x^2}=-C_1*2xe^{-x^2}+C_1*2xe^{-x^2} = 0.
\end{eqnarray}
</p>
<h4>Definition</h4>
An <b>Ordinary Differential Equation</b> for the function $y$ only depends on a single (independent) variable $x$. Consequently equation (1) is an ordinary differential equation. Mostly the derivate is denoted by the Leibniz-Notation: $d$.

An Equation is called <b>Partial Differential Equation</b> if the function $u$ consists of more than one (independent) variable its depending on. Take for instance the equation:
\begin{eqnarray}\label{eq:partial}
\frac{\partial u}{\partial t} = \frac{\partial^2 u}{\partial x^2}+ \frac{\partial^2 u}{\partial y^2}-u.
\end{eqnarray}
The function $u(t,x,y)$ is dependent on three (independent) variables and is therefore a partial differential equation. Following previous <a href="#def:diff">definition </a> we can furthermore say it is a second-order partial differential equation. Interchangeably to denote a derivate using $d$ is $\partial$ in a partial differential equation. Even shorter is the subscript notation, which converts equation (\ref{eq:partial}) to:
\begin{eqnarray}
u_t= u_{xx}+u_{yy}-u.
\end{eqnarray}
The subscript and amount of subscripts indicate the respective partial derivative and order. An <b>equilibrium equation</b> models an unchanging physical system, only dependent on space (not time in particular). A <b>dynamical equation</b> uses space coordinates and additionaly varies with time.
<h3>Remark</h3>
Most applications make use of partial differential equation of first- or second-order. Third-order equation model waves. Fourth-order can describe elasticity, particularly plate and beam mechanics. Equation of order 5 or higher are very rare.

<h2> Classical Solution </h2>
<div>
<h3> Definition </h3>
<p> A (classical) <i>solution</i> to a differential equation is a sufficiently enough smooth function $u$ at every point of its domain $D$.
$D$ will be an <i>open</i> subset, usually <i>connected</i> and often particularly in equilibrium equation <i>bounded</i> with a reasonably nice <i>boundary</i>, denoted by $\partial D$.
A solution is called smooth when a function $u$ is $n$ times differentiable on $D$, where $n$ is the order of the partial differential equation.
</p>
<h3> Remark </h3>
<p> <i> open </i>: in an open set $X$ you can put an open ball $B_x(r)$ on every $x \in X$ with r > 0. For instance: In $\mathbb{R}$ an open subset X would be the open interval $x \in ]0;1[ $.
</p>
<p> <i> connected </i>: $X$ cannot be subdivided into two open, disjoint(!) sets (because the exacty boundary between these two sets would be missing if the set is connected or they would be not disjoint)
</p>
<p>
<p> <i> bounded </i>: M $\subseteq$ X and there exists a supremum, infimum $a,b \in M$ (every value of X wont be higher, lower than $a$/$b$)
</p>
<p> <i> boundary </i>: M $\subseteq$ X and open, an open ball $B_x(r)$  placed on a boundary point $x \in X$ always consists of at least one point in M and one not in M
</p>
<h3> Example </h3>
<p>
A classical solution to the heat equation:
\begin{eqnarray}
\frac{\partial u}{\partial t}= \frac{\partial^2 u}{\partial x^2}
\end{eqnarray}
is a function $u(t,x)$, defined on a domain $D \subset \mathbb{R}$, such that all of the partial derivatives until order 2
</p>
<p> $u,\frac{\partial u}{\partial t},\frac{\partial u}{\partial x},\frac{\partial^2 u}{\partial t^2},\frac{\partial^2 u}{\partial x \partial t} = \frac{\partial^2 u}{\partial t \partial x}, \frac{\partial^2 u}{\partial x^2}$	  
</p>
<p>
are well defined and continous at every point $(t,x) \in D$. We require continuity of all the partial derivatives of order $\leq 2$.
</p>
<p> The following function satisfies the heat equation (<b>product rule!</b>):</p>
\begin{eqnarray}
u(t,x) = \frac{e^{-x^2/4t}}{2 \sqrt{\pi t}}, \frac{\partial u}{\partial t} =  \frac{\partial^2 u}{\partial x^2} = (\frac{x^2}{4t^2}-\frac{1}{2t})\frac{e^{-x²/4t}}{2 \sqrt{\pi t}} = (\frac{x^2}{2t}-1)\frac{\sqrt{t}e^{-x²/4t}}{\sqrt{\pi}}
\end{eqnarray}


<ol style="text-align:right;">
<li> Walter, W., Ordinary Differential Equations, Springer New York, 1998</li>
<li> Olver, P., Introduction to Partial Differential Equations, Springer International Publishing, 2013</li>
</ol>
