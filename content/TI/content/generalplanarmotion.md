---
jupytext:
    formats: md:myst
    text_representation:
        extension: .md
        format_name: myst
kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---
(ch:planarmotion)=
# General planar motion

```{index} planar motion
```
Although Newton's laws of motion, the various force laws, and the three conservation laws we have derived, are all valid in three dimensions, we have so far restricted our study of motion almost exclusively to two special cases: linear motion in one dimension, and rotational motion in a plane, where the radius of the rotation is constant. Although for the second case we do need two directions to describe it, the motion itself is constricted to a circle, and thus essentially one-dimensional. In this section, we'll look at general motion in a plane - which turns out to capture a large number of important nontrivial cases.

## Projectile motion

```{index} projectile motion
```
The simplest case of two-dimensional motion occurs when a particle experiences a force only in one direction. The prime example of this case is the motion of a projectile in Earth's (or any other planet's) gravitational field as locally described by Galilean gravity (equation&nbsp;{eq}`Fg`): $\bm{F} = m \bm{g}$. Once a projectile has been fired with a certain initial velocity&nbsp;$\bm{v}_0$, we can find its trajectory by solving the equation of motion that follows from Newton's second law: $m \bm{g} = m \ddot{\bm{r}}$. We can decompose $\bm{r}$ and $\bm{v}_0$ in horizontal ($x$) and vertical ($z$) components; each of them has its own one-dimensional equation of motion, which we already solved in {numref}`sec:eom`. The horizontal component experiences no force and thus executes a simple linear motion with uniform velocity $v_0 \cos(\theta_0)$, where $\theta_0 = \arccos(\bm{v}_0 \cdot \bm{\hat{x}}) / v_0$ is the angle with the horizontal under which the projectile was fired and $v_0 = |\bm{v}_0|$ the initial speed. Likewise, because the acceleration due to gravitation is constant, our projectile will execute a uniformly accelerated motion in the vertical direction with initial velocity $v_0 \sin(\theta_0)$. If the projectile's initial position is $(x_0, z_0)$, its motion is thus described by:

$$
\bm{r}(t) = \begin{pmatrix} x(t) \\ z(t) \end{pmatrix} = \begin{pmatrix} x_0 \\ z_0 \end{pmatrix} + v_0 \begin{pmatrix} \cos(\theta_0) \\ \sin(\theta_0) \end{pmatrix} t - \begin{pmatrix} 0 \\ g \end{pmatrix} \frac12 t^2.
$$ (projectilemotion)

We can find the trajectory of the projectile through space by eliminating the time from equation&nbsp;{eq}`projectilemotion`. We have $t = (x - x_0) / v_0 \cos(\theta_0)$, which gives for the $z$ coordinate as a function of $x$:

$$
z(x) = z_0 + \tan(\theta_0) (x-x_0) - \frac12 g \left(\frac{x-x_0}{v_0 \cos(\theta_0)}\right)^2.
$$ (projectiletrajectory)

Equation&nbsp;{eq}`projectiletrajectory` describes the well-known parabolic trajectory of a projectile under the force of gravity.

(sec:polarplanarmotion)=
## General planar motion in polar coordinates

```{index} central force
```
Although in principle all planar motion can be described in Cartesian coordinates, they are not always the easiest choice. Take, for example, a central force field (a force field whose magnitude only depends on the distance to the origin, and points in the radial direction), as we'll study in the next section. For such a force field polar coordinates are a more natural choice than Cartesians. However, polar coordinates do carry a few subtleties not present in the Cartesian system, because the direction of the axes depends on position. We will therefore first derive the relevant expressions for the position, velocity and acceleration vector, as well as the components of the force vector, in polar coordinates for the general case.

As we already know (see {numref}`appsec:polarcoords`), the position vector $\vec{r} = x\bm{\hat{x}} + y\bm{\hat{y}}$ has a particularly simple expression in polar coordinates: $\bm{r} = r \bm{\hat{r}}$, where $r = \sqrt{x^2 + y^2}$. To find the velocity and acceleration vectors in polar coordinates, we take time derivatives of $\bm{r}$. Note that because the orientation of the polar basis vectors depends on the position in space, the time derivative acts on both the distance to the origin $r$ and the basis vector $\bm{\hat{r}}$. Because the two polar basis vectors are each other's derivatives with respect to $\theta$ (see equation&nbsp;{eq}`polarbasisvectorderivatives`), we find for their time derivatives:

$$
\frac{\mathrm{d}\bm{\hat{r}}}{\mathrm{d}t} = \frac{\mathrm{d}\bm{\hat{r}}}{\mathrm{d}\theta} \frac{\mathrm{d}\theta}{\mathrm{d}t} = \dot{\theta} \bm{\hat{\theta}}, \qquad \frac{\mathrm{d}\bm{\hat{\theta}}}{\mathrm{d}t} = \frac{\mathrm{d}\bm{\hat{\theta}}}{\mathrm{d}\theta} \frac{\mathrm{d}\theta}{\mathrm{d}t} = -\dot{\theta} \bm{\hat{r}}.
$$ (polarbasisvectortimederivatives)

For the velocity and acceleration vectors we then find:
```{math}
:label: polarvelocity
\begin{align*}
\bm{v} &= \frac{\mathrm{d}\bm{r}}{\mathrm{d}t} = \dot{r} \bm{\hat{r}} + r \dot{\theta} \bm{\hat{\theta}}, \
\end{align*}
```

```{math}
:label: polaracceleration
\begin{align*}
\bm{a} &= \frac{\mathrm{d}\bm{v}}{\mathrm{d}t} = (\ddot{r} - r \dot{\theta}^2) \bm{\hat{r}} + (r \ddot{\theta} + 2 \dot{r} \dot{\theta}) \bm{\hat{\theta}}.
\end{align*}
```
Note that equations&nbsp;{eq}`rotationv` and&nbsp;{eq}`rotationa` are the special cases of equations&nbsp;{eq}`polarvelocity` and&nbsp;{eq}`polaracceleration` for which both the radius&nbsp;$r$ and the angular velocity&nbsp;$\omega = \dot{\theta}$ are constant.

Using equation&nbsp;{eq}`polaracceleration` for $\ddot{\bm{r}}$ in Newton's second law, we get an expression decomposing the net force&nbsp;$\bm{F}$ into a radial and an angular part, each of which consists of two terms:
```{math}
:label: polarforce
\begin{align*}
\bm{F} &= m \ddot{\bm{r}} = F_r \bm{\hat{r}} + F_\theta \bm{\hat{\theta}} \
\end{align*}
```

```{math}
:label: radialforce
\begin{align*}
F_r &= m(\ddot{r} - r \dot{\theta}^2) 
\end{align*}
```

```{math}
:label: angularforce
\begin{align*}
F_\theta &= m (r \ddot{\theta} + 2 \dot{r} \dot{\theta})
\end{align*}
```

```{index} radial acceleration, centripetal force, tangential acceleration, Coriolis force
```
The two terms in $F_r$ are readily identified as the radial acceleration $\ddot{r}$ (acting along the line through the origin) and the centripetal force (which causes objects to rotate around the origin, see equation&nbsp;{eq}`Fcp`). The first term $r \ddot{\theta}$ in $F_\theta$ is the tangential acceleration&nbsp;$\alpha$ of a rotating object whose angular velocity is changing (equation&nbsp;{eq}`angularacceleration`). The last term in $F_\theta$ we have not encountered before; it is known as the *Coriolis force*

$$
\mathbf{F}_\mathrm{Cor} = 2 m \dot{r} \dot{\theta} \bm{\hat{\theta}},
$$ (FCoriolis)

and is associated with a velocity in both the radial and the angular direction. It is fairly weak on everyday length scales, but gets large on global length scales. In particular, if you move over the surface of the Earth (necessarily with a nonzero angular component of your velocity), it tends to deflect you from a straight path. On the Northern hemisphere, if you move horizontally, it tends to push you to the right; it also pushes you west when going up, and east when going down. Coriolis forces are responsible for the rotational movement of air around high and low pressure zones, causing respectively clockwise and counterclockwise currents around them on the Northern hemisphere (see {numref}`fig:Coriolis`). We'll encounter the Coriolis force again in the more general three-dimensional setting in {numref}`sec:rotatingframes`.

```{figure} images/mechanics/Coriolis.svg
:name: fig:Coriolis
The Coriolis force causes clockwise and counterclockwise currents around high and low pressure zones on the Northern hemisphere. (a) Pressure gradient (blue), Coriolis force (red) and resulting air flow (black) around a low pressure zone. (b) Typical satellite picture of a low-pressure zone and associated winds over Iceland. Picture by NASA's Aqua/MODIS satellite <sup>[^1]</sup>.
```

(sec:centralforce)=
## Motion under the action of a central force

```{index} central force, gravity, Coulomb force
```
A *central force* is a force that points along the (positive or negative) radial direction $\bm{\hat{r}}$, and whose magnitude depends only on the distance $r$ to the origin - so $\bm{F}(\bm{r}) = F(r) \bm{\hat{r}}$. Central forces can be defined in both two and three dimensions, with the three-dimensional concept of the radial distance (to the origin) and direction (direction of increasing $r$) completely analogous to the two-dimensional case. Two important examples of central forces are (general) Newtonian gravity {eq}`FGrav` and the Coulomb force {eq}`FCoulomb` between two charged objects. Although these forces are three-dimensional examples, discussing them here is appropriate, as the following theorem shows.


```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter8/c8q3.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```


```{prf:theorem}
:label: thm:motionundercentralforce
The motion of a particle under the action of a central force takes place in a plane.
```

```{prf:proof}
We first note that a central force can exert no torque on an object: $\bm{\tau} = \bm{r} \times \bm{F} = F(r) (\bm{r} \times \bm{\hat{r}}) = 0$. Consequently, under the action of a central force, angular momentum is conserved. Moreover, we have $\bm{r} \cdot \bm{L} = \bm{r} \cdot (\bm{r} \times \bm{p}) = 0$ and $\bm{v} \cdot \bm{L} = \bm{v} \cdot (\bm{r} \times m\bm{v}) = 0$. Both the position vector $\bm{r}$ and the velocity vector $\bm{v}$ thus lie in the plane perpendicular to $\bm{L}$. As $\bm{L}$ is conserved $\bm{r}$ and $\bm{v}$ must be confined to the plane perpendicular to $\bm{L}$ and through the origin.
```

Applying the results of the previous section to the motion of a single particle under the action of a central force, we find (for the plane in which the particle moves):

$$
F(r) = F_r = m \ddot{r} - m r \dot{\theta}^2 = m \ddot{r} - \frac{L^2}{m r^3},
$$ (centralforce1)

where we used that for a single particle, the magnitude of the angular momentum is given by $L = m r^2 \dot{\theta}$. Rewriting equation&nbsp;{eq}`centralforce1` gives

$$
m \ddot{r} = F(r) + \frac{L^2}{m r^3} = F(r) + F_\mathrm{cf},
$$ (centralforce2)

```{index} centrifugal force
```
where $F_\mathrm{cf}$ is known as the *centrifugal force*, as it tends to move our particle away from the origin. We can write the centrifugal force as the derivative of a potential:

$$
F_\mathrm{cf} = - \frac{\mathrm{d}U_\mathrm{cf}}{\mathrm{d}r} = - \frac{\mathrm{d}}{\mathrm{d}r} \left( \frac{L^2}{2 m r^2} \right).
$$ (centrifugalpotential)

Writing the original force as the derivative of a potential $U(r)$ as well, we can write down an equation for the total energy of the system:

$$
E = K + U = \frac12 m \dot{r}^2 + U(r) + \frac{L^2}{2 m r^2}.
$$ (centralforceenergy)

For both Newtonian gravity and the Coulomb force, the potential can be written as $U(r) = - \alpha/r$, where $\alpha = G m_1 m_2$ for gravity and $\alpha = -k_\mathrm{e} q_1 q_2$ for Coulomb's law. We can then rewrite the energy equation as a differential equation for $r(t)$:

$$
\frac12 m \left( \frac{\mathrm{d}r}{\mathrm{d}t} \right)^2 = E + \frac{\alpha}{r} - \frac{L^2}{2 m r^2}.
$$ (centralforceenergy2)

To describe the motion of the particle, rather than specifying $r(t)$ and $\theta(t)$, we would like to express $r$ as a function of $\theta$. We can rewrite equation&nbsp;{eq}`centralforceenergy2` to a differential equation for $r(\theta)$ by invoking the chain rule:

$$
\left( \frac{\mathrm{d}r}{\mathrm{d}t} \right)^2 = \left( \frac{\mathrm{d}r}{\mathrm{d}\theta} \frac{\mathrm{d}\theta}{\mathrm{d}t} \right)^2 = \left( \frac{\mathrm{d}r}{\mathrm{d}\theta} \right)^2 \left(\frac{L}{m r^2}\right)^2,
$$ (radiuschainrule)

where we again used that $L = m r^2 \dot{\theta}$. Equation&nbsp;{eq}`centralforceenergy2` now becomes:

$$
\left( \frac{1}{r^2} \frac{\mathrm{d}r}{\mathrm{d}\theta} \right)^2 = -\frac{1}{r^2} + \frac{2m\alpha}{L^2 r} + \frac{2mE}{L^2}.
$$ (centralforceenergy3)

Equation&nbsp;{eq}`centralforceenergy3` isn't pretty, but can be simplified a little by absorbing the $1/r^2$ on the left hand side into the derivative, and completing the square on the right hand side:

$$
\left( \frac{\mathrm{d}(\frac{1}{r})}{\mathrm{d}\theta} \right)^2 = -\left(\frac{1}{r} - \frac{m\alpha}{L^2} \right)^2 + \left(\frac{m\alpha}{L^2}\right)^2 \left(1 + \frac{2EL^2}{m \alpha^2} \right).
$$ (centralforceenergy4)

We can simplify equation&nbsp;{eq}`centralforceenergy4` further by introducing a new variable, $z=\frac{1}{r} - m\alpha / L^2$. We also introduce a dimensionless constant $\varepsilon = \sqrt{1 + 2 E L^2 / m\alpha^2}$ and an inverse length $q = m\alpha \varepsilon / L^2$. With these substitutions, our equation becomes:

$$
\left( \frac{\mathrm{d}z}{\mathrm{d}\theta} \right)^2 = - z^2 + q^2.
$$ (centralforceenergy5)

We can solve equation&nbsp;{eq}`centralforceenergy5` by separation of variables:

$$
\int \frac{1}{\sqrt{q^2-z^2}} \mathrm{d}z = \int \mathrm{d}\theta \Rightarrow \arccos\left(\frac{z}{q}\right) = \theta - \theta_0.
$$ (centralforceenergy6)

Taking the reference angle&nbsp;$\theta_0$ (our integration constant) to be zero, we find $z(\theta) = q \cos(\theta)$. Translating back to $r(\theta)$, we obtain a fairly simple solution:

$$
r(\theta) = \frac{L^2}{m \alpha} \frac{1}{1+\varepsilon \cos\theta}.
$$ (centralforceorbit)

```{index} orbit
```
What the solution&nbsp;{eq}`centralforceorbit` (the *orbit* of our particle under the action of the central force) actually looks like, depends on the value of our dimensionless variable $\varepsilon$, known as the *eccentricity* of the orbit. To find out which orbits we can get, we translate equation&nbsp;{eq}`centralforceorbit` back to Cartesian coordinates, using $x = r \cos\theta$. Defining $k = L^2/m\alpha$, we get $k = r + \varepsilon r \cos \theta = r + \varepsilon x$, or $r = k - \varepsilon x$. Now using $r^2 = x^2 + y^2$, we get

$$
x^2 + y^2 = (k-\varepsilon x)^2 = k^2 - 2 \varepsilon k x + \varepsilon^2 x^2.
$$ (centralforceorbitcartesians)

We can now distinguish four possibilities (see {numref}`fig:orbits`a):
1. $\varepsilon = 0$: In this case, equation&nbsp;{eq}`centralforceorbitcartesians` becomes $x^2 + y^2 = k^2$, so our orbit is a *circle* with the origin at its center.
1. $0 < \varepsilon < 1$: For this case, with some algebra (see {numref}`pb:ellipticalorbitproperties`), we can rewrite equation&nbsp;{eq}`centralforceorbitcartesians` as $((x-x_0)/a)^2 + (y/b)^2 = 1$, where $a = k / (1-\varepsilon^2)$, $x_0 = - \varepsilon a$, and $b = k / \sqrt{1-\varepsilon^2}$. These orbits are *ellipses*, with the center of the ellipse at $(x_0, 0)$, semi-major axis $a$, semi-minor axis $b$, and focal length $f = \sqrt{a^2 - b^2} = k \varepsilon / (1-\varepsilon^2) = - x_0$. One of the foci thus lies at the origin.
1. $\varepsilon = 1$: Equation&nbsp;{eq}`centralforceorbitcartesians` now becomes $y^2 = k^2 - 2kx$, which is the equation for a *parabola* (extending along the negative $x$-axis) with its 'top' (in this case, rightmost point) at $(k/2, 0)$ and focal length $k/2$, so the (single) focus is again located at the origin.
1. $\varepsilon > 1$: This case again requires some algebra to rewrite equation&nbsp;{eq}`centralforceorbitcartesians` in a recognizable standard form: $((x-x_0)/a)^2 - (y/b)^2 = 1$, where $a = k / (\varepsilon^2 - 1)$, $x_0 = \varepsilon a$ and $b = k / \sqrt{\varepsilon^2 - 1}$. These orbits are *hyperbola*, crossing the $x$-axis at $(x_0, 0)$, and approaching asymptotes $y = \pm b ((x/a) - \varepsilon)$, which meet at $(x_0+a,0)$. The focal length is now $f = \sqrt{a^2 + b^2} = k \varepsilon / (\varepsilon^2 - 1) = \varepsilon a = x_0 + a$, so the focus of the hyperbola is also located at the origin.

```{index} planetary orbits
```
In mathematics, these four possible types of orbits are known as *conic sections*: the curves you can get by intersecting a cone with a plane. Specifically, when the central force is gravity, such as in the solar system (where the sun is so much heavier than everything else combined that to good approximation we can describe orbits as being determined by the sun's gravitational field alone), the four cases listed above are the only possible orbits bodies can have. The planets, dwarf planets, asteroids, and many minor objects in our solar system all follow elliptical orbits around the sun, albeit with different eccentricity<sup>[^2]</sup> - Earth's is almost zero (0.017), but that of Mars is significantly higher (0.09), and of Pluto much higher still (0.25). Comets, on the other hand, typically parabolic or hyperbolic orbits. Spacecraft such as the [Voyager](https://en.wikipedia.org/wiki/Voyager_program) and [New Horizons](https://en.wikipedia.org/wiki/New_Horizons) probes are often put on trajectories past planets that are not their final destination, to pick up (or lose) speed through a gravitational assist (in which they take a little bit of momentum from the planet's orbit); those paths past planets are typically hyperbola. Getting a spacecraft to orbit another planet (i.e., in a bound, so elliptical) orbit is actually much harder, but again, the resulting orbit is described by the maths presented above.

```{figure} images/mechanics/orbits.svg
:name: fig:orbits
Orbits under the action of a central force. All orbits are described by equations&nbsp;{eq}`centralforceorbit` and&nbsp; {eq}`centralforceorbitcartesians` and are conic sections. (a) Four qualitatively different orbits, corresponding to different values of the parameter&nbsp;$\varepsilon$. Foci (colored dots) are shifted to show the orbits more clearly; as solutions of equation&nbsp;{eq}`centralforceorbit` or&nbsp; {eq}`centralforceorbitcartesians` all foci would be in the center. Blue: $\varepsilon = 0$, circular orbit. Orange: $\varepsilon = \frac12$, elliptical orbit. Green: $\varepsilon = 1$, parabolic orbit. Red: $\varepsilon = 2$, hyperbolic orbit. (b) Properties of the elliptical orbit. The orbit has semi-major axis&nbsp;$a$, semi-minor axis&nbsp;$b$, and focal distance $f = \sqrt{a^2-b^2}$. Distances in equation&nbsp;{eq}`centralforceorbit` are measured from the focal point in the origin; angles are measured with respect to the positive $x$-axis.
```

From the dimensionless eccentricity of an orbit, we can work out the total energy of that orbit easily. As $\varepsilon = \sqrt{1 + 2 E L^2 / m \alpha^2}$, we find

$$
E_\mathrm{orbit} = - \frac12 \left( \frac{\alpha}{L} \right)^2 (1-\varepsilon^2) m.
$$ (orbitenergy)

For elliptical orbits (where $(1-\varepsilon^2) = k/a = L^2 / (\alpha m a)$, with $a$ the semi-major axis), this expression gives a negative total energy that depends on the length of the semi-major axis only

$$
E_\mathrm{ellipticalorbit} = - \frac{\alpha}{2a},
$$ (ellipticalorbitenergy)

which is exactly half the potential energy of such an orbit. For a parabolic orbit (the boundary case between a closed and an open orbit), $\varepsilon = 1$, and so the total energy of the orbit vanishes; for a hyperbolic orbit we have $(\varepsilon^2 - 1) = k/a$ and we get a positive energy total energy.

(sec:Keplerslaws)=
## Kepler's laws

```{index} Kepler's laws
```
The fact that the planets move in elliptical orbits was first discovered by Kepler, based on observational data alone (he didn't have the benefit, as we do, of living after Newton and thus knowing about Newton's law of gravity). Kepler summarized his observational facts in three laws, which we can, with the benefit of hindsight, prove to be corollaries of Newton's laws.

```{index} Kepler
```
````{admonition} Johannes Kepler (1571-1630)
:class: dropdown
**Johannes Kepler** (1571-1630) was a German astronomer and mathematician who made major contributions to understanding the motion of the planets. Copernicus had published his heliocentric (rather than geocentric) view of the universe posthumously in 1543, but the two systems were still heavily debated in Kepler's time. Having been convinced that Copernicus was right, Kepler set out to construct a geometric description of the solar system. He initially tried to do so using polyhedra and Platonic solids, but found that these could not accurately describe the data. In 1600, Kepler met with astronomer Tycho Brahe, who had made meticulous observations of the known planets, and, having been convinced of Kepler's skills in mathematics, shared his data with him. After Tycho's death in 1601, Kepler succeeded him as imperial mathematician in Prague, where he developed his laws over the next decade. Unfortunately, Kepler's Calvinist views got him in trouble frequently with both the Catholic and the Lutheran church, which led to his excummunication, but he managed to avoid further persecution by moving frequently, and he always could continue his scientific work. The Kepler spacecraft and mission, launched in 2009 to hunt for extrasolar terrestial planets, is named in his honor.
```{figure} images/portraits/Kepler.jpg
---
width: 300
---
Portrait of Johannes Kepler (1610) <sup>[^3]</sup>.
```
````

```{prf:theorem} Kepler's first law
:label: thm:Kepler1
The planets move in elliptical orbits, with the sun at one of the foci.
```

```{prf:proof}
This is case two of the general result given by equations&nbsp;{eq}`centralforceorbit` and&nbsp;{eq}`centralforceorbitcartesians`.
```

```{index} conservation of angular momentum
```

```{prf:theorem} Kepler's second law
:label: thm:Kepler2
A line segment joining a planet and the sun sweeps out equal areas during equal intervals of time.
```

```{prf:proof}
This law is nothing but a special case of conservation of angular momentum. Consider a small piece of the orbit, in which the planet moves a distance $\mathrm{d}x$. The lines connecting the initial and final points of this piece of orbit with the sun make an angle $\mathrm{d}\theta$. If the initial distance from the planet to the sun was $r$, and the final distance $r + \mathrm{d}r$, we have, to first order, $\mathrm{d}x = r \mathrm{d}\theta$. The infinitesimal area the planet has swiped out is then given by (area of a triangle): $\mathrm{d}A = \frac12 r \mathrm{d}x = \frac12 r^2 \mathrm{d}\theta$. If we want to know how much area was swept out over an amount of time, we need to know the time derivative of $A$, which is thus given by $\mathrm{d}A / \mathrm{d}t = \frac12 r^2 \mathrm{d}\theta / \mathrm{d}t$. Now using that the angular momentum of the planet is given by $L = m r^2 \dot{\theta}$, we find

$$
\frac{\mathrm{d}A}{\mathrm{d}t} = \frac{r^2}{2} \frac{\mathrm{d}\theta}{\mathrm{d}t} = \frac{L}{2m},
$$ (KeplerTwo)

which is constant if $L$ is conserved.
```

```{prf:theorem} Kepler's third law
:label: thm:Kepler3
The square of the period&nbsp;$T$ of an orbit is proportional to the cube of its semi-major-axis length&nbsp;$a$:

$$
T^2 = \frac{4 \pi^2}{G M_\odot} a^3,
$$ (KeplerThree)

where $M_\odot$ is the mass of the sun.
```

```{prf:proof}
We integrate equation&nbsp;{eq}`KeplerTwo` over the period of a whole orbit, which gives $A = LT / 2m$. By Kepler's first law, the orbit is an ellipse, so its area equals $A = \pi a b$, with $a$ and $b$ the ellipse's semi-major and semi-minor axes. The two axes are related by $b = a \sqrt{1-\varepsilon^2}$, with $\varepsilon$ again the eccentricity of the ellipse. Making these substitutions and squaring the resulting relation, we get:

$$
\pi^2 a^4 = \frac{L^2}{m(1-\varepsilon^2)} \frac{T^2}{4m}.
$$

Using $k = L^2 / m\alpha$, like in equation&nbsp;{eq}`centralforceorbitcartesians`, and the observation that for an elliptical orbit $k/(1-\varepsilon^2) = a$, we get $L^2/m(1-\varepsilon^2) = \alpha a$. Now for orbits in the solar system, $\alpha = G M_\odot m$, so we arrive at equation&nbsp;{eq}`KeplerThree`.
```

Kepler's third law allows us to calculate the mass of any celestial body that is orbited by a (natural or artificial) satellite, simply by measuring the period and semi-major axis of the satellite's orbit.

## Problems
```{exercise} Geosynchronous orbit
:label: pb:geosynchronousorbit
:class: dropdown
A particularly useful orbit for satellites is the *geosynchronous* one: the orbit in which the satellite rotates around the Earth in exactly one day, so with respect to the ground, it is always in the same position. Find the altitude (i.e., distance above the Earth's surface) for a circular geosynchronous orbit.
```

```{exercise} Properties of elliptical orbits
:label: pb:ellipticalorbitproperties
:class: dropdown
In {numref}`sec:centralforce`, we found four possibilities for the orbits under a central force, all described by equation&nbsp;{eq}`centralforceorbit`: $r(\theta) = k / (1+\varepsilon \cos\theta)$. For $0 < \varepsilon < 1$ these orbits are ellipses. In this problem, we'll find expressions for the quantities that we usually use to parametrize an ellipse (see {numref}`fig:orbits`b) in terms of&nbsp;$\varepsilon$ and $k$.
1. The easiest parameter to find is the length&nbsp;$a$ of the semi-major axis, as twice the semi-major axis equals the distance between $r(0)$ and $r(\pi)$. From this equality, show that $a = k / (1-\varepsilon^2)$.
1. The focal distance&nbsp;$f$ is the distance from the center of the ellipse to the focal point. As we put the focal point in the origin, we have $f = a - r(0)$. Show that $f = \varepsilon a= k\varepsilon / (1-\varepsilon^2)$.
1. Find $x_0$ (no extra calculation required).
1. At the 'top' of the ellipse (where $y=b$), we have $\cos(\theta - \pi) = f/r$ and $r^2 = b^2 + f^2$. From these two equations, show that $b = a \sqrt{1-\varepsilon^2} = k / \sqrt{1-\varepsilon^2}$. *Hint: first show that $r=a$ at this position; from that you also get $f = \sqrt{a^2-b^2}$.*
```

```{exercise} Velocity vector in an elliptical orbit
:label: pb:ellipticalorbitradialvelocity
:class: dropdown
Prove that for an elliptical orbit, the velocity of the orbiting object is purely tangential at both the pericenter and apocenter (the closest and furthest point from the origin in the orbit). *Hint: take the time derivative of equation&nbsp;{eq}`centralforceorbit` to find the radial speed.*
```

```{exercise} Juno spacecraft
:label: pb:Junospacecraft
:class: dropdown
At the time of writing, the [Juno spacecraft](https://en.wikipedia.org/wiki/Juno_(spacecraft)) is in a polar orbit around Jupiter. It's perijove (closest distance to Jupiter) is at an altitude of&nbsp;$4200\;\mathrm{km}$, or $75600\;\mathrm{km}$ from Jupiter's center; Juno's apojove is $8.1\cdot 10^6 \;\mathrm{km}$ from Jupiter's center. The spacecraft weighs $1593\;\mathrm{kg}$. Jupiter's mass (known from the orbits of its moons) is $1.90 \cdot 10^{27}\;\mathrm{kg}$.
1. Find the semi-major axis and eccentricity of Juno's orbit around Jupiter.
1. How long does it take Juno to complete one orbit?
1. Find Juno's maximum and minimum speed while traversing this orbit. You may find the result of {numref}`pb:ellipticalorbitradialvelocity` useful in answering this question.
1. Suppose NASA wants to make Juno's orbit more circular. Should it have Juno fire its thruster rockets to accelerate or decelerate its angular velocity?
```

````{exercise} Kepler's laws and reduced mass
:label: pb:Keplerreducedmass
:class: dropdown
Kepler's laws apply to the case that an object with relatively small mass&nbsp;$m$ orbits an object with large mass&nbsp;$M$, which we assume stays fixed. Technically, this is incorrect: both objects rotate about their common center of mass. Fortunately, we can still use the expressions derived in this section, with a small modification. To see how this works, we write down the equations of motion for the two objects, due to the force they exert on each other:
```{math}
:label: twoobjectseom
\ddot{\bm{x}}_1 = -\frac{1}{m} \bm{F}(\bm{r}), \quad \ddot{\bm{x}}_2 = \frac{1}{M} \bm{F}(\bm{r}),
```
where $\bm{x}_1$ is the position of the object with mass&nbsp;$m$, $\bm{x}_2$ that of the object with mass&nbsp;$M$, and $\bm{r} = \bm{x}_2 - \bm{x}_1$ their separation. We denote the position of the center of mass of the system by $\bm{R}$, so
```{math}
:label: CoMtwoobjects
\bm{R} = \frac{m \bm{x}_1 + M \bm{x}_2}{m + M}.
```
1. As there is no external force acting on the system, the total momentum is conserved and therefore the center of mass cannot accelerate. Prove this statement by showing that
	```{math}
	:label: COMeom
	(m+M)\ddot{\bm{R}} = 0.
	```
1. From equation&nbsp;{eq}`twoobjectseom`, derive an equation of motion for the separation&nbsp;$\bm{r}$ between the two objects.
	The equations you found in (a) and (b) together are equivalent to the equations of motion in equation&nbsp;{eq}`twoobjectseom`, but they are uncoupled: we don't need to know the position of the center of mass to find the separation, and vice versa.
1. Show that you can re-write the equation of motion for the separation between the two objects as $\bm{F}(\bm{r}) = \mu \ddot{\bm{r}}$, where $\mu$ is the *reduced mass* (which we also encountered when studying collisions in the center of mass frame), given by
	```{math}
	\mu = \frac{m M}{m+M}.
	```
	Note that solving the final equation for the separation&nbsp;$\bm{r}$ is entirely equivalent to solving the equation of motion of a single particle under the action of a central force, with the modification that the mass of the particle is replaced by the reduced mass. The central force $\bm{F}(r)$ is still just the force that the two masses exert on each other. For the case that $m \ll M$, the reduced mass is approximately equal to $m$.
1. Calculate the reduced mass of the Earth-Moon two body problem. Can we state that the Moon revolves around the Earth?
1. Nowhere in the derivations in this problem did we assume that $m \ll M$. The same rules apply to any two objects. Consider the opposite limit: two objects (these might for instance be binary stars) of equal mass&nbsp;$M$ that rotate around their common center of mass. Show that for this case, for circular orbits the orbital period is given by
	```{math}
	:label: orbitbinarystars
	T^2 = \frac{2\pi^2 d^3}{GM},
	```
	where $d$ is the distance between the two objects.
````

```{exercise} Walking on a merry-go-round
:label: pb:merrygoround
:class: dropdown
A student with mass $65.0\;\mathrm{kg}$ stands at the center of a simple merry-go-round that consists of a large disk of radius $1.5\;\mathrm{m}$ and mass $25\;\mathrm{kg}$ and is making a full rotation every $2.0\;\mathrm{s}$. The student walks out to a distance of $0.50\;\mathrm{m}$ from the center.
1. Find the rotational frequency of the merry-go-round with the student at this point.
1. What are the forces acting on the student at this point?
```

[^1]: Image from NASA's Aqua/MODIS satellite, retreived from [Wikimedia commons](https://commons.wikimedia.org/wiki/File:Low_pressure_system_over_Iceland.jpg), public domain.

[^2]: See {numref}`tab:solarsystem` for data on the orbits of all planets and a number of their moons.

[^3]: Portrait of Johannes Kepler by an unknown artist, 1610. Picture is a faithful reproduction of a two-dimensional public domain work, retrieved from [Wikimedia commons](https://commons.wikimedia.org/wiki/File:Johannes_Kepler_1610.jpg).

