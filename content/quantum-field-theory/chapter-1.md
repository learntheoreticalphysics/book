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
