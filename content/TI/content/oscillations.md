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
(ch:oscillations)=
# Oscillations

(sec:oscillation)=
## Oscillatory motion

### Harmonic oscillator

```{index} harmonic oscillator, Hooke's law
```
We've already encountered two examples of oscillatory motion - the rotational motion of {numref}`ch:rotation`, and the mass-on-a-spring system in {numref}`sec:eom` (see {numref}`fig:harmonicoscillator`). The latter is the quintessential oscillator of physics, known as the *harmonic oscillator*. Recapping briefly, we get its equation of motion by considering a mass $m$ that is being pulled on by a massless ideal spring of spring constant $k$. Equating the resulting spring force (Hooke's law) to the net force in Newton's second law of motion, we get:

$$
m \ddot{x} = - k x.
$$ (harmosceom)

The harmonic oscillator is characterized by its *natural frequency*&nbsp;$\omega_0$:

$$
\omega_0 = \sqrt{\frac{k}{m}},
$$ (harmoscfreq)

as follows readily by dimensional arguments (or, of course, by solving the differential equation). Because equation&nbsp;{eq}`harmosceom` is second-order, its solution has two unknowns; moreover, as it has to be minus its own derivative we readily see that it should be a linear combination of sines and cosines (for a formal derivation, see {numref}`app:solode`). We can write the solution in two different ways:
```{math}
:label: harmonicoscillator1
\begin{align*}
x(t) &= x(0) \cos(\omega_0 t) + \frac{v(0)}{\omega_0} \sin(\omega_0 t), \
\end{align*}
```

```{math}
:label: harmonicoscillator2
\begin{align*}
&= A \cos(\omega_0 t + \phi),
\end{align*}
```
where the phase $\phi$ is given by $\tan\phi = -\frac{1}{\omega} \frac{v(0)}{x(0)}$ and the amplitude $A$ by $A = \frac{x(0)}{\cos\phi}$. Unsurprisingly, as they are both simple periodic motions, there is a direct relationship between a harmonic oscillator with natural frequency&nbsp;$\omega_0$, and a point on a disk rotating with uniform angular velocity&nbsp;$\omega_0$ in the $xy$-plane - the motion of the harmonic oscillator is that of the disk projected on the $x$ (or $y$) axis.

### Torsional oscillator

```{index} torsional oscillator
```
A torsional oscillator is the rotational analog of a harmonic oscillator - imagine a disk with moment of inertia $I$ suspended by a massless, frictionless rope that has a torsional constant&nbsp;$\kappa$, i.e., the force to twist the rope is given by $F = - \kappa \theta$, with $\theta$ the twist angle. By invoking the rotational analog of Newton's second law of motion, equation&nbsp;{eq}`torquelaw`, we readily find for the equation of motion of the torsional oscillator:

$$
I \ddot{\theta} = - \kappa \theta,
$$

so the torsional oscillator indeed is the exact rotational analog of the harmonic oscillator, and has a natural frequency of $\omega_0 = \sqrt{\kappa/I}$.

```{index} Huygens
```
````{admonition} Christiaan Huygens (1629-1695)
:class: dropdown
**Christiaan Huygens** (1629-1695) was a Dutch physicist and astronomer, and one of the major figures in the scientific revolution. Huygens invented the pendulum clock in 1656, which revolutionized timekeeping and remained the most accurate clock for 300 years. Huygens was also the first to cast the laws of physics in mathematical form, writing down an early (quadratic) version of Newton's second law of motion, the equation for the centripetal force (eq.&nbsp;{eq}`Fcp`), and the correct form of the laws of elastic collisions ({numref}`sec:totallyelasticcollisions`). Observing two pendulum clocks on the same wall, Huygens observed that they synchronized (see {numref}`sec:coupledoscillators`). Huygens' study of optics led him to formulate the wave theory of light, which can correctly predict light diffraction. In astronomy, he discovered the first feature on the surface of Mars, the largest moon of Saturn (Titan), and that the previously observed 'shape changes' of Saturn were due to the presence of its rings. The Huygens probe that landed on Titan in 2005 was very appropriately named in his honor.
```{figure} images/portraits/Huygens.jpg
---
width: 300
---
1671 portrait of Huygens by Caspar Netscher <sup>[^1]</sup>.
```
````

(sec:pendulum)=
### Pendulum

```{index} pendulum
```
A pendulum is an object that is suspended on a horizontal peg through any point&nbsp;$x_\mathrm{P}$ but its center of mass&nbsp;$x_\mathrm{CM}$ (it won't oscillate if you pin it at the center of mass). If the center of mass of the pendulum is pulled sideways, gravity will exert a torque around the position of the peg, pulling the pendulum back down. If the distance between $x_{P}$ and $x_{CM}$ is $L$, and the line connecting them makes an angle&nbsp;$\theta$ with the vertical through&nbsp;$x_\mathrm{P}$, then the torque exerted by gravity around&nbsp;$x_P$ equals $-mgL\sin\theta$, where as usual&nbsp;$m$ is the mass of the pendulum. Now again invoking equation&nbsp;{eq}`torquelaw`, we can write for the equation of motion of the pendulum (with&nbsp;$I$ its moment of inertia about&nbsp;$x_\mathrm{P}$):

$$
I \ddot{\theta} = -mgL \sin\theta.
$$ (physicalpendulum)

```{index} physical pendulum
```
Unfortunately we can't solve equation&nbsp;{eq}`physicalpendulum`. For small angles however, we can Taylor-expand the sine, and write $\sin\theta \approx \theta$, which takes us back to the harmonic oscillator equation. From that we find that for this pendulum (called the *physical pendulum*), the natural frequency is $\omega_0 = \sqrt{mgL/I}$. For the special case that the pendulum consists of a mass&nbsp;$m$ suspended on a massless rope of length&nbsp;$L$ (the *simple pendulum*), we have $I=mL^2$ and thus $\omega_0 = \sqrt{g/L}$.

(sec:generaloscillations)=
### Oscillations in a potential energy landscape

```{index} potential energy ; oscillations
```
The potential energy associated with a mass on a spring has a very simple form: $U_\mathrm{s}(x) = \frac12 k x^2$ (see equation&nbsp;{eq}`Us`). The potential energy landscape of a harmonic oscillator thus has the shape of a parabola. Now that's a shape that we encounter very often: the shape of pretty much every landscape about a minimum closely resembles a parabola<sup>[^2]</sup>. To see why this is the case, simply Taylor-expand the potential energy about a minimum at $x_0$: because the function has a minimum at $x_0$, $U'(x_0) = 0$, and the Taylor expansion gives

$$
U(x) = U(x_0) + \frac12 U''(x_0) x^2 + \mathcal{O}(x^3).
$$ (potenTaylor)

Around a minimum in the potential energy, any potential energy thus resembles that of a harmonic oscillator. Any particle placed in such a potential energy landscape close to a minimum (i.e., a particle on which a force acts close to the point where the force vanishes) will therefore tend to oscillate. By comparing equation&nbsp;{eq}`potenTaylor` with the potential energy of the harmonic oscillator, we can immediately read off that the resulting oscillatory motion is identical to that of a harmonic oscillator with spring constant $k = U''(x_0)$. A particle released close to a minimum of the potential energy will thus oscillate with a frequency $\omega = \sqrt{U''(x_0) / m}$.

```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter9/c9q1.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```
```{figure} images/quizes/c9q1_energyandequilibrium.svg
:name: fig:c9q1_energyandequilibrium
:width: 400px
```

```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter9/c9q2.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```
```{figure} images/quizes/c9q2_generaloscillator.svg
:name: fig:c9q2_generaloscillator
:width: 400px
```

(sec:dampedoscillator)=
## Damped harmonic oscillator

```{index} harmonic oscillator ; damped
```

```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter9/c9q3.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```

So far we've disregarded damping on our harmonic oscillators, which is of course not very realistic. The main source of damping for a mass on a spring is due to drag of the mass when it moves through air (or any fluid, either gas or liquid). For relatively low velocities, drag forces on an object scale linearly with the object's velocity, as illustrated by Stokes' law (equation&nbsp;{eq}`FStokes`). For an object of arbitrary shape moving through an arbitrary fluid we'll write $F_\mathrm{drag} = -\gamma \dot{x}$, with $\gamma$ the drag coefficient, and of course opposing the direction of motion. Adding this to the spring force gives for the equation of motion of the *damped harmonic oscillator*:

$$
m \ddot{x} = -\gamma \dot{x} - k x.
$$ (dampedharmosceom)

We now have two numbers that determine the motion: the undamped frequency&nbsp;$\omega_0 = \sqrt{k/m}$ and the damping ratio $\zeta = \gamma / 2 \sqrt{mk}$. In terms of these parameters, we can rewrite equation&nbsp;{eq}`dampedharmosceom` as:

$$
\ddot{x} + 2 \zeta \omega_0 \dot{x} + \omega_0^2 x = 0.
$$ (dampedharmosc2)

The solution of equation&nbsp;{eq}`dampedharmosc2` depends strongly on the value of&nbsp;$\zeta$, see {numref}`fig:dampedoscillations`. We can find it<sup>[^3]</sup> by substituting the Ansatz $x(t) = e^{\lambda t}$, which gives a characteristic equation for $\lambda$:

$$
\lambda^2 + 2\zeta\omega_0 \lambda + \omega_0^2 = 0,
$$ (dampedharmoscchareq)

so

$$
\lambda = -\zeta \omega_0 \pm \omega_0 \sqrt{\zeta^2-1}.
$$ (dampedharmoscchareq2)

For $\zeta < 1$, there are two complex solutions for&nbsp;$\lambda$, and we find that $x(t)$ undergoes an oscillation with an exponentially decreasing amplitude:

$$
x(t) = e^{-\zeta \omega_0 t} [A \cos(\omega_d t) + B \sin(\omega_d t)],
$$ (underdampedoscillator)

where $\omega_d = \omega_0 \sqrt{1-\zeta^2}$ and $A$ and $B$ follow from the initial conditions. Because there is still an oscillation, this type of motion is called *underdamped*. In contrast, if $\zeta >1$, the roots $\lambda_\pm$ in equation&nbsp;{eq}`dampedharmoscchareq2` are real, and we get qualitatively different, *overdamped* behavior, in which $x$ returns to 0 with an exponential decay without any oscillations:

$$
x(t) = A e^{\lambda_+ t} + B e^{\lambda_- t} = e^{-\zeta \omega_0 t} \left[ A e^{\Omega t} + B e^{-\Omega t} \right],
$$ (overdampedoscillator)

where $\Omega = \omega_0 \sqrt{\zeta^2-1}$. Naturally the boundary case is when $\zeta=1$, which is a *critically damped* oscillator - the fastest return to 0 without oscillations. Because in this case equation&nbsp;{eq}`dampedharmoscchareq2` only has one root, we again get a qualitatively different solution:

$$
x(t) = (A + B t) e^{-\omega_0 t}.
$$ (criticallydampedoscillator)

The three different cases and the undamped oscillation are shown in {numref}`fig:dampedoscillations`.

```{code-cell} ipython3
:tags: [hide-input, remove-output]

%config InlineBackend.figure_formats = ['svg']
import numpy as np
import matplotlib.pyplot as plt
plt.rcParams.update({'font.size': 12})
from myst_nb import glue

def x(t):
    # Returns x(t), with x(0) = 1, v(0) = 0, and omega_0 = 1.
    return np.cos(t)

def xud(t):
    # Returns x_{underdamped}(t), zeta = 0.25 and omega_0 =1 (and therefore omega_d = sqrt{1-0.25^2}).
    return np.exp(-0.25*t) * np.cos(np.sqrt(1-0.25*0.25) * t)

def xcd(t):
    # Returns x_{critically damped}(t), A = B = omega_0 = 1.
    return (1 + t) * np.exp(-t)

def xod(t):
    # Returns x_{overdamped}(t), with zeta = 2 and omega_0 =1, and therefore Omega = sqrt(3). Also choose A and B such that x(0) = 1.
    return ((0.5 + 1/np.sqrt(3))*np.exp(np.sqrt(3) * t) + (0.5 - 1/np.sqrt(3))*np.exp(-np.sqrt(3) * t)) * np.exp(-2*t)

fig, ax = plt.subplots(figsize=(6,4))

t = np.linspace(0, 4*np.pi, 1000)

line1 = ax.plot(t, x(t), label='$\\zeta = 0$')
line2 = ax.plot(t, xud(t), label='$0 < \\zeta < 1$')
line3 = ax.plot(t, xcd(t), label='$\\zeta = 1$')
line4 = ax.plot(t, xod(t), label='$\\zeta > 1$')

ax.axhline(y = 0, color = 'k', linestyle = ':')

ax.set_xlim(0,4*np.pi)
ax.set_xticks([0, np.pi, 2*np.pi, 3*np.pi, 4*np.pi], labels=['$0$', '$\\pi$', '$2\\pi$', '$3\\pi$', '$4\\pi$'])
ax.set_yticks([-1, -0.5, 0, 0.5, 1], labels=['$-1$', '$-\\frac{1}{2}$', '$0$', '$\\frac{1}{2}$', '$1$'])
ax.set_xlabel('$t$')
ax.set_ylabel('$x(t)$')
ax.legend()

# Save graph to load in figure later (special Jupyter Book feature)
glue("dampedoscillations", fig, display=False)
```

```{glue:figure} dampedoscillations
:name: fig:dampedoscillations
Position as function of time for four types of oscillation: undamped ($\zeta = 0$, blue), underdamped ($0 < \zeta < 1$, orange), critically damped ($\zeta = 1$, green) and overdamped ($\zeta > 1$, red). In all cases the initial conditions are $x(0) = 1$ and $v(0) = 0$.
```


```{code-cell} ipython3
:tags: ["remove-input"]

import numpy as np
import plotly.graph_objects as go

# Define parameters for the slider
zeta_values = np.linspace(0, 2, 21)

fig = go.Figure()

# Function to determine color based on zeta value
def get_color(zeta):
    if zeta == 0:
        return '#0f63a3'
    elif 0 < zeta < 1:
        return 'orange'
    elif zeta == 1:
        return 'green'
    else:  # zeta > 1
        return 'red'

# Function to determine damping condition based on zeta value
def get_damping_condition(zeta):
    if zeta == 0:
        return 'Undamped'
    elif 0 < zeta < 1:
        return 'Underdamped'
    elif zeta == 1:
        return 'Critically damped'
    else:  # zeta > 1
        return 'Overdamped'

# Add traces for each zeta value
for zeta in zeta_values:
    t = np.linspace(0, 4*np.pi, 400)
    if zeta == 0:
        y = np.cos(t)
    elif zeta < 1:
        y = np.exp(-zeta*t) * np.cos(np.sqrt(1-zeta**2) * t)
    elif zeta == 1:
        y = (1 + t) * np.exp(-t)
    else:  # zeta > 1
        Omega = np.sqrt(zeta**2 - 1)
        A = 0.5 + 1/(2*Omega)
        B = 0.5 - 1/(2*Omega)
        y = (A*np.exp((Omega - zeta) * t) + B*np.exp((-Omega - zeta) * t))
    
    color = get_color(zeta)
    damping_condition = get_damping_condition(zeta)
    fig.add_trace(go.Scatter(x=t, y=y, visible=False, name=f'ζ = {zeta:.2f} ({damping_condition})', line=dict(color=color)))

# Make the first trace visible
fig.data[0].visible = True

# Create and add slider
steps = []
for i, zeta in enumerate(zeta_values):
    damping_condition = get_damping_condition(zeta)
    step = dict(
        method="update",
        args=[{"visible": [False] * len(zeta_values)},
              {"title": f"Position as function of time for oscillation type: {damping_condition}"}],
        label=f"{zeta:.2f}")
    step["args"][0]["visible"][i] = True
    steps.append(step)

sliders = [dict(
    active=0,
    currentvalue={"prefix": "\u03B6 = "},
    pad={"t": 50},
    steps=steps
)]

fig.update_layout(
    sliders=sliders,
    title=f"Position as function of time for oscillation type: {get_damping_condition(zeta_values[0])}",
    yaxis=dict(range=[-1, 1]),
    xaxis=dict(
        tickmode='array',
        tickvals=[0, np.pi, 2*np.pi, 3*np.pi, 4*np.pi],
        ticktext=['0', '\u03C0', '2\u03C0', '3\u03C0', '4\u03C0']
    ),
    xaxis_title='t',
    yaxis_title='x(t)'
)

fig.show()

```


## Driven harmonic oscillator

```{index} harmonic oscillator ; driven
```
A mass on a spring, displaced out of its equilibrium position, will oscillate about that equilibrium for all time if undamped, or relax towards that equilibrium when damped. Its amplitude will remain constant in the first case, and decrease monotonically in the second. However, if we give the mass a periodic small push at the right moment in its oscillation cycle, its amplitude can increase, and even diverge. To see how this works we study the *driven oscillator*, where we apply a periodic driving force $F_\mathrm{D}(t) = F_\mathrm{D}\cos(\omega_\mathrm{D} t) = \frac12 F_\mathrm{D} \left(e^{i \omega_\mathrm{D}t} + e^{-i \omega_\mathrm{D}t}\right)$. Adding this driving force to the equation of motion&nbsp;{eq}`dampedharmosceom` of a damped harmonic oscillator, we obtain:

$$
\ddot{x} + 2 \omega_0 \zeta \dot{x} + \omega_0^2 x = \frac{F_\mathrm{D}}{2m} \left(e^{i \omega_\mathrm{D}t} + e^{-i \omega_\mathrm{D}t}\right).
$$ (drivenharmosceom)

We already know the homogeneous solution to equation&nbsp;{eq}`drivenharmosceom` - that's just the damped oscillator again, so depending on the value of $\zeta$, we get one of the three possible solutions of the previous section. To find a particular solution, we first note that we can split the driving term in two - if we have a particular solution for each of the oscillating exponentials, we can simply add them. Also, these exponentials themselves look very similar to the underdamped solutions, so they may make a good guess for a particular solution. For a right-hand side of $(F_\mathrm{D}/2m) e^{\pm i \omega_\mathrm{D}t}$ we therefore try $x_\mathrm{p} = A e^{\pm i \omega_\mathrm{D}t}$. Substituting this into equation&nbsp;{eq}`drivenharmosceom` with the appropriate right-hand side, we get:

$$
A\left(-\omega_\mathrm{D}^2 \pm 2 i \omega_0 \zeta \omega_\mathrm{D} + \omega_0^2 \right) e^{\pm i \omega_\mathrm{D}t} = \frac{F_\mathrm{D}}{2m} e^{\pm i \omega_\mathrm{D}t},
$$ (drivenharmosctrialsln)

so we find that we have indeed a solution if the amplitude is given by

$$
A(\omega_\mathrm{D}) = \frac{F_\mathrm{D}}{2m\left(\omega_0^2 \pm 2 i \omega_0 \zeta \omega_\mathrm{D} - \omega_\mathrm{D}^2 \right)}.
$$ (drivenharmoscpartslnamplitude)

The full particular solution of equation&nbsp;{eq}`drivenharmosceom` is then given by
```{math}
:label: drivenharmoscpartsolution
\begin{align*}
x_\mathrm{p}(t) &= \frac{F_\mathrm{D}}{2m} \left[\frac{e^{i \omega_\mathrm{D}t}}{\omega_0^2 + 2 i \omega_0 \zeta \omega_\mathrm{D} - \omega_\mathrm{D}^2} + \frac{e^{-i \omega_\mathrm{D}t}}{\omega_0^2 - 2 i \omega_0 \zeta \omega_\mathrm{D} - \omega_\mathrm{D}^2} \right]  \\
&= \frac{F_\mathrm{D}}{m} \left[ \frac{(\omega_0^2 - \omega_\mathrm{D}^2) \cos(\omega_\mathrm{D}t) + 2 \omega_0 \zeta \omega_\mathrm{D} \sin(\omega_\mathrm{D}t)}{(\omega_0^2 - \omega_\mathrm{D}^2)^2 + 4 \omega_0^2 \zeta^2 \omega_\mathrm{D}^2} \right]  \\
&= \frac{F_\mathrm{D}}{m R(\omega_\mathrm{D})} \cos\left(\omega_\mathrm{D}t - \phi(\omega_\mathrm{D})\right)
\end{align*}
```
where the factor $R(\omega_\mathrm{D})$ in the amplitude is defined by

$$
R^2(\omega_\mathrm{D}) = (\omega_0^2 - \omega_\mathrm{D}^2)^2 + 4 \omega_0^2 \zeta^2 \omega_\mathrm{D}^2,
$$ (drivenharmoscR)

and the phase&nbsp;$\phi(\omega_\mathrm{D})$ by $\cos\phi = (\omega_0^2-\omega_\mathrm{D}^2)/R(\omega_\mathrm{D})$, $\sin\phi = 2\omega_0\zeta\omega_\mathrm{D}/R(\omega_\mathrm{D})$, so

$$
\tan(\phi(\omega_\mathrm{D})) = \frac{2 \omega_0 \zeta \omega_\mathrm{D}}{(\omega_0^2-\omega_\mathrm{D}^2)}.
$$ (drivenharmoscphase)

```{index} resonance
```
*Resonance*, a large response of the harmonic oscillator to a small driving force, occurs when $x_\mathrm{p}(t)$ blows up, or $R(\omega_\mathrm{D})$ goes to zero. That does not always happen, but $R(\omega_\mathrm{D})$ can reach a minimum at which the amplitude becomes large:

$$
0 = \frac{\mathrm{d}R^2}{\mathrm{d}\omega_\mathrm{D}} = -4 (\omega_0^2 - \omega_\mathrm{D}^2) \omega_\mathrm{D} + 8 \omega_0^2 \zeta^2 \omega_\mathrm{D},
$$ (resonancecondition)

which is at

$$
\omega_\mathrm{D}^2 = \omega_0^2 - 2\omega_0^2 \zeta^2,
$$ (resonancefreq)

or $\omega_\mathrm{D} \simeq \omega_0$ if the damping factor $\zeta$ is small. Note that in this same limit (small $\zeta$), we find that when $\omega_\mathrm{D} \simeq \omega_0$, $\tan \phi \to \infty$, so $\phi \to \pi/2$. Therefore, in this case the driving happens out of phase with the response, that is to say, you push hardest when the mass is at its point of maximum speed, increasing that speed even further, and leading to an increase in amplitude. In practice, this is what kids do when they sit on a swing: they fling back their legs when they go through the lowest point (maximum speed) going backwards, and fling their legs forward at the same point when going forwards, increasing their speed and thus amplitude.

(sec:phaseportraits)=
## Phase portraits

```{index} phase portrait
```
So far, we've studied harmonic oscillators, for which the equation of motion is linear. We also already encountered a case for which this is just an approximation, the pendulum in {numref}`sec:pendulum`. We could solve the non-linear equations of motion of a general oscillator linearly, but there is a lot we can learn about them without having to resort to numerical methods. The key tool for analyzing the behavior of a non-linear oscillator is a *phase portrait*. Rather than plotting the position and velocity of an oscillator as a function of time, we plot them against each other, with the position on the horizontal axis, and the velocity on the vertical axis. This ($x$, $v$) plane is usually referred to as the phase plane. A phase portrait depicts possible trajectories in the phase plane. For a harmonic oscillator, we have $\ddot{x} = - \omega^2 x$, or, re-writing the equations in terms of the position $x$ and the velocity $v$:

```{math}
:label: harmonicoscillatorphaseportrait
\begin{align*}
\dot{x} &= v, \\
\dot{v} &= - \omega_0^2 x.
\end{align*}
```

Note that the system of two first-order differential equations&nbsp;{eq}`harmonicoscillatorphaseportrait` is completely equivalent to the second-order differential equation we started with. We can do the same for any second-order differential equation by considering the first derivative of our variable at interest (here the velocity&nbsp;$v$, as the derivative of the position&nbsp;$x$) as a separate variable.

For a harmonic oscillator, the phase portrait consists of concentric ellipses, see {numref}`fig:phaseportraits`(a). Which ellipse depends on the initial conditions, but, as there is no dissipation of energy in the simple harmonic oscillator, once the oscillator is set in motion, it will stay on its trajectory forever. In particular, each ellipse corresponds to a given amount of mechanical energy, namely

$$
E = K + U = \frac12 m v^2 + \frac12 k x^2 = \frac12 m \left( v^2 + \omega_0^2 x^2 \right).
$$

The trajectories have a direction: they will always rotate clockwise in our phase plane, except at one point, $x = v = 0$, which is a fixed point in which an unperturbed harmonic oscillator stays put for all eternity.

We can also draw the phase portrait of a pendulum; now the phase plane is spanned by the angle&nbsp;$\theta$ and the angular velocity<sup>[^4]</sup>&nbsp;$\omega$, which satisfy

```{math}
:label: pendulumphaseportrait
\begin{align*}
\dot{\theta} &= \omega, \\
\dot{\omega} &= - \omega_0^2 \sin(\theta).
\end{align*}
```

One immediate difference between the phase portrait of the simple harmonic oscillator and the pendulum is that the latter is periodic. Like for the harmonic oscillator, the pendulum has stable fixed points, for $\theta$ any integer multiple of $2\pi$ (including $0$) and $\omega = 0$. As long as $\theta$ and $\omega$ are small, the trajectories in the phase plane are periodic, although they start deviating from ellipses as $\theta$ increases. For large values of&nbsp;$\theta$ or $\omega$ though, the trajectories are no longer closed: they 'hop' from one period to the next. Physically, these trajectories correspond to pendulums that make full rotations.

In between the closed and open trajectories there is one special trajectory, corresponding to the release of a pendulum in its unstable position (with the mass above the pivot). As you know, this pendulum will make a single full rotation, initially accelerating, decelerating again as it goes up to make a full circle. The unstable points are equilibrium points of equation&nbsp;{eq}`pendulumphaseportrait`, with $\omega = 0$ and $\theta = (2n+1)\pi$, where $n$ is any integer. They are known as saddle points in the phase portrait, as they have two incoming and two outgoing trajectories, see {numref}`fig:phaseportraits`(b).

Like the trajectories of the harmonic oscillator, those of the pendulum have a conserved total energy, given by

$$
E = K + U = \frac12 I \omega^2 + \int m g L \sin(\theta) \mathrm{d}\theta = I \left( \frac12 \omega^2 - \omega_0^2 \cos(\theta)\right).
$$

Real pendulums and other oscillators experience drag forces, and will therefore not continue oscillating indefinitely. Instead, they lose (or dissipate) a bit of mechanical energy every cycle. We can see this beautifully in the phase plane of the pendulum if we add the drag force, which adds a second term of the form $-\zeta \omega$ to equation&nbsp;{eq}`pendulumphaseportrait`A. The trajectories are now no longer closed loops, but spiral inwards into a stable fixed point, even if they start at conditions where they'd have an open trajectory without drag, see {numref}`fig:phaseportraits`(c).

Phase portraits are used throughout physics, as they can be drawn for every system described by a second-order differential equation. They are especially useful for studying periodic motion, and particularly so when the equations are nonlinear. As a final example, we'll draw the phase diagram of the Van der Pol oscillator, which has a nonlinear damping term. The equations for this oscillator are given by

```{math}
:label: vanderPoloscillator
\begin{align*}
\dot{x} &= v \\
\dot{v} &= \mu (1-x^2) v - x
\end{align*}
```

The van der Pol oscillator differs from the damped pendulum in that instead of converging to a stationary point, it converges to a limit cycle: the system evolves over time to a specific trajectory in the phase plane, see {numref}`fig:phaseportraits`(d).

Although the details of a trajectory in the phase plane can often only be found through numerical solution, we can usually determine the long-term behavior of the system analytically. The first step is to identify *steady-state* solutions that do not change in time. If the solutions are time-independent, their time derivatives have to vanish. In general, we can write for any phase portrait

```{math}
:label: generalphaseportrait
\begin{align*}
\dot{x} = f(x, v), \\
\dot{v} = g(x, v),
\end{align*}
```

where $f$ and $g$ are analytic functions. In the examples we have seen so far, we always had $f(x, v) = v$, but in many cases it is easier to write the system in different form. To find the steady-state solutions of the system, we now solve 

$$
f(x, v) = g(x, v) = 0.
$$ (phaseportraitequilibriumpoints)

The solutions to equation&nbsp;{eq}`phaseportraitequilibriumpoints` are known as equilibrium points or fixed points of the system if they are points, and limit cycles if they are trajectories. Equilibrium points come in various kinds. We already encountered stable fixed points (or 'nodes'), saddle points, and stable spiral points when discussing the pendulum; there are also unstable fixed points and unstable saddle points, from which all solutions move or spiral away. We can determine the nature of each fixed point through linear stability analysis. The basic idea is to approximate the functions&nbsp;$f(x, v)$ and $g(x, v)$ by their Taylor expansions near each fixed point and look at the solutions of the linearized differential equation. If we do so, we get

```{math}
:label: generalphaseportraitexpansion
\begin{align*}
\dot{x} = f(x, v) \approx \left.\frac{\partial f}{\partial x}\right|_{\bm{x}_\mathrm{eq}} (x-x_\mathrm{eq}) + \left.\frac{\partial f}{\partial v}\right|_{\bm{x}_\mathrm{eq}} (v-v_\mathrm{eq}), \\
\dot{v} = g(x, v) \approx \left.\frac{\partial g}{\partial x}\right|_{\bm{x}_\mathrm{eq}} (x-x_\mathrm{eq}) + \left.\frac{\partial g}{\partial v}\right|_{\bm{x}_\mathrm{eq}} (v-v_\mathrm{eq}),
\end{align*}
```

where $\bm{x}_\mathrm{eq} = (x_\mathrm{eq}, v_\mathrm{eq})$ is the fixed point. We can re-write equation&nbsp;{eq}`generalphaseportraitexpansion` as a matrix equation

$$
\begin{pmatrix} \dot{x} \\ \dot{v} \end{pmatrix} = A \begin{pmatrix} x-x_\mathrm{eq} \\ v-v_\mathrm{eq} \end{pmatrix},
$$ (generalphaseportraitlinearization)

where $A$ is the matrix of first derivatives at the fixed points. The solution of equation&nbsp;{eq}`generalphaseportraitlinearization` is easy if $A$ has two different eigenvalues $\lambda$ and $\mu$, with corresponding eigenvectors $\bm{p}$ and $\bm{q}$:

$$
\begin{pmatrix} x \\ v \end{pmatrix} = \begin{pmatrix} x_\mathrm{eq} \\ v_\mathrm{eq} \end{pmatrix} + C e^{\lambda t} \begin{pmatrix} p_1 \\ p_2 \end{pmatrix} + D e^{\mu t} \begin{pmatrix} q_1 \\ q_2 \end{pmatrix},
$$ (generalphaseportraitlinearizationsolution)

where $C$ and $D$ are integration constants. We now have four options. If $\lambda$ and $\mu$ are both real, the solution will be a node. The stability of the node depends on the signs of the eigenvalues, as listed in table. If $\lambda$ and $\mu$ have a nonzero imaginary part, they must be each other's complex conjugate. As long as the eigenvalues have nonzero real part, we get a spiral, again with the stability depending on the sign. Finally, if the two eigenvalues are purely imaginary, we get periodic solutions.

```{figure} images/oscillationsandwaves/phaseportraits.svg
:name: fig:phaseportraits
Phase portraits in the ($x$, $v$) phase plane. Arrows indicate the direction a trajectory moves in at that point, continuous lines are example trajectories. (a) For a harmonic oscillator, the phase portrait consists of concentric ellipses (equation&nbsp;{eq}`harmonicoscillatorphaseportrait`). Different colors correspond to different energies; the blue dot at the origin is the single fixed point. (b) For a pendulum, the phase portrait contains stable fixed points (blue dots), closed trajectories (blue and green) for small amplitudes, saddle points (orange dots), marginal trajectories (orange lines) and open trajectories (red lines) corresponding to continuous rotations. (c) For a damped pendulum, the trajectories eventually become spirals into a stable fixed point. (d) Phase portrait of the nonlinear van der Pol oscillator (equation&nbsp;{eq}`vanderPoloscillator`).
```

(sec:coupledoscillators)=
## Coupled oscillators

(sec:coupledpendulums)=
### Two coupled pendulums

```{code-cell} ipython3
:tags: ["remove-input"]

import json
from jupyterquiz import display_quiz

with open("./quizes/chapter9/c9q4.json", "r", encoding="utf-8") as f:
    questions = json.load(f)

display_quiz(questions, shuffle_answers=False)
```

```{figure} images/oscillationsandwaves/Coupledpendulums.svg
:name: fig:coupledpendulums
Motion of two coupled pendulums. (a) Sketch of the setup. Two identical pendulums of length&nbsp;$L$ and mass&nbsp;$m$ are connected through a weak spring of spring constant&nbsp;$k$. As our initial condition we choose both pendulums at rest, with the right one in its equilibrium position and the left one given a finite amplitude. (b) Resulting motion of the two pendulums: left (blue) and right (orange).
```

```{index} pendulum ; coupled pendulums, coupled pendulums
```
A beautiful demonstration of how energy can be transferred from one oscillator to another is provided by two weakly coupled pendulums. Imagine we have two identical pendulums of length&nbsp;$L$ and mass&nbsp;$m$, which are connected by a weak spring with spring constant&nbsp;$k$ ({numref}`fig:coupledpendulums`a). The equation of motion of the combined system is then given by:

```{math}
:label: coupledpendulumA
\begin{align*}
L \ddot{\theta}_1 &= -g \sin\theta_1 - kL(\sin\theta_1 - \sin\theta_2), \\
L \ddot{\theta}_2 &= -g \sin\theta_2 + kL(\sin\theta_1 - \sin\theta_2).
\end{align*}
```

We will once again use the small angle expansion in which we can approximate $\sin \theta \approx \theta$, and identify $\omega_0 = \sqrt{g/L}$ as the frequency of each of the (uncoupled) pendulums. Equations&nbsp;{eq}`coupledpendulumA` then become

```{math}
:label: coupledpendulumB
\begin{align*}
\ddot{\theta}_1 &= -\omega_0^2 \theta_1 - k\theta_1 +k\theta_2, \\
\ddot{\theta}_2 &= -\omega_0^2 \theta_2 + k\theta_1 - k\theta_2.
\end{align*}
```

We can solve the system of coupled equations&nbsp;{eq}`coupledpendulumB` easily by introducing two new variables: $\alpha = \theta_1 + \theta_2$ and $\beta = \theta_1 - \theta_2$, which gives us two uncoupled equations:

```{math}
:label: coupledpendulumC
\begin{align*}
\ddot{\alpha} &= - \omega_0^2 \alpha, \\
\ddot{\beta} &= - \omega_0^2 \beta - 2 k \beta = - (\omega')^2 \beta,
\end{align*}
```

where $(\omega')^2 = \omega_0^2 + 2k$ or $\omega' = \sqrt{2 k + g/L}$. Since equations&nbsp;{eq}`coupledpendulumC`A and&nbsp;{eq}`coupledpendulumC`B are simply the equations of harmonic oscillators, we can write down their solutions immediately:

```{math}
\begin{align*}
\alpha(t) &= A \cos(\omega_0 t + \phi_0), \\
\beta(t) &= B \cos(\omega' t + \phi').
\end{align*}
```

Converting back to the original variables $\theta_1$ and $\theta_2$ is also straightforward, and gives

```{math}
\begin{align*}
\theta_1 &= \frac12(\alpha + \beta) = \frac{A}{2} \cos(\omega_0 t + \phi_0) + \frac{B}{2} \cos(\omega' t + \phi'),\\
\theta_2 &= \frac12(\alpha - \beta) = \frac{A}{2} \cos(\omega_0 t + \phi_0) - \frac{B}{2} \cos(\omega' t + \phi').
\end{align*}
```

Let's put in some specific initial conditions: we leave pendulum number 2 at rest in its equilibrium position ($\theta_2(0) = \dot{\theta}_2(0) = 0$ and give pendulum number&nbsp;1 a finite amplitude but also release it at rest ($\theta_1(0) = \theta_0$, $\dot{\theta_1}(0) = 0$). Working out the four unknowns ($A$, $B$, $\phi_0$ and $\phi'$) is straightforward, and we get:

```{math}
:label: coupledpendulumE
\begin{align*}
\theta_1 &= \frac{\theta_0}{2} \cos(\omega_0 t) + \frac{\theta_0}{2} \cos(\omega' t) = \theta_0 \cos\left(\frac{\omega_0 + \omega'}{2}t\right) \cos\left(\frac{\omega_0 - \omega'}{2}t\right),\\
\theta_2 &= \frac{\theta_0}{2} \cos(\omega_0 t) - \frac{\theta_0}{2} \cos(\omega' t) = \theta_0 \sin\left(\frac{\omega_0 + \omega'}{2}t\right) \sin\left(\frac{\omega' - \omega_0}{2}t\right).
\end{align*}
```

The solution given by equations&nbsp;{eq}`coupledpendulumE` is plotted in {numref}`fig:coupledpendulums`b. Note that the solutions have two frequencies (known as the *eigenfrequencies* of the system). The fast one, $\frac12(\omega_0 + \omega')$, which for a weak coupling constant&nbsp;$k$ is very close to the eigenfrequency&nbsp;$\omega_0$ of a single pendulum, is the frequency at which the pendulums oscillate. The do so in anti-phase, as expressed mathematically by the fact that one oscillation has a sine and the other a cosine (which is of course just a sine shifted over $\pi/2$). The second frequency, $\frac12(\omega' - \omega_0)$ is much slower, and represents the frequency at which the two pendulums transfer energy to each other, through the spring that couples them. In {numref}`fig:coupledpendulums`b, it is the frequency of the envelope of the amplitude of the oscillation of either of the pendulums. All these phenomena will return in the next section, in the study of waves, which travel in a medium in which many oscillators are coupled to one another.

(sec:normalmodes)=
### Normal modes

For a system with only two oscillators, the technique we used above for solving the system of coupled equations&nbsp;{eq}`coupledpendulumA` is straightforward. It does however not generalize easily to systems with many oscillators. Instead, we can exploit the fact that the equations are linear and use techniques from linear algebra (as you may have guessed from the term eigenfrequency). We can rewrite equations&nbsp;{eq}`coupledpendulumA` in matrix form:

$$
\frac{\mathrm{d}^2}{\mathrm{d}t^2} \begin{pmatrix}\theta_1 \\ \theta_2 \end{pmatrix} = \begin{pmatrix} -(\omega_0^2 + k) & k  \\ k & -(\omega_0^2 + k) \end{pmatrix} \begin{pmatrix}\theta_1 \\ \theta_2 \end{pmatrix}.
$$ (coupledpendulimatrixform)

Equation&nbsp;{eq}`coupledpendulimatrixform` is a homogeneous, second-order differential equation with constant coefficients, strongly resembling the equation for a simple, one-dimensional harmonic oscillator. Consequently, we may expect the solutions to look similar as well, so we try our usual Ansatz:

$$
\begin{pmatrix}\theta_1 \\ \theta_2 \end{pmatrix} = \begin{pmatrix}C_1 \\ C_2 \end{pmatrix} e^{i\omega t},
$$ (coupledpenduliAnsatz)

where $C_1$ and $C_2$ are constants. Substituting&nbsp;{eq}`coupledpenduliAnsatz` in&nbsp;{eq}`coupledpendulimatrixform` gives

$$
\begin{pmatrix} \omega_0^2 + k & -k  \\ -k & \omega_0^2 + k \end{pmatrix} \begin{pmatrix}C_1 \\ C_2 \end{pmatrix} = \omega^2 \begin{pmatrix}C_1 \\ C_2 \end{pmatrix},
$$ (coupledpendulieigenvalueproblem)

which you hopefully recognize as an eigenvalue problem. Solving for the eigenvalues $\omega^2$ gives:

$$
(-\omega^2 + \omega_0^2 + k)^2 - k^2 = 0.
$$ (coupledpendulieigenfrequencyeq)

The solutions of equation&nbsp;{eq}`coupledpendulieigenfrequencyeq` unsurprisingly reproduce the frequencies of the uncoupled equations in {numref}`sec:coupledpendulums`:

$$
\omega_{+}^2 = \omega_0^2, \quad \omega_{-}^2 = \omega_0^2 + 2 k.
$$ (coupledpendulieigenfrequencies)

The eigenvectors of&nbsp;{eq}`coupledpendulieigenvalueproblem` are given by

$$
\bm{C}_{+} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ 1 \end{pmatrix}\quad \text{for}\quad \omega_{+} \quad \text{and} \quad \bm{C}_{-} = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 \\ -1 \end{pmatrix}\quad \text{for}\quad \omega_{-}.
$$ (coupledpendulieigenvectors)

```{index} normal modes
```
Note that the eigenvectors are orthogonal; this is a general property of the eigenvectors of symmetric matrices. Each eigenvector corresponds to a possible steady-state of motion of the system; these states are known as the *normal modes* ('normal' referring to the orthogonality of the eigenvectors). We can now immediately write down the most general solution of equation&nbsp;{eq}`coupledpendulimatrixform` as a linear combination of the eigenmodes:

$$
\begin{pmatrix} \theta_1(t) \\ \theta_2(t) \end{pmatrix} = \frac{A_{+}}{2} e^{i(\omega_{+}t + \phi_{+})} \begin{pmatrix} 1 \\ 1 \end{pmatrix} + \frac{A_{-}}{2} e^{i(\omega_{-}t + \phi_{-})} \begin{pmatrix} 1 \\ -1 \end{pmatrix},
$$ (coupledpendulisolution)

where the amplitudes $A_\pm$ and phases $\phi_\pm$ are determined by the initial conditions.

```{index} phonons
```
Writing our system of equations in matrix form allows us to easily generalize both to asymmetric configurations (see problem&nbsp;{numref}`sec:coupledoscillators`.\ref{prob:coupledoscillators}) and to systems with many coupled oscillators. An important example of the latter case is the study of vibrations in solids. Atoms or ions in solids typically form a crystal lattice, that can be modeled as a large number of masses coupled by springs. Such crystals can have complicated vibrational properties, that can be analyzed in terms of its normal modes. In particular the modes with a low energy can typically be accessed easily. They are known as *phonons*, and correspond to sound waves in the solid.

## Problems
```{exercise} Speed in simple harmonic motion
:class: dropdown
An object undergoes simple harmonic motion of amplitude $A$ and angular frequency $\omega$ about the equilibrium point $x = 0$. Find the speed $v$ of the object in terms of $A$, $\omega$, and $x$.
*Hint*: use conservation of energy.
```

````{exercise} A mass connected by two springs
:class: dropdown
A mass $m$ is mounted between two springs with spring constants $k_1$ and $k_2$, as shown in the figure. The structure is constructed such that in equilibrium both springs attain their rest length. Naturally, shifting the block from equilibrium to the left or right and letting go results in oscillatory motion. In the case both the drag on the block and the friction between the block and the floor can be neglected, find the (angular) oscillation frequency of the block&nbsp;$\omega$.
```{figure} images/oscillationsandwaves/problems/blockwithtwosprings.svg
:width: 300
```
````

````{exercise} Oscillating suspended disk
:class: dropdown
A disk of radius&nbsp;$R$ and mass&nbsp;$M$ is suspended from a pivot somewhere between its center and its edge, see figure below. For what pivot point (i.e., which distance&nbsp;$d$) will the period of this physical pendulum be a minimum (or equivalently the frequency a maximum)? You may find one of the theorems we proved in {numref}`ch:rotation` useful in answering this question.
```{figure} images/oscillationsandwaves/problems/suspendeddisk.svg
:width: 300
```
````

````{exercise} Oscillating seesaw
:class: dropdown
{numref}`fig:seesaw2` shows a common present-day seesaw design, also featured in {numref}`pb:seesaw`. In addition to a beam with two seats, this seesaw also contains two identical springs (with spring constant $10\;\mathrm{kN}/\mathrm{m}$) that connect the beam to the ground. The distance between the pivot and each of the springs is $30.0\;\mathrm{cm}$, the distance between the pivot and each of the seats is $1.50\;\mathrm{m}$.
```{figure} images/oscillationsandwaves/problems/seesaw.svg
:name: fig:seesaw2
Seesaw with two springs.
```
Two children sit on the two seats. Both children kick off against the ground a couple of time, putting the seesaw in an oscillating motion with an amplitude of $50.0\;\mathrm{cm}$. At $t=0$ the children stop kicking. The plot in figure&nbsp;c shows the height of one of the seats as a function of time afterwards.
1. In what type of motion is the seesaw after the children stop kicking?
1. You could model the seesaw with the two children as a simple mass-on-a-spring, with a spring constant twice that of the individual spring in the seesaw. Using the graph in figure&nbsp;c, estimate the effective mass of this system.
1. After a while, the children resume kicking, slowly bringing their amplitude back up to $50.0\;\mathrm{cm}$. Using the mass-spring system of (b), estimate the amount of energy the children have to put in per period to achieve this.
````

````{exercise} Inelastic collision between an oscillating and a moving block
:class: dropdown
A block with mass $m_1 = 1.5\;\mathrm{kg}$ is supported by a frictionless surface and attached to a horizontal spring of constant&nbsp;$k=22\;\mathrm{N}/\mathrm{m}$, as shown in the figure. The block oscillates with an amplitude of&nbsp;$10.0\;\mathrm{cm}$, executing a simple harmonic motion.
```{figure} images/oscillationsandwaves/problems/slidingblockcollision.svg
:width: 400
```
1. Find the frequency&nbsp;$\omega$ of the oscillation of the block.
1. Write down the equation for the position of the block as a function of time, $x(t)$, in such a form that it is at its rightmost position at $t=0$.
    A second block of mass&nbsp;$0.80\;\mathrm{kg}$ moves in from the right at&nbsp;$2.5\;\mathrm{m}/\mathrm{s}$ and hits the first block at $t=0$, i.e., when it is in its rightmost position. The two blocks then stick together and continue moving as one.
1. Which quantity / quantities are conserved during the collision?
1. Determine the frequency of the motion of the two blocks after the collision.
1. Determine the amplitude of the motion of the two blocks after the collision.
````

```{exercise} Measuring gravitational acceleration
:class: dropdown
Suppose you are stranded on an unknown planet with nothing but a physical pendulum and a stopwatch. You determined the properties of the pendulum back on Earth, and found $m=2.0\;\mathrm{kg}$, $h = 0.50\;\mathrm{m}$ and $I = 3.0\;\mathrm{kg}\cdot\mathrm{m}^2$. Having nothing better to do, you measure the time it takes your pendulum to complete 50 cycles, and find that this time equals&nbsp;$170\;\mathrm{s}$. Use this information to compute the value of the gravitational acceleration&nbsp;$g$ on your new home world.
```

```{exercise} Power dissipated in a driven damped oscillator
:class: dropdown
For a damped harmonic oscillator driven by a sinusoidal force (as in equation&nbsp;{eq}`drivenharmosceom`), find the average power dissipated per (driving) period. *Hint*: use $P = F \cdot v$.
```

```{exercise} Two coupled harmonic oscillators
:label: prob:coupledoscillators
:class: dropdown
Consider a system of two coupled harmonic oscillators, where one (with mass&nbsp;$2m$ and spring constant&nbsp;$2k$) is suspended from the ceiling, and the other (with mass&nbsp;$m$ and spring constant&nbsp;$k$) is suspended from the first, as shown in the figure.
1. Find the equation of motion of this system of coupled oscillators, and write it in matrix form. For each mass, use coordinates in which the zero is at the equilibrium position.
1. Find the frequencies of the normal modes of this coupled system.
```

[^1]: Portrait of Christiaan Huygens by Caspar Netscher, painted in 1671, currently located at museum Boerhave in Leiden, The Netherlands. Picture is a faithful reproduction of a two-dimensional public domain work, retrieved from [Wikimedia commons](https://commons.wikimedia.org/wiki/File:Christiaan_Huygens-painting.jpeg).

[^2]: The only exception being functions of the form $x^{2n}$ for $n>1$.

[^3]: See {numref}`app:solode` for the mathematical details on how to solve general equations of this type.

[^4]: Unfortunately both the oscillation frequency and the angular velocity are usually denoted by&nbsp;$\omega$. While this makes sense in many cases, here it can lead to confusion. To be clear, the $\omega$ without subscript or prime in this subsection refers to the angular velocity of the pendulum, with frequency $\omega_0$; for the other sections in this chapter, the $\omega$'s with subscripts or primes are all frequencies.

