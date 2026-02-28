(sec:multivariatecalculus)=
# Multi-variate calculus

```{figure} images/appendices/vectorfields.svg
:name: fig:vectorfields
Examples of scalar and vector fields. (a) Temperature (a scalar) at every point in the Netherlands at 17:30 on March 25, 2025. Lines of equal temperature are drawn in black; the gradient of the temperature field is everywhere perpendicular to these lines. (b) Wind velocity (a vector) at every point in the Netherlands at the same time as the temperature map. Colors correspond to the magnitude of the velocity. (a and b) from&nbsp;<sup>[^1]</sup>, &copy;  KNMI 2025, CC0. (c) Example of a vector field with a large divergence and zero curl. (d) Example of a vector field with a large curl (and low but nonzero divergence).
```

## The gradient operator
Functions (scalar or vector) that are defined at every point in space are sometimes called *fields*. Examples are the temperature (scalar) and wind (vector) at every point on the planet, see {numref}`fig:vectorfields`. Just like you can calculate the rate of change of a function in time, you can also consider how a function changes in space. Fortunately, just like we can decompose a vector in various components, we can do the same with changes in space of a function: we consider the variation with respect to perpendicular directions separately. For example, if we have a function $f(x,y,z)$ that depends on the position in $\mathbb{R}^3$, we can define an '$x$-derivative' of $f$ by looking at how it changes as we change only the $x$ coordinate. As $y$ and $z$ are perpendicular to $x$, their values won't be affected. We call such derivatives with respect to only one of the coordinates *partial derivatives*, which we distinguish from 'regular' derivatives by writing them with a $\partial$ instead of a $\mathrm{d}$.

In general, we will want to consider changes in $f$ under arbitrary displacements, not just along the coordinate axes. Fortunately, in the limit that we take in calculating the derivative, namely that the step size becomes infinitely small, only terms to linear order in the displacements remain, and the change in $f$ simply becomes the sum of the changes in the three coordinate directions. We can therefore relate the change $\mathrm{d}{f}$ in $f$ due to an arbitrary displacement vector $\mathrm{d}{\bm{l}} = \bm{\hat{x}} \mathrm{d}{x} + \bm{\hat{y}} \mathrm{d}{y} + \bm{\hat{z}} \mathrm{d}{z}$ as
```{math}
:label: multivariatedifferential
\begin{align*}
\mathrm{d}{f}  &= \frac{\partial f}{\partial x} \mathrm{d}{x} + \frac{\partial f}{\partial y} \mathrm{d}{y} + \frac{\partial f}{\partial z} \mathrm{d}{z}  \\
&= \left( \frac{\partial f}{\partial x} \bm{\hat{x}} + \frac{\partial f}{\partial y} \bm{\hat{y}} + \frac{\partial f}{\partial z} \bm{\hat{z}} \right) \, \cdot \, \left( \bm{\hat{x}} \,\mathrm{d}{x} + \bm{\hat{y}} \,\mathrm{d}{y} + \bm{\hat{z}} \,\mathrm{d}{z} \right)  \\
&= \left(\bm{\nabla} f\right) \cdot \mathrm{d}{\bm{l}}.
\end{align*}
```
The vector of partial derivatives $\bm{\nabla} f$ is known as the *gradient* of&nbsp;$f$, given by

$$
\bm{\nabla} f = \frac{\partial f}{\partial x} \bm{\hat{x}} + \frac{\partial f}{\partial y} \bm{\hat{y}} + \frac{\partial f}{\partial z} \bm{\hat{z}} = \begin{pmatrix} \partial f/\partial x \\ \partial f/\partial y \\ \partial f/\partial z \end{pmatrix}.
$$ (defgradient)

The operator $\bm{\nabla}$ is known as the gradient operator; its symbol is sometimes called 'nabla'. The direction of the gradient $\bm{\nabla} f$ is the direction of maximal change, and its magnitude tells you how quickly the function changes in that direction. To see why that is the case, we look at the last line of equation&nbsp;{eq}`multivariatedifferential`. If we fix the length of the (function-independent) line element $\mathrm{d}{\bm{l}}$, the inner product is maximal if $\mathrm{d}{\bm{l}}$ points in the same direction as $\bm{\nabla}f$; therefore, the direction of $\mathrm{d}{\bm{l}}$ is the direction in which $\mathrm{d}{f}$ is maximal. The rate of change of $f$ in that direction is then simply the magnitude of $\bm{\nabla}f$.

## Divergence and curl
 For a vector field $\bm{v}$, we can't take the gradient, but we can use the 'vector' $\bm{\nabla}$ of partial derivatives combined with either the dot or cross product. The first option is known as the *divergence* of $\bm{v}$, and tells you how quickly $\bm{v}$ spreads out; the second is the *curl* of $\bm{v}$ and tells you how much $\bm{v}$ rotates:
```{math}
\begin{align*}
\mathrm{div}(\bm{v}) &= \bm{\nabla} \cdot \bm{v} = \frac{\partial v_x}{\partial x} + \frac{\partial v_y}{\partial y} + \frac{\partial v_z}{\partial z}, \\
\mathrm{curl}(\bm{v}) &= \bm{\nabla} \times \bm{v} = \begin{pmatrix} \partial_y v_z - \partial_z v_y \\ \partial_z v_x - \partial_x v_z \\ \partial_x v_y - \partial_y v_x \end{pmatrix},
\end{align*}
```
where $\partial_x = \partial / \partial x$, and so on. {numref}`fig:vectorfields`c shows a vector field with a large divergence and zero curl. In contrast, the vector field plotted in {numref}`fig:vectorfields`d has a large curl.

## The Laplacian operator
The gradient of a scalar function gives us a vector; the divergence of a vector gives us a scalar, and the curl of a vector gives us another vector. These observations allow us to combine our vector derivatives into second derivatives. Fortunately, some of them will always be zero, a fact that comes in extremely handy in many situations in physics. In particular, for any scalar function $f$ and any vector field $\bm{v}$ we have
```{math}
:label: curlofgradient
\begin{align*}
\bm{\nabla} \times \left(\bm{\nabla} f\right) &= 0, \
\end{align*}
```

```{math}
:label: divergenceofcurl
\begin{align*}
\bm{\nabla} \cdot \left(\bm{\nabla} \times \bm{v}\right) &= 0.
\end{align*}
```
In words, both the curl of a gradient and the divergence of a curl always vanish. You can prove both these relations easily by simply writing them out, and using the second-derivative identity

$$
\frac{\partial }{\partial x} \frac{\partial f}{\partial y} = \frac{\partial }{\partial y} \frac{\partial f}{\partial x}.
$$

Less trivial, and very commonly encountered in physics, is the divergence of the gradient. This operator can act on a scalar function; it then yields another scalar function. It could also act on a vector field, by acting on each of the vector's components; the result will be another vector field. The operator is so common that it got its own name, the *Laplacian*. Unfortunately, there are two common ways of denoting the Laplacian: either as a Delta ($\Delta$), or as the square of a (non-bold) nabla ($\nabla^2$):

$$
\Delta f = \nabla^2 f = \bm{\nabla} \cdot \left(\bm{\nabla} f\right).
$$ (defLaplacian)

In Cartesian coordinates, a simple calculation shows that the Laplacian is simply the sum of the second derivatives:

$$
\nabla^2 f = \frac{\partial^2 f}{\partial x^2} + \frac{\partial^2 f}{\partial y^2} + \frac{\partial^2 f}{\partial z^2}.
$$ (CartesianLaplacian)

Unfortunately the expressions in cylindrical and spherical coordinates are not so straightforward; together with expressions for the gradient, divergence and curl they're given in {numref}`sec:vectorderivativeexpressions`.

The two other possible second derivatives that involve the gradient operator, the gradient of the divergence and the curl of the curl, occur much less frequently than the Laplacian, and haven't gotten their own names. The three second derivatives are related (again something you can prove by writing out the definitions) through

$$
\bm{\nabla} \times \left( \bm{\nabla} \times \bm{v} \right) = \bm{\nabla} \cdot \left( \bm{\nabla} \cdot \bm{v} \right) - \nabla^2 \bm{v}.
$$

## Volume integrals
Like differentiation, integration extends to multiple dimensions. In its most direct form, it is an extension of one-dimensional integration much like partial derivatives of a scalar function are extensions of derivatives of single-variable functions. In one dimension, an integral can be approximated by cutting up the line segment of interest (say $[x_1, x_2]$) in little sections of size $\Delta x$; we then evaluate the function $f(x)$ we want to integrate at each segment, and add all segments together. In the limit that we go to infinitely many infinitesimally short segments, this sum becomes a Riemann sum, which in turn becomes an integral:

$$
\sum_{k=1}^N f(x_1 + k * \Delta x) \Delta x \;\to\; \lim_{N \to \infty} \sum_{k=1}^N f\left(x_1 + k* \frac{x_2-x_1}{N} \right) \frac{x_2-x_1}{N} \;\to\; \int_{x_1}^{x_2} f(x) \mathrm{d}{x}.
$$

In two and three dimensions, we can do much the same, now cutting up an area in little squares, or a volume in little cubes. In Cartesian coordinates, the (infinitesimal) volume of each little cube is simply $\mathrm{d}{V} = \mathrm{d}{x} \mathrm{d}{y} \mathrm{d}{z}$, and our volume integral reads

$$
\int_V f(\bm{x}) \mathrm{d}{V} = \int_{x_1}^{x_2} \int_{y_1}^{y_2} \int_{z_1}^{z_2} f(x, y, z) \mathrm{d}{x} \mathrm{d}{y} \mathrm{d}{z}.
$$ (defvolumeintegral)

The subscript&nbsp;$V$ below the integral on the left-hand side of&nbsp;{eq}`defvolumeintegral` indicates the region over which we integrate. You'll sometimes see a double or triple integral sign to indicate a multi-dimensional integral, though mostly in introductory texts. The region&nbsp;$V$ over which we integrate need not have a block shape. If not, the bounding planes may be functions, and it could sometimes be quite a challenge to evaluate the volume integral. Fortunately, there is no a-priori order in the integration; after all, it doesn't matter which direction we call $x$, $y$ or $z$, so the value of the integral should be independent of our arbitrary choice.

In many cases, it will be helpful to use cylindrical or spherical coordinates to evaluate a volume integral. Fortunately expressing equation&nbsp;{eq}`defvolumeintegral` in terms of these coordinates is fairly straightforward. There are two routes towards doing so. The first is by considering the volume of a small element if we chop things up not in little cubes, but in little segments of a cylinder or a sphere. The second (which also works more generally for arbitrary coordinates) is to do a coordinate transformation. To illustrate, we'll work out both cases for two-dimensional polar coordinates (which generalize to three-dimensional cylindrical ones as the $z$ coordinate is identical in cylindrical and Cartesian coordinates).

````{prf:example} Integration in polar coordinates
:label: sec:integrationinpolarcoordinates
:class: example
If we work in polar coordinates $(r, \theta)$, the lines on which one of our coordinates is constant are circles (constant $r$) and radial lines (constant $\theta$). A little piece of area between lines of constant $r$ and constant $\theta$ then resembles a piece cut off from the end of a piece of pie: two arcs connected by two straight lines. The radii of the arcs are $r$ and $r + \mathrm{d}{r}$, and their opening angle is $\mathrm{d}\theta$. To calculate the area of our little piece, we simply subtract the areas of the two pieces of pie (where the factor&nbsp;$\frac12$ is because a full circle is $2\pi$, but the area of a disk is $\pi r^2$):
```{math}
\mathrm{d}{A} = \frac12 \left(r + \mathrm{d}{r}\right)^2 \mathrm{d}{\theta} - \frac12 r^2 \mathrm{d}{\theta} = r \mathrm{d}{r}\mathrm{d}{\theta} + \frac12 \mathrm{d}{r}^2\mathrm{d}{\theta}.
```
In the limit that the area becomes infinitesimally small, we only retain terms of the same order as our area, i.e., we only have the term $r \mathrm{d}{r} \mathrm{d}{\theta}$. Therefore, for a function defined on $\mathbb{R}^2$:
```{math}
:label: areaintegralCartesianpolar
\int_A f(\bm{r}) \mathrm{d}{A} = \int_{x_1}^{x_2} \int_{y_1}^{y_2} f(x, y) \mathrm{d}{x} \mathrm{d}{y} = \int_{r_1}^{r_2} \int_{\theta_1}^{\theta_2} f(r, \theta) r \mathrm{d}{r} \mathrm{d}{\theta}.
```
Instead of directly calculating the area element, we can also use a coordinate transform. First, we note that
```{math}
\mathrm{d}{f} = \frac{\partial f}{\partial x} \mathrm{d}{x} + \frac{\partial f}{\partial y} \mathrm{d}{y} = \frac{\partial f}{\partial r} \mathrm{d}{r} + \frac{\partial f}{\partial \theta} \mathrm{d}{\theta}
```
and by the chain rule
```{math}
\begin{align*}
\frac{\partial f}{\partial x} &= \frac{\partial f}{\partial r} \frac{\partial r}{\partial x} + \frac{\partial f}{\partial \theta} \frac{\partial \theta}{\partial x} \\
\frac{\partial f}{\partial y} &= \frac{\partial f}{\partial r} \frac{\partial r}{\partial y} + \frac{\partial f}{\partial \theta} \frac{\partial \theta}{\partial y}
\end{align*}
```
which we can combine into
```{math}
:label: derivativetransform
\begin{pmatrix} \frac{\partial f}{\partial x} \\ \frac{\partial f}{\partial y} \end{pmatrix} = \begin{pmatrix} \frac{\partial r}{\partial x} &\frac{\partial \theta}{\partial x} \\ \frac{\partial r}{\partial y} &\frac{\partial \theta}{\partial y} \end{pmatrix} \begin{pmatrix} \frac{\partial f}{\partial r} \\ \frac{\partial f}{\partial \theta} \end{pmatrix}.
```
The matrix in equation&nbsp;{eq}`derivativetransform` is known as the *Jacobian*&nbsp;$J$. We can evaluate it using the definition of polar coordinates from {numref}`appsec:polarcoords`:
```{math}
:label: polarJacobian
J = \begin{pmatrix} \frac{\partial x}{\partial r} &\frac{\partial x}{\partial \theta} \\ \frac{\partial y}{\partial r} &\frac{\partial y}{\partial \theta} \end{pmatrix} = \begin{pmatrix} \cos(\theta) & -r \sin(\theta) \\ \sin(\theta) & r \cos(\theta) \end{pmatrix}.
```
As we've seen in {numref}`sec:determinant`, the determinant of the Jacobian matrix gives us the area of our volume element; in this case, we get $\det(J) = r$, and thus $\mathrm{d}{A} = \mathrm{d}{x} \mathrm{d}{y} = \det(J) \mathrm{d}{r}\mathrm{d}{\theta} = r \mathrm{d}{r} \mathrm{d}{\theta}$, and equation&nbsp;{eq}`areaintegralCartesianpolar` again follows.

````

[^1]: Screen shots from [knmi.nl](https://www.knmi.nl/nederland-nu/weer/waarnemingen), taken on March 25, 2025, &copy; KNMI, CC0.

