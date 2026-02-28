(sec:complexnumbers)=
# Complex numbers

## A product for two-dimensional vectors
When we first discussed vectors in {numref}`appsec:vectors`, we saw that while you can add and subtract vectors easily, you cannot multiply them like you would regular numbers. We did define an inner product, but that's not a 'product of vectors', as the result is not another vector, but a scalar. We also defined the cross product, which only exists for vectors in $\mathbb{R}^3$. While the outcome is an object that for most purposes can be considered to be another vector, it is technically a *pseudovector*: it won't flip sign if you mirror the system (consider what happens to the cross product in {numref}`fig:vectorprodsderivatives` in either the $(\bm{a}, \bm{b})$ plane or the $(\bm{a}, \bm{a} \times \bm{b})$ plane).

You might have wondered why we don't simply define a vector product like we do a vector sum: take the pairwise product of the elements. The reason is that this definition has an undesirable side effect: the product of two vectors that are both not zero could be zero, as in $(1, 0) \times (0, 1) = (1 \cdot 0, 0 \cdot 1) = (0, 0)$. However, there is an alternative option for vectors in two dimensions, that does not suffer from this problem, and will allow us to define a proper product between vectors. For general vectors $(a, b)$ and $(c, d)$ in $\mathbb{R}^2$, this product is given by:

$$
(a, b) \times (c, d) = (ac-bd, ad+bc).
$$ (complexproduct2Dvectors)

It is not hard to prove that with this product, we only get zero as the outcome if one of the inputs is zero. To get zero, we need $ac=bd$ and $ad = -bc$. Dividing the first equation by the second, we get $c/d = -d/c$, or $c^2 = -d^2$, which only holds if $c=d=0$, as squares are always nonnegative<sup>[^1]</sup> (and only the square of zero is zero). It is also a straightforward exercise to show that the product is commutative (i.e., the order doesn't matter) and associative (i.e., $x \times (y \times z) = (x \times y) \times z$).

The *unit* of the product defined by equation&nbsp;{eq}`complexproduct2Dvectors`, i.e., the equivalent of the number&nbsp;$1$ in regular multiplication, will be the vector $(1, 0)$. You can easily check that indeed $(1, 0) \times (a, b) = (a, b)$ for any choice of $a$ and $b$. Finally, we can also define an *inverse*, and thus the concept of division: if we multiply $(a, b)$ with $(a/(a^2 + b^2), -b/(a^2+b^2))$ we get $(1,0)$, the unit of multiplication, so dividing by $(a,b)$ is the same as multiplying with $(a/(a^2 + b^2), -b/(a^2+b^2))$.

```{index} complex numbers
```
Now that we have defined a proper multiplication on $\mathbb{R}^2$, we have defined a (mathematical) *field*, much the same as $\mathbb{R}$ is a field. The pairs of numbers $(a, b)$ are known as *complex numbers*. The name 'complex' represents the fact that the numbers are composite, not that they're 'difficult' (however you may feel about them). The collection of complex numbers is denoted as $\mathbb{C}$.

To facilitate notation, and make the relation with the real numbers (even) more clear, people have introduced a special notation for the (Cartesian) basis of $\mathbb{R}^2$ when seen as the collection of complex numbers. With a little abuse of notation, we write $1 = (1,0)$, identifying the units of multiplication in $\mathbb{R}$ and $\mathbb{C}$. For the other basis vector in $\mathbb{C}$, which has no equivalent in $\mathbb{R}$, we write $i = (0, 1)$. An arbitrary complex number $(a, b)$ can then be written as $a + bi$. We call $a$ the *real part* and $b$ the *imaginary part* of the complex number. Complex numbers are commonly given the symbol $z$, so we write $z = a + bi$. In analogy, we call the $x$-axis of the complex plane the *real axis*, and the $y$-axis the *imaginary axis*, and define $\Re(z) = a$, $\Im(z) = b$.

Just like any other vector in $\mathbb{R}^2$, we can express our new complex number $z$ not just in Cartesian coordinates $(a, b)$, but also in polar ones. The magnitude (or 'absolute value') of $z$ is simply the length of the vector, so $|z| = \sqrt{a^2 + b^2}$, and the polar angle is taken with respect to the positive real axis, so $\tan(\theta) = b/a$. The polar angle is often called the *argument* or *phase* of the complex number $z$, denoted $\arg(z)$. We can use this polar representation to easily identify the vector corresponding to the product of two complex numbers $z_1$ and $z_2$: the length of the product is the product of the lengths, $|z_1 \cdot z_2| = |z_1| \cdot |z_2|$, while the phase of the product is the sum of the phases of the inputs, $\arg(z_1 \cdot z_2 = \arg(z_1) + \arg(z_2)$, see {numref}`pb:complexproduct`.

```{figure} images/appendices/complexsumproduct.svg
:name: fig:complexsumproduct
Sum and product of two complex numbers. (a) The sum of two complex numbers is calculated in the same way as we find the sum of two vectors in $\mathbb{R}^2$, by putting them head-to-tail. Algebraically, we simply add the components. (b) For the product of two complex numbers, we use the &nbsp;{eq}`complexproduct2Dvectors`. The length of the resulting vector (or norm of the resulting complex number) equals the product of the norms of the two original numbers, while the  phase of the product is the sum of the phases of the originals.
```

We can express the complex number&nbsp;$z$ in terms of its magnitude $|z|$ and argument $\theta = \arg(z)$ using the sine and cosine:

$$
z = |z| \left[ \cos(\theta) + i \sin(\theta) \right].
$$ (complexpolar)

We will use equation&nbsp;{eq}`complexpolar` in {numref}`sec:complexfunctions` below to extend the exponential function to the complex numbers.

## Complex numbers as solutions of polynomial equations
Even though the 'new number' $i$ is entirely outside $\mathbb{R}$, its square is not, as we can easily calculate:

$$
i^2 = (0, 1) \times (0, 1) = (0-1,0+0) = (-1, 0) = -1.
$$ (complexisquared)

By equation&nbsp;{eq}`complexisquared`, in the space of complex numbers, the square root of the number $-1$ thus exists, and is equal to $i$. As you might expect, there is another number whose square is $-1$, namely $-i = (0, -1)$, as you can easily check. By extension, we can find the square root of any negative number $-a$, as $(i \sqrt{a})^2 = (0, \sqrt{a}) \times (0, \sqrt{a}) = (-a, 0) = -a$. If you have encountered complex numbers before, it is probably in this context, defining $i$ as the square root of $-1$; by starting from the vector space $\mathbb{R}^2$, we get this result for free.

When working in real numbers, polynomial equations do not always have solutions (or *roots*); a familiar example is the equation $x^2 + 1 = 0$. However, if we extend to the complex numbers, this equation does have two solutions, $\pm i$. We can extend this result to any quadratic equation, $a x^2 + b x + c = 0$ (where $a$, $b$, and $c$ are now real numbers, though the result will also be true for complex coefficients). The solutions of this equation are given by the famous 'abc formula':

$$
z_\pm = -\frac{b}{2a} \pm \frac{1}{2a} \sqrt{b^2 - 4 a c}.
$$

If $b^2 > 4 ac$, we get two real roots; if $b^2 = 4ac$ we get only a single root. If $b^2<4ac$, our roots become complex numbers, which moreover are closely related: their real parts ($-b/2a$) are equal, while their imaginary parts ($(1/2a)\sqrt{4ac - b^2}$) are equal in magnitude but opposite in sign. We call such pairs of complex numbers *complex conjugates*. For an arbitrary complex number $z = a+bi$, the complex conjugate, denoted $z^*$ (or sometimes $\bar{z}$), is given by $z^* = a - bi$. Geometrically, the complex conjugate of a complex number is the vector you get by reflection in the real axis.

Similar results hold for higher-order equations. In particular, we can always find $n$ solutions to the equation $x^n + 1 = 0$. Likewise, we can find $n$ complex solutions to the equation $z^n - 1 = 0$, or $z^n = 1$. The solutions to $z^n = 1$ are known as *roots of unity*. The root of unity with the smallest argument is sometimes denoted $\zeta_n$; the other roots are then simply powers of $\zeta_n$. For example, for $n=3$, we have three solutions: $1$, $\zeta_3 = -\frac12 + \frac12 \sqrt{3}$ and $\zeta_3^2 = -\frac12 - \frac12 \sqrt{3}$. Probably unsurprisingly, $\zeta_3$ and $\zeta_3^2$ are each other's complex conjugate. When drawn in the complex plane, the three roots all lie on the unit circle, forming an equilateral triangle. The $n$th roots of unity similarly form pairs of complex conjugates (except the ones with imaginary part zero), lie on the unit circle, and form a regular $n$-polygon, as shown in {numref}`fig:complexunityroots`.

```{figure} images/appendices/complexunityroots.svg
:name: fig:complexunityroots
Complex roots of the equation $z^n = 1$, known as *roots of unity* for (a) $n=3$ and (b) $n=8$. The root with the smallest argument is denoted $\zeta_n$, the other roots are powers of $\zeta_n$. The roots all either have imaginary part zero, or form pairs of complex conjugates. They also all lie on the unit circle in the complex plane, forming a regular polygon with $n$ vertices.
```

```{index} fundamental theorem of algebra
```
Unlike for the real numbers, in which we can write down a polynomial equation with no real roots, the complex numbers are *algebraically closed*: every polynomial with complex coefficients has at least one complex root. This statement is known as the *fundamental theorem of algebra*. There are many proofs of this theorem, most of which use more advanced mathematical concepts from analysis or topology; some are given on the [Wikipedia page of the theorem](https://en.wikipedia.org/wiki/Fundamental_theorem_of_algebra).

(sec:complexfunctions)=
## Functions of complex numbers

Just like for real numbers, we can define functions of complex numbers. We've already seen how to tackle addition and multiplication (from which we can construct any polynomial function). It's very useful to also consider exponentials and logarithms. We start with the simplest exponential function, $e^z$. Naturally, this function should behave like the exponential function we know if $z$ is real. In particular, we'll define it (as usual) by demanding that the derivative of the function is the function itself.

Equation&nbsp;{eq}`complexpolar` allows us to define the complex exponential function as the desired extension of the real one. Let $x$ be a real number; in general, $e^{i x}$ will be a complex number that can be written in the form of equation&nbsp;{eq}`complexpolar`:

$$
e^{ix} = r \left[ \cos(\theta) + i \sin(\theta) \right].
$$ (eixpolar)

To find $r$ and $\theta$, we now take derivatives with respect to $x$ on both sides, using the chain rule:
```{math}
:label: eixderivative
\begin{align*}
i e^{ix} &= \left[ \cos(\theta) + i \sin(\theta) \right] \frac{\mathrm{d} r}{\mathrm{d} x} + r \left[ -\sin(\theta) + i \cos(\theta) \right] \frac{\mathrm{d} \theta}{\mathrm{d} x}  \\
i r \left[ \cos(\theta) + i \sin(\theta) \right]  &= \left[ \cos(\theta) \frac{\mathrm{d} r}{\mathrm{d} x} - r \sin(\theta) \frac{\mathrm{d} \theta}{\mathrm{d} x} \right] + i  \left[ \sin(\theta) \frac{\mathrm{d} r}{\mathrm{d} x} + r \cos(\theta) \frac{\mathrm{d} \theta}{\mathrm{d} x} \right]
\end{align*}
```
In equation&nbsp;{eq}`eixderivative`, the real parts and the imaginary parts need to be equal on both sides (remember that they're the parts of the complex number as a vector, and thus represent orthogonal components). We thus get two equations:

```{math}
:label: eixderivatives
\begin{align*}
- r \sin(\theta) &= \cos(\theta) \frac{\mathrm{d} r}{\mathrm{d} x} - r \sin(\theta) \frac{\mathrm{d} \theta}{\mathrm{d} x}\\
r \cos(\theta) &= \sin(\theta) \frac{\mathrm{d} r}{\mathrm{d} x} + r \cos(\theta) \frac{\mathrm{d} \theta}{\mathrm{d} x}
\end{align*}
```

If we now add {eq}`eixderivatives`A times $\cos(\theta)$ to {eq}`eixderivatives`B times $\sin(\theta)$, we get $\frac{\mathrm{d} r}{\mathrm{d} x} = 0$. Likewise, if we subtract $\sin(\theta)$ times {eq}`eixderivatives`A from $\cos(\theta)$ times {eq}`eixderivatives`B, we get $\frac{\mathrm{d} \theta}{\mathrm{d} x} = 1$. Therefore, $r$ is independent of $x$, while $\theta$ is proportional to $x$. For $x=0$, we get $e^{ix} = e^0 = 1$, so there $r=1$ and $\theta=0$. Equation&nbsp;{eq}`eixpolar` thus becomes

$$
e^{ix} = \cos(x) + i \sin(x).
$$ (Eulerformula)

```{index} Euler's formula
```
Equation&nbsp;{eq}`Eulerformula` is known as *Euler's formula*. We can use it to define $e^z$ for an arbitrary complex number $z = a + bi$ by exploiting the rule that the product of two exponentials is the exponential of the sum of their arguments:

$$
e^z = e^{a + bi} = e^a e^{bi} = e^a \left[\cos(b) + i \sin(b)\right].
$$

Euler's formula has (at least) three more applications. One is perhaps more aesthetic than useful: we can use it to write an expression containing five important and familiar numbers, by taking $x = \pi$:

$$
e^{i \pi} + 1 = 0.
$$

The second, more serious (and useful) application is that we can now write any complex number as the product of its magnitude and a exponential of a purely imaginary number, namely $i$ times its argument:

$$
z = r e^{i \theta}.
$$ (complexnumberpolarform)

The third application is that we can invert equation&nbsp;{eq}`Eulerformula` to express the sine and cosine functions in terms of complex exponentials:

```{math}
:label: cossinexponentials
\begin{align*}
\cos(x) = \frac{e^{ix} + e^{-ix}}{2},\\
\sin(x) = \frac{e^{ix} - e^{-ix}}{2i}.
\end{align*}
```

Evaluating integrals that contain powers or products of sines and cosines is a lot easier if you first write them as exponentials using equation&nbsp;{eq}`cossinexponentials`; the same goes for checking the validity of some familiar relations between the cosine and sine functions. Note that, despite appearances, the right-hand sides of equation&nbsp;{eq}`cossinexponentials` are strictly real numbers if $x$ is real<sup>[^2]</sup>.

Equations&nbsp;{eq}`cossinexponentials` also give us a way to define the sine and cosine of a complex number $z$: we simply replace $x$ by $z$ in the equations. While this definition obviously reverts to the real one if $z$ is real, we need to show (using the properties of the complex exponential) that other familiar relations for sines and cosines also hold for the complex versions, see {numref}`pb:complexsinecosine`.

Like for functions with real arguments, we can expand functions of complex numbers in Taylor series, given that the function is differentiable (i.e., all its derivatives exist in the relevant domain). The power series of the complex exponential function is the same as that of the real function:

$$
e^z = \sum_{n=0}^\infty \frac{z^m}{n!}.
$$

Now that we know how to calculate $e^z$, any other exponential follows trivially, using the rule that $a^{b^c} = a^{b \cdot c}$. Similarly, we only need to know how to deal with one logarithm to be able to handle them all. Our logarithm of choice will have base&nbsp;$e$. The associated 'natural logarithm' is often written as $\ln(z)$; mathematicians (and some of their theoretical physicists friends) prefer simply $\log(z)$. To avoid confusion, we'll go with the former notation here. Like we did for the exponential, we want to define the logarithm of a complex number $z$ such that it extends the definition of the logarithm on the real numbers, maintaining as many properties as possible, and reverting to the real one if $z$ is real. Formally, defining the complex logarithm is then easy: $\ln(z)$ is the complex number&nbsp;$w$ for which $e^w = z$. However, there is a snag: $w$ is not uniquely defined. To see why, we write $z$ in polar form, equation&nbsp;{eq}`complexnumberpolarform`, i.e., $z = r e^{i\theta}$. We then get $e^w = z$ for $w = i\theta + \ln(r)$. Because the argument $\theta$ is periodic, we also get $w = i (\theta + 2n\pi) + \ln(r)$ as the logarithm of $z$, for any integer $n$. There are therefore infinitely many values that are the logarithm of a complex number $z$ (except for $z=0$, for which the logarithm is not defined). We call the logarithm of $z$ with imaginary part between<sup>[^3]</sup> $-\pi$ and $\pi$ the *principal value* of $\ln(z)$; this is the one we'll usually employ. For the principal value we can write

$$
\ln(z) = \ln(r) + i\theta = \ln(|z|) + i \arg(z).
$$ (complexlog)

Note that the definition of the logarithm of a complex number allows us to define the logarithm of a negative real number as well; the only value that we still cannot take the logarithm of is zero.

If we restrict the complex logarithm to the principal value, some of the familiar rules of logarithms break. For example, we have $\ln(a) + \ln(b) = \ln(a \cdot b)$ in real numbers; the same holds if $a$ and $b$ are complex numbers, but only up to factors $2 \pi i$ (take, for example, $a=-1$ and $b=i$).

## Differentiation of complex functions
When introducing the complex exponential above, we defined it by the property that it is equal to its derivative. However, we haven't formally defined the derivative of a complex function yet. Here too, we simply extend the definition of real-valued functions, so we have, for the derivative of a complex function $f(z)$ at the point $z=z_0$:

$$
f'(z_0) = \lim_{h \to 0} \frac{f(z_0 + h) - f(z_0)}{h}.
$$ (defcomplexderivative)

Note that both the numerator and the denominator in the limit in equation&nbsp;{eq}`defcomplexderivative` are complex numbers. Also, while there are only two ways to approach a point on the real axis (from the left and from the right), there are infinitely many different directions in the complex plane from which we can approach $h = 0$. For the derivative of $f(z)$ to exist at $z=z_0$, the limit in equation&nbsp;{eq}`defcomplexderivative` must give the same value regardless of the direction chosen. An important consequence of this much stronger condition is that if a derivative of $f(z)$ exists at $z=z_0$, all higher-order derivatives of $f(z)$ also exist at $z=z_0$.

To determine whether or not complex derivatives exist, we fortunately do not need to calculate infinitely many limits. Instead, we'll exploit the complex nature of the function $f(z)$ by writing it as a combination of two real-valued<sup>[^4]</sup> functions of two real-valued arguments. If we write $z = x + iy$, with $x$ and $y$ real, we can write $f(z)$ as

$$
f(z) = f(x + iy) = u(x,y) + i v(x,y),
$$

where $u$ and $v$ are real-valued functions of real-valued arguments $x$ and $y$. Now if $f(z)$ is differentiable at $z=z_0$, equation&nbsp;{eq}`defcomplexderivative` must give the same result for every choice of path for $h$. In particular, we can take $h$ to approach $0$ along the real and imaginary axes. For the real axis, equation&nbsp;{eq}`defcomplexderivative` becomes

$$
\lim_{h \to 0} \frac{f(z_0 + h) - f(z_0)}{h} = \frac{\partial f}{\partial x}(z_0) = \frac{\partial u}{\partial x}(z_0) + i\frac{\partial v}{\partial x}(z_0),
$$

because $h$ is now a real number. Along the imaginary axis, we can also take a real limit:

$$
\lim_{h \to 0} \frac{f(z_0 + ih) - f(z_0)}{ih} = \frac{1}{i}\frac{\partial f}{\partial y}(z_0) = -i \frac{\partial u}{\partial y}(z_0) + \frac{\partial v}{\partial y}(z_0).
$$

As the two limits must give the same result, we thus obtain

$$
i \frac{\partial f}{\partial x}(z_0) = \frac{\partial f}{\partial y}(z_0),
$$ (CauchyRiemanngeneral)

or, in the real and imaginary components of $f$

```{math}
:label: CauchyRiemannspecific
\begin{align*}
\frac{\partial u}{\partial x}(z_0) &= \frac{\partial v}{\partial y}(z_0), \\
\frac{\partial u}{\partial y}(z_0) &= -\frac{\partial v}{\partial x}(z_0).
\end{align*}
```

```{index} Cauchy-Riemann equations
```
Equation&nbsp;{eq}`CauchyRiemanngeneral` and&nbsp;{eq}`CauchyRiemannspecific` are known as the *Cauchy-Riemann equations*. There are some more subtleties involved if you wish to be mathematically rigorous (for example, $u$ and $v$ must not just have partial derivatives at $z=z_0$, but be real-differentiable themselves), but for most cases, checking that the real and imaginary parts of $f(z)$ satisfy the Cauchy-Riemann equations is enough to show that $f(z)$ is complex differentiable.

Complex derivatives extend real ones; when we revert to real-valued functions of real variables, we should retrieve the familiar results. Many also go the other way around; the rule for differentiating polynomials is the same in complex numbers as it is in real ones, and the sum, product, quotient, and chain rules all apply to complex differentiation. The proofs are analogous to their real counterparts.

```{index} holomorphic function, analytic function
```
A function $f(z)$ of a complex number is called *holomorphic* at $z=z_0$ if it is differentiable 'near $z=z_0$', or formally, in an open subset of $\mathbb{C}$ that contains $z_0$. The function is called *analytic* if it is (locally) given by a convergent power series. The 'locally' means that we can restrict the allowed values of $z$ to an open subset of $\mathbb{C}$, in that case the function is only analytic on that subset of $\mathbb{C}$. Now that we have a definition of complex differentiation, we can define the complex version of a Taylor series; naturally, an analytic function will then be equal to its Taylor series. A function that is not analytic will not have a converging Taylor series; it may however have a converging Laurent series, which extends the Taylor series to include terms with negative exponents (i.e., terms of the form $1/z$, $1/z^2$, and so on). 

## Problems
```{exercise} Product of two complex numbers
:label: pb:complexproduct
:class: dropdown
Prove that for the complex product defined by equation&nbsp;{eq}`complexproduct2Dvectors`, the magnitude of the product is the product of the magnitudes (i.e., $|z_1 \cdot z_2| = |z_1| \cdot |z_2|$), while the phase of the product is the sum of the phases (i.e., $\arg(z_1 \cdot z_2) = \arg(z_1) + \arg(z_2)$).
```

```{exercise} Goniometric relations for complex numbers
:label: pb:complexsinecosine
:class: dropdown
Using the equations&nbsp;{eq}`cossinexponentials` to define the sine and cosine of a complex number&nbsp;$z$, prove that the following relations hold for arbitrary $z, w \in \mathbb{C}$:
1. $\sin^2(z) + \cos^2(z) = 1$,
1. $\sin(z+w) = \sin(z) \cos(w) + \cos(z) \sin(w)$,
1. $\cos(z+w) = \cos(z) \cos(w) - \sin(z) \sin(w)$.
```

[^1]: Squares of real numbers that is, but $c$ and $d$ here are real numbers, as are $a$ and $b$.

[^2]: One quick way to check that both expressions on the right-hand side of equation&nbsp;{eq}`cossinexponentials` are real is by taking their complex conjugates (which boils down to replacing every $i$ by a $-i$ and vice versa). The result is the same expression; a number that is equal to its complex conjugate is a real number.

[^3]: To be precise, the interval $(-\pi, \pi]$, so we include $\pi$ but not $-\pi$.

[^4]: With 'real-valued', we mean that the number that the function gives us is a real number; we also have 'integer-valued' and 'complex-valued' functions.

