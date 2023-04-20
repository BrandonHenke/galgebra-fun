# Density Operators

The density operator is a more general object for discussing quantum states than the typical state vector, since it can be used to describe mixed states.
The typical way of discussing them might not be the best way, I think.
Geometric algebra might give a better way of representing density operators, and quantum mechanics.

The typical representation for density operator is the density matrix, represented by
$$\begin{equation}
    \rho = \sum_n p_n |\psi_n\rangle\langle \psi_n|,
\end{equation}$$
where $|\psi_n\rangle$ are pure quantum states prepared with probability $p_n$.

## Spin-1/2 States

The Stern-Gerlach experiment indicates that the intrinsic angular momentum can take only two states, either aligned with or anti-aligned with the measurement.
Aligned is "spin up" and anti-aligned is "spin down".
Defining this axis as the $z$-axis is common.

<!-- The spin of a particle is an observable, which is represented by a Hermitian operator,
$$
    \hat{\bm{s}} = \frac{\hbar}{2}\hat{\bm{\sigma}},
$$
where $\hat{\bm{\sigma}} = \sum_n \sigma_n$ and $\sigma_n$ are the Pauli spin matrices. -->

Given some observable, there exists a Hermitian operator, $\hat{O}$, which represents this observable.
The measurement of an observable can only result in an eigenvalue of the observable operator, and the quantum state changes to be the eigenstate with the measured eigenvalue.
From this, choosing the spin states to be the following is the natural choice:
$$\begin{equation}
    \hat{s}_z |\pm\rangle = \pm \frac{\hbar}{2}|\pm\rangle.
\end{equation}$$
In this basis,
$$\begin{equation}
    \hat{s}_z = \frac{\hbar}{2}\sigma_z,
\end{equation}$$
where $\sigma_z$ is the $z$ Pauli matrix.

It turns out that the spin states $|\psi\rangle = \alpha|+\rangle + \beta|-\rangle$ are two-component complex spinors.
Notably, however, spin (angular momentum) is an axial vector, not a spinor.
The result one gets from the measurement, then, is an axial vector, but the states are represented by spinors.
This infuriates me.

## Geometric Algebra

The Pauli spin matrices are a representation of a geometric algebra, $\mathcal{G}(3)$, so let's play with that a bit.

In $\mathcal{G}(3)$, there are eight basis elements, a scalar, three orthonormal vectors, three orthonormal bivectors, and one trivector (the pseudoscalar element).
Axial vectors and bivectors are the same thing.

Angular momentum is a bivector, since $L = x\wedge p$.
Hence, the spin of a particle is a bivector.
A spinor is a rotor, which generates rotations:
$$\begin{equation}
    g' = R g R^{-1},
\end{equation}$$
where $g$ becomes $g'$ by a rotation in the plane specified by $R$.

Therefore, let's represent the spin (intrinsic angular momentum) as a bivector, and represent the spin states with a rotor (spinor), in GA.
How hard could this be?

## Translation into GA: It's Hard

Spin up, is charactorized by being measured along the positive $z$ axis, so the result of a measurement should be
$$\begin{equation}
    S = \frac{\hbar}{2} \sigma_{12}.
\end{equation}$$
However, this is the result of the measurement of the state, not the state itself.
The state is a spinor.
A spinor is an element of the even subalgebra of the GA, so it contains scalar and bivector elements.
Conveniently, there is an object which looks very similar to this: the density operator for the spin-1/2 system.
$$\begin{equation}
    \rho = \frac{1}{2}(1+r),
\end{equation}$$
where $r$ is a vector, where the basis vectors are $\sigma_n$.
Let's just switch it up a bit, and multiply $r$ by the pseudovector for the space, $i$:
$$\begin{equation}
    \rho \rightarrow \rho = \frac{1}{2}(1 + ir).
\end{equation}$$
For now, we don't know what the factor out front should be, so we'll leave it as $1/2$.
Unsurprisingly, this looks very much like a complex number, so let's go ahead and write it in the polar representation:
$$\begin{equation}
    \rho = \frac{1}{2} \sqrt{1+r^2} e^{i\theta\hat{r}},
\end{equation}$$
where $\theta = \arctan (|r|)$.

Let's work with this.
Supposing we are using the traditional method, consider the pure spin up state, $|+\rangle$.
The density operator for this is $|+\rangle\langle+|$, or
$$\begin{equation}
    \rho = \frac{1}{2}(1+\sigma_z).
\end{equation}$$
The state, under some operation, transforms as $|+\rangle \rightarrow \hat{O}|+\rangle$, so the density operator transforms as
$$\begin{equation}
    \rho \rightarrow \hat{O}\rho\hat{O}^\dagger.
\end{equation}$$
Hence, under the spin $z$ operator,
$$\begin{align}
    \rho \rightarrow \rho' &= \frac{\hbar^2}{8}\sigma_z (1 + \sigma_z)\sigma_z,\\
    &= \frac{\hbar^2}{8}(1 + \sigma_z^3),\\
    &= \frac{\hbar^2}{8}(1 + \sigma_z),\\
    &= \frac{\hbar^2}{4}\rho.
\end{align}$$
To be fair, the expectation, here, wasn't that the density operator would stay normalized, since the state doesn't stay normalized under this operation.
A similar result is found in the spin down case:
$$\begin{align}
    \rho \rightarrow \rho' &= \frac{\hbar^2}{8}\sigma_z (1 - \sigma_z)\sigma_z,\\
    &= \frac{\hbar^2}{4}\rho.
\end{align}$$
Testing the spin $x$ operator gives the following:
$$\begin{align}
    \rho \rightarrow \rho' &= \frac{\hbar^2}{8}\sigma_x (1 + \sigma_z)\sigma_x,\\
    &= \frac{\hbar^2}{8}(1-\sigma_z).
\end{align}$$
This is interesting.
It seems that the effect of this is to flip the vector $r$ across the $x$-axis.

Anyway, let's try this in our new representation (here I switch $x,y,z \rightarrow 1,2,3$):
$$\begin{align}
    \rho = \frac{1}{\sqrt{2}}e^{i\sigma_3\pi/4} \rightarrow \rho' &= \frac{\hbar^2}{4} \sigma_{12} \frac{1}{\sqrt{2}}e^{i\sigma_3\pi/4} \sigma_{21},\\
    &= \frac{\hbar^2}{4} \frac{1}{\sqrt{2}}e^{\sigma_{12}i\sigma_3\sigma_{21}\pi/4},\\
    &= \frac{\hbar^2}{4} \frac{1}{\sqrt{2}}e^{i\sigma_3\pi/4},\\
    &= \frac{\hbar^2}{4}\rho.
\end{align}$$
This is the same result as in the traditional case!
Let's try the other test cases:
$$\begin{align}
    \rho = \frac{1}{\sqrt{2}}e^{-i\sigma_3\pi/4} \rightarrow \rho' &= \frac{\hbar^2}{4} \sigma_{12} \frac{1}{\sqrt{2}}e^{i\sigma_3\pi/4} \sigma_{21},\\
    &= \frac{\hbar^2}{4} \frac{1}{\sqrt{2}}e^{-\sigma_{12}i\sigma_3\sigma_{21}\pi/4},\\
    &= \frac{\hbar^2}{4} \frac{1}{\sqrt{2}}e^{-i\sigma_3\pi/4},\\
    &= \frac{\hbar^2}{4}\rho.\\
    \rho = \frac{1}{\sqrt{2}}e^{i\sigma_3\pi/4} \rightarrow \rho' &= \frac{\hbar^2}{4} \sigma_{23} \frac{1}{\sqrt{2}}e^{i\sigma_3\pi/4} \sigma_{32},\\
    &= \frac{\hbar^2}{4} \frac{1}{\sqrt{2}}e^{\sigma_{23}i\sigma_3\sigma_{32}\pi/4},\\
    &= \frac{\hbar^2}{4} \frac{1}{\sqrt{2}}e^{-i\sigma_3\pi/4}. \quad \text{(spin down \checkmark)}
\end{align}$$
This looks good, so far.

### Recap of Translation

$$\begin{align}
    \text{(vector)}\quad\hat{\bm{s}} = \frac{\hbar}{2} \bm{\sigma} &\rightarrow \frac{\hbar}{2} i\bm{\sigma} = S\quad\text{(bivector)}\\
    \text{(scalar+vector)}\quad \rho = \frac{1}{2} (1+r) &\rightarrow \frac{1}{2} \sqrt{1+r^2} e^{i\theta\hat{r}} = \rho\quad\text{(spinor)}
\end{align}$$
Rather than use state vectors at all, we can just use the density operator.
Additionally, rather than a general operator acting only from the left, the transformation is done by acting with it on both sides:
$$\begin{equation}
    \hat{O}|\psi\rangle \rightarrow \hat{O} \rho \hat{O}^\dagger.
\end{equation}$$

## Probabilities and Expectation Values

The traditional way of determining the probability of some outcome is to calculate $|\langle\phi | \psi\rangle|^2$, where $|\phi\rangle$ is the eigenstate of some operator.

$$\begin{align}
    ρ &= \frac{1}{2}(1+\sigma_3).\\
    ρ^2 &= \frac{1}{4}(1+\sigma_3)(1+\sigma_3),\\
    &= \frac{1}{4}(2+2\sigma_3),\\
    &= ρ
\end{align}$$