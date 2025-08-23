+++
title = "The Yukawa theory of nuclear interactions"
date = 2025-08-24
+++

Up to this point, we have seen only one example of an interacting quantum field theory: $\phi^4$ theory, which we said was a basic, low-energy model of pions. We also derived the **Feynman rules** for $\phi^4$ theory, which allowed us to compute cross-sections with (relative) ease. "This all sounds nice and cool", you might say, "but so far we haven't seen any quantum field theories that actually describe realistic physics!" Indeed you would be right - $\phi^4$ theory is ultimately just a toy model, and the predictions from $\phi^4$ theory are rather lackluster in describing _real pions_. But the tools we developed in $\phi^4$ theory carry over to our first _physically-meaningful_ quantum field theory: **Yukawa's theory of the strong interaction**.

## The Yukawa Lagrangian

From the perspective of modern theoretical physics, the Yukawa theory is regarded as a primitive model for quantum electrodynamics, since it is relativistic but does not include the effects of spin. However, its first success came in describing the **strong nuclear force** between **nucleons** (protons and neutrons), for which it was extraordinarily successful. The Lagrangian of Yukawa theory can be written as:

{% math() %}
\mathscr{L} = \mathscr{L}_\text{real} + \mathscr{L}_\text{complex} + \mathscr{L}_\text{int}
{% end %}

Where {% inlmath() %}\mathscr{L}_\text{real}{% end %} is the Lagrangian for a free scalar field, {% inlmath() %}\mathscr{L}{% end %} is the Lagrangian for a complex scalar field, and {% inlmath() %}\mathscr{L}_\text{int}{% end %} is the interaction Lagrangian, also called the **Yukawa interaction** term. They are respectively given by:

{% math() %}
\begin{align*}
\mathscr{L}_\text{real} &= \dfrac{1}{2} \partial_\mu \phi \, \partial^\mu \phi - \dfrac{1}{2} m^2 \phi^2 \\
\mathscr{L}_\text{complex} &= \partial^\mu \psi \partial_\mu \overline\psi - M^2 \psi \overline \psi \\
\mathscr{L}_\text{int} &= - g \overline \psi \phi \psi
\end{align*}
{% end %}

The complete Lagrangian thus reads:

{% math() %}
\mathscr{L} = \dfrac{1}{2} \partial_\mu \phi \, \partial^\mu \phi +  \partial^\mu \psi \partial_\mu \overline\psi - \dfrac{1}{2} m^2 \phi^2 - M^2 \psi \overline \psi - g \overline \psi \phi \psi
{% end %}

This is the first example we've seen of a Lagrangian with _two_ different fields ($\psi$ and $\phi$) as well as the first with a complex-valued field ($\psi$). The equations of motion are therefore more complicated, and there are two of them: one for $\psi$ and one for $\phi$. It is helpful to first start with the equations of motion for $\phi$, since they are similar to those of the free scalar field, which we have seen before. The Euler Lagrange equation for $\phi$ is given by:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \phi} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \phi)}\right) = 0
{% end %}

By substituting {% inlmath() %}\mathscr{L} = \mathscr{L}_\text{real} + \mathscr{L}_\text{complex} + \mathscr{L}_\text{int}{% end %}, we have:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \phi} &= \dfrac{\partial}{\partial \phi}(\mathscr{L}_\text{real} + \mathscr{L}_\text{complex} + \mathscr{L}_\text{int}) \\
&= \dfrac{\partial \mathscr{L}_\text{real}}{\partial \phi} + \cancel{\dfrac{\partial \mathscr{L}_\text{complex}}{\partial \phi}}^0 + \dfrac{\partial \mathscr{L}_\text{int}}{\partial \phi} \\
\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \phi)} &= \dfrac{\partial}{\partial (\partial_\mu \phi)}(\mathscr{L}_\text{real} + \mathscr{L}_\text{complex} + \mathscr{L}_\text{int}) \\
&= \dfrac{\partial \mathscr{L}_\text{real}}{\partial (\partial_\mu \phi)} + \cancel{\dfrac{\partial \mathscr{L}_\text{complex}}{\partial (\partial_\mu \phi)}}^0 + \cancel{\dfrac{\partial \mathscr{L}_\text{int}}{\partial (\partial_\mu \phi)}}^0
\end{align*}
{% end %}

Where the partial derivative of {% inlmath() %}\mathscr{L}_\text{complex}{% end %} with respect to $\phi$ and $\partial_\mu \phi$ is zero since {% inlmath() %}\mathscr{L}_\text{complex}{% end %} does not depend on $\phi$ or $\partial_\mu \phi$; similarly, {% inlmath() %}\mathscr{L}_\text{int}{% end %} does not depend on derivatives of $\phi$, so the derivative of {% inlmath() %}\mathscr{L}_\text{int}{% end %} with respect to $\partial_\mu \phi$ is also zero. Now, {% inlmath() %}\mathscr{L}_\text{real}{% end %} is just the free scalar field Lagrangian that we saw in chapter 2, where we calculated that:

{% math() %}
\dfrac{\partial \mathscr{L}_\text{real}}{\partial (\partial_\mu \phi)} = \partial^\mu \phi, \quad \dfrac{\partial \mathscr{L}_\text{real}}{\partial \phi} = -m^2 \phi
{% end %}

The interaction term $\mathscr{L}_\text{int}$ is also straightforward to differentiate, giving us:

{% math() %}
\dfrac{\partial \mathscr{L}_\text{int}}{\partial \phi} = \dfrac{\partial}{\partial \phi}\left(- g \overline \psi \phi \psi\right) = -g \overline \psi \psi
{% end %}

Thus the derivatives of the Lagrangian with respect to $\phi$ and $\partial_\mu \phi$ are respectively given by:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \phi} &= -m^2 \phi - g \overline \psi \psi \\
\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\phi)} &= \partial^\mu \phi
\end{align*}
{% end %}

Thus, substituting our partial derivatives into the Euler-Lagrange equations, we get:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \phi} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \phi)}\right) &= -m^2 \phi - g\overline \psi \psi  -  \partial_\mu \partial^\mu \phi \\
&= 0
\end{align*}
{% end %}

We can algebraically clean this up a bit to recover the standard form of the equation of motion for $\phi$:

{% math() %}
(\partial_\mu \partial^\mu + m^2)\phi = -g |\psi|^2 \quad \Rightarrow \quad \square \phi = -g|\psi|^2
{% end %}

> **Note:** Here, remember that $|\psi|^2 = \overline \psi \psi$ and $\square \phi = \partial_\mu \partial^\mu \phi$. We will frequently use these simplifications when analyzing complex-valued fields.

The Euler Lagrange equation for the complex scalar field $\psi$ are unfortunately more complicated. A complex field still obeys the Euler-Lagrange equation, but it is important to remember that a complex field $\psi$ is technically just a convenient way of packaging two _real-valued fields_ $\psi_1, \psi_2$ together. That is:

{% math() %}
\begin{align*}
\psi &= \dfrac{1}{2}(\psi_1 + i \psi_2) \\
\overline \psi &= \frac{1}{2}(\psi_1 - i \psi_2)
\end{align*}
{% end %}

Thus, we actually have _two_ Euler-Lagrange equations, one for each real-valued field:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \psi_1} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_1)}\right) = 0 \\
\dfrac{\partial \mathscr{L}}{\partial \psi_2} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_2)}\right) = 0
\end{align*}
{% end %}

This is not just a mathematical abstraction: we will see once we discuss _quantum electrodynamics_ that it takes *two* real-valued fields $\psi_1, \psi_2$ to describe both _particles_ and _anti-particles_. However, it is mathematically convenient to package the two real-valued fields into a single complex-valued field $\psi = \frac{1}{2}(\psi_1 + i\psi_2)$. In that case, we can use a result from complex analysis (the [Cauchy-Riemann equations](https://en.wikipedia.org/wiki/Cauchy%E2%80%93Riemann_equations)) that says that for any function $f(z)$, where $z = x + i y$, we have:

{% math() %}
\dfrac{\partial f}{\partial \overline z} = \dfrac{1}{2} \left(\dfrac{\partial f}{\partial x} + i \dfrac{\partial f}{\partial y}\right)
{% end %}

Thus, if we make the substitutions $z \to \psi$, $f(z) \to \mathscr{L}(\psi)$, and $(x, y) \to \frac{1}{2}(\psi_1, \psi_2)$, the Cauchy-Riemann equations tell us that:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \overline \psi} = \dfrac{\partial \mathscr{L}}{\partial \psi_1} + i \dfrac{\partial \mathscr{L}}{\partial \psi_2}
{% end %}

And similarly, if we make the substitutions $(x, y) \to \frac{1}{2}(\partial_\mu \psi_1, \partial_\mu \psi_2)$, we find that:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \overline \psi)} = \dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_1)} + i\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_2)}
{% end %}

Combining the results together, we have:

{% math() %}
\begin{align*}
% line 1
\dfrac{\partial \mathscr{L}}{\partial \overline \psi} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \overline \psi)}\right) &= \left(\dfrac{\partial \mathscr{L}}{\partial \psi_1} + i \dfrac{\partial \mathscr{L}}{\partial \psi_2}\right) + \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_1)} + i\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_2)}\right) \\
% line 2
&= \left[\dfrac{\partial \mathscr{L}}{\partial \psi_1} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_1)}\right)\right] + i\left[\dfrac{\partial \mathscr{L}}{\partial \psi_2} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu\psi_2)}\right)\right] \\
&= 0
\end{align*}
{% end %}

Notice how this is just the (complex-valued) sum of the two separate Euler-Lagrange equations for $\psi_1$ and $\psi_2$! Thus, a convenient trick to quickly get the equations of motion for a complex-valued field $\psi$ rather than needing to first write it as a sum of two real-valued fields is to simply use the _modified_ Euler-Lagrange equation, which treats $\psi$ and $\overline \psi$ as _independent_ fields:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial \overline \psi} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \overline \psi)}\right) = 0
{% end %}

Remember that this is a _mathematical shortcut_ as opposed to any new physics; it tells us the _same information_ as the standard Euler-Lagrange equations for the individual fields $\psi_1$ and $\psi_2$. Upon taking the derivatives with respect to $\overline \psi$, we have:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \overline \psi} &= \cancel{\dfrac{\partial \mathscr{L}_\text{real}}{\partial \overline \psi}}^0 + \dfrac{\partial \mathscr{L}_\text{complex}}{\partial \overline \psi} + \dfrac{\partial \mathscr{L}_\text{int}}{\partial \overline \psi} \\
&= \dfrac{\partial}{\partial \overline \psi}(\partial^\mu \psi \partial_\mu \overline\psi - M^2 \psi \overline \psi - g \overline \psi \phi \psi) \\
&= -M^2 \psi - g \phi \psi
\end{align*}
{% end %}

Where the derivatives simplify upon recognizing that {% inlmath() %}\mathscr{L}_\text{real}{% end %} has no dependence on $\overline \psi$. Meanwhile, taking the derivatives with respect to $\partial_\mu \overline \psi$ gives us:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \overline \psi)} &= \cancel{\dfrac{\partial \mathscr{L}_\text{real}}{\partial (\partial_\mu \overline \psi)}}^0 + \dfrac{\partial \mathscr{L}_\text{complex}}{\partial (\partial_\mu \overline \psi)} + \cancel{\dfrac{\partial \mathscr{L}_\text{int}}{\partial (\partial_\mu \overline \psi)}}^0 \\
&= \dfrac{\partial}{\partial (\partial_\mu \overline \psi)} \bigg(\partial^\mu \psi \partial_\mu \overline \psi\bigg) = \partial^\mu \psi
\end{align*}
{% end %}

Where we find that {% inlmath() %}\mathscr{L}_\text{real}{% end %} and {% inlmath() %}\mathscr{L}_\text{int}{% end %} have no dependence on $\partial_\mu \overline \psi$, so their derivatives with respect to $\partial_\mu \overline \psi$ are also zero. Combining things together, we get the equation of motion for $\psi$:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial \phi} - \partial_\mu \left(\dfrac{\partial \mathscr{L}}{\partial (\partial_\mu \phi)}\right) &= -M^2 \psi - g \phi \psi - \partial_\mu (\partial^\mu \psi)\\
&= 0
\end{align*}
{% end %}

Simplifying gives us the standard form of the equation of motion for the $\psi$ field:

{% math() %}
(\partial_\mu \partial^\mu + M^2)\psi = -g\phi \psi 
{% end %}

We have thus found the equations of motion of both of our fields.

## Quantization and the Feynman rules

The quantization of the Yukawa theory is the same idea as other quantum field theories: we want to find the **field operators** $\hat \phi, \hat \psi$ that satisfy the _operator-valued_ versions of our equations of motion:

{% math() %}
\begin{align*}
(\partial_\mu \partial^\mu + m^2)\hat \phi &= -g |\hat \psi|^2 \\
(\partial_\mu \partial^\mu + M^2)\hat\psi &= -g \hat \phi \hat \psi 
\end{align*}
{% end %}

Therefore, we expand our fields in terms of creation and annihilation operators, where $\hat a, \hat a^\dagger$ are the creation and annihilation operators of the $\phi$ field, and $\hat b, \hat b^\dagger$ are the creation and annihilation operators of the $\psi$ field. We can write these as follows:

{% math() %}
\begin{align*}
\hat \phi(x) &= \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \left[\hat a_p e^{ipx} + \hat a^\dagger_p e^{-ipx}\right] \\
\hat \psi(x) &= \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \left[\hat b_p e^{ipx} + \hat c^\dagger_p e^{-ipx}\right] 
\end{align*}
{% end %}

> **Note:** As with the last chapter, $x$ is shorthand for $x^\mu$ and $px$ is shorthand for $p_\mu x^\mu$.

When we quantize the fields, we promote $\psi$ and $\phi$ to the field operators $\hat \psi$ and $\hat \phi$, meaning that the conjugate field $\overline \psi$ now becomes operator-valued as well, so we write it as $\hat \psi^\dagger$. It is given by:

{% math() %}
\hat \psi^\dagger(x) = \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \left[\hat b_p^\dagger e^{ipx} + \hat c_p e^{-ipx}\right]
{% end %}

Here is where we must take a more careful interpretation of our field operators. $\hat \phi$ is the same field operator as we have already seen for the real scalar field, and contains a single creation ($\hat a_p^\dagger$) and annihilation ($\hat a_p$) operator to create (or destroy) particles from the $\phi$ field. However, $\hat \psi$ and $\hat \psi^\dagger$ are both _complex-valued_, so we interpret them differently. Here, $(\hat b_p^\dagger, \hat b_p)$ are the creation and annihilation operators for **nucleons**, but $(\hat c_p^\dagger, \hat c_p)$ are the creation and annihilation operators for **anti-nucleons**. We have now taken our first glimpse of _antiparticles_ in quantum field theory! This gives us our following interpretation:

- $\hat \psi$ can create an anti-nucleon through $\hat c_p^\dagger$ or annihilate a nucleon through $\hat b_p$
- $\hat \psi^\dagger$ can create a nucleon through $\hat b_p^\dagger$ or annihilate an anti-nucleon through $\hat c_p$

It also allows us to figure out that when normal-ordered, the field products satisfy:

{% math() %}
:\hat \psi(x) \hat \psi(y): \quad = \quad :\hat \psi^\dagger(x) \hat \psi^\dagger(y): \quad = 0
{% end %}

To derive the Feynman rules for Yukawa theory, we use the same procedure as $\phi^4$ theory: we expand the S-matrix $\hat S$ as a series, giving us a probability amplitude:

{% math() %}
\mathcal{A} = \langle f |\hat S|i\rangle = \left \langle i\left| \bigg\{1 - i \int d^4 x \mathcal{T}\{\mathcal{H}(x)\} + \dfrac{(-i)^2}{2} \int d^4 x\, d^4y \mathcal{T}\{\mathcal{H}(x) \mathcal{H}(y)\} + \dots\bigg\}\right|f\right\rangle
{% end %}

The _interaction part_ of the field Hamiltonian is the part that interests us. We recall that (as long as the interaction Lagrangian contains no derivatives of fields) we have {% inlmath() %}\mathcal{H}_\text{int} = -\mathscr{L}_\text{int}{% end %}. Thus we have:

{% math() %}
\mathscr{L}_\text{int} = -g\overline \psi \phi \psi \quad \Rightarrow \quad \mathcal{H}_\text{int} = g\overline \psi \phi \psi
{% end %}

Thus we have:

{% math() %}
\hat H_\text{int} = \int d^3x\, \mathcal{H}_\text{int} = g\int d^3x\, \hat \psi^\dagger \hat \phi \hat \psi
{% end %}

In the case of the Yukawa theory, let us consider the scattering of two nucleons. We denote our initial state as $|p_1,p_2\rangle$ and our scattered state as $|q_1,q_2\rangle$ just as before, and we know that nucleons come from the $\psi$ field. We'll first examine the _second-order term_ in the probability amplitude, which is given by:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= \dfrac{(-i)^2}{2} \int d^4x\,d^4y\, \mathcal{T}\{\mathcal{H}(x)\mathcal{H}(y)\} \\ &= \dfrac{(-ig)^2}{2} \int d^4x\,d^4y\, \mathcal{T}\{\hat \psi^\dagger(x) \hat \phi(x) \hat \psi(x)\hat \psi^\dagger(y) \hat \phi(y) \hat \psi(y)\}
\end{align*}
{% end %}

To evaluate the time-ordered product of the field operators, we use a Wick expansion. Here, it is rather inconvenient that we need to deal with the time-ordered product of six field operators, but we can use the tricks we demonstrated in the last chapter to help us simplify things. Recall how Wick's theorem tells us that a time-ordered product of field operators can be written in the following form:

{% math() %}
\begin{align*}
\mathcal{T}(\hat \phi_1 \hat \phi_2 \hat \phi_3 \dots \hat \phi_n) &= ~:\hat \phi_1 \hat \phi_2 \hat \phi_3 \dots \hat \phi_n: + \text{Normal-ordered part} \\
&\qquad \quad+ \text{Pure contractions part}
\end{align*}
{% end %}

In addition, since we are considering six field operators, but a contraction can only involve two fields (that is, it must be the form $\overbracket{\hat \phi_a \hat \phi_b}$ or $\overbracket{\hat \psi_a \hat \psi_b}$), then the normal-ordered terms must involve $6 - 2 = 4$ normal-ordered field operators (as well as a contraction of the two remaining field operators). Thus we would get terms with normal-ordered products like $:\hat \phi(x) \hat \phi(y) \hat \psi(x) \hat \psi(y) : \overbracket{\hat \psi(x)^\dagger \psi(y)^\dagger}$ and $:\hat \psi(x) \hat \phi(x) \hat \psi^\dagger(y) \hat \phi(y) : \overbracket{\hat \psi^\dagger(x) \hat \psi(y)}$ in the normal-ordered part of the Wick expansion. However, the nucleons come from the $\psi$ field, not the $\phi$ field, so acting the $\hat \phi$ operator on the two-nucleon state $|p_1, p_2\rangle$ has no effect. This means that we can narrow our attention to only those terms that are made entirely of normal-ordered products of $\hat \psi$ and $\hat \psi^\dagger$ operators. More precisely, the terms we get to "play around" with are $\hat \psi(x)$, $\hat \psi^\dagger(x)$, $\hat \psi(y)$, and $\hat \psi^\dagger(y)$.

We can try arranging these in a variety of different ways, but remember that $\hat \psi$ annihilates a nucleon and creates an anti-nucleon, whereas $\hat \psi^\dagger$ creates a nucleon and annihilates an anti-nucleon. Thus, if we have two $\hat \psi^\dagger$'s on the right (that is, $\hat \psi^\dagger \hat \psi^\dagger$) we would create two anti-nucleons that would then be annihilated by the two $\hat \psi$'s on the left. The same goes if we have two $\hat \psi$'s on the right and two $\hat \psi^\dagger$'s on the left; the two $\hat \psi$'s would annihilate two nucleons, leaving our poor two-nucleon state with zero nucleons left! This rules out the possibility of the $\hat \psi (x) \hat \psi(x) \hat \psi^\dagger(y) \hat \psi^\dagger(y)$ and $\hat \psi^\dagger(x) \hat \psi^\dagger(x)\hat \psi (y) \hat \psi(y)$ terms. This gives us one option left: $\hat \psi^\dagger \hat \psi$ on the right _and_ the left. This combination makes sure that we end up with the same number of nucleons at the end (two of them), which we would expect for our final state $|q_1, q_2\rangle$. Expanding the term out in full gives:

{% math() %}
\text{Normal-ordered part} = \text{Copies of}~ : \hat \psi^\dagger(x) \hat \psi(x) \hat \psi^\dagger(y) \hat \psi(y) : \overbracket{\hat \phi(x) \hat \phi(y)}
{% end %}

Again, these results proceed from the fact that Wick's theorem lets us expand out a time-ordered product of field operators in terms of normal-ordered products and contractions, and normal-ordered products allow us to literally "read off" the number of particles created and annihilated. So we have Wick's theorem to thank for these simplifications! What's more, if we expand our our normal-ordered terms, we find that:

{% math() %}
\langle q_1, q_2, \dots q_n|: \hat \psi^\dagger(x) \hat \psi(x) \hat \psi^\dagger(y) \hat \psi(y) :|p_1, p_2, \dots p_n\rangle \to \int d^4 x\,e^{i(p_1 + p_2 + \dots)x}e^{-i(q_1 + q_2 + \dots)x}
{% end %}

We can infer this by noting that since the normal-ordered product $: \hat \psi^\dagger(x) \hat \psi(x) \hat \psi^\dagger(y) \hat \psi(y) :$ creates two particles (which we can represent by $e^{i(p_1 + p_2)x}$, since particles in QFT are represented by plane waves) and then annihilates two particles (which we can represent by $e^{-i(q_1 + q_2)x}$), the result is just a product of these plane waves for ingoing and outgoing particles. We have seen integrals of this form before - they just evaluate to Dirac deltas of the form:

{% math() %}
\begin{align*}
\langle q_1, q_2, \dots q_n|: \hat \psi^\dagger(x) \hat \psi(x) &\hat \psi^\dagger(y) \hat \psi(y) :|p_1, p_2, \dots p_n\rangle \\
&\to (2\pi)^4 \delta^4(p_1 + p_2 + \dots + p_n- q_1 - q_2 - \dots - q_n)
\end{align*}
{% end %}

Last, of course, we don't want to forget about the pure contractions part. Remember that contractions can only happen with the _same field_ evaluated at different spacetime positions. Thus, there are only two possibilities: the contraction $\overbracket{\hat \phi(x) \hat \phi(y)}$ and the contraction $\overbracket{\hat \psi(x) \hat \psi^\dagger(y)}$. It may not immediately be obvious why the $\overbracket{\hat \psi \hat \psi}$ and $\overbracket{\hat \psi^\dagger \hat \psi^\dagger}$ contractions are zero. An intuitive way to understand this is to remember that a contraction is equivalent to a _Feynman propagator_, which measures the probability for a particle created at $x$ to later be annihilated at $y$. However, $\overbracket{\hat \psi \hat \psi}$ and $\overbracket{\hat \psi^\dagger \hat \psi^\dagger}$ would essentially be measuring the probability for a particle (nucleon or anti-nucleon) to be twice-created or twice-annihilated, which does not match the creation-to-annihilation process that the Feynman propagator describes! Thus, we only have two contractions left, which are (as we mentioned) $\overbracket{\hat \phi(x) \hat \phi(y)}$ and $\overbracket{\hat \psi(x) \hat \psi^\dagger(y)}$. Since these are equivalently Feynman propagators, we will call them $D_{F}^{(\phi)}$ and $D_{F}^{(\psi)}$ to distinguish between them; they are given by:

{% math() %}
\begin{align*}
D_{F}^{(\phi)}(x-y) &= \overbracket{\hat \phi(x) \hat \phi(y)} = \int \dfrac{d^4 p}{(2\pi)^4} \dfrac{e^{-ip(x-y)}}{p^2 - m^2 + i \epsilon} \\
D_{F}^{(\psi)}(x-y) &= \overbracket{\hat \psi(x) \hat \psi^\dagger(y)} = \int \dfrac{d^4 p}{(2\pi)^4} \dfrac{e^{-ip(x-y)}}{p^2 - M^2 + i \epsilon}
\end{align*}
{% end %}

It is frequently more convenient to use the Fourier-transformed versions of the propagators (since they appear in the momentum-space Feynman rules, which are simpler but equivalent to the position-space Feynman rules). The momentum-space versions are respectively given by:

{% math() %}
\begin{align*}
\tilde D_{F}^{(\phi)}(x-y) &= \dfrac{i}{p^2 - m^2 + i \epsilon} \\
\tilde D_{F}^{(\psi)}(x-y) &= \dfrac{i}{p^2 - M^2 + i \epsilon}
\end{align*}
{% end %}

We now have all the ingredients we need to infer the Feynman rules for Yukawa theory!

### The Feynman rules of Yukawa theory

The momentum-space Feynman rules are remarkably similar to $\phi^4$ theory, though this is not necessarily surprising since both are theories of scalar fields. We state them below:

> **Feynman rules for Yukawa theory (momentum-space):**
> 
> 1. For each **incoming** particle with momentum $p$, draw an external line coming _into_ the diagram, and multiply by a factor of $1$.
> 2. For each **outgoing** particle with momentum $q$, draw an external line coming _out of_ the diagram, and multiply by a factor of $1$.
> 3. Whenever two or more lines meet, multiply by a factor of $-ig$. This corresponds to a **vertex**, represented by a dot on the Feynman diagram.
> 4. For each **virtual $\psi$ particle**, draw an internal line (either between two vertices, or a loop around a single vertex), and multiply by the propagator $\dfrac{i}{p^2 - M^2 + i\epsilon}$
> 5. For each **virtual $\phi$ particle**, draw an internal line (either between two vertices, or a loop around a single vertex), and multiply by the propagator $\dfrac{i}{p^2 - m^2 + i\epsilon}$
> 6. After combining all the multiplicative factors, integrate over $d^4 p$ **for each loop**. For instance, for a single loop, this would be $\displaystyle \int \dfrac{d^4 p}{(2\pi)^4}$, while for two loops, this would be $\displaystyle \int \dfrac{d^4 p_1}{(2\pi)^4} \dfrac{d^4 p_2}{(2\pi)^4}$.
> 7. Multiply by a Dirac delta $(2\pi)^4 \delta^4(\sum p_i - \sum q_i)$ to ensure conservation of momentum, where $\sum p_i$ is the sum of all momenta of all incident (real) particles and similarly $\sum q_i$ is the sum of all momenta of all outgoing (real) particles.
> 8. Divide by a symmetry factor $S$ dependent on the type of process.

## The Yukawa potential

Armed with the Feynman rules for Yukawa theory, we can now consider one of the most classical Feynman diagrams in quantum field theory: the diagram describing the interaction between two nucleons. We will consider the second-order process where two nucleons of momenta $p_1, p_2$ interact by the emission and absorption (often called an _exchange_) of a virtual pion. In this scenario, a nucleon with momentum $p_1$ emits a virtual pion with momentum $k$, and then scatters off with momentum $q_1$. Another nucleon with momentum $p_2$ then _absorbs_ the virtual pion and scatters off with momentum $q_1$. This process can be represented by the following Feynman diagram:

{{ diagram(src="../diagrams/yukawa-nuclear-potential.svg" desc="") }}

> **Note:** Be aware that this diagram, unlike the previous diagrams we've seen, reads from bottom to up. The incident particles $\psi(p_1), \psi(p_2)$ are at the **bottom** of the diagram, and the time axis is upwards, not rightwards! It is **very important** to follow the directions of the arrows to make sure you've read the diagram correctly.

We can now write down the S-matrix term corresponding to this diagram. Since we have two vertices, we need one factor of $(-ig)$ for each vertex. We'll also need Dirac deltas for all external lines (corresponding to incident and outgoing particles), which becomes $(2\pi)^4 \delta^4(p_1 + p_2 - q_1 - q_2)$. For our internal line (corresponding to the virtual pion $\phi$), we need the propagator for the $\phi$ field, which is given by $D_F^{(\phi)}$. In addition, to ensure momentum conservation, the momentum $k$ of the virtual pion must be equal to $q_1 - p_1$. This is because the virtual pion (despite being a _virtual particle_) carries real momentum and energy from the first nucleon and transfers it to the second. Thus, the momentum *lost* by the first nucleon after *emitting* the virtual pion must be the momentum *gained* by the second nucleon after *absorbing* the virtual pion. We thus have:

{% math() %}
k = q_1 - p_1 = q_2 - p_2
{% end %}

Combining our terms, we have:

{% math() %}
(-ig)^2(2\pi)^4 \times \delta^4(p_1 + p_2 - q_1 - q_2) \times \left[\dfrac{i}{k^2 - m^2 + i\epsilon}\right]
{% end %}

This result is the transition (probability) amplitude for our diagram! This time, however, we will not write a direct equality between $\mathcal{A}_{(2)}$ and our Feynman diagram-derived terms, since we know that this is just _one way_ that two-nucleon scattering can happen. Instead, we will write the amplitude as follows:

{% math() %}
\mathcal{A}_{(2)} \sim (-ig)^2(2\pi)^4 \delta^4(p_1 + p_2 - q_1 - q_2)  \left[\dfrac{i}{(q_1 - p_1)^2 - m^2 + i\epsilon}\right]
{% end %}

Using our convenient definition of $\tilde A_{(2)}$ which absorbs the factors of the Dirac delta, we have {% inlmath() %}i\mathcal{M} = \tilde{\mathcal{A}}_{(2)}{% end %}, where {% inlmath() %}\mathcal{A}_{(2)} = (2\pi)^4 \delta^4(\dots )\tilde{\mathcal{A}}_{(2)}{% end %}. This allows us to write down the **invariant amplitude** for the process:

{% math() %}
\begin{gather*}
i\mathcal{M} = (-ig)^2 \left[\dfrac{i}{(q_1 - p_1)^2 - m^2 + i\epsilon}\right] = \dfrac{-ig^2}{(q_1 - p_1)^2 - m^2 + i\epsilon} \\
\Rightarrow \mathcal{M} = \dfrac{-g^2}{(q_1 - p_1)^2 - m^2}
\end{gather*}
{% end %}

Where in the last line, we took the limit of $\epsilon \to 0$ (again, we always need to do so to recover a physical result). Interestingly enough, this calculation can also be done using non-relativistic quantum mechanics using the **Born approximation**. The Born approximation tells us that the invariant amplitude of a process in which a quantum particle scatters off a potential $V(r)$ (whether deflected or attracted), to lowest-order, is given by:

{% math() %}
i\mathcal{M} \sim -i\int d^3x\, V(\mathbf{r})e^{-i(\mathbf{p}_i-\mathbf{p}_f) \cdot \mathbf{r}}
{% end %}

Where we use natural units and $\mathbf{p}_i, \mathbf{p}_f$ are the initial and final (three-)momenta of the particle, respectively. (Technically, this is off by a few constants, but we can absorb this into $V(\mathbf{r})$ later, so it won't affect our calculations.) Of course, we know that non-relativistic quantum mechanics is only an _approximation_ to quantum field theory, but the Born approximation offers a link between a fundamentally QFT process (nucleon-nucleon scattering via virtual particle exchange) with a non-relativistic QM process (a particle scattering off a potential). By equating the QFT amplitude and the non-relativistic QM amplitude, we have, up to some constants:

{% math() %}
\begin{align*}
i\mathcal{M} &= -i\int d^3x\, V(\mathbf{r})e^{-i(\mathbf{p}_i-\mathbf{p}_f) \cdot \mathbf{r}} = \dfrac{-ig^2}{(q_1 - p_1)^2 - m^2}
\end{align*}
{% end %}

Up to this point, our QFT amplitude is fully relativistic, but since the Born approximation is non-relativistic, we want to take the non-relativistic limit of our QFT amplitude for the two to match. Remember that $q_1$ and $p_1$ (despite our "sloppy" notation) are actually **four-vectors**, given (in SI units) by:

{% math() %}
p_1 = \begin{pmatrix} E_1/c \\ p_{1x} \\ p_{1y} \\ p_{1z} \end{pmatrix} = \begin{pmatrix} E_1/c \\ \mathbf{p}_1 \end{pmatrix}, \quad
q_1 = \begin{pmatrix} E_1'/c \\ q_{1x} \\ q_{1y} \\ q_{1z} \end{pmatrix} = \begin{pmatrix} E_1'/c \\ \mathbf{q}_1 \end{pmatrix}
{% end %}

(The factor of $1/c$ in the zeroeth-component of $q_1$ and $p_1$ becomes evident only in SI units.) The dot product of two four-vectors always has a negative sign for the spatial components. Thus, if we expand $(q_1 - p_1)^2$, we have:

{% math() %}
(q_1 - p_1)^2 = \begin{pmatrix} (E_1'-E_1) /c \\ \mathbf{q}_1 - \mathbf{p}_1 \end{pmatrix}^2 = \dfrac{1}{c^2} (E_1' - E_1)^2 - (\mathbf{q}_1 - \mathbf{p}_1)^2
{% end %}

But if the particles are non-relativistic, then $(E_1' - E_1) / c^2 \approx 0$, since $c^2$ is such a large number compared to the energies of the non-relativistic particles. Thus, in the non-relativistic regime, we have:

{% math() %}
(q_1 - p_1)^2 \approx -(\mathbf{q}_1 - \mathbf{p}_1)^2
{% end %}

Thus, by substituting the above result into our QFT amplitude, as well as $(\mathbf{p}_i - \mathbf{p}_f) = (\mathbf{q}_1 - \mathbf{p}_1)$ into the Born approximation amplitude, we have:

{% math() %}
\begin{align*}
i\mathcal{M} =-i\int d^3x\, V(\mathbf{r})e^{-i(\mathbf{q}_1-\mathbf{p}_1) \cdot \mathbf{r}} &= \dfrac{-ig^2}{(q_1 - p_1)^2 - m^2} \\
&\approx \dfrac{-ig^2}{-(\mathbf{q}_1 - \mathbf{p}_1)^2 - m^2} \\
&= \dfrac{ig^2}{(\mathbf{q}_1 - \mathbf{p}_1)^2 + m^2}
\end{align*}
{% end %}

Finally, if we define $k^2 = (\mathbf{q}_1 - \mathbf{p}_1)^2$ and $\mathbf{k} = \mathbf{q}_1 - \mathbf{p}_1$ as the (three-)momentum transferred via the virtual pion, we get:

{% math() %}
\begin{align*}
-i\int d^3x\, V(\mathbf{r}) e^{-i\mathbf{k} \cdot \mathbf{r}} &= \dfrac{ig^2}{k^2 + m^2} \\
\Rightarrow \int d^3x\, V(\mathbf{r}) e^{-i\mathbf{k} \cdot \mathbf{r}} &= -\dfrac{g^2}{k^2 + m^2}
\end{align*}
{% end %}

We aim to solve for $V(\mathbf{r})$ to recover the approximate _classical potential_ that can model the same process in non-relativistic QM. By inverting this (more precisely, taking the inverse Fourier transform of both sides) and taking the limit $\epsilon \to 0$, we get:

{% math() %}
V(\mathbf{r}) = -g^2\int \dfrac{d^3 k}{(2\pi)^3} \dfrac{1}{k^2 + m^2}e^{i\mathbf{k} \cdot \mathbf{r}}
{% end %}

We will not solve this integral (although we'll learn how to solve integrals like this in the next chapter); instead, we'll only state that the solution is given by:

{% math() %}
V(\mathbf{r}) = -g^2 \dfrac{e^{-m|\mathbf{r}|}}{4\pi |\mathbf{r}|}
{% end %}

Rewriting this in a slightly sloppier notation, where $r = |\mathbf{r}|$, we have:

{% math() %}
V(r) = -g^2\dfrac{e^{-m r}}{4\pi r}
{% end %}

This is the **Yukawa potential**, and it is the _classical approximation_ to nucleon-nucleon scattering in quantum field theory. It tells us that quantum particles interacting in a classical potential is actually just an *approximation* for the more fundamental description of quantum field theory, where particles actually interact by virtual particle exchange and scattering. It is truly a remarkable result.

Furthermore, despite being an approximation, the Yukawa potential tells us a lot about how nucleons interact with each other. First, as long as $g^2 > 0$, the negative sign in front means that it is *always* an attractive potential, unlike the Coulomb potential for charged particles, which can be attractive _or_ repulsive. This tells us that it results in an attractive force that binds nucleons (protons and neutrons) to each other, successfully answering the question of how the positively-charged protons in the nucleus stay together. Second, we can use it to predict the _mass_ of the pion, and this was the result that arguably made Yukawa famous.

### Calculating the pion mass

The fact that we can calculate the pion's mass comes from the fact that the strong force rapidly decays with distance. In fact, if we compute the Yukawa potential at a distance $R = 1/m$, it evaluates to:

{% math() %}
\begin{align*}
V(R) &= -\dfrac{g^2}{4\pi} me^{-1} \\
&= -\dfrac{mg^2}{4\pi e} \\
&\approx 0
\end{align*}
{% end %}

The last step comes from the fact that $\frac{1}{4\pi e} \approx \frac{1}{34} \ll 1$ and we expect the pion's mass $m$ to be a very small number, so the expression reduces to effectively zero. Thus, we often say that $R = 1/m$ is the _range_ of the strong force: beyond this range, the strong force is far too weak to influence interactions between particles, and the electromagnetic force dominates.

In addition, we can rearrange this result for the mass of the pion, which becomes $m = 1/R$. If we restore appropriate factors of $c$ and $\hbar$ to convert to SI units, this becomes $m = \dfrac{\hbar}{Rc}$. In particle physics, where it is common to give mass in units of energy (since $m = E_0/c^2$; particle physicists just omit the $c^2$ factor and often say "particle $X$ has a mass of $Y$ MeV", where MeV = mega-electronvolts). So, we can use $E_0 = mc^2$ to get our result of:

{% math() %}
E_0 = mc^2 = \dfrac{\hbar c}{R}
{% end %}

Yukawa knew from previously-conducted experimental measurements that the strong force has a range of around $\pu{10^{-15} m}$, from which he was able to obtain a result of $E_0 \approx \pu{197 MeV}$. More modern measurements place the range of the strong force at closer to $\pu{1.5E-15 m}$, for which we get $E_0 \approx \pu{131.55 MeV}$, which agrees closely with the experimental value of $E_0 = \pu{139.57 MeV}$.

We should note that while we consider just a single scattering process (2 nucleons interacting through the exchange of a pion), in reality, this interaction happens over and over, with nucleons continuously exchanging pions, which is what we perceive as the effect of a potential that binds the nucleons together. Thus, the nucleons stay bound over time, rather than just an instant. Technically speaking, we're being a bit sloppy here: bound states (bound configurations of particles) are _non-perturbative_ in nature, given that the interaction no longer happens over short enough timescales to approximate it as a "small" perturbation from the free field. Thus our calculation, which was based on a pertubative approach, is not *technically* justified, although it is "good enough" to predict reasonably accurate results (as we saw from our calculation of the pion's mass).

> **Note:** The same techniques for calculating effective potentials are used in plasma physics and condensed-matter physics. It could be said that a potential is the physicist's way of abstracting any number of complicated interactions into a "simple" potential!

### Recovering the Coulomb potential

Before we conclude this section, there is one last insight the Yukawa potential can give us, but it is one very much worth discussing. If take the limit $m \to 0$ and substitute $g$ with the elementary charge constant $e$, we find that we recover the **Coulomb potential** from electromagnetic theory! Thus, we find that a force mediated by the exchange of massless particles (photons) rather than massive particles (pions) thus obeys **Coulomb's law**:

{% math() %}
\lim_{m \to 0} V_\text{Yukawa}(r) = -\frac{e^2}{4\pi r} = V_\text{Coulomb}(r)
{% end %}

It is remarkable that this result can be found from Yukawa theory without any mention of quantum electrodynamics. One could say that it vindicates Yukawa theory as describing the correct physics of nature and reproduces quantum electrodynamics in the low-energy limit. Indeed, if we assume that **gravity** is *also* mediated by massless particles (the hypothetical _graviton_) and has a coupling constant $g \propto \sqrt{GMm}$, then we recover the **gravitational potential**:

{% math() %}
V_\text{gravity} \sim -\dfrac{GMm}{r}
{% end %}

Before closing, we should note that Yukawa's theory, while groundbreaking for its time, is now understood to be the low-energy limit to the more fundamental theory of **quantum chromodynamics** in describing strong nuclear interactions between nucleons. However, that doesn't mean it's irrelevant in modern physics! This is because the type of coupling present in Yukawa's theory (in the form $\mathscr{L}_\text{int} \sim g\overline \psi \psi \phi$) appears over and over in numerous quantum field theories, including in the Standard Model. In fact, most of the interaction terms in the Standard Model Lagrangian use a Yukawa or Yukawa-like coupling! A knowledge of Yukawa theory will prepare us well for the much more complex quantum field theories to come.