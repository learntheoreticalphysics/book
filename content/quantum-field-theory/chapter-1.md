+++
title = "Getting started with quantum field theory"
date = 2025-04-27
+++

## The motivation for quantum field theory

As far as we know, all matter in the universe is quantum in nature. Quantum mechanics governs the behavior of all matter, and at an introductory and intermediate level, the dynamics of quantum systems is typically solved with the Schrödinger equation:

{% math() %}
i\hbar \dfrac{\partial}{\partial t} \Psi(\mathbf{r}, t) = \left(-\dfrac{\hbar^2}{2m} \nabla^2 + V(\mathbf{r})\right) \Psi(x, t)
{% end %}

However, relativistic quantum field theory is a far more accurate theory of quantum mechanics than the Schrödinger equation. In fact, while we may use approximations like (semi-)classical theory and nonrelativistic or single-particle quantum mechanics, quantum field theory, and specifically the Standard Model, offers the best and most accurate results. 

That is to say, any quantum system may be solved for by the Schrödinger equation, but doing the same calculations with quantum field theory offers results with unparalleled precision. Predictions of the [magnetic moment of electrons](https://en.wikipedia.org/wiki/Magnetic_moment), [energy levels of the hydrogen atom](https://en.wikipedia.org/wiki/Lamb_shift), a variety of [previously-unknown elementary particles](https://physics.info/standard/), and the [Rydberg constant](https://en.wikipedia.org/wiki/Rydberg_constant) made through quantum field theory have been experimentally tested and confirmed very well.

These are not meaningless predictions either; our understanding of the emission and absorption of light, of the subatomic origins of magnetism, and even our standard of time in the [definition of a second](https://en.wikipedia.org/wiki/Second) are based on these predictions. In turn, numerous scientific experiments, material science, laser technology, and electronics depend on applying these predictions, without which they would likely not progress to how they are today.

### Things to know

We'll be working with natural units where $c = \hbar = 1$ simply out of convenience. Also, (almost) everything will be in tensors. We will be working in the formalism of Lagrangian and Hamiltonian field theory, as is standard in theoretical physics. Don't worry if some of these topics are unfamiliar; we will review all of these topics before we begin, and consult the other free books on this site for more information.

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

Where $d^4 x = dx\, dy\, dz\, dt$, and the integral is conducted over
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
this means that the Lagrangian must satisfy the following partial
differential equation:

{% math() %}\frac{\partial \mathscr{L}}{\partial \phi} - \partial_\mu \left(\frac{\partial \mathscr{L}}{\partial (\partial_\mu \phi)}\right) = 0{% end %}

This partial differential equation is called the **Euler-Lagrange
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
\delta^{ij} \partial_j \partial_i f = 0
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

And the matrix multiplication formula becomes:

{% math() %}
C_{ij} = A_{ik} B^k {}_j
{% end %}

To be able to discuss tensors further, however, we must introduce two concepts: that of a co-vector, and of the metric: 

{% math() %}V_j e^j{% end %}

Euclidean metric/kronecker delta: 

{% math() %}\delta_{ij}{% end %}

Dot product (euclidean, for all non-euclidean spaces replace $\delta_{ij}$ with the metric tensor):

{% math() %}
S = A^i e_i B^j e_j = \delta_{ij} A^i B^j = A^i B_i
{% end %}

(where for the last term we used the kronecker delta to lower an index, that is $\delta_{ij} B^j = B_i$)

Cross product:

{% math() %}
C^k = A_i B_j - A_j B_i
{% end %}

Gradient:

{% math() %}
\nabla F = \partial_\mu F
{% end %}

Curl:

{% math() %}
\nabla \times F = \partial_\nu V_\mu - \partial_\mu V_\nu
{% end %}

Relabelling ($j \to i$):
{% math() %}
\delta^i_j T^j = T^i
{% end %}

Where we use the fact that $\delta^i_j = \delta^{ik} \delta_{kj}$.
