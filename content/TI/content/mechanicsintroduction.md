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
(ch:mechanicsintroduction)=
# Introduction to classical mechanics

Classical mechanics is the study of the motion of bodies under the action of physical forces. A *force* is any influence that can cause an object to change its velocity. The object can be anything from an elementary particle to a galaxy. Of course anything larger than an elementary particle is ultimately a composite of elementary particles, but fortunately we usually don't have to consider all those, and can *coarse-grain* to the scale of the objects at hand. As is true for any physical model, classical mechanics is an approximation and has its limits - it breaks down at very small scales, high speeds and large gravitational fields - but within its range of applicability (which includes pretty much every single phenomenon in everyday life) it is extremely useful.

Classical mechanics is based on a small number of *physical laws*, which are mathematical formulations of a physical observation. Some laws can be derived from others, but you cannot derive all of them from scratch. Some laws are *axioms*, and we'll assume they are valid. The laws we'll encounter can be divided up in three classes: Newton's laws of motion, conservation laws and force laws. As we'll see, the three conservation laws of classical mechanics (of energy, momentum and angular momentum) can be derived from Newton's second and third laws of motion, as can Newton's first law. The force laws give us the force exerted by a certain physical system - a compressed spring (Hooke's law) or two charged particles (Coulomb's law) for example. These also feed back into Newton's laws of motion, although they cannot be derived from these and are axioms by themselves.

In addition to the physical laws, there is a large number of *definitions* - which should not be confused with the laws. Definitions are merely convenient choices. A good example is the definition of the number $\pi$: half the ratio of the circumference to the radius of a circle. As you have no doubt noticed, it is very convenient that this number has gotten its own symbol that is universally recognized, as it pops up pretty much everywhere. However, there is no axiom here, as we are simply taking a ratio and giving it a name.

## Dimensions and units

```{index} physical quantities
```
In physics in general, we are interested in relating different *physical quantities* to one another - we want to answer questions like 'how much work do I need to do to get this box up to the third floor'? In order to be able to give an answer, we need certain measurable quantities as input - in the present case, the mass of the box and the height of a floor. Then, using our laws of physics, we will be able to produce another measurable quantity as our answer - here the amount of work needed. Of course, you could check this answer, and thus validate our physical model of reality, by measuring the quantity in question.

```{figure} images/mechanics/SIbaseunitsandconstants.svg
---
figclass: margin
name: fig:SIunits
alt: Overview of the SI quantities and units, and the physical constants they are based on.
---
Overview of the SI quantities and units, and the physical constants they are based on<sup>[^1]</sup>.
```

```{table} Overview of the SI quantities and units, and the physical constants they are based on.
:name: tab:SIunits
| **quantity** | **symbol** | **unit** | **symbol** | **based on**|
| :--- | :--: | :--- | :--: | :--- |
| length | $L$ | meter | $\mathrm{m}$ | speed of light|
| time | $T$ | second | $\mathrm{s}$ | caesium atom oscillation|
| mass | $M$ | kilogram | $\mathrm{kg}$ | Planck's constant|
| current | $I$ | Amp&egrave;re | $\mathrm{A}$ | electron charge|
| temperature | $T$ | Kelvin | $\mathrm{K}$ | Boltzmann's constant|
| luminosity | $J$ | candela | $\mathrm{cd}$ | monochromatic radiation|
| particle count | $N$ | mole | $\mathrm{mol}$ | Avogadro's constant|
```

```{index} dimensions, units
```
Measurable (or 'physical', or 'observational') quantities aren't just numbers - the fact that they correspond to something physical matters, and 10 seconds is something very different from 10 meters, or 10 kilograms. The term we use to express this is, rather unfortunately, to say that physical quantities have a *dimension* - not to be confused with length, height and width. Anything that has a dimension can be measured, and to do so we use *units* - though there may be different units in which we measure the same quantity, such as centimeters and inches for length. When measuring the same quantity in different units, you can always convert between them - there are 2.54 centimeters in an inch - but it's meaningless to try to convert centimeters into seconds, because length and time are different quantities - they have different dimensions.

```{index} Syst\'eme International
```
We will encounter only three different basic quantities, which have the dimensions of length ($L$), time ($T$), and mass ($M$). Thanks to the Napoleonic conquest of Europe in the early 1800s, we have a basic unit for each of these: meters (m) for length, seconds (s) for time, and kilograms (kg) for mass. Although we won't encounter them here, the standard system of units (called the Syst\'eme International, or SI) has four more of these basic pairs: (electric) current&nbsp;$I$, measured in Amp\'eres (A), temperature&nbsp;$T$, measured in Kelvin (K), luminosity&nbsp;$J$, measured in candelas (cd), and 'amount of stuff', measured in moles (mol), see {numref}`tab:SIunits`. Unfortunately, although this system is commonly used in (continental) Europe and in many other parts of the world, it is not everywhere, notably in the US, where people persist in using such things as inches and pounds, so you'll often have to convert between units.

From the seven basic quantities in the SI, all others can be derived. For example, speed is defined as the distance traveled (length) divided by the time it took, so speed has the dimension of $L/T$ and is measured in units of $\mathrm{m}/\mathrm{s}$. Note that in order to be able to compare two quantities, they must have the same dimension. This simple observation has an important consequence: in any physics equation, the dimensions on both sides of the equality sign always have to be the same. There's no bargaining on this point: equating two quantities with different dimensions does not make any kind of sense, so if you find that that's what you're doing at any point, backtrack and find where things went wrong.


```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter1/c1q1.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```


(sec:dimanalysis)=
## Dimensional analysis

```{index} dimensional analysis, harmonic oscillator
```
Although you will of course need a complete physical model (represented as a set of mathematical equations) to fully describe a physical system, you can get surprisingly far with a simple method that requires no detailed knowledge at all. This method is known as *dimensional analysis*, and based on the observation in the previous section that the two sides of any physical equation have to have the same dimension. You can use this principle to qualitatively understand a system, and make predictions on how it will respond quantitatively if you change some parameter. To understand how dimensional analysis works, an example is probably the most effective - we'll take one that is ubiquitous in classical mechanics: a mass oscillating on a spring (known as the *harmonic oscillator*), see {numref}`fig:harmonicoscillator`.

```{figure} images/mechanics/harmonicoscillator.svg
:name: fig:harmonicoscillator
A harmonic oscillator: a mass&nbsp;$m$ suspended on a spring with spring constant&nbsp;$k$, oscillating with a frequency&nbsp;$\omega$.
```

````{prf:example} dimensional analysis of the harmonic oscillator
:label: sec:exampleharmonicoscillatordimensionalanalysis
:class: example

Consider the harmonic oscillator consisting of a mass of magnitude&nbsp;$m$, suspended on a spring with spring constant&nbsp;$k$. If you pull down the mass a bit and release, it will oscillate with a frequency&nbsp;$\omega$. Can we predict how this frequency will change if we double the mass?

There are two ways to answer this question. One is to consider all the forces acting on the mass, then use Newton's second law to derive a differential equation (known as the equation of motion) for the mass, solve it, and from the solution determine what happens if we change the mass. The second is to consider the dimensions of the quantities involved. We have a mass, which has dimension of mass&nbsp;($M$), as it is one of our basic quantities. We have a spring with spring constant&nbsp;$k$, which has dimensions of force per unit length, or mass per unit time squared:

$$
[k] = F/L = M L T^{-2} / L = M / T^2.
$$ (springconstantdimension)

Note the notation $[k]$ for the dimension of $k$. For the frequency, we have $[\omega] = 1/T$. Now we know that the frequency is a function of the spring constant and the mass, and that both sides of that equation must have the same sign. Since there is no mass in the dimension of the frequency, but it exists in the dimension of both the spring constant and the mass, we know that $\omega$ must depend on the ratio of $k$ and $m$: $\omega \sim k/m$. Now $[k/m] = 1/T^2$, and from $[\omega] = 1/T$, we conclude that we must have

$$
\omega \sim \sqrt{k/m}.
$$ (hofreqscaling)

Equation&nbsp;{eq}`hofreqscaling` allows us to answer our question immediately: if we double the mass, the frequency will decrease by a factor&nbsp;$\sqrt{2}$.

Note that in equation&nbsp;{eq}`hofreqscaling` I did not write an equals sign, but a 'scales as' sign ($\sim$, sometimes also written as $\propto$). That is because dimensional analysis will not tell us about any numerical factor that may appear in the expression, as those numerical factors have no unit (or, more correctly, have no dimension - they are *dimensionless*).

You may object that there might be another factor at play: shouldn't gravity matter? The answer is no, as we can also quickly see from dimensional analysis. The force of gravity is given by $mg$, introducing another parameter $g$ (the gravitational acceleration) with dimension $[g] = L / T^2$. Now if the frequency were to depend on&nbsp;$g$, there has to be another factor to cancel the dependence on the length, as the frequency itself is length-independent. Neither $m$ nor $k$ has a length-dependence in its dimension, and so they *cannot* 'kill' the $L$ in the dimension of&nbsp;$g$; the frequency therefore also cannot depend on&nbsp;$g$ - which we have now figured out without invoking any (differential) equations!

Above, I've sketched how you can use dimensional analysis to arrive at a physical scaling relation through inspection: we've combined the various factors to arrive at the right dimension. Such combinations are not always that easy to see, and in any case, you may wonder if you've correctly spotted them all. Fortunately, there is a more robust method, that we can also use to once again show that the frequency is independent of the gravitational acceleration. Suppose that in general $\omega$ could depend on $k$, $m$ and $g$. The functional dependence can then be written as<sup>[^2]</sup>

$$
[\omega] = [k^\alpha m^\beta g^\gamma] = (M/T^2)^\alpha M^\beta (L/T^2)^\gamma = M^{\alpha+\beta} T^{-2(\alpha + \gamma)} L^\gamma,
$$ (dimanalysisgeneral)

which leads to three equations for the exponents:
```{math}
\begin{align*}
\alpha + \beta &= 0, \\
-2(\alpha + \gamma) &= -1, \\
\gamma &= 0,
\end{align*}
```
which you can easily solve to find $\alpha = 1/2$, $\beta = -1/2$, $\gamma = 0$, which gives us equation&nbsp;{eq}`hofreqscaling`. This method<sup>[^3]</sup> will allow you to get dimensional relations in surprisingly many different cases, and is used by most physicist as a first line of attack when they first encounter an unknown system.
````

```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter1/c1q2.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```

## Problems
```{exercise} Harmonic oscillator revisited
:class: dropdown
**Harmonic oscillator revisited** 
Suppose you have a small object of mass&nbsp;$m$, which you attach to a spring of spring constant $k$ (which itself is fixed to a wall at its other end, {numref}`fig:harmonicoscillator`). Above, we derived an expression for the frequency of oscillation of the mass. We also argued that it should be the same for both a horizontally-positioned and a vertically-positioned oscillator, i.e., that the frequency is independent of the gravitational acceleration&nbsp;$g$.
1. Show that the frequency of oscillation is also independent of its amplitude $A$ (the maximum distance from the equilibrium position the oscillating mass reaches).
1. Use dimensional analysis to derive an expression for the maximum velocity of the mass during the oscillation, as a function of $m$, $k$, and $A$.
```

```{exercise} Units based on physical constants
:class: dropdown
In physics, we assume that quantities like the speed of light ($c$) and Newton's gravitational constant ($G$) have the same value throughout the universe, and are therefore known as physical constants. A third such constant from quantum mechanics is Planck's constant ($\hbar$, an $h$ with a bar). In high-energy physics, people deal with processes that occur at very small length scales, so our regular SI-units like meters and seconds are not very useful. Instead, we can combine the fundamental physical constants into different basis values.
1. Combine $c$, $G$ and $\hbar$ into a quantity that has the dimensions of length.
1. Calculate the numerical value of this length in SI units (this is known as the Planck length). You can find the numerical values of the physical constants in {numref}`app:eqsconstants`.
1. Similarly, combine $c$, $G$ and $\hbar$ into a quantity that has the dimensions of energy (indeed, known as the Planck energy) and calculate its numerical value.
```

````{exercise} Reynolds numbers
:label: pb:Reynoldsnumbers
:class: dropdown
**Reynolds numbers**
Physicists often use *dimensionless quantities* to compare the magnitude of two physical quantities. Such numbers have two major advantages over quantities with numbers. First, as dimensionless quantities carry no units, it does not matter which unit system you use, you'll always get the same value. Second, by comparing quantities, the concepts 'big' and 'small' are well-defined, unlike for quantities with a dimension (for example, a distance may be small on human scales, but very big for a bacterium). Perhaps the best known example of a dimensionless quantity is the *Reynolds number* in fluid mechanics, which compares the relative magnitude of inertial and drag forces acting on a moving object:
```{math}
:label: Reynoldsnumber
\mathrm{Re} = \frac{\text{inertial forces}}{\text{drag forces}} = \frac{\rho v L}{\eta},
```
where $\rho$ is the density of the fluid (either a liquid or a gas), $v$ the speed of the object, $L$ its size, and $\eta$ the viscosity of the fluid. Typical values of the viscosity are $1.0\;\mathrm{mPa}\cdot\mathrm{s}$ for water, $50\;\mathrm{mPa}\cdot\mathrm{s}$ for ketchup, and $1.0\;\mu\mathrm{Pa}\cdot\mathrm{s}$ for air.
1. Estimate the typical Reynolds number for a duck when flying and when swimming (you may assume that the swimming happens entirely submerged). NB: This will require you looking up or making educated guesses about some properties of these birds in motion. In either case, is the inertial or the drag force dominant?
1. Estimate the typical Reynolds number for a swimming bacterium. Again indicate which force is dominant.
1. Oil tankers that want to make port in Rotterdam already put their engines in reverse halfway across the North sea. Explain why they have to do so.
1. Express the Reynolds number for the flow of water through a (circular) pipe as a function of the radius&nbsp;$R$ of the pipe, the volumetric flow rate (i.e., volume per second that flows through the pipe)&nbsp;$Q$, and the kinematic viscosity&nbsp;$\nu \equiv \eta / \rho$. 
1. For low Reynolds number, fluids will typically exhibit so-called laminar flow, in which the fluid particles all follow paths that nicely align (this is the transparent flow of water from a tap at low flux). For higher Reynolds number, the flow becomes turbulent, with many eddies and vortices (the white-looking flow of water from the tap you observe when increasing the flow rate). The maximum Reynolds number for which the flow is typically laminar is experimentally measured to be about 2300. Estimate the flow velocity and volumetric flow rate of water from a tap with a 1.0&nbsp;cm diameter in the case that the flow is just laminar.
````

```{exercise} Escape velocity
:label: pb:escapevelocitydimensional
:class: dropdown
The *escape velocity* of a planet is defined as the minimal initial velocity an object must have to escape its gravitational pull completely (and thus go fast enough to defy the rule that 'what goes up must come down').
1. From Newton's universal law of gravitation (equation&nbsp;{eq}`FGrav`), determine the dimension of the gravitational constant $G$.
1. Use dimensional analysis to show that for a planet of mass $M$ and radius $R$, the escape velocity scales as $v \sim \sqrt{MG/R}$.
1. A more detailed calculation shows that in fact we have $v_\mathrm{escape} = \sqrt{2GM/R}$. Express this value of the escape velocity in terms of the (mass) density $\rho$ of the planet, instead of its mass $M$.
1. The average density of the moon is about $6/10$th that of the Earth, and the Moon's radius is about $11/40$ times that of the Earth. From these numbers and your answer at (c), calculate the ratio of the escape velocities of the Moon and the Earth, and explain why the Apollo astronauts needed a huge rocket to get to the Moon, and only a tiny one to get back.
```

[^1]: Source: [Bureau International de Poids et Mesures](https://www.bipm.org), via [Wikimedia commons](https://commons.wikimedia.org/wiki/File:SI_Illustration_Base_Units_and_Constants_Colour_Full.svg), public domain.

[^2]: The actual function may of course contain multiple terms which are summed, but all those must have the same dimension. Operators like sines and exponentials must be dimensionless, as there are no dimensions of the form $\sin(M)$ or $e^L$. The only allowable dimensional dependencies are thus power laws.

[^3]: The method is sometimes referred to as the Rayleigh algorithm, after [John William Strutt, Lord Rayleigh](https://en.wikipedia.org/wiki/John_William_Strutt,_3rd_Baron_Rayleigh) (1842-1919), who applied it, among other things, to light scattering in the air. The result of Rayleigh's analysis can be used to explain [why the sky is blue](https://en.wikipedia.org/wiki/Rayleigh_sky_model).

