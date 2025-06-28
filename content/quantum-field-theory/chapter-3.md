+++
title = "Quantization of the electromagnetic field"
date = 2025-04-28
+++

The theory of classical electromagnetism is one of the most beautiful theories in physics, and also the jumping-off point to one of the earliest (and most successful) quantum field theories. It made the startling - but correct - prediction that all types of light were in fact _electromagnetic waves_ travelling at a fixed, universal speed $c$. We'll take our first steps into a "real" quantum field theory - the theory of **quantum electrodynamics** - from here.

## What is electromagnetism?

Before we get to quantum electrodynamics, we need to first examine the classical theory it was built upon. Classical electromagnetism tells us that even empty space is not _truly_ empty; rather, it is filled with electromagnetic fields. All electric charges (from the smallest electron to the largest stars) interact by these fields: charges create variations in the electromagnetic field, which in turn exerts a force on other charges - both those close by and those far away. In this way, the electromagnetic field is responsible for all electrical _and_ magnetic phenomena (hence why it is called the _electromagnetic field_).

For primarily historical reasons, it is customary to divide the electromagnetic field into two separate parts - the electrical part, which we call the _electric field_ and represent as $\mathbf{E}$ (or $E^i$ in tensor notation), as well as the magnetic part, which we call the _magnetic field_ and represent as $\mathbf{B}$ (or $B^i$ in tensor notation). In reality, electric and magnetic fields are parts of one thing, but this distinction has stuck around and is standard convention.

A surprising prediction of electromagnetism is that many things that don't immediately appear to be related to electricity or magnetism in nature are actually fundamental electromagnetic phenomena. The most famous example? Electromagnetic theory predicts that **light is an electromagnetic wave**. While this might be hard to believe - what does light have in common with electricity? - you probably are surrounded by invisible electromagnetic waves right this moment! Radio waves that carry television signals, microwaves used to transmit Wi-Fi, visible light that we use to see, infrared light from the Sun that keeps us warm, X-rays used for medical imaging: these are _all_ electromagnetic waves.

Quantum electrodynamics, the quantum field theory we'll be examining, extends our knowledge of classical electrodynamics to the quantum world. We'll soon learn that in quantum field theory, the electromagnetic field comes in distinct energy states - a **vacuum state** (lowest-energy state) that we write as $|0\rangle$ using Dirac notation, a first excited state $|1\rangle$, and so on. We'll also find out that the first excited state $|1\rangle$ corresponds to _particles_ that we call **photons**. There's a lot to learn - so let's get started!

## The Maxwell Lagrangian

Both classical and quantum electrodynamics are field theories, which means that they are associated with a **Lagrangian** (and thus, an action, which is just the spacetime integral of a Lagrangian). _Technically-speaking_, what we commonly-call the Lagrangian should be more properly called the _Lagrangian density_ (the Lagrangian is its integral over all space) but we'll use the common (though incorrect) practice of just calling it "the Lagrangian". The action for the electromagnetic field (in our convention where $\hbar = c = 1$) is given by:

{% math() %}
S = \int d^4 x \left[-\dfrac{1}{4} F_{\mu \nu} F^{\mu \nu} + A_\mu J^\mu\right]
{% end %}

Where our Lagrangian is called the **Maxwell Lagrangian**, and is given by:

{% math() %}
\mathscr{L} = -\dfrac{1}{4} F_{\mu \nu} F^{\mu \nu} + A_\mu J^\mu
{% end %}

Here, $F_{\mu \nu}$ is the **Faraday field tensor**, whose components are the electric and magnetic fields, as given by:

{% math() %}
F_{\mu \nu }=\partial_\mu A_\nu -\partial_\nu A_\mu =
\begin{bmatrix}
0 &E_{x} &E_{y} &E_{z}  \\
-E_{x} &0 &-B_{z}&B_{y} \\
-E_{y} &B_{z}&0 &-B_{x} \\
-E_{z} &-B_{y}&B_{x}&0
\end{bmatrix}
{% end %}

The Faraday tensor can also be related to the **electromagnetic force** $f^\nu$ (also called the _Lorentz force_ by $f^\nu = F^{\mu \nu} \dot x_\nu$), which naturally encodes the idea that _fields exert forces on particles_. Meanwhile, $A_\mu$ is called the **electromagnetic four-potential** (or simply the _four-potential_ for short), which encodes the energy and momentum present in the electromagnetic field. 

In quantum field theory, the electromagnetic four-potential is actually much _more_ useful than the field tensor $F^{\mu \nu}$, so much so that when quantum field theorists refer to the "electromagnetic field", they typically are talking about the electromagnetic four-potential $A_\mu$ rather than the field tensor. Why? The reason is because in nature, particles want to attain their lowest possible potential energy to gain stability. You see this all the time - for instance, radioactive atoms like uranium decay into more stable atoms, releasing energy in the process, and gaining a more stable configuration as a result. Transfering energy - like by forcibly fusing heavy atoms together - has the opposite result, making them _more unstable_ and highly energetic (and dangerous!) as a result. 

The potential energy stored in fields (like the electromagnetic field) can give potential energy to particles. This means that every field (electromagnetic, gravitational, etc.) can effectively be thought of as having a certain amount of potential energy at every point, which becomes transferred to a particle placed at that location. We call that potential energy gained per particle a **potential field**, and in the case of electromagnetism, it is the _electromagnetic four-potential_ $A_\mu$. Since it's very hard to measure the forces on individual particles but comparatively easier to measure their energies and momenta, it is natural to think about the four-potential first and the field tensor second.

which are (unsurprisingly) the potential associated with the electromagnetic field. Let's now derive the field equations for $A_\mu$, from which we can find the field equations for $F_{\mu \nu}$. For this, we use the Euler-Lagrange equations for $A_\mu$:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial A_\mu} - \partial_\beta\left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta A_\mu)}\right) = 0
{% end %}

> **Note:** In the Euler-Lagrange field equations, $A_\mu$ and $\partial_\beta$ must be **different indices** because the field is a _function_ of position, that is, $A_\mu = A_\mu(x^\beta)$. Thus, the field must be denoted with a different index compared to the position $x^\beta$ (after all, the $A_x$ component of the field is not just a function of $x$, nor is $A_y$ just a function of $y$!) 

But as soon as we start, uh-oh, we have a problem! The Lagrangian is written in terms of _both_ $F_{\mu \nu}$ and $A_\mu$, but we want to find the field equations for $A_\mu$ specifically. Therefore, we want to first expand the Lagrangian to be explicitly written in terms of $A_\mu$. This involves a bit of an extensive calculation, so let's do this step-by-step.

First, let's find $F^{\mu \nu}$, the upper-index version of $F_{\mu \nu}$. Remember that we can use the metric tensor $\eta_{\mu \nu}$ to raise and lower tensors: here, $F^{\alpha \beta} = \eta^{\alpha \mu}\eta^{\beta \nu} F_{\mu \nu}$ (again, we need to balance the upper and lower repeated indices so there's an equal number of either). Substituting in the definition of the Faraday tensor $F_{\mu \nu} = \partial_\mu A_\nu -\partial_\nu A_\mu$ gets us:

{% math() %}
\begin{align*}
F^{\alpha \beta} &= \eta^{\alpha \mu} \eta^{\beta \nu} F_{\mu \nu} \\
&= \eta^{\alpha \mu} \eta^{\beta \nu} (\partial_\mu A_\nu -\partial_\nu A_\mu) \\
&= \underbrace{\eta^{\alpha \mu} \eta^{\beta \nu}\partial_\mu A_\nu - \eta^{\alpha \mu} \eta^{\beta \nu} \partial_\nu A_\mu}_\text{we distribute here} \\
&= (\eta^{\alpha \mu}\partial_\mu )(\eta^{\beta \nu} A_\nu) - (\eta^{\beta \nu} \partial_\nu)(\eta^{\alpha \mu} A_\mu) \\
&= \partial^\alpha A^\beta - \partial^\beta A^\alpha
\end{align*}
{% end %}

> **Tip:** Remember that we can raise and lower indices using the Minkowski metric, for instance, $\eta^{\alpha \mu} A_\mu = A^\alpha$. Meanwhile, we can use the Kronecker delta to relabel indices (but _not_ raise or lower indices), for example $\delta^\mu{}_\nu A^\nu = A^\mu$.

Let's recap our steps. First, we distributed out the terms; then, we grouped terms with like indices, where we could move the metric _inside_ terms because we know the Minkowski metric has constant coefficients. This allowed us to raise indices with the metric - for instance, $\eta^{\alpha \mu} \partial_\mu = \partial^\alpha$ and $\eta^{\beta \nu} A_\nu = A^\beta$. This gave us the result $F^{\alpha \beta} = \partial^\alpha A^\beta - \partial^\beta A^\alpha$. Since we have no terms involving $\mu$ or $\nu$ indices in $F^{\alpha \beta}$, the last step is to do an index replacement of $\alpha \to \mu, \beta \to \nu$ (remember, tensor indices are merely _labels_ and we can change those symbols as we wish). This gives us:

{% math() %}
F^{\mu \nu} = \partial^\mu A^\nu - \partial^\nu A^\mu
{% end %}

Plugging this (and the definition of $F_{\mu \nu}$) into the Maxwell Lagrangian gives us a lots of terms, but ones that end up simplifying nicely:

{% math() %}
\begin{align*}
\mathscr{L} &= -\dfrac{1}{4} F_{\mu \nu}F^{\mu \nu} + A_\mu J^\mu \\
&= -\dfrac{1}{4}(\partial_\mu A_\nu -\partial_\nu A_\mu)(\partial^\mu A^\nu - \partial^\nu A^\mu) + A_\mu J^\mu \\
&= -\dfrac{1}{4}(\partial_\mu A_\nu \partial^\mu A^\nu - \partial_\mu A_\nu \partial^\nu A^\mu \\
&\qquad \qquad- \partial_\nu A_\mu \partial^\mu A^\nu + \partial_\nu A_\mu \partial^\nu A^\mu) + A_\mu J^\mu
\end{align*}
{% end %}

While this may look complicated, notice that $\mu$ and $\nu$ are repeated as upper and lower indices in all the terms (except $A_\mu J^\mu$ but let's ignore that for now). This means $\mu$ and $\nu$ are **dummy indices** (summation indices) and we are free to change the indices to whatever we want! In the first and second terms ($\partial_\mu A_\nu \partial^\mu A^\nu$ and $\partial_\mu A_\nu \partial^\nu A^\mu$), let's make the index replacements $\mu \to \sigma$ and $\nu \to \lambda$. This turns them respectively into $\partial_\sigma A_\lambda \partial^\sigma A^\lambda$ and $\partial_\sigma A_\lambda \partial^\lambda A^\sigma$. Meanwhile, in the third and fourth terms ($\partial_\nu A_\mu \partial^\mu A^\nu$ and $\partial_\nu A_\mu \partial^\nu A^\mu$) let's make the index replacements $\mu \to \lambda$ and $\nu \to \sigma$ (which, again, we are free to do because of the Einstein summation convention). This turns them respectively into $\partial_\sigma A_\lambda \partial^\lambda A^\sigma$ and $\partial_\sigma A_\lambda \partial^\sigma A^\lambda$. Then the Lagrangian becomes:

{% math() %}
\begin{align*}
\mathscr{L} &= -\dfrac{1}{4}(\partial_\sigma A_\lambda \partial^\sigma A^\lambda - \partial_\sigma A_\lambda \partial^\lambda A^\sigma \\
&\qquad \qquad- \partial_\sigma A_\lambda \partial^\lambda A^\sigma + \partial_\sigma A_\lambda \partial^\sigma A^\lambda) + A_\mu J^\mu \\
&= -\dfrac{1}{4}(2\partial_\sigma A_\lambda \partial^\sigma A^\lambda - \underbrace{2\partial_\sigma A_\lambda \partial^\lambda A^\sigma}_{\text{swap indices } \lambda \leftrightarrow \sigma}) + A_\mu J^\mu \\
&= -\dfrac{1}{2} (\partial_\sigma A_\lambda \partial^\sigma A^\lambda - \partial_\lambda A_\sigma \partial^\sigma A^\lambda) + A_\mu J^\mu \\
&= -\dfrac{1}{2} \partial^\sigma A^\lambda[\partial_\sigma A_\lambda - \partial_\lambda A_\sigma] + A_\mu J^\mu
\end{align*}
{% end %}

Again, let's recap: after subsituting in our relabelled expressions, we find that - ta-da! - the first four terms collapse to just two. What's more, we can factor out a common factor $\partial^\sigma A^\lambda$ to simplify further. We do need to make one slight change by relabelling the $2\partial_\sigma A_\lambda \partial^\lambda A^\sigma$ term to $2\partial_\lambda A_\sigma \partial^\sigma A^\lambda$. If this is hard to understand, you can achieve an equivalent result in two steps. First, relabel $\sigma, \lambda$ to another set of dummy indices first (for instance, $\sigma \to \alpha, \lambda \to \beta$). Then, we get $2\partial_\sigma A_\lambda \partial^\lambda A^\sigma \to 2\partial_\alpha A_\beta \partial^\beta A^\alpha$. We can then perform another completely-valid replacement of $\alpha \to \lambda, \beta \to \sigma$ (since both are dummy indices). Then, we get $2\partial_\alpha A_\beta \partial^\beta A^\alpha \to 2\partial_\lambda A_\sigma \partial^\sigma A^\lambda$, which is our result from before.

Phew, that was a lot! Now, we can _finally_ find the equations of motion. Remember the Euler-Lagrange equation for $A_\mu$ is given by:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial A_\mu} - \partial_\beta\left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta A_\mu)}\right) = 0
{% end %}

Let us now take the partial derivatives of the Lagrangian, which we perform step-by-step below. It's helpful to actually first expand the Lagrangian:

{% math() %}
\begin{align*}
\mathscr{L} &= -\dfrac{1}{2} \partial^\sigma A^\lambda [\partial_\sigma A_\lambda - \partial_\lambda A_\sigma] + A_\mu J^\mu \\
&= -\dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) + \dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma) + A_\mu J^\mu \\
\end{align*}
{% end %}

Now we can differentiate, as follows:

{% math() %}
\begin{align*}
% derivative of Lagrangian with respect to field
\dfrac{\partial \mathscr{L}}{\partial A_\mu} &= J^\mu \\
% derivative of Lagrangian with respect to partial derivative of field
\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta A_\mu)} &= \dfrac{\partial}{\partial(\partial_\beta A_\mu)}\left[-\dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) + \dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)\right] \\
&\qquad \qquad + \cancel{\dfrac{\partial}{\partial(\partial_\beta A_\mu)}\bigg[A_\mu J^\mu\bigg]}^0 \\
&= \dfrac{\partial}{\partial(\partial_\beta A_\mu)}\left[-\dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) + \dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)\right] \\
\end{align*}
{% end %}

The partial derivative with respect to $\partial_\beta A_\mu$ is by far the more difficult of the two partial derivatives, so let's go through it. In the first step, since $A_\mu J^\mu$ does not depend on $\partial_\beta A_\mu$ so its derivative is zero, as we showed above. Continuing from where we left off, we have:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial (\partial_\beta A_\mu)} &= \dfrac{\partial}{\partial(\partial_\beta A_\mu)}\left[-\dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) + \dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)\right] \\
% step 1
&= \dfrac{1}{2}\dfrac{\partial}{\partial(\partial_\beta A_\mu)}\bigg[-(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) +  (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)\bigg] \\
\end{align*}
{% end %}

> **Tip**: This is a great example of how to properly take derivatives with respect to a tensor with upper and lower indices. For some tensor $K^{\mu \nu}$, it's important to remember that $\partial_\mu K^{\mu \nu} \neq \partial^\mu K_{\mu \nu} \neq \partial_\mu K_{\mu \nu}$. Rather, we must **lower the indices first** with $K^{\mu \nu} = \eta^{\mu \alpha} \eta^{\nu \beta} K_{\alpha \beta}$ and **then** take the derivatives with respect to the lower index. We do the same for some tensor with lower indices, except we would need to **raise the indices** first. Furthermore, we have to be careful of products, in which case we need to use the **product rule** for differentiation.

We now have two terms to differentiate, $(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda)$ and $(\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)$. We'll differentiate them one by one. Starting with the first term and using the product rule for derivatives, we have:

{% math() %}
\begin{align*}
\dfrac{\partial}{\partial(\partial_\beta A_\mu)}(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) &= (\partial_\sigma A_\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}(\partial^\sigma A^\lambda) \\
&\qquad \qquad+ (\partial^\sigma A^\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}(\partial_\sigma A_\lambda) \\
&= (\partial_\sigma A_\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}\underbrace{(\eta^{\mu \sigma} \eta^{\beta \lambda}\partial_\mu A_\beta)}_\text{lower indices} \\
&\qquad \qquad+ (\partial^\sigma A^\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}\underbrace{(\delta^\mu{}_\sigma \delta^\beta{}_\lambda \partial_\mu A_\beta)}_\text{relabel indices} \\
&=\underbrace{(\partial_\sigma A_\lambda)\eta^{\mu \sigma} \eta^{\beta \lambda} + (\partial^\sigma A^\lambda)\delta^\mu{}_\sigma \delta^\beta{}_\lambda}_\text{distribute after differentiating} \\
&=\partial^\mu A^\beta + \partial^\mu A^\beta  \\
&= 2\partial^\mu A^\beta
\end{align*}
{% end %}

Here, we first lowered the indices so that we had all expressions dependent on $A_\mu$ as a _lower index_, because we have to make sure that our indices match, since $\dfrac{\partial}{\partial(\partial_\beta A_\mu)} \neq \dfrac{\partial}{\partial(\partial^\beta A^\mu)}$. So, we used the Minkowski metric to lower the indices, after which we could properly differentiate. Using the exact same procedure, we can find that:

{% math() %}
\dfrac{\partial}{\partial(\partial_\beta A_\mu)}(\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma) = 2\partial^\beta A^\mu
{% end %}

Meaning, if we substitute back into our expression for the partial derivative of the Lagrangian with respect to $\partial_\beta A_\mu$, we have:

{% math() %}
\begin{align*}
\dfrac{\partial \mathscr{L}}{\partial (\partial_\beta A_\mu)} &= \dfrac{1}{2}\dfrac{\partial}{\partial(\partial_\beta A_\mu)}\bigg[-(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) +  (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)\bigg] \\
&= \dfrac{1}{2} \bigg[-2\partial^\mu A^\beta + 2\partial^\beta A^\mu] \\
&= \partial^\beta A^\mu- \partial^\mu A^\beta \\
&= F^{\beta \mu} \\
\end{align*}
{% end %}

Thus, substituting our results into the Euler-Lagrange equation for $A_\mu$, we have:

{% math() %}
\begin{gather*}
\dfrac{\partial \mathscr{L}}{\partial A_\mu} - \partial_\beta\left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta A_\mu)}\right) = J^\mu - \partial_\beta F^{\mu \beta} = 0 \\
\Rightarrow \partial_\beta F^{\beta \mu} = J^\mu
\end{gather*}
{% end %}

After a rather horrendous amount of math, we have therefore derived the essential equation of classical electrodynamics - **Maxwell's equations**, given by $\partial_\beta F^{\beta \mu} = J^\mu$ (although it is usually written with the different tensor indices $\partial_\mu F^{\mu \nu} = J^\mu$ instead, though that's just a matter of notational preference). Note that if we so wished, we could also express Maxwell's equations purely in terms of $A^\mu$ as follows:

{% math() %}
\begin{align*}
\partial_\beta F^{\beta \mu} &= \partial_\beta(\partial^\beta A^\mu- \partial^\mu A^\beta) \\
&= \partial_\beta \partial^\beta A^\mu - \partial_\beta \partial^\mu A^\beta \\
&= \partial_\beta \partial^\beta A^\mu-\underbrace{\delta^\mu{}_\beta\, \partial_\beta \partial^\beta A^\beta}_{\delta^\mu{}_\beta\partial^\beta = \partial^\mu} \\
&=\partial_\beta\partial^\beta A^\mu -\delta^\mu{}_\beta\,\partial_\beta (\partial_\beta A^\beta)
\end{align*}
{% end %}

So we have:

{% math() %}
\partial_\beta\partial^\beta A^\mu -\delta^\mu{}_\beta\,\partial_\beta (\partial_\beta A^\beta) = J^\mu
{% end %}

Ah, but this is a very inelegant equation, with two terms and a clunky Kronecker delta in the middle! We would _much_ prefer being able to reduce this to one term. Luckily, there _is_ a way. $A^\mu$ is the _electromagnetic 4-potential_ after all. In physics, a potential must be defined with respect to _some reference point_ of zero potential energy. We can shift that reference point wherever we like, since we can only measure _energy differences_ in physics, so whether we define the surface of the Earth as our point of "zero potential" or somewhere a light-year away, it does not matter; the fields (and therefore the Faraday tensor) remains the same. This means that we can define our potential _such that_ as long as it doesn't change the Faraday tensor, our choice of definition doesn't matter. This is called **gauge invariance** and will be very important later on.

Now, it turns out that a brilliant physicist named [Ludvig Lorenz](https://en.wikipedia.org/wiki/Ludvig_Lorenz) (whose name unfortunately is often misspelled as "Lorentz", causing him to be confused with [another physicist of great fame](https://en.wikipedia.org/wiki/Hendrik_Lorentz)) figured out that if we define the 4-potential _such that_ $\partial_\beta A^\beta = 0$, the Faraday tensor remains the same. This is called the **Lorenz gauge condition** and means that our equation of motion for the $A^\mu$ field becomes:

{% math() %}
\partial_\beta\partial^\beta A^\mu -\delta^\mu{}_\beta\,\partial_\beta \cancel{(\partial_\beta A^\beta)}^0 = \partial_\beta \partial^\beta A^\mu = J^\mu
{% end %}

This equation, $\partial_\beta \partial^\beta A^\mu = J^\mu$, is the **alternate form of Maxwell's equations**. Using the d'Alembertian operator $\square = \partial_\beta \partial^\beta$ we can write this even more simply as $\square A^\mu = J^\mu$. Now _that_ is an elegant equation!

## Canonical quantization of the EM field

To quantized the electromagnetic field, we start with Maxwell's equations, $\square A^\nu = \partial_\mu \partial^\mu A^\nu = J^\nu$, just as we started with the Klein-Gordon equation, the equation of motion for the free scalar field. It's much easier to start with Maxwell's equations in _free space_, $\square A^\nu = 0$ (since there are no sources, $J^\nu = 0$). We will go into the case where $J^\nu \neq 0$ later when we explore the full theory of quantum electrodynamics, but we'll start by solving for the _free electromagnetic field_, which we'll then quantize.

Luckily for us, notice how Maxwell's equations in free space look very, very similar to the equation of motion for the free scalar field, which took the form $\partial_\mu \partial^\mu \phi + m^2 \phi = 0$. Indeed, if we set $m = 0$, then the Klein-Gordon equation reduces to $\partial_\mu \partial^\mu \phi = 0$, which looks near-identical to Maxwell's equations, with exception of being scalar-valued rather than vector-valued.

> **Why not the Faraday tensor form of Maxwell's equations?** The reason we use the version of Maxwell's equations for the $A^\nu$ field instead of the Faraday tensor $F^{\mu \nu}$ is that because of the laws of special relativity, the electric and magnetic field components of $F^{\mu \nu}$ switch upon a transformation of coordinates. Thus, the field tensor isn't a fundamental quantity, so it makes sense to quantized the much-more fundamental $A^\nu$ field.

This illuminates our way of solving Maxwell's equations. Let us first start by assuming that a solution must be in the form:

{% math() %}
A^\nu = \epsilon^\nu \phi
{% end %}

Where $\epsilon^\nu$ is a constant vector (called the **polarization**), and $\phi$ is a scalar-valued function. If we substitute this into Maxwell's equations, we find that it indeed satisfies Maxwell's equations in free space, and furthermore, that $\phi$ satisfies the Klein-Gordon equation:

{% math() %}
\begin{align*}
\partial_\mu \partial^\mu A^\nu &= \partial_\mu \partial^\mu (\epsilon^\nu \phi) \\
&= \epsilon^\nu\partial_\mu \partial^\mu \phi \\
&= 0 \rightarrow \partial_\mu \partial^\mu \phi = 0
\end{align*}
{% end %}

This gives us a shortcut solution, since we already know the general solution to the Klein-Gordon equation, which we wrote as a Fourier expansion:

{% math() %}
\phi(x^\mu) = \int \dfrac{d^3 p}{(2\pi)^32E_p} \left[a(p) e^{ip_\mu x^\mu} + a^*(p) e^{-ip_\mu x^\mu}\right] 
{% end %}

Thus, our solution to Maxwell's equation becomes:

{% math() %}
A^\nu = \epsilon^\nu \phi =\int \dfrac{d^3 p}{(2\pi)^32E_p}\left[\epsilon^\nu a(p) e^{ip_\mu x^\mu} + \epsilon^\nu a^*(p) e^{-ip_\mu x^\mu}\right]
{% end %}

Out of notational preference, we'll switch to the lower-index version of the field $A_\mu = \eta_{\mu \nu} A^\nu$, and write $a(p)$ as $a_p$ as well as {% inlmath() %}a^*(p){% end %} as {% inlmath() %}a^*_p{% end %}. The solution largely remains the same, with the only difference being that the polarization vector {% inlmath() %}\eta_{\mu \nu} \epsilon^\nu = \epsilon_\mu{% end %} must also shift to a lower index, thus giving us:

{% math() %}
A_\mu =\int \dfrac{d^3 p}{(2\pi)^32E_p}\left[\epsilon_\mu a_p e^{ip_\mu x^\mu} + \epsilon_\mu a^*_p e^{-ip_\mu x^\mu}\right]
{% end %}

Let's take a short moment to discuss the polarization vector $\epsilon_\mu$. Physically-speaking, the polarization vector represents the _orientation_ of the field vectors. It turns out that there are two possible orientations for the $A_\mu$ field, and thus two polarization vectors, which are, respectively:

{% math() %}
\begin{align*}
\epsilon_\mu^{(1)} = \begin{pmatrix} 0 \\ 1 \\ 0 \\ 0 \end{pmatrix}, \quad
\epsilon_\mu^{(2)} = \begin{pmatrix} 0 \\ 0 \\ 1 \\ 0 \end{pmatrix}
\end{align*}
{% end %}

> **Why only two polarizations?** We skip over this topic here so that we can focus on our main goal of quantizing the $A_\mu$ field, but [this Physics StackExchange answer](https://physics.stackexchange.com/questions/395284/why-does-each-mode-of-the-electromagnetic-field-have-two-degrees-of-freedom) offers an explanation for why.

Given the two polarizations, the most general solution to Maxwell's equations should be a superposition of both polarizations - so we write the solution as a sum of the two polarizations:

{% math() %}
A_\mu = \int\dfrac{d^3 p}{(2\pi)^3} \sum_{r = 1}^2\dfrac{1}{2E_p} \left(\epsilon^{(r)}_\mu a_p e^{ip_\mu x^\mu} + \epsilon_\mu^{(r)} a^*_p e^{-ip_\mu x^\mu}\right)
{% end %}

Given how similar the free electromagnetic field is to the free scalar field, we can essentially use the exact same procedure for quantization: $a_p$ and $a_p^*$ become the annihilation and creation operators $\hat a_p, \hat a_p^\dagger$ respectively. The only difference is due to polarization, which was absent for the free scalar field. Thus, we use the notations $\hat a_p^r$ and $\hat a_p^{r\dagger}$ to recognize that states of the electromagnetic field could have either one of the two polarizations. Thus, we have:

{% math() %}
\hat A_\mu = \int\dfrac{d^3 p}{(2\pi)^3} \sum_{r = 1}^2\dfrac{1}{2E_p} \left(\epsilon^{(r)}_\mu \hat a^r_p e^{ip_\mu x^\mu} + \epsilon_\mu^{(r)} \hat a^{r\dagger}_p e^{-ip_\mu x^\mu}\right)
{% end %}

The creation and annihilation operators for the two polarizations create or annihilate a particle in that particular polarization state, as follows:

{% math() %}
\begin{align*}
\hat a^{(1)}_p |0\rangle = 0,\quad  & \hat a^{(2)}_p|0\rangle = 0 \\
\hat a^{(1)\dagger}_p|0\rangle = |1^{(1)}\rangle, \quad &\hat a^{(2)\dagger}_p|0\rangle = |1^{(2)}\rangle
\end{align*}
{% end %}

Here, $|1^{(1)}\rangle$ is the first excited state in the $\epsilon_\mu^{(1)}$ polarization, while $|1^{(2)}\rangle$ is the first excited state in the $\epsilon_\mu^{(2)}$ polarization. Let us emphasize: these are _indices_, **not exponents**! This is why we write the numbers $(1), (2)$ in parentheses to avoid confusion with the similar notation of raising something to the power of one or two.

So we're done! We now have the quantized electromagnetic field $\hat A_\mu$, which is an operator, just like any other quantum field. And just as we saw that the field operator for a free scalar field $\hat \phi$ acting on the vacuum state $|0\rangle$ can be interpreted as creating a particle, $\hat A_\mu|0\rangle$ also has the interpretation of creating a particle. In particular, this particle is the familiar **photon**, which forms electromagnetic radiation that we perceive as **light**!

> **Note:** Since the photon is massless but has momentum, we have $E_p = p$ for the $\hat A_\mu$ field, instead of $E_p = \sqrt{p^2 + m^2}$ for the free scalar field. Here, be aware that $p = |\mathbf{p}|$, that is, the _magnitude_ of the momentum of the photon.

## Vacuum energy and the Casimir effect

Unlike classical fields, quantum fields have nonzero expectation values even when there is nothing "in" them. This is known as the **vacuum expectation value** (VEV), and it means that quantum fields have a nonzero energy even in their vacuum state.

To show this, let's again consider the free electromagnetic field $A_\mu$ (the field in the absence of sources, as it would be in vacuum). The field operator $\hat A_\mu$ would be given by:

{% math() %}
\hat A_\mu = \int\dfrac{d^3 p}{(2\pi)^3} \sum_{r = 1}^2\dfrac{1}{2E_p} \left(\epsilon^{(r)}_\mu \hat a^r_p e^{ip_\mu x^\mu} + \epsilon_\mu^{(r)} \hat a^{r\dagger}_p e^{-ip_\mu x^\mu}\right)
{% end %}

Let us recall that previously, for the free scalar field, we derived the Hamiltonian density operator to be:

{% math() %}
\hat{\mathcal{H}} = \dfrac{1}{2} \int \dfrac{d^3p\,E_p\,}{(2\pi)^3}(\hat a^\dagger_p \hat a_p + \hat a_p \hat a^\dagger_p)
{% end %}

The free electromagnetic field is _extremely similar_ - we need only replace $\hat a_p, \hat a_p^\dagger$ with $\hat a_p^r, \hat a^{r\dagger}_p$ to incorporate the polarizations of the field, and sum over the two possible polarizations.

{% math() %}
\hat{\mathcal{H}} = \dfrac{1}{2} \int \sum_{r = 1}^2 \dfrac{d^3p\,E_p\,}{(2\pi)^3}(\hat a^{r\dagger}_p \hat a_p^r + \hat a_p^r \hat a^{r\dagger}_p)
{% end %}

The **vacuum energy density** for the $A^\mu$ field is the expectation value of the Hamiltonian density for the vacuum state:

{% math() %}
\mathcal{E} = \langle 0 |\hat{\mathcal{H}}|0\rangle
{% end %}

Where we use the notation $\mathcal{E}$ to remind us that this is an energy _density_; the total energy is $\mathcal{E}$ integrated over all space. Let us now compute this vacuum energy density. A first simplification we can use is to ignore the polarization, since we know that the vacuum energy density ultimately evaluates to a scalar. Then, the sum of the two terms just reduces to:

{% math() %}
\begin{align*}
\hat{\mathcal{H}} = \dfrac{1}{2} \int 2\dfrac{d^3p\,E_p\,}{(2\pi)^3}(\hat a^{\dagger}_p \hat a_p + \hat a_p \hat a^{\dagger}_p)
\end{align*}
{% end %}

So we have:

{% math() %}
\begin{align*}
\langle 0|\hat{\mathcal{H}}|0\rangle &= \langle 0| \int \dfrac{d^3p\,E_p\,}{(2\pi)^3}\underbrace{(\hat a^{\dagger}_p \hat a_p + \hat a_p \hat a^{\dagger}_p) |0\rangle}_\text{distribute this} \\
% first step
&= \langle 0| \int \dfrac{d^3p\,E_p\,}{(2\pi)^3}(\underbrace{\hat a^{\dagger}_p \hat a_p|0\rangle}_{\hat a^{\dagger}_p \hat a_p|0\rangle = 0} + \underbrace{\hat a_p \hat a^{\dagger}_p|0\rangle}_{\hat a_p \hat a^{\dagger}_p|0\rangle = |0\rangle}) \\
&= \langle 0 | \int \dfrac{d^3p\,E_p\,}{(2\pi)^3} |0\rangle \\
&= \int \dfrac{d^3p\,E_p\,}{(2\pi)^3} \cancel{\langle 0|0\rangle}^1 \\
\end{align*}
{% end %}

In the Casimir effect, we consider grounded conducting plates of equal side lengths $L$. The plates are separated by a small distance $d$, where $L \gg d$ (this notation means "$L$ is much greater than $d$"). We show this in the diagram below:

{{ diagram(
src="../Casimir-effect.excalidraw.svg"
desc="A diagram of the Casimir effect"
) }}

Since the plates are _grounded conducting plates_, the electromagnetic 4-potential (classically) vanishes on both plates. Thus we have certain **boundary conditions** for $A^\mu(\mathbf{x}, t) = A^\mu(x, y, z, t)$, which are given by:

{% math() %}
\begin{align*}
A^\mu(x, y, 0, t) = A^\mu(x, y, d, t) = 0
\end{align*}
{% end %}

Where here, since nothing is changing in time, we just set $t = 0$. The basic solutions for Maxwell's equations $\partial_\nu \partial^\nu A^\mu = 0$ are just **plane waves** given by $A^\mu = e^{i(p_\nu x^\nu)} = e^{ip_\mu x^\mu}$ (again, since we set $t = 0$ we have $p_\nu x^\nu = p_\mu x^\mu$).

> **Note:** We derive this form of Maxwell's equations from the general form $\partial_\nu \partial^\nu A^\mu = J^\mu$, then setting $J^\mu = 0$ since we have no sources.

However, to satisfy the boundary conditions, our solution is restricted to a certain form. This form is given by:

{% math() %}
\begin{gather*}
A^\mu(\mathbf{x}, t) = \exp \left(i(p_x x + p_y y + p_z z)\right), \\
p_x = \dfrac{n_x \pi x}{L}, \quad p_y = \dfrac{n_y \pi y}{L}, \quad p_z = \dfrac{n_z \pi z}{d}
\end{gather*}
{% end %}

So if we substitute the energy-momentum relation for photons $E_p = |\mathbf{p}|$ (again, this comes from $E_p = pc$ which reduces to $E_p = p$ in natural units), we have:

{% math() %}
E_p = \sqrt{p_x^2 + p_y^2 + p_z^2}
{% end %}

Thus, using the result we derived before for $\mathcal{E}$, the vacuum energy density of the $A^\mu$ field would be given by:

{% math() %}
\begin{align*}
\mathcal{E} &= \langle 0|\hat{\mathcal{H}}|0\rangle \\
&=\int \dfrac{d^3p\,E_p\,}{(2\pi)^3} \\
&=\int \dfrac{d^3p}{(2\pi)^3}\sqrt{p_x^2 + p_y^2 + p_z^2} \\
\end{align*}
{% end %}

Except this is not _quite_ true. Since our allowable values of $p_x, p_y, p_z$ are restricted by our boundary conditions, we don't have a continuous sum anymore, so our integral technically needs to be replaced by a continuous sum. This means our previous expression becomes:

{% math() %}
\int \dfrac{d^3p}{(2\pi)^3}\sqrt{p_x^2 + p_y^2 + p_z^2} \Rightarrow \dfrac{1}{(2\pi)^3}\sum_{n_x=1}^\infty \sum_{n_y=1}^\infty \sum_{n_z=1}^\infty\sqrt{p_x^2 + p_y^2 + p_z^2}
{% end %}

In our case though, since $L \gg d$, we can _roughly say_ that $p_x$ and $p_y$ are *essentially* continuous. Let's break down this argument, since it may not be particularly obvious. $L \gg d$ essentially means that the area of the plates is much greater than the distance separating them. Thus, we get an effectively continuous distribution of momentum over them, so we can integrate over $p_x, p_y$, though we have to sum over $p_z$. Thus, we are left with:

{% math() %}
\langle 0 |\hat H|0\rangle= \int \dfrac{dp_x\, dp_y}{(2\pi)^2} \sum_{n = 1}^\infty\sqrt{p_x^2 + p_y^2 + \left(\dfrac{n\pi}{d}\right)^2}
{% end %}

Where we get rid of $dp_z/(2\pi)$ because we have converted it to a sum over the discrete values of $p_z$, but where we keep $dp_x, dp_y$ as continuous. This integral is not easy at all to evaluate, and the formal solution would require using contour integration in the complex plane. However, that is a math problem, not a physics problem, so we will focus on the physics and just give the solution:

{% math() %}
\mathcal{E} = \langle 0 |\hat H|0\rangle = -\dfrac{\pi^2}{720d^3}
{% end %}

Remember that this is the vacuum energy _density_; to get the vacuum energy $E_V$ we must integrate over the entire area $A = L^2$ of the plate, so we have:

{% math() %}
E_V = \int \left(-\dfrac{\pi^2}{720d^3}\right)\,dA = -\dfrac{\pi^2A}{720d^3}
{% end %}

The lower vacuum energy density in the region between the plates compared to that outside the region creates an _energy difference_, which leads to something akin to a force. The force is just the partial derivative of the energy with respect to distance, that is, $F = -\dfrac{\partial E_V}{\partial d}$, so we have:

{% math() %}
F = -\dfrac{\partial E_V}{\partial d} = -\dfrac{\pi^2 A}{240 d^4}
{% end %}

This is our result, though we should be careful to note that it is in *natural units*. If we restore the factors of $\hbar$ and $c$, we find that our result becomes:

{% math() %}
F = -\dfrac{\hbar c\pi^2 A}{240 d^4}
{% end %}

This attractive "force" (we know it's attractive because of the minus sign) is also called the **Casimir force**, although strictly speaking, it is not really a force, but rather a result of a difference in potential energy. The Casimir force is typically extremely weak. If we have two plates with $L = \pu{10 cm^2}$ separated by a distance of $\pu{3 \mu m}$, then the magnitude of the Casimir force pushing the plates together is roughly $\pu{1.606E-5 N}$, thus why it requires extremely sensitive equipment to detect. However, since it scales by $d^{-4}$, the Casimir force grows substantially as the plates are pushed ever closer together - when the plates at a smaller separation of $\pu{0.1 \mu m}$, its magnitude increases to $\pu{13 N}$, and if the plates are pushed even closer to just $\pu{0.01 \mu m} = \pu{10 nm}$, its magnitude increases to over $\pu{130 kN}$! However, it is experimentally difficult to place two conducting plates that close together, and in any case the theory may break down in such conditions, so this is purely theoretical (for now).
