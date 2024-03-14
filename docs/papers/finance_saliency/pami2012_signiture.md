# Image Signature: Highlighting Sparse Salient Regions

Hou X<sup>1</sup>, Harel J, Koch C. IEEE transactions on ***pattern analysis and machine intelligence***, 2011, 34(1): 194-201.

1. *the Department of Computation and Neural Systems, California Institute of Technology*
2. *the Department of Electrical Engineering, California Institute of Technology*
3. *the Department of Biology and Computation and Neural Systems, California Institute of Technology*



$$
\begin{equation}
    \mathrm{x=f+b,~x,f,b\in\mathbb{R}^N,}
\end{equation}
$$

$f$ represents the foreground of figure signal and is assumed to be **sparsely** supported **in the standard spatial basis**. $b$ represents the background and is assumed to **be sparsely supported in the basis of the Discrete Cosine Transform**.

**Distance matrix**

$$
\begin{equation}
    D(\mathbf{x}^1,\mathbf{x}^2)=\|\mathrm{sign}(\mathbf{\hat{x}}^1)-\mathrm{sign}(\mathbf{\hat{x}}^2)\|_0.
\end{equation}
$$


**Proposition 1 (Signature suppresses background)**: The image reconstructed from the image signature approximates the location of a sufficiently sparse foreground on a sufficiently sparse background as follows:

$$
\begin{equation}
    E{\left(\frac{\langle\bar{\mathbf{f}},\bar{\mathbf{x}}\rangle}{\|\bar{\mathbf{f}}\|\cdot\|\bar{\mathbf{x}}\|}\right)}\geq0.5,\quad\mathrm{for~}|\Omega_{\mathbf{b}}|<\frac{N}{6}.
\end{equation}
$$














