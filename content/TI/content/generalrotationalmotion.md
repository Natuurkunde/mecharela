(ch:generalrotationalmotion)=
# General rotational motion*

## Linear and angular velocity

```{index} angular velocity
```
We related the linear and angular velocities of a rotating object in two dimensions in {numref}`sec:rotationbasics`. There, we also already stated the relation between the linear velocity vector and rotation vector in three dimensions (equation&nbsp;{eq}`omegavrelation3D`):

$$
\bm{v} = \bm{\omega} \times \bm{r}.
$$

It is not hard to see that this expression indeed simplifies to the scalar relationship $v = \omega r$ for rotations in a plane, with the right sign for the linear velocity. That's hardly a proof though, so let's put this on some more solid footing. Suppose $\bm{r}$ makes an angle&nbsp;$\phi$ with $\bm{\omega}$. Suppose also that it changes by $\mathrm{d}\bm{r}$ in a time interval $\mathrm{d}t$, then if we have pure rotation, $\mathrm{d}\bm{r}$ is perpendicular to both $\bm{r}$ and $\bm{\omega}$, and its magnitude is given by $|\mathrm{d}\bm{r}| = \omega r \sin\phi \mathrm{d}t = |\bm{\omega} \times \bm{r}| \mathrm{d}t$, where $\omega$ and $r$ are the lengths of their respective vectors. Finally, as seen from the top (i.e., looking down the vector $\bm{\omega}$), the rotation should be counter-clockwise (by definition of the direction of $\bm{\omega}$), which corresponds with the direction of $\bm{\omega} \times \bm{r}$. We thus find that both the magnitude and direction of $\bm{v} = \mathrm{d}\bm{r} / \mathrm{d}t$ indeed equal $\bm{\omega} \times \bm{r}$, and equation&nbsp;{eq}`omegavrelation3D` holds.

(sec:rotatingframes)=
## Rotating reference frames

```{index} rotating reference frame
```
In {numref}`sec:frames`, we considered what happens if we considered the (linear) motion of an object from a stationary ('lab frame') or co-moving point of view, with special attention for the center of mass frame. These frames were moving with constant velocity with respect to each other, and were all inertial frames - Newton's first and second laws hold in all inertial frames. In this section, we'll consider a rotating reference frame, where instead of co-moving with a linear velocity, we co-rotate with a constant angular velocity. Rotating reference frames are not inertial frames, as to keep something rotating (and thus change the direction of the linear velocity) requires the application of a net force. Instead, as we'll see, in a rotating frame of reference we'll get all sorts of *fictitious forces* - forces that have no real physical source, like gravity or electrostatics, but originate from the fact that we're in a rotating reference frame.

In a rotating reference frame, the direction of the basis vectors changes over time (as measured with respect to the stationary lab frame - this is different from the linearly co-moving frames, where the directions of the basis vectors remained constant). To see how the basis vectors change over time, we can simply calculate their linear velocity, using equation&nbsp;{eq}`omegavrelation3D`:

$$
\frac{\mathrm{d}\bm{\hat{x}}}{\mathrm{d}t} = \bm{\omega} \times \bm{\hat{x}}, \qquad \frac{\mathrm{d}\bm{\hat{y}}}{\mathrm{d}t} = \bm{\omega} \times \bm{\hat{y}}, \qquad \frac{\mathrm{d}\bm{\hat{z}}}{\mathrm{d}t} = \bm{\omega} \times \bm{\hat{z}}.
$$ (rotatingbasisvectors)

We can now easily determine the change of an arbitrary vector $\bm{u} = u_x \bm{\hat{x}} + u_y \bm{\hat{y}} + u_z \bm{\hat{z}}$ over time:
```{math}
:label: rotatingtimederivative
\begin{align*}
\frac{\mathrm{d}\bm{u}}{\mathrm{d}t} &= \left( \frac{\partial u_x}{\partial t} \bm{\hat{x}} + \frac{\partial u_y}{\partial t} \bm{\hat{y}} + \frac{\partial u_z}{\partial t} \bm{\hat{z}}\right) + \left( u_x \frac{\mathrm{d}\bm{\hat{x}}}{\mathrm{d}t} + u_y \frac{\mathrm{d}\bm{\hat{y}}}{\mathrm{d}t} + u_z \frac{\mathrm{d}\bm{\hat{z}}}{\mathrm{d}t}\right) \\
&= \frac{\delta \bm{u}}{\delta t} + \bm{\omega} \times \bm{u},
\end{align*}
```
where $\frac{\delta \bm{u}}{\delta t}$ is defined by equation&nbsp;{eq}`rotatingtimederivative`, and represents the time derivative of $\bm{u}$ in the rotating basis<sup>[^1]</sup>. We see that in addition to the 'regular' time derivative, acting on the components of $\bm{u}$, we get an additional term $\bm{\omega} \times \bm{u}$ due to the rotation of the system. Note that for $\bm{u} = \bm{\omega}$, we find that $\mathrm{d}\bm{\omega} / \mathrm{d}t = \delta \bm{\omega} / \delta t = \dot{\bm{\omega}}$, i.e., the time derivative of the rotation vector is the same in the stationary and rotating frames.

The prime example of a vector is of course the position vector $\bm{r}$ of a particle, the second derivative of which appears in Newton's second law of motion. We'll calculate that second derivative for a position vector in a rotating coordinate frame. The first derivative is a simple application of equation&nbsp;{eq}`rotatingtimederivative`:

$$
\frac{\mathrm{d}\bm{r}}{\mathrm{d}t} = \frac{\delta \bm{r}}{\delta t} + \bm{\omega} \times \bm{r}.
$$ (rotatingvelocity)

To get the second derivative, we apply&nbsp;{eq}`rotatingtimederivative` to the velocity vector found in&nbsp;{eq}`rotatingvelocity`:
```{math}
:label: rotatingacceleration
\begin{align*}
\frac{\mathrm{d}^2 \bm{r}}{\mathrm{d}t^2} &= \frac{\mathrm{d}}{\mathrm{d}t} \left( \frac{\delta \bm{r}}{\delta t} + \bm{\omega} \times \bm{r} \right)  \\
&= \frac{\delta}{\delta t} \left( \frac{\delta \bm{r}}{\delta t} + \bm{\omega} \times \bm{r} \right) + \bm{\omega} \times \left( \frac{\delta \bm{r}}{\delta t} + \bm{\omega} \times \bm{r} \right)  \\
&= \frac{\delta^2 \bm{r}}{\delta t^2} + \frac{\delta \bm{\omega}}{\delta t} \times \bm{r} + 2 \bm{\omega} \times \frac{\delta \bm{r}}{\delta t} + \bm{\omega} \times (\bm{\omega} \times \bm{r}).
\end{align*}
```
Like in the two-dimensional case given by equation&nbsp;{eq}`polaracceleration`, we find that the acceleration in a rotating reference frame picks up extra terms compared to a stationary (or more general, inertial) frame. To get a complete picture, we also allow the origin of the rotating frame to be different from that of the stationary lab frame. Let $\bm{r}_\mathrm{lab}$ be the position vector in the lab frame, $\bm{R}$ the vector pointing from the origin of the lab frame to that of the rotating frame, and $\bm{r}$ the position vector in the rotating frame. We then have $\bm{r}_\mathrm{lab} = \bm{R} + \bm{r}$, and for the second derivative of $\bm{r}_\mathrm{lab}$ we find:
```{math}
:label: labrotatingacceleration
\begin{align*}
\frac{\mathrm{d}^2 \bm{r}_\mathrm{lab}}{\mathrm{d}t^2} &= \frac{\mathrm{d}^2 \bm{r}}{\mathrm{d}t^2} + \frac{\mathrm{d}^2 \bm{R}}{\mathrm{d}t^2} \\
&= \frac{\delta^2 \bm{r}}{\delta t^2} + \bm{\omega} \times (\bm{\omega} \times \bm{r}) + 2 \bm{\omega} \times \frac{\delta \bm{r}}{\delta t} + \frac{\delta \bm{\omega}}{\delta t} \times \bm{r} + \frac{\mathrm{d}^2 \bm{R}}{\mathrm{d}t^2}.
\end{align*}
```

```{index} Newton's laws of motion ; in a rotating reference frame
```
We can substitute equation&nbsp;{eq}`labrotatingacceleration` in Newton's second law of motion in the lab frame (i.e., just $\bm{F} = \mathrm{d}\bm{r}_\mathrm{lab} / \mathrm{d}t$) to find the expression for that law in the rotating frame:

$$
m \frac{\delta^2 \bm{r}}{\delta t^2} = \bm{F} - m \left[ \bm{\omega} \times (\bm{\omega} \times \bm{r}) + 2 \bm{\omega} \times \bm{v} + \dot{\bm{\omega}} \times \bm{r} + \frac{\mathrm{d}^2 \bm{R}}{\mathrm{d}t^2} \right],
$$ (NewtonSecondrotating)

```{index} fictitious force, centrifugal force, Coriolis force, azimuthal force, translational force
```
where we defined $\bm{v} = \delta \bm{r} / \delta t$ as the velocity in the rotating frame, and used that the time derivative of $\bm{\omega}$ is the same in both the stationary and the rotating frame. We find that we get four correction terms to the force due to our transition to a rotating frame. They are not 'real' forces like gravity or friction, as they vanish in the lab frame, but you can easily experience their effects, when you're in a turning car or rotating carousel. As they have no physical origin, we call these forces *fictitious*. They are known as the centrifugal, Coriolis, azimuthal, and translational force, respectively:
```{math}
:label: centrifugalforce
\begin{align*}
\bm{F}_\mathrm{cf} &= -m \bm{\omega} \times (\bm{\omega} \times \bm{r}) \
\end{align*}
```

```{math}
:label: Coriolisforce
\begin{align*}
\bm{F}_\mathrm{Cor} &= -2m \bm{\omega} \times \bm{v} 
\end{align*}
```

```{math}
:label: azimuthalforce
\begin{align*}
\bm{F}_\mathrm{az} &= -m \dot{\bm{\omega}} \times \bm{r} 
\end{align*}
```

```{math}
:label: translationalforce
\begin{align*}
\bm{F}_\mathrm{trans} &= -m \frac{\mathrm{d}^2 \bm{R}}{\mathrm{d}t^2}
\end{align*}
```

We encountered the centrifugal, Coriolis and azimuthal force before in {numref}`sec:polarplanarmotion`. To see how the expressions above connect to the planar versions, let us pick the coordinates of the rotating frame such that the direction of $\bm{\omega}$ coincides with the $z$-axis. The rotational motion and the forces can then be described in terms of the cylindrical coordinates consisting of the polar coordinates ($\rho$, $\theta$) in the $xy$-plane and $z$ along the $z$-axis (note that we use $\rho = \sqrt{x^2 + y^2}$ for the radial distance in the $xy$ plane instead of $r$, as $r$ is now the distance from the origin to our point in three dimensions). For the centrifugal force we have $\bm{\omega} \cdot \bm{F}_\mathrm{cf} = 0$, so it lies in our newly defined $xy$ plane, and in cylindrical coordinates it can be expressed as

$$
\bm{F}_\mathrm{cf} = - m \left[ \bm{\omega} (\bm{\omega} \cdot \bm{r}) - \omega^2 \bm{r} \right] = m \omega^2 (x \bm{\hat{x}} + y \bm{\hat{y}}) = m \omega^2 \rho \bm{\hat{\rho}}.
$$ (centrifugalcylindrical)

```{index} centripetal force
```
The centrifugal force is thus nothing but minus the centripetal force, which we already encountered for uniform rotational motion in equation&nbsp;{eq}`Fcp`, and as the second term in&nbsp;{eq}`radialforce`. The centrifugal force is the force you 'feel' pushing you sidewards when your car makes a sharp turn, and is also responsible for creating the parabolic shape of the water surface in a spinning bucket, see {numref}`pb:parabolicwatersurface`. 
The Coriolis force is present whenever a particle is moving with respect to the rotating coordinates, and tends to deflect particles from a straight line (which you'd get in an inertial reference frame). We have $\bm{\omega} \cdot \bm{F}_\mathrm{Cor} = \bm{v} \cdot \bm{F}_\mathrm{Cor} = 0$, so the Coriolis force is perpendicular to both the rotation and velocity vectors - note that this is the velocity in the rotating frame. In the two-dimensional case, we had $\bm{F}_\mathrm{Cor} = 2 m \dot{\rho} \omega \bm{\hat{\theta}}$ (equation&nbsp;{eq}`FCoriolis`), which for a velocity in the radial direction, $\dot{\rho}$, gives a force in the angular direction&nbsp;$\bm{\hat{\theta}}$.

The azimuthal force occurs when the rotation vector of our rotating system changes - i.e., when the rotation speeds up or decelerates, or the plane of rotation alters. In either case we have $\bm{r} \cdot \bm{F}_\mathrm{Cor} = 0$, so the force is perpendicular to the position vector. If it is the magnitude of the rotation vector that changes, and we again take the rotation vector to lie along the $z$-axis in the rotating frame, $\dot{\bm{\omega}}$ also lies along the $z$-axis, and we get

$$
\bm{F}_\mathrm{az} = - m \dot{\omega} \bm{\hat{z}} \times \bm{r} = - m r \ddot{\theta} \bm{\hat{\theta}},
$$ (azimuthalcylindrical)

so the azimuthal force is minus $m$ times the tangential acceleration $\alpha$ (see equation&nbsp;{eq}`angularacceleration`), or minus the first term of&nbsp;{eq}`angularforce`.

The translational force finally occurs when the rotating reference frame's origin accelerates with respect to that of the stationary lab frame. You also feel it if the 'rotating' reference frame is actually not rotating, but only accelerating linearly - it's the force that pushes you back in your seat when your car or train accelerates.

(sec:arbitraryaxisrotation)=
## Rotations about an arbitrary axis

(sec:MoItensor)=
### Moment of inertia tensor

In {numref}`ch:rotation`, we studied the rotation of rigid bodies about an axis of symmetry. For these cases, we have $\bm{L} = I \bm{\omega}$, where $I$ is the moment of inertia with respect to the rotation axis. We already noted that $I$ depends on which axis we pick, and that the proportional relation between the rotation vector and angular momentum is not the most general possibility. In this section, we'll derive the more general form, in which the number $I$ is replaced by a 2-tensor, i.e., a map from a vector space (here $\mathbb{R}^3$) into itself, represented by a $3 \times 3$ matrix.

```{figure} images/mechanics/dumbbellrotation.svg
:name: fig:dumbbellrotation
Rotation of a dumbbell, consisting of two equal masses $m$ separated by a distance $d=2r$ about an axis which is not a symmetry axis of the system.
```

```{index} angular momentum
```
To arrive at the more general relation between $\bm{L}$ and $\bm{\omega}$, we go back to the original definition of $\bm{L} = \bm{r} \times \bm{p}$, and consider the motion of a dumbbell around an axis which is not a symmetry axis (see {numref}`fig:dumbbellrotation`). If the dumbbell makes an angle&nbsp;$\theta$ with the rotation axis, and rotates counter-clockwise as seen from the top, we get:
```{math}
:label: Ldumbbell
\begin{align*}
\bm{L} &= m \bm{r} \times \bm{v} + m (-\bm{r}) \times (-\bm{v})  \\
&= 2 m \bm{r} \times (\bm{\omega} \times \bm{r})  \\
&= 2m \left[ \bm{\omega} (\bm{r}\cdot\bm{r}) - \bm{r} (\bm{r} \cdot \bm{\omega})\right] \\
&= 2m r^2 \bm{\omega} - 2 m \omega r \cos\theta \bm{r}
\end{align*}
```
where we used equation&nbsp;{eq}`omegavrelation3D` relating the linear velocity $\bm{v}$ to the rotational velocity $\bm{\omega}$ through $\bm{v} = \bm{\omega} \times \bm{r}$. Equation&nbsp;{eq}`Ldumbbell` shows that for a rotation about an arbitrary axis through the center of the dumbbell, we get two terms in $\bm{L}$. The first term, $2m r^2 \bm{\omega}$, is the rotation about an axis perpendicular to the dumbbell, and equals $I \bm{\omega}$ for $I = 2 m r^2$, as we found in {numref}`sec:MoI`. The second term, $- 2 m \omega r \cos\theta \bm{r}$, tells us that in general we also get a component of $\bm{L}$ along the axis pointing from the rotation center to the rotating mass (i.e., the arm). Note that the two terms cancel when $\theta = \pi/2$, as we'd expect for in that case the moment of inertia of the dumbbell is zero.

We can easily generalize equation&nbsp;{eq}`Ldumbbell` to any set of masses $m_\alpha$ with position vectors $\bm{r}_\alpha$ (where the index $\alpha$ runs over all particles), and with a rotation $\bm{\omega}$ about an arbitrary axis:

$$
\bm{L} = \sum_\alpha m_\alpha \bm{r}_\alpha \times (\bm{\omega} \times \bm{r}_\alpha) \equiv \bm{I} \cdot \bm{\omega}.
$$ (Lomegageneral)

```{index} moment of inertia tensor
```
The *moment of inertia tensor* is defined by equation&nbsp;{eq}`Lomegageneral`. It is a symmetric tensor, mapping a vector $\bm{\omega}$ in $\mathbb{R}^3$ onto another vector $\bm{L}$ in $\mathbb{R}^3$. In Cartesian coordinates, we can express its nine components as three moments of inertia about the $x$, $y$ and $z$ axes, which will be the diagonal terms of $\bm{I}$:

$$
I_{xx} = \sum_\alpha m_\alpha (y_\alpha^2 + z_\alpha^2) \qquad I_{yy} = \sum_\alpha m_\alpha (x_\alpha^2 + z_\alpha^2) \qquad I_{zz} = \sum_\alpha m_\alpha (x_\alpha^2 + y_\alpha^2),
$$ (momentsofinertia)

```{index} product of inertia
```
and three *products of inertia* for the off-diagonal components:

$$
I_{xy} = I_{yx} = -\sum_\alpha m_\alpha x_\alpha y_\alpha \qquad I_{xz} = I_{zx} = -\sum_\alpha m_\alpha x_\alpha z_\alpha \qquad I_{yz} = I_{zy} = -\sum_\alpha m_\alpha y_\alpha z_\alpha.
$$ (productsofinertia)

We can also write equations&nbsp;{eq}`momentsofinertia` and&nbsp;{eq}`productsofinertia` more succinctly using index notation, where $i$ and $j$ run over $x$, $y$ and $z$, and we use the Kronecker delta $\delta_{ij}$ which is one if $i=j$ and zero if $i \neq j$:

$$
I_{ij} = \sum_\alpha m_\alpha (r^2 \delta_{ij} - r_i r_j).
$$ (momentofinertiacomponents)

Equations&nbsp;{eq}`momentsofinertia` and&nbsp;{eq}`productsofinertia` generalize to continuous objects in the same way equation&nbsp;{eq}`discretemomentofinertia` generalized to&nbsp;{eq}`continuousmomentofinertia`. Using the index notation again, we can explicitly write:

$$
I_{ij} = \int_V (r^2 \delta_{ij} - r_i r_j) \rho(\bm{r}) \mathrm{d}V.
$$ (momentsofinertiaobject)

The moment of inertia tensor contains all information about the rotational inertia of an object (or a collection of particles) about any axis. In particular, if one of the axes (say the $z$-axis) is an axis of symmetry, we get that $I_{xz} = I_{yz} = 0$, and for rotations about that axis (so $\bm{\omega} = \omega \bm{\hat{z}}$), we retrieve $\bm{L} = I_\mathrm{z} \bm{\omega}$.

In addition to calculating the angular momentum, we can also use the moment of inertia tensor for calculating the kinetic energy for rotations about an arbitrary axis. We have:
```{math}
:label: Kinenrotarbaxis
\begin{align*}
K &= \frac12 \sum_\alpha m_\alpha \bm{v}_\alpha \cdot \bm{v}_\alpha \\
&= \frac12 \sum_\alpha m_\alpha (\bm{\omega} \times \bm{r}_\alpha) \cdot  (\bm{\omega} \times \bm{r}_\alpha) \\
&= \frac12 \bm{\omega} \cdot \left[ \sum_\alpha m_\alpha \bm{r}_\alpha \times (\bm{\omega} \times \bm{r}_\alpha) \right]  \\
&= \frac12 \bm{\omega} \cdot \bm{L} = \frac12 \bm{\omega} \cdot \bm{I} \cdot \bm{\omega}.
\end{align*}
```

```{index} Euler
```
````{admonition} Leonhard Euler (1707-1783)
:class: dropdown
**Leonhard Euler** (1707-1783) was a Swiss mathematician who made major contributions to many different branches of mathematics, and, by application, physics. He also introduced much of the modern mathematical terminology and notation, including the concept of (mathematical) functions. Euler was possibly the most prolific mathematician who ever lived, and likely is the person with the most equations and formulas named after him. Although his father, who was a pastor, encouraged Euler to follow in his footsteps, Euler's tutor, famous mathematician (and family friend) Johann Bernoulli convinced both father and son that Euler's talent for mathematics would make him a giant in the field. Famous examples of Euler's work include his contributions to graph theory (the K&ouml;ningsberg bridges problem), the relation $e^{i\pi}+1=0$ between five fundamental mathematical numbers named after him, his work on power series, a method for numerically solving differential equations, and his work on fluid mechanics (in which there is also an 'Euler's equation').
```{figure} images/portraits/Euler.jpg
---
width: 300
---
Portrait of Leonhard Euler by Jakob Handmann (1753) <sup>[^2]</sup>.
```
````

### Euler's equations
In the lab frame, we have equation&nbsp;{eq}`torqueangularmomentumrelation` relating the torque and the angular momentum. We used this equation to prove conservation of angular momentum in the absence of a net external torque, and to study precession. However, for rotations about an arbitrary axis, it is easier to transform to a frame in which we rotate with the object, much like moving with the center of mass makes the study of collisions much easier. We've already done the math for transforming to a co-rotating frame in {numref}`sec:rotatingframes`; here we only need the result in equation&nbsp;{eq}`rotatingtimederivative` to find the time derivative of the angular momentum in the rotating frame. Equation&nbsp;{eq}`torqueangularmomentumrelation` then translates to:

$$
\bm{\tau} = \frac{\delta \bm{L}}{\delta t} + \bm{\omega} \times \bm{L} = \bm{I} \cdot \dot{\bm{\omega}} + \bm{\omega} \times (\bm{I} \cdot \bm{\omega}).
$$ (rotatingtorque)

```{index} principal axes, principal moments of inertia, product of inertia
```
Now since $\bm{I}$ is symmetric, all its eigenvalues are real, and its eigenvectors are a basis for $\mathbb{R}^3$; moreover, for distinct eigenvalues the eigenvectors are orthogonal, so from the eigenvector basis we can easily construct an orthonormal basis $(\bm{\hat{e}}_1, \bm{\hat{e}}_2, \bm{\hat{e}}_3)$ of eigenvectors corresponding to the three eigenvalues $I_1$, $I_2$ and $I_3$. If we express the moment of inertia tensor in this orthonormal eigenvector basis, its representation becomes a simple diagonal matrix, $\bm{I} = \mathrm{diag}(I_1, I_2, I_3)$. We call the directions $\bm{\hat{e}}_i$ the *principal axes* of our rotating object, and the associated eigenvalues the *principal moments of inertia*. The construction of the principal axes and moments of inertia works for any object - including ones that do not exhibit any kind of symmetry. If an object does have a symmetry axis, that axis is usually also a principal axis, as can easily be checked by calculating the products of inertia with respect to that axis (they vanish for a principal axis).

If we express our rotational quantities in the principal axis basis $\{\bm{\hat{e}}_i\}$ of our rotating object, our equations become much simpler. We have

$$
\bm{L} = \bm{I} \cdot \bm{\omega} = \begin{pmatrix} I_1 & 0 & 0 \\ 0 & I_2 & 0 \\ 0 & 0 & I_3 \end{pmatrix} \begin{pmatrix} \omega_1 \\ \omega_2 \\ \omega_3 \end{pmatrix} = \begin{pmatrix} I_1 \omega_1 \\ I_2 \omega_2 \\ I_3 \omega_3 \end{pmatrix},
$$ (angularmomentummatrixproduct)

or in components: $L_i = I_i \omega_i$. Equation&nbsp;{eq}`rotatingtorque` simplifies to:

$$
\bm{\tau} = \begin{pmatrix} I_1 \dot{\omega}_1 \\ I_2 \dot{\omega}_2 \\ I_3 \dot{\omega}_3 \end{pmatrix} + \begin{pmatrix} \omega_1 \\ \omega_2 \\ \omega_3 \end{pmatrix} \times \begin{pmatrix} I_1 \omega_1 \\ I_2 \omega_2 \\ I_3 \omega_3 \end{pmatrix},
$$ (rotatingtorqueprincipalaxes)

which gives for the three components of the torque:

```{math}
:label: Eulersequations
\begin{align*}
\tau_1 &= I_1 \dot{\omega}_1 + (I_3-I_2) \omega_3 \omega_2,\\
\tau_2 &= I_2 \dot{\omega}_2 + (I_1-I_3) \omega_1 \omega_3,\\
\tau_3 &= I_3 \dot{\omega}_3 + (I_2-I_1) \omega_2 \omega_1.
\end{align*}
```

```{index} Euler's equations
```
Equations&nbsp;{eq}`Eulersequations` are known as *Euler's equations* (of a rotating object - the classification is necessary as there are many equations associated with Euler).

As an example, let's apply Euler's equations to our dumbbell. We take the origin at the pivot, i.e., where the rotation axis crosses the dumbbell's own axis. The dumbbell does have rotational symmetry, about the axis connecting the two masses - let's call that the $3$-axis. The other two axes then span the plane perpendicular to the dumbbell; we can pick any orthonormal pair for the $1$ and $2$-axes. The rotation vector in this basis is given by

$$
\bm{\omega} = \begin{pmatrix} \omega_1 \\ \omega_2 \\ \omega_3 \end{pmatrix} = \omega \begin{pmatrix} 0 \\ \sin\theta \\ \cos\theta \end{pmatrix}.
$$ (dumbbellrotationvector)

The products of inertia vanish; the principal moments are given by $I_1 = I_2 = \frac12 m d^2$ (with $d$ the distance between the two masses) and $I_3 = 0$. As long as the rotational velocity is constant ($\dot{\bm{\omega}} = 0$), we get from Euler's equations that $\tau_2 = \tau_3 = 0$, and $\tau_1 = - \frac12 m d^2 \omega^2 \sin\theta \cos\theta$. We can thus rotate our dumbbell about an axis that's not a symmetry axis, but at a price: it exerts a torque on its support, which in turn exerts a counter-torque to keep the dumbbell's rotation axis in place. This torque will change the angular momentum of our dumbbell over time. If we remove the force exerting the counter-torque (e.g., if our dumbbell is supported at the pivot, remove the support), the dumbbell will turn, in our example about axis&nbsp;$2$, until the rotation vector&nbsp;$\bm{\omega}$ has become parallel with the angular momentum vector&nbsp;$\bm{L}$.

For the dumbbell, as it has a rotational symmetry, two of the principal moments are identical. There are many objects that have no such symmetry, but they still have three well-defined principal axes. While for the dumbbell rotation about any of the principal axes is stable, this is not the case for an object with three different principal moments. A good example is a tennis racket, whose principal axes are sketched in {numref}`fig:tennisracket`. The accompanying theorem about the stability of rotations about these axes is easily demonstrated with a tennis racket, and bears its name.

````{prf:theorem} Tennis racket theorem
:label: thm:tennisrackettheorem

```{index} tennis racket theorem
```
If the three principal moments of inertia of an object are different (say $I_1 < I_2 < I_3$), then rotations about the principal axes $1$ and $3$ associated with the maximum and minimum moments $I_1$ and $I_3$ are stable, but those about the principal axis $2$ associated with the intermediate moment $I_2$ are unstable.
````

````{prf:proof}
For rotations about a principal axis, the torque is zero (by construction), so Euler's equations read

```{math}
:label: Eulernotorque
\begin{align*}
\dot{\omega}_1 + \frac{I_3-I_2}{I_1} \omega_3 \omega_2 &=0, \\
\dot{\omega}_2 + \frac{I_1-I_3}{I_2} \omega_1 \omega_3 &=0, \\
\dot{\omega}_3 + \frac{I_2-I_1}{I_3} \omega_2 \omega_1 &=0.
\end{align*}
```

If we rotate about axis&nbsp;$1$, then $\omega_2$ and $\omega_3$ are (at least initially) very small, so equation&nbsp;{eq}`Eulernotorque`a gives $\dot{\omega}_1 = 0$. We can then derive an equation for $\omega_2$ by taking the time derivative of&nbsp;{eq}`Eulernotorque`b and using&nbsp;{eq}`Eulernotorque`c for $\dot{\omega}_3$, which gives:

$$
0 = \ddot{\omega}_2 + \frac{I_1-I_3}{I_2} \left( \dot{\omega}_1 \omega_3 + \omega_1 \dot{\omega_3} \right) = \ddot{\omega}_2 - \frac{I_1-I_3}{I_2} \frac{I_2-I_1}{I_3} \omega_1^2 \omega_2.
$$ (tennisracketomega2)

Now $(I_1-I_3)/I_2 < 0$, $(I_2-I_1)/I_3 > 0$, and $\omega_1^2 > 0$, and $\omega_2$ satisfies the differential equation $\ddot{\omega}_2 = - c \omega_2$, with $c>0$. Solutions to this equation are of course sines and cosines with constant amplitude. Although $\omega_2$ can thus be finite, its amplitude does not grow over time (and will in fact decrease due to drag), so rotations about axis $2$ are opposed. Similarly, we find that rotations about axis $3$ cannot grow in amplitude either, and rotations about axis&nbsp;$1$ are stable. We can repeat the same argument for axes $2$ and $3$. For axis $3$, we find that rotations about the other two axes are likewise opposed, so rotations about this axis are stable as well. For axis&nbsp;$2$ on the other hand, we find that

$$
0 = \ddot{\omega}_1 - \frac{I_3-I_2}{I_1} \frac{I_2-I_1}{I_3} \omega_2^2 \omega_1,
$$ (tennisracketomega1)

or $\ddot{\omega}_1 = c \omega_1$, with $c$ another positive constant. Solutions to this equation are not sines and cosines, but exponential: $\omega_1(t) = A \exp(\sqrt{c}t) + B \exp(-\sqrt{c}t)$, which means that for any finite initial rotation about the&nbsp;$1$ axis, the amplitude of this rotation will grow over time, and rotations about the $2$-axis are thus unstable.
````

```{figure} images/mechanics/tennisracketprincipalaxes.svg
:name: fig:tennisracket
The three principal axes of a tennis racket.
```

## Problems
```{exercise} Recreating Galilei's experiment
:label: pb:churchtowerstonedrop
:class: dropdown
Two Delft students wish to re-create Galilei's experiment dropping objects with different mass from a high tower. They use the tower of the Old Church in Delft, which, like the more famous one in Pisa supposedly used by Galilei, leans over somewhat. The tip of the tower is $75\;\mathrm{m}$ above street level, and $2.0\;\mathrm{m}$ removed from the vertical. The student who will drop the objects stands on the trans at $60\;\mathrm{m}$. The base of the tower is a square of $10\times10\;\mathrm{m}$.
1. How far from the base of the tower do you expect the stone to fall?
1. The second student, who has done the same calculation you did in (a), has put a camera close to the floor aimed at the spot where the objects will drop. Surprisingly, in a test drop of a single stone, he observes that the actual position the stone hits the ground deviates from this spot. The student at the top however insists that she dropped the stone straight down from the tower trans, as agreed. The students therefore go back to their Mechanics books and realize that they forgot to account for the rotation of the Earth. Which of the (fictional) forces described in this chapter could cause the stone to deviate from its straight path down?
1. Delft is located on the Northern hemisphere. In which direction will the trajectory of the stone be deflected?
1. Delft is at $52.0^\circ\mathrm{N}$. What is the magnitude of the deflection of the dropped stone on the ground? You may neglect air resistance in this calculation.
```

````{exercise} Foucault's pendulum
:label: pb:Foucaultspendulum
:class: dropdown

```{index} Foucault's pendulum
```
**Foucault's pendulum** A well-known (and conclusive) proof of the fact that the Earth is rotating is provided by a Foucault pendulum, first presented by French physicist L&eacute;on Foucault in 1851 (a replica of his device is on permanent exhibit in the Panth&eacute;on in Paris, as well as in many other science musea around the world, see {numref}`fig:Foucaultpendulum`). A key part of this pendulum is the way its pivot is constructed: it has to be rotationally symmetric and frictionless, so it can't exert any torques on the pendulum itself. Consequently, the plane in which the pendulum oscillates will remain unchanged<sup>[^3]</sup>, *even as* the Earth rotates. Therefore, for observers on Earth, the plane of the pendulum seems to rotate over time. To see how this works, consider putting this pendulum at the North pole. Then for an external observer, the plane of the pendulum stays fixed (there are no forces acting on it), while the Earth (looking down on the North pole) rotates counterclockwise; for an Earth-bound observer, the pendulum's plane thus seems to move clockwise (again as seen from the top), making one full revolution in one day.
```{figure} images/mechanics/Foucault.svg
:name: fig:Foucaultpendulum
Foucault's pendulum. (a) Coordinates in Paris. (b) For a pendulum with a long string and small amplitude, the velocity of the bob will be almost horizontal. (c) The replica of Foucault's original pendulum at the Panth&eacute;on&nbsp;<sup>[^4]</sup>.
```
Paris is not on the North pole, but it does lie on the Northern hemisphere, so the pendulum will still appear to rotate clockwise, just at a slower frequency. We'll calculate this precession frequency in this problem.
1. First, we need the angular velocity in Paris, in a useful coordinate system. Define the $\bm{\hat{z}}$ axis as pointing upwards in Paris, and $\bm{\hat{x}}$ as the tangent to the planet due North (see {numref}`fig:Foucaultpendulum`a). Express $\bm{\omega}$ in these coordinates.
1. If the pendulum has a very long string (the original Foucault one is 67&nbsp;m) compared to its amplitude, the velocity $v$ of the weight will be roughly in the horizontal direction, see {numref}`fig:Foucaultpendulum`b. Argue why, in this case, the component of $\bm{\omega}$ in the $\bm{\hat{x}}$ direction will not change the frequency at which the plane of the pendulum precesses.
1. The pendulum's plane rotates with a (precession) frequency $\bm{\omega}_\mathrm{P} = \omega_\mathrm{P} \bm{\hat{z}}$ with respect to the Earth's frame fixed in Paris. This precession frequency must exactly compensate for the Earth's rotation in the frame of the pendulum (as in that frame, there are no forces acting on the pendulum, and thus its plane of oscillation stays fixed). Show that these considerations imply that $\omega_\mathrm{P} = - \omega \cos\theta$.
1. Suppose that you enter the Panth&eacute;on at noon, and mark the direction in which the pendulum is oscillating. When you return an hour later, by how much will this plane have rotated? Will this be enough to be visible by eye? The Panth&eacute;on is at $48^\circ50'46''\mathrm{N}$ (note that degrees, like hours, are divided in (arc)minutes and seconds that run up to 60, not 100).
````

```{exercise} Fictitious forces on a sliding particle
:class: dropdown
An alternative way to show the effect of the rotation of the Earth involves only a smooth horizontal plane and a particle that can slide over it. Show that if the particle's velocity is&nbsp;$v$, its trajectory will be a circle with radius $r = v/2\Omega$, where $\Omega$ is the Earth's rotational velocity.
```

````{exercise} Parabolic water surface
:label: pb:parabolicwatersurface
:class: dropdown
The centrifugal force emerges in a rotating coordinate frame, and famously causes the parabolic shape of the surface of water in a rotating bucket. As the centrifugal force is always perpendicular to the rotation axis, we can pick coordinates such that the rotation axis coincides with the $z$-axis, $\bm{\omega} = \omega \bm{\hat{z}}$, and we can express the centrifugal force in cylindrical coordinates as $\bm{F}_\mathrm{cf} = m \omega^2 \rho \bm{\hat{\rho}}$ (equation&nbsp;{eq}`centrifugalcylindrical`).
```{figure} images/mechanics/parabolicwatersurface.svg
:name: fig:parabolicwatersurface
Parabolic water surface in a rotating bucket. The axis of rotation coincides with the axis of symmetry. For a small volume of water at the surface, the gravitational force and the centrifugal force add up to an effective gravitational force, which must be perpendicular to the water surface in steady-state. This net force is counterbalanced by the pressure in the water ($\bm{F}'$).
```
We now consider a small volume of water at the rotating surface (in steady-state). There are two forces acting on this mass of water: gravity (pointing down, as always) and the centrifugal force, pointing outward, see {numref}`fig:parabolicwatersurface`. The resulting net force cannot have a component along the surface, as this would result in an acceleration of the water (and hence a water flow); therefore, the force must be perpendicular to the surface, and counterbalance the pressure in the water (just like it would for the flat surface of water in a bucket that is not rotating).
The gravitational and centrifugal force add up to what is known as an *effective gravity*, given by
```{math}
:label: effectivegravitycylindrical
\bm{g}_\mathrm{eff} = - g \bm{\hat{z}} + \omega^2 \rho \bm{\hat{\rho}}.
```
1. Find the angle&nbsp;$\theta$ the direction of the effective gravitational force makes with the vertical (see {numref}`fig:parabolicwatersurface`).
1. If the gravitational force is to be perpendicular to the water surface, we must have
	```{math}
	\frac{\mathrm{d}z}{\mathrm{d}\rho} = \tan\theta.
	```
	Integrate this equation to find $z(\rho)$ (and thus the shape of the surface).
1. Find the potential energy corresponding to the effective gravitational force, $\bm{F}_\mathrm{eff} = m \bm{g}_\mathrm{eff}$.
1. Argue why the potential energy must be constant on the water surface, and from this condition, again derive the shape of the water surface.
````

[^1]: Some authors use the notation $\left(\frac{\mathrm{d}\bm{u}}{\mathrm{d}t}\right)_\mathrm{rot}$ for $\frac{\delta\bm{u}}{\delta t}$.

[^2]: Portrait of Leonhard Euler by Jakob Emanuel Handmann, 1753. Picture is a faithful reproduction of a two-dimensional public domain work (now in the Kunstmuseum Basel), retrieved from [Wikimedia commons](https://commons.wikimedia.org/wiki/File:Leonhard_Euler.jpg).

[^3]: With respect to the (relatively) fixed frame provided by a collection of distant stars.

[^4]: Image by Arnaud 25, [Wikimedia commons](https://commons.wikimedia.org/w/index.php?curid=3759554), public domain.

