+++
title = "Quantization of the electromagnetic field"
date = 2025-04-28
+++

The theory of classical electromagnetism is one of the most beautiful theories in physics, and also the jumping-off point to one of the earliest (and most successful) quantum field theories. It made the startling - but correct - prediction that all types of light were in fact _electromagnetic waves_ travelling at a fixed, universal speed $c$. We'll take our first steps into a "real" quantum field theory - the theory of **quantum electrodynamics** - from here.

## The Maxwell Lagrangian

Before we get to quantum electrodynamics, we need to first examine the classical theory it was built upon. The action for _classical_ electrodynamics is given by:

{% math() %}
S = \int d^4 x \left[-\dfrac{1}{4} F_{\mu \nu} F^{\mu \nu} + A_\mu J^\mu\right]
{% end %}

Where our Lagrangian (Lagrangian density, technically) is called the **Maxwell Lagrangian**, and is given by:

{% math() %}
\mathscr{L} = -\dfrac{1}{4} F_{\mu \nu} F^{\mu \nu} + A_\mu J^\mu
{% end %}

Here, $F_{\mu \nu}$ is the **Faraday tensor**, whose components are the electric and magnetic fields, as given by:

{% math() %}
F_{\mu \nu }=\partial_\mu A_\nu -\partial_\nu A_\mu =
\begin{bmatrix}
0 &E_{x} &E_{y} &E_{z}  \\
-E_{x} &0 &-B_{z}&B_{y} \\
-E_{y} &B_{z}&0 &-B_{x} \\
-E_{z} &-B_{y}&B_{x}&0
\end{bmatrix}
{% end %}

Meanwhile, $A_\mu$ is called the **electromagnetic four-potential**, which are (unsurprisingly) the potential associated with the electromagnetic field. Let's now derive the field equations for $A_\mu$, from which we can find the field equations for $F_{\mu \nu}$. For this, we use the Euler-Lagrange equations for $A_\mu$:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial A_\mu} - \partial_\beta\left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta A_\mu)}\right) = 0
{% end %}

> **Note:** In the Euler-Lagrange field equations, $A_\mu$ and $\partial_\beta$ must be **different indices** because the field is a _function_ of position, that is, $A_\mu = A_\mu(x^\beta)$. Thus, the field must be denoted with a different index compared to the position $x^\beta$ (after all, the $A_x$ component of the field is not just a function of $x$, nor is $A_y$ just a function of $y$!) 

But as soon as we start, uh-oh, we have a problem! The Lagrangian is written in terms of _both_ $F_{\mu \nu}$ and $A_\mu$, but we want to find the field equations for $A_\mu$ specifically. Therefore, we want to first expand the Lagrangian to be explicitly written in terms of $A_\mu$:

{% math() %}
\begin{align*}
% step 1
\mathscr{L} &= -\dfrac{1}{4} F_{\mu \nu} F^{\mu \nu} + A_\mu J^\mu \\
&= -\dfrac{1}{4} F_{\mu \nu} \, \underbrace{\eta^{\mu \alpha} \eta^{\nu \beta} F_{\alpha \beta}}_\text{lower indices} + A_\mu J^\mu \\
% step 2
&= -\dfrac{1}{4} \eta^{\mu \alpha} \eta^{\nu \beta}[F_{\mu \nu}F_{\alpha \beta}] + A_\mu J^\mu \\
% step 3
&= -\dfrac{1}{4} \eta^{\mu \alpha} \eta^{\nu \beta}\underbrace{(\partial_\mu A_\nu -\partial_\nu A_\mu)(\partial_\alpha A_\beta -\partial_\beta A_\alpha)}_\text{expand Faraday tensor} + A_\mu J^\mu \\
% step 4
&= -\dfrac{1}{4} \eta^{\mu \alpha} \eta^{\nu \beta}[(\partial_\mu A_\nu)(\partial_\alpha A_\beta) - (\partial_\mu A_\nu)(\partial_\beta A_\alpha) \\
&\qquad \quad - (\partial_\nu A_\mu)(\partial_\alpha A_\beta)+ (\partial_\nu A_\mu)(\partial_\beta A_\alpha)] + A_\mu J^\mu \\
\end{align*}
{% end %}

> **Tip:** Remember that we can raise and lower indices using the Minkowski metric for example $\eta^{\alpha \mu} A_\mu = A^\alpha$ and the Kronecker delta to relabel indices (but _not_ raise or lower indices), for example $\delta_\nu^\mu A^\nu = A^\mu$.

Let's recap what we did in the above calculation. First, since $F^{\mu \nu}$ is a contravariant tensor (meaning it has upper indices), we needed to rewrite it in lower indices. It's important to remember that $F_{\mu \nu} \neq F^{\mu \nu}$! So instead, we used the metric tensor (Minkowski metric) to lower indices - since $F^{\mu \nu} = \eta^{\mu \alpha} \eta^{\nu \beta} F_{\alpha \beta}$. Since the Minkowski metric is unrelated to $F_{\mu \nu}$ we can then factor it out, giving us an expression _completely in terms of_ $A_\mu$ with lower indices (different lower indices but all lower indices, at least). This then allows us to distribute, and if we do so, we get:

{% math() %}
\begin{align*}
% step 5
\mathscr{L} &= -\dfrac{1}{4}[\eta^{\mu \alpha} \eta^{\nu \beta}(\partial_\mu A_\nu)(\partial_\alpha A_\beta) - \eta^{\mu \alpha} \eta^{\nu \beta}(\partial_\mu A_\nu)(\partial_\beta A_\alpha) \\
&\qquad \quad - \eta^{\mu \alpha} \eta^{\nu \beta}(\partial_\nu A_\mu)(\partial_\alpha A_\beta)+ \eta^{\mu \alpha} \eta^{\nu \beta}(\partial_\nu A_\mu)(\partial_\beta A_\alpha)] + A_\mu J^\mu \\
% step 6
&= -\dfrac{1}{4}[\underbrace{\delta^\mu_\mu \delta_\nu^\nu\,(\partial^\alpha A^\beta)(\partial_\alpha A_\beta)}_\text{tensor contraction}- \delta^\mu_\mu \delta_\nu^\nu(\partial^\alpha A^\beta)(\partial_\beta A_\alpha) \\
&\qquad \quad - \delta^\mu_\mu \delta_\nu^\nu(\partial^\beta A^\alpha)(\partial_\alpha A_\beta) + \delta^\mu_\mu \delta_\nu^\nu(\partial^\beta A^\alpha)(\partial_\beta A_\alpha)] + A_\mu J^\mu \\
% step 7
&= -\dfrac{1}{4}\delta^\mu_\mu \delta^\nu_\nu[\underbrace{(\partial^\alpha A^\beta)(\partial_\alpha A_\beta)}_{\alpha, \beta \text{ are dummy indices}} + (\partial^\beta A^\alpha)(\partial_\beta A_\alpha) \\
&\qquad\quad - (\partial^\alpha A^\beta)(\partial_\beta A_\alpha) -(\partial^\beta A^\alpha)(\partial_\alpha A_\beta)] -A_\mu J^\mu \\
% step 8
&= -\dfrac{1}{4}\delta^\mu_\mu \delta^\nu_\nu[(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) + (\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) \\
% step 9
&\qquad \quad - (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma) - (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)] + A_\mu J^\mu \\
% step 10
&= -\dfrac{1}{4} \delta^\mu_\mu \delta^\nu_\nu [2(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) - 2(\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)] + A_\mu J^\mu \\
% step 11
&= -\dfrac{1}{2} \underbrace{\delta^\mu_\mu \delta^\nu_\nu\, \partial^\sigma A^\lambda}_{\partial^\sigma A^\lambda}
[\partial_\sigma A_\lambda - \partial_\lambda A_\sigma] + A_\mu J^\mu \\
&= -\dfrac{1}{2} \partial^\sigma A^\lambda [\partial_\sigma A_\lambda - \partial_\lambda A_\sigma] + A_\mu J^\mu
\end{align*}
{% end %}

In the second part of our calculation, we distributed the Minkowski metric $\eta^{\mu \alpha} \eta^{\nu \beta}$, which we had previously factored out, across every term. This gives us a bunch of Kronecker deltas, but we now have everything in terms of the same indices.

> **Note:** We could have avoided all the difficult tensor manipulations _if_ we knew beforehand the precise expression for $F^{\mu \nu}$. But since we _didn't_ know this beforehand, we had to use the Minkowski metric to lower the indices to find $F^{\mu \nu}$ in terms of $F_{\mu \nu}$.

Finally, using the fact that since repeated upper and lower indices are dummy indices (which we can rename to whatever indices we want), we can relabel them as anything we want. This means that for the first term $(\partial^\alpha A^\beta)(\partial_\alpha A_\beta)$, we can relabel with $\alpha \to \sigma, \beta \to \lambda$, giving us $(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda)$ as the relabelled (but completely equivalent) expression. Meanwhile, for the second term$(\partial^\beta A^\alpha)(\partial_\beta A_\alpha)$ we can relabel with $\alpha \to \lambda, \beta \to \sigma$ (again, the indices we choose to relabel with _do not matter_), which gives us the relabelled expression $(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda)$. This allows us to collect like terms together, much simplifying the expression for the Lagrangian. We also did the same for $A_\mu J^\mu$ - since we have repeated upper and lower indices, we may freely choose $\mu \to \sigma$ (although again we could've picked _any_ other index; indeed, we could've chosen $\mu \to \lambda$ if we so wanted). In the last step, we made the simplification $\delta^\mu_\mu \delta^\nu_\nu\, \partial^\sigma A^\lambda = \partial^\sigma A^\lambda$: since $\delta^\mu_\mu = \delta^\nu_\nu = I^4$ (the 4D identity matrix), the tensor product of the Kronecker delta with $\partial^\sigma A^\lambda$ just returns $\partial^\sigma A^\lambda$ itself.

Phew, that was a lot! Now, we can _finally_ find the equations of motion. Remember the Euler-Lagrange equation for $A_\mu$ is given by:

{% math() %}
\dfrac{\partial \mathscr{L}}{\partial A_\mu} - \partial_\beta\left(\dfrac{\partial \mathscr{L}}{\partial(\partial_\beta A_\mu)}\right) = 0
{% end %}

Let us now take the partial derivatives of the Lagrangian, which we perform step-by-step below:

{% math() %}
\begin{align*}
\mathscr{L} &= -\dfrac{1}{2} \partial^\sigma A^\lambda [\partial_\sigma A_\lambda - \partial_\lambda A_\sigma] + A_\mu J^\mu \\
&= -\dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) + \dfrac{1}{2} (\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma) + A_\mu J^\mu \\
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

We now have two terms to differentiate, $(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda)$ and $(\partial^\sigma A^\lambda)(\partial_\lambda A_\sigma)$. We'll differentiate them one by one. Starting with the first term, we have:

{% math() %}
\begin{align*}
\dfrac{\partial}{\partial(\partial_\beta A_\mu)}(\partial^\sigma A^\lambda)(\partial_\sigma A_\lambda) &= \underbrace{(\partial_\sigma A_\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}(\partial^\sigma A^\lambda) + (\partial^\sigma A^\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}(\partial_\sigma A_\lambda)}_\text{expanded using the product rule} \\
&= (\partial_\sigma A_\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}\underbrace{(\eta^{\mu \sigma} \eta^{\beta \lambda}\partial_\mu A_\beta)}_\text{lower indices} + (\partial^\sigma A^\lambda)\dfrac{\partial}{\partial(\partial_\beta A_\mu)}\underbrace{(\delta^\mu{}_\sigma \delta^\beta{}_\lambda \partial_\mu A_\beta)}_\text{relabel indices} \\
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
&= 0 \text{ if }\partial_\mu \partial^\mu \phi = 0
\end{align*}
{% end %}

This gives us a shortcut solution, since we already know the general solution to the Klein-Gordon equation, which we wrote as a Fourier expansion:

{% math() %}
\phi(x^\mu) = \int \dfrac{d^3 p}{(2\pi)^32E_p} \left[a(p) e^{i\mathbf{p} \cdot \mathbf{x}} + a^*(p) e^{-i\mathbf{p} \cdot \mathbf{x}}\right] 
{% end %}

Thus, our solution to Maxwell's equation becomes:

{% math() %}
A^\nu = \epsilon^\nu \phi =\int \dfrac{d^3 p}{(2\pi)^32E_p}\left[\epsilon^\nu a(p) e^{i\mathbf{p} \cdot \mathbf{x}} + \epsilon^\nu a^*(p) e^{-i\mathbf{p} \cdot \mathbf{x}}\right]
{% end %}

Out of notational preference, we'll switch to the lower-index version of the field $A_\mu = \eta_{\mu \nu} A^\nu$, and write $a(p)$ as $a_p$ as well as $a^*(p)$ as $a^*_p$. The solution largely remains the same, with the only difference being that the polarization vector $\eta_{\mu \nu} \epsilon^\nu = \epsilon_\mu$ must also shift to a lower index, thus giving us:

{% math() %}
A_\mu =\int \dfrac{d^3 p}{(2\pi)^32E_p}\left[\epsilon_\mu a_p e^{i\mathbf{p} \cdot \mathbf{x}} + \epsilon_\mu a^*_p e^{-i\mathbf{p} \cdot \mathbf{x}}\right]
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
A_\mu = \int\dfrac{d^3 p}{(2\pi)^3} \sum_{r = 1}^2\dfrac{1}{2E_p} \left(\epsilon^{(r)}_\mu a_p e^{i\mathbf{p} \cdot \mathbf{x}} + \epsilon_\mu^{(r)} a^*_p e^{-i\mathbf{p} \cdot \mathbf{x}}\right)
{% end %}

Given how similar the free electromagnetic field is to the free scalar field, we can essentially use the exact same procedure for quantization: $a_p$ and $a_p^*$ become the annihilation and creation operators $\hat a_p, \hat a_p^\dagger$ respectively. The only difference is due to polarization, which was absent for the free scalar field. Thus, we use the notations $\hat a_p^r$ and $\hat a_p^{r\dagger}$ to recognize that states of the electromagnetic field could have either one of the two polarizations. Thus, we have:

{% math() %}
\hat A_\mu = \int\dfrac{d^3 p}{(2\pi)^3} \sum_{r = 1}^2\dfrac{1}{2E_p} \left(\epsilon^{(r)}_\mu \hat a^r_p e^{i\mathbf{p} \cdot \mathbf{x}} + \epsilon_\mu^{(r)} \hat a^{r\dagger}_p e^{-i\mathbf{p} \cdot \mathbf{x}}\right)
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
\hat A_\mu = \int\dfrac{d^3 p}{(2\pi)^3} \sum_{r = 1}^2\dfrac{1}{2E_p} \left(\epsilon^{(r)}_\mu \hat a^r_p e^{i\mathbf{p} \cdot \mathbf{x}} + \epsilon_\mu^{(r)} \hat a^{r\dagger}_p e^{-i\mathbf{p} \cdot \mathbf{x}}\right)
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

Where here, since nothing is changing in time, we just set $t = 0$. The basic solutions for Maxwell's equations $\partial_\nu \partial^\nu A^\mu = 0$ are just **plane waves** given by $A^\mu = e^{i(p_\nu x^\nu)} = e^{i\mathbf{p} \cdot \mathbf{x}}$ (again, since we set $t = 0$ we have $p_\nu x^\nu = \mathbf{p} \cdot \mathbf{x}$).

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