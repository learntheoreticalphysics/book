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

After a rather horrendous amount of math, we have therefore derived the essential equation of classical electrodynamics - **Maxwell's equations**, given by $\partial_\beta F^{\beta \mu} = J^\mu$. Note that if we so wished, we could also express Maxwell's equations purely in terms of $A^\mu$ as follows:

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