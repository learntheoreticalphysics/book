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

- Momentum ($p$) becomes the same thing as the wavevector ($k$), because in natural units where $\hbar = 1$ (which we're using), $p = \hbar k$ becomes $p = k$
- For photons, angular frequency $\omega$ and energy $E$ become equivalent, because in natural units where $c = 1$ (which we're using), $E = \hbar \omega$ becomes $E = \omega$
- Einstein's relativistic energy-momentum relation of $E^2 = (pc)^2 + (mc^2)^2$ becomes simply $E^2 = p^2 + m^2$, so we get $E = \sqrt{p^2 + m^2}$. You may also see this denoted as $E_p = \sqrt{p^2 + m^2}$, such as in Peskin and Schroeder's _An Introduction To Quantum Field Theory_. **This is the notation we'll use**.
	- Additionally (for photons/massless particles only), $E_p = p$, because (again) in natural units where $c = 1$ (which we're using), $E_p = pc$ becomes $E_p = p$

This means that every text often has its own notational system, especially if a certain text doesn't use natural units. Here, we will **always use natural units** unless otherwise denoted.

## Equations of motion of a free scalar field

The "simplest" quantum field theory is the theory of a free scalar field. We should note that "simple" is a rather relative term; approaching even this relatively simple quantum field theory can be an intimidating task, so it's important that we get the basics down.

Since the free scalar field theory is after all a _field theory_, we start with its field Lagrangian. In this case, the field Lagrangian of a free scalar field is given by:

{% math() %}
\mathscr{L} = \dfrac{1}{2} \partial_\mu \phi \partial^\mu \phi - \dfrac{1}{2} m^2 \phi^2
{% end %}

Using the Euler-Lagrange equations, we can find the equations of motion of the field $\phi$. For the free scalar field, the Euler-Lagrange equations take the form:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \phi} - \partial_\beta \left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta \phi)}\right) = 0
{% end %}

Let's now compute the partial derivatives. Let's start with the derivative with respect to $\phi$, which is relatively simple to find:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \phi} = -m^2 \phi
{% end %}

The derivative with respect to $\partial_\beta \phi$ is not as easy to find, so we'll show the steps below:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta \phi)}
&= \dfrac{1}{2}\dfrac{\partial}{\partial(\partial_\beta \phi)} \bigg(\partial_\mu \phi \partial^\mu \phi - m^2 \phi^2\bigg) \\
&= \dfrac{1}{2}\dfrac{\partial}{\partial(\partial_\beta \phi)} \bigg(\partial_\mu \phi \partial^\mu \phi\bigg) - \cancel{\dfrac{\partial}{\partial(\partial_\beta \phi)}\bigg(m^2 \phi^2\bigg)}^0 \\
&= \dfrac{1}{2}\dfrac{\partial}{\partial(\partial_\beta \phi)} \underbrace{\bigg(\partial_\beta \phi \partial^\beta \phi\bigg)}_\text{relabel dummy indices} \\
&= \dfrac{1}{2}\dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \underbrace{\eta^{\alpha \beta}\partial_\alpha \phi}_\text{lower indices}\bigg) \\
&= \dfrac{1}{2}\dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \eta^{\alpha \beta} \underbrace{\delta^\beta{}_\alpha \partial_\beta}_\text{relabel}  \phi\bigg) \\
&= \dfrac{1}{2}\eta^{\alpha \beta} \delta^\beta{}_\alpha\dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \partial_\beta \phi\bigg)
\end{align*}
{% end %}

Let's recap on the steps we've done so far. First, since the $m^2 \phi^2$ term doesn't depend on the derivatives of $\phi$, its partial derivative is zero. This leaves us with just the $\partial_\mu \phi \partial^\mu \phi$ term left. Since $\mu$ is repeated over the upper and lower indices, we know that it is a **dummy index** so we can relabel it whatever we want - here we chose $\mu \to \beta$ because we're differentiating with respect to $\beta$, because again, since it's a dummy index, $\partial_\mu \phi \partial^\mu \phi = \partial_\beta \phi \partial^\beta \phi$.

Finally, we needed to get the $\partial^\beta \phi$ term as a lower index. To do this, we used the Minkowski metric $\eta^{\alpha \beta}$ to lower the index, and then used the Kronecker delta {% inlmath() %}\delta^\beta{}_\alpha{% end %} to relabel. The end result we got was {% inlmath() %}\partial^\beta \phi = \eta^{\alpha \beta} \delta^\beta{}_\alpha \partial_\beta \phi{% end %}, from which we could pull out the (constant) factor of {% inlmath() %}\eta^{\alpha \beta} \delta^\beta{}_\alpha{% end %}. This gives us everything inside the derivative _purely_ in terms of {% inlmath() %}\partial_\beta \phi{% end %}, at which point we can _finally_ differentiate:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial (\partial_\beta \phi)} 
&= \dfrac{1}{2}\eta^{\alpha \beta} \delta^\beta{}_\alpha\dfrac{\partial}{\partial(\partial_\beta \phi)} 
\bigg(\partial_\beta \phi\, \partial_\beta \phi\bigg) \\
&= \dfrac{1}{2}\eta^{\alpha \beta} \delta^\beta{}_\alpha (2\partial_\beta \phi) \\
&= \dfrac{1}{2}\underbrace{2\eta^{\alpha \beta}\delta^\beta_\alpha \partial_\beta \phi}_\text{now contract indices} \\
&= \partial^\beta \phi
\end{align*}
{% end %}

Here, we took the derivative in the standard way (it is just taking the derivative of $(\partial_\beta \phi \partial_\beta \phi)^2$ which yields $2\partial_\beta \phi$). Then, we contracted the indices with the Minkowski metric and Kronecker delta terms, giving us $\eta^{\alpha \beta}\delta^\beta_\alpha \partial_\beta \phi = \partial^\beta \phi$. So, substituting into the Euler-Lagrange equations, we have:

{% math() %}
\begin{gather*}
-m^2 \phi - \partial_\beta(\partial^\beta \phi) = 0 \\
\Rightarrow \partial_\beta \partial^\beta \phi + m^2 \phi = 0
\end{gather*}
{% end %}

This is our **equation of motion** for our free scalar field, and it is called the **Klein-Gordon equation**, although it is usually written with the dummy index $\mu$ instead of $\beta$, in which it takes the form:

{% math() %}
\partial_\mu \partial^\mu \phi + m^2 \phi = 0
{% end %}

## Canonical quantization

Now is the time to take our _classical_ field $\phi$ and turn it into a quantum field, a process called **canonical quantization**. To start, we first need to solve the Klein-Gordon equation with a [Fourier decomposition](https://ese-msc.github.io/preinduction/edsml/primer/notebooks/c_mathematics/differential_equations/11_pde_fourier.html), which gives the general solution:

{% math() %}
\phi(x^\mu) = \int \dfrac{d^3 p}{(2\pi)^32E_p} \left[a(p) e^{ip_\mu x^\mu} + a^*(p) e^{-ip_\mu x^\mu}\right] 
{% end %}

Where $E_p = \sqrt{p^2 + m^2}$ comes from the energy-momentum relation, as we discussed earlier. We may promote this to a field if we make the identifications of $a \to \hat a$, $a^* \to a^\dagger$, which are the _creation and annihilation operators_ which generalize the raising and lowering operators we previously saw. Thus, our _quantum_ field $\hat \phi$ is now an operator:

{% math() %}
\hat \phi(x^\mu) = \int \dfrac{d^3 p}{(2\pi)^32E_p} \left[\hat a(p) e^{ip_\mu x^\mu} + \hat a^\dagger(p) e^{-ip_\mu x^\mu}\right] 
{% end %}

For mathematical convenience we write $\hat a(p)$ as $\hat a_p$ and $\hat a^\dagger(p)$ as $\hat a^\dagger_p$, and we write $\hat \phi(x^\mu)$ as just $\hat \phi$. Thus our field operator becomes:

{% math() %}
\hat \phi = \int \dfrac{d^3 p}{(2\pi)^3 2E_p} \left[\hat a_p e^{ip_\mu x^\mu} + \hat a^\dagger_p e^{-ip_\mu x^\mu}\right] 
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
\hat \phi|0\rangle &= \int \dfrac{d^3 p}{(2\pi)^32E_p} \left[\hat a_p e^{ip_\mu x^\mu} + \hat a^\dagger_p e^{-ip_\mu x^\mu}\right] |0\rangle \\
% step 1
&= \int \dfrac{d^3 p}{(2\pi)^32E_p} \bigg[\underbrace{\hat a_p|0\rangle}_\text{distribute} e^{ip_\mu x^\mu} + \underbrace{\hat a^\dagger_p|0\rangle}_\text{distribute} e^{-ip_\mu x^\mu}\bigg] \\
% step 2
&= \int \dfrac{d^3 p}{(2\pi)^32E_p} \bigg[\underbrace{\cancel{\hat a_p|0}\rangle^0}_{\text{since } \hat a_p|0\rangle = 0 } e^{ip_\mu x^\mu} + \underbrace{|1\rangle e^{-ip_\mu x^\mu}}_{\text{since } \hat a_p^\dagger|0\rangle = |1\rangle}\bigg] \\
&= \int \dfrac{d^3 p}{(2\pi)^32E_p}|1\rangle \, e^{-ip_\mu x^\mu} \\
&= \int d^3 p\dfrac{e^{-ip_\mu x^\mu}}{(2\pi)^32E_p}|1\rangle
\end{align*}
{% end %}

So we've found that the field operator acting on the vacuum state $|0\rangle$ produces a **superposition** of the **first excited state** $|1\rangle$. The physical interpretation is that the field acting on $|0\rangle$ has _created_ a particle!

Let's break down what this means. An integral is just an infinite sum, so the integral over $p$ gives a superposition of the first excited state $|1\rangle$. It is a _superposition_ because when the field acts on the vacuum state $|0\rangle$ to produce the first excited state $|1\rangle$ (which we interpret as the field creating a particle), the resultant particle may have a range of different momenta, so we must sum over all possible momenta. This is a profound result: a quantum field can _create_ particles and (we'll soon see) _annihilate_ particles by acting on a state to produce another state.

Let's show our result even more explicitly by finding the _expectation value_ of the field for a single-particle excited state. We *define* a **single-particle state** with momentum $p$ (and thus energy $E_p = \sqrt{p^2 + m^2}$) as $|p\rangle$ where $|p\rangle$ is given by:

{% math() %}
|p\rangle = 2E_p\, \hat a_p^\dagger |0\rangle = 2E_p\,|1\rangle
{% end %}

If our physical interpretation is correct, then the single-particle state $|p\rangle$ represents a particle created by the field - and we'll show that this is true. Before we begin though, we also need to *define* our states to satisfy the following orthogonality relation:

{% math() %}
\langle p |p'\rangle = 2E_p (2\pi)^3 \delta^3(p-p')
{% end %}

Where $\delta^3$ is the three-dimensional Dirac delta function, which obeys $\displaystyle \int d^3 p \delta^3(p) = 1$, a fact that will be _extremely helpful_ later.

> **Why this particular orthogonality relation?** The answer is that however we choose to define orthogonality between two states, any scaling constants are **a matter of personal preference**. Here, we just chose the constant factor $(2\pi)^3$ because it is convenient for our later calculations, but it doesn't really matter. After all, we cannot measure quantum states (directly) anyways, so it really **does not matter** how we define them. As long as our definitions are **consistent** and our states are **normalized** (such that you can never have a probability greater than one!), we may choose whatever normalization constants we want.

To calculate the expectation value of the single-particle state $\langle 0 |\hat \phi| p\rangle$, we just "flip" our previous result for $\hat \phi |0\rangle$ around to get:

{% math() %}
\langle 0| \hat \phi = \langle 1|\int d^3 p\dfrac{e^{-ip_\mu x^\mu}}{(2\pi)^32E_p}
{% end %}

Then, substituting in {% inlmath() %}|p\rangle = 2E_p\, \hat a_p^\dagger |0\rangle = 2E_p\,|1\rangle{% end %}, we have:

{% math() %}
\begin{align*}
\langle 0 |\hat \phi |p\rangle &= \langle 1|\int d^3 p\dfrac{e^{-ip_\mu x^\mu}}{(2\pi)^32E_p}|p\rangle \\
&= \langle 1|\int d^3 p\dfrac{e^{-ip_\mu x^\mu}}{(2\pi)^32E_p} \underbrace{2E_p\,|1\rangle}_{|p\rangle = 2E_p\,|1\rangle} \\
&= \int d^3 p \dfrac{e^{-ip_\mu x^\mu}}{(2\pi)^3} \underbrace{\langle 1|1\rangle}_\text{orthogonal} \\
&= \int d^3 p \dfrac{e^{-ip_\mu x^\mu}}{(2\pi)^3}(2\pi)^3 \delta^3(p - p') \\
&= \int d^3 p \underbrace{\left[e^{-ip_\mu x^\mu}\delta^3(p - p')\right]}_\text{Dirac delta integrates to 1} \\
&= e^{-ip_\mu x^\mu}
\end{align*}
{% end %}

So the expectation value of the field for the single-particle state is just $e^{-ip_\mu x^\mu}$, which describes a plane wave of a free particle with momentum $\small \mathbf{p}$! Note that since these plane wave solutions have exactly-known momentum, the Heisenberg uncertainty principle tells us that their position cannot be determined. We come to the conclusion that such a particle could be anywhere!

Physically-speaking, we have thus shown that our quantum field $\hat \phi$ can _create_ particles, and this is why we often call $\hat a^\dagger_p$ the **creation operator**. Our field $\hat \phi$ can also _annihilate_ particles, and this is why we often call $\hat a_p$ the **annihilation operator**. This means that, unlike non-relativistic quantum mechanics, where the particle (such as the electron) is the fundamental entity, in quantum field theory, the *field* is the fundamental entity, out of which particles arise and disappear - which is why quantum field theory is the basic theoretical framework for **particle physics**. Indeed, the free scalar field theory is a theory that can describe particles called [pions](https://en.wikipedia.org/wiki/Pion) (also called pi mesons), although not much else. We'll soon see more "interesting" (but also more complicated) theories that describe particles that are much more well-known, like photons, electrons, and quarks.

## The field Hamiltonian

Just like single-particle nonrelativistic quantum mechanics, quantum fields have an associated Hamiltonian. We can arrive at this quantum field Hamiltonian by starting with the classical field Hamiltonian (density). In classical field theory, the Hamiltonian density is defined as follows:

{% math() %}
\mathcal{H} = \Pi\,\partial_0\phi - \mathscr{L}
{% end %}

Where $\Pi$ (uppercase $\pi$) here is called the **canonical momentum density**, and is defined by:

{% math() %}
\Pi = \dfrac{\partial \mathscr{L}}{\partial (\partial_0 \phi)}
{% end %}

Note that $\partial_0 \phi$ is the **time derivative** of the field, since $\partial_0 = \partial_t$ in 4-dimensional spacetime. Recall that our Lagrangian for the free scalar field is given by:

{% math() %}
\mathscr{L} = \dfrac{1}{2}\partial_\mu \phi \partial^\mu \phi - \dfrac{1}{2}\dfrac{1}{2} m^2 \phi^2
{% end %}

Note that here, we have a summation over $\mu$, since $\mu$ is a dummy index. This means that we can expand it out as follows:

{% math() %}
\begin{align*}
\partial_\mu \phi \partial^\mu \phi &= 
\partial_0 \phi \partial^0 \phi
+ \underbrace{\partial_1 \phi \partial^1 \phi
+ \partial_2 \phi \partial^2 \phi
+ \partial_3 \phi \partial^3 \phi}_{\partial_i \phi \partial^i \phi} \\
&= \partial_0 \phi \partial^0 \phi + \partial_i \phi \partial^i \phi, \quad i = 1, 2, 3
\end{align*}
{% end %}

Notice what we did above: we expanded $\partial_\mu \phi \partial^\mu \phi$ according to the Einstein summation convention, which allowed us to split it into two portions: the spatial part $\partial_i \phi \partial^i \phi$, and the temporal part $\partial_0 \phi \partial^0 \phi$. This allows us to rewrite our Lagrangian as follows:

{% math() %}
\mathscr{L} = \dfrac{1}{2}\partial_0 \phi \partial^0 \phi - \dfrac{1}{2}\partial_i \phi \partial^i \phi - \dfrac{1}{2} m^2 \phi^2
{% end %}

> **Note:** The separation of the time and spatial parts of $\partial_\mu \phi \partial^\mu \phi$ gives us a way to write out the Lagrangian in the more familiar notation of vector calculus. In vector calculus notation this Lagrangian can equivalently be written $\mathscr{L} = \dfrac{1}{2} \left(\dfrac{\partial^2 \phi}{\partial t^2}\right)\phi^2 - \dfrac{1}{2}(\nabla \phi)^2 - \dfrac{1}{2} m^2 \phi^2$ (the minus sign is due to the Minkowski metric needed to lower $\partial^i$ to $\partial_i$ for the spatial components, since $\eta_{11}, \eta_{22}, \eta_{33} = -1$).

Now, we can find the canonical momentum. But before we do so, we need to first lower our indices, since we are differentiating with respect to the lower index, and we emphasize, we cannot _always_ assume that $\partial(\partial_0 \phi) = \partial(\partial^0 \phi)$ (though it will turn out that it is true in this case). Here, we use the Minkowski metric to lower indices (as usual), giving us $\partial^0 = \eta^{00}\partial_0$. Luckily for us, $\eta^{00} = \eta_{00} = 1$, so we (luckily!) have $\partial_0 = \partial^0$. Thus the first term in the Lagrangian becomes:

{% math() %}
\mathscr{L} = \dfrac{1}{2}(\partial_0 \phi)^2 - \dfrac{1}{2}\partial_i \phi \partial^i \phi - \dfrac{1}{2} m^2 \phi^2
{% end %}

Which we can differentiate to get $\Pi$:

{% math() %}
\begin{align*}
\Pi &= \dfrac{\partial \mathscr{L}}{\partial (\partial_0 \phi)} \\
&= \dfrac{\partial}{\partial (\partial_0 \phi)}\bigg[\dfrac{1}{2}(\partial_0 \phi)^2 - \cancel{\dfrac{1}{2}\partial_i \phi \partial^i \phi} - \cancel{\dfrac{1}{2} m^2 \phi^2}\bigg] \\
&= \dfrac{\partial}{\partial (\partial_0 \phi)}\bigg[\dfrac{1}{2}(\partial_0 \phi)^2 \bigg] \\
&= \partial_0 \phi
\end{align*}
{% end %}

> **Note:** Here, $\dfrac{\partial}{\partial(\partial_0 \phi)}(\partial_i \phi \partial^i \phi) = 0$ because the spatial ($\partial_i \phi \partial^i \phi$) and temporal ($\partial_0 \phi \partial^0 \phi$) components of $\partial_\mu \phi \partial^\mu \phi$ are **independent**.

Thus using the previous expression $\mathcal{H} = \Pi\,\partial_0\phi - \mathscr{L}$ that we found, and substituting our Lagrangian and canonical momentum that we just found, the Hamiltonian becomes:

{% math() %}
\begin{align*}
\mathcal{H} &= \Pi\,\partial_0\phi - \mathscr{L} \\
&= (\partial_0 \phi)(\partial_0 \phi) - \bigg[\dfrac{1}{2}(\partial_0 \phi)^2 - \dfrac{1}{2}\partial_i \phi \partial^i \phi - \dfrac{1}{2} m^2 \phi^2\bigg] \\
&= \dfrac{1}{2}(\partial_0 \phi)^2 + \dfrac{1}{2}\partial_i \phi \partial^i \phi - \dfrac{1}{2} m^2 \phi^2 \\
&= \dfrac{1}{2}\Pi^2 + \dfrac{1}{2}\partial_i \phi \partial^i \phi - \dfrac{1}{2} m^2 \phi^2
\end{align*}
{% end %}

To obtain the quantum Hamiltonian density, we need only find the quantum canonical momentum $\hat \Pi$, and substitute $\hat \phi$ and $\hat \Pi$ into our expression for the classical Hamiltonian density. From $\Pi = \partial_0 \phi$, it follows that $\hat \Pi = \partial_0 \hat \phi$. Recall that $\hat \phi$ is given by:

{% math() %}
\hat \phi = \int \dfrac{d^3 p}{(2\pi)^3 2E_p} \bigg[\hat a_p e^{ip_\mu x^\mu} + \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg]
{% end %}

Thus we have:

{% math() %}
\begin{align*}
\hat \Pi &= \partial_0 \hat \phi \\
&= \int \dfrac{d^3 p}{(2\pi)^32E_p} \bigg[\hat a_p \underbrace{\partial_0 e^{ip_\mu x^\mu}}_{ip_0e^{ip_\mu x^\mu}} + \hat a_p^\dagger\underbrace{\partial_0  e^{-ip_\mu x^\mu}}_{-ip_0e^{ip_\mu x^\mu}}\bigg] \\
&= \int \dfrac{d^3 p}{(2\pi)^32E_p} \underbrace{(ip_0)}_{p_0=E_p} \bigg[\hat a_p e^{ip_\mu x^\mu} - \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg] \\
&= \int \dfrac{d^3 p}{(2\pi)^32E_p} (iE_p) \bigg[\hat a_p e^{ip_\mu x^\mu} - \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg]
\end{align*}
{% end %}

Note that the reason $\partial_0 e^{ip_\mu x^\mu} = ip_0 e^{ip_\mu x^\mu}$ is that the momentum $\mathbf{p} = p^\mu = \langle p^0, p^1, p^2, p^3\rangle$ is a four-component vector, so when we differentiate it, we get $ip_0$ as a constant factor. The four components of $p^\mu$ are $p^\mu = \langle E_p, p_x, p_y, p_z$, which turned $ip_0$ to $iE_p$. Substituting our results for $\hat \phi$ and $\hat \Pi$ into our definition of $\hat{\mathcal{H}}$, where we substitute $\phi$ for $\hat \phi$ and $\Pi$ for $\hat \Pi$, we have:

{% math() %}
\begin{align*}
\hat{\mathcal{H}} &= \dfrac{1}{2}\hat\Pi^2 + \dfrac{1}{2} \underbrace{\partial_i \hat \phi \partial^i \hat \phi}_{-(\partial_i\hat \phi)^2} - \dfrac{1}{2} m^2 \hat \phi^2 \\
&= \dfrac{1}{2} \int \dfrac{d^3 p}{(2\pi)^32E_p} (iE_p) \bigg[\hat a_p e^{ip_\mu x^\mu} - \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg]\int \dfrac{d^3 p}{(2\pi)^32E_p} (iE_p) \bigg[\hat a_p e^{ip_\mu x^\mu} - \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg] \\ 
% step 2
&\qquad - \dfrac{1}{2}\left(\partial_i \int \dfrac{d^3 p}{(2\pi)^3 2E_p} \bigg[\hat a_p e^{ip_\mu x^\mu} + \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg]\right)^2 \\
&\qquad - \dfrac{1}{2}m^2 \int \dfrac{d^3 p}{(2\pi)^3 2E_p} \bigg[\hat a_p e^{ip_\mu x^\mu} + \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg] \int \dfrac{d^3 p}{(2\pi)^3 2E_p} \bigg[\hat a_p e^{ip_\mu x^\mu} + \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg] \\
% step 3
&= \dfrac{1}{2} \int \dfrac{d^6 p}{[(2\pi)^32E_p]^2} (iE_p) \bigg[\hat a_p e^{ip_\mu x^\mu} - \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg]  \bigg[\hat a_p e^{ip_\mu x^\mu} - \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg] \\ 
&\qquad - \dfrac{1}{2}\left(\partial_i \int \dfrac{d^3 p}{(2\pi)^3 2E_p} \bigg[\hat a_p e^{ip_\mu x^\mu} + \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg]\right)^2 \\
&\qquad - \dfrac{1}{2}m^2 \int \dfrac{d^6 p}{[(2\pi)^3 2E_p]^2} \bigg[\hat a_p e^{ip_\mu x^\mu} + \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg]\bigg[\hat a_p e^{ip_\mu x^\mu} + \hat a_p^\dagger e^{-ip_\mu x^\mu}\bigg] \\
% last step
&= \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)
\end{align*}
{% end %}

Let's walk through our steps. First, we substituted our respective expressions for $\hat \Pi$ and $\hat \phi$. We note that $\partial_i \hat \phi \partial^i \hat \phi = -(\partial_i \hat \phi)^2$, since $\partial^i = \eta^{ii} \partial_i$ and $\eta^{ii}$ (the spatial components of the Minkowski metric, that is, $\eta_{11}$, $\eta_{22}$, and $\eta_{33}$) are all equal to $-1$. Thus we have $\partial_i \hat \phi \partial^i \hat \phi = - \partial_i \hat \phi \partial_i \hat \phi = -(\partial_i \hat \phi)^2$. After that we have a lot of cancellations (we don't show the full calculations here for brevity), and since $e^{i\mathbf{p}\cdot \mathbf{x}}e^{-i\mathbf{p}\cdot \mathbf{x}} = 1$, everything simplifies down nicely and we have no complex exponentials in our fully-simplified answer. We have now obtained the _quantum_ Hamiltonian density:

{% math() %}
\hat{\mathcal{H}} = \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)
{% end %}

Here, we are very careful to use the notation $\hat{\mathcal{H}}$ instead of $\hat H$, since we are talking about the Hamiltonian _density_. The actual Hamiltonian operator would be the integral of the Hamiltonian over all space, that is:

{% math() %}
\hat H = \int d^3 x\,\hat{\mathcal{H}} = \dfrac{1}{2} \int \dfrac{d^3x\,d^3p E_p}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)
{% end %}

Note that this may look more familiar if we restore our conventional units by putting back the factors of $\hbar$, which means that $E_p = \hbar \omega_p$ and $p = \hbar k$ (so $dp = \hbar\, dk$). This gives us:

{% math() %}
\hat H = \int d^3 x \left[\dfrac{1}{2} \hbar \int d^3p \dfrac{\omega_p}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)\right]
{% end %}

If we then go from the continuous momentum distribution to a single momentum, we would have:

{% math() %}
\hat H = \int d^3 x \int \dfrac{1}{2} \hbar \omega_p (\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)
{% end %}

And finally, if we take the discrete limit of a quantum field, where instead of a continuous oscillating system across all space, we have a finite number of oscillators at specific locations, we obtain:

{% math() %}
\hat H = \sum_n\dfrac{1}{2} \hbar \omega_p (\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)
{% end %}

Which is just a system of a quantum harmonic oscillators! Indeed, a quantum field behaves much like a system of infinite harmonic oscillators, with one oscillator at every point in space.

The physical interpretation of the Hamiltonian (density) is much the same as it is in the quantum harmonic oscillator: given a state $|n\rangle$, the Hamiltonian (density) acting on the state, that is, $\hat H|n\rangle$, gives the energy of the state. If we act the Hamiltonian density on the vacuum state $|0\rangle$, we have:

{% math() %}
\begin{align*}
\hat{\mathcal{H}}|0\rangle &= \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)|0\rangle \\
&= \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)|0\rangle \\
&= \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3}(\cancel{\hat a^\dagger_p \hat a_p|0\rangle}^0 + \hat a_p \hat a^\dagger_p|0\rangle) \\
&= \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3}\hat a_p \hat a^\dagger_p|0\rangle
\end{align*}
{% end %}

Thus to find the _vacuum expectation energy_, we need only find $\langle 0 |\hat{\mathcal{H}}|0\rangle$, which gives us:

{% math() %}
\begin{align*}
\langle 0|\hat{\mathcal{H}}|0\rangle 
&= \langle 0|\int \dfrac{1}{2} \dfrac{d^3p\,E_p}{(2\pi)^3}\hat a_p \hat a^\dagger_p|0\rangle \\
&= \langle 0|\int \dfrac{1}{2} \dfrac{d^3p\,E_p}{(2\pi)^3}\hat a_p|1\rangle \\
&= \langle 0|\int \dfrac{1}{2} \dfrac{d^3p\,E_p}{(2\pi)^3}|0\rangle \\
&= \int \dfrac{1}{2} \dfrac{d^3p\,E_p}{(2\pi)^3}\langle 0|0\rangle \\
&= \dfrac{1}{2}\int \dfrac{dp^3}{(2\pi)^3}\sqrt{p^2 + m^2} \\
&= \infty
\end{align*}
{% end %}

This integral diverges rapidly to infinity, giving us an infinite energy, so clearly there must be something wrong! In the physics literature, there are several different _interpretations_:

1. An infinite ground-state energy doesn't really matter, since we can only measure energy _differences_ in energy, not absolute values of energy, so we might as well _define_ the ground-state energy to be zero
2. Our theory is not well-defined for all energies; it only holds up to a finite energy scale, and since $E_p = \sqrt{p^2 + m^2}$, there is an upper bound of the momenta we integrate over, rather than integrating over an infinite range of possible momenta.

The first answer is the more common one that most texts give, but it isn't _entirely correct_. This is because _gravity_ is affected by _any form_ of energy density, and in theory, this includes the vacuum energy of quantum fields. The second answer is the more physically-accurate one - even our best quantum field theories fail at extremely high energies, and finding a way to make them work at those energies is an active field of research. But for functional purposes, it suffices to simply ignore the second term of the Hamiltonian (density):

{% math() %}
\begin{align*}
\hat{\mathcal{H}} &= \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \cancel{\hat a_p \hat a^\dagger_p}) \\
&= \dfrac{1}{2} \int \dfrac{d^3p\,E_p}{(2\pi)^3} \hat a^\dagger_p \hat a_p
\end{align*}
{% end %}

This means that $\langle 0|\hat{\mathcal{H}}|0\rangle = 0$ (the ground-state energy of the vacuum state $|0\rangle$) is **zero**, so that now we are able to perform calculations without getting non-sensical answers of infinite energies.

## The vacuum energy, again

Let's take another look at the vacuum energy (ground-state energy) of a free scalar field. Recall how we stated that this ground-state energy is formally infinite, but this is because we assumed that our quantum field theory would be a valid theory up to infinitely-high energies: this is absolutely not the case! To represent this, we choose a "cutoff" energy, which can be expressed as an energy of $E = \Lambda$, where $\Lambda$ has the same units as the wavenumber $k$ (since $E = p$ and $p = k$ in natural units). We assume that our theory holds up to this energy. By making this modification, the ground-state energy $E_0$ in natural units is no longer infinite, but rather a finite value. We can compute this value by doing the integral for $E_0 = \langle 0|\hat{\mathcal{H}}|0\rangle$ explicitly:

{% math() %}
\begin{align*}
E_0 &= \int_0^\Lambda \dfrac{d^3 k}{(2\pi)^3} \dfrac{1}{2}\omega \\
&= \dfrac{1}{2}\int_0^\Lambda \dfrac{d^3 k}{(2\pi)^3} \sqrt{p^2 + m^2} \\
&= \dfrac{1}{2}\int_0^\Lambda \dfrac{d^3 k}{(2\pi)^3} \sqrt{k^2 + m^2}
\end{align*}
{% end %}

The exact analytical solution of the integral is given by:

{% math() %}
E_0 = \dfrac{\Lambda^2 m}{32\pi^3}\left(\Lambda \sqrt{m^2 + \left(\dfrac{\Lambda}{m}\right)^2} + m\, \text{arcsinh}\left(\dfrac{\Lambda}{m}\right)\right)
{% end %}

However, if we consider that the mass-energy of the particle $m$ is close to the cutoff $\Lambda$, which is the domain up to which most quantum field theories are well-defined and well-tested, we can make the approximation that $\Lambda \approx m$. Since $\text{arcsinh}(1) \approx 1$ and using the binomial approximation $\sqrt{1 + \alpha} \approx 1 + \frac{\alpha}{2}$, we have:

{% math() %}
E_0 \approx\dfrac{m^3}{32 \pi^3}\left(m\left(1+ \dfrac{m^2}{2}\right) +m\right)
{% end %}

> **Note for the advanced reader:** The approximation $\Lambda \approx m$ comes from setting the cutoff energy $\Lambda = \dfrac{2\pi}{\lambda}$ equal to the Compton wavelength $\lambda = 2\pi \hbar/mc$ (which is $\lambda = 2\pi/m$ in natural units). This is because energies around the Compton wavelength are the standard domain of quantum field theories, so it is well-suited to be a cutoff. We thus have $\Lambda = \dfrac{2\pi}{(2\pi/m)} = m$.

This result for the vacuum energy is no longer divergent, but rather has a well-defined value that is dependent on the mass of the particle modelled by the field. In the following chapters, we'll learn what particle this is, and actually _calculate_ this mass!

## Our next steps

Throughout this chapter, we've developed the quantum field theory of a _free_ scalar field. Free fields are, unfortunately, not very physically-realistic, since no particle-particles interactions occur in free fields. Quantum field theories that describe the _actual world_ are interacting field theories, where particles can scatter off each other, transferring energy and momentum in the process. We'll soon see that this gives rise to the _forces_ of nature, and see how this results in the production of _new particles_. Additionally, we'll discover powerful tools (and pretty diagrams!) to calculate these subatomic processes.
