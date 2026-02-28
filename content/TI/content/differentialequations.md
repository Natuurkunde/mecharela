(app:solvingde)=
# Solving differential equations

```{index} differential equations
```
A *differential equation* is an equation which contains derivatives of the function to be determined. They can be very simple. For example, you may be given the (constant) velocity of a car, which is the derivative of its position, which we'd write mathematically as:

$$
v = \frac{\mathrm{d}x}{\mathrm{d}t} = v_0.
$$ (constspeeddv)

To determine where the car ends up after one hour, we need to solve this differential equation. We also need a second piece of information: where the car was at some reference time (usually $t=0$), the *initial condition*. If $x(0) = 0$, you don't need advanced maths skills to figure out that $x(1\;\text{hour}) = v_0 \cdot (1\;\text{hour})$. Unfortunately, things aren't usually this easy.

Before we proceed to a few techniques for solving differential equations, we need some terminology. The *order* of a differential equation is the order of the highest derivative found in the equation; equation&nbsp;{eq}`constspeeddv` is thus of first order. A differential equation is called *ordinary* if it only contains derivatives with respect to one variable, and *partial* if it contains derivatives to multiple variables. The equation is *linear* if it does not contain any products of (derivatives of) the unknown function. Finally, a differential equation is *homogeneous* if it only contains terms that contain the unknown function, and *inhomogeneous* if it also contains other terms. Equation&nbsp;{eq}`constspeeddv` is ordinary and inhomogeneous, as the $v_0$ term on the right does not contain the unknown function&nbsp;$x(t)$. In the sections below, we discuss the various cases you'll encounter in this book; there are many others (many of which can't be solved explicitly) to which a whole subfield of mathematics is dedicated.

(app:folode)=
## First-order linear ordinary differential equations

Suppose we have a general equation of the form

$$
a(t) \frac{\mathrm{d}x}{\mathrm{d}t} + b(t) x(t) = f(t),
$$ (firstorderdv)

where $a(t)$, $b(t)$ and $f(t)$ are known functions of $t$, and $x(t)$ is our unknown function. Equation&nbsp;{eq}`firstorderdv` is a first-order, ordinary, linear, inhomogeneous differential equation. In order to solve it we will use two techniques that are tremendously useful: separation of variables and separation into homogeneous and particular solutions.

Suppose we had $f(t) = 0$. Then, if we had two solutions $x_1(t)$ and $x_2(t)$ of equation&nbsp;{eq}`firstorderdv`, we could construct a third as $x_1(t) + x_2(t)$ (or any linear combination of $x_1(t)$ and $x_2(t)$), since the equation is linear. Now since $f(t)$ is not zero, we can't do this, but we can do something else. First, we find the most general solution to the equation where $f(t) = 0$, which we call the *homogeneous solution* $x_\mathrm{h}(t)$. Second, we find a solution (any at all) of the full equation&nbsp;{eq}`firstorderdv`, which we call the *particular solution*&nbsp;$x_\mathrm{p}(t)$. The full solution is then the sum of these two solutions, $x(t) = x_\mathrm{h}(t) + x_\mathrm{p}(t)$. You may worry that there may be multiple particular solutions: how would we pick the 'right' one? Fortunately, we don't need to worry: the homogeneous solution will contain an unknown variable, which will be set by the initial condition. Changing the particular solution will  change the value of the variable, such that the final solution will be the same and satisfy both the differential equation and the initial condition.

To find the solution to the homogeneous equation

$$
a(t) \frac{\mathrm{d}x_\mathrm{h}}{\mathrm{d}t} + b(t) x_\mathrm{h}(t) = 0,
$$ (firstorderdvhom)

we're going to use a technique called *separation of variables*. There are two variables in this system: the independent parameter&nbsp;$t$ and the dependent parameter&nbsp;$x$. The trick is to get everything depending on&nbsp;$t$ on one side of the equals sign, and everything depending on&nbsp;$x$ on the other. To do so, we're going to treat&nbsp;$\mathrm{d}x/\mathrm{d}t$ as if it were an actual fraction<sup>[^1]</sup>. In that case, it's not hard to see that we can re-arrange equation&nbsp;{eq}`firstorderdvhom` to

$$
\frac{1}{x_\mathrm{h}} \mathrm{d}x_\mathrm{h} = - \frac{b(t)}{a(t)} \mathrm{d}t.
$$ (firstorderdvseparated)

By itself, equation&nbsp;{eq}`firstorderdvseparated` means little, but if we integrate both sides, we get something that makes sense:

$$
\int \frac{1}{x_\mathrm{h}} \mathrm{d}x_\mathrm{h} = \log(x_\mathrm{h}) + C = - \int \frac{b(t)}{a(t)} \mathrm{d}t
$$ (firstorderdvintegrated)

or

$$
x_\mathrm{h}(t) = A \exp \left[ - \int \frac{b(t)}{a(t)} \mathrm{d}t \right],
$$ (firstorderdvhomsol)

where $A = \exp(C)$ is an integration constant (the unknown constant that will be set by our initial condition). Of course, in principle it may not be possible to evaluate the integral in equation&nbsp;{eq}`firstorderdvhomsol`, but even then the solution is valid. In practice, you'll often encounter situations in which $a(t)$ and $b(t)$ are simple functions or even constants, and the evaluation of the integral is straightforward.

Now that we have our homogeneous solution, we still need a particular one. Sometimes you're lucky, and you can easily guess one - for instance one in which $x_\mathrm{p}(t)$ doesn't depend on $t$ at all. In case you're not lucky, there's are two other techniques you may try, either using *variation of constants* or finding an *integrating factor*. To demonstrate variation of constants, we'll pick a specific example, to not get lost in a bunch of abstract functions. Let $a(t) = a$ be a constant and $b(t) = b t$ be linear. The homogeneous solution then becomes $x_\mathrm{h}(t) = A \exp\left[-\frac12 \frac{b}{a} t^2 \right]$. The constant we're going to vary is our integration constant $A$, so our guess for the particular solution will be

$$
x_\mathrm{p}(t) = A(t) \exp\left[-\frac12 \frac{b}{a} t^2 \right].
$$ (partsolvarconstguess)

We substitute&nbsp;{eq}`partsolvarconstguess` back into the full differential equation&nbsp;{eq}`firstorderdv`, which gives:

$$
\left[ a \frac{\mathrm{d}A}{\mathrm{d}t} - a A(t) \frac{b t}{a} + b t A(t) \right] \exp\left[-\frac12 \frac{b}{a} t^2 \right] = a \frac{\mathrm{d}A}{\mathrm{d}t} \exp\left[-\frac12 \frac{b}{a} t^2 \right] = f(t).
$$

A big part of the left-hand side thus cancels, and that's not a coincidence - that's because it is based on the homogeneous equation. What remains is a differential equation in $A(t)$ that can be trivially solved by direct integration:

$$
A(t) = \int \frac{\mathrm{d}A}{\mathrm{d}t} \mathrm{d}t = \frac{1}{a}\int f(t) \exp\left[\frac12 \frac{b}{a} t^2 \right] \mathrm{d}t.
$$ (varconstsol)

Again, it may not be possible to evaluate the integral in equation&nbsp;{eq}`varconstsol`, but in principle the solution could be inserted in equation&nbsp;{eq}`partsolvarconstguess` to give us our particular solution, and the whole differential equation will be solved.

Alternatively, we may try to find an *integration factor* for equation&nbsp;{eq}`firstorderdv`. This means that we try to re-write the left hand side of the equation as a total derivative, after which we can simply integrate to get the solution. To do so, we first divide the whole equation by $a(t)$, then look for a function $\mu(t)$ that satisfies the condition that

$$
\frac{\mathrm{d}}{\mathrm{d}t} \left[ \mu(t) x(t) \right] = \mu(t) \frac{\mathrm{d}x}{\mathrm{d}t} + x(t) \frac{\mathrm{d}\mu}{\mathrm{d}t} = \mu(t) \frac{\mathrm{d}x}{\mathrm{d}t} + \mu(t) \frac{b(t)}{a(t)} x(t),
$$ (integrationfactorcondition)

from which we can read off that we need to solve the homogeneous equation

$$
\frac{\mathrm{d}\mu}{\mathrm{d}t} = \frac{b(t)}{a(t)} \mu(t).
$$ (integrationfactorode)

We can solve&nbsp;{eq}`integrationfactorode` by separation of constants, which gives us

$$
\mu(t) = \exp \left( \int \frac{b(t)}{a(t)} \mathrm{d}t \right),
$$ (integrationfactor)

where we set the integration constant to one, as it drops out of the equation for $x(t)$ anyway. With this function $\mu(t)$, we can rewrite equation&nbsp;{eq}`firstorderdv` as

$$
\frac{\mathrm{d}}{\mathrm{d}t} \left[ \mu(t) x(t) \right] = \mu(t) \frac{f(t)}{a(t)},
$$ (firstorderdvwithintegrationfactor)

which we can integrate to find&nbsp;$x(t)$:

$$
x(t) = \frac{1}{\mu(t)} \int \mu(t) \frac{f(t)}{a(t)} \mathrm{d}t.
$$ (firstorderdvsolwithintegrationfactor)

(app:solode)=
## Second-order linear ordinary differential equations with constant coefficients

Second order ordinary differential equations are essential for the study of mechanics, as its central equation, Newton's second law of motion (equation&nbsp;{eq}`N2`) is of this type. In the case that the equation is also linear, we have some hopes of solving it analytically. There are several examples of this type of equation in the main text, especially in {numref}`sec:eomsolutions`, where we solve the equation of motion resulting from Newton's second law for three special cases, and {numref}`sec:oscillation`, where we study a number of variants of the harmonic oscillator.

For the case that the equation is homogeneous and has constant coefficients, we can write down the general solution<sup>[^2]</sup>. The equation to be solved is of the form

$$
a \frac{\mathrm{d}^2 x}{\mathrm{d}t^2} + b \frac{\mathrm{d}x}{\mathrm{d}t} + c x(t) = 0.
$$ (secondorderodeconstcoeff)

For the case that $a=0$, we retrieve a first-order differential equation, whose solution is an exponential (as can be found by separation of variables and integration): $x(t) = C \exp(c t / b)$. In many cases an exponential is also a solution of equation&nbsp;{eq}`secondorderodeconstcoeff`. To figure out which exponential, let's start with the trial function (or 'Ansatz') $x(t) = \exp(\lambda	 t)$, where $\lambda$ is an unknown parameter. Substituting this Ansatz into equation&nbsp;{eq}`secondorderodeconstcoeff` yields the *characteristic polynomial* for this ode:

$$
a \lambda^2 + b \lambda + c = 0,
$$ (secondorderodecharpol)

which almost always has two solutions:

$$
\lambda_\pm = -\frac{b}{2a} \pm \frac{\sqrt{b^2-4ac}}{2a}.
$$ (secondorderodesol1)

Note that the solutions can be real or complex. If there are two of them, we can write the general solution<sup>[^3]</sup> of equation&nbsp;{eq}`secondorderodeconstcoeff` as a linear combination of the Ansatz with the two cases:

$$
x(t) = A e^{\lambda_{+}t} + B e^{\lambda_{-}t},
$$ (secondorderodesol2)

where $A$ and $B$ are set by either initial or boundary conditions. Since the $\lambda_\pm$ may be complex, so may $A$ and $B$; it's their combination that should give a real number (as $x(t)$ is real), see {numref}`pb:secondorderodesolutions`a.

In the case that equation&nbsp;{eq}`secondorderodesol1` gives only one solution, the corresponding exponential function is still a solution of equation&nbsp;{eq}`secondorderodeconstcoeff`, but it is not the most general one, as we only can put a single undetermined constant in front of it. We therefore need a second, independent solution. To guess one, here's a third useful trick<sup>[^4]</sup>: take the derivative of our known solution, $e^{\lambda t}$, with respect to the parameter $\lambda$. This gives a second Ansatz: $t e^{\lambda t}$, where $\lambda = -b/2a$. Substituting this Ansatz into equation&nbsp;{eq}`secondorderodeconstcoeff` for the case that $c = b^2/2a$, we find:

$$
\frac{\mathrm{d}^2 x}{\mathrm{d}t^2} + b \frac{\mathrm{d}x}{\mathrm{d}t} + \frac{b^2}{2a} x(t) = a \left( -\frac{b}{a} + \frac{b^2}{4a^2} t \right) e^{-\frac{bt}{2a}} + b \left(1 - \frac{b}{2a} t \right) e^{-\frac{bt}{2a}} + \frac{b^2}{4a} t e^{-\frac{bt}{2a}} = 0,
$$

so our Ansatz is again a solution. For this special case, the general solution is therefore given by

$$
x(t) = A e^{-\frac{bt}{2a}} + B t e^{-\frac{bt}{2a}}.
$$ (secondorderodesol3)

In {numref}`sec:dampedoscillator`, where we discuss the damped harmonic oscillator, the special case corresponds to the critically damped oscillator. We get an underdamped oscillator when the roots of the characteristic polynomial are complex, and an overdamped one when they are real.

## Second-order linear ordinary differential equations of Euler type
There's a second class of linear ordinary differential equations that we can solve explicitly: those of Euler (or Cauchy-Euler) type, where the coefficient in front of a derivative contains the variable to the power of the derivative, i.e., for a second-order differential equation, we have as the most general form:

$$
a x^2 \frac{\mathrm{d}^2 y}{\mathrm{d}x^2} + b x \frac{\mathrm{d}y}{\mathrm{d}x} + c y(x) = 0.
$$ (secondorderodeEuler)

Note that we are now solving for $y(x)$; we do so because this type of equation typically occurs in the context of position- rather than time-dependent functions. An example is the Laplace equation ($\nabla^2 y = 0$) in polar coordinates. Like for the second order ode with constant coefficients, the ode of Euler type can be generalized to higher-order equations.

There are (at least) two ways to solve equation&nbsp;{eq}`secondorderodeEuler`: through an Ansatz, and through a change of variables. For the Ansatz, note that for any polynomial, the derivative of each term reduces the power by one, and here we're multiplying each such term with the variable to the power the number of derivatives<sup>[^5]</sup>. This suggests we simply try a polynomial, so our Ansatz here will be $y(x) = x^n$. Substituting in equation&nbsp;{eq}`secondorderodeEuler` gives:

$$
a x^2 n(n-1) x^{n-2} + b x n x^{n-1} + c x^n = [a n (n-1) + b n + c] x^n = 0,
$$

so we get another second order polynomial to solve, this time in $n$:

$$
a n^2 + (b-a) n + c = 0 \quad \Rightarrow \quad n_\pm = \frac12 - \frac{b}{2a} \pm \frac12 \sqrt{(a-b)^2-4ac}.
$$ (Eulerodesol1)

If the roots in equation&nbsp;{eq}`Eulerodesol1` are both real (the most common case in physics problems), we have two independent solutions, and we are done. If the roots are complex, we also have two independent solutions, though they involve complex powers of $x$; like for the equation with constant coefficients, we can rewrite these as real functions with Euler's formula. For the case that we have only one root, we again apply our trick to get a second: we try $\mathrm{d}x^n / \mathrm{d}n = x^n \ln(x)$, which turns out to be indeed a solution, and the general solution is again a linear combination of the two solutions found (see {numref}`pb:secondorderodesolutions`).

Alternatively, we could have solved equation&nbsp;{eq}`secondorderodeEuler` by a change of variables. Although this method is occasionally useful (and so it's good to be aware of its existence), there is no systematic way of deriving which change of variables will do the trick, so you'll have to go by trial-and-error (without a priori guarantee of success). In this case, this process leads to the following substitution:

$$
x = e^t, \quad y(x) = y\left(e^t\right) \equiv \phi(t),
$$ (Eulerodesol4)

where we introduce $\phi(t)$ for convenience. Taking derivatives of $y(x)$ with the chain rule gives

$$
\frac{\mathrm{d}y}{\mathrm{d}x} = \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d}t}{\mathrm{d}x} = \frac{1}{x} \frac{\mathrm{d}\phi}{\mathrm{d}t}, \quad \frac{\mathrm{d}^2 y}{\mathrm{d}x^2} = \frac{1}{x^2} \left( \frac{\mathrm{d}^2\phi}{\mathrm{d}t^2} - \frac{\mathrm{d}\phi}{\mathrm{d}t} \right),
$$ (Eulerodesol5)

where we kept the $1/x$ and $1/x^2$ as they'll cancel the coefficients in equation&nbsp;{eq}`secondorderodeEuler`. Substituting&nbsp;{eq}`Eulerodesol4` and&nbsp;{eq}`Eulerodesol5` in equation&nbsp;{eq}`secondorderodeEuler`, we get

$$
a \frac{\mathrm{d}^2\phi}{\mathrm{d}t^2} + (b-a) \frac{\mathrm{d}\phi}{\mathrm{d}t} + c \phi(t) = 0,
$$ (Eulerodesol6)

which is a second order differential equation with constant coefficients, and thus of the form given in  equation&nbsp;{eq}`secondorderodeconstcoeff`. We therefore know how to find its solutions, and can use equation&nbsp;{eq}`Eulerodesol4` to transform those solutions back to functions&nbsp;$y(x)$.

(app:odereductionoforder)=
## Reduction of order

If you find yourself with a non-homogeneous second order differential equation where the homogeneous equation either has constant coefficients or is of Euler type, you can again use the technique of variation of constants to find a particular solution. A similar technique, known as reduction of order, may help you find solutions to a second (or higher) order equation where the coefficients are not constant. In order to be able to use this technique, you need to know a solution to the homogeneous equation, so it is not as universally applicable as the techniques in the previous two sections, but still frequently very helpful.

Let us write the general non-homogeneous second-order linear differential equation as

$$
\frac{\mathrm{d}^2 y}{\mathrm{d}x^2} + p(t) \frac{\mathrm{d}y}{\mathrm{d}x} + q(x) y(x) = r(x).
$$ (secondorderodeinhom)

Note that this is the most general form: if there is a coefficient (constant or otherwise) in front of the second derivative, we simply divide the whole equation by that coefficient and redefine the coefficients to match equation&nbsp;{eq}`secondorderodeinhom`. Now suppose we have a solution $y_1(x)$ of the homogeneous equation (so for the case that $r(x) = 0$). As the equation is homogeneous, for any constant $v$ the function $v y_1(x)$ will also be a solution. As an Ansatz for the second solution, we'll try a variant of variation of constants, and take

$$
y_2(x) = v(x) y_1(x),
$$ (inhomodesol1)

where $v(x)$ is an arbitrary function. Substituting&nbsp;{eq}`inhomodesol1` back into&nbsp;{eq}`secondorderodeinhom`, we find

$$
y_1(x) \frac{\mathrm{d}^2 v}{\mathrm{d}x^2} + \left[ 2 \frac{\mathrm{d}y_1}{\mathrm{d}x} + p(x) y_1(x) \right] \frac{\mathrm{d}v}{\mathrm{d}x} + \left[ \frac{\mathrm{d}^2 y_1}{\mathrm{d}x^2} + p(x) \frac{\mathrm{d}y_1}{\mathrm{d}x} + q(x) y_1(x) \right] v(x) = r(x).
$$ (inhomodesol2)

We recognize the prefactor of $v(x)$ as exactly the homogeneous equation, which $y_1(x)$ satisfies, so this term vanishes. Now defining $w(x) = \mathrm{d}v / \mathrm{d}x$, we are left with a first-order equation for $w(x)$:

$$
y_1(x) \frac{\mathrm{d}w}{\mathrm{d}x} + \left[ 2 \frac{\mathrm{d}y_1}{\mathrm{d}x} + p(x) y_1(x) \right] w(x) = r(x).
$$ (secondorderodereduced)

Equation&nbsp;{eq}`secondorderodereduced` is a first-order linear differential equation, and can be solved by the techniques from {numref}`app:folode`. Integrating the equation $w(x) = \mathrm{d}v / \mathrm{d}x$ then gives us $v(x)$, and hence the second solution&nbsp;{eq}`inhomodesol1` of the (inhomogeneous) second order differential equation.

(app:odepowerseries)=
## Power series solutions

If none of the techniques in the sections above apply to your differential equation, there's one last Ansatz you can try: a power series expansion of your solution. To illustrate, we'll again pick a concrete example: Legendre's differential equation, given by

$$
\frac{\mathrm{d}}{\mathrm{d}x} \left[ (1-x^2) \frac{\mathrm{d}y}{\mathrm{d}x} \right] + n(n+1) y(x) = (1-x^2) \frac{\mathrm{d}^2y}{\mathrm{d}x^2} - 2x \frac{\mathrm{d}y}{\mathrm{d}x} + n(n+1) y(x) = 0,
$$ (Legendreode)

where $n$ is an integer. As an Ansatz for the solution, we'll try a power series expansion of $y(x)$:

$$
y(x) = \sum_{k=0}^\infty a_k x^k.
$$ (ypowerseries)

Our task is now to find numbers $a_k$ (many of which may be zero) such that&nbsp;{eq}`ypowerseries` is a solution of&nbsp;{eq}`Legendreode`. Fortunately, we can simply substitute our trial solution and re-arrange to get

```{math}
:label: Legendreodepowerseries
\begin{align*}
0 &= (1-x^2) \frac{\mathrm{d}^2}{\mathrm{d}x^2} \left( \sum_{k=0}^\infty a_k x^k \right) - 2 x \frac{\mathrm{d}}{\mathrm{d}x} \left( \sum_{k=0}^\infty a_k x^k \right) + n(n+1) \sum_{k=1}^\infty a_k x^k \\
&= (1-x^2) \left( \sum_{k=0}^\infty k (k-1) a_k x^{k-2} \right) - 2 x \left( \sum_{k=0}^\infty k a_k x^{k-1} \right) + n(n+1) \sum_{k=1}^\infty a_k x^k \\
&= \sum_{k=0}^\infty \left[ \left( -k(k-1) - 2 k + n(n+1) \right) a_k x^k + k (k-1) a_k x^{k-2}\right] \\
&= \sum_{k=0}^\infty \left[ \left( -k(k+1) + n(n+1) \right) a_k + (k+2)(k+1) a_{k+2} \right] x^k,
\end{align*}
```

where in the last line, we 'shifted' the index of the last term<sup>[^6]</sup>. We do so in order to get at an expression for the coefficient of $x^i$ for any value of $k$. As the functions $x^k$ are linearly independent<sup>[^7]</sup> (i.e., you can't write $x^k$ as a linear combination of other functions $x^m$ where $m \neq k$), the coefficient of each of the powers in the sum in equation&nbsp;{eq}`Legendreodepowerseries`D has to vanish for the sum to be identically zero. This gives us a *recurrence relation* between the coefficients $a_k$:

$$
a_{k+2} = \frac{k(k+1)-n(n+1)}{(k+2)(k+1)} a_k.
$$ (Legendrerecurrence)

Given the values of $a_0$ and $a_1$ (the two degrees of freedom that our second-order differential equation allows us), we can repeatedly apply equation&nbsp;{eq}`Legendrerecurrence` to get all coefficients. Note that for $k=n$ the coefficient equals zero. Therefore, if for an even value of $n$, we set $a_1 = 0$, and for an odd value of $n$, we set $a_0 = 0$, we get a finite number of nonzero coefficients. The resulting solutions are polynomials, characterized by the number $n$; in this case, they're known as the *Legendre polynomials*, typically denoted $P_n(x)$, and normalized (by setting the value of the remaining free coefficient) such that $P_n(1) = 1$. {numref}`table:Legendrepolynomials` lists the first five, which are also plotted in {numref}`fig:LegendreBessel`a.

```{table} Legendre polynomials.
:name: table:Legendrepolynomials
| $n$ | $P_n(x)$ |
| :--: | :--: |
| $0$ | $1$ |
| $1$ | $x$ |
| $2$ | $\frac12 (3x-1)$ |
| $3$ | $\frac12 (5x^3 - 3x)$ |
| $4$ | $\frac18 (35 x^4 - 30 x^2 +3)$ |
| $5$ | $\frac18 (63 x^5 - 70 x^3 + 15 x)$ |
```
The first five (and zeroth, for good measure) Legendre polynomials, the solutions of equation&nbsp;{eq}`Legendreode` for the given value of $n$ and the appropriate choice of $a_0$ and $a_1$.

Legendre polynomials have many other interesting properties (many of which can be found in either math textbooks or on their Wikipedia page). They occur frequently in physics, for example in solving problems involving Newtonian gravity or Laplace's equation from electrostatics.

If we replace the $n(n+1)$ factor in the Legendre differential equation with an arbitrary number&nbsp;$\lambda$, the series solution remains a solution, but it no longer terminates<sup>[^8]</sup>. There are many other differential equations that lead to both infinite series and polynomial solutions. A well-known example is the Bessel differential equation:

$$
x^2 \frac{\mathrm{d}^2 y}{\mathrm{d}x^2} + x \frac{\mathrm{d}y}{\mathrm{d}x} + (x^2-n^2) y(x) = 0.
$$ (Besselode)

The solutions to this equation are known as the Bessel functions of the first and second kind (see {numref}`pb:Besselfunctions`, where you'll prove that for these functions the series never terminates). These functions generalize the sine and cosine function and occur in the vibrations of two-dimensional surfaces. Other examples include the Hermite and Laguerre polynomials, which feature in quantum mechanics, and Airy functions, which you can encounter when studying optics.

```{figure} images/appendices/LegendreBessel.svg
:name: fig:LegendreBessel
Solutions to the Legendre and Bessel differential equations. (a) The first five Legendre polynomials ({numref}`table:Legendrepolynomials`). Note that the polynomials with even $n$ are all even, and those with odd $n$ are all odd. (b-c) The first five Bessel functions of the first (b) and second (c) kind.
```

## Problems
````{exercise} Solutions of a second-order ordinary differential equation
:label: pb:secondorderodesolutions
:class: dropdown
1.  Suppose we have a solution of equation&nbsp;{eq}`secondorderodeconstcoeff` where the roots $\lambda_\pm$ of the characteristic polynomial (equation&nbsp;{eq}`secondorderodesol1`) are complex, so $\lambda_\pm = \alpha \pm i \beta$. Rewrite the general solution&nbsp;{eq}`secondorderodesol2` in real functions with real coefficients $C$ and $D$, and express $C$ and $D$ in terms of $A$ and $B$. *Hint*: use Euler's formula $e^{ix} = \cos(x) + i \sin(x)$.
1.  Suppose we have a solution of equation&nbsp;{eq}`Eulerodesol1` where the roots $n_\pm$ are complex, so $n_\pm = \alpha \pm i \beta$. To get a solution of equation&nbsp;{eq}`secondorderodeEuler` without complex numbers, we make the substitution&nbsp;$x = e^t$, so
```{math}
x^{n_\pm} = x^{\alpha \pm i \beta} = e^{\alpha t} e^{\pm i \beta t}.
```
Use Euler's formula again to rewrite the complex exponential in terms of sines and cosines, and make the back-substitution to $x$ to show that the general solution of equation&nbsp;{eq}`secondorderodeEuler` in this case is given by
```{math}
:label: Eulerodesol2
y(x) = x^\alpha \left[ A \cos\left(\beta \ln(x)\right) + \sin\left(\beta \ln(x)\right)\right].
```
1.  Suppose we have a solution of equation&nbsp;{eq}`Eulerodesol1` for which there is only a single root&nbsp;$n$. Show that the derivative of $x^n$ with respect to $n$ is in this case also a solution of equation&nbsp;{eq}`secondorderodeEuler`, and that the general solution is given by
```{math}
:label: Eulerodesol3
y(x) = x^n \left[ A + B \ln(x) \right].
```
````

```{exercise} Reduction of order
:label: pb:odereductionoforder
:class: dropdown
Use the method of reduction of order to obtain a second solution of equation&nbsp;{eq}`secondorderodeconstcoeff` for the case that the characteristic polynomial (equation&nbsp;{eq}`secondorderodesol1`) has only a single root.
```

```{exercise} Bessel functions
:label: pb:Besselfunctions
:class: dropdown
1. Use the power series technique to find a solution to Bessel's differential equation&nbsp;{eq}`Besselode`. Why doesn't the series terminate in this case? Why do you only get one family of solutions? We'll call these solutions 'Bessel functions of the first kind' and label them as $J_n(x)$ (see {numref}`fig:LegendreBessel`b).
1. Use the method of reduction of order to find a second family of solutions to the Bessel differential equation, known as 'Bessel functions of the second kind' ($Y_n(x)$, see {numref}`fig:LegendreBessel`c).
```

[^1]: If you're worried about the validity of this shortcut, consider that we could also have left $\mathrm{d}x_\mathrm{h}/\mathrm{d}t$ intact, to give $\frac{1}{x_\mathrm{h}} \mathrm{d}x_\mathrm{h}/\mathrm{d}t = - b(t)/a(t)$. Integrating both sides over time gives 
	```{math}
	\int \frac{1}{x_\mathrm{h}} \mathrm{d}x_\mathrm{h}/\mathrm{d}t \mathrm{d}t = \int \frac{1}{x_\mathrm{h}} \mathrm{d}x_\mathrm{h} = - \int \frac{b(t)}{a(t)} \mathrm{d}t,
	```
	which takes us back to equation&nbsp;{eq}`firstorderdvintegrated`.

[^2]: This approach generalizes to higher-order differential equations, though the characteristic polynomial may not be as easy to solve in the general case.

[^3]: You may wonder how we know that this is the most general solution of equation&nbsp;{eq}`secondorderodeconstcoeff`. The argument follows from the proof of the [Picard-Lindel&ouml;f theorem](https://en.wikipedia.org/wiki/Picard–Lindelof_theorem), which states that under fairly weak conditions on the ode (which are met by equation&nbsp;{eq}`secondorderodeconstcoeff`), there exists a single unique solution, which depends on as many free parameters as the order of the equation. For example, if you know the position and its derivative at $t=0$, everything else is fixed: equation&nbsp;{eq}`secondorderodeconstcoeff` gives you the value of the second derivative, from which you can calculate the value of the derivative and the function itself at some later time&nbsp;$\Delta t$, and so on. As equation&nbsp;{eq}`secondorderodesol2` has two unknowns, we've used up all our degrees of freedom in determining them, and as the solution is unique, it cannot contain another term.

[^4]: Alternatively, you could use a variant of variation of constants, known as reduction of order; see {numref}`app:odereductionoforder` and {numref}`pb:odereductionoforder`.

[^5]: An admittedly complicated sentence, but if you find yourself wondering about it, just press on, and return later, when it will hopefully be obvious.

[^6]: Note that we can do this because the index $k$ is a 'dummy', i.e., an index that we sum over and thus does not appear in the end answer. We could just as well have called it $j$, or we could define $j=k-1$, and re-write the sum over $k$ as
	```{math}
	\sum_{k=0}^\infty a_k x^k = \sum_{j=-1}^\infty a_{j+1} x^{j+1} = \sum_{j=-1}^\infty a_{j+1} x^{j+1}.
	```
	Therefore
	```{math}
	\sum_{k=0}^\infty k a_k x^{k-1} = \sum_{j=-1}^\infty (j+1) a_{j+1} x^j = \sum_{j=0}^\infty (j+1) a_{j+1} x^j,
	```
	where in the last equality we drop the term with $j=-1$ as it is identically zero. Applying this concept twice on the last term of&nbsp;{eq}`Legendreodepowerseries`C and then relabeling $j=k$ in the result gives us equation&nbsp;{eq}`Legendreodepowerseries`D.

[^7]: Or 'orthogonal'. The proof of this property of the polynomial functions can be found in many analysis and linear algebra books.

[^8]: Except, of course, if you choose $\lambda = n(n+1)$.

