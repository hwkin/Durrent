This note consists of remarks on the book under the same directory.

#### 2.4 Energy

1. There is a correspondence between notions here and notions of differential geometry.

   | Notions in this chapter                                     | Notions in differential geometry                             |
   | ----------------------------------------------------------- | ------------------------------------------------------------ |
   | $f\in\mathcal l^2(V)$                                       | $f\in \Omega^0(M)$, a smooth function                        |
   | $\theta\in\mathcal l_-^2(E)$                                | $\alpha\in\Omega^1(M)$, a 1-form                             |
   | coboundary operator $d:\mathcal l^2(V)\to\mathcal l_-^2(E)$ | exterior derivative $d:\Omega^0(M)\to\Omega^1(M)$ ,or $-\text{grad}$ |
   | boundary operator $d^*:\mathcal l_-^2(E)\to\mathcal l^2(V)$ | codifferential $d^*:\Omega^1(M)\to\Omega^0(M)$ or $-\text{div}$ |

   The notions "boundary" and "coboundary" comes from algebraic topology instead.

2. The space $\bigstar$ is the space of irrotational field with source and the space $\lozenge$ is the space of rotational field without source. 

#### 5.2 The first-moment method

Solution to exercise 5.7: 

Denote $P_p^G$ to be the probability that in a percolation with probability $p$ on $G$. 

Let $X_i\sim B(p), Y_i\sim B(r)$ be the indicators that $i$ is open in $G$, i.e., in $\omega$ and $i$ is open in $\omega$, then $X_iY_i\sim B(pr)$, which indicates that the eventual graph is a percolation with probability $pr$. This gives 
$$
\mathbb E P_r^\omega=P_{pr}^G
$$
When $pr>p_c(G)$, $RHS=1$, which implies $P_r^\omega=1$ a.s., while $pr<p_c(G)$ implies $P_r^\omega=0$ a.s..
