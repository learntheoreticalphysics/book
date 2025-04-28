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

### Scattering and propagators

Relativistic QFT is most often used in the calculation of **scattering cross-sections** that describes what happens when elementary particles interact. To understand how this procedure works, let us consider a QFT with Hamiltonian $\hat H$. This Hamiltonian can be divided into two parts: the free Hamiltonian $\hat H_0$, and the _interaction_ Hamiltonian $\hat H_i$. Thus we have:

{% math() %}
\hat H = \hat H_0 + \hat H_i
{% end %}
