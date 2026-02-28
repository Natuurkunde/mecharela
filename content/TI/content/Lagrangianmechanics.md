(ch:Lagrangianmechanics)=
# Lagrangian mechanics*

In the preceding chapters, we studied mechanics based on Newton's laws of motion. From these laws we can derive equations of motion that describe the dynamics of particles under the action of forces or torques. We also found that the laws of motion lead to three conservation laws. In this chapter, we will construct and apply an alternative approach, which will also allow us to derive conservation laws and equations of motion, in a somewhat more general way than we did so far. In particular, the method will allow us to easily find the equation of motion of a system with constraints or systems in which the choice of coordinates is not obvious,  and identify the relation between conserved quantities and the symmetries of a system.

(sec:EulerLagrange)=
## Hamilton's principle and the Euler-Lagrange equations

To illustrate the basic idea of Lagrangian mechanics, we start with a simple case: a particle of mass $m$ that can move in one dimension under the action of a conservative force $F(x)$. Writing the force as the derivative of a potential energy $U(x)$, Newton's second law of motion gives us the equation of motion for this system:

$$
m \ddot{x} = - \frac{\mathrm{d}U(x)}{\mathrm{d}x}.
$$ (simpleeom)

```{index} Lagrangian
```
As we've seen in {numref}`ch:energy`, the sum of the kinetic energy&nbsp;$K = \frac12 m \dot{x}^2$ and the potential energy&nbsp;$U$ of the particle is conserved. Here we'll work with the difference between the kinetic and potential energy, known as the *Lagrangian*:

$$
\mathcal{L}(x, \dot{x}) = K - U = \frac12 m \dot{x}^2 - U(x).
$$ (defLagrangian)

In equation&nbsp;{eq}`defLagrangian` we've written the Lagrangian<sup>[^1]</sup> as a function of the position&nbsp;$x$ and the velocity&nbsp;$\dot{x}$ of the particle. Note that, although the potential and kinetic energy (and thus the Lagrangian) do not depend *explicitly* on time (there is no $t$ in their definition), they do depend on time *implicitly* because $x(t)$ and $\dot{x}(t)$ do; ultimately, time is the only free parameter in this system. By writing $L$ as a function of the functions $x(t)$ and $\dot{x}(t)$, we have created a *functional*: a function of a function.

```{index} action functional
```
Because of the (implicit) time dependence of $\mathcal{L}$, we can integrate it over time; this integral gives us another functional of $x$, the *action*:

$$
S[x] = \int_0^T \mathcal{L}(x(t), \dot{x}(t)) \,\mathrm{d}t.
$$ (defaction)

In equation&nbsp;{eq}`defaction` we used the square brackets to indicate that $S$ is a functional rather than a function; by substituting the explicit dependence of $x(t)$ and $\dot{x}(t)$ on time, $\mathcal{L}$ in equation&nbsp;{eq}`defaction` has become an ordinary function of time.

Equation&nbsp;{eq}`defaction` allows us to calculate a value for the action for any trajectory $x(t)$ that takes a particle from a point $x_A$ to a point $x_B$ in a time interval $T$. *Newtonian* mechanics tells us that, once we know all the forces, there are only two conditions we can freely select (because Newton's second law of motion is of second order), which, once set, uniquely determine the particle's path. So far, we've usually set initial conditions: the position and velocity of a particle at $t=0$, but we could also have set boundary conditions (e.g. the position of the particle at $t=0$ and $t=T$), as we do here. As we know<sup>[^2]</sup> that Newtonian mechanics gives correct predictions about the path taken, calculating an action for alternative paths may seem like a rather futile exercise<sup>[^3]</sup>. However, it turns out that the actual path is always at an extremum of the action (known as a *stationary point* for functionals). The foundation of Lagrangian mechanics lies in exactly this property, which can be formulated as an alternative axiom:
```{prf:axiom} Hamilton's principle
:label: axiom:Hamiltonsprinciple
The time evolution $x(t)$ of a mechanical system corresponds to a stationary point of the action functional&nbsp;{eq}`defaction`.
```

To find the stationary point(s) of the action functional, we need to find a function $x(t)$ for which the value of $S[x]$ is at an extremum. Perhaps surprisingly, doing so is fairly straightforward. Suppose we have a function $x(t)$ for which $S[x]$ is at an extremum, and we have a collection of other functions $h(t)$ that satisfy $h(0) = h(T) = 0$. If the magnitudes of both $h(t)$ and its derivative $\dot{h}(t)$ are relatively small, we can expand the expression in the action functional in $h$:
```{math}
:label: actionfunctionalexpansion
\begin{align*}
S[x+h] &= \int_0^T \mathcal{L}(x(t) + h(t), \dot{x}(t) + \dot{h}(t)) \,\mathrm{d}t  \\
&= \int_0^T \left[ \mathcal{L}(x(t), \dot{x}(t)) + \frac{\partial \mathcal{L}}{\partial x} h(t) + \frac{\partial \mathcal{L}}{\partial \dot{x}} \dot{h}(t)) + \mathcal{O}(h^2) \right] \mathrm{d}t,
\end{align*}
```
where $\mathcal{O}(h^2)$ stands for terms that are quadratic in either $h(t)$ or $\dot{h}(t)$, and the partial derivatives of $\mathcal{L}(x, \dot{x})$ treat the Lagrangian $\mathcal{L}$ as a (regular) function of $x$ and $\dot{x}$. Since the zeroth-order term in the expansion in&nbsp;{eq}`actionfunctionalexpansion` is simply the action functional of $x$, we can express the difference between $S[x+h]$ and $S[x]$ in terms of $h$ and&nbsp;$\dot{h}$; if we then integrate the term with $\dot{h}$ by parts, we arrive at an expression that depends on $h(t)$ alone:

$$
S[x+h] - S[x] = \int_0^T \left[ \frac{\partial \mathcal{L}}{\partial x} - \frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial \mathcal{L}}{\partial \dot{x}} \right] h(t) \,\mathrm{d}t + \mathcal{O}(h^2).
$$ (actionfunctionalvariation)

```{index} Euler-Lagrange equation
```
Now $x(t)$ is a stationary point of $S[x]$ if and only if the left-hand side<sup>[^4]</sup> of equation&nbsp;{eq}`actionfunctionalvariation` vanishes for any function $h(t)$. For that to hold, the right-hand side must also vanish, which means that the expression inside the square brackets in the integral must vanish. We have thus arrived at a differential equation involving the Lagrangian; it is known as the *Euler-Lagrange equation*:

$$
\frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial \mathcal{L}}{\partial \dot{x}} - \frac{\partial \mathcal{L}}{\partial x} = 0.
$$ (ELequation)

For the Lagrangian in equation&nbsp;{eq}`defLagrangian`, the Euler-Lagrange equation reproduces Newton's second law, equation&nbsp;{eq}`simpleeom`. For conservative systems, we can thus replace Newton's second law as an axiom with Hamilton's principle. So far, however, that just involves extra maths; you may well wonder why we bother re-deriving what we already know. The answer is twofold. First, Hamilton's principle applies to any set of coordinates, not just Cartesian ones, which makes finding expressions in other coordinate systems much easier. Second, the formalism allows us to easily include constraints on the motion (e.g. fixing the motion to a given surface in three-dimensional space), while the equivalent approach in Newtonian mechanics would yield very cumbersome equations.

(sec:ELgeneralcoordinates)=
## Euler-Lagrange equations in general coordinates

Before we go to arbitrary coordinate systems, we first expand the Euler-Lagrange equations to multiple dimensions. Fortunately, that is easy: we can write the Lagrangian in terms of vectors $\bm{x}(t)$ and $\dot{\bm{x}}(t)$, which gives us an action that is a functional of $\bm{x}$. The variation follows the same steps, which gives for the equivalent of equations&nbsp;{eq}`actionfunctionalexpansion` and&nbsp;{eq}`actionfunctionalvariation`:
```{math}
:label: actionfunctionalvariation3D
\begin{align*}
S[\bm{x} + \bm{h}] &= \int_0^T \mathcal{L}(\bm{x}(t) + \bm{h}(t), \dot{\bm{x}}(t) + \dot{\bm{h}}(t)) \,\mathrm{d}t  \\
&= \int_0^T \left[ \mathcal{L}(\bm{x}(t), \dot{\bm{x}}(t)) + \sum_i \frac{\partial \mathcal{L}}{\partial x_i} h_i(t) + \sum_i \frac{\partial \mathcal{L}}{\partial \dot{x_i}} \dot{h_i}(t)) + \mathcal{O}(|h|^2) \right] \mathrm{d}t  \\
&= S[\bm{x}] + \int_0^T \sum_i \left[ \frac{\partial \mathcal{L}}{\partial x_i} - \frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial \mathcal{L}}{\partial \dot{x}_i} \right] h_i(t) \,\mathrm{d}t + \mathcal{O}(|h|^2).
\end{align*}
```
In equation&nbsp;{eq}`actionfunctionalvariation3D`, $x_i$ is the $i$th component of $\bm{x}$, $h_i$ the $i$th component of $\bm{h}$, and $|h| = |\bm{h}|$ (again under the assumption that both $\bm{h}$ and $\dot{\bm{h}}$ are small). As the integral in equation&nbsp;{eq}`actionfunctionalvariation3D` has to vanish for any function $\bm{h}(t)$, it has to vanish for each choice of $h_i(t)$, and thus we find a *separate* Euler-Lagrange equation for each variable $x_i$:

$$
\frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial \mathcal{L}}{\partial \dot{x}_i} - \frac{\partial \mathcal{L}}{\partial x_i} = 0.
$$ (ELequations)

```{index} Lagrange
```
````{admonition} Joseph-Louis Lagrange (1736-1813)
:class: dropdown
**Joseph-Louis Lagrange** (1736-1813) was an Italian/French mathematician, physicist and astronomer, and one of the creators of both the calculus of variations and of analytical mechanics. Born in Italy as the son of a law professor and a mother from a wealthy family, Lagrange initially studied classical antiquity, with (as directed by his father) the objective of becoming a lawyer. Triggered by a paper by Halley that he found by accident, Lagrange self-studied mathematics, and quickly got a position as a mathematics professor, teaching the theories of Euler, with whom he also corresponded. The flow of information went both ways, with Lagrange proposing what became the Euler-Lagrange equations, as well as the method of Lagrange multipliers for dealing with constraints. By Euler's recommendation, Lagrange succeeded him as director of mathematics of the Prussian Academy of Sciences in Berlin in 1766, where he published extensively on analytical mechanics. A key contribution is his discovery of what are now known as Lagrange points in celestial mechanics, which explains the localization of the trojan asteroids that share their orbits with Jupiter, as well as being an ideal position for satellites like the James Webb telescope.Lagrange became a member of the French Academy of Sciences in 1787, when he also moved to Paris (and was later naturalized to French). In Paris, Lagrange was one of the founders and first professors of the École Polytechnique and the Bureau des Longuitudes. In the latter capacity, he played a central role in the introduction of the metric system.
```{figure} images/portraits/Lagrange.jpg
---
width: 300
---
19th century portrait of Lagrange <sup>[^5]</sup>.
```
````

Now suppose we have another set of coordinates $\bm{q}$ (these are often referred to as general or generalized coordinates). We can then express the coordinates $\bm{q}$ in the Cartesian coordinates $\bm{x}$ through a coordinate transformation, which simply means that the components of $\bm{q}$ are functions of $\bm{x}$:

$$
\bm{q}(t) = \bm{q}(\bm{x}(t)) \quad \text{and} \quad \dot{\bm{q}}(t) = \sum_i \frac{\partial \bm{q}}{\partial x_i} \dot{x}_i.
$$ (generalizedcoordinates)

Inversely, we can express the Cartesian coordinates in terms of the general ones as

$$
\bm{x}(t) = \bm{x}(\bm{q}(t)) \quad \text{and} \quad \dot{\bm{x}}(t) = \sum_i \frac{\partial \bm{x}}{\partial q_i} \dot{q}_i.
$$ (generalcoordinatesinverse)

We can now re-write the action in terms of the generalized coordinates:

$$
S[\bm{x}] = \int_0^T \mathcal{L}(\bm{x}(t), \dot{\bm{x}}(t)) \,\mathrm{d}t = \int_0^T \mathcal{L}\left((\bm{x}(\bm{q}(t)), \sum_i \frac{\partial \bm{x}}{\partial q_i} \dot{q}_i(t)\right) \,\mathrm{d}t = \int_0^T \tilde{\mathcal{L}}(\bm{q}(t), \dot{\bm{q}}(t)) \,\mathrm{d}t,
$$ (actionfunctionalcoordinatetransformation)

where $\tilde{\mathcal{L}}(\bm{q}(t), \dot{\bm{q}}(t))$ is the Lagrangian in terms of the generalized coordinates (which we will usually just write as $\mathcal{L}$). We can now apply Hamilton's principle to the action $S[\bm{q}]$ in terms of the generalized coordinates, which gives us a set of Euler-Lagrange equations for $q_i(t)$:

$$
\frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial \mathcal{L}}{\partial \dot{q}_i} - \frac{\partial \mathcal{L}}{\partial q_i} = 0.
$$ (ELequationsgencoord)

### Example: Equations of motion in polar coordinates
In {numref}`sec:polarplanarmotion` we derived the equations for Newton's second law in polar coordinates. Doing that using the Lagrangian formalism is considerably easier. We take $q_1 = r = \sqrt{x^2 + y^2}$ and $q_2 = \theta = \arctan(y/x)$. In polar coordinates, the Lagrangian reads

$$
\mathcal{L}(r, \dot{r}, \theta, \dot{\theta}) = \frac12 m (\dot{r}^2 + r^2 \dot{\theta}^2) - V(r, \theta).
$$ (polarLagrangian)

Substituting this Lagrangian into equation&nbsp;{eq}`ELequationsgencoord` reproduces equations&nbsp;{eq}`radialforce` and&nbsp;{eq}`angularforce`:

```{math}
\begin{align*}
F_r &= - \frac{\partial V}{\partial r} = m \ddot{r} - m r \dot{\theta}^2, \\
F_\theta &= - \frac{\partial V}{\partial \theta} = m r \ddot{\theta} + 2m \dot{r} \dot{\theta}.
\end{align*}
```

(sec:ELconstraint)=
## Euler-Lagrange equations for a system with constraints

Many mechanical systems have constraints: conditions which limit their degrees of freedom. Such constraints are often difficult to account for in a force-based description, as it is often not obvious which force you need to ensure that the system satisfies the constraint. In Lagrangian mechanics however, we can easily include 'constraint rules' which ensure that constraints are satisfied, and, as an added bonus (but with a caveat, as we'll see below), can give you the required forces.

```{index} Lagrange multiplier
```
To illustrate the concept, we'll start with an almost tautological example. Suppose a bead of mass&nbsp;$m$ is fixed to the end of a massless wire of length&nbsp;$L$, which you spin around with angular velocity&nbsp;$\omega$. We know of course that the bead will then execute a circular motion. For the sake of illustration, we will ignore this piece of knowledge, to see it emerge instead from the Lagrangian approach, under the action of a *constraint*: putting the free end of the wire at the origin, we impose that the mass must be at distance&nbsp;$L$, i.e., we have $L = \sqrt{x^2 + y^2}$, taking the mass to move in the $xy$ plane. In Lagrangian mechanics, we treat the constraint as an integral part of the problem. We absorb it into an extended version of the Lagrangian, with the addition of an extra variable, a *Lagrange multiplier*. As the only energy in the problem is the kinetic energy of the mass, $K = \frac12 m \dot{x}^2 + \frac12 m \dot{y}^2$, our extended Lagrangian becomes:

$$
\mathcal{L}'(x, \dot{x}, y, \dot{y}, \lambda) = \mathcal{L}(x, \dot{x}, y, \dot{y}) - \lambda\left(\sqrt{x^2 + y^2} - L\right) = \frac12 m \left(\dot{x}^2 + \dot{y}^2\right) - \lambda\left(\sqrt{x^2 + y^2} - L\right).
$$ (Lagrangemultiplierexample)

Note that we wrote the constraint in the form $\mathrm{function} = 0$. To find the constrained equations of motion, we now apply the Euler-Lagrange equations to the extended Lagrangian $\mathcal{L}'$, which gives us three equations (for $x$, $y$, and $\lambda$):

```{math}
:label: Lagrangemultiplierexampleeom
\begin{align*}
m \ddot{x} &= - \frac{\lambda x}{\sqrt{x^2 + y^2}} = - \frac{\lambda x}{L} \\
m \ddot{y} &= -mg - \frac{\lambda y}{\sqrt{x^2 + y^2}} = - \frac{\lambda y}{L} \\
0 &= - \left(\sqrt{x^2 + y^2} - L\right)
\end{align*}
```

Equation&nbsp;{eq}`Lagrangemultiplierexampleeom`C reproduces our constraint, which we've used to put equations {eq}`Lagrangemultiplierexampleeom`A and&nbsp;{eq}`Lagrangemultiplierexampleeom`B in simpler form. We now get equations of motion for the $x$ and $y$ coordinates that satisfy the constraint. In this case, we can immediately write down the solutions, as the equations are those of the simple harmonic oscillator:

```{math}
\begin{align*}
x(t) &= A \sin(\omega t) + B \cos(\omega t), \\
y(t) &= C \sin(\omega t) + D \cos(\omega t),
\end{align*}
```

where $\omega = \sqrt{m R / \lambda}$. If we put the initial position of the bead at $x=L, y=0$, we get $B = R$ and $D = 0$; from the condition that the angular velocity is $\omega$, we get $A = 0$ and $C = R$. Note that by specifying the angular velocity, we get the value of the Lagrange multiplier $\lambda$. Moreover, the terms on the right hand side of equations {eq}`Lagrangemultiplierexampleeom`A and&nbsp;{eq}`Lagrangemultiplierexampleeom`B represent forces, which are exactly those forces that will keep the bead in its circular motion. For the current example, $\lambda$ represents the tension in the wire, equal to $m R / \omega^2$. Note however that for the interpretation of the Lagrange multiplier as a force, we have to be careful about how we include the constraint. In the current example, we could also have written the constraint as $x^2 + y^2 - L^2 = 0$. Had we included that condition, the corresponding Lagrange multiplier would not be a force (it wouldn't even have the dimension of a force), but we would still have gotten the correct equations of motion.

````{prf:example} Rolling cylinder
:label: sec:rollingcylinderexample
:class: example
```{figure} images/mechanics/rollingcylinderinpipe.svg
:name: fig:rollingcylinder
:width: 300
A solid cylinder of radius&nbsp;$r$ rolling inside a larger cylinder of radius&nbsp;$R$, with indicated coordinates&nbsp;$\theta$ and $\phi$.
```
Suppose we take a solid cylinder of mass&nbsp;$m$ and radius&nbsp;$r$ which we place on the inner surface of a larger cylinder with radius&nbsp;$R$, see {numref}`fig:rollingcylinder`. We make sure that the axes of both cylinders are horizontal and keep the larger cylinder fixed. The smaller cylinder can then roll along the larger cylinder's inner surface under the force of gravity. Find the equation of motion of the rolling cylinder, and the frequency of the resulting oscillatory motion.

---
**Solution**
 We need two coordinates to describe a point on the surface of the smaller cylinder: the angle $\theta$ that its center makes as measured from the vertical, and the rotation angle&nbsp;$\phi$ of the smaller cylinder with respect to some reference line. We're given that the smaller cylinder is rolling, so the rolling condition applies, meaning that the point where its surface touches that of the larger cylinder is momentarily stationary. We can capture this condition as the following constraint:
```{math}
:label: rollingcylinderconstraint
(R-r) \dot{\theta} - r \dot{\phi} = 0.
```
For the kinetic and potential energy of the smaller cylinder we get:
```{math}
\begin{align*}
K &= \frac12 m (R-r)^2 \dot{\theta}^2 + \frac12 \left(\frac12 m r^2 \right) \dot{\phi}^2, \\
U &= - m g (R-r) \cos(\theta).
\end{align*}
```
For the Lagrangian (including a Lagrange multiplier&nbsp;$\lambda$ for the constraint&nbsp;{eq}`rollingcylinderconstraint`) we thus get:
```{math}
:label: rollingcylinderLagrangian
\mathcal{L}(\theta, \dot{\theta}, \phi, \dot{\phi}, \lambda) = \frac12 m (R-r)^2 \dot{\theta}^2 + \frac12 \left(\frac12 m r^2 \right) \dot{\phi}^2 + m g (R-r) \cos(\theta) - \lambda \left[(R-r) \dot{\theta} - r \dot{\phi} \right].
```
The Euler-Lagrange equation for $\lambda$ reproduces the constraint&nbsp;{eq}`rollingcylinderconstraint`. The equations for $\theta$ and $\phi$ give
```{math}
:label: rollincylinderthetaEOM
\begin{align*}
m (R-r)^2 \ddot{\theta} - \lambda (R-r) + m g (R-r) \sin(\theta) &= 0 \
\end{align*}
```
```{math}
:label: rollincylinderphiEOM
\begin{align*}
\frac12 m r^2 \ddot{\phi} + \lambda r &= 0.
\end{align*}
```
We now have three equations for the three variables&nbsp;$\theta$, $\phi$ and $\lambda$. In this case, reducing the system to one equation for one unknown is easy. We use equation&nbsp;{eq}`rollincylinderphiEOM` to express $\lambda$ in terms of $\phi$, which we can substitute in equation&nbsp;{eq}`rollincylinderthetaEOM`:
```{math}
:label: rollingcylindercombinedEOM
m (R-r)^2 \ddot{\theta} + \frac12 m r (R-r) \ddot{\phi} + m g (R-r) \sin(\theta) = 0.
```
The constraint&nbsp;{eq}`rollingcylinderconstraint` relates the derivatives of $\theta$ and $\phi$; taking the time derivative of this equation, we get $\ddot{\phi}$ in terms of $\ddot{\theta}$, which we can use to eliminate $\ddot{\phi}$ from equation&nbsp;{eq}`rollingcylindercombinedEOM`, and we obtain:
```{math}
:label: rollingcylinderEOM
\frac32 m (R-r)^2 \ddot{\theta} + m g (R-r) \sin(\theta) = 0.
```
We find that the equation of motion&nbsp;{eq}`rollingcylinderEOM` is mathematically equivalent to that of a simple pendulum. Re-writing the equation in the form $\ddot{\theta} + \omega^2 \sin(\theta)$, we can read off that the frequency of the oscillatory motion is given by
```{math}
:label: rollincylinderfrequency
\omega = \frac{2g}{3 (R-r)}.
```

````

## Symmetries and conservation laws
The Langrangian formalism not only gives us easy methods for transforming coordinates and incorporating constraints, it also allows us to uncover a connection between the *symmetries* of a mechanical system and its conserved quantities. A symmetry in physics is any operation that does not change the properties of the system, generalizing the notion of symmetry in geometric shapes. In geometry, a square has mirror (or reflection) symmetry about various axes, and rotational symmetry for rotations which are multiples of $90^\circ$; both are examples of discrete symmetries. A circle has a continuous symmetry under rotations about an arbitrary angle. Likewise, a mechanical system can be symmetric under rotations; an example we encountered before is a radial force field, for which the potential depends on the distance between two objects, but not on the angle with respect to some arbitrary reference. We've seen in {numref}`sec:centralforce` that for such a force, the angular momentum is conserved. A system with a radial force field has another symmetry: nothing changes if we translate the  system in time. Just like we can define an arbitrary angle as the zero angle $\theta = 0$, we can define an arbitrary point in time as $t=0$, but those are choices for convenience; they do not influence the equations of motion of the system, which are independent of both $\theta$ and $t$. Indeed, there is also a second conserved quantity, the total energy of the system, and we used both conserved quantities when describing the possible orbits for a particle under the action of a (constant) central force.

A second example of a system with a physical symmetry is billiards, in which balls collide fully elastically. Here too, time does not enter explicitly in the equations, and we have conservation of energy. Moreover, if we move the whole system over an arbitrary displacement in space, nothing changes in the collision itself, and we therefore have symmetry under (spatial) translations. The associated conserved quantity is the total momentum of the system<sup>[^6]</sup>.

```{index} Noether's theorem
```
All three relations between conservation laws and symmetries are special cases of *Noether's theorem*, which states that if the Lagrangian of a system is invariant under a continuous symmetry of a variable, there is an associated conserved quantity<sup>[^7]</sup> of the system. To keep things concrete, we will prove Noether's theorem for the conservation laws we encountered so far.

```{index} Noether
```
````{admonition} Emmy Noether (1882-1935)
:class: dropdown
**Emmy Noether** (1882-1935) was a German mathematician, who made key contribution both to the development of abstract algebra and to ideas in theoretical physics. In physics, she uncovered a deep connection between symmetry and conservation laws (now known as *Noether's theorem*, considered by many as the most important theorem for the development of modern physics): for every continuous symmetry of a system, there exists a conserved quantity. Applications of Noether's theorem include conservation of energy (corresponding to invariance under time translation, i.e., it doesn't matter where you set $t=0$, {prf:ref}`thm:timetranslationsymmetryenergyconservation`), conservation of momentum (invariance under space translation, i.e., it doesn't matter where you put the origin) and conservation of angular momentum (invariance under space rotation, i.e., it doesn't matter in which direction you choose your x-axis), see {prf:ref}`thm:generalizedmomentumconservation`. Similar conservation laws are found in special and general relativity, quantum mechanics, and quantum field theory. Unfortunately, even in the early 20th century, women were still excluded from most academic positions. Noether therefore initially worked for free at the university of Erlangen, getting a paid position in G\"ottingen in 1915 at the invitation of Hilbert and Klein, who had both been convinced by the quality of her work. Her fame grew through the 1910s and 1920s, gaining worldwide recognition. Due to her Jewish descent, she was dismissed from her academic position by the Nazi government in 1933, and moved to the United States, where she died two years later at age 53. Various institutes and scholarship programs, mostly in Germany, are now named in her honor.
```{figure} images/portraits/Noether.jpg
---
width: 300
---
Emmy Noether <sup>[^8]</sup>.
```
````

(sec:CoEHamiltonian)=
### Conservation of energy and the Hamiltonian

```{prf:theorem} Conservation of energy under time translation symmetry
:label: thm:timetranslationsymmetryenergyconservation
If a mechanical system is invariant under translations in time, i.e., if its Lagrangian does not explicitly depend on $t$, then the system's total energy $E = K + U$ is conserved.
```

```{index} Hamiltonian
```
````{prf:proof}
We consider a general Lagrangian as a function of generalized coordinates<sup>[^9]</sup> $\bm{q}$ which does not explicitly depend on time, $\mathcal{L}(\dot{\bm{q}}, \bm{q})$. As we've shown in {numref}`sec:ELgeneralcoordinates`, for each component of $\bm{q}$, we have a separate equation of motion, given by equation&nbsp;{eq}`ELequationsgencoord`. We now define the *Hamiltonian*&nbsp;$\mathcal{H}$ as

$$
\mathcal{H} = -\mathcal{L} + \sum_i \dot{q}_i \frac{\partial \mathcal{L}}{\partial \dot{q}_i}.
$$ (defHamiltonian)

A simple calculation shows that the Hamiltonian is conserved:
```{math}
:label: Hamiltonianconservation
\begin{align*}
\frac{\mathrm{d}\mathcal{H}}{\mathrm{d}t} &= -\frac{\mathrm{d}\mathcal{L}}{\mathrm{d}t} + \sum_i \frac{\mathrm{d}}{\mathrm{d}t} \left( \dot{q}_i \frac{\partial \mathcal{L}}{\partial \dot{q}_i} \right) \\
&= -\sum_i \frac{\partial \mathcal{L}}{\partial \dot{q}_i} \frac{\partial \dot{q}_i}{\partial t} - \sum_i \frac{\partial \mathcal{L}}{\partial q_i} \frac{\partial q_i}{\partial t} + \sum_i \frac{\partial \dot{q}_i}{\partial t} \frac{\partial \mathcal{L}}{\partial \dot{q}_i} + \sum_i \dot{q}_i \frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial \mathcal{L}}{\partial \dot{q}_i} = 0,
\end{align*}
```
where the first and third term cancel each other trivially, and the second and fourth term cancel because of the Euler-Lagrange equation&nbsp;{eq}`ELequationsgencoord`.
````

You might complain that while we've shown that the newly-introduced Hamiltonian is conserved, we did not prove anything about the energy. They are, however, one and the same, or more precisely, the Hamiltonian is the generalization of the energy to the general coordinates&nbsp;$\bm{q}$. Returning to the one-dimensional Cartesian coordinate case of {numref}`sec:EulerLagrange`, we can easily show that the Hamiltonian we get from the Lagrangian given in equation&nbsp;{eq}`defLagrangian` is indeed the total energy:

$$
\mathcal{H} = -\mathcal{L} + \dot{x} \frac{\partial \mathcal{L}}{\partial \dot{x}} = -\frac12 m \dot{x}^2 + U(x) + \dot{x} m \dot{x} = \frac12 m \dot{x}^2 + U(x) = E,
$$

and similarly for the three-dimensional case. We can make the relation with the energy more explicit in the case of generalized coordinates by observing that the derivative of the Lagrangian to the velocity is simply the momentum:

$$
p = m \dot{x} = \frac{\partial K}{\partial \dot{x}} = \frac{\partial \mathcal{L}}{\partial \dot{x}}.
$$ (momentumLagrangian)

Moreover, by Newton's second law, the time derivative of the momentum is the force, which is the derivative of the Lagrangian to the position:

$$
\dot{p} = F = - \frac{\partial U}{\partial x} = \frac{\partial K-U}{\partial x} = \frac{\partial \mathcal{L}}{\partial x}.
$$ (forceLagrangian)

Note that equations&nbsp;{eq}`momentumLagrangian` and {eq}`forceLagrangian` combined give the Euler-Lagrange equation&nbsp;{eq}`ELequation`; again the generalization to three dimensions is straightforward. We can also generalize to general coordinates&nbsp;$\bm{q}$, introducing the associated general momentum, defined as

$$
p_i = \frac{\partial \mathcal{L}}{\partial \dot{q}_i}.
$$ (generalmomentum)

In terms of the general position and momentum, we can thus write for the Hamiltonian

$$
\mathcal{H} = -\mathcal{L}(\bm{q}, \dot{\bm{q}}) + \sum_i \dot{q}_i \frac{\partial \mathcal{L}}{\partial \dot{q}_i} = -K(\dot{\bm{q}}) + U(\bm{q}) + \sum_i p_i \dot{q}_i = K(\dot{\bm{q}}) + U(\bm{q}),
$$

showing that it is indeed the energy expressed in terms of our general coordinates.

```{index} Hamilton's equations of motion
```
As you may know, the Hamiltonian is the central function in quantum mechanics. The Schr\"odinger equation, which is the quantum mechanical equivalent of Newton's second law as the central equation around which the theory is built, contains a 'quantized' version of the Hamiltonian, which can be split into a kinetic and a potential energy term. In classical mechanics, the Hamiltonian can be used to write the basis equations in a third alternative form (next to Newton's second law and the Euler-Lagrange equations), known as *Hamilton's equations of motion*, given by

```{math}
:label: Hamiltoneq
\begin{align*}
\dot{q}_i &= \frac{\partial \mathcal{H}}{\partial p_i}, \\
\dot{p}_i &= -\frac{\partial \mathcal{H}}{\partial q_i}.
\end{align*}
```

### Conservation of linear and angular momentum
The conservation laws for the two kinds of momentum are special cases of the following property of a Lagrangian in generalized coordinates.
```{prf:theorem} Conservation of generalized momentum
:label: thm:generalizedmomentumconservation
If the Lagrangian of a system with generalized coordinates $\bm{q}$ does not depend on the coordinate $q_i$, then the associated general momentum $p_i$ is conserved.
```

```{prf:proof}
By the Euler-Lagrange equations we have

$$
\frac{\mathrm{d}p_i}{\mathrm{d}t} = \frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial \mathcal{L}}{\partial \dot{q}_i} = \frac{\partial \mathcal{L}}{\partial q_i} = 0,
$$

where the last equality follows because $\mathcal{L}$ is independent of $q_i$.
```

```{index} cyclic coordinate
```
A coordinate $q_i$ on which the Lagrangian does not depend (and of which the associated generalized momentum is thus conserved) is sometimes called a *cyclic coordinate*.

```{prf:corollary} Conservation of linear momentum in Cartesian coordinates
:label: cor:linearmomentum
For a system described by Cartesian coordinates, if the Lagrangian does not depend on $x$, $y$, or $z$, the associated linear momenta $p_x$, $p_y$ and $p_z$ are conserved.
```

The proof of {prf:ref}`cor:linearmomentum` is simply that of {prf:ref}`thm:generalizedmomentumconservation` with $q_i$ replaced by $x_i$. A good example is a ball which you throw horizontally. While in the vertical direction there is an external force due to gravity, in the absence of drag, there is no horizontal force, and we thus expect the horizontal momentum to be conserved. Indeed, the associated Lagrangian in three dimensions is given by

$$
\mathcal{L} = \frac12 m \left( \dot{x}^2 + \dot{y}^2 + \dot{z}^2 \right) - m g z,
$$

which is independent of both $x$ and $y$, so the momenta $p_x$ and $p_y$ are conserved by {prf:ref}`cor:linearmomentum`.

```{prf:corollary} Conservation of angular momentum in spherical coordinates
:label: cor:angularmomentum
For a system described by spherical coordinates, if the Lagrangian does not depend on the azimuthal angle&nbsp;$\phi$, describing rotations about the $z$-axis, the angular momentum $L_z$ about the $z$-axis is conserved.
```

```{prf:proof}
The Lagrangian does not depend on $\phi$ if the potential does not; therefore, in this case the potential is a function of $r$ and $\theta$ alone. The most general Lagrangian that satisfies this condition is

$$
\mathcal{L} = K - V = \frac12 m \left( \dot{r}^2 + r^2 \dot{\theta}^2 + r^2 \sin^2(\theta) \dot{\phi}^2 \right) - V(r, \theta).
$$ (polarLagrangianphiindependent)

Because the Lagrangian does not depend on $\phi$, the associated general momentum is constant:

$$
p_\phi = \frac{\partial \mathcal{L}}{\partial \dot{\phi}} = m r^2 \sin^2(\theta) \dot{\phi}.
$$

Note that $p_\phi$ has the dimension of angular momentum. To see that it is indeed the angular momentum about the $z$-axis, we note that $\rho = r \sin(\theta)$ is the distance to the $z$-axis, and $\dot{\phi}$ is simply the angular velocity around the $z$-axis, so we have $p_\phi = m \rho^2 \dot{\phi} = L_z$.
```

As {prf:ref}`thm:generalizedmomentumconservation` holds for generalized coordinates, it can also be applied to cylindrical coordinates (see {numref}`pb:cylindricalcoordinatesconservationlaw`) or any other coordinate system of your liking. In some cases you'll get conservation laws for both linear and angular momentum. In all cases, the conservation law follows from a symmetry: the system doesn't change if you change the value of a coordinate.

### Noether's theorem*
In general, we define a continuous symmetry of a Lagrangian with respect to some coordinate $q_i$ to mean that, to first order, the Lagrangian does not change if the coordinate $q_i$ changes by a small amount. Therefore, if we apply a coordinate change

$$
q_i \to q_i + \varepsilon M_i(\bm{q}),
$$ (generalizedcoordinatechange)

the Lagrangian is invariant under this coordinate change if the change does not introduce any corrections of order $\varepsilon$ to the Lagrangian. Note that in equation&nbsp;{eq}`generalizedcoordinatechange`, the function&nbsp;$M_i(\bm{q})$ can depend on all coordinates&nbsp;$q_j$, not just on $q_i$. It may seem that we are making a weaker statement than before by restricting the definition of the symmetry to first-order effects, but in the derivation of the Euler-Lagrange equations we also ignored higher-order effects, and therefore we implicitly assumed the same in {prf:ref}`thm:timetranslationsymmetryenergyconservation` and&nbsp;{prf:ref}`thm:generalizedmomentumconservation`.
```{prf:theorem} Noether's theorem
:label: thm:Noether
For each continuous symmetry of the Lagrangian, there is an associated conserved quantity.
```

```{prf:proof}
We consider a coordinate transformation of the type given by equation&nbsp;{eq}`generalizedcoordinatechange`. By definition of the continuous symmetry, the transformation does not introduce any changes to the Lagrangian of order&nbsp;$\varepsilon$, and we therefore have

$$
0 = \lim_{\varepsilon \to 0} \frac{\mathrm{d}\mathcal{L}}{\mathrm{d}\varepsilon} = \lim_{\varepsilon \to 0} \sum_i \left( \frac{\partial \mathcal{L}}{\partial q_i} \frac{\partial q_i}{\partial \varepsilon} + \frac{\partial \mathcal{L}}{\partial \dot{q}_i} \frac{\partial \dot{q}_i}{\partial \varepsilon} \right) = \sum_i \left( \frac{\partial \mathcal{L}}{\partial q_i} M_i + \frac{\partial \mathcal{L}}{\partial \dot{q}_i} \dot{M}_i \right),
$$ (Noetherthmproof1)

where we could drop the limit after the last equality as it no longer has any dependence on&nbsp;$\varepsilon$. Using the Euler-Lagrange equations&nbsp;{eq}`ELequationsgencoord`, we can re-write our expression as

$$
0 = \sum_i \left[ \frac{\mathrm{d}}{\mathrm{d}t} \left(\frac{\partial \mathcal{L}}{\partial \dot{q}_i}\right) M_i + \frac{\partial \mathcal{L}}{\partial \dot{q}_i} \dot{M}_i \right] = \frac{\mathrm{d}}{\mathrm{d}t} \left( \sum_i \frac{\partial \mathcal{L}}{\partial \dot{q}_i} M_i \right).
$$ (Noetherthmproof2)

Equation&nbsp;{eq}`Noetherthmproof2` gives us our conserved quantity $P(\bm{q}, \dot{\bm{q}})$:

$$
P(\bm{q}, \dot{\bm{q}}) = \left( \sum_i \frac{\partial \mathcal{L}}{\partial \dot{q}_i} M_i \right).
$$ (conservedmomentum)

```

## Problems
```{exercise} Constraint forces for a particle sliding off a hemisphere without friction.
:label: pb:frictionlesshemisphereLagrangian
:class: dropdown
We revisit {numref}`pb:frictionlesshemisphere` of a particle sliding off a hemisphere with radius&nbsp;$R$ without friction. Let&nbsp;$\theta$ be the angle between the vertical and the current position of the particle.
1. Write down the Lagrangian of the particle in terms of the (constant) parameter&nbsp;$R$ and the variable&nbsp;$\theta$.
1. From your Lagrangian in (a), find the equation of motion of the particle (which will be valid only as long as the particle touches the hemisphere).
    While the procedure you followed in (a) and (b) quickly gave you the correct equation of motion, you've done so through the (implicit) assumption that the particle always touches the sphere. If instead we include the constraint as a (to be determined) constraining force, in the form of a Lagrange multiplier, we can also get the value of the force. To that end, we'll write the Lagrangian in terms of two coordinates: $r$, the distance of the particle to the center of the hemisphere, and $\theta$, the same angle as before.
1. Find the kinetic energy of the particle in terms of $r$ and $\theta$.
1. Write down the total Lagrangian of the particle: $\mathcal{L} = K - V_\mathrm{grav} - \lambda(R-r)$, where $V(r)$ is the (still to be determined) constraining potential.
1. From the Lagrangian, find the equations of motion of both $r$ and $\theta$.
1. Now apply the constraint (the 'equation of motion' you get from $\lambda$) $r=R$, which also gives $\dot{r} = \ddot{r} = 0$ to simplify your equations.
1. Use the one remaining nontrivial equation to find $\lambda$, and verify that it gives you the normal force of the sphere on the particle.
```

````{exercise} Conservation of momentum
:label: pb:cylindricalcoordinatesconservationlaw
:class: dropdown
Prove the following corollary of {prf:ref}`thm:generalizedmomentumconservation`:
```{prf:corollary} Conservation of linear and angular momentum in cylindrical coordinates
For a system described by cylindrical coordinates, if the Lagrangian does not depend on either the $z$-coordinate or the angular coordinate&nbsp;$\theta$, describing rotations about the $z$-axis, both the linear momentum in the $z$ direction and the angular momentum $L_z$ about the $z$-axis are conserved.
```
````

[^1]: We use a 'script L', $\mathcal{L}$, as our symbol for the Lagrangian, to avoid confusion with the angular momentum. Many other texts simply use a capital&nbsp;$L$.

[^2]: We know from experience, not from mathematical proof, since Newton's laws were our axioms.

[^3]: Things are rather different in quantum mechanics: there all possible paths are taken into account, and every path that fits the boundary conditions gets a finite probability of being taken.

[^4]: As you have surely noted, the left-hand side of equation&nbsp;{eq}`actionfunctionalvariation` strongly resembles the expression in the definition of the derivative of an ordinary function $f(t)$, which reads $f'(t) = \lim_{\Delta t \to 0} \frac{f(t+\Delta t) - f(t)}{\Delta t}$. Similarly, one can construct a *functional derivative* of any functional; the stationary points are those points for which the functional derivative vanishes.

[^5]: Portrait of Joseph-Louis Lagrange, 19th century, unknown painter. Picture is a faithful reproduction of a two-dimensional public domain work, retrieved from [Wikimedia commons](https://en.wikipedia.org/wiki/Joseph-Louis_Lagrange).

[^6]: Linear momentum is also conserved in a two-particle gravitational system, such as a single planet orbiting a star, as long as we describe the system using the reduced mass and the center of gravity.

[^7]: An alternative name you might encounter for the conserved quantity is a *first integral*.

[^8]: Photograph of Emmy Noether, unknown date and photographer, obtained from [Wikimedia commons](https://commons.wikimedia.org/wiki/File:Noether.jpg), public domain.

[^9]: While we write $\bm{q}$ as a vector for simplicity, it could be a vector of arbitrary dimension, containing multiple variables; for example, in the rolling cylinder example of {prf:ref}`sec:rollingcylinderexample`, $\bm{q}$ would contain $\theta$, $\phi$, and $\lambda$.

