+++
title = "Introduction to Feynman diagrams"
date = 2025-08-24
+++

## Feynman diagrams

As we promised, in this chapter, we will now discuss how to actually _compute_ cross-sections and transition rates. For this, we'll need to learn another tool in the quantum field theorist's toolbox: **Feynman diagrams**. If you are math-queasy, you might find them a welcome sigh of relief from the relentless math of quantum field theory - drawing Feynman diagrams involves no math at all, just pretty pictures! For instance, you've already seen this Feynman diagram (describing a process called _Møller scattering_, we'll get to it later) at the start of this book:

{{ diagram(src="../diagrams/moller-scattering.svg" desc="") }}

Feynman diagrams are not just pretty pictures though: they are pictorial representations of terms in the S-matrix that allow us to calculate transition rates and scattering cross-sections. This makes doing scattering calculations much more straightforward: instead of needing to manually do loads of math, we can just draw a Feynman diagram according to the interaction process, translate it to the appropriate terms in the S-matrix, and we get our cross-sections!

### Remember: Feynman diagrams are not black magic!

We should prepend our previous enthusiasm with a caveat: Feynman diagrams only "work" _if_ the coupling constant $\lambda$ in the interaction Hamiltonian is relatively small. Why must this be the case? Well, if $\lambda$ is small, then the first few terms in the Dyson series are a good approximation to the total probability amplitude of scattering processes. We then say that the theory is _perturbative_, meaning that expanding the Dyson series to desired order in powers of $\lambda$ is a practical way of doing calculations. However, if $\lambda$ is large, then you would need far more than the first few terms in the Dyson series to gain a sufficiently-accurate approximation of the total probability amplitude. In fact, you would need effectively _infinite_ terms in the Dyson series, and thus, Feynman diagrams, which are built on terms in the Dyson series, become completely unusable. We then say that the theory is _non-perturbative_, and other methods (often numerical methods) are necessary to compute the correct probability amplitudes.

We'll soon see examples of both perturbative and non-perturbative quantum field theories.
**Quantum electrodynamics** (QED), perhaps the most famous of the quantum field theories of the Standard Model, is a perturbative quantum field theory. It has a very small coupling constant, meaning that Feynman diagrams have been able to make astonishingly precise calculations that have been experimentally verified to a very high degree of accuracy. **Quantum chromodynamics** (QCD), by contrast, is non-perturbative. Its coupling constant is variable, but grows quite large for low energies, so it is not well-described by Feynman diagrams in general.

However, in a larger sense, there isn't really a fine line separating perturbative and non-perturbative QFTs - for example, QED is expected to become non-perturbative at very high energy scales, a phenomenon we'll get to in the next few chapters, while QCD (surprisingly) becomes perturbative at high energy scales and short-ranged interactions (this is called asymptotic freedom). The point to understand is that Feynman diagrams only work since we happen to be lucky enough to have quantum field theories that behave "nicely" due to their small coupling constants. But enough talk! Let's delve straight into Feynman diagrams!

### Deriving Feynman rules for quartic theory

As we saw in the previous chapter, evaluating the terms in the S-matrix involves _long_ integrals for even basic processes. Deducing the right forms of those integrals and simplifying them until they become tractable is an extremely complicated task. Feynman's key contribution to quantum field theory is that he removed the need to write out the full expansion of the S-matrix terms when computing probability amplitudes. Instead, via an ingenious process of deduction, he could "read off" the correct terms by drawing a diagram, omitting the need to do needlessly-complicated math. To make things easier while getting started, we will not justify all our mathematical manipulations, aiming for better _understanding_ instead of better calculating.

> **Note:** If you're disatisfied with the handwaving, you can read ahead to the end of the chapter to see the mathematical justification.

It is helpful (for reasons we'll see soon) to write the field operator $\hat \phi(x)$ in terms of a sum of two operators, $\hat \phi_+$ and $\hat \phi_-$, which are defined as follows:

{% math() %}
\begin{align*}
\hat \phi_+(x) &= \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \hat a_p^\dagger e^{+ip_\mu x^\mu}, \\
\hat \phi_-(x) &= \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \hat a_p e^{-ip_\mu x^\mu}
\end{align*}
{% end %}

Here, we use $\hat \phi_+$ to denote the part of the field operator that _creates_ particles, while we use $\hat \phi_-$ to denote the part of the field operator that _annihilates_ particles. (Note that some texts may use different sign conventions.) The advantage of splitting the field operator into two is that $\hat \phi_+$ and $\hat \phi_-$ automatically obey the following identities:

{% math() %}
(\hat \phi_\pm)^\dagger = \hat \phi_\mp, \quad \hat \phi_-|0\rangle = \langle 0|\hat \phi_+= 0
{% end %}

> **Note:** This is because $\hat \phi_-$ contains only an annihilation operator ($\hat a_p$), and $\hat \phi_+$ only contains a creation operator ($\hat a^\dagger_p$); also remember from chapter 2 that $\langle n|\hat \phi = (\hat \phi |n\rangle)^\dagger$, which is how we know that $\hat \phi_+|0\rangle = \langle 0|\hat \phi_-$.

In addition, we will introduce a special function called the **Feynman propagator**, denoted $D_F(x-x)$, whose most general form is given by:

{% math() %}
D_F(x-y) = \lim_{\epsilon \to 0^+} \int \dfrac{d^4 p}{(2\pi)^4}\dfrac{ie^{-ip(x-y)}}{p^2 -m ^2 + i \epsilon}
{% end %}

To clean up the notation, it is common to not explicitly write out the limit $\lim_{\epsilon \to 0^+}$, with the understanding that it is implicitly there and we must take the limit $\epsilon \to 0$ after finishing our calculations. Thus in this condensed notation, we have:

{% math() %}
D_F(x-y) =\int \dfrac{d^4 p}{(2\pi)^4}\dfrac{ie^{-ip(x-y)}}{p^2 -m ^2 + i \epsilon}
{% end %}

Which, in the case of $x = y$, reduces to:

{% math() %}
D_F(x-x) = \int \dfrac{d^4 p}{(2\pi)^4}\dfrac{i}{p^2 -m ^2 + i \epsilon}
{% end %}

The Feynman propagator is very similar to the "plain" propagator $D(x - x')$ that we saw in the last chapter, and we can interpret it in pretty much the same way: it tells us that the probability amplitude that a particle originally known to be at position $y$ at some initial time is later found to be at position $x$ at some later time. However, the Feynman propagator modifies $D(x-x')$ to avoid some mathematical complications that lead to unphysical scenarios (for reasons we'll discuss later).

We now have the basic mathematical tools we need to start with an example calculation. Consider perhaps the simplest scattering process possible: we start with a particle that is created with some momentum (let's call it $p$) and ends up with some other momentum (let's call it $q$) when it is annihilated by the field. Recall that we define our single-particle states as $|p\rangle = \sqrt{2E_p} \hat a_p^\dagger|0\rangle$ - thus, our particle's initial and final states are given by:

{% math() %}
\begin{gather*}
|i\rangle = |p\rangle = \sqrt{2E_p} \hat a_p^\dagger |0\rangle \\
|f\rangle = |q\rangle = \sqrt{2E_q} \hat a_q^\dagger |0\rangle \\
\qquad \Rightarrow \langle f| = \sqrt{2E_1} \langle 0|\hat a_q
\end{gather*}
{% end %}

Where $E_p, E_q$ are the initial and final energies of the particle, and $\hat a_p^\dagger, \hat a_q$ respectively create the particle with initial momentum $p$ and annihilate it with final momentum $q$. Note that (as with previously) when we flip the ket $|f\rangle \to \langle f|$ we need to conjugate, so $\hat a^\dagger_q \to (\hat a^\dagger_q)^\dagger = \hat a_q$. Substituting in our initial states $|i\rangle, |f\rangle$, we have:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= \dfrac{-i\lambda}{4!} \int d^4 x \langle f| \mathcal{T}\{\hat \phi(x) \hat \phi(x) \hat \phi(x) \hat \phi(x)\}|i\rangle \\
&= \dfrac{-i\lambda}{4!} \int d^4 x \langle q| \mathcal{T}\{\hat \phi(x) \hat \phi(x) \hat \phi(x) \hat \phi(x)\}|p\rangle \\
\end{align*}
{% end %}

Here is where things start getting a bit more complicated, because the time-ordering operator is non-trivial and requires a technique known as a **Wick expansion** to be able to compute - something we'll learn to do later. For now, we will simply note that the Wick expansion evaluates to:

{% math() %}
\begin{align*}
\langle q|\mathcal{T}\{\hat \phi(x) \hat \phi(x) \hat \phi(x) \hat \phi(x)\}
&\to \langle q|\hat \phi_+(x) \hat \phi_+(x) \hat \phi_-(x) \hat \phi_-(x)|p\rangle \\ &\qquad+  6 \langle q| \hat \phi_+(x)\hat \phi_-(x)|p\rangle D_F(x -x)
\end{align*}
{% end %}

The above expansion is is not a _strict_ equality since it only applies in this particular case, which is why we use the arrow and not the equal sign. However, this is where using the $\hat \phi_+$ and $\hat \phi_-$ operators comes in handy. Noticing that since each $\hat \phi_-$ contains a single annihilation operator, and thus the combination $\hat \phi_- \hat \phi_-$ contains two, we learn that $\hat \phi_- \hat \phi_-|p\rangle = 0$ (since $|p\rangle = \sqrt{2E_p} \hat a_p^\dagger|0\rangle$, and $\hat a_p \hat a_p \sqrt{2E_p} \hat a^\dagger_p|0\rangle = 0$). This helps us rapidly ascertain that:

{% math() %}
\langle q|\hat \phi_+(x) \hat \phi_+(x) \hat \phi_-(x) \hat \phi_-(x)|p\rangle = \langle q|\hat \phi_+ \hat \phi_+ \underbrace{\left(\hat \phi_- \hat \phi_-|p\rangle\right)}_0 = 0
{% end %}

This lets us immediately clear out the first term in the expansion, leaving us with the two terms left. The next step is to compute $\langle q| \hat \phi_+(x) \hat \phi_-(x) |p\rangle$. By simply substituting in the definitions of $\hat \phi_-$ and $\hat \phi_+$, we have:

{% math() %}
\begin{align*}
\hat \phi_-|p\rangle &= \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \hat a_p e^{-ip_\mu x^\mu} |p\rangle, \\
\hat \phi_-|q\rangle &= \int \dfrac{d^3 q}{(2\pi)^3} \dfrac{1}{\sqrt{2E_q}} \hat a_q e^{-iq_\mu x^\mu} |q\rangle
\end{align*}
{% end %}

Now noting that $\langle q|\hat \phi_+ = (\phi_-|q\rangle)^\dagger$, we can calculate $\langle q|\hat \phi_+$ from our known result for $\hat \phi_-|q\rangle$:

{% math() %}
\langle q|\phi_+ = \langle 0|\int \dfrac{d^3 q}{(2\pi)^3} \dfrac{1}{\sqrt{2E_q}} \hat a_q^\dagger e^{iq_\mu x^\mu}
{% end %}

Doing these pre-simplifications allows us to compute $\langle q| \hat \phi_+(x) \hat \phi_-(x) |p\rangle$, as follows:

{% math() %}
\begin{align*}
\langle q| \hat \phi_+(x) \hat \phi_-(x) |p\rangle &= \langle q|\int \dfrac{d^3 q}{(2\pi)^3} \dfrac{1}{\sqrt{2E_q}} \hat a_q^\dagger e^{iq_\mu x^\mu}\int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \hat a_p e^{-ip_\mu x^\mu} |p\rangle \\
% second line
&= \langle q|\int \dfrac{d^3 p}{(2\pi)^3}\dfrac{d^3 q}{(2\pi)^3} \dfrac{1}{\sqrt{2E_q} \sqrt{2E_p}} \hat a_q^\dagger e^{iq_\mu x^\mu} \hat a_p e^{-ip_\mu x^\mu} |p\rangle \\
% third line
&= \langle q|\int \dfrac{d^3 p}{(2\pi)^3}\dfrac{d^3 q}{(2\pi)^3} \dfrac{1}{\sqrt{4E_pE_q}} e^{i(q_\mu - p_\mu) x^\mu}\hat a_q^\dagger \hat a_p |p\rangle
\end{align*}
{% end %}

Here is where we need to be quite delicate, since there are multiple simplifications possible but only one will lead to a sane (non-infinite) answer! First, we note the identity:

{% math() %}
\hat a^\dagger_q \hat a_p = (2\pi)^3 \delta(q-p)
{% end %}

Applying this identity allows us to turn a six-dimensional integral into a three-dimensional integral, and then evaluate the integral explicitly:

{% math() %}
\begin{align*}
\langle q|\int \dfrac{d^3 p}{(2\pi)^3}\dfrac{d^3 q}{(2\pi)^3} & \dfrac{1}{\sqrt{4E_pE_q}} e^{i(q_\mu - p_\mu) x^\mu}\hat a_q^\dagger \hat a_p |p\rangle \\
&= \langle q|\left[\int \dfrac{d^3 p}{(2\pi)^3} e^{i(q_\mu - p_\mu) x^\mu}\right]\int \dfrac{d^3 q}{\cancel{(2\pi)^3}}\dfrac{1}{\sqrt{4E_pE_q}}\cancel{(2\pi)^3}\delta^3(q-p)|p\rangle  \\
&= \langle q|\int \dfrac{d^3 p}{(2\pi)^3}\dfrac{e^{i(q_\mu - p_\mu)x^\mu}}{\sqrt{4E_pE_q}}\sqrt{2E_p}\hat a^\dagger_p|0\rangle \\
&=\underbrace{\sqrt{2E_q}\langle 0|\hat a_q}_{\langle q|} \int \dfrac{d^3 p}{(2\pi)^3}\dfrac{e^{i(q_\mu - p_\mu)x^\mu}}{\sqrt{4E_pE_q}}\sqrt{2E_p}\hat a^\dagger_p|0\rangle \\
&= \int \dfrac{d^3 p}{(2\pi)^3} e^{i(q_\mu - p_\mu)x^\mu} \langle 0|\hat a_q \hat a^\dagger_p|0\rangle \\
&= \int \dfrac{d^3 p}{\cancel{(2\pi)^3}} e^{i(q_\mu - p_\mu)x^\mu} \cancel{(2\pi)^3} \delta^3(q-p) \\
&= e^{-i(q_\mu - p_\mu)x^\mu} \\
&= e^{i(p_\mu - q_\mu)x^\mu}
\end{align*}
{% end %}

Thus, all of this math has led us to a wonderfully-elegant result:

{% math() %}
\langle q| \hat \phi_+(x) \hat \phi_-(x) |p\rangle = e^{i(p_\mu - q_\mu)x^\mu}
{% end %}

Now, substituting our expressions back into $\mathcal{A}_{(1)}$, we have:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= \dfrac{-i\lambda}{4!} \int d^4 x \langle q| \mathcal{T}\{\hat \phi(x) \hat \phi(x) \hat \phi(x) \hat \phi(x)\}|p\rangle \\
&= \dfrac{-i\lambda}{4!} \int d^4 x \bigg\{ \cancel{\langle q|\hat \phi_+(x) \hat \phi_+(x) \hat \phi_-(x) \hat \phi_-(x)|p\rangle}^0 \\ 
&\qquad \qquad+  6 \underbrace{\langle q| \hat \phi_+(x)\hat \phi_-(x)|p\rangle}_{e^{i(p_\mu - q_\mu)x^\mu}} D_F(x -x) \bigg\} \\
&= 6\left(\dfrac{-i\lambda}{4!}\right) \int d^4x \bigg\{ e^{i(p_\mu - q_\mu)x^\mu} D_F(x-x)\bigg\}
\end{align*}
{% end %}

Since $e^{i(p_\mu - q_mu)x^\mu}$ is rather messy, we replace it with the "sloppy" notation $e^{i(p-q)x}$ to be easier to read. With this updated notation $\mathcal{A}_(1)$ reads:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= 6\left(\dfrac{-i\lambda}{4!}\right) \int d^4x \bigg\{ e^{i(p-q)x} D_F(x-x)\bigg\} \\
&= \left(\dfrac{-i\lambda}{4}\right)\int d^4x \bigg\{ e^{i(p-q)x} D_F(x-x)\bigg\}
\end{align*}
{% end %}

Even after simplifications, this rather unwieldy expression is not exactly the easiest thing to understand! However, we notice that it contains several distinct terms that are often multiplied (or added) together:

- $-i\lambda$, which is multiplied by various constant factors
- Exponentials of the form $e^{\pm ipx}$ and $e^{\mp i qx}$
- The Feynman propagator $D_F(x - y)$, where here we have $x = y$

If we try to compute S-matrix terms for more complicated scattering scenarios (like multi-particle scattering and higher-order processes), we'll find the same repeated sums and products of these basic terms, suggesting that they have a fundamental importance to *any* interaction in $\phi^4$ theory. What if we could create a _systematic_ set of rules to be able to compute terms in the S-matrix based on these terms? This is the right idea, and in fact, it leads to the famous **Feynman rules**.

To understand the Feynman rules, we'll need two parts. The first part is to simplify the terms as much as possible. The second is to identify them with a particular _pictorial representation_ that lets us "read" the terms right off a picture. These two steps are what we'll do next!

#### Infering the Feynman rules for $\phi^4$ theory

As a brief review, after computing each of the terms that we found when expanding the S-matrix to first-order, we found several common repeated terms, like $e^{\pm ipx}$, $-i\lambda$, and $D_F(x-y)$. We can now finally assign an _interpretation_ to this collection of terms. 

Recall that the specific process we were interested in was as follows: a particle appears with momentum $p$, is detected at point $x$, and at some time later it is annihilated with momentum $q$. If we write out the total scattering (probability) amplitude $\mathcal{A}$ to first-order and substitute in our simplifications, we have:

{% math() %}
\begin{align*}
\mathcal{A} &= \mathcal{A}_{(0)} + \mathcal{A}_{(1)} \\
&= \langle q|p\rangle +\mathcal{A}_{(1)} \\
&= \langle q|p\rangle-\left(\dfrac{i\lambda}{4}\right)\int d^4x \bigg\{ e^{i(p-q)x} D_F(x-x)\bigg\}
\end{align*}
{% end %}

If we only consider the contribution from the _free field_, where $\mathcal{H}_I = 0$, then we are left with only the zeroeth-order term $\langle q|p\rangle$ from our normalization condition:

{% math() %}
\langle q|p\rangle = 2 E_p (2\pi)^3 \delta^3(p-q)
{% end %}

Our zeroeth-order scattering amplitude therefore reduces to:

{% math() %}
\mathcal{A}_{(0)} \propto \delta^3(q - p)
{% end %}

This is a rather boring result, since the scattering amplitude $\mathcal{A} = 0$ unless if $p = q$. This shouldn't be too unexpected though: it physically represents a particle that simply appears and disappears without interacting with anything. However, it does reveal an important aspect of Feynman rules: they must satisfy **conservation of momentum**. If the particle started off with momentum $p$ and did not interact with anything before it was annihilated with momentum $q$, the only possibility is that the particle's initial momentum $p$ is equal to its final momentum $q$. Otherwise, we would violate conservation of momentum! A way to visually represent our conclusions from analyzing the zeroeth-order term is to denote a particle with an arrow and label with its momentum. This is our first Feynman diagram:

{{ diagram(src="../diagrams/free-particle.svg" desc="") }}


The much more interesting part of the scattering amplitude is in the _first-order_ term $\mathcal{A}_{(1)}$. As a reminder, it is given by:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= \left(\dfrac{-i\lambda}{4}\right)\int d^4x \bigg\{ e^{i(p-q)x}  D_F(x-x)\bigg\} \\
&= \left(\dfrac{-i\lambda}{4}\right)\int d^4x \bigg\{ e^{i(p-q)x} \left[\int \dfrac{d^4 p}{(2\pi)^4}\dfrac{i}{p^2 -m ^2 + i \epsilon}\right]\bigg\}
\end{align*}
{% end %}

Notice how, unlike the zeroeth-order term, it also contains the $-i\lambda$ and Feynman propagator $D_F(x-x)$ terms. Since the Feynman propagator measures the probability amplitude for a particle to _propagate_ from $x$ to $y$, it must be the case that $D_F(x - x)$ measures the probability amplitude for the particle to stay in its place. You might think this would be zero, but not so fast: notice how the Feynman propagator integrates over _unconstrained_ momenta ($p = -\infty$ to $p = \infty$, though we usually omit the bounds). _Something_ happens to the particle to give it an extra boost of momentum, and this "something" is one of the most mysterious facets of quantum field theory. The precise meaning of what exactly this "something" is depends on who you ask:

- A physicist would answer that the particle emits a **virtual particle**, which it then re-absorbs, leading to a modification of its energy and momentum.
	- The Heisenberg uncertainty principle tells us that the total energy in quantum fields is uncertain, meaning that quantum fields have spontaneous energy fluctuations.
	- These fluctations, says the physicist, are short-lived excited states that allow _virtual_ particles to pop in and out of existence, which can then affect the energy (and thus momenta) of "real" particles.
	- A real particle that emits then absorbs a virtual particle would then gain its energy and thus momentum of that particle. This is known as the **self-energy** effect since the energy (apparently) seems to come from the particle itself! (Of course, it actually comes from the particle interacting with the quantum field)
- A philosopher would say that the idea of virtual particles is complete and utter nonsense, and that they are just convenient calculation devices for the fluctuations of the quantum vacuum. 
	- They would point out to the fact that there is no way to detect virtual particles, save for the effects they have on "real" particles, so calling them "particles" is too much imagination on the part of physicists.

> **Doesn't this violate conservation of momentum?** Not actually! We'll see later that the self-energy becomes absorbed in a particle's mass from something called **mass renormalization**, which causes the particle's measured mass to be different from its theoretical mass.

Regardless of whether they exist in physical reality or not, we will use the idea of virtual particles because that leads to the correct results in calculations, and leave the question of interpretation open for you to decide. With the idea of virtual particles, we understand the first-order term as arising from self-energy effects (the emission and re-absorption of a virtual particle by a real particle). We can then draw a diagram like this:

{{ diagram(src="../diagrams/quartic-one-loop.svg" desc="") }}

This tells us that an incident particle starts off with momentum $p$, then emits a virtual particle at some spacetime position $x$, which we represent with a dot on the diagram. This dot is more formally called a **vertex**; the loop attached to the vertex represents the emitted and re-absorbed virtual particle. Afterwards, the particle is annihilated with momentum $q$. Notice how our pictorial representation is able to tell us the same information as the long integral for $\mathcal{A}_{(1)}$! We are now able to state the **Feynman rules** we have discovered as a result of our Feynman-inspired reasoning:

> **Feynman rules for $\phi^4$ theory (position-space):**
> 
> 1. For each **incoming** particle with momentum $p$, draw a line coming _into_ the diagram, and multiply by a factor of $e^{ipx}$. This is called an **external line**, since it comes from "outside" the diagram and is not attached to anything on one end.
> 2. For each **outgoing** particle with momentum $q$, draw a line coming _out of_ the diagram, and multiply by a factor of $e^{-iqx}$. This is *also* an external line.
> 3. Whenever two or more lines meet, multiply by a factor of $-i\lambda$. This corresponds to a **vertex**, represented by a dot on the Feynman diagram.
> 4. For each **virtual particle**, draw a line that connects two vertices (or a loop around a single vertex), and multiply by the propagator $D_F(x-y)$. This is called an **internal line**, since it joins two vertices together (or, for $x = y$, loops around one vertex), and thus exists "inside" the diagram.
> 5. After combining all the multiplicative factors, integrate over spacetime for each vertex. For instance, for a single vertex $x$, this would be $\displaystyle \int d^4 x$, while for two vertices $(x,y)$ this would be $\displaystyle \int d^4x d^4y$.
> 6. Divide by a symmetry factor depending on the type of process (often, this factor is $2$, we'll learn later how to determine this factor).

We can summarize the basic features of Feynman diagrams, as follows:

| Feature on Feynman diagram | Appearance                                                  | Corresponds to...                     |
| -------------------------- | ----------------------------------------------------------- | ------------------------------------- |
| External line              | An open-ended line (not connected to anything on one end)   | Incident or scattered (real) particle |
| Vertex                     | A point at which two lines meet                             | Spacetime location of interaction     |
| Internal line              | Either a line joining two vertices or loop around one point | Virtual particle                      |

The position-space Feynman rules are called such because they require performing spacetime integrals over position (that is, integrals in the form $\displaystyle \int d^4 x$). Needing to perform such integrals is quite a hassle oftentimes. Luckily, there exists a simpler set of Feynman rules, and we can demonstrate how to find them by evaluating the first-order term $\mathcal{A}_{(1)}$ of our S-matrix expansion:

{% math() %}
\mathcal{A}_{(1)} =\left(\dfrac{-i\lambda}{4}\right)\int d^4x \bigg\{ e^{i(p-q)x} \left[\int \dfrac{d^4 p}{(2\pi)^4}\dfrac{i}{p^2 -m ^2 + i \epsilon}\right]\bigg\}
{% end %}

To evaluate it, we can use the identity $\displaystyle \int d^4 x e^{-ikx} = (2\pi)^4 \delta^4(k)$, which comes from the Fourier transform of a complex exponential. We'll also write out the Feynman propagators in explicit form. After simplifications, we get:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &=
% first line
\left(\dfrac{-i\lambda}{4}\right) \int d^4x\, e^{i(p - q)x} \left[\int \dfrac{d^4 p}{(2\pi)^4}\dfrac{i}{p^2 -m ^2 + i \epsilon}\right] \\
% second line
&= \left(\dfrac{-i\lambda}{4}\right) (2\pi)^4 \delta^4(q - p)\int \dfrac{d^4p}{(2 \pi)^4}\dfrac{i}{p^2 -m ^2 + i \epsilon} \\
&= \left(\dfrac{-i\lambda}{4}\right) (2\pi)^4 \delta^4(q - p)\int \dfrac{d^4p}{(2 \pi)^4}\dfrac{i}{p^2 -m ^2 + i \epsilon}
\end{align*}
{% end %}

We have thus eliminated all integrals over spacetime positions, and replaced them with delta functions $(2\pi)^4 \delta^4(q-p)$, which make sense since they are there to ensure conservation of momentum. By making similar replacements of $\displaystyle \int d^4 x~e^{i(p \pm q)x} \to (2\pi)^4 \delta(q \mp p)$, we now obtain the *momentum-space Feynman rules*, which are simplified (but equivalent) versions of the original position-space rules:

> **Feynman rules for $\phi^4$ theory (momentum-space):**
> 
> 1. For each **incoming** particle with momentum $p$, draw an external line coming _into_ the diagram, and multiply by a factor of $1$.
> 2. For each **outgoing** particle with momentum $q$, draw an external line coming _out of_ the diagram, and multiply by a factor of $1$.
> 3. Whenever two or more lines meet, multiply by a factor of $-i\lambda$. This corresponds to a **vertex**, represented by a dot on the Feynman diagram.
> 4. For each **virtual particle**, draw an internal line (either between two vertices, or a loop around a single vertex), and multiply by $\dfrac{i}{p^2 - m^2 + i\epsilon}$ (the Fourier transform of the Feynman propagator).
> 5. After combining all the multiplicative factors, integrate over $d^4 p$ **for each loop**. For instance, for a single loop, this would be $\displaystyle \int \dfrac{d^4 p}{(2\pi)^4}$, while for two loops, this would be $\displaystyle \int \dfrac{d^4 p_1}{(2\pi)^4} \dfrac{d^4 p_2}{(2\pi)^4}$.
> 6. Multiply by a Dirac delta $(2\pi)^4 \delta^4(\sum p_i - \sum q_i)$ to ensure conservation of momentum, where $\sum p_i$ is the sum of all momenta of all incident (real) particles and similarly $\sum q_i$ is the sum of all momenta of all outgoing (real) particles.
> 7. Divide by a symmetry factor depending on the type of process (often this factor is $2$).

> **Tip:** The number of vertices in a diagram represents the **order** of the process. For instance, a first-order process (corresponding to the {% inlmath() %}\mathcal{A}_{(1)}{% end %} term) has one vertex, a second-order process (corresponding to the {% inlmath() %}\mathcal{A}_{(2)}{% end %} term) has two, a third-order process has three, and so on.

## Basic cross-sections with Feynman diagrams

Having talked about the theory behind Feynman diagrams, let's see how to evaluate them in practice. We will consider three different (and progressively more difficult) Feynman diagrams, each of which represents a specific physical process.

The first process is the case of two-particle scattering. Imagine two incident scalar particles (let's call them _pions_ because they can roughly be described by $\phi^4$ theory) of momenta $p_1$ and $p_2$ that scatter off each other, forming two new pions of momenta $q_1$ and $q_2$. We can denote our initial two-pion state as $|p_1, p_2\rangle$ and our scattered two-pion state as $|q_1, q_2\rangle$. Let us now calculate the cross-section of this process.

The first step, of course, is to draw a corresponding Feynman diagram. Since we have two incident particles, we will need two external lines that come _into_ the diagram; and since we also have two outgoing particles, we will need two external lines that come _out of_ the diagram. Whenever two (or more) lines meet, we need to put a vertex. Since we have no virtual particles, we don't need to add any internal lines. Thus, our Feynman diagram would look like this:

{{ diagram(src="../diagrams/two-pion-vertex.svg" desc="") }}

Now, we'll use our momentum-space Feynman rules. Each incoming particle and each outgoing particle contributes a multiplicative factor of $1$, and the vertex contributes a factor of $-i\lambda$. We don't need to add any Feynman propagators since we have no virtual particles. Lastly, since our particles have incident momenta $p_1, p_2$ and outgoing momenta $q_1, q_2$, we need to add a momentum-conserving delta function of the form $(2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)$. As we have a single vertex, we identify our Feynman diagram as representing the $\mathcal{A}_{(1)}$ term in the transition (probability) amplitude. Putting it all together, we have:

{% math() %}
\begin{align*}
\mathcal{A}_{(1)} &= 1 \times 1 \times (-i\lambda) \times (2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2) \times 1 \times 1 \\
&= -i\lambda (2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)
\end{align*}
{% end %}

> **Note:** It should be noted that technically speaking, this Feynman diagram is not directly equal to {% inlmath() %}\mathcal{A}_{(1)}{% end %}, since there are multiple first-order processes possible for two-pion scattering and it is the **sum** of the amplitudes of each process that is equal to {% inlmath() %}\mathcal{A}_{(1)}{% end %}. For the purposes of our discussion, however, we will initially assume that this particular Feynman diagram is the dominant contribution to $\mathcal{A}_{(1)}$.

Thus, with our result for $\mathcal{A}_{(1)}$, the full transition amplitude (to first-order) is given by:

{% math() %}
\begin{align*}
\mathcal{A} &= \mathcal{A}_{(0)} + \mathcal{A}_{(1)} \\
&= \underbrace{\langle p_1,p_2|q_1,q_2\rangle}_{\langle f|i\rangle} 
-i\lambda (2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)
\end{align*}
{% end %}

Now recall that the scattering cross-section is defined *not* in terms of the probability amplitude $\mathcal{A}$ but rather in terms of the **invariant amplitude** $\mathcal{M}$, which is related to $\mathcal{A}$ by:

{% math() %}
\begin{align*}
\mathcal{A} &= \langle f|i\rangle + i\mathcal{M}(2\pi)^4\delta^4\left(\sum_j p_j - \sum_j q_j\right) \\
&= \langle p_1,p_2|q_1,q_2\rangle + i\mathcal{M}(2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)
\end{align*}
{% end %}

By comparing terms, we find that $\mathcal{M} = -\lambda$. Now, since we are considering two-pion scattering, where our incident and scattered particles are of the same type, they must be of equal masses. Therefore, we can use the formula for differential cross-sections of identical-mass particles, we have:

{% math() %}
\dfrac{d\sigma}{d\Omega} = \dfrac{1}{64\pi^2 E_\mathrm{cm}^2}  |\mathcal{M}|^2 = \frac{\lambda^2}{64 \pi^2 E_\mathrm{cm}^2}
{% end %}

Before we can proceed further, we should note that (for reasons we'll soon see) the theoretical value for the coupling constant $\lambda$ is actually formally infinite! Instead, we must make the replacement $\lambda \to \lambda_R$, where $\lambda_R$ is the _real coupling constant_ based on experimental measurement. From experiments with pions, we know that $\lambda_R \approx 328.7$ (to lowest-order)[^1]. Making this replacement gives:

{% math() %}
\dfrac{d\sigma}{d\Omega} =  \frac{\lambda_R^2}{64 \pi^2 E_\mathrm{cm}^2}
{% end %}

Since this differential cross-section is a constant, finding the _total_ cross-section $\sigma$ is just integrating a constant, leading to a straightforward integral:

{% math() %}
\begin{align*}
\sigma &= \int_0^{2\pi} d\phi \int_0^\pi d\theta\sin \theta \left(\dfrac{d\sigma}{d\Omega}\right) \\
&= \left(\dfrac{d\sigma}{d\Omega}\right)\underbrace{\int_0^{2\pi} d\phi \int_0^\pi d\theta\sin \theta}_{4\pi} \\
&= \left(\dfrac{d\sigma}{d\Omega}\right)(4\pi) \\
&= \frac{\lambda_R^2}{16 \pi E_\mathrm{cm}^2}
\end{align*}
{% end %}

This is _almost_ the correct answer; the correct result, when taking into account the properties of pions, is twice this value:

{% math() %}
\sigma = \frac{\lambda_R^2}{32 \pi E_\mathrm{cm}^2}
{% end %}

Still, the Feynman rules got us most of the way there, and gave us the correct differential cross-section, all without needing to compute lengthy integrals in the S-matrix expansion! The introduction of Feynman diagrams was crucial to the development of quantum field theory for _precisely_ this reason: it made it possible to quickly compute cross-sections for a variety of processes that were previously extremely tedious to calculate. As physicist and Nobel Prize winner Julian Schwinger said:

> "Like the silicon chip of more recent years, the Feynman diagram was bringing computation to the masses."

The second process is a more complicated case. Consider the two-pion scattering process again, except this time their collision forms a virtual particle (virtual pion) which then instantly decays into two real particles. This means that we now need to consider a Feynman diagram with an internal line. And since we now have two vertices, the process is _second-order_, and we will be computing (a major part of) the $\mathcal{A}_{(2)}$ term. To draw the diagram, we proceed as before with two incoming and two outgoing external lines. However, each pair meets at a _different_ vertex, and the two vertices are connected by an **internal line** that represents the virtual particle. Our diagram thus looks like this:

{{ diagram(src="../diagrams/two-pion-tree-level.svg" desc="") }}

Luckily, the Feynman rules make writing down the amplitudes relatively straightforward. We have a factor of $-i\lambda$ for each vertex, and a total of two vertices, thus giving a factor of $(-i\lambda)^2$. In addition, we have an internal line, giving us a a factor of $\dfrac{i}{k^2 - m^2 + i\epsilon}$ (from the propagator). Here, $k = p_1 + p_2$, since momentum must be conserved at every vertex. We also have a delta function term $(2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)$ to ensure conservation of momentum for all real particles. Thus, our total amplitude is given by:

{% math() %}
\begin{align*}
\mathcal{A}_{(2)} &= (-i\lambda)^2 (2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)\left(\dfrac{i}{k^2 - m^2 + i\epsilon}\right) \\
&= (2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)\left(\dfrac{-i\lambda^2}{k^2 - m^2 + i\epsilon}\right)
\end{align*}
{% end %}

If we'll ignore the first-order term {% inlmath() %}\mathcal{A}_{(1)}{% end %} for now and add it back in later, we have {% inlmath() %}\mathcal{A} \approx \langle f|i\rangle + \mathcal{A}_{(2)}{% end %}, where {% inlmath() %}\langle p_1,p_2|q_1,q_2\rangle{% end %}. Again, by comparing with the expression for $\mathcal{A}$ in terms of $\mathcal{M}$, we find that:

{% math() %}\begin{align*}
\mathcal{A} &= \langle f|i\rangle + i\mathcal{M}(2\pi)^4\delta^4\left(\sum_j p_j - \sum_j q_j\right) \\
&= \langle p_1,p_2|q_1,q_2\rangle + i\mathcal{M}(2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2) \\
&= \langle p_1,p_2|q_1,q_2\rangle +(2\pi)^4 \delta^4 (p_1 + p_2 - q_1 - q_2)\left(\dfrac{-i\lambda^2}{k^2 - m^2 + i\epsilon}\right) \\
&\Rightarrow \mathcal{M} = \dfrac{\lambda^2}{k^2 - m^2+ i \epsilon}
\end{align*}
{% end %}

We can now make a few simplifications before we calculate the cross-section. It is conventional to define a new variable $s = k^2 = (p_1 + p_2)^2$. Also, we remember that physical cross-sections require taking the limit of $\epsilon \to 0$, so we have:

{% math() %}
\mathcal{M} = \lim_{\epsilon \to 0}\dfrac{\lambda^2}{s - m^2 + i \epsilon} =\dfrac{\lambda^2}{s - m^2}
{% end %}

Plugging everything into the differential cross-section formula and again making the replacement $\lambda \to \lambda_R$ as before yields:

{% math() %}
\dfrac{d\sigma}{d\Omega} = \dfrac{1}{64\pi^2 E_\mathrm{cm}^2}  |\mathcal{M}|^2 = \frac{\lambda_R^4}{64 \pi^2 E_\mathrm{cm}^2} \dfrac{1}{(s-m^2)^2}
{% end %}

We may now use a very convenient simplification: we claim that the total energy in the center-of-mass frame, $E_\mathrm{cm}$, is equal to $s$. Why is this the case? Well, remember that $p_1$ and $p_2$ are actually _four-vectors_, given by:

{% math() %}
p_1 = \begin{pmatrix}
E_1 \\ p_{1x} \\ p_{1y} \\ p_{1z}
\end{pmatrix} = \begin{pmatrix}
E_1 \\ \mathbf{p}_1
\end{pmatrix}, \quad
p_2 = \begin{pmatrix}
E_2 \\ p_{2x} \\ p_{2y} \\ p_{2z}
\end{pmatrix} = \begin{pmatrix}
E_2 \\ \mathbf{p}_2
\end{pmatrix}
{% end %}

Where here we use the bolded momenta {% inlmath() %}\mathbf{p}_1, \mathbf{p}_2{% end %} to represent the three-momentum {% inlmath() %}\mathbf{p} = \langle p_x, p_y, p_z \rangle{% end %}. Recall that the dot product of two four-vectors $p^\mu, p^\nu$ is given by $\eta_{\mu \nu} p^\mu p^\nu$, where $\eta_{\mu \nu}$ (the Minkowski metric) contributes a minus sign to the spatial components. Thus, if we explicitly compute $s$, we have:

{% math() %}
s = (p_1 + p_2)^2 = \eta_{\mu \nu} \begin{pmatrix}
E_1 + E_2 \\
\mathbf{p}_1 + \mathbf{p}_2
\end{pmatrix}^2  = (E_1 + E_2)^2 - (\mathbf{p}_1 + \mathbf{p}_2)^2
{% end %}

Where $\eta_{\mu \nu}$ is the Minkowski metric and $(\mathbf{p}_1 + \mathbf{p}_2)^2$ is a shorthand for $(\mathbf{p}_1 + \mathbf{p}_2) \cdot (\mathbf{p}_1 + \mathbf{p}_2)$. However, the **center-of-momentum frame** is _defined_ to be the reference frame in which the total momentum of the system is zero (in other words, $\mathbf{p}_1 + \mathbf{p}_2 = 0$). Thus, we have:

{% math() %}
s = (E_1 + E_2)^2 - \cancel{(\mathbf{p}_1 + \mathbf{p}_2)^2}^0 = (E_1 + E_2)^2 = E_\mathrm{cm}^2
{% end %}

Where $E_\mathrm{cm} \equiv E_1 + E_2$ is the total energy in the center-of-momentum frame. Using this simplifies things considerably:

{% math() %}
\dfrac{d\sigma}{d\Omega} = \frac{\lambda_R^4}{64 \pi^2 E_\mathrm{cm}^2} \dfrac{1}{(s-m^2)^2} = \dfrac{\lambda_R^4}{64 \pi^2 s} \dfrac{1}{(s - m^2)^2}
{% end %}

Since we once again have a constant differential cross-section, the total cross-section $\sigma$ is simply equal to the differential cross-section multiplied by $4\pi$ (just like our first Feynman diagram example). So, we have:

{% math() %}
\sigma = 4\pi \left(\dfrac{d\sigma}{d\Omega}\right) = \dfrac{\lambda_R^4}{16\pi s(s-m^2)^2}
{% end %}

The last diagram we will consider is substantially harder to calculate than the first two, so we will only evaluate it part-way. Consider the same scattering scenario with two incident pions of momenta $p_1, p_2$, except this time they form a pair of virtual particles when they interact, symbolized by a **loop** on the Feynman diagram. Afterwards, the two virtual particles are annihilated and form two new pions with momenta $q_1, q_2$. This is the first diagram where we have a loop due to the pair of virtual particles that are produced - something that will become absolutely crucial once we get to quantum electrodynamics. The diagram is shown below:

{{ diagram(src="../diagrams/two-pion-loop.svg" desc="") }}

As with before, we have two vertices, so we need two $(-i\lambda)$ terms. In addition, to ensure momentum conservation for all real particles, we again need the Dirac delta $(2\pi)^4 \delta^4(p_1 + p_2 - q_1 - q_2)$. The more interesting (and difficult) part of this Feynman diagram is the loop in the center, which comes as a result of the virtual particle pair. Momentum is still conserved at each vertex, so the momenta of the two particles must be $k$ and $l = p_1 + p_2 - k$; but it is not conserved _in the loop_ since the virtual particles are so short-lived that they can have arbitrary energy and momentum (from the Heisenberg uncertainty principle). This means that we have to _integrate_ over the loop; since we have one loop, we need one integral over $k$. Lastly, we need the propagators for the two internal lines (representing the virtual particle pair), which are $\dfrac{i}{k^2 - m^2 + i\epsilon}$ and $\dfrac{i}{l^2 - m^2 + i\epsilon}$. Combining everything together gives us the scattering amplitude:

{% math() %}
\mathcal{A}_{(2)} = (-i\lambda)^2(2\pi)^4 \delta^4(p_1 + p_2 - q_1 - q_2) \int \dfrac{d^4k}{(2\pi)^4} \dfrac{i}{k^2 - m^2 + i\epsilon} \dfrac{i}{l^2 - m^2 + i\epsilon}
{% end %}

Thus, we have {% inlmath() %}\mathcal{A} \approx \langle f|i\rangle + \mathcal{A}_{(2)}{% end %} (as long as we are only considering this Feynman diagram). Let's now get the invariant amplitude ($\mathcal{M}$) from our scattering amplitude, using the same term-comparison method as we did previously. As it is quite annoying to write out $\mathcal{A} = \langle f|i\rangle + i\mathcal{M}(2\pi)^4\delta^4\left(\sum_j p_j - \sum_j q_j\right)$  every single time due to the verbose delta functions, it is often simpler to define a modified amplitude $\tilde{\mathcal{A}}_{(2)}$ given by:

{% math() %}
\mathcal{A}_{(2)} =\tilde{\mathcal{A}}_{(2)} \delta^4\left(\sum_j p_j - \sum_j q_j\right)
{% end %}

This allows us to just write $i\mathcal{M} = \tilde{\mathcal{A}}_{(2)}$ rather than the complicated expression for $\mathcal{A}$ in terms of $\mathcal{M}$. Substituting our previous results, we have:

{% math() %}
\begin{align*}
i\mathcal{M} &= \tilde{\mathcal{A}}_{(2)} \\
&= (-i\lambda)^2 \int \dfrac{d^4k}{(2\pi)^4} \dfrac{i}{k^2 - m^2 + i\epsilon} \dfrac{i}{l^2 - m^2 + i\epsilon} \\
&\Rightarrow \mathcal{M} =  (-\lambda^2) \int \dfrac{d^4k}{(2\pi)^4} \dfrac{i}{k^2 - m^2 + i\epsilon} \dfrac{i}{l^2 - m^2 + i\epsilon}
\end{align*}
{% end %}

Where as with before we would need to take the limit $\epsilon \to 0$ at the end of our calculations. Now, we encounter a problem, because the integral over $d^4k$ is actually a _divergent_ integral! In fact, this is an issue with all diagrams with loops. The way to solve this problem took physicists decades and was not resolved until the 1950s and 1960s, when Feynman, Schwinger and Tomonaga published a set of seminal papers that showed how it was possible to make integrals convergent using a process called **renormalization**.

> **Note on terminology:** The first two Feynman diagrams we considered only contained straight lines, which somewhat resemble branches of a tree, so they are called **tree-level diagrams**. The third diagram, however, has a loop, so it is called a **loop-level diagram**. The invariant amplitude $\mathcal{M}$, up to second-order, is the _sum_ of all three diagrams we have considered. Also note that all loop-level diagrams are formally divergent and require renormalization to solve.

### Normal ordering and Wick's theorem

To understand how Feynman diagrams work at a conceptual level, we need to introduce the idea of **normal ordering**. Recall how, when we first quantized our classical field $\phi$ to promote it to an operator $\hat \phi$, we wrote our field in terms of _creation and annihilation operators_. Normal ordering takes a combination of operators, and sorts them so that creation operators are always on the _left_ and annihilation operators are always on the _right_, as shown in the below set of equations:

{% math() %}
\begin{align*}
\hat a_p \hat a_p^\dagger &\xrightarrow{\text{normal order}} \hat a_p^\dagger \hat a_p \\
\hat a_p \hat a_p \hat a_p^\dagger &\xrightarrow{\text{normal order}} \hat a_p^\dagger \hat a_p \hat a_p \\
\hat a_p^\dagger \hat a_p \hat a_p^\dagger &\xrightarrow{\text{normal order}} \hat a_p^\dagger \hat a_p^\dagger \hat a_p \\
\hat a_p \hat a^\dagger_p + \hat a_p\hat a_p^\dagger \hat a_p &\xrightarrow{\text{normal order}} \hat a^\dagger_p \hat a_p + \hat a^\dagger_p \hat a_p \hat a_p
\end{align*}
{% end %}

We denote normal ordering either with the $N[\dots]$ notation or (the notation we'll use) with colons $:$ surrounding the operators we're interested in. With this notation, our previous set of equations reads:

{% math() %}
\begin{align*}
:\hat a_p \hat a_p^\dagger: ~ &= ~ \hat a_p^\dagger \hat a_p \\
:\hat a_p \hat a_p \hat a_p^\dagger: ~ &= ~ \hat a_p^\dagger \hat a_p \hat a_p \\
:\hat a_p^\dagger \hat a_p \hat a_p^\dagger : ~ &= ~ \hat a_p^\dagger \hat a_p^\dagger \hat a_p \\
:\hat a_p \hat a^\dagger_p + \hat a_p\hat a_p^\dagger \hat a_p : ~ &= ~\hat a^\dagger_p \hat a_p + \hat a^\dagger_p \hat a_p \hat a_p
\end{align*}
{% end %}

What is the use of normal ordering? Well, normal ordering helps us evaluate products of creation and annihilation operators much more easily. Take, for instance, the expression $\hat a_p \hat a_p^\dagger \hat a_p \hat a_p \hat a_p^\dagger|0\rangle$; this is not so easy to evaluate, since we have creation operators and annihilation operators all jumbled together! However, if we _normal-order_ the same expression, we have:

{% math() %}
:\hat a_p \hat a_p^\dagger \hat a_p \hat a_p \hat a_p^\dagger: |0\rangle = \underbrace{\hat a_p^\dagger \hat a_p^\dagger}_{2 \times \hat a_p^\dagger} \underbrace{\hat a_p \hat a_p \hat a_p}_{3 \times \hat a_p} |0\rangle
{% end %}

Now, we can see that we have 2 creation operators on the left, and 3 annihilation operators on the right. This makes the expression much easier to evaluate; since we know that $\hat a_p|0\rangle = 0$, the whole expression becomes zero! The same idea works with non-vacuum states too. For instance, assume we have a two-particle state $|p_1, p_2\rangle$. The three annihilation operators can each annihilate a single particle, but we have only two, so we have $\hat a_p \hat a_p \hat a_p |p_1, p_2\rangle = 0$. The same idea generalizes to a three-particle state $|p_1, p_2, p_3\rangle$; the three annihilation operators each annihilate a single particle, so we have no particles left (though this time we're left with the vacuum state $|0\rangle$, because we'd need a fourth annihilation operator to annihilate the vacuum state).

The takeaway is that normal ordering makes things convenient because it puts all the annihilation operators on the right, allowing us to easily "read off" the particles annihilated by the operators. In the case where we have more annihilation operators than we have particles, then we know that acting the operators on our particle state gives zero. For the same reason, the vacuum expectation value $\langle 0|:\hat a_p^\dagger \dots \hat a_p:|0\rangle$ of _any normal-ordered product_ of creation and annihilation operators is zero! (Since we have zero particles and at least one annihilation operator in the normal-ordered product, acting the operators on $|0\rangle$ gives zero.)

Let us now consider the time-ordered product of two field operators given by $\mathcal{T}\{\hat \phi(x) \hat \phi(y)\}$. A useful trick from earlier is write $\hat \phi$ as the sum of two operators $\hat \phi_+$ and $\hat \phi_-$, which are respectively given by:

{% math() %}
\begin{align*}
\hat \phi_+(x) &= \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \hat a_p^\dagger e^{+ip_\mu x^\mu}, \\
\hat \phi_-(x) &= \int \dfrac{d^3 p}{(2\pi)^3} \dfrac{1}{\sqrt{2E_p}} \hat a_p e^{-ip_\mu x^\mu}
\end{align*}
{% end %}

Now, what's essential is that the expressions for $\hat \phi_+$ and $\hat \phi_-$ are *directly related* to the creation and annihilation operators:

{% math() %}
\begin{align*}
\hat \phi_+(x) \sim \hat a_p^\dagger \\
\hat \phi_-(x) \sim \hat a_p
\end{align*}
{% end %}

Normal-ordering can help us solve what would otherwise be a very tricky problem in computing time-ordered products, like $\mathcal{T}\{\hat \phi(x) \hat \phi(y)\}$. To start, let us recall that the time-ordered product $\mathcal{T}\{\hat \phi(x) \hat \phi(y)\}$ is _defined_ as:

{% math() %}
\langle 0|\mathcal{T} \big\{ \hat \phi(x_2) \hat \phi(x_1) \big\} |0\rangle = \begin{cases}
\langle 0|\hat \phi(x_2) \hat \phi(x_1)|0\rangle, & t_2 > t_1, \\
\langle 0|\hat \phi(x_1) \hat \phi(x_2)|0\rangle, & t_1 > t_2
\end{cases}
{% end %}

Let us assume that the particle is initially at spacetime point $(t_1, x^i)$ and then is later found at spacetime point $(t_2, y^i)$, where $x^i$ and $y^i$ refer to the spatial (three-dimensional) positions of the particle at $t_1$ and $t_2$ respectively. Using $\hat \phi = \hat \phi_+ + \hat \phi_-$, we have:

{% math() %}
\begin{align*}
\hat \phi(x) \hat \phi(y) &= [\hat \phi_+(x) + \hat \phi_- (x)][\hat \phi_+(y) + \hat \phi_- (y)] \\
&= \hat \phi_+(x) \hat \phi_+(y) + \hat \phi_+(x) \hat \phi_-(y) + \hat \phi_-(x) \hat \phi_+(y) + \hat \phi_-(x) \hat \phi_-(y) \\
&= \hat \phi_+(x) \hat \phi_+(y) + \hat \phi_+(x) \hat \phi_-(y) + \hat \phi_+(y) \hat \phi_-(x) + \hat \phi_-(x) \hat \phi_-(y) \\
&\qquad + [\hat \phi_-(x), \hat \phi_+(y)] \\
\end{align*}
{% end %}

Where $[\hat \phi_-(x), \hat \phi_+(y)] \equiv \hat \phi_-(x) \hat \phi_+(y) - \hat \phi_+(y)\hat \phi_-(x)$ is the **commutator** between the $\hat \phi_-(x)$ and $\hat \phi_+(y)$. We notice that the first four terms of the expansion is the same thing as the normal-ordered product $:\hat \phi(x)\hat \phi(y):$, which is given by:

{% math() %}
:\hat \phi(x) \hat \phi(y): ~= ~\hat \phi_+(x) \hat \phi_+(y) + \hat \phi_+(x) \hat \phi_-(y) + \hat \phi_+(y) \hat \phi_-(x) + \hat \phi_-(x) \hat \phi_-(y)
{% end %}

It may not be obvious at first glance that our expression is normal-ordered. However, recalling that $\hat \phi_+ \sim \hat a_p^\dagger$ and $\hat a_- \sim \hat a_p$, we realize that this expression _is_ indeed normal-ordered:

- $\hat \phi_+(x) \hat \phi_+(y) \sim \hat a_p^\dagger \hat a_p^\dagger$, but since this expression contains no annihilation operators it is _already_ normal-ordered (if you don't have any $\hat a_p$'s to put on the right, any combination of $\hat a_p^\dagger$'s is normal-ordered!)
- $\hat \phi_-(x) \hat \phi_-(y) \sim \hat a_p \hat a_p$, but since this expression contains no creation operators it is also _already_ normal-ordered for the same reason as why $\hat a_p^\dagger \hat a_p^\dagger$ is already normal-ordered
- $\hat \phi_+(x) \hat \phi_-(x) \sim \hat a_p^\dagger \hat a_p$ has the creation operators on the left and the annihilation operators on the right, so it is normal-ordered
- $\hat \phi_+(y) \hat \phi_-(x) \sim \hat a_p^\dagger \hat a_p$ also has the creation operators on the left and the annihilation operators on the right, so it is also normal-ordered

Another useful fact is that since $\hat \phi_+(x) \hat \phi_+(y) \sim \hat a_p^\dagger \hat a_p^\dagger$ (creating two particles) and $\hat \phi_-(x) \hat \phi_-(y) \sim \hat a_p \hat a_p$ (annihilating two particles), they essentially cancel each other out. The remaining terms $\hat \phi_+(x) \hat \phi_-(x)$ and $\hat \phi_+(y) \hat \phi_-(x)$ each have a single creation operator and a single annihilation operator. Their net effect is to **create two particles** and **annihilate two particles**. This helps us neatly read off the action of $:\hat \phi(x) \hat \phi(y):$ on a state of $N$ particles without needing to write out the full normal-ordered expansion:

- If our $N$-particle state $|p_1, p_2, \dots, p_N\rangle$ has $N < 2$ then $:\hat \phi(x) \hat \phi(y): |p_1, p_2, \dots, p_N\rangle \to 0$, since $:\hat \phi(x) \hat \phi(y):$ is capable of annihilating _two particles_, meaning we need at least two particles in the state to not be completely annihilated.
- If our $N$-particle state $|p_1, p_2, \dots, p_N\rangle$ has $N \geq 2$ then $:\hat \phi(x) \hat \phi(y): |p_1, p_2, \dots, p_N\rangle$ causes us to end up in a state with the same number of particles. Again, since $:\hat \phi(x) \hat \phi(y):$ annihilates two particles but then creates two more, the net number of particles is unchanged.

Meanwhile, the last term in the expansion (the commutator $[\hat \phi_-(x), \hat \phi_+(y)]$) is called a **contraction**, and we denote it with the notation $\overbracket{\hat \phi(x) \hat \phi(y)}$, which gives us (although this is not easy to see) the Feynman propagator!

{% math() %}
\overbracket{\hat \phi(x) \hat \phi(y)} = [\hat \phi_-(x), \hat \phi_+(y)] = D_F(x-y)
{% end %}

> **Note:** The contraction of two fields must be in the form $\overbracket{\hat \phi(x_1) \hat \phi(x_2)}$, that is, the same field evaluated at two different spacetime locations. You **cannot** have a contraction between two different fields.

An *extremely* nice property of the contraction of two fields is that it is _independent of time ordering_. This means that all our results from our assumption that $t_2 > t_1$ is _also_ true for $t_1 < t_2$! A way to intuitively understand this is that the contraction of two fields is simply the Feynman propagator, and the Feynman propagator is *already* time-ordered in its definition. Therefore, it doesn't matter if $t_2 > t_1$ or $t_1 > t_2$; the Feynman propagator gives the identical result. The same is _not_ true for the normal-ordered product $:\hat \phi(x) \hat \phi(y):$, which _is_ time dependent, but the addition of the contraction $\overbracket{\hat \phi(x) \hat \phi(y)}$ "corrects" for the discrepancy and makes the overall Wick expansion time-independent. Thus, combining our results, we have:

{% math() %}
\begin{align*}
\mathcal{T}\{\hat \phi(x) \hat \phi(y)\} &= \hat \phi_+(x) \hat \phi_+(y) + \hat \phi_+(x) \hat \phi_-(y) + \hat \phi_+(y) \hat \phi_-(x) + \hat \phi_-(x) \hat \phi_-(y) \\
&\qquad + [\hat \phi_-(x), \hat \phi_+(y)] \\
&=~:\hat \phi(x) \hat \phi(y): + \overbracket{\hat \phi(x) \hat \phi(y)}
\end{align*}
{% end %}

We have now found a way to convert a _time-ordered_ product into a _normal-ordered_ product! This leads to a profound result, which we call **Wick's theorem**:

> **Wick's theorem:** The time-ordered product $\mathcal{T}(\hat \phi_1 \hat \phi_2 \dots \hat \phi_n)$ of an arbitrary number of field operators, where $\hat \phi_n = \hat \phi(x_n)$, can be written as the sum of $: \hat \phi_1 \hat \phi_2 \dots \hat \phi_n:$ and all possible contractions $\overbracket{\hat \phi_a \hat \phi_b}$.

As it is often quite bothersome to write out the Wick expansion from scratch, it is often convenient to refer to the following formulae for the Wick expansion of two, three, and four field operators:

{% math() %}
\begin{align*}
% two field operators
\mathcal{T} \{\hat \phi_1 \hat \phi_2 \} &= ~:\hat \phi_1 \hat \phi_2 :~ + \overbracket{\hat \phi_1 \hat \phi_2} \\
% three field operators
\mathcal{T} \{\hat \phi_1 \hat \phi_2 \hat \phi_3\} &= :\hat \phi_1 \hat \phi_2 \hat \phi_3: + :\hat \phi_1 : \overbracket{\hat \phi_2 \hat \phi_3} + :\hat \phi_2: \overbracket{\hat \phi_1 \hat \phi_3} + :\hat \phi_3: \overbracket{\hat \phi_1 \hat \phi_2} \\
% four field operators
\mathcal{T} \{\hat \phi_1 \hat \phi_2 \hat \phi_3 \hat \phi_4\} &= ~:\hat \phi_1 \hat \phi_2 \hat \phi_3 \hat \phi_4: + :\hat \phi_3 \hat \phi_4:\overbracket{\hat \phi_1 \hat \phi_2} + :\hat \phi_2 \hat \phi_4: \overbracket{\hat \phi_1 \hat \phi_3} + :\hat \phi_2 \hat \phi_3: \overbracket{\hat \phi_1 \hat \phi_4} \\
&\qquad \qquad+ :\hat \phi_1 \hat \phi_4: \overbracket{\hat \phi_2 \hat \phi_3} + :\hat\phi_1 \hat \phi_3: \overbracket{\hat \phi_2 \hat \phi_4} + :\hat \phi_1 \hat \phi_2: \overbracket{\hat \phi_3 \hat \phi_4} \\
&\qquad \qquad+ \overbracket{\hat \phi_1 \hat \phi_2} \overbracket{\hat \phi_3 \hat \phi_4} + \overbracket{\hat \phi_1 \hat \phi_3} \overbracket{\hat \phi_2 \hat \phi_4} + \overbracket{\hat \phi_1 \hat \phi_4} \overbracket{\hat \phi_2 \hat \phi_3}
\end{align*}
{% end %}

It is possible to write out the Wick expansion of a greater number of field operators, but some clever reasoning usually means we don't have to. For instance, consider a theory with a $\phi^6$ interaction, where $\phi$ is a real scalar field. Since contractions always involve the product of two field operators $\overbracket{\hat \phi_a \hat \phi_b} = \overbracket{\hat \phi(x_a) \hat \phi(x_b)}$ and never more (or less) than two, we know that other than the $:\hat \phi_1 \hat \phi_2 \hat \phi_3 \hat \phi_4 \hat \phi_5 \hat \phi_6 :$ term at the beginning, the terms with normal-ordered products in the Wick expansion must be in the form $:\hat \phi_a \hat \phi_b \hat \phi_c \hat \phi_d: \overbracket{\hat \phi_e \hat \phi_f}$. This is because $\phi^6$ theory translates to the time-ordered product $\mathcal{T}(\hat \phi_1 \hat \phi_2 \hat \phi_3 \hat \phi_4 \hat \phi_5 \hat \phi_6)$ with **six field operators**, but since the contraction must always be **two field operators**, the number of normal-ordered field operators in each term must be $6 - 2 = 4$, which is where we get:

{% math() %}
\text{Normal-ordered part} =
~:\hat \phi_a \hat \phi_b \hat \phi_c \hat \phi_d: ~ = 4 \times \text{field operators}
{% end %}

Other than the normal-ordered part, we also know that there are several terms made entirely of contractions, which we collectively call the _pure contractions part_. For instance, in $\phi^6$ theory, we would have terms like $\overbracket{\hat \phi_1 \hat \phi_2} \overbracket{\hat \phi_3 \hat \phi_4} \overbracket{\hat \phi_5 \hat \phi_6}$ in the pure contraction part. We can check that we indeed wrote the correct number of contractions in the pure contraction part (assuming a time-ordered product of $n$ fields) with the formula:

{% math() %}
\text{Contractions in pure contractions part} = \dfrac{n!}{(n-2)!}
{% end %}

For $n = 6$ we have $\frac{6!}{(6-2)!} = 30$, which is rather ridiculous to write out by hand. However, since $\phi^6$ has just one field, we have $\hat \phi_1 = \hat \phi_2 = \hat \phi_3 = \hat \phi_4 = \hat \phi_5 = \hat \phi_6$. Thus, instead of 30 contractions to write out by hand, the pure contractions part is $30 \times \overbracket{\hat \phi \hat \phi} \overbracket{\hat \phi \hat \phi} \overbracket{\hat \phi \hat \phi}$. So, the total Wick contraction is given by:

{% math() %}
\begin{align*}
\mathcal{T}(\hat \phi(x)^6) &= ~: \hat \phi\hat \phi\hat \phi\hat \phi\hat \phi\hat \phi: + \text{Normal-ordered part} + \text{Pure contractions part} \\
&= ~: \hat \phi\hat \phi\hat \phi\hat \phi\hat \phi\hat \phi: + \text{Normal-ordered part} + 30 \overbracket{\hat \phi \hat \phi} \overbracket{\hat \phi \hat \phi} \overbracket{\hat \phi \hat \phi}
\end{align*}
{% end %}

Since normal-ordering puts all annihilation operators on the right and creation operators on the left, we know that any expression $\langle i|:\hat \phi_a \hat \phi_b \hat \phi_c \hat \phi_d:|f\rangle$ must have two annihilation operators on the right (from $\hat \phi_c \hat \phi_d:$) and two creation operators on the left (from $:\hat \phi_a \hat \phi_b$). Thus we can write:

{% math() %}
:\hat \phi_a \hat \phi_b \hat \phi_c \hat \phi_d:~ \sim ~ \hat a_p^\dagger \hat a_p^\dagger \hat a_p \hat a_p \quad \Rightarrow \quad \langle i|:\hat \phi_a \hat \phi_b \hat \phi_c \hat \phi_d:|f\rangle \sim  \langle i|\hat a_p^\dagger \hat a_p^\dagger \hat a_p \hat a_p|f\rangle
{% end %}

Similarly, for the first term ($\hat \phi \hat \phi \hat \phi \hat \phi \hat \phi \hat \phi$) we have:

{% math() %}
:\hat \phi_a \hat \phi_b \hat \phi_c \hat \phi_d \hat \phi_d \hat \phi_f: ~ \sim ~\langle i|\hat a_p^\dagger \hat a_p^\dagger \hat a_p^\dagger \hat a_p \hat a_p \hat a_p|f\rangle \quad \Rightarrow \quad\langle i |:\hat \phi_a \hat \phi_b \dots \hat \phi_f:|f\rangle \sim \langle i|\hat a_p^\dagger \hat a_p^\dagger \hat a_p^\dagger \hat a_p \hat a_p \hat a_p|f\rangle
{% end %}

But we know that $\hat a_p \hat a_p |f\rangle = 0$ and $\hat a_p \hat a_p \hat a_p|f\rangle = 0$ for all single-particle states! Thus, if $|f\rangle = |q\rangle$ is a single-particle state, all the normal-ordered terms vanish. Using this, we can find that for $|i\rangle = |p\rangle$ and $|f\rangle = |q\rangle$:

{% math() %}
\langle p|\mathcal{T}(\hat \phi(x)^6)|q\rangle = 30 \overbracket{\hat \phi \hat \phi} \overbracket{\hat \phi \hat \phi} \overbracket{\hat \phi \hat \phi} = 30D_F(x-x)^3
{% end %}

For a two-particle state $|p_1,p_2\rangle$, we have $\hat a_p \hat a_p |f\rangle \neq 0$ (since the number of annihilation operators matches the number of creation operators, giving $\hat a_p \hat a_p|p_1, p_2\rangle \sim \sqrt{2E_p}(2\pi)^3|0\rangle$), though as with before $\hat a_p \hat a_p \hat a_p|f\rangle = 0$. The beauty of Feynman diagrams lies in the fact that they reproduce the _same terms_ as performing a Wick expansion. When Wick expansions can involve hundreds or even thousands of terms(!), they become _absolutely essential_ for calculating probability amplitudes, for which writing out the Wick expansion manually become impossible. It is no surprise, then, that Richard Feynman won the Nobel Prize in Physics in 1965; his contribution to quantum field theory opened up countless doors that previously were out of the reach of physics, allowing us to understand the Universe as never before.

### Symmetry factors

Before we close our chapter on Feynman diagrams, it is important to address something we have thus ignored, and that is the importance of the **symmetry factor**. As we saw in our statement of Feynman rules for $\phi^4$ theory, the last step in any Feynman diagram is to multiply all terms by an appropriate symmetry factor. The importance of this factor lies in the fact that several different Feynman diagrams may represent (part of) the same term in the S-matrix; for instance, if we rotate a diagram by 90 degrees, it (obviously) is still the same process, but the Feynman diagram would be different. Thus, we need a compensating factor to remove the redundancy of several Feynman diagrams that describe the same physical process. This factor, which we'll call $S$ (for "symmetry factor"), contributes to a Feynman diagram by a factor of $1/S$.

The precise determination of the symmetry factor requires complicated proofs from topology and combinatorics. However, a rough set of rules is as follows:

- In tree-level diagrams, identical particles (such as pions) have $S = 2$ whereas non-identical particles (such as electrons with opposite spins) have $S = 1$
- In loop-level diagrams, every loop contributes a multiplicative factor of $2$ to the symmetry factor
- If two vertices are connected by $n$ internal lines, they collectively contribute to a multiplicative factor of $n!$

Let's consider some examples. In the first Feynman diagram we saw, we considered two identical pions; thus the symmetry factor was $S = 2$. _Identical_ here doesn't refer to two particles with exactly the same momenta or energy; rather, it means that if we have two particles of the same type (in our case, two pions) we could not distinguish them apart. Meanwhile, for the one-loop diagram, the loop contributes a factor of $2$, and since it is not a tree level diagram this is the only contribution, so again we have $S = 2$. Using the same process, we could do this for other diagrams as well.

[^1]: Quartic theory can be understood as the low-energy limit of **chiral perturbation theory (CPT)**, the theory that describes composite particles bound by the strong interaction, including pions (more precisely, the sigma model). The theoretical amplitude from CPT (first computed by [Weinberg in 1966](https://doi.org/10.1103/PhysRevLett.17.616)) is $\mathcal{M} \approx 4\left(\dfrac{g_V}{F_\pi}\right)^2(m_\pi^2 - t)$, where $t$ is a [Mandelstam variable](https://en.wikipedia.org/wiki/Mandelstam_variables) equal to $(p_4 - p_2)^2 c^2$, $g_V \approx 6$ is the [axial-vector coupling constant](https://doi.org/10.1103/PhysRevD.104.034021) from CPT, $F_\pi \approx \pu{92.4 MeV}$ is the pion decay constant, and $m_\pi \approx \pu{139.6 MeV}$ is the pion mass. Assuming a perfectly elastic collision between identical pions, we have $p_2 = p_4$ and thus $\mathcal{M} \approx 4 m_\pi^2 g_V^2/F_\pi^2$. To lowest-order we know that quartic theory predicts $|\mathcal{M}| = \lambda_R$, so this gives $\lambda_R \approx 4 m_\pi^2 g_V^2/F_\pi^2$ which gives $\lambda_R \approx 328.7$.