## Chapter 3 Reversible Markov Chains

### 3.1 Introduction

**Definition** The chain is **reversible** if $\pi_i p_{ij}=\pi_j p_{ji}\forall i,j$. The equations are called **detailed balanced equations**. 

Below we suppose the chain are all irreducible and reversible.

_Remark_ If there is $\pi$ such that $\sum_i \pi_i=1$ and $\pi_ip_{ij}=\pi_jp_{ji}\forall i,j$ then $\pi$ is the stationary distribution, since from _detailed balance equations_ we can attain _balanced equations_:
$$
\sum_i \pi_i p_{ij}=\sum_i \pi_j p_{ji}=\pi_j
$$
_Property_ The chain is called _reversible_ since when $X_0\sim\pi$, $(X_0,...,X_t)=_d (X_t,...,X_0)$.

This yields $\pi_i p_{ij}^{(t)}=\pi_j p_{ji}^{(t)}$, which indicates $\pi_i Z_{ij}=\pi_j Z_{ji}$. But, in general, ==$\pi_i E_i T_j\ne \pi_j E_j T_i$==.

**Lemma 3.1** TFAE for reversible chain (a) $p_{ii}^{(t)}=p_{jj}^{(t)},i,j\in I,t\ge 1$. (b) $P_i(T_j=t)=P_j(T_i=t),i,j\in I,t\ge 1$.

_proof_ 