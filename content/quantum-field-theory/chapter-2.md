+++
title = "Quantization of a free scalar field"
date = 2025-04-28
+++

## Quantization of a free scalar field

The free scalar field - the simplest quantum field theory - is a natural extension of the model of the quantum harmonic oscillator. In the quantum harmonic oscillator, we have a ground state that we denote as $|0\rangle$, and any number of excited states $|1\rangle, |2\rangle, |3\rangle, \dots, |n\rangle$. We also have the following Hamiltonian:

{% math() %}
\hat H = \hbar \omega \left(\hat a^\dagger \hat a + \dfrac{1}{2}\right) = \hbar \omega \left(\hat N + \dfrac{1}{2}\right)
{% end %}

Where $\hat N = \hat a^\dagger \hat a$ is the **number operator**. The $\hat a^\dagger$ (raising) and $\hat a$ (lowering) operators respectively increase the state to a higher-energy state or lower the state to a lower-energy state. That is:

{% math() %}
\begin{align*}
\hat a^\dagger |n\rangle = \alpha_+ |n + 1\rangle \\
\hat a |n\rangle = \alpha_- |n -1\rangle
\end{align*}
{% end %}

Where $\alpha_+, \alpha_-$ are the eigenvalues of the raising and lowering operators respectively, for a single oscillator. If we have multiple quantum harmonic oscillators, then we would need to sum over each of the individual oscillators, giving us the Hamiltonian:

{% math() %}
\hat H = \sum_i \hbar \omega_i \left(\hat a^\dagger_i \hat a_i + \dfrac{1}{2}\right)
{% end %}

To go from the quantum harmonic oscillator to quantum field theory, we need to make "just" a few changes:

- Instead of the position and momentum operators $\hat x, \hat p$, we switch to the **field operator** $\hat \phi$ and **momentum density operator** $\hat \pi$ 
- We derive the field operator by solving the Euler-Lagrange equations from a **field Lagrangian** $\mathscr{L}$ and making the suitable identifications of the appropriate raising and lowering operators, which we reinterpret as _creation_ and _annihilation_ operators
- The Hamiltonian must sum over an infinite number of harmonic oscillators, so the sum over oscillators becomes an integral
- The states $|0\rangle, |1\rangle, |2\rangle, \dots |n\rangle$ are now the states of the _quantum field_ $\hat \phi$, where the field has now become an operator with $|0\rangle, |1\rangle, |2\rangle, \dots |n\rangle$ being its eigenstates

### Sidenote on notation

In quantum field theory, there are a billion different conventions for almost *anything*. This leads to some pretty bizarre results:

- Momentum ($p$) becomes the same thing as the wavevector ($k$), because in natural units where $\hbar = 1$ (like we're using), $p = \hbar k$ becomes $p = k$
- For photons, angular frequency $\omega$ and energy $E$ become equivalent, because in natural units where $c = 1$ (like we're using), $E = \hbar \omega$ becomes $E = \omega$
- Einstein's relativistic energy-momentum relation of $E^2 = (pc)^2 + (mc^2)^2$ becomes simply $E^2 = p^2 + m^2$, so we get $E = \sqrt{p^2 + m^2}$. You may also see this denoted as $E_p = \sqrt{p^2 + m^2}$, such as in Peskin and Schroeder's _An Introduction To Quantum Field Theory_.

This means that every text often has its own notational system, especially if a certain text doesn't use natural units. Here, we will **always use natural units** unless otherwise denoted.

### Equations of motion of a free scalar field

The "simplest" quantum field theory is the theory of a free scalar field. We should note that "simple" is a rather relative term; approaching even this relatively simple quantum field theory can be an intimidating task, so it's important that we get the basics down.

Since the free scalar field theory is after all a _field theory_, we start with its field Lagrangian. In this case, the field Lagrangian of a free scalar field is given by:

{% math() %}
\mathscr{L} = \partial_\mu \phi \partial^\mu \phi - m^2 \phi^2
{% end %}

Using the Euler-Lagrange equations, we can find the equations of motion of the field $\phi$. For the free scalar field, the Euler-Lagrange equations take the form:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \phi} - \partial_\beta \left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta \phi)}\right) = 0
{% end %}

Let's now compute the partial derivatives. Let's start with the derivative with respect to $\phi$, which is relatively simple to find:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \phi} = -2m^2 \phi
{% end %}

The derivative with respect to $\partial_\beta \phi$ is not as easy to find, so we'll show the steps below:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta \phi)}
&= \dfrac{\partial}{\partial(\partial_\beta \phi)} \bigg(\partial_\mu \phi \partial^\mu \phi - m^2 \phi^2\bigg) \\
&= \dfrac{\partial}{\partial(\partial_\beta \phi)} \bigg(\partial_\mu \phi \partial^\mu \phi\bigg) - \cancel{\dfrac{\partial}{\partial(\partial_\beta \phi)}\bigg(m^2 \phi^2\bigg)}^0 \\
&= \dfrac{\partial}{\partial(\partial_\beta \phi)} \underbrace{\bigg(\partial_\beta \phi \partial^\beta \phi\bigg)}_\text{relabel dummy indices} \\
&= \dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \underbrace{\eta^{\alpha \beta}\partial_\alpha \phi}_\text{lower indices}\bigg) \\
&= \dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \eta^{\alpha \beta} \underbrace{\delta^\beta{}_\alpha \partial_\beta}_\text{relabel}  \phi\bigg) \\
&= \eta^{\alpha \beta} \delta^\beta{}_\alpha\dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \partial_\beta \phi\bigg)
\end{align*}
{% end %}

Let's recap on the steps we've done so far. First, since the $m^2 \phi^2$ term doesn't depend on the derivatives of $\phi$, its partial derivative is zero. This leaves us with just the $\partial_\mu \phi \partial^\mu \phi$ term left. Since $\mu$ is repeated over the upper and lower indices, we know that it is a **dummy index** so we can relabel it whatever we want - here we chose $\mu \to \beta$ because we're differentiating with respect to $\beta$, because again, since it's a dummy index, $\partial_\mu \phi \partial^\mu \phi = \partial_\beta \phi \partial^\beta \phi$.

Finally, we needed to get the $\partial^\beta \phi$ term as a lower index. To do this, we used the Minkowski metric $\eta^{\alpha \beta}$ to lower the index, and then used the Kronecker delta {% inlmath() %}\delta^\beta{}_\alpha{% end %} to relabel. The end result we got was {% inlmath() %}\partial^\beta \phi = \eta^{\alpha \beta} \delta^\beta{}_\alpha \partial_\beta \phi{% end %}, from which we could pull out the (constant) factor of {% inlmath() %}\eta^{\alpha \beta} \delta^\beta{}_\alpha{% end %}. This gives us everything inside the derivative _purely_ in terms of {% inlmath() %}\partial_\beta \phi{% end %}, at which point we can _finally_ differentiate:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial (\partial_\beta \phi)} &= \eta^{\alpha \beta} \delta^\beta{}_\alpha\dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \partial_\beta \phi\bigg) \\
&= \eta^{\alpha \beta} \delta^\beta{}_\alpha (2\partial_\beta \phi) \\
&= \underbrace{2\eta^{\alpha \beta}\delta^\beta_\alpha \partial_\beta \phi}_\text{now contract indices} \\
&= 2 \partial^\beta \phi
\end{align*}
{% end %}

Here, we took the derivative in the standard way (it is just taking the derivative of $(\partial_\beta \phi \partial_\beta \phi)^2$ which yields $2\partial_\beta \phi$). Then, we contracted the indices with the Minkowski metric and Kronecker delta terms, giving us $\eta^{\alpha \beta}\delta^\beta_\alpha \partial_\beta \phi = \partial^\beta \phi$. So, substituting into the Euler-Lagrange equations, we have:

{% math() %}
\begin{gather*}
-2m^2 \phi - \partial_\beta(2\partial^\beta \phi) = 0 \\
\Rightarrow \partial_\beta \partial^\beta \phi + m^2 \phi = 0
\end{gather*}
{% end %}

This is our **equation of motion**, and it is called the **Klein-Gordon equation**, although it is usually written with the dummy index $\mu$ instead of $\beta$, in which it takes the form:

{% math() %}
\partial_\mu \partial^\mu \phi + m^2 \phi = 0
{% end %}

We may solve the Klein-Gordon equation with a [Fourier decomposition](https://ese-msc.github.io/preinduction/edsml/primer/notebooks/c_mathematics/differential_equations/11_pde_fourier.html), which gives the general solution:

{% math() %}
\phi(x^\mu) = \int \dfrac{d^3 p}{(2\pi)^32E} \left[a(p) e^{i\mathbf{p} \cdot \mathbf{x}} + a^*(p) e^{-i\mathbf{p} \cdot \mathbf{x}}\right] 
{% end %}

Where $E = \sqrt{p^2 + m^2}$ comes from the energy-momentum relation, as we discussed earlier. We may promote this to a field if we make the identifications of $a \to \hat a$, $a^* \to a^\dagger$, which are the _creation and annihilation operators_ which generalize the raising and lowering operators we previously saw. Thus, our _quantum_ field $\hat \phi$ is now an operator:

{% math() %}
\hat \phi(x^\mu) = \int \dfrac{d^3 p}{(2\pi)^32E} \left[\hat a(p) e^{i\mathbf{p} \cdot \mathbf{x}} + \hat a^\dagger(p) e^{-i\mathbf{p} \cdot \mathbf{x}}\right] 
{% end %}

For mathematical convenience we write $\hat a(p)$ as $\hat a_p$ and $\hat a^\dagger(p)$ as $\hat a^\dagger_p$, and we write $\hat \phi(x^\mu)$ as just $\hat \phi$. Thus our field operator becomes:

{% math() %}
\hat \phi = \int \dfrac{d^3 p}{(2\pi)^3 2E} \left[\hat a_p e^{i\mathbf{p} \cdot \mathbf{x}} + \hat a^\dagger_p e^{-i\mathbf{p} \cdot \mathbf{x}}\right] 
{% end %}

Where we _define_ our raising and lowering operators such that:

{% math() %}
\begin{align*}
\hat a_p |n\rangle &= \sqrt{n}\,|n - 1\rangle \\
\hat a_p^\dagger|n\rangle &= \sqrt{n + 1}\,|n + 1\rangle
\end{align*}
{% end %}

Which is just like the quantum harmonic oscillator. We note that for the vacuum state $|0\rangle$, we have:

{% math() %}
\hat a_p|0\rangle = 0, \quad \hat a_p^\dagger|0\rangle = |1\rangle
{% end %}

The raising operator $\hat a_p$ raises the field to a higher-energy state, whereas the lowering operator $\hat a_p^\dagger$ acting on a state drops the field to a lower-energy state - in the case of the vacuum state, we end up with just zero. Let us now take an example of using the field operator $\hat \phi$. For instance, what happens if we act it on the ground state? Well, if we do the calculation, we find that:

{% math() %}
\begin{align*}
\hat \phi|0\rangle &= \int \dfrac{d^3 p}{(2\pi)^32E} \left[\hat a_p e^{i\mathbf{p} \cdot \mathbf{x}} + \hat a^\dagger_p e^{-i\mathbf{p} \cdot \mathbf{x}}\right] |0\rangle \\
% step 1
&= \int \dfrac{d^3 p}{(2\pi)^32E} \bigg[\underbrace{\hat a_p|0\rangle}_\text{distribute} e^{i\mathbf{p} \cdot \mathbf{x}} + \underbrace{\hat a^\dagger_p|0\rangle}_\text{distribute} e^{-i\mathbf{p} \cdot \mathbf{x}}\bigg] \\
% step 2
&= \int \dfrac{d^3 p}{(2\pi)^32E} \bigg[\underbrace{\cancel{\hat a_p|0}\rangle^0}_{\text{since } \hat a_p|0\rangle = 0 } e^{i\mathbf{p} \cdot \mathbf{x}} + \underbrace{|1\rangle e^{-i\mathbf{p} \cdot \mathbf{x}}}_{\text{since } \hat a_p^\dagger|0\rangle = |1\rangle}\bigg] \\
&= \int \dfrac{d^3 p}{(2\pi)^32E}|1\rangle \, e^{-i\mathbf{p} \cdot \mathbf{x}} \\
&= \int d^3 p\dfrac{e^{-i\mathbf{p} \cdot \mathbf{x}}}{(2\pi)^32E}|1\rangle
\end{align*}
{% end %}

So we've found that the field operator acting on the vacuum state $|0\rangle$ produces a **superposition** of the **first excited state** $|1\rangle$. The physical interpretation is that the field acting on $|0\rangle$ has _created_ a particle!

Let's break down what this means. An integral is just an infinite sum, so the integral over $p$ gives a superposition of the first excited state $|1\rangle$. It is a _superposition_ because when the field acts on the vacuum state $|0\rangle$ to produce the first excited state $|1\rangle$ (which we interpret as the field creating a particle), the resultant particle may have a range of different momenta, so we must sum over all possible momenta. This is a profound result: a quantum field can _create_ particles and (we'll soon see) _annihilate_ particles by acting on a state to produce another state.

Let's show our result even more explicitly by finding the _expectation value_ of the field for a single-particle excited state. We *define* a **single-particle state** with momentum $p$ (and thus energy $E = \sqrt{p^2 + m^2}$) as $|p\rangle$ where $|p\rangle$ is given by:

{% math() %}
|p\rangle = 2E\, \hat a_p^\dagger |0\rangle = 2E\,|1\rangle
{% end %}

If our physical interpretation is correct, then the single-particle state $|p\rangle$ represents a particle created by the field - and we'll show that this is true. Before we begin though, we also need to *define* our states to satisfy the following orthogonality relation:

{% math() %}
\langle p |p'\rangle = 2E (2\pi)^3 \delta^3(p-p')
{% end %}

Where $\delta^3$ is the three-dimensional Dirac delta function, which obeys $\displaystyle \int d^3 p\, \delta^3(p) = 1$, a fact that will be _extremely helpful_ later.

> **Why this particular orthogonality relation?** The answer is that however we choose to define orthogonality between two states, any scaling constants are **a matter of personal preference**. Here, we just chose the constant factor $(2\pi)^3$ because it is convenient for our later calculations, but it doesn't really matter. After all, we cannot measure quantum states (directly) anyways, so it really **does not matter** how we define them. As long as our definitions are **consistent** and our states are **normalized** (such that you can never have a probability greater than one!), we may choose whatever normalization constants we want.

To calculate the expectation value of the single-particle state $\langle 0 |\hat \phi| p\rangle$, we just "flip" our previous result for $\hat |0\rangle$ around to get:

{% math() %}
\langle 0| \hat \phi = \langle 1|\int d^3 p\dfrac{e^{-i\mathbf{p} \cdot \mathbf{x}}}{(2\pi)^32E}
{% end %}

Then, substituting in $|p\rangle = 2E\, \hat a_p^\dagger |0\rangle = 2E\,|1\rangle$, we have:

{% math() %}
\begin{align*}
\langle 0 |\hat \phi |p\rangle &= \langle 1|\int d^3 p\dfrac{e^{-i\mathbf{p} \cdot \mathbf{x}}}{(2\pi)^32E}|p\rangle \\
&= \langle 1|\int d^3 p\dfrac{e^{-i\mathbf{p} \cdot \mathbf{x}}}{(2\pi)^32E} \underbrace{2E\,|1\rangle}_{|p\rangle = 2E\,|1\rangle} \\
&= \int d^3 p \dfrac{e^{-i\mathbf{p} \cdot \mathbf{x}}}{(2\pi)^3} \underbrace{\langle 1|1\rangle}_\text{orthogonal} \\
&= \int d^3 p \dfrac{e^{-i\mathbf{p} \cdot \mathbf{x}}}{(2\pi)^3}(2\pi)^3 \delta^3(p - p') \\
&= \int d^3 p \underbrace{\left[e^{-i\mathbf{p} \cdot \mathbf{x}}\delta^3(p - p')\right]}_\text{Dirac delta integrates to 1} \\
&= e^{-i\mathbf{p} \cdot \mathbf{x}}
\end{align*}
{% end %}

So the expectation value of the field for the single-particle state is just $e^{-i\mathbf{p} \cdot \mathbf{x}}$, _exactly_ the same as the wavefunction of a single particle with momentum $\mathbf{p}$. Physically-speaking, we have thus shown that our quantum field $\hat \phi$ can _create_ particles, and this is why we often call $\hat a^\dagger_p$ the **creation operator**. Our field $\hat \phi$ can also _annihilate_ particles, and this is why we often call $\hat a_p$ the **annihilation operator**.

This means that, unlike non-relativistic quantum mechanics, where the particle (such as the electron) is the fundamental entity, in quantum field theory, the *field* is the fundamental entity, out of which particles arise and disappear - which is why quantum field theory is the basic theoretical framework for **particle physics**. Indeed, the free scalar field theory is a theory that can describe particles called [pions](https://en.wikipedia.org/wiki/Pion) (also called pi mesons), although not much else. We'll soon see more "interesting" (but also more complicated) theories that describe particles that are much more well-known, like photons, electrons, and quarks.

### Scattering and propagators

Relativistic QFT is most often used in the calculation of **scattering cross-sections** that describes what happens when elementary particles interact. To understand how this procedure works, let us consider a QFT with Hamiltonian $\hat H$. This Hamiltonian can be divided into two parts: the free Hamiltonian $\hat H_0$, and the _interaction_ Hamiltonian $\hat H_i$. Thus we have:

{% math() %}
\hat H = \hat H_0 + \hat H_i
{% end %}
