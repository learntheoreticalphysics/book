+++
title = "Getting started with quantum field theory"
date = 2025-04-27
+++

## The very basics of quantum field theory

Quantum field theory resolves a fundamental question at the heart of physics: the problem of **wave-particle duality**. This is the phenomenon where electrons, photons, and other quantum particles can behave like classical waves in some scenarios, while behaving like classical particles in some scenarios. For instance, light was classically-understood as an **electromagnetic wave**, and the prevelance of modern radio antennas, Wi-Fi, and telecommunications, all technologies founded on the wave theory of light, would suggest that this is a pretty successful theory! However, precision experiments at the turn of the 20th century also found that light could behave like a particle. Shining light on a metal plate, for instance, could "knock out" electrons in the plate (the [photoelectric effect](https://en.wikipedia.org/wiki/Photoelectric_effect)), and X-rays aimed at a graphite sample would become deflected as they passed out of the sample ([Compton scattering](https://en.wikipedia.org/wiki/Compton_scattering)). The wave theory of light predicted some aspects of the behavior of light fantastically, yet failed to predict all of these particle-like phenomena, while the particle theory of light (as developed by physicists such as Einstein and Planck) could explain the particle-like phenomena, but _not_ the wave-like phenomena. The mystery remained even more elusive for other quantum particles like electrons and protons, which _also_ exhibited these perplexing properties.

Quantum field theory resolves this mystery with a surprising conclusion: the fundamental entities of the Universe are _not_ waves or particles, but **quantum fields**. A quantum field is the quantum extension of a _classical field_ such as the electromagnetic and gravitational fields. Just like classical fields, quantum fields describe quantities that are spread throughout all space and carry interactions ("forces" in classical physics) between particles. There is, however, one very big difference: quantum fields can only come in certain **states**. Each state corresponds to a specific oscillation of the quantum field, and those oscillations (also called _modes_) are what we call particles! Furthermore, quantum field theory predicts that all particle-particle interactions are actually just interacting quantum fields, which transfer energy and momentum with each other, leading to the _creation_ and _annihilation_ of particles!

The consequencies of quantum field theory are profound. Quantum field theory introduces a Universe that is fundamentally not static, where particles can be created from pure energy in quantum fields, and where even a perfect vacuum still has a nonzero energy! In fact, this is just the beginning: we'll eventually find out that _most_ of the energy in the Universe is actually contained in quantum fields, as opposed to the rest mass of actual particles: [more than 99%](https://en.wikipedia.org/wiki/Conformal_anomaly#Quantum_chromodynamics) of the mass of all matter in the Universe comes from the quantum fields inside and around it! Even what we regard as "forces" _actually_ come from quantum fields exchanging particles, so it is safe to say that at a fundamental level, at least as far as we understand, quantum fields make up everything in the Universe, and are responsible for **all** matter interactions. Without further ado, let's begin on this exciting learning journey!

### The motivation for quantum field theory

As far as we know, all matter and radiation in the Universe is quantum in nature. Quantum mechanics governs the behavior of all matter, and has been a _massively_ successful theory that has made countless successful predictions. Quantum field theory is our most _accurate_ formulation of quantum mechanics, but is not typically taught when introducing the subject. (This is not without reason, as experience has shown that starting with quantum field theory, with its integrals requiring pages-long contour integration, typically leads to long-term physics paranoia). Instead, at an introductory and intermediate level, the dynamics of quantum systems is typically analyzed with the Schrödinger equation:

{% math() %}
i\hbar \dfrac{\partial}{\partial t} \Psi(\mathbf{r}, t) = \left(-\dfrac{\hbar^2}{2m} \nabla^2 + V(\mathbf{r})\right) \Psi(\mathbf{r}, t)
{% end %}

> **Note:** It's okay if you don't know that this equation says or means! We'll go through all of the prerequisite quantum mechanics shortly.

The advantage of this simpler approach is that it makes reasonably-accurate predictions for simple quantum systems. However, it is not compatible with special relativity (which is important for quantum particles, since they often travel at close to or _exactly_ the speed of light), and moreover, describing quantum systems with many particles becomes extremely tedious. Quantum field theory, or more precisely _relativistic_ quantum field theory, is a far more accurate theory of quantum mechanics than the Schrödinger equation. In fact, while we may use approximations like (semi-)classical theory and nonrelativistic or single-particle quantum mechanics, quantum field theory, and specifically the Standard Model, offers the best and most accurate results. 

That is to say, any quantum system may be solved for by the Schrödinger equation, but doing the same calculations with quantum field theory offers results with unparalleled precision. Predictions of the [magnetic moment of electrons](https://en.wikipedia.org/wiki/Magnetic_moment), [energy levels of the hydrogen atom](https://en.wikipedia.org/wiki/Lamb_shift), a variety of [previously-unknown elementary particles](https://physics.info/standard/), and the [Rydberg constant](https://en.wikipedia.org/wiki/Rydberg_constant) made through quantum field theory have been experimentally tested and confirmed very well.

These are not meaningless predictions either; our understanding of the emission and absorption of light, of the subatomic origins of magnetism, and even our standard of time in the [definition of a second](https://en.wikipedia.org/wiki/Second) are based on these predictions. In turn, numerous scientific experiments, material science, laser technology, and electronics depend on applying these predictions, without which they would likely not progress to how they are today.

### Things to know

We'll be working with natural units where we set two natural constants (the [speed of light](https://en.wikipedia.org/wiki/Speed_of_light) $c$ and the [reduced Planck constant](https://en.wikipedia.org/wiki/Planck_constant) $\hbar = h/2\pi$) to have a value of 1: this simplifies a lot of equations and makes the mathematics a lot easier. For instance, as we'll see, Einstein's energy-momentum relation, which is normally given by:

{% math() %}
E^2 = (pc)^2 + (mc^2)^2
{% end %}

becomes the much simpler and prettier-looking expression:

{% math() %}
E^2 = p^2 + m^2
{% end %}

> **Note:** You can think of this as _redefining_ time and length to use the same unit, as well as redefining momentum, energy, and mass to use the same unit. As we'll soon see, at a fundamental level, time and length _are_ actually the same thing (likewise, mass and energy are the same thing), although we assign different names and units to them. By removing this artificial restriction, we end up with *natural units*, since these are the units that are only based off _physical quantities_ in the Universe.

However, since we have now made both $c$ and $\hbar$ hidden, we have to adjust _all_ of the rest of our units as a result. This means that after we finish our calculations, we must convert back to the SI unit system (which is standard in the rest of physics) by multiplying by appropriate factors of $\hbar$ and $c$. This is a bit of a convoluted process, so it is helpful to refer to tables that give the appropriate multiplicative factors, such as [this PDF of tables](https://www.seas.upenn.edu/%7Eamyers/NaturalUnits.pdf) (which is where the below table comes from). The idea is that if you have an expression in **natural units** that has units of **energy** ($E$), the appropriate conversions are as follows:

| If our expression should have SI units of... | Convert with... |
|--------------|-------------|
| Length ($L$) | $L = \hbar c/E$ |
| Area ($A$) | $A = (\hbar c/E)^2$ |
| Mass ($m$) | $m = E/c^2$ |
| Time ($t$) | $t = \hbar/E$ |
| Energy ($E$) | $E = E$ |
| Momentum ($p$) | $p = E/c$ |
| Acceleration ($a$) | $a = Ec/\hbar$ |
| Frequency ($\omega$) | $\omega = E/\hbar$ |

What if our expression (let's call it $Q$) doesn't have units of energy in natural units? Well, we can *convert* an expression in natural units to units of energy by multiplying by the following factors:

| Expression ($Q$) has natural units of... | Convert to units of energy with a factor of... |
|--------------|-------------|
| Mass | $E = Qc^2$ |
| Energy | $E = Q$ |
| Momentum | $E = Qc$ |
| Length | $E = \hbar c/Q$ |
| Time | $E = \hbar/Q$ |

> **Note:** Dimensionless expressions in natural units can be converted to SI by multiplying by $c$ (for velocity) or $\hbar$ (for action/angular momentum).

Afterwards, we can just use the first table to convert dimensions of energy into our desired SI unit. We can then compose other units by multiplying these together - for instance, velocity is simply length over time, so we divide the corresponding conversion factors of length by time. This may all sound super confusing, so let's practice with an example. Consider the formula for the **Compton wavelength** $\lambda_c$, which is very important in quantum field theory. In standard SI units, it takes the form:

{% math() %}
\lambda_c = \dfrac{2\pi \hbar}{mc}
{% end %}

In natural units, where we set $\hbar = c = 1$, it instead takes the form:

{% math() %}
\lambda_c = \dfrac{2\pi}{m}
{% end %}

This equation has dimensions of _inverse mass_ in natural units. To convert back to SI units, we use a two-step process.

- First, we convert our expression in natural units to equivalent units of energy by replacing $m$ with $mc^2$ (according to $E = Qc^2$ in the second table). Thus, our expression becomes $\lambda_c = \dfrac{2\pi}{mc^2}$ and has dimensions of inverse energy.
- Then, we convert energy to wavelength (which has units of length) by multiplying by $\hbar c$ (according to $L = \hbar c/E$ in the second table, which we can rearrange to $L = \hbar c E^{-1}$). This gives us $\lambda_c = \dfrac{2\pi}{mc^2} \hbar c = \dfrac{2\pi \hbar}{mc} = \dfrac{h}{mc}$, which is indeed our expected result in SI units.

> **Note for the advanced reader:** Also, instead of standard vectors, almost everything will use _tensors_. We will be working in the formalism of Lagrangian and Hamiltonian field theory, as is standard in theoretical physics. Don't worry if some of these topics are unfamiliar; we will review all of these topics before we begin, and consult the other free books on this site for more information.

## An overview of classical field theory

Before we get started with the complex quantum
field theories of the Standard Model, we must look at their shared
fundamental structure in *classical field theory*. A classical field
theory describes a *field*, which can be thought of as a physical
quantity that fills all of space and allows interactions between
particles to propagate between each other, leading to what we perceive
as "force".

The nebulous idea of a field can be more easily quantified by
considering the following example: you stand in a room that has varying
temperature. The temperature changes depending on where you are in the
room (a physicist would call that *position dependence*), and the
temperature also changes over time (in the language of physics, *time
dependence*). Thus, if we let $\vec x = \langle x, y, z\rangle$ denote
the position in the room and $t$ denote the time, we can write the
temperature field, represented as $\phi$, with:

{% math() %}\phi(\vec x, t){% end %}

Our modern formulation of classical field theory is that of the
**Lagrangian and Hamiltonian formulation** of classical fields. Such a
formulation begins by describing a field in terms of a specific function
of the field, called a **Lagrangian** , and written as
$\mathscr{L}(\phi, \vec x, t)$, where, again, $\phi$ is a function of
$\vec x$ and $t$, that is, position and time. (Technically speaking, the
more accurate term for fields is to use the term *Lagrangian density*,
but we will use an abuse of terminology and simply call the Lagrangian
density \"the Lagrangian\".)

The precise form of the Lagrangian depends highly on which exact field
we are studying. But if we want our theories to \"make sense\" in the
physical world, it must satisfy the following constraints:

1.  Any derivatives of the field that appear in the Lagrangian can be at
    most *first derivatives*. That is, we can have
    $\dfrac{\partial \phi}{\partial x}$ or $(\nabla \phi)^2$ as terms in
    the Lagrangian, but **not** $\nabla^2 \phi$ as that would be
    second-order. This is because we do not observe physical fields
    satisfying partial differential equations (PDEs) that include
    anything above a second-order derivative, and the process we will
    soon see to determine the PDEs of the fields always raises the order
    of the derivatives by one.

2.  It must be a function of *individual positions* in space. Thus, the
    Lagrangian cannot have a term that depends on two positions
    $\vec x_1, \vec x_2$. This ensures that the field does not violate
    *locality* (the fact that information propagates at a finite speed
    and, therefore, information transfer cannot be instantaneous).

3.  It must be scalar-valued and have units of *energy*, and we will see
    why soon.

There are further restrictions on the specific form of the Lagrangian of
a field based on the specific **symmetries** that we want the Lagrangian
(and thus our theory) to obey. For instance, if we want our theory to
have *translational symmetry* (symmetric in position), then the
Lagrangian **cannot** contain any terms that would lead to
$\mathscr{L}(\phi(\vec x + \vec \epsilon), \vec x + \vec \epsilon, t) \neq \mathscr{L}(\phi(\vec x, \vec t))$,
where $\vec \epsilon$ is some shift in position. We may impose further
restrictions by requiring, for instance, that the Lagrangian respects
**rotational symmetry** or symmetry upon \"flipping\" the field (which
is the transformation $\phi(\vec x, t) \to \phi(-\vec x, t)$). These
symmetries are desirable because a famous theorem known as **Noether's
theorem** says that certain symmetries lead to *conservation laws*, such
as the conservation of energy, momentum, and charge, which are
fundamental laws of nature. We will also encounter a specific type of
symmetry later on called **Lorentz symmetry** that imposes even stricter
conditions on the form the Lagrangian can take. In practice, the
combination of symmetries may often be so restrictive that there are
only a few possibilities for a field's Lagrangian that can satisfy all
the symmetries. But there is no absolute rule for finding the right
Lagrangian; even though we can often narrow down the Lagrangian into a
much simpler form, the specific Lagrangian that \"wins out\" in the end
is the one that leads to a theory that makes successful predictions,
verified by experiments. Physics, is ultimately an *empirical science*,
and the source of truth within theoretical physics, just like all other
branches of physics, is *consistency with observation*.

### The Principle of Stationary Action

Upon defining a Lagrangian, we can then write out a quantity known as
the **action**. The action $S$ is defined as:

{% math() %}S = \int \limits_\text{space+time} \mathscr{L}(\phi(\vec x, t), \vec x, t)\, d^4 x{% end %}

Where {% inlmath() %}d^4 x = dx\, dy\, dz\, dt{% end %}, and the integral is conducted over
all space and all times. Why define this quantity? Because it turns out
that the correct partial differential equation to describe the field
$\phi(\vec x, t)$ is the one that makes the action *stationary*.
Stationary is a concept that comes from calculus; for the action, it
means that rate of change of the action with respect to change in $\phi$
must be zero, which we write as:

{% math() %}\delta S = 0{% end %}

This requirement for the action being stationary is (unsurprisingly)
called the **Principle of Stationary Action**. It is also sometimes
called the Principle of *Least* Action, although the action may not
always be a minimum, so that alternate term can be misleading. It turns
out (we will not show here as it is a rather involved derivation) that
this means that the Lagrangian must satisfy the following tensor partial
differential equation:

{% math() %}\frac{\partial \mathscr{L}}{\partial \phi} - \partial_\mu \left(\frac{\partial \mathscr{L}}{\partial (\partial_\mu \phi)}\right) = 0{% end %}

> **Note:** It's okay to not understand what this equation means yet. We'll cover tensors in more detail shortly.

This partial differential equation (PDE) is called the **Euler-Lagrange
Equation** for fields and always gives the correct PDE for the field. We
refer to this PDE as the **equation of motion** of the field, as it
describes how the field evolves through time and changes in space.
Solving the PDE (with suitable boundary conditions) allows us to find
the field as a function of position and time.

Rather incredibly, the basic mathematics and structure of classical
theories of fields carry over even to domains where classical mechanics
no longer holds - including the relativistic and quantum domains. This
is why it remains an important area of study over 200 years since its
inception.

## An overview of tensors

Tensors are some of the most elegant ways to write the laws of physics, used extensively in relativistic mechanics and relativistic quantum theory. However, they can be quite complicated to read and understand, so we will go over them here.

### What is a tensor?

A tensor is a general name for a class of coordinate-independent objects. A scalar is a tensor, so is a vector, a matrix, and anything made of a combination of these. Whether we use spherical or cylindrical or cartesian coordinates, after all, the air temperature (a scalar field) doesn't change, the wind current velocity (a vector field) doesn't change, and the rotation of baseball hurtling towards me (a transformation matrix) also doesn't change. These are all examples of a general principle:

> The universe just doesn't care what coordinates we use to measure it. Coordinates are human constructs, not a fundamental fact of nature.

However, when we impose a coordinate system to write out the equations of physics, we fix the values of the components. So a vector might be the same physical thing regardless of coordinate system, but its _components_ are different in different coordinates. This can be an annoying issue: equations that might look simple in cartesian coordinates can grow monstrously annoying to read in, for instance, spherical coordinates. For example, this is Laplace's equation, often used for modelling gravity in a vacuum, in cartesian coordinates:

{% math() %}
\nabla^2 f = 0
{% end %}

And this is its equivalent in spherical coordinates:


{% math() %}
{\frac {1}{r^{2}}}{\frac {\partial }{\partial r}}\left(r^{2}{\frac {\partial f}{\partial r}}\right)+{\frac {1}{r^{2}\sin \theta }}{\frac {\partial }{\partial \theta }}\left(\sin \theta {\frac {\partial f}{\partial \theta }}\right)+{\frac {1}{r^{2}\sin ^{2}\theta }}{\frac {\partial ^{2}f}{\partial \varphi ^{2}}} = 0
{% end %}

With a change of coordinates, equations that looked elegant and easy to work with become clunky and untractable. What if there were a way to formulate physics in a way that doesn't depend on coordinates, and where we could use whichever coordinates we wished? This is where tensors come in. The tensor formulation of the same equation is given by:

{% math() %}
\dfrac{1}{\sqrt{g}} \partial_i(\sqrt{g} g^{ij} \partial_j) f = 0, \quad g=\det(g_{ij})
{% end %}

How amazingly simple and graceful! _This_ is why we use tensors.

### Tensor algebra and calculus

To use tensors, it's helpful to start from our familiar vector and matrix formulas and build up from there.

For instance, consider a vector in Euclidean 3D space. Written in terms of a Cartesian basis, it is given by:

{% math() %}
\vec V = V_x \hat e_x + V_y \hat e_y + V_z \hat e_z
{% end %}

It is common convention when writing tensors to write the components of vectors with superscript (upstairs) indices and their basis vectors with subscript (downstairs) indices. The reason will become apparent later, consider this just a convention for now. So we can rewrite as:

{% math() %}
\vec V = V^x \hat e_x + V^y \hat e_y + V^z \hat e_z
{% end %}

If we set $x = 1, y = 2, z = 3$ we can equivalently write using _index_ notation:

{% math() %}
\vec V = V^1 \hat e_1 + V^2 \hat e_2 + V^3 \hat e_3 = \sum_{i = 1}^3 V^i \hat e_i
{% end %}

So a vector can be written in tensor form with:

{% math() %}
\hat V = \sum_{i = 1}^3 V^i \hat e_i
{% end %}

When writing tensors, it is common practice to omit the summation sign; as long as the reader is aware that you are using tensors and that the summation is there even if it's not written out, the conveyed meaning remains the same, but the notation becomes much more compact:

{% math() %}
\hat V = V^i \hat e_i
{% end %}

In a similar fashion, the dot product formula expressed using tensors can be written as:

{% math() %}
S = A^i B_i
{% end %}

### Upper and lower indices

To be able to discuss tensors further, however, we must introduce two concepts: that of a **co-vector**, and of the **metric**. A co-vector is like a row vector in Cartesian coordinates. Remember that a row vector and a column vector create a scalar through their dot product:

{% math() %}
\begin{bmatrix} a_1 & b_1 & c_1 \end{bmatrix}
\begin{bmatrix} a_2 \\ b_2 \\ c_2 \end{bmatrix} 
= a_1 a_2 + b_1 b_2 + c_1 c_2
{% end %}

A **co-vector** is the generalization of the idea of a row vector. We denote co-vectors with a subscript, such as $\vec V^T = V_i$ ($T$ here means "transpose" since a row vector is the transpose of a column vector). By contrast, we denote **vectors** with a superscript, such as $\vec W = W^j$.

For instance, consider the position vector $\vec x = x^i$, where the index $i$ indexes over the 3 coordinates of the position $(x^1, x^2, x^3) = (x, y, z)$. Because the position vector is a vector, and vectors are tensors, the position vector is _also_ a tensor.

Now, the index of a tensor represents its _components_. This is important because two tensors with the same index have _different_ components. For instance, we may have two tensors $\vec x = x^i$ and $\vec x' = x^j$, where the prime mark ($'$) indicates different coordinates. That is:

{% math() %}
x^i = \begin{bmatrix} x \\ y \\ z \end{bmatrix}, \quad
x^j = \begin{bmatrix} x' \\ y' \\ z' \end{bmatrix}
{% end %}

This is important in tensor calculus, as it allows us to write tensors that have different components without needing to write a bunch of primed marks.

Just as we can for any vector, we can write the position _co-vector_ $\vec x^T$ in tensor notation as $x_i$, and $\vec x^T$ as $x_j$. Therefore, we have:

{% math() %}
x_i = \begin{bmatrix} x & y & z \end{bmatrix}, \quad
x_j = \begin{bmatrix} x' & y' & z' \end{bmatrix}
{% end %}

This gives us the ability to write out the dot product formula (which we just saw earlier) in tensor notation as:

{% math() %}
\sum_i x_i x^i = x^2 + y^2 + z^2 = R^2
{% end %}

Where here, $R^2$ is the **squared magnitude** of the position vector, and is thus a **scalar**. Note that the expression $x_i x^j$ is _not_ a valid expression for the dot product, because it would evaluate to:

{% math() %}
\sum_i x_i x^i = xx' + y y' + zz' \neq x_i x^i
{% end %}

So it is important that we specify a tensor's index carefully so that **tensors with different components have different indices**, even if they are the same type of tensor. As we saw, a position vector $\vec x = x^i$ and a position vector with different components $\vec x' = x^j$ are both position vectors, but since they have **different components**, they must use **different tensor indices**.

### Free indices, dummy indices, and the Einstein summation convention

After working with tensors for a while, it often becomes increasingly annoying to write out summation signs. For instance, recall our expression for the dot product:

{% math() %}
\mathbf{A} \cdot \mathbf{B} = \sum_i A_i B^i
{% end %}

While this may not look so bad, consider taking the product of like-index components of two matrices. Then we would have:

{% math() %}
AB = \sum_i \sum_j A_{ij} B^{ij}
{% end %}

But there are even higher-dimensional tensors, which means that we may encounter expressions in the form:

{% math() %}
\sum_i \sum_j \sum_k A_{ijk} B^{ijk}
{% end %}

At this point, writing any more summation signs becomes a hassle. So instead, we often _drop_ the summation signs, with the understanding that the summation signs are there, just not explicitly written-out. For instance, the dot product formula would just read $A_i B^i$, where we implicitly sum over $i$. This is called the **Einstein summation convention**.

The _Einstein summation convention_ says that whenever an index appears once as a lower index and once as an upper index in a particular tensor expression, then the index is **summed over**. When this happens, we say that the twice-appearing index is a **dummy index** (also called a **summation index**), and we can choose to _freely change_ the index's letter to any other letter. For instance, since the dot product in tensor notation has $i$ appearing twice - once as an upper index, and once as a lower index - we can change the index letter $i$ to any other letter, so the following are **all equivalent**:

{% math() %}
x_i x^i = x_k x^k = x_r x^r = x_\delta x^\delta
{% end %}

A difference, however, is if we had an expression in the form $x_i x^j$. Since these are **not** a set of indentical upper and lower indices, they are **not implicitly summed over**. Thus, we say that they are **free indices**.

The key part of tensor algebra is that we must _keep track of our indices_ such that all our equations have *balanced indices*. This means that the **total number of free indices** on both sides of an equation must be the **same**. Consider, for instance, the following expression:

{% math() %}
R_{ij} = C_i B_j
{% end %}

Is this expression valid? Let's check the number of free indices. On the left, both $i, j$ are free indices, since neither appears twice (in an upper and lower index) in the expression. On the right, we also have two free indices, and they are the _same_ free indices. So indeed, this tensor expression is valid. Note that if we changed this expression to:

{% math() %}
R^i{}_j = C_i B^i
{% end %}

Then this expression would no longer be correct! On the left, we have the same two _free_ indices $i, j$, but on the right, the index $i$ appears both as a lower and an upper index, so it is a _dummy index_, not a free index.

Let's examine a third case:

{% math() %}
V_{ij} = q_i q^j e^k e_k
{% end %}

Would _this_ expression be valid? If we check the left and right-hand sides, we find that both sides have two free indices - since $k$ appears as an upper and lower index in $e^k e_k$, it is a dummy index and doesn't count. But we now have a new problem: the index $j$ is a lower index on the left, and an _upper index_ on the right! So this expression is _invalid_. But we could correct it by rewriting the expression with $j$ as a _lower index_:

{% math() %}
V_{ij} = q_i q_j e^k e_k
{% end %}

Note that because $k$ is a dummy index, by the Einstein summation convention, we could change $k$ to any letter we want. Thus, it would be equally valid to write:

{% math() %}
V_{ij} = q_i q_j e^\beta e_\beta
{% end %}

As a summary, tensors have two types of indices: **free indices** and **dummy (summation) indices**. Free indices _must_ be balanced on the left- and right-hand sides of an equation, but dummy indices can be changed at will. This delicate balancing act - of making sure that all tensor equations have the same number of free indices - is the basis of tensor algebra, and as we'll see, tensor calculus. It makes sure that all our operations are mathematically valid, and lets us just concentrate on the physics without ever needing to think about the complex linear algebra that underlies all our operations.

### Relabeling indices with the Kronecker delta

Previously, we've learned that indices are _fundamental_ to tensors, and they are what distinguish tensors with different components. For instance, $x^i \neq x^j$, even though they are both position vectors, and the difference in index tells us that they have _different components_. Furthermore, since $i$ appears only one time in $x^i$, it is a **free index** - the same is true for $j$ in $x^j$. Thus, the tensor equation $x^i = x^j$ would automatically be invalid, since we'd have different free indices on the left-hand side and right-hand side.

However, it is sometimes convenient to _change_ an index. Suppose that we wanted to turn $x^i$ _into_ $x^j$. Think about it for a moment - how would we do that, using standard vectors and matrices? Well, a matrix maps one vector to another, so we would want some sort of "conversion matrix", which (for reasons we'll see soon) we'll call $\delta_{ij}$:

{% math() %}
x^i = \delta_{ij} x^j
{% end %}

Ah, but now our indices are unbalanced - both sides have $i$ as their free index ($j$ is a dummy index), but $i$ is a _lower index_ on the right and an _upper index_ on the left of the equation. So let's fix that by turning $i$ into an upper index on the right-hand side, too:

{% math() %}
x^i = \delta^i {}_j x^j
{% end %}

And _there_, we've got it! This particular matrix $\delta^i{}_j$ is called the **Kronecker delta**, and it is also a tensor. It is defined as:

{% math() %}
\delta_{ij} = \delta^{ij} = \delta^i{}_j = \delta_i{}^j = \begin{cases}
1, & i = j \\
0, & i \neq j
\end{cases}
{% end %}

Which also means that we can represent it as a sort of identity matrix:

{% math() %}
\delta_{ij} = \begin{pmatrix}
1 & 0 & 0 & \dots & 0 \\
0 & 1 & 0 & \dots & 0 \\
0 & 0 & 1 & \dots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \dots & 1
\end{pmatrix}
{% end %}

> **Note:** Our preferred notation is to write the Kronecker delta with its upper and lower indices as $\delta^i{}_j$. But it is also common to just write $\delta^i_j$. **Both forms are equivalent**, it is only a difference of convention.

The Kronecker delta's power to allow us to relabel indices is incredibly powerful. It means that we can turn a tensor with one set of indices, such as $A_{sl}$, into a tensor $A_{jk}$ with a completely different set of indices:

{% math() %}
A_{jk} = \delta^s{}_j \delta^l{}_k A_{sl}
{% end %}

This expression, however, might be rather hard to read. A visual way of understaning it is to remember that we need to _balance_ our  indices. When we apply the Kronecker delta, identical upper and the lower indices "cancel" out, so we can cross them out, like this:

{% math() %}
A_{jk} = \delta^{\cancel{s}}{}_j \delta^{\cancel{l}}{}_k A_{\cancel{s}\cancel{l}}
{% end %}

Note how by "crossing out" the repeated $s$ and $l$ indices that both occur as an upper and lower index, we just get the indices $j, k$ left on the right-hand side, which then balances the left-hand side!

This is a powerful trick that we can use, for instance, to generalize the dot product by relabeling indices:

{% math() %}
A^i B_j = A^i \delta^j{}_i B_j = A^i \delta^{\cancel{j}}{}_i B_{\cancel{j}} = A^i B_i
{% end %}

Here, by using the Kronecker delta, we could effectively "cross out" the index $j$, giving us just $A^i B_i$ left, which is just the dot product!

### Raising and lowering indices

We saw how useful the Kronecker delta can be, when we wanted to relabel a tensor's index. But the Kronecker delta has a limitation: while it can _relabel_ an index - for instance, changing $x^i$ to $x^j$ - it _can't_ convert an upper index to a lower index.

To actually convert between lower and upper indices, we need to use the **metric tensor**. The metric tensor $g_{ij}$ is perhaps the _most_ important tensor. It allows taking a tensor with a lower index, such as $x_j$, and converting it to a tensor with an upper index, like $x^i$:

{% math() %}
x^i = g^{ij} x_j
{% end %}

This is called **lowering an index**. Likewise, the metric tensor also allows us to take a tensor with an upper index and converting it to a tensor with a lower index:

{% math() %}
x_i = g_{ij} x^j
{% end %}

This is called **raising an index**. Furthermore, if we combine the Kronecker delta and the metric tensor, we can convert a tensor to its upper-index or lower-index equivalent with the _same_ index:

{% math() %}
\begin{align*}
x_i = \delta^j{}_i g_{ij} x^i = \delta^j{}_i x_j \\
x^i = \delta^i{}_j g^{ij} x_i =  \delta^i{}_j x^j
\end{align*}
{% end %}

Aside from just being useful, the metric tensor also has a very important place in physics. We will shortly discuss what the metric tensor $g_{ij}$ _physically represents_, but first, we need to cover a little bit more tensor algebra.

### Tensor contraction

We saw previously that by the Einstein summation convention, identical upper and lower indices are summed over:

{% math() %}
A_i B^i = A_1 B^1 + A_2 B^2 + A_3 B^3 + \dots + A_n B^n
{% end %}

> **Note:** Remember that $A^1$ represents the _first component_ of the vector $A_i$, and $A^2$ represents its _second component_. For instance, if we were working with Cartesian coordinates, $A^1 = A^x$ and $A^2 = A^y$. The indices $1, 2, 3,\dots$ are _tensor indices_, **not exponents**.

But we can also do this for single tensors. For instance, suppose we have a tensor $T^i{}_j$. If we make the two indices identical, we would have $T^i{}_i$, which again is implicitly summed over $i$:

{% math() %}
T^i{}_i = T^1{}_1 + T^2{}_2 + \dots + T^n{}_n
{% end %}

This is called a **tensor contraction** (also called the **trace**), and it's significant because it turns the tensor into a _scalar_. For instance, if our tensor $T_{ij}$ (we write it in the lower index for convenience) is given by:

{% math() %}
T_{ij} = \begin{pmatrix}
T_{11} & T_{12} & T_{13} \\
T_{21} & T_{22} & T_{23} \\
T_{31} & T_{32} & T_{33}
\end{pmatrix}
{% end %}

Then the tensor contraction $T^i{}_i$ becomes:

{% math() %}
T^i{}_i = T^1{}_1 + T^2{}_2 + T^3{}_3
{% end %}

Which is just the sum of the diagonals of $T_{ij}$ (with one raised index). We can also do this with tensors of three indices like $R^i{}_{jk}$, in which we have:

{% math() %}
R^i{}_{ik} = R^1{}_{1k} + R^2{}_{2k} + R^3{}_{3k} + \dots + R^n{}_{nk}
{% end %}

The importance of the tensor contraction is that it takes a higher-dimensional tensor and returns a lower-dimensional tensor - often, returning a scalar. It is in many ways the _generalization_ of the dot product (which takes two vectors and outputs a scalar) but for tensors of arbitrary dimensions. Being able to form a scalar from tensors is physically important because _scalars are invariant_ - scalars are just numbers, and a number is a number is a number, no matter the coordinates we use. This makes it very important for **relativistic theories** - we're getting a bit ahead of ourselves here, but we'll get there soon!

### Practicing contractions

Tensor contraction can be a bit unfamiliar, so let's do a practice problem: let's evaluate the expression {% inlmath() %}\delta^\mu {}_\mu \delta^\nu {}_\nu{% end %}, where $\mu, \nu = 0, 1, 2, 3$.

> **Note:** Don't be scared by the weird choice of letters $\mu, \nu$ for indices! We can just as well use $i, j$, because dummy indices can use any letter we want.

To solve, we expand the tensors with the implicit summations written out explicitly, This gives us:

{% math() %}
\begin{align*}
\delta^\mu {}_\mu \delta^\nu {}_\nu &= \underbrace{\sum_{\mu = 0}^3 \sum_{\nu = 0}^3 \delta^\mu {}_\mu \delta^\nu {}_\nu}_\text{write sums explicitly} \\
&= \underbrace{\delta^0{}_0 \delta^0{}_0 + \delta^1{}_1 \delta^1{}_1 + \delta^2{}_2 \delta^2{}_2 + \delta^3{}_3 \delta^3{}_3}_\text{only nonzero terms in the sum are left} \\
&= 1 + 1 + 1 + 1 \\
&= 4
\end{align*}
{% end %}

**Why is this correct?** This is due to the fact that _by definition_ $\delta^i{}_i \delta^j{}_j$ is _only nonzero_ if $i = j$. If we have $i = j$ then $\delta^i{}_i \delta^j{}_j = \delta^i{}_i \delta^i{}_i = 1$, but if we have $i \neq j$ we have $\delta_i^i \delta_j^j = 0$. Thus the summation (which would've usually been over 16 terms!) collapses only to four terms!

### Tensor calculus

Just as we could do algebra with tensors, we can also do calculus with tensors. For instance, we could take the derivative of the position vector $x^i$ to get the velocity vector $v^i$:

{% math() %}
v^i = \dfrac{dx^i}{dt}
{% end %}

We can also take _partial derivatives_. Suppose we had a scalar function $\phi(x^i) = \phi(x, y, z)$. Then, the partial derivative with respect to the potential can be written as:        

{% math() %}
\dfrac{\partial \phi}{\partial x^i} = \nabla \phi
{% end %}

In tensor notation, it is common to use the shorthand $\partial_i = \dfrac{\partial}{\partial x^i}$, meaning the above can also be written as:

{% math() %}
\partial_i \phi = \nabla \phi
{% end %}

Remember that just like $\nabla \phi$ is a vector, $\partial_i \phi$ is also a vector! This means that $\partial_1 \phi = \partial_x \phi = \frac{\partial \phi}{\partial x}$, $\partial_2 \phi = \partial_y \phi = \frac{\partial \phi}{\partial y}$, and so on. The power of tensor calculus really starts, however, when we start differentiating _tensors_ other than scalars. For instance, we can write the **divergence** as:

{% math() %}
\partial_i F^i = \nabla \cdot \vec F
{% end %}

You may notice that since $i$ as both an upper and lower index, it is a dummy index: so this is a _tensor contraction_, which creates a scalar! Indeed, if we expand it, we have:

{% math() %}
\partial_i F^i = \partial_x F^x + \partial_y F^y + \partial_z F^z
{% end %}

Which is just the standard vector calculus formula for the divergence. Additionally, just like any other tensor, we can raise and lower the index of the partial derivative $\partial_i$ using the metric. Thus, we have:

{% math() %}
\partial^i = g^{ij} \partial_i
{% end %}

Treating the partial derivative as a tensor may be a bit uncomfortable, but it is mathematically made possible by the formalism of tensor calculus. It allows us to take otherwise very complicated derivatives, such as derivatives of a matrix:

{% math() %}
\partial_i F^{ij} = J^j
{% end %}

To summarize, tensor calculus allows us to take derivatives of a variety of mathematical objects that go beyond just vectors and scalars. Crucially, it allows us to take complicated deriatives of tensors in ways that cannot be done with just vector calculus.

### Relativity and spacetime

We've covered a lot about tensors, but let's now return to a topic we discussed earlier: the **metric tensor**.

To begin, we have to discuss first the _geometric_ origins of tensors. Tensors are not just arbitrary combinations of indices; they represent something with a particular set of _components_. These components are dependent upon the underlying space. For instance, a 2D vector $V^i$ represents a directional quantity, with two components $V^x, V^y$ in 2D Cartesian space. But that same vector could have _different_ components if we use another coordinate system. Taking our example, if we switch to polar coordinates, the vector's components would switch to $V^r, V^\theta$. Thus, while tensors themselves are coordinate-independent - after all, the Universe doesn't care whether you use Cartesian or polar coordinates - the _components_ of tensors are definitely dependent on the coordinate system we use, and the underlying geometry of space.

The **metric tensor** $g_{ij}$ lets us characterize a system of coordinates in a geometric space by defining what a _distance_ represents. You might think - why do we need to formalize what a distance means? Isn't that _obvious_? But in fact, the notion of a distance is not a simple as it may seem. For instance, in Euclidean 3D space, the infinitesimal distance between two points is given by:

{% math() %}
ds^2 = dx^2 + dy^2 + dz^2
{% end %}

"I knew that!", you might say, "that's just Pythagoras's theorem written with infinitesimals $dx, dy, dz$ rather than $x, y, z$!" And indeed you would be correct. For hundreds of years, we have no reason to think that the Universe was anything other than 3D space with Euclidean geometry.

But at the dawn of the 20th century, the very famous Albert Einstein discovered that our Universe was not three-dimensional, as had been throught; rather, it was four-dimensional, containing one dimension of time and three of space - what we call **spacetime**. So in fact, the _correct_ expression for the infinitesimal distance between two points is given by Pythagoras' formula:

{% math() %}
ds^2 = dt^2 - (dx^2 + dy^2 + dz^2)
{% end %}

(For those readers already familiar with the Minkowski metric, be aware that we use units where $c$, the speed of light, is equal to one). Except this distance formula isn't completely correct either: Einstein found that this was a _special case_ of a more general tensor expression for the distance between two points in spacetime:

{% math() %}
\begin{align*}
ds^2 &= g_{\mu \nu} dx^\mu dx^\nu \\
&= g_{00} dt^2 + g_{01} dt\,dx + g_{02} dt\,dy + \dots \\
&\qquad + g_{10} dx dt + g_{11} dx^2 + g_{12} dx\, dy + \dots \\
&\qquad + g_{30} dz\,dt + g_{31} dz\,dx + g_{32} dz\,dy + g_{33}\,dz^2
\end{align*}
{% end %}

Where $g_{\mu \nu}$ is the four-dimensional **metric tensor**, given by: 

{% math() %}
g_{\mu \nu} = \begin{pmatrix}
g_{00} & g_{01} & g_{02} & g_{03} \\
g_{10} & g_{11} & g_{12} & g_{13} \\
g_{20} & g_{21} & g_{22} & g_{23} \\
g_{30} & g_{31} & g_{32} & g_{33}
\end{pmatrix}
{% end %}

Why is this significant? Because it means that distance is dependent on the _geometry_ of spacetime, and that implies that time and space are interdependent, and that spacetime can be **curved**! In fact, the metric tensor is the foundation of Einstein's theories of **special and general relativity**.

> **Note on notation:** It is customary to use latin indices like $i, j, k, \dots$ when we are only talking about three-dimensional tensors, such as position $x^i$. However, when we are talking about _four-dimensional_ tensors in spacetime, such as the metric tensor, we use greek indices like $\mu, \nu, \gamma$.

## Special relativity

With our newfound knowledge of tensors and spacetime, we're ready to tackle the **special theory of relativity** in full. We've discussed earlier that special relativity postulates that our Universe is four-dimensional, and its geometric structure is a four-dimensional geometry called **spacetime**. 

In most of quantum field theory, we work in **Minkowski spacetime**, the _special case_ of the four-dimensional spacetime that we discussed earlier. The correct expression for the infinitesimal distance in Minkowski space, as we saw, is given by:

{% math() %}
ds^2 = dt^2 - (dx^2 + dy^2 + dz^2)
{% end %}

Note that we can also write this expression in matrix-vector form, as:

{% math() %}
ds^2 = 
\begin{bmatrix} dt \\ dx \\ dy \\ dz \end{bmatrix}^T
\underbrace{\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & -1 & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & -1 \\
\end{pmatrix}}_{\eta_{\mu \nu}}
\begin{bmatrix} dt \\ dx \\ dy \\ dz \end{bmatrix}
{% end %}

By comparison with $ds^2 = g_{\mu \nu} dx^\mu dx^\nu$, we find that the matrix in the middle of the above expression is the **metric tensor** for Minkowski spacetime, which characterizes the geometry of spacetime in special relativity. We usually call this tensor the _Minkowski metric_, and denote it as $\eta_{\mu \nu}$:

{% math() %}
\eta_{\mu \nu} = \begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & -1 & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & -1 \\
\end{pmatrix}
{% end %}

> **Note:** Quantum field theory is (mostly) based off Minkowski spacetime, so the Minkowski metric will be the metric tensor we use for raising and lowering indices. We'll wait to look into _general relativity_ with its much more complicated curved spacetimes, but we'll get to that in time.

While the Minkowski metric may _look_ deceptively simple and appear to be a simple four-dimensional extension of the Euclidean metric with a few sign changes, it is actually _radically different_, and the signs make all the difference.

## Useful math

### The Fourier transform

In physics, it is very useful to decompose a complicated function as a sum of sines and cosines - which, remember, can be written as complex exponentials. Sines and cosines are well-studied functions with very nice properties, which cannot be said of all functions (especially the Dirac delta "function")! The Fourier transform gives us a way to convert between these two representations. The basic idea is this: by _adding_ lots of little sinusoidal waves that have slightly different spatial periods (wavelengths) and different amplitudes, we can approximate the shape of some complicated function $f(x)$. Each of these waves has amplitude (magnitude)

Since a sum over continous functions is just an integral, we can write this as:

{% math() %}
f(x) = \int_{-\infty}^\infty \dfrac{dk}{2\pi} \tilde f(k) e^{-ikx} dk
{% end %}

Where the function $\tilde f(k)$ gives the _amplitude_ of each one of those infinitely-many little sinusoidal waves of wavenumber $k = 2\pi/\lambda$. But how do we get the function $\tilde f(k)$ that gives the amplitudes? The answer is the **Fourier transform**:

{% math() %}
\tilde f(k) = \int_{-\infty}^\infty dk f(x) e^{ikx}
{% end %}

It is a common (but confusing) convention in quantum physics to use the same symbol for a function and its Fourier transform in physics, as well as omitting the bounds of integration. So, in the standard quantum physics notation, the Fourier transform can also be written as:

{% math() %}
f(k) = \int \dfrac{dk}{2\pi} f(x) e^{-ikx}
{% end %}

We can also define the Fourier transform in more than one dimension. Of particular interest to us is the _three-dimensional_ Fourier transform, given by:

{% math() %}
f(k) = \int \dfrac{d^3k}{(2\pi)^3} f(\vec x) e^{-i \vec k \cdot \vec x}
{% end %}

Where $\vec k, \vec x$ are three-vectors. In $n$ dimensions, the $n$-th dimensional Fourier transform is given by:

{% math() %}
f(k) = \int \dfrac{d^nk}{(2\pi)^n} f(x^\mu) e^{-ik_\mu x^\mu}
{% end %}

Among the _many_ uses of Fourier transforms are that they can be used to solve a variety of partial differential equations (PDEs), and in particular, a certain class of PDEs known as **wave equations** that pop up everywhere in quantum mechanics and quantum fiedl theory. We will soon see this in the next chapter!