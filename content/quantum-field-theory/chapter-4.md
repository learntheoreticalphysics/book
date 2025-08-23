+++
title = "Non-trivial scalar field theories"
date = 2025-06-27
+++

Previously, we have seen how we could quantize a classical scalar field to obtain the quantum field theory of a free scalar field. But free fields are uninteresting; there are no interactions in a free field theory, so the fields are nothing but probabilities of their different states. In addition, free fields do not model any of the real fields we observe in nature. For anything to _happen_, so to speak, we must consider **interacting theories**, in which quantum fields interact, either with themselves (we'll soon get to what this means), or with other fields. Building on what we've learned, let's start by examining the theory of _interacting_ scalar fields.

## Interacting scalar fields and nuclear physics

Our journey into interacting scalar fields begins with a short dive into history. In the early 20th-century, physicists had just begun to understand the characteristics of the atomic nucleus. Experiments done by James Chadwick in 1932 confirmed the existence of **neutrons**, and it was known that atomic nuclei were formed by a combination of **protons and neutrons**.

This, however, left a big mystery. Protons are positively-charged particles, while neutrons have no net charge. This means that protons should repel each other by repulsive electromagnetic forces - in fact, very strongly so, at the extremely short distances between protons in the nucleus! So if the electromagnetic force is constantly trying to push protons apart in the nucleus, how could any atomic nucleus be stable?

The solution came in 1935, when the famed physicist Hideki Yukawa developed a theory for the **strong nuclear force**. Yukawa postulated the existence of a force holding the nucleus together, one that must be far, far stronger than the electromagnetic force - specifically, around 100 times stronger. Owing to the lack of creativity of physicists, we call it the _strong force_ (or more precisely, _strong nuclear force_) to this day. In Yukawa's model, nucleons (protons and neutrons) interact with each other by exchanging particles called **pions**. Energy and momentum is transferred between the nucleons by the creation of a pion from the energy-momentum of one nucleon, which scatters off the other nucleon, imparting its momentum onwards (in fact, this leads to an _attractive force_ that is modelled by the [Yukawa potential](https://en.wikipedia.org/wiki/Yukawa_potential), which we'll soon derive). Pions are associated with a quantum field of their own (the _pion field_ $\phi$), which shares much of the same form as the real scalar field Lagrangian we first examined, except with an additional _interaction term_ in the Lagrangian that gives rise to its interactions with nucleons. Yukawa's theory - and its subsequent confirmation - was one of the earliest successes of quantum field theory in explaining nuclear interactions.

In this chapter, we will get to the Yukawa theory later on, but we'll start with two much simpler scalar field theories.

## Schrödinger field theory

The first scalar field theory we'll examine is the field theory of the Schrödinger field. "Whaaaat...but the Schrödinger equation describes a wavefunction, not a field?!?!" you might say. This indeed _was_ true in single-particle quantum mechanics, but remember, single-particle quantum mechanics is an **approximation** to the more fundamental theory of QFT. Quantum field theory tells us that rather than describing a wavefunction, the Schrödinger equation actually describes a _scalar field_ in space. In fact, we can even write a Lagrangian for the Schrödinger scalar field:

{% math() %}
\mathscr{L} = i\overline \psi\, \partial_0 \psi + \dfrac{1}{2m}\partial_i \overline \psi\, \partial^i \psi - V(x^\mu) \psi \overline \psi
{% end %}

Where the third term containing $V(x^\mu)$ is the **interaction term**, and $V(x^\mu)$ is the field theory analogue to the classical potential energy term in the Schrödinger equation, and the space and time derivatives are written as $\partial_\mu = (\partial_0, \partial_i) = \left(\frac{\partial}{\partial t}, \nabla\right)$. We should note that the Lagrangian for the Schrödinger field is non-relativistic, but not all quantum field theories have to be relativistic, and we often study non-relativistic quantum field theories as approximations to more complex *relativistic* quantum field theories (more on that later).

What does the Schrödinger field physically represent? Well, we know that a field is a continuous quantity that permeates space. Thus, we can _physically interpret_ the Schrödinger field as describing _electrons_ distributed all throughout space; like any other quantum field, the excited states in the Schrödinger field are particles, and those particles (in our case) are electrons. This is similar in nature to the four-current $J^\mu$, which is _also_ a function of space, and which _also_ describes something formed by many (classical) charges. So we can say that the Schrödinger field is, in some ways, an analogue to the four-current at microscopic scales, with the small difference that the Schrödinger field is a scalar field (unlike the four-current, which is a vector, but assume we consider just the magnitude of the four-current). _Technically_, this interpretation is inaccurate, but for practical purposes, it is a good thinking aid.

> **Note:** One of the inaccuracies with this interpretation is that the Schrödinger field doesn't include the effects of **spin**, so technically it can only accurately model bosons (spinless particles) and not fermions (particles with spin-1/2, like electrons). However, as an approximation, the Schrödinger field can be used to describe electrons, as long as we are aware of this limitation.

And since any field has an associated equation of motion, so does the Schrödinger field - indeed, its equation of motion is simply the Schrödinger equation! In fact, any calculation in single-particle quantum mechanics can be done in quantum field theory, except with us recognizing that $\psi$, the solution to the Schrödinger equation, is a _field_, not a wavefunction. This change in interpretation of the Schrödinger equation - from describing a probabilistic wavefunction to a quantum field - is quite drastic and is often a major source of confusion, so we will spend some time discussing the Schrödinger field further before we move on to other scalar field theories.

### The free and interacting Schrödinger fields

The simplest Schrödinger field is one that contains no interactions - what we would call the _free particle_ in single-particle quantum mechanics. The Lagrangian for the free field is given by:

{% math() %}
\mathscr{L} = i\overline \psi\, \partial_0 \psi + \dfrac{1}{2m}\partial_i \overline \psi\, \partial^i \psi
{% end %}

We can proceed by using the Euler-Lagrange equations, as usual, which results in the following very familiar equation of motion:

{% math() %}
i\partial_0 \psi + \frac{1}{2m}\partial_i\partial^i \psi = 0
{% end %}

Which we can rewrite in more familiar non-tensor notation ($\partial_0 = \frac{\partial}{\partial t}, \partial_i \partial^i = \nabla^2$) as:

{% math() %}
i \dfrac{\partial}{\partial t} \psi = -\dfrac{1}{2m} \nabla^2 \psi
{% end %}

Which is simply the Schrödinger equation, with $\hbar = c = 1$, as per our convention! Again, it is important to remember that $\psi$ is _not_ the wavefunction, but a _field_ (which, for our purposes, we interpret as the _field of electrons_). Again, in this interpretation, the Schrödinger field is the quantum field whose excitations (excited states) are electrons; unlike the (typically) single-body wavefunction, the Schrödinger field describes an arbitrary number of electrons. In its classical limit, the Schrödinger field follows the Schrödinger equation, but again, it describes the effective mean field of _all_ electrons in space. It is also possible to interpret the square of the Schrödinger field $n(\mathbf{x}) = \overline \psi \psi$ as the _electron density_ of electrons in space (this is something also used in condensed matter physics, in a slightly different form to describe [effective fields of bosons](https://en.wikipedia.org/wiki/Bose%E2%80%93Einstein_condensate), but we'll get to that later).

### The limitations of the Schrödinger field theory

While a good basic model, the Schrödinger field does have significant limitations. First, the Schrödinger field treats nuclei as classical point particles that are infinitely heavy that generate a potential that interacts with the electrons, but are non-interacting themselves. This is pretty clearly a mathematical idealization that doesn't actually correspond to physical reality. Second, the Schrödinger field doesn't include the effects of **spin**. It is _possible_ to include the effect of spin by using the [Pauli Lagrangian](https://physics.stackexchange.com/questions/354346/whats-the-lagrangian-for-the-pauli-equation), shown below:

{% math() %}
\mathcal{L} = i\hbar\overline\psi\,\partial_0\psi - \overline\psi \cdot \Big(   \frac{1}{2m}(\boldsymbol{\sigma}\cdot(-i\hbar \nabla - q \mathbf{A}))^2 + q V \Big) \psi
{% end %}

Where $V$ is the electric potential, $\mathbf{A}$ is the magnetic vector potential, and $\mathbf{\sigma} = \langle \sigma_x, \sigma_y, \sigma_z\rangle$ are the **Pauli matrices**, a set of three $(2 \times 2)$ matrices with constant coefficients that are essential to our understanding of spin. Finally, we mentioned that the Schrödinger field is non-relativistic; indeed, it is a non-relativistic _approximation_ of a much more complicated _relativistic_ field, called the **Dirac field**, whose equation of motion is the famous **Dirac equation**. When we reach our chapter on quantum electrodynamics, we will discuss the Dirac field and Dirac equation in full detail, as well as its non-relativistic limit as the Schrödinger field.

### Recovering the single-particle wavefunction

Before we end, there is one more important topic to consider about the Schrödinger field, and that is the manner in which it reduces to the quantum wavefunction in the limit of few particles. We know that the Schrödinger field is actually the more fundamental entity, and that what we call the quantum "wavefunction" is just an approximation. But let's see how this approximation makes sense.

> **Note:** For simplicity purposes, instead of working in four-dimensional spacetime, we consider just one dimension of space and one of time. 

Recall that previously we saw that $\hat \psi(x) |0\rangle$ could be understood as a single-particle state with the particle at position $x$. Similarly, $\hat \psi^*(x')|0\rangle$ could be understood as a single-particle state with the particle at position $x'$. Then, the **propagator** is given by:

{% math() %}
D(\mathbf{x} - \mathbf{x}') = \langle 0|\hat \psi(x, t) \hat \psi^*(x', t')|0\rangle
{% end %}

We interpret $D(\mathbf{x} - \mathbf{x}')$ as telling us the probability amplitude that a particle originally known to be at position $x'$ at time $t'$ is later found to be at position $x$ at time $t$. Note that this interpretation so far is only correct for **single-particle states**, although it can be generalized.

Let's now turn back to non-relativistic quantum mechanics, where the unitary time-evolution operator $\hat U$ is responsible for evolving the quantum state from $|\Psi(t')\rangle$ at time $t'$ to $|\Psi(t)\rangle$ at time $t$. That is:

{% math() %}
|\Psi(t)\rangle = \hat U(t, t') |\Psi(t')\rangle
{% end %}

In single-particle quantum mechanics (or at least when particle number is fixed/there is no creation or annihilation of particles), one can construct position basis states $|x\rangle$ that describe a particle located at an exactly-known location $x$. In quantum field theory, this is not possible, because special relativity tells us that absolute space does not exist, so position is no longer an operator, and thus its eigenstates $|x\rangle$ do not exist anymore either. But in non-relativistic quantum mechanics, we *can* have position basis states, and this is what allows us to complete our derivation.

Suppose the particle's initial state is $|x'\rangle$, meaning it is known to be at location $x'$ at time $t'$. If we evolve the state with the time-evolution operator, then its state at time $t$ becomes $\hat U(t, t') |x'\rangle$. As usual in quantum mechanics, we _don't_ know what exactly this new position is, but we can find the _probability amplitude_ of this new position being some position $x$. This probability amplitude is given by $\langle x |\hat U|x'\rangle$, and is _exactly_ the free-particle propagator:

{% math() %}
D(x - x') = \langle x | \hat U|x'\rangle
{% end %}

To make the notation slightly more readable, consider a particle at known initial position $x'$ and initial time $t' = t_0$. Then, we may write the particle's initial state as:

{% math() %}
|\Psi_0\rangle = |\Psi(t_0)\rangle
{% end %}

With this cleaner notation, we find that if we use a clever rewriting trick, by letting $\hat U = \hat U \hat I$ (where $\hat I$ is the identity operator), we have:

{% math() %}
\begin{align*}
|\Psi(t)\rangle &= \hat U|\Psi_0\rangle \\
&= \hat U \hat I |\Psi_0\rangle \\
&= \hat U \int dx'\, |x'\rangle \langle x' |\Psi_0\rangle \\
&= \int dx'\, \hat U |x'\rangle \langle x' |\Psi_0\rangle
\end{align*}
{% end %}

This is because, for any continuous basis $|s\rangle$, the identity operator is _defined_ to be:

{% math() %}
\hat I = \int ds\,|s\rangle \langle s|
{% end %}

Then if we multiply both sides by $\langle x|$, we get:

{% math() %}
\begin{align*}
\langle x|\Psi(t)\rangle &= \langle x|\int dx'\, \hat U |x'\rangle \langle x' |\Psi_0\rangle \\
&= \int dx'\, \underbrace{\langle x| \hat U |x'\rangle}_{D(x-x')}\ \underbrace{\langle x' |\Psi_0\rangle}_{\Psi(x', t_0)} \\
&= \int dx'\, D(x - x')\Psi(x', t_0)
\end{align*}
{% end %}

But we know that $\langle x|\Psi(t)\rangle$ is just the wavefunction $\Psi(x, t)$ in the position basis! So:

{% math() %}
\langle x|\Psi(t)\rangle = \Psi(x, t) =\int dx'\, D(x - x')\Psi(x', t_0)
{% end %}

If we adopt the common notation where $\psi(x) \equiv \Psi(x, t_0)$ is the wavefunction at $t = t_0$, then we may write this even more simply as:

{% math() %}
\Psi(x, t) = \int dx'\, D(x - x')\psi(x')
{% end %}

Let's consider the case where we assume we know that at $t = t_0$, the particle is _exactly_ at a particular location $x'$, and we (as before) want to find its position at some later time $t$. In quantum field theory, this would be highly improbable, since particles are created and destroyed from the vacuum all the time. But in the single-particle limit, we can have perfectly-localized particles, in which case the initial wavefunction would be a delta function, that is, $\psi(x) = \delta(x-x')$. Then, we have:

{% math() %}
\begin{align*}
\Psi(x, t) &= \int dx'\, D(x - x')\psi(x') \\
&= \int dx' D(x - x') \delta (x - x') \\
&= D(x - x')
\end{align*}
{% end %}

Thus we have recovered the wavefunction from quantum field theory. Let's summarize our process: by making the approximation of low energies, where particles cannot be created or destroyed, the **propagator** $D(x-x')$ in quantum field theory can be interpreted as the probability amplitude for one particle initially known to be at $(x', t_0)$ to be found at $(x, t)$. In single-particle quantum mechanics, where position basis states $|x\rangle$ are well-defined (unlike in QFT), we can then write the propagator as $D(x - x') = \langle x | \hat U|x'\rangle$. With some clever math tricks, we showed that we could write the time-evolution of a quantum state in single-particle quantum mechanics as $|\Psi(t)\rangle = \displaystyle \int dx'\, \hat U |x'\rangle \langle x' |\Psi_0\rangle$, where we could then take the inner product with a position basis bra $\langle x|$ and rearrange to end up with the wavefunction. 

What the math is saying is that if we *assume* certain conditions (a single particle that cannot be destroyed and whose position can be definitively measured), then the propagator can be interpreted as _evolving_ a particle starting out in state $\psi(x) = \Psi(x, t_0)$ to end up in state $\Psi(x, t)$. And if we take that idea one step further and only care about where the particle _ends up_ after a certain time $t$, we can choose $\psi(x)$ to be a Delta function (representing a particle at a known position), in which limit the propagator _becomes_ the same thing as the wavefunction!

The big takeaway is this: the wavefunction $\psi$ in single-particle quantum mechanics is **completely different** from the more fundamental Schrödinger field $\hat \psi$ in quantum field theory, despite using confusingly-similar notation. The wavefunction $\psi$ is the non-relativistic _representation_ of the _quantum state_ of a single particle (or a small number of particles) with a well-defined position. It is only valid when particle numbers are fixed (meaning particles cannot be created or destroyed). But the Schrödinger field $\hat \psi$ represents the fundamental *quantum field* in which electrons (among other particles) exist, where *excitations* of the Schrödinger field are interpreted as those particles. However, in the special case of **single-particle states** $\hat \psi|0\rangle$ (or at least when there are a fixed number of particles), one can define a position basis $|x\rangle$ in which the state of the particle(s) can be expressed as a wavefunction $\Psi(x, t) = \langle x|\Psi\rangle$. Moreover, the propagator of the Schrödinger field, which expresses the probability a particle known to be at $(x', t')$ will be found at $(x, t)$, reduces down to the free-particle propagator $D(x - x') = \langle x | \hat U|x'\rangle$, which can be used to find the wavefunction $\Psi(x, t)$ given knowledge of a particle's initial state.

## Quartic field theory

The first interacting scalar field theory we'll examine in detail is known as **quartic field theory** or $\phi^4$ theory. It comes with the following Lagrangian:

{% math() %}
\mathscr{L} = \dfrac{1}{2} \partial^\mu \phi \partial_\mu \phi - \dfrac{1}{2} m^2 \phi^2 - \dfrac{\lambda}{4!}\phi^4
{% end %}

Where $\lambda$ is a constant called the **coupling constant** - we'll go into what this means later. We recognize the first two terms as being identical to the Lagrangian of a free scalar field (which we examined earlier). Like any Lagrangian, we can find the equations of motion for $\phi$ from the Euler-Lagrange equation:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \phi} - \partial_\beta \left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta \phi)}\right) = 0
{% end %}

A useful trick is to note that the first term is the _only_ term that involves a derivative of $\phi$, so the partial derivative of the Lagrangian with respect to $\partial_\mu \phi$ is _the same_ as that for the free scalar field Lagrangian, which we already calculated. From earlier, we found this to be given by:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial(\partial_\mu \phi)} = \partial^\mu \phi
{% end %}

Or equivalently, if we switch indices from $\mu \to \beta$:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta \phi)} = \partial^\beta \phi
{% end %}

Meanwhile, the derivative of the Lagrangian with respect to $\phi$ can be readily computed, as follows:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \phi} &= \dfrac{\partial}{\partial \phi} \left[- \dfrac{1}{2} m^2 \phi^2 - \dfrac{\lambda}{4!}\phi^4\right] \\
&= - m^2 \phi - \dfrac{\lambda}{3!} \phi^3
\end{align*}
{% end %}

So, substituting both results into the Euler-Lagrange equation, we get:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \phi} - \partial_\beta \left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta \phi)}\right) &= -m^2 \phi - \dfrac{\lambda}{3!} \phi^3 - \partial_\beta \partial^\beta \phi \\ &= 0
\end{align*}
{% end %}

If we clean things up a little bit and relabel $\beta \to \mu$ (as is common convention) we get:

{% math() %}
\partial_\beta \partial^\beta \phi + m^2 \phi = -\dfrac{\lambda}{3!} \phi^3
{% end %}

This is the **nonlinear Klein-Gordon equation**, and is the equation of motion for a quartic interacting scalar field. As a sidenote, it is closely related to the **Higgs field** in the Standard Model, which also involves a (modified) quartic interaction term and is also a (complex-valued) scalar field. In fact, studying the quartic theory will help us later on, when we examine the Higgs field and the Higgs mechanism in the Standard Model.

### The field Hamiltonian of interacting scalar fields

The simplest types of interacting scalar fields, including $\phi^4$ theory, have relatively simple field Hamiltonians (at least, by the standards of quantum field theory). This is because their Lagrangians can be written in the general form:

{% math() %}
\mathscr{L} = \dfrac{1}{a} \partial_\mu \phi \partial^\mu \phi - \dfrac{1}{b} m^2 \phi^2 + \mathscr{L}_\text{int}(\phi), \quad a, b = \text{const.}
{% end %}

Where $\mathscr{L}_\text{int}(\phi)$ describes the _interacting part_ of the field Lagrangian and thus only depends on the field $\phi$ itself, not its derivatives. This means that when we write the Hamiltonian in the form $\hat H = \hat H_0 + \hat H_I$, where $\hat H_I$ denotes the interaction part of the Hamiltonian, there is a relatively simple expression for $\hat H_I$; it is given by:

{% math() %}
\hat H_I = -\int d^3x\, \mathscr{L}_\text{int}(\phi)
{% end %}

Thus, for $\phi^4$ theory, we have:

{% math() %}
\mathscr{L}_\text{int}(\phi) = -\dfrac{\lambda}{4!} \phi^4 \Rightarrow \hat H_I = \int d^3x\, \dfrac{\lambda}{4!} \phi^4
{% end %}

Thus, the interaction Hamiltonian density $\mathcal{H}_I$ associated with the interaction Hamiltonian $\hat H_I$ is simply:

{% math() %}
\hat{\mathcal{H}}_I = \dfrac{\lambda}{4!} \phi^4
{% end %}


## Scattering processes

A common question we often ask in quantum field theory is this: given a known interacting field (or several) prepared in some initial state, how do the field(s) interact? We can also frame it in more common terminology as this: if we have some collection of particles (which, again, are excited states of quantum fields), what happens when they encounter other particles? In the case of $\phi^4$ theory, which describes _pions_, such interactions might include any of the following processes, which are called **scattering processes**:

- Two pions interacting with each other to produce two new pions
- One pion decays into several pions
- Several pions combine into one new pion
- A virtual pion is created and then instantly annihilated back into the vacuum
- Combinations of the above

Here, we come to a big problem: since $\phi^4$ theory is nonlinear (as it involves the field raised to the fourth power), it's impossible to do exact calculations with it! However, we do have a way around this. Recall that the Lagrangian of $\phi^4$ theory is identical to that of the free scalar field, with exception of the $-\frac{\lambda}{4!}\phi^4$ term. So we can do _approximate_ calculations by first assuming that the additional term represents a small _modification_ of the free scalar field. Since the free scalar field is a _linear_ theory, we can solve it exactly. We can then add the effects of the $\phi^4$ theory's additional term on top of the known solution to the free scalar field, which gives us a pretty good approximate result!

To understand how this procedure works, let us consider a quantum system with a Hamiltonian $\hat H$. This Hamiltonian can be divided into two parts: the free Hamiltonian $\hat H_0$, and the _interaction_ Hamiltonian $\hat H_I$. $\hat H_0$ is the Hamiltonian of the theory without any interactions (i.e. the free field theory), and $\hat H_I$ is a small perturbation, that is, a small corrective term that represents the deviation of the interacting field from the free field. We have:

{% math() %}
\hat H = \hat H_0 + \hat H_I
{% end %}

We can give this a physical interpretation, as follows: before and after an interaction happens, the quantum field(s) evolved as essentially free fields and aren't interacting. Think of two particles that initially start infinitely-far away from each other: they won't be able to have any effect on each other. During an interaction, however, the particles are at (relatively) close range, so the fields have a very brief period in which they interact. Thus, it is physically valid to consider the interaction as a small deviation from otherwise free fields.

We have thus simplified what would be a complicated problem into a slightly less-complicated problem, since we already know how to solve the theory of a _free_ scalar field. But how does that help us compute cross-sections? Now is a good time to review the basic postulates of quantum mechanics. Recall that the time-evolution of any quantum system is determined by the generalized Schrödinger equation:

{% math() %}
i\dfrac{\partial}{\partial t} |\psi\rangle = \hat H |\psi\rangle 
{% end %}

This holds true whether we're in quantum field theory or in non-relativistic quantum mechanics. Now, if we know the initial state of the system at $t = 0$, the Schrödinger equation can be "solved" with a particular operator called the **time-evolution operator** $\hat U$:

{% math() %}
|\Psi(t)\rangle = \hat U(t, t_0)|\psi\rangle
{% end %}

Where $|\psi\rangle = |\Psi(0)\rangle$. If we now take the inner product with $\langle \Psi(t)|$ on both sides, we have:

{% math() %}
\begin{align*}
\underbrace{\langle \Psi(t)|\Psi(t)\rangle}_A = \langle\Psi(t)|\hat U|\psi\rangle \\
A = \langle \Psi(t) |\hat U |\psi\rangle \\
A = \langle f|\hat U|i\rangle
\end{align*}
{% end %}

Where $|f\rangle = |\Psi(t)\rangle$ is the final state of the particle (at time $t$) while $|i\rangle = |\psi\rangle$ is the initial state of the particle (at time $t = 0$). The probability amplitude $A$ of the particle starting from state $|i\rangle$ to end up in state $|f\rangle$ a time $t$ layer is therefore given by $A = \langle f|\hat U|i\rangle$. By definition, $A$ is dimensionless, since it is a probability amplitude - and in general, it is complex-valued. The time-evolution operator can be written out in explicit form as a **[Dyson series](https://web2.ph.utexas.edu/~vadim/Classes/2016f/dyson.pdf)**:

{% math() %}
\begin{align*}
\hat U(t,t_0) & =1-i\int_{t_0}^tdt_1\hat H_I(t_1)-\int_{t_0}^tdt_2\hat H_I(t_2)\int_{t_0}^{t_2}dt_1\hat H_I(t_1) \\
 & +i\int_{t_0}^tdt_3\hat H_I(t_3)\int_{t_0}^{t_3}dt_2\hat H_I(t_2)\int_{t_0}^{t_2}dt_1\hat H_I(t_1)+\cdots \\
 & =1+\sum_{n=1}^\infty(-i)^n\underset{t_0<t_1<\cdots<t_n<t}{\operatorname*{\operatorname*{\int}}}dt_n\cdots dt_1\hat{H}_I(t_n)\cdots\hat{H}_I(t_1).
\end{align*}
{% end %}

In quantum field theory, the Dyson series is known as the **S-matrix** (short for _scattering matrix_). The basic concept of the Dyson series remains the same, although the notation is a bit different: we use $\hat S$ instead of $\hat U$, and the probability amplitude is usually denoted $\mathcal{A}$ instead of $A$. Using this new notation, the probability amplitude ($\mathcal{A}$) of a transition occuring from state $|i\rangle$ to state $|f\rangle$ takes the form:

{% math() %}
\mathcal{A} = \langle f |\hat S |i\rangle
{% end %}

Where the S-matrix (the QFT version of the Dyson series) takes the form:

{% math() %}
\begin{align*}
\hat S &= \sum_{n=0}^\infty \frac{(-i)^{n}}{n!}\int d^4x_{1} \cdots \int d^4x_{n} \mathcal{T} \bigg\{ \mathcal{H}(x_{1})\cdots \mathcal {H}(x_{n}) \bigg \} \\
&= 1 -i \int d^4x_{1} \,\mathcal{T}\left\{{\mathcal {H}}(x_{1})\right\} \\
&\qquad+ \dfrac{(-i)^2}{2!} \int d^4x_{1}\,d^4x_2\,\mathcal{T}\left\{ \mathcal{H}(x_1)\mathcal{H}(x_2)\right\} + \dots
\end{align*}
{% end %}

Here, $\mathcal{T}\{\dots \}$ is the **time-ordering operator**, which sorts operators in order. This is very important to ensure that we don't break causality by having scattering events that go backwards in time! It is defined by:

{% math() %}
\langle 0|\mathcal{T} \big\{ \hat \phi(x_2) \hat \phi(x_1) \big\} |0\rangle = \begin{cases}
\langle 0|\hat \phi(x_2) \hat \phi(x_1)|0\rangle, & t_2 > t_1, \\
\langle 0|\hat \phi(x_1) \hat \phi(x_2)|0\rangle, & t_1 > t_2
\end{cases}
{% end %}

This definition may _look_ complicated, but it actually captures a much simpler idea: if a particle is created at point $x_1$ in spacetime and propagates to position $x_2$, we can't find it at $x_2$ before it is created, or otherwise we'd have particles travelling backwards in time! Without the time-ordering operator, physics would break down, so the time-ordering operator is **absolutely essential**; we will therefore discuss it at length later. With these definitions, the probability amplitude $\mathcal{A}$ can then be explicitly written as an infinite series:

{% math() %}
\begin{align*}
\mathcal{A} &= \mathcal{A}_{(0)} + \mathcal{A}_{(1)} + \mathcal{A}_{(2)} + \mathcal{A}_{(3)} + \dots + \mathcal{A}_{(\infty)}, \\
&\qquad \mathcal{A}_{(n)} = \left\langle i\left|\frac{(-i)^{n}}{n!}\int d^4x_{1} \cdots \int d^4x_{n} \mathcal{T} \bigg\{ \mathcal{H}(x_{1})\cdots \mathcal {H}(x_{n}) \bigg \}\right| f\right\rangle
\end{align*}
{% end %}

The S-matrix is significant because it is the main way we calculate **probability amplitudes** in quantum field theories. This means that calculating scattering processes in quantum field theory is therefore equivalent to obtaining the S-matrix associated with different quantum fields, and then using its series expansion to calculate the probability amplitudes for the processes we're interested in.

> **Why is the S-matrix called a matrix?** This is to do with the fact that formally, the S-matrix is indeed a type of matrix, since it maps an initial state-vector $|i\rangle$ to a final state $\langle f|$, exactly as a matrix would map a vector to another vector. The fact that it is typically expressed as a product of integrals simply stems from the fact that the Hamiltonian in quantum field theories is the Hamiltonian density integrated over all space, so the S-matrix is filled with integrals.

### Computing the S-matrix

The S-matrix is conceptually powerful, but it is an _infinite_ series and usually cannot be summed explicitly. So, to make it actually _computable_, we usually take only the first few terms of the S-matrix into account when computing the probability amplitude $\mathcal{A}$. The zeroeth-order term $\mathcal{A}_{(0)} = \langle f|i\rangle$ describes a non-interacting free field, so the dominant contribution to most QFT interactions are found in the first-order and second-order terms, which are respectively:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= (-i)\left\langle f\left|\int d^4x_{1} \,\mathcal{T}\left\{{\mathcal {H}}(x_{1})\right\}\right|i\right\rangle \\
\mathcal{A}_{(2)} &= \dfrac{1}{2}\left\langle f\left|\int d^4x_{1}\,d^4x_2\,\mathcal{T}\left\{ \mathcal{H}(x_1)\mathcal{H}(x_2)\right\}\right|i\right\rangle
\end{align*}
{% end %}

> **Note:** Here, be careful of the notation we use: $i$ in $(-i)$ is the imaginary unit, but $|i\rangle$ is the initial state.

This means that the total probability amplitude $\mathcal{A}$, to second-order, becomes:

{% math() %}
\begin{align*}
\mathcal{A} &= \mathcal{A}_0 + \mathcal{A}_1 + \mathcal{A}_{(2)} \\
&= \langle f|i\rangle + \mathcal{A}_1 + \mathcal{A}_{(2)}
\end{align*}
{% end %}

Let's demonstrate by using the case of the scalar $\phi^4$ field theory. Recall that the interaction Hamiltonian density for $\phi^4$ theory is:

{% math() %}
\mathcal{H}_I = \dfrac{\lambda}{4!} \hat \phi^4 
{% end %}

So, if we substitute our interaction Hamiltonian, the first- and second-order terms in the probability amplitude are, respectively:

{% math() %}
\begin{align*}
% first order
\mathcal{A}_{(1)} &= \dfrac{-i\lambda}{4!}\int d^4x \langle f|\,\mathcal{T}\{\hat \phi^4\}|i\rangle \\
&= \dfrac{-i\lambda}{4!}\int d^4x \langle f|\,\mathcal{T}\bigg\{\hat \phi(x^\mu) \hat \phi(x^\mu) \hat \phi(x^\mu) \hat \phi(x^\mu)\bigg\}|i\rangle \\
% second order
\mathcal{A}_{(2)} &= \dfrac{1}{2}\left\langle f\left|\int d^4x_{1}\,d^4x_2\,\mathcal{T}\big\{ \mathcal{H}(x_1)\mathcal{H}(x_2)\big\}\right|i\right\rangle \\
&= \dfrac{\lambda}{12} \int d^4 x_1\, d^4 x_2 \langle f | \bigg\{\hat \phi(x_1^\mu) \hat \phi(x_1^\mu) \hat \phi(x_1^\mu) \hat \phi(x_1^\mu) \\
&\qquad \qquad \times \hat \phi(x_2^\nu) \hat \phi(x_2^\nu) \hat \phi(x_2^\nu) \hat \phi(x_2^\nu) \bigg\}|i\rangle
\end{align*}
{% end %}

It is common for physicists to be sloppy with their notation and ignore writing the operator hats and $x_1, x_2, \dots x_n$, so you can often see e.g. $\langle f|\phi(x) \phi(y) |i\rangle$ which actually means $\langle 0 |\hat \phi(x_1^\mu)\, \hat \phi(x_2^\nu)|0\rangle$. Here, $x, y$ mean _two distinct spacetime locations_, not the $x$ and $y$ components of a spacetime position! We will not drop the operator hats, but we will adopt the $x, y$ notation simply because it makes these extremely verbose expressions in the S-matrix easier to write. With the new "sloppy" physics notation, we have:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= \dfrac{-i\lambda}{4!} \int d^4 x \langle f| \mathcal{T}\{\hat \phi(x) \hat \phi(x) \hat \phi(x) \hat \phi(x)\}|i\rangle \\
\mathcal{A}_{(2)} &= \dfrac{\lambda}{12} \int d^4x\, d^4 y\, \langle f| \mathcal{T}\bigg\{\hat \phi(x) \hat \phi(x) \hat \phi(x) \hat \phi(x) \\
&\qquad \qquad \times \hat \phi(y) \hat \phi(y) \hat \phi(y) \hat \phi(y)\bigg\} |i\rangle
\end{align*}
{% end %}

We immediately see that we have terms in the form $\langle f | \hat \phi(x) \hat \phi(x) \dots \hat \phi(x)|i\rangle$, where we repeatedly apply the field operator on states. These are called **correlation functions**. You will often see texts referrring to the _n-point correlation function_, which is defined as applying the field operator $n$ times on the initial state, that is, $\langle f | \underbrace{\hat \phi(x) \hat \phi(x) \dots \hat \phi(x)}_{n \text{ times}}|i\rangle$.

## Cross sections and transition rates

When discussing quantum field theory, it is impossible to avoid the topic of **scattering cross-sections**, usually just called "cross-sections". Cross-sections are a way of describing the probability of particle-particle interactions within quantum field theory. Why is this important? Because we know that quantum physics is inherently _statistical_, in that among very few things we can theoretically predict are the _probabilities_ of a particular interaction occuring. In general, these probabilities are extremely small. For instance, in the famous [photoelectric effect](https://en.wikipedia.org/wiki/Photoelectric_effect), photons fired at a metal target have a small chance of colliding with one of the valence electrons in the target's atoms, but the probability of this occuring is around  $10^{-6}$ to $10^{-5}$, meaning that on average, for close to every _million_ photons, only _one_ interacts with an atom and causes the release of an electron![^1] What is important, however, is that these probabilities can be _precisely_ measured with modern equipment, and they provide important tests of quantum field theory.

To understand the concept of a cross-section, imagine an archer shooting arrows at a target while blindfolded. The archer cannot see their target while blindfolded, so the archer shoots an enormous number of arrows in the hopes that at least some of their arrows will manage to hit the target. But - alas! - the archer is then told (by some overenthusiastic sports announcer) that the arrows they shot have _bounced off_ the target, so they don't actually know how many arrows hit before bouncing off! However, by asking the sports announcer about the places the arrows landed, the archer can roughly estimate the size of the target, and therefore approximately how many arrows hit on-target. That estimated target size is what we would call the **cross-section** $\sigma$, and the archer's estimate of the percentage of the arrows that hit on-target across the total time they were shooting is what we would call the **transition rate** (the probability of a transition, or in this case a successful hit, per unit time). 

The archer may also want to be more specific, and examine their hit-rate at different shooting angles. If the target is not a perfectly-symmetric shape, the archer may find that shooting at different angles to the target leads to a different hit-rate. Thus, the target size *appears* to change as a function of angle, and the target size per unit angle is what we would call the **differential cross-section**, denoted $\frac{d\sigma}{d\Omega}$. Of course, all this happens without the blindfolded archer being _actually aware_ of how the target looks like or what the target's shape is. The archer can only shoot lots of arrows in many different directions and ask the sports announcer where their arrows ended up, so as to reconstruct a mental image of their target.

If all of this is too much imagination, blame us physicists! However, the point this analogy was trying to get across is that the _physical_ idea of a cross-section is the _effective area_ of a hypothetical object scattering the incident particles. That is, in any particular scattering process described in quantum field theory, where particles interact with each other, the cross-section is the size of an imaginary object that would scatter the particles in the same way as the actual quantum process. Cross-sections are often extremely tiny, and are usually measured in units of $\pu{fm^2}$ ($\pu{1 fm} = \pu{10^{-15}m}$) or barns ($\pu{b}$), where $\pu{1b} = \pu{100 fm^2}$ (just to be clear, _barns_, despite their name, are not used to measure the enclosures of livestock; rather, they are a unit predominantly used in particle physics). Borrowing our previous example of the photoelectric effect, we can replicate the 1-million-to-1 chance of a photon managing to eject an electron with classical particles scattering off an _imaginary_ sphere whose cross-sectional area is roughly $\pu{0.38 nm^2}$[^2]. Such a tiny sphere would barely be much of a collision target, so most of the incident particles wouldn't even collide with it, leaving only a few particles (1 in a million) to actually scatter off the sphere, which reproduces the transition rates we observe in the photoelectric effect. Using the same analogy, the *differential* cross-section would be the cross-sectional area of a tiny angular slice of that same hypothetical scattering object - which is hugely important for particle processes whose cross-section is dependent on angle. With powerful particle detectors all over the world specifically dedicated to measuring cross-sections, and equally impressive mathematical tools (as well as decades of theoretical research) into cross-sections, it is no wonder that so much of quantum field theory is _all about_ cross-sections.

> **Note:** [This article from CERN](https://cms.cern/news/what-do-we-mean-cross-section-particle-physics) and [this Physics Stack Exchange answer](https://physics.stackexchange.com/a/777460/497517) are also good resources for gaining more intuition on cross-sections.

### Scattering cross-sections

While we will wait until the next chapter to actually _compute_ cross-sections, now is a good time to understand how cross-sections can be found from the S-matrix. Recall that the probability amplitude is given by:

{% math() %}
\begin{align*}
\mathcal{A} &= \langle f|\hat S|i\rangle \\ &= \langle f|i\rangle 
-i \left\langle f\left|\int d^4x \,\mathcal{T}\left\{{\mathcal {H}}(x)\right\} \right|i\right \rangle \\
&\qquad\qquad+ \dfrac{(-i)^2}{2!} \left\langle f\left| \int d^4x\,d^4y\,\mathcal{T}\left\{ \mathcal{H}(x)\mathcal{H}(y)\right\}\right|i\right \rangle + \dots 
\end{align*}
{% end %}

The probability amplitude is essential in quantum field theory, but it itself is not a physically-measurable quantity: it is usually complex-valued and often contains delta functions that become infinite when their argument is zero. Instead, we define an **invariant amplitude** $\mathcal{M}$, which is related to the probability amplitude $\mathcal{A}$ by:

{% math() %}
\begin{align*}
\mathcal{A} &= \langle f|i\rangle + i\mathcal{M}(2\pi)^4\delta^4\left(\sum_j p_j - \sum_j q_j\right) \\
&= \langle f|i\rangle + i\mathcal{M}(2\pi)^4\delta^4(p_1 +p_2 + \dots + p_n- q_1 - q_2 - \dots -q_n)
\end{align*}
{% end %}

Where $p_1, p_2, \dots$ are the momenta of each of the **incident** particles, and $q_1, q_2, \dots$ are the momenta of each of the **outgoing** particles. The above equation may also be written in a more elegant manner if we define $P = \sum_j p_j$ as the **total momentum** of all incident particles, and $Q = \sum_j q_j$ as the **total momentum** of all outgoing (scattered) particles. This greatly simplifies the formula to:

{% math() %}
\mathcal{A} = \langle f|i\rangle + i\mathcal{M}(2\pi)^4 \delta^4(P - Q)
{% end %}

> **Note for the advanced reader:** The invariant amplitude $\mathcal{M}$ is chosen so that it reproduces the transition matrix element $M_{if}$, which appears in [Fermi's Golden Rule](https://hyperphysics.phy-astr.gsu.edu/hbase/quantum/fermi.html) from **non-relativistic quantum mechanics**.

Unlike the probability amplitude $\mathcal{A}$, the invariant amplitude $\mathcal{M}$ does _not_ include any delta functions and therefore avoids the issue of singularities associated with delta functions. This means that quantities depending on $|\mathcal{M}|^2$, which is real-valued, _can_ actually be measured. For instance, the differential cross-section of any two-particle scattering process is given by:

{% math() %}
\dfrac{d\sigma}{d\Omega} = \dfrac{1}{64\pi^2 E_\mathrm{cm}^2} \dfrac{|\mathbf{p}_f|}{|\mathbf{p}_i|} |\mathcal{M}|^2
{% end %}

Where $E_\mathrm{cm}$ is the total energy in the center-of-momentum frame, and $\mathbf{p}_i, \mathbf{p}_f$ are the initial and final (3-)momenta of the particles (again in the center-of-momentum frame).

> **Note:** This expression is in natural units: to convert to SI units simply multiply the differential cross-section formula given above by a factor of $\hbar^2 c^2$.

In the case that the two particles have identical masses (which is always true for massless particles like photons), the differential cross-section simplifies to:

{% math() %}
\dfrac{d\sigma}{d\Omega} = \dfrac{1}{64\pi^2 E_\mathrm{cm}^2}  |\mathcal{M}|^2
{% end %}

To find the _total cross-section_ $\sigma$, we integrate the differential cross-section across all angles $\phi$ and $\theta$, which gives us:

{% math() %}
\sigma = \int_0^{2\pi} d\phi \int_0^\pi d\theta\sin \theta \left(\dfrac{d\sigma}{d\Omega}\right)
{% end %}

In an actual experimental setting, cross-sections are not measured directly - after all, they are an abstract quantity in the first place! Instead, a particle beam is fired at some target with a known particle density; some particles in the original beam will not interact with the target's particles at all, whereas others do interact and are scattered. By counting the number of scattered particles versus the number of particles in the original beam, we can deduce the approximate probability that an incident particle will end up getting scattered. For instance, let $n_i$ be the number of incident particles, and $n_s$ be the number of particles scattered. Then, the probability $\mathscr{p}$ that an incident particle gets scattered would be given by:

{% math() %}
\mathscr{p} = \dfrac{n_s}{n_i}
{% end %}

Now, let $N$ be the number of particles per unit area of the target. The cross-section $\sigma$ can then be found by the formula:

{% math() %}
\sigma = \dfrac{\mathscr{p}}{N} = \dfrac{n_s}{n_i N}
{% end %}

For instance, let us consider an imaginary particle collider (similar to the [Large Hadron Collider](https://en.wikipedia.org/wiki/Large_Hadron_Collider)) that produces two particle beams, each with $N = \pu{5E17 m^{-2}}$ particles per unit area, and aims them at each other[^3]. The cross-sectional area of the beam is about $\pu{3 mm^2}$, meaning that the number of incident particles on the target is $\pu{3mm^2} \times \pu{5E30 m^{-2}}$, which evaluates to $1.5\times 10^{12}$ incident particles. Now, assume that the detector measured $850$ scattered particles. The cross-section of the process is then given by:

{% math() %}
\sigma = \dfrac{850}{1.5\times 10^{12}} \dfrac{1}{\pu{5E17 m^{-2}}} \approx \pu{1.1E-21 mm^2} = \pu{11.3b}
{% end %}

As another example, in the case of **Thomson scattering**, where an incident photon scatters off a non-relativistic electron, the cross-section is given by:

{% math() %}
\sigma = \dfrac{8\pi}{3} \left(\dfrac{\alpha \lambda_c}{2\pi}\right)^2
{% end %}

Where $\alpha \approx 1/137$ is the fine-structure constant, and $\lambda_c$ is the Compton wavelength of the electron (which we saw at the start of the book). This leads to a numerical value of about $\pu{0.65 b}$, which has been [closely-measured experimentally](https://physics.nist.gov/cgi-bin/cuu/Value?sigmae) and has shown excellent agreement with theory.

[^1]: <p style="font-size: small">This assumes 10 nm X-rays incident on sodium atoms. The numerical value was computed via the formula $\sigma = \frac{16\pi\sqrt{2}}{3}\alpha^8 Z^5 a_0^2 (m_e c^2/E_\gamma)^{7/2}$, taken from <a href="https://bohr.physics.berkeley.edu/classes/221/9697/photelec.pdf">the Physics 221 Lecture Notes</a> from the University of Berkeley.</p>
[^2]: <p style="font-size: small">This figure is from <a href="https://physics.stackexchange.com/questions/193622/quantum-efficiency-of-photoelectric-effect">this Physics SE answer</a> on the photoelectric effect.</p>
[^3]: <p style="font-size: small">These figures are fictitious but partially based on <a href="https://lhc-machine-outreach.web.cern.ch/beam.htm">this source from CERN</a> that provides specifications of the Large Hadron Collider's particle beams.</p>