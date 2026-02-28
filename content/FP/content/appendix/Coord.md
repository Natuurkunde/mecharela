
<!-- 
```{warning}
Tekst hieronder moet nog gemaakt worden
```
### Other coordinate system

In many cases, using Cartesian coordinates is not the most suitable choice. Sometimes cylindrical coordinates or spherical coordinates are a much more natural choice. We introduce these two coordinate systems here. We will not make use of these coordinate systems throughout the book, although we will refer to these later~

**Cylindrical coordinates**  
In the Cartesian coordinate system, a vector $\vec{P}$ is described in terms of $x, y$ and $z$. In the cylindrical coordinate system, we describe the same vector $\vec{P}$ but then in terms of $r, \theta$ and $z$, see {numref}`fig_cylindrical`. 


```{figure} ../images/cylindricalcoord.svg
:width: 60%
:label: fig_cylindrical
:alt: A 3D coordinate system with a vector r, which starts at the origin (0,0,0) and ends at point P(r,theta,z). 

The cylindrical coordinates
```

We can transform the vector $\vec{P}(x,y)$ into $\vec{P}(r,\theta)$ via:

$$
\left 
\{ 
    \begin{array}{lll}
    r = \sqrt{x^2+y^2}\\
    \theta = \arctan(y/x)\\
    z = z
    \end{array} 
\right

$$


**Spherical coordinates**


$$
\begin{aligned}
r = \sqrt{x^2+y^2+z^2}\\
\theta = arccos(\frac{z}{x^2+y^2+z^2})\\
\phi = arccos(\frac{x}{\sqrt{x^+y^2}})

\end{aligned}
$$


$$
\vec{r} = x\hat{x} + y\hat{y} = r\hat{r}
$$

The coordinates are transformed into each other via:

$$
\left . \begin{array}{ll} x = r \cos \phi \\
             y = r \sin \phi\end{array} \right \} \leftrightarrow \left \{ \begin{array}{ll} r = \sqrt{x^2 + y^2} \\
             \phi = \arctan (y/x) \end{array} \right .
$$

It is also necessary to be able to transform both sets of unit vectors into each other. From the drawing on the right you can figure out that this goes as following:

$$
\left . \begin{array}{ll} \hat{r} = \cos \phi \hat{x} + \sin \phi \hat{y} \\
            \hat{\phi} = -\sin \phi \hat{x} + \cos \phi \hat{y} \end{array} \right \} \leftrightarrow \left \{ \begin{array}{ll} \hat{x} = \cos \phi \hat{r} - \sin \phi \hat{\phi} \\
             \hat{y} = \sin \phi \hat{r} + \cos \phi \hat{\phi} \end{array} \right .
$$

If you are familiar with matrices and rotation, you can notice that indeed the corresponding matrix is $\left ( \begin{matrix}\cos \phi & -\sin \phi \\ \sin \phi &\cos \phi \end{matrix} \right )$.

The expression therefore can be written as following:

$$
\begin{bmatrix}\hat{x} \\
\hat{y} 
\end{bmatrix} 
=
\begin{bmatrix}\cos \phi & - \sin \phi \\
\sin \phi & \cos \phi 
\end{bmatrix}  
\begin{bmatrix}\hat{r} \\
\hat{\phi} \end{bmatrix} 
$$ -->
