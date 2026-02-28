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
(app:linalg)=
# Linear algebra

(appsec:vectors)=
## Vector basics

Classical mechanics describes the motion of bodies as they move through space. To describe a motion in space it is not sufficient to give a position and a speed: you need a *direction* as well. Therefore we work with *vectors*: mathematical objects that have both a *magnitude* and a *direction*. If you tell me you're moving, I know something, but not much; I'll know more if you tell me you're moving at walking speed, and have full information of your velocity once you tell me that you're moving at walking speed towards the coffee machine. Although in principle we could make do with specifying a magnitude and direction of every vector in this way, it is often more convenient to express our vectors in a *basis*. To do so, we choose an (arbitrary) origin, and as many basis vectors as we have spatial dimensions, in such a way that they are not parallel to one another, and usually mutually perpendicular (orthogonal) and of unit length (orthonormal). Then we *decompose* our vector by giving its *components* along each of the basis vectors. The most common choice is to use a Cartesian basis, of two or three (depending on spatial dimension) basis vectors of unit length pointing in the standard $x$, $y$ and $z$ directions, and indicated as $\bm{\hat{x}}$, $\bm{\hat{y}}$ and $\bm{\hat{z}}$, or (rather annoyingly) sometimes as $\bm{i}$, $\bm{j}$ and $\bm{k}$, the latter especially in American textbooks. Other often encountered systems are polar coordinates (2D) and cylindrical and spherical coordinates (3D). To write our vectors, we now specify the components in each direction, writing for example $\bm{v} = 3 \bm{\hat{x}} + 3 \bm{\hat{y}}$ for a vector (in boldface) representing a speed of $3\sqrt{2}$ and a direction making an angle of $45^\circ$ with the horizontal.

Vectors can be added and subtracted just like scalars - simply add and subtract them by component. Graphically, you add two vectors by putting them head-to-tail: you can find the sum of two vectors $\bm{v}$ and $\bm{w}$ by putting the start of $\bm{w}$ at the end of $\bm{v}$, the sum $\bm{v}+\bm{w}$ then points from the start of $\bm{v}$ to the end of $\bm{w}$. You can also multiply a vector by a scalar, by multiplying every component of the vector with that scalar. Graphically, this means that you extend the length of the vector with the scalar factor you just multiplied with.

```{figure} images/appendices/vectorprodsderivs.svg
:name: fig:vectorprodsderivatives
Products and derivatives of vectors. (a) The dot product of two vectors $\bm{a}$ and $\bm{b}$ gives the length of the projection of $\bm{a}$ in the direction of $\bm{b}$ (or vice versa). (b) The cross product of two vectors $\bm{a}$ and $\bm{b}$ gives a vector perpendicular to the plane spanned by $\bm{a}$ and $\bm{b}$ and with a magnitude equal to the area of the parallelogram spanned by $\bm{a}$ and $\bm{b}$. (c-f) Acceleration as a change in velocity. In every panel, the original velocity is shown in black, the velocity a short time $\Delta t$ later is shown in blue, and the acceleration is shown in red. (c) Acceleration for an increase in the magnitude of the velocity. (d) Acceleration for a decrease in the magnitude of the velocity. (e) Acceleration for a change in direction of the velocity at constant magnitude. (f) Acceleration for a change in velocity that involves both a change in direction and a decrease in magnitude.
```

You can't take the product of two vectors like you would two scalars. There are however two vector operations that closely resemble the product, known as the inner (or dot) and outer (or cross) product, see {numref}`fig:vectorprodsderivatives`. The dot product represents the length of the projection of one vector on another (and thus gives a scalar); it is zero for perpendicular vectors, and the dot product of a vector with itself gives the square of its length. To calculate the dot product of two vectors, sum the products of their components: if $\bm{v} = v_x \bm{\hat{x}} + v_y \bm{\hat{y}}$ and $\bm{w} = w_x \bm{\hat{x}} + w_y \bm{\hat{y}}$, then $\bm{v} \cdot \bm{w} = v_x w_x + v_y w_y$. You can use the dot product to find the angle between two vectors, using standard geometry, which gives

$$
\cos \theta = \frac{\bm{v} \cdot \bm{w}}{|\bm{v}| |\bm{w}|} = \frac{v_x w_x + v_y w_y}{|\bm{v}| |\bm{w}|},
$$

where $|\bm{v}|$ and $|\bm{w}|$ are the lengths of vectors $\bm{v}$ and $\bm{w}$, respectively. The cross product is only defined for three-dimensional vectors, say $\bm{v} = v_x \bm{\hat{x}} + v_y \bm{\hat{y}} + v_z \bm{\hat{z}}$ and $\bm{w} = w_x \bm{\hat{x}} + w_y \bm{\hat{y}} + w_z \bm{\hat{z}}$. The result is another vector, with a direction perpendicular to the plane spanned by $\bm{v}$ and $\bm{w}$, and a magnitude equal to the area of the parallelogram bounded by them. The cross product is most easily expressed in column vector form:

$$
\bm{v} \times \bm{w} = \begin{pmatrix} v_x \\ v_y \\ v_z \end{pmatrix} \times \begin{pmatrix} w_x \\ w_y \\ w_z \end{pmatrix} = \begin{pmatrix} v_y w_z - v_z w_y \\ v_z w_x - v_x w_z \\ v_x w_y - v_y w_x \end{pmatrix}.
$$ (crossproduct)

The cross product of a vector with itself is zero.

Vectors can be *functions*, just like scalar quantities: they can depend on one or more parameters, like position or time. Also, again just like scalar functions, you can calculate a *rate of change* of vector function as you move through parameter values, for instance asking how the velocity of a car changes as a function of time. An instantaneous rate of change is simply a derivative, which is calculated in exactly the same manner as the derivative of a scalar function. For example, the rate of change of the velocity, known as the *acceleration*&nbsp;$\bm{a}$, is defined as:

$$
\bm{a} = \lim_{\Delta t \to 0} \frac{\bm{v}(t+\Delta t) - \bm{v}}{\Delta t}.
$$ (defacceleration)

Since the velocity itself is the derivative of the *position*&nbsp;$\bm{x}(t)$, the acceleration is also the second derivative of the position. Time derivatives occur so frequently in classical mechanics that we use a special notation for them: a first derivative is indicated by a dot on top of the quantity, and a second derivative by a double dot - so we have $\bm{a} = \dot{\bm{v}} = \ddot{\bm{x}}$.

Vector derivatives are somewhat richer than those of scalar functions, since there are more ways that a vector can change. Like a scalar function, the magnitude of a vector can increase or decrease. Moreover, its direction can also change, which also means that it has a nonzero derivative, and of course, you can have a combination of a change in magnitude and a change in direction, see {numref}`fig:vectorprodsderivatives`. We'll discuss them in more detail in {numref}`sec:multivariatecalculus`.

(appsec:polarcoords)=
## Polar coordinates

You can specify any point in the plane by specifying its projection on two perpendicular axes - we typically call these the $x$ and $y$-axes and $x$ and $y$ coordinates. In this Cartesian system (named after Descartes), we identify *unit vectors* $\bm{\hat{x}}$ and $\bm{\hat{y}}$, pointing along their respective axes, and being of unit length. A position $\bm{r}$ can then be decomposed in the two directions: $\bm{r} = r_x \bm{\hat{x}} + r_y \bm{\hat{y}}$, with $r_x = \bm{r}\cdot\bm{\hat{x}}$ and $r_y = \bm{r}\cdot\bm{\hat{y}}$. Alternatively, we can write $\bm{\hat{x}} = \begin{pmatrix} 1 \\ 0 \end{pmatrix}$ and $\bm{\hat{y}} = \begin{pmatrix} 0 \\ 1 \end{pmatrix}$, which gives for $\bm{r}$:

```{math}
\bm{r} = r_x \bm{\hat{x}} + r_y \bm{\hat{y}} = \begin{pmatrix} r_x \\ r_y \end{pmatrix}.
```

Instead of specifying the $x$ and $y$ coordinates of our position, we could also uniquely identify it by giving two different numbers: its distance to the origin&nbsp;$r$, and the angle&nbsp;$\theta$ the line to the origin makes with a fixed reference axis (typically the $x$-axis), see {numref}`fig:polarcoordinates`. Invoking the Pythagorean theorem and basic trigonometry, we readily find $r = \sqrt{r_x^2 + r_y^2}$ and $\tan\theta = r_y/r_x$. We call $r$ the length of the vector $\bm{r}$. We could also invert the relations for $r$ and $\theta$ so we can get the Cartesian components if the length and angle are known: $r_x = r \cos\theta$ and $r_y = r\sin\theta$.

```{figure} images/appendices/polarcoordinates.svg
:name: fig:polarcoordinates
:width: 300px
Polar coordinate system and polar unit vectors. A position $\bm{r}$ in the plane can be specified either by giving its projections on two reference axes (along the $\bm{\hat{x}}$ and $\bm{\hat{y}}$ direction), or by giving its distance $r$ to the origin, and the angle&nbsp;$\theta$ the line to the origin makes with the $x$ axis. The polar basis vectors are defined as pointing in the direction of increasing $r$ (i.e., radially outward), and increasing&nbsp;$\theta$ (i.e., rotating counterclockwise around the origin).
```

Like the Cartesian basis vectors $\bm{\hat{x}}$ and $\bm{\hat{y}}$, which point in the direction of increasing $x$ and $y$ values, we can also define unit vectors pointing in the direction of increasing $r$ and $\theta$. These directions do depend on our position in space, but they do have a clear geometrical interpretation: $\bm{\hat{r}}$ always points radially outward from the origin, and $\bm{\hat{\theta}}$ in the direction you'd move if you'd be making a counterclockwise rotation about the origin. Given a position vector $\bm{r}$, finding the vector in the direction of increasing $r$ is very easy: $\bm{\hat{r}} = \bm{r} / r$. The expression for $\bm{r}$ in our new polar basis $(\bm{\hat{r}}, \bm{\hat{\theta}})$ is almost tautological: $\bm{r} = r \bm{\hat{r}}$.

Relating the polar basis vectors to the Cartesian ones is straightforward. We have:

```{math}
\bm{r} = r_x \bm{\hat{x}} + r_y \bm{\hat{y}} = r \bm{\hat{r}},
```

and using $r_x = r \cos\theta$, $r_y = r \sin\theta$ we also have

```{math}
\bm{r} = r \cos\theta \bm{\hat{x}} + r \sin\theta \bm{\hat{y}}.
```

We thus find that $\bm{\hat{r}} = \cos\theta \bm{\hat{x}} + \sin\theta \bm{\hat{y}}$. For $\bm{\hat{\theta}}$ we note that to rotate around the origin, the direction of motion needs to be perpendicular to $\bm{\hat{r}}$. There are of course two such directions. We pick the sign by demanding that the counterclockwise rotation is positive. This convention gives $\bm{\hat{\theta}} = (r_y/r) \bm{\hat{x}} - (r_x/r) \bm{\hat{y}} = \sin\theta \bm{\hat{x}} - \cos\theta \bm{\hat{y}}$. Written out as vectors, we have:

$$
\bm{\hat{r}} = \begin{pmatrix} \cos\theta \\ \sin\theta \end{pmatrix}, \qquad \bm{\hat{\theta}} = \begin{pmatrix} \sin\theta \\ -\cos\theta \end{pmatrix}.
$$ (polarbasisvectors)

Note that

$$
\bm{\hat{r}} = \frac{\partial \bm{\hat{\theta}}}{\partial \theta}, \qquad \bm{\hat{\theta}} = -\frac{\partial \bm{\hat{r}}}{\partial \theta}.
$$ (polarbasisvectorderivatives)

Naturally, we can also express the Cartesian basis in terms of the polar ones:

```{math}
:label: Cartesianbasisvectorsintermsofpolar
\begin{align*}
\bm{\hat{x}} &= \cos\theta \bm{\hat{r}} + \sin\theta \bm{\hat{\theta}}, \\
\bm{\hat{y}} &= \sin\theta \bm{\hat{r}} - \cos\theta \bm{\hat{\theta}}.
\end{align*}
```

```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter6/c6q1.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```


## Systems of linear equations

```{index} linear algebra
```
Linear algebra is the study of systems of linear equations. We frequently encounter such systems when studying relations between vectors; treating each of the components of the vectors as an independent variable, an equation between two vectors becomes a system of three equations in three-dimensional space. Naturally, these equations will in general not be linear, but just like in one-dimensional systems, nonlinear systems can sometimes be approximated by linear ones (through a Taylor series expansion). Moreover, in several examples the equations are linear; important cases include the harmonic oscillator in classical mechanics, the diffusion equation in thermodynamics, and the Schr\"odinger equation in quantum mechanics.

To keep things simple, we'll discuss two-dimensional systems mostly; all ideas generalize to multiple dimensions. If we have two vectors $\bm{x} = (x_1, x_2)$ and $\bm{y} = (y_1, y_2)$ that are linearly related to each other, we can write for the components:

```{math}
:label: generallinearsystem
\begin{align*}
x_1 &= a_{11} y_1 + a_{12} y_2, \\
x_2 &= a_{21} y_1 + a_{22} y_2,
\end{align*}
```

where $a_{11}$, $a_{12}$, $a_{21}$ and $a_{22}$ are the various proportionality constants. If we know $y_1$ and $y_2$, we can calculate $x_1$ and $x_2$; if we know $x_1$ and $x_2$, we can solve for $y_1$ and $y_2$ by elimination. For two-dimensional systems this is fairly straightforward, but things can get complicated quickly if we have more components, so a more systematic approach can be useful. To start, we re-write equation&nbsp;{eq}`generallinearsystem` in terms of vectors and a matrix

$$
\begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix}
a_{11} & a_{12} \\ a_{21} & a_{22}
\end{pmatrix} \begin{pmatrix} y_1 \\ y_2 \end{pmatrix}
$$ (generallinearsystemmatrixform)

Equation&nbsp;{eq}`generallinearsystemmatrixform` requires a rule for calculating the product of the matrix with the vector. The rule is simple: we get a new vector, for which each component is the dot product between the corresponding row of the matrix with the whole vector behind it. That rule exactly reproduces equation&nbsp;{eq}`generallinearsystem` from equation&nbsp;{eq}`generallinearsystemmatrixform`.

We can now write equation&nbsp;{eq}`generallinearsystemmatrixform` more concisely as

$$
\bm{x} = A \bm{y},
$$ (basicmatrixequation)

where $A$ is the matrix with coefficients $a_{ij}$. Note that we label coefficients of a matrix with two indexes, the first ($i$) for the row, the second ($j$) for the column. Equations&nbsp;{eq}`generallinearsystem`, {eq}`generallinearsystemmatrixform` and {eq}`basicmatrixequation` can now all be written as

$$
x_i = \sum_{j=1}^2 a_{ij} y_j.
$$

Given a system of linear equations written in matrix form, $\bm{x} = A \bm{y}$, we can solve for $\bm{y}$ in a systematic manner by sequential elimination. To show how this works, it is easiest to give an example, which we'll do for a three-dimensional system as otherwise the method is almost tautological.

````{prf:example} solving a system of linear equations
:label: sec:solvematrixequation
:class: example
Suppose we have a system of the form&nbsp;{eq}`basicmatrixequation` where the matrix $A$ and vector $\bm{x}$ are given by
```{math}
:label: linalgexample1A
A = \begin{pmatrix}
1 & 2 & 3 \\ 3 & 1 & 1 \\ 1 & -3 & 1
\end{pmatrix},
\qquad \text{and} \qquad
\bm{x} = \begin{pmatrix}
5 \\ 4 \\ 3
\end{pmatrix}.
```
Find $\bm{y}$.

---
**Solution**
The equation $\bm{x} = A \bm{y}$ now stands for three linear equations. We can add and subtract these equations at will from each other, and retain valid equations. We will do so successively to simplify the equations to the point where we can read of the answer. First, we'll do it with the equations themselves, then in matrix notation. We have
```{math}
:label: linalgexample1B
\begin{align*}
5 &= y_1 + 2 y_2 + 3 y_3, \\
4 &= 3y_1 + y_2 + y_3, \\
3 &= y_1 - 3y_2 + y_3.
\end{align*}
```
If we subtract the first equation from the third, we eliminate $y_1$ form the third equation. Likewise, if we subtract the first equation three times from the second, we eliminate $y_1$ from that equation. The resulting set of equations reads
```{math}
:label: linalgexample1C
\begin{align*}
5 &= y_1 + 2 y_2 + 3 y_3, \\
-11 &= 0 - 5y_2 - 8 y_3, \\
-2 &=  0 - 5y_2 - 2y_3.
\end{align*}
```
We can now eliminate $y_2$ from the third equation by subtracting the second equation from it, which gives an equation with $y_3$ alone:
```{math}
:label: linalgexample1D
\begin{align*}
5 &= y_1 + 2 y_2 + 3 y_3, \\
-11 &= 0 - 5y_2 - 8 y_3, \\
9 &=  0 + 0 + 6y_3.
\end{align*}
```
We can now read off that $y_3 = \frac32$. We can either again combine the third equation with the second to eliminate $y_3$ from the second, or simply substitute our found solution, which gives $y_2 = -\frac15$. Substituting both $y_2$ and $y_3$ in the first equation we find that $y_1 = \frac{9}{10}$.
Note that we needn't have kept the order of the equations, we could have shuffled them if that made life easier. However, we need not, as we can always solve the system of equations by sequentially eliminating terms this way. To simplify notation, we can write the steps in equations {eq}`linalgexample1B`-{eq}`linalgexample1D` as a combination of a matrix and a vector:
```{math}
:label: linalgexample1E
\left( \begin{matrix}
1 & 2 & 3 \\ 3 & 1 & 1 \\ 1 & -3 & 1
\end{matrix} \, \middle| \,
\begin{matrix}
5 \\ 4 \\ 3
\end{matrix} \right) \sim \left( \begin{matrix}
1 & 2 & 3 \\ 0 & -5 & -8 \\ 0 & -5 & -2
\end{matrix} \, \middle| \,
\begin{matrix}
5 \\ -11 \\ -8
\end{matrix} \right) \sim \left( \begin{matrix}
1 & 2 & 3 \\ 0 & -5 & -8 \\ 0 & 0 & 6
\end{matrix} \, \middle| \,
\begin{matrix}
5 \\ -11 \\ 9
\end{matrix} \right).
```
The steps in equation&nbsp;{eq}`linalgexample1E` are the same as before, it's just less writing. The symbol $\sim$ is used to indicate that the systems of equations corresponding to the matrix-vector combination are similar, i.e., they have the same solution.

````

## Matrix multiplication and inverse
Matrices can be multiplied. If the vector&nbsp;$\bm{y}$ depends linearly on another vector $\bm{z}$ through $\bm{y} = B \bm{z}$ with $B$ another matrix with coefficients $b_{jk}$, then $\bm{x}$ will depend linearly on $\bm{z}$ through

$$
x_i = \sum_{j=1}^2 a_{ij} y_j = \sum_{j=1}^2 a_{ij} \left( \sum_{k=1}^2 b_{jk} z_k \right) = \sum_{j=1}^2 \sum_{k=1}^2 a_{ij} b_{jk} z_k,
$$

or in matrix notation

$$
\bm{x} = A B \bm{z}.
$$

The combination $A B$ defines a new matrix $C$, where the element $c_{ik}$ on the $i$th row and $k$th column of $C$ is the dot product of the $i$th row of $A$ with the $k$th column of $B$:

$$
c_{ik} = \sum_{j=1}^2 a_{ij} b_{jk}.
$$

Two matrices $A$ and $B$ can be multiplied if the number of columns of $A$ equals the number of rows of $B$; the resulting matrix $A B$ will have the same number of rows as $A$ and the same number of columns as $B$. In practice we will mostly deal with square matrices, for which the number of rows and columns is equal. Like 'regular' multiplication of numbers (sometimes also referred to as 'scalars', to distinguish them from vectors and matrices), matrix multiplication is associative: $(AB) C = A (BC)$ for any three matrices $A$, $B$ and $C$. However, matrix multiplication is in general not commutative, meaning that the ordering of the matrices in the multiplication matters, i.e. (in general) $A B \neq B A$. 

```{index} matrix ; transpose
```
The *transpose* of a matrix $A$, denoted $A^\mathrm{T}$, is the same matrix with all elements reflected in the main diagonal, running from the top left to bottom right. For our two-dimensional example matrix $A$ in equation&nbsp;{eq}`generallinearsystemmatrixform`, the transpose is thus given by

$$
A = \begin{pmatrix}
a_{11} & a_{12} \\ a_{21} & a_{22}
\end{pmatrix} \qquad \Rightarrow \qquad A^\mathrm{T} = \begin{pmatrix}
a_{11} & a_{21} \\ a_{12} & a_{22}
\end{pmatrix}.
$$ (matrixtranspose2D)

A *symmetric* matrix is equal to its transpose, while a *skew symmetric* matrix equals minus its transpose (and thus necessarily has all zeros on its diagonal). The transpose of the product of two matrices is the reversed-order product of the transposes, i.e. $(AB)^\mathrm{T} = B^\mathrm{T} A^\mathrm{T}$.

```{index} inverse matrix, matrix ; inverse
```
In some cases, matrices can be *inverted*. To define the inverse, we first need the concept of the identity matrix&nbsp;$I$: a square matrix with all diagonal elements $1$ and all others $0$; if $\bm{x} = I \bm{y}$, then $\bm{x} = \bm{y}$. The inverse of a matrix $A$ is the matrix that, when multiplied with $A$, gives the identity matrix $I$. We denote the matrix inverse of $A$ as $A^{-1}$, and we thus have $A^{-1} A = I$. As you can easily prove (see {numref}`pb:matrixinverseproperties`), the ordering in the multiplication in this case doesn't matter; also $A$ is the inverse of $A^{-1}$. If the inverse is defined, we can use it to solve equation&nbsp;{eq}`basicmatrixequation`, simply by multiplying both sides by $A^{-1}$:

```{math}
\begin{align*}
\bm{x} &= A \bm{y}\\
A^{-1} \bm{x} &= A^{-1} A \bm{y} = I \bm{y} = \bm{y}.
\end{align*}
```

```{index} orthogonal matrix, matrix ; orthogonal matrix
```
Matrices for which the inverse equals the transpose are known as *orthogonal matrices*.

Finding an explicit expression for the inverse of a matrix goes analogously to solving the system of equations, except that we don't put the known on the right-hand side, but the identity matrix. Again, an example will most easily illustrate how this works; we'll take a two-dimensional example here.

````{prf:example} finding the inverse of a matrix
:label: sec:matrixinverseconstruction
:class: example
Find the inverse of the matrix
```{math}
:label: linalgexample2A
A = \begin{pmatrix}
2 & 1 \\ 2 & 4
\end{pmatrix}.
```

---
**Solution**
We write the matrix $A$ in combination with the identity matrix, then apply row-reduction until we've reduced $A$ itself to the identity matrix.
```{math}
:label: linalgexample2B
\begin{align*}
\left( \begin{matrix}
2 & 1 \\ 2 & 4 
\end{matrix}\, \middle| \, \begin{matrix}
 1 & 0 \\ 0 & 1
\end{matrix} \right) \sim \left( \begin{matrix}
2 & 1 \\ 0 & 3 
\end{matrix}\, \middle| \, \begin{matrix}
 1 & 0 \\ -1 & 1
\end{matrix} \right) \sim \left( \begin{matrix}
2 & 1 \\ 0 & 1 
\end{matrix}\, \middle| \, \begin{matrix}
 1 & 0 \\ -\frac13 & \frac13
\end{matrix} \right) \sim \left( \begin{matrix}
2 & 0 \\ 0 & 1 
\end{matrix}\, \middle| \, \begin{matrix}
 \frac43 & -\frac13 \\ -\frac13 & \frac13
\end{matrix} \right) \sim \left( \begin{matrix}
1 & 0 \\ 0 & 1 
\end{matrix}\, \middle| \, \begin{matrix}
 \frac23 & -\frac16 \\ -\frac13 & \frac13
\end{matrix} \right),
\end{align*}
```
where in the first step we subtracted the first row from the second, in the second step we divided the second row by $3$, in the third step we subtracted the second row from the first, and in the last step we divided the first row by $2$. We can now read off that the inverse of $A$ is given by
```{math}
:label: linalgexample2C
A^{-1} = \begin{pmatrix}
\frac23 & -\frac16 \\ -\frac13 & \frac13
\end{pmatrix} = \frac16 \begin{pmatrix}
4 & -1 \\ -2 & 2
\end{pmatrix}.
```

````

(sec:lineartransformations)=
## Matrices as linear transformations

One way to interpret matrices is as linear maps<sup>[^1]</sup>, transforming any given vector $\bm{y}$ into another one $\bm{x}$ by equation&nbsp;{eq}`basicmatrixequation`. A good example is the rotation matrix in two dimensions, $R(\theta)$, which we can write as

$$
R(\theta) = \begin{pmatrix}
\cos(\theta) & -\sin(\theta) \\ \sin(\theta) & \cos(\theta)
\end{pmatrix}.
$$ (rotationmatrix)

Note that if we apply<sup>[^2]</sup> $R(\theta)$ to the unit vector in the positive $x$ direction, $\bm{\hat{x}}$, we rotate it (counter-clockwise) over an angle $\theta$; in particular, for $\theta = \pi/2$, we get the unit vector in the positive $y$ direction, $\bm{\hat{y}}$. Naturally, we can apply multiple rotations, and also rotate in the opposite direction; we find that $R(\theta) R(\phi) = R(\theta + \phi)$ and $R(-\theta) = \big(R(\theta)\big)^{-1}$. The rotation matrix does not change the length of the vector it acts on, only its angle. Likewise, we can define a transformation matrix that changes the length of the vector, but not its direction; this transformation is simply a number times the identity matrix, with the number equal to the change in length. We could also reflect the vector in either axis (or any arbitrary axis in the plane). Rotation, scaling and reflection are three qualitatively different linear transformations, that all have obvious inverse operations. As it turns out, you can write any transformation of the plane as a combination of these three. The collection of all linear transformations of the plane is known as the general linear group, denoted $GL(2)$. Not all $2 \times 2$ matrices represent a linear transformation; a matrix that has no inverse (known as a singular or degenerate matrix) cannot represent such a transformation. Therefore, it is useful to be able to classify all matrices into invertible and singular ones. From the method of constructing the inverse in {prf:ref}`sec:matrixinverseconstruction` we can get a condition immediately: the columns of $A$ should not be sums or multiples of one another, that is, they should be *linearly independent*. A vector $\bm{y}$ is linearly dependent on a collection of other vectors, $\lbrace\bm{y}_k\rbrace$ (with $k$ an arbitrary integer), if there are numbers $a_k$ such that

$$
\bm{y} = \sum_k a_k \bm{y}_k.
$$ (lineardependence)

It is easy to see that if the columns are not linearly independent, we cannot construct the inverse of the matrix, and thus linear independence of the columns is a necessary condition for the inverse to exist. It turns out also to be a sufficient condition, which we can prove by starting from the opposite side. Suppose we have an invertible matrix $A$, and consider the equation $A \bm{x} = \bm{0}$. Because $A$ is invertible, it follows trivially that the only solution to this equation is $\bm{x} = \bm{0}$ (simply multiply both sides with $A^{-1}$). However, if the columns of $A$ were linearly dependent, then by equation&nbsp;{eq}`lineardependence`, there would also be another solution (taking for $\bm{x}$ minus the values of the coefficients in the sum expressing one column in terms of the others), and thus, we have arrived at a contradiction. Therefore, the columns of the invertible matrix&nbsp;$A$ are linearly independent.

For an $n$-dimensional space, you can always write down exactly $n$ linearly independent vectors. If you're using Cartesian basis vectors, it is almost trivial to see that this is true: in $\mathbb{R}^n$, there are $n$ Cartesian basis vectors, which are linearly independent, and all other vectors are written as linear combinations of the $n$ basis vectors. Extending on this notion, we can take *any* set of $n$ vectors that are linearly independent of each other as a basis; all other vectors can then always be expressed as linear combinations of our chosen basis. As we'll see below, in many cases the Cartesian basis vectors are not the easiest choice; instead, we can often choose a set of basis vectors for which our linear transformations become simple operations. These vectors will be the *eigenvectors* of the transformation, which we'll define in {numref}`sec:matrixeigenvalues`.

(sec:determinant)=
## Volume element and determinant

```{index} determinant, matrix ; determinant
```
If the column vectors of a matrix&nbsp;$A$ are independent, they together create a *volume element* with which we can tile the space; in two dimensions this volume element is a parallelogram, in three or more dimensions it is a parallelepiped. The volume of this volume element can be calculated directly from the matrix; it defines a property of the matrix known as its *determinant*, denoted either as $\det(A)$ or simply $|A|$. The determinants of $2 \times 2$ and $3 \times 3$ matrices can be calculated as

```{math}
:label: matrixdeterminants
\begin{align*}
\begin{vmatrix}
a & b \\ c & d
\end{vmatrix} &= ad - bc \\
\begin{vmatrix}
a & b & c \\ d & e & f \\ g & h & i
\end{vmatrix} &= a \begin{vmatrix} e & f \\ h & i \end{vmatrix} - b \begin{vmatrix} d & f \\ g & i \end{vmatrix} + c \begin{vmatrix} d & e \\ g & h \end{vmatrix} = a e i + b f g + c d h - c e g - b d i - a f h.
\end{align*}
```

Each determinant of a $2 \times 2$ matrix in equation&nbsp;{eq}`matrixdeterminants`B is called a *minor* of the original $3 \times 3$ matrix. The construction extends to higher-dimensional matrices. The determinant of an $n \times n$ matrix&nbsp;$A$ is given iteratively in terms of its minors $M_{i,j}$, which themselves are the determinants of the $(n-1) \times (n-1)$ matrices you get when deleting row&nbsp;$i$ and column&nbsp;$j$ from $A$. The determinant of $A$ is then

$$
\det(A) = \sum_{j=1}^n (-1)^{i+j} a_{ij} M_{i,j},
$$ (matrixdeterminantN)

where, as before, $a_{ij}$ is the element on row $i$ and column&nbsp;$j$ of $A$. Equation&nbsp;{eq}`matrixdeterminantN` is known as the Laplace expansion of the determinant.

In practice, there are some tricks for making the calculation of determinants faster (e.g. by wisely choosing which row to take first in the first step of equation&nbsp;{eq}`matrixdeterminants`B, as a row with many zeros will have fewer minors to compute). Also, it is easy to prove that $\det(A) = \det(A^\mathrm{T}) = 1/\det(A^{-1})$ and that $\det(AB) = \det(A) \det(B)$ for square matrices $A$ and $B$ of equal size (see {numref}`pb:matrixdeterminants`). Finally, for a matrix with columns that are linearly dependent, we always get $\det(A) = 0$, while for a matrix with linearly independent columns, we have $\det(A) \neq 0$. Therefore, the condition that $A$ is invertible is equivalent to the condition that its determinant in nonzero. Moreover, if the determinant of a matrix equals $\pm 1$, the corresponding linear transformation is *volume-conserving*.

The general linear group, $GL(n)$, consists of all $n \times n$ matrices with nonzero determinant. The special linear group $SL(n)$ is the smaller subgroup of all $n \times n$ matrices with determinant $+1$. The orthogonal group (sometimes called the general orthogonal group) $O(n)$ are all the $n \times n$ matrices for which the transpose equals the inverse, i.e., all matrices $A$ for which $A A^\mathrm{T} = A^\mathrm{T} A = I$. From the definition, it is easy to see that all matrices in the orthogonal group have determinant $\pm 1$ and are thus volume-conserving. The elements of $O(n)$ represent rotations and reflections. The subgroup of matrices with determinant $+1$ is known as the special orthogonal group $SO(n)$; $SO(2)$ is the collection of rotations of the form&nbsp;{eq}`rotationmatrix`, therefore also known as the circle group.

(sec:matrixeigenvalues)=
## Eigenvalues and eigenvectors

General linear transformations are combinations of stretches, rotations, and reflections. It is often useful to decompose these operations, in a wide range of applications. An obvious one is the deformation of a piece of material: there, we are interested in the stretch, but not in the rotation (rotating a rubber band doesn't require any work, but stretching it does). A more mathematical application is solving a system of coupled differential equations, as for example in  the coupled harmonic oscillators in {numref}`sec:coupledoscillators`. There are many others, including data analysis (determining the most important component of a system, known as principal component analysis), quantum mechanics, and computer graphics.

If a matrix represents a stretching operation, it multiplies the elements of a vector by a scalar value. Such an operation can be written as

$$
A \bm{v} = \lambda \bm{v}.
$$ (eigenvalueequation)

```{index} matrix ; eigenvalues, eigenvalues, matrix ; eigenvectors, eigenvectors
```
In equation&nbsp;{eq}`eigenvalueequation`, $\lambda$ is the amount of stretch, and $\bm{v}$ the direction in which the stretch is applied. If $\lambda = 1$, there is no stretch; if $\lambda = -1$, there is a reflection. Rather than using the scale&nbsp;$\lambda$ and direction $\bm{v}$ to define the linear transformation in $A$, for a general linear transformation, we can look for values of $\lambda$ and $\bm{v}$ that satisfy equation&nbsp;{eq}`eigenvalueequation`. These values and vectors are known as the *eigenvalues* and *eigenvectors* of $A$, respectively<sup>[^3]</sup>.

While equation&nbsp;{eq}`eigenvalueequation` is motivated by the geometric interpretation of a matrix as a linear transformation, it also works for matrices with determinant zero. As we'll see, for such a non-invertible matrix, we'll get a zero eigenvalue, though they may still have nonzero eigenvalues as well. In general, for an $n \times n$ matrix $A$, there will be $n$ solutions, i.e., $n$ sets of eigenvalues and eigenvectors $\lambda_i, \bm{v}_i$; however, not all eigenvalues have to be different.

To find the eigenvalues and eigenvectors of a matrix $A$, we start from equation&nbsp;{eq}`eigenvalueequation`. First, we multiply the right-hand side with the $n \times n$ identity matrix $I$, then move it to the left-hand side, so we get

$$
A \bm{v} - \lambda I \bm{v} = \left( A - \lambda I \right) \bm{v} = \bm{0}.
$$ (eigenvalueequation2)

Now, as we've seen in {numref}`sec:lineartransformations`, the only way that equation&nbsp;{eq}`eigenvalueequation2` has a solution (outside the trivial $\bm{v} = \bm{0}$) is if the matrix multiplying $\bm{v}$ is not invertible, i.e., if its determinant equals zero. Therefore, the eigenvalues of the matrix $A$ are given by the *characteristic equation*

$$
\det\left( A - \lambda I \right) = 0.
$$ (characteristicequation)

In general, the characteristic equation of an $n \times n$ matrix is an $n$th order polynomial. By the fundamental theorem of algebra, this polynomial will have $n$ roots (which we can label&nbsp;$\lambda_i$), which in general may be complex numbers. They need not all be unique; the *algebraic multiplicity* of an eigenvalue $\lambda_i$ is the number of times it occurs as a solution of the characteristic equation (formally, the maximum number of times that you can divide the polynomial by $(\lambda - \lambda_i)$).

With each eigenvalue&nbsp;$\lambda_i$ comes an eigenvector&nbsp;$\bm{v}_i$; if an eigenvalue has an algebraic multiplicity larger than one, it can have multiple eigenvectors. The number of linearly independent eigenvectors corresponding to a given eigenvalue is called the *geometric multiplicity* of the eigenvalue. The geometric multiplicity equals the dimension of the corresponding *eigenspace*, which is the (sub)space of which the eigenvectors are the basis. The geometric multiplicity is always less than or equal to the algebraic multiplicity.

To illustrate how we can find eigenvalues and eigenvectors, an example will again be helpful.

````{prf:example} finding eigenvalues and eigenvectors
:label: sec:findingeigenvalues
:class: example
Find the eigenvalues and eigenvectors of the following matrices:
```{math}
A = \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix}, \qquad B = \begin{pmatrix} 1 & 0 & 1 \\ 0 & 2 & 0 \\ 1 & 0 & 1 \end{pmatrix}.
```

---
**Solution**
For the matrix $A$, we can write down and solve the characteristic equation with ease:
```{math}
0 = \det(A - \lambda I) = \begin{vmatrix} 1-\lambda & 2 \\ 2 & 1-\lambda\end{vmatrix} = (1-\lambda)^2 - 4 = \lambda^2 - 2 \lambda - 3 = (\lambda-3)(\lambda+1),
```
so the roots are $\lambda_1 = 3$ and $\lambda_2 = -1$. To find the corresponding eigenvectors, we substitute the found eigenvalues back into the defining equation&nbsp;{eq}`eigenvalueequation2`. For the first eigenvalue $\lambda_1 = 3$, we then get
```{math}
(A - 3 I) \bm{v} = \begin{pmatrix} -2 & 2 \\ 2 & -2 \end{pmatrix} \begin{pmatrix} v_1 \\ v_2 \end{pmatrix} = \begin{pmatrix} -2v_1 & 2v_2 \\ 2v_1 & -2v_2 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix},
```
so we get two identical equations, both reading $v_1 - v_2 = 0$. Therefore, any vector for which $v_1 = v_2$ is an eigenvector of $A$ with eigenvalue $\lambda_1 = 3$. That makes sense: we can multiply both sides of equation&nbsp;{eq}`eigenvalueequation` with an arbitrary number, so any multiple of an eigenvector will also be an eigenvector. It is therefore sufficient to specify an eigenvector; we can do so either by choosing 'nice' numbers ($v_1 = v_2 = 1$ would do here), or by always normalizing our eigenvectors. With the exact same procedure, we find that for the second eigenvalue $\lambda_2 = -1$, we have $v_1 = -v_2$. The normalized eigenvectors of $A$ are thus
```{math}
\bm{v}_1 = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ 1 \end{pmatrix}, \qquad \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ -1 \end{pmatrix}.
```
To find the eigenvalues of $B$, we also need to find the roots of the characteristic equation, but now we have a third order polynomial. Fortunately, the second column of $B$ contains only zeros; therefore, the equation immediately separates into the product of a first-order and a second-order term:
```{math}
0 = \det(B-\lambda I) = \begin{vmatrix} 1-\lambda & 0 & 1 \\0 & 2-\lambda & 1 \\ 1 & 0 & 1-\lambda\end{vmatrix} = (2-\lambda)[(1-\lambda)^2-1] = (2-\lambda)(\lambda^2 - 2\lambda) = -\lambda (2-\lambda)^2,
```
so we get $\lambda_1 = 0$ and $\lambda_2 = \lambda_3 = 2$ (i.e., an eigenvalue with multiplicity two). From the fact that we get a zero eigenvalue, we can read off (if we had not seen this already) that the matrix&nbsp;$B$ is singular, i.e., it has no inverse (and equivalently, has determinant zero, and columns that are linearly dependent). The corresponding eigenvector can again be found from equation&nbsp;{eq}`eigenvalueequation2`:
```{math}
(B - 0 I) \bm{v} = \begin{pmatrix} 1 & 0 & 1 \\ 0 & 2 & 0 \\ 1 & 0 & 1 \end{pmatrix} \begin{pmatrix}
v_1 \\ v_2 \\ v_3 \end{pmatrix} = \begin{pmatrix} v_1 & 0 & v_3 \\ 0 & v_2 & 0 \\ v_1 & 0 & v_3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix},
```
so we get $v_2 = 0$ and $v_1 = - v_3$. For the other eigenvector, we substitute $\lambda = 2$ in equation&nbsp;{eq}`eigenvalueequation2` again:
```{math}
(B - 2 I) \bm{v} = \begin{pmatrix} -1 & 0 & 1 \\ 0 & 0 & 0 \\ 1 & 0 & -1 \end{pmatrix} \begin{pmatrix}
v_1 \\ v_2 \\ v_3 \end{pmatrix} = \begin{pmatrix} -v_1 & 0 & v_3 \\ 0 & 0 & 0 \\ v_1 & 0 & -v_3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}.
```
Apart from the trivial equation $0 = 0$, we now have $v_1 = v_3$. However, as we've asserted above, there should be two solutions, as the solution $\lambda = 2$ has multiplicity two. Sometimes indeed the procedure we just carried out will give us two solutions, but in this case it seemingly does not. The key is in the 'trivial' equation, which actually reads $0 v_2 = 0$, meaning that *any* vector with *any* value of $v_2$ (and $v_1 = v_3 = 0$) will be an eigenvector - as you can readily check. Therefore, the system of eigenvalues and eigenvectors of $B$ is
```{math}
\lambda_1 = 0 \; \text{with} \; \bm{v}_1 = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ 0 \\ -1 \end{pmatrix} \qquad \text{and} \quad \lambda_2 = 2 \; \text{with} \; \bm{v}_2 = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}\; \text{and} \; \bm{v}_3 = \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}.
```

````

## Eigenvalues of symmetric matrices
As you may have noticed, the matrices in the example above were both symmetric, and their eigenvalues were all real<sup>[^4]</sup>. That is not a coincidence, but a general (and very useful) property, which we can prove rather easily. In a similar fashion, we can prove that for two different eigenvalues of a symmetric matrix, the corresponding eigenvectors are always orthogonal (i.e., perpendicular to each other).

```{prf:theorem}
:label: symmetricmatrixeigenvalues
The eigenvalues of a symmetric matrix&nbsp;$A$ are real.
```

```{prf:proof}
Let $\lambda$ be an eigenvalue of $A$, and $\bm{v}$ the corresponding normalized eigenvector. We then have

$$
\lambda = \lambda \langle \bm{v}, \bm{v} \rangle = \langle \bm{v}, \lambda \bm{v} \rangle = \langle \bm{v}, A \bm{v} \rangle = \langle A^\mathrm{T} \bm{v}, \bm{v} \rangle = \langle A \bm{v}, \bm{v} \rangle = \langle \lambda^* \bm{v}, \bm{v} \rangle = \lambda^* \langle \bm{v}, \bm{v} \rangle,
$$

where the fifth equality is the key step, using that $A = A^\mathrm{T}$. As $\lambda = \lambda^*$, we conclude that $\lambda$ is real.
```

```{prf:theorem}
:label: symmetricmatrixeigenvectors
The eigenvectors corresponding to different eigenvalues of a symmetric matrix&nbsp;$A$ are orthogonal.
```

```{prf:proof}
Let $\lambda$ and $\mu$ be an eigenvalues of $A$, and $\bm{v}$ and $\bm{w}$ the corresponding normalized eigenvectors. We then have

$$
\lambda \langle \bm{w}, \bm{v} \rangle = \langle \bm{w}, \lambda \bm{v} \rangle = \langle \bm{w}, A \bm{v} \rangle = \langle A^\mathrm{T} \bm{w}, \bm{v} \rangle = \langle A \bm{w}, \bm{v} \rangle = \langle \mu^* \bm{w}, \bm{v} \rangle = \mu \langle \bm{w}, \bm{v} \rangle,
$$

where in the fourth equality we again used that $A = A^\mathrm{T}$, and  $\mu = \mu^*$ in the last. Now either $\lambda = \mu$, or $\langle \bm{w}, \bm{v} \rangle = 0$, therefore, if $\lambda \neq \mu$, $\bm{w}$ and $\bm{v}$ are orthogonal.
```

(sec:matrixdiagonalization)=
## Diagonalization

Diagonal matrices (i.e., matrices that only have nonzero entries on their main diagonal, from top-left to bottom-right) are very easy to work with. For example, if a matrix represents an operation that you have to apply multiple times, you need to calculate powers of the matrix, which is computationally expensive, unless the matrix is diagonal. Likewise, finding the inverse and the determinant of a diagonal matrix is much easier than of a general one. Fortunately, if you know the eigenvalues and eigenvectors of a general matrix&nbsp;$A$, there is a way to relate the matrix to a diagonal one, with the eigenvalues as the entries, making calculating powers and inverses a breeze.

Formally, an $n \times n$ matrix&nbsp;$A$ is called *diagonalizable* if there exists an invertible matrix $C$ such that $C^{-1} A C$ is diagonal. We say that $C$ diagonalizes $A$. The diagonal matrix is usually denoted&nbsp;$D$. The matrix transformation $C^{-1} A C = D$ is sometimes referred to as a *similarity transform*; in general, matrices $A$ and $B$ are said to be similar if there exists an invertible matrix $C$ such that $C^{-1} A C = B$.

If you have $n$ eigenvalues $\lambda_i$ and corresponding eigenvectors $\bm{v}_i$ of the matrix $A$, then constructing such a matrix $C$ is easy: it's the $n \times n$ matrix of which the columns are the vectors $\bm{v}_i$. The diagonal matrix $D$ then has $\lambda_i$ as its $i$th entry. To see that this is true, consider the matrix products $AC$ and $CD$. The columns of the matrix $AC$ are the vectors $A \bm{v}_i$. The columns of the matrix $CD$ are the vectors $\lambda_i \bm{v}_i$. Therefore, for $AC$ and $CD$ to be equal, for each value of $i$ we must have $A\bm{v}_i = \lambda_i \bm{v}_i$. Thus, $AC = CD$ if (and only if) the $\lambda_i$ and $\bm{v}_i$ are the eigenvalues and eigenvectors of $A$. Consequently, we indeed have $C^{-1} A C = D$.

The 'and only if' above gives us a criterion for diagonalization: an $n \times n$ matrix $A$ is diagonalizable if it has $n$ linearly independent eigenvectors, i.e., if its eigenvectors form a basis for $\mathbb{R}^n$. Equivalently, we can state that $A$ is diagonalizable if the geometric multiplicity of each eigenvalue equals the algebraic multiplicity of that eigenvalue.

```{index} orthogonal matrix, matrix ; orthogonal matrix
```
If $A$ is a symmetric matrix, by the two theorems in the previous section, its eigenvalues are real, and eigenvectors corresponding to different eigenvalues are orthogonal. There may of course be eigenvalues with multiplicity larger than 1, which therefore have multiple eigenvectors. However, if $A$ is invertible, these eigenvectors are linearly independent, and therefore, we can always construct an equivalent set of orthogonal eigenvectors, using the Gram-Schmidt process (see {numref}`sec:GramSchmidt`). If we normalize all eigenvectors, we get a matrix $C$ with columns that are all orthonormal: their inner product with each other is zero, and with themselves is one (we can write this statement concisely as $\bm{v}_i \cdot \bm{v}_j = \delta_{ij}$). Finding the inverse of $C$ is then trivial, as it is equal to the transpose (and $C$ is thus *orthogonal)*: $C^{-1} = C^\mathrm{T}$, i.e., $C^{-1}$ is the matrix of which the rows are the normalized eigenvectors $\bm{v}_i$.

The above result easily extends to any $n \times n$ matrix $A$ for which all eigenvalues $\lambda_i$ are distinct: in that case, the eigenvectors are linearly independent and the matrix $A$ is diagonalizable. However, in this case the matrix $C$ (which still has the eigenvectors of $A$ as its columns) is not necessarily orthogonal, and thus we need to do an actual calculation to find $C^{-1}$.

As advertised at the start of this section, if a matrix&nbsp;$A$ is diagonalizable by a matrix&nbsp;$C$, calculating $A^k$ is easy:

$$
A^k = (CDC^{-1})^k = CDC^{-1} \cdot CDC^{-1} \cdot \ldots \cdot CDC^{-1} = C D^k C^{-1},
$$

and because $D$ is diagonal, so is $D^k$, with the elements of the diagonal simply the $k$th power of the elements of the diagonal of $D$. Likewise, we can calculate the inverse of $A$ using the diagonalization and the product rule that $(AB)^{-1} = B^{-1} A^{-1}$ (see {numref}`pb:matrixinverseproperties`):

$$
A^{-1} = (CDC^{-1})^{-1} = (C^{-1})^{-1} D^{-1} C^{-1} = C D^{-1} C^{-1},
$$

and the inverse of $D$ is simply the diagonal matrix with on the diagonal the values $1/d_i$ (where $d_i$ is the $i$th element of $D$).

(sec:GramSchmidt)=
## Constructing an orthogonal set of vectors: the Gram-Schmidt process

In {numref}`appsec:vectors` we defined the concept of orthogonal vectors: vectors $\bm{v}$ and $\bm{w}$ are orthogonal if their inner product is zero. Graphically, orthogonal vectors are perpendicular to each other. We can easily extend this notion to a collection of vectors $\{\bm{v}_i\}$; the collection is orthogonal if all the vectors are mutually orthogonal. The collection is *orthonormal* if the vectors are orthogonal and all or unit length. Orthonormal sets of vectors are a convenient choice of basis, as it is easy to express any other vector in the basis: to find the components of a vector $\bm{w}$ in an orthonormal basis set $\{\bm{v}_i\}$, we simply calculate the dot product between $\bm{w}$ and each of the basis vectors $\bm{v}_i$, defining $w_i = \bm{w} \cdot \bm{v}_i$; we then get

$$
\bm{w} = \sum_{i=1}^n w_i \bm{v}_i.
$$

```{index} Gram-Schmidt process
```
As we've seen in {numref}`sec:matrixeigenvalues` and&nbsp;{numref}`sec:matrixdiagonalization`, the eigenvectors of a diagonalizable $n \times n$ matrix are a basis for $\mathbb{R}^n$. However, this basis is not necessarily orthogonal. Fortunately, there is an easy way of constructing an orthogonal set of vectors from any linearly independent set of vectors; we can then turn the set into an orthonormal one by dividing each vector by its length. The idea is pretty simple: we pick a random vector to start with, and for each next vector we pick, we subtract the part of the vector along any vector already in our orthogonal set. To find the parts of the vector along the others, we project on the others, in exactly the same way we found the components of the vector $\bm{w}$ above (which we did by projecting on each of the $\bm{v}_i$). This procedure is known as the *Gram-Schmidt process*.

Written out, the Gram-Schmidt process to create a orthogonal collection of vectors&nbsp;$\{\bm{u}_i\}$ from a collection of linearly independent vectors $\{\bm{v}_i\}$ consists of the following steps:
1. Pick a vector to start with: $\bm{u}_1 = \bm{v}_1$.
1. For each following value of $i$ ($i=2, \ldots, n$), calculate $\bm{u}_i$ as

$$
\bm{u}_i = \bm{v}_i - \sum_{j=1}^{i-1} \frac{\bm{v}_i \cdot \bm{u}_j}{\bm{u}_j \cdot \bm{u}_j} \bm{u}_j.
$$

1. Normalize the vectors $\bm{u}_i$ to get an orthonormal basis (i.e., divide each of the $\bm{u}_i$ by $\sqrt{\bm{u}_i \cdot \bm{u}_i}$).

The Gram-Schmidt process allows us to construct an orthogonal set out of any linearly independent set of vectors. Next to constructing orthogonal bases, it forms the foundation of another very useful procedure, known as $Q R$ factorization. If we have an $n \times n$ matrix $A$ with linearly independent column vectors $\bm{a}_i$, we can use the Gram-Schmidt process to construct an orthogonal set $\{\bm{q}_i\}$ out of the set $\{\bm{a}_i\}$. Naturally, we can express the original vectors $\bm{a}_i$ in the new basis. In particular, we have $\bm{a}_1 = r_1 \bm{q}_1$, $\bm{a}_2 = r_{12} \bm{q}_1 + r_{22}\bm{q}_2$, and so on. If we now define $Q$ as the matrix with column vectors $\bm{q}_i$, and $R$ as the matrix with elements $r_{ij}$, we can write $A = Q R$, where $Q$ has orthonormal column vectors (making $Q$ an orthogonal matrix), and $R$ is *upper-triangular*, meaning that all elements 'below' the diagonal are zero. The factorization is especially useful in numerical applications, as finding the inverse of $R$ is often (much) faster than finding the inverse of $A$.

## Problems
```{exercise} Properties of the matrix inverse.
:label: pb:matrixinverseproperties
:class: dropdown
1. Prove that if $A^{-1}$ is the left-inverse of a matrix $A$ (i.e, $A^{-1} A = I$), then $A^{-1}$ is also the right-inverse of $A$, i.e., $A A^{-1} = I$.
1. Prove that if $A^{-1}$ is the inverse of a matrix $A$, then $A$ is the inverse of $A^{-1}$.
1. Prove that if $A$ and $B$ are invertible $n \times n$ matrices, then $(AB)^{-1} = B^{-1} A^{-1}$.
```

````{exercise} The inverse of a two dimensional matrix
:label: pb:twodimensionalmatrixinverse
:class: dropdown
Show that the inverse of an arbitrary $2 \times 2$ matrix
\[ A = \begin{pmatrix}
a & b \\ c & d
\end{pmatrix} \]
is given by
```{math}
:label: twodimensionalmatrixinverse
A^{-1} = \frac{1}{\det(A)} \begin{pmatrix}
d & -b \\ -c & a
\end{pmatrix}.
```
````

````{exercise} Matrix determinants
:label: pb:matrixdeterminants
:class: dropdown
1. Show that for the $3 \times 3$ matrix in equation&nbsp;{eq}`matrixdeterminants`B, we would have found the same result for the determinant if instead of taking the top row elements times the minors of the bottom block, we would have taken either of the other rows times the minors of the remaining rows.
1. Find the determinants of the following matrices in a way that requires minimal computational effort:
```{math}
\begin{pmatrix}
1 & 1 & 1 \\ 2 & 0 & 0 \\ 3 & 4 & 5
\end{pmatrix}, \qquad \text{and} \qquad 
\begin{pmatrix}
1 & 1 & 1 \\ 2 & 0 & 2 \\ 3 & 3 & 0
\end{pmatrix}
```
1.  Similarly, show that we would have gotten the same result for the determinant if we had taken the elements of the first column times the minors of the block of the other two columns.
1. Conclude from (c) that the determinant of a matrix equals the determinant of its transpose.
1. Extend the calculation of determinants to $4 \times 4$ matrices to determine the determinant of
```{math}
\begin{pmatrix}
1 & 1 & 1 & 1\\ 2 & 0 & 0 & 2\\ 3 & 4 & 5 & 6 \\ 1 & 0 & 0 & 0
\end{pmatrix}.
```
1. Prove that for an $n \times n$ matrix $A$ and a number $c$, we have $\det(c A) = c^n \det(A)$.
````

````{exercise} Matrix eigenvalues
:label: pb:matrixeigenvalues
:class: dropdown
Find the eigenvalues and eigenvectors of
```{math}
A = \begin{pmatrix} 1 & 1 & -2 \\ 0 & 1 & 0 \\ 2 & 1 & 1 \end{pmatrix}.
```
````

[^1]: The mathematical term 'map' is essentially equivalent to the term 'function'.

[^2]: Another mathematical term; 'applying a transformation to a vector' just means multiplying the corresponding matrix with that vector.

[^3]: The names eigenvalue and eigenvector come from German, the word 'eigen' means 'self' or 'own' (according to linguists, 'eigen' and 'own' are cognate, i.e., have the same etymological origin). As it happens, the Dutch and German words for 'eigen' are the same, so the Dutch word for eigenvalue is 'eigenwaarde', which in a different context also means 'self-esteem'.

[^4]: See {numref}`sec:complexnumbers` if you are not familiar with complex numbers.

