## Chapter 3 Reversible Markov Chains

### 3.1 Introduction

**Definition** The chain is **reversible** if $\pi_i p_{ij}=\pi_j p_{ji}\forall i,j$. The equations are called **detailed balanced equations**. For cts-time chain, the equations are $\pi_i q_{ij}=\pi_j q_{ji}$.

_Remark_ If there is $\pi$ such that $\sum_i \pi_i=1$ and $\pi_ip_{ij}=\pi_jp_{ji}\forall i,j$ then $\pi$ is the stationary distribution, since from _detailed balance equations_ we can attain _balanced equations_:
$$
\sum_i \pi_i p_{ij}=\sum_i \pi_j p_{ji}=\pi_j
$$
_Property_ The chain is called _reversible_ since when $X_0\sim\pi$, $(X_0,...,X_t)=_d (X_t,...,X_0)$.

This yields $\pi_i p_{ij}^{(t)}=\pi_j p_{ji}^{(t)}$, which indicates $\pi_i Z_{ij}=\pi_j Z_{ji}$. But, in general, ==$\pi_i E_i T_j\ne \pi_j E_j T_i$==.

**Lemma 3.1** TFAE for reversible chain (a) $p_{ii}^{(t)}=p_{jj}^{(t)},i,j\in I,t\ge 1$. (b) $P_i(T_j=t)=P_j(T_i=t),i,j\in I,t\ge 1$.

_proof_ Recall $G_{ij}=\sum_t p_{ij}^{(t)}z^t$ and $F_{ij}=\sum_t P_i (T_t=j)z^t$ satisfy $F_{ij}(z)=G_{ij}(z)/G_{jj}(z)$. Notice (b)$\Leftrightarrow F_{ij}=F_{ji}\Leftrightarrow G_{ij}(z)/G_{jj}(z)=G_{ji}(z)/G_{ii}(z)$. Since the chain is reversible, $\pi_i G_{ij}(z)=\pi_j G_{ji}(z)$, so continue this equivalence chain $\Leftrightarrow \pi_i G_{jj}(z)=\pi_j G_{ii}(z)$. If this is true, let $z=0$, we have $\pi_i=\pi_j$, so $G_{ij}=G_{ji}$, i.e. (a) holds. If (a) is true, push $t\to\infty$ we have $\pi_i=\pi_j$, meanwhile $G_{ii}=G_{jj}$, which together gives $\pi_i G_{jj}(z)=\pi_j G_{ii}$.

#### 3.1.1 Time-reversals and cat-and-mouse games

**Definition** For a general chain, the **time-reversed chain** is a Markov chain with transition matrix $\mathbf P^*$ where $\pi_i p_{ij}=\pi_j p_{ji}^*$. The stationary reversed chain is just the stationary original chain run backwards in time.

_Remark_ The chain is reversible iff $\mathbf P=\mathbf P^*$.

_Property_ $\pi_i Z_{ij}=\pi_jZ_{ji}$.

**Lemma 3.2 The cyclic tour property** For states $i_0,i_1,...,i_m$ of a reversible chain, $\sum_{k=0}^n E_{i_k}T_{i_{k+1}}=\sum_{k=0}^n E_{i_k}T_{i_{k-1}}$. Actually, for general chain we have $\sum_{k=0}^n E_{i_k}T_{i_{k+1}}=\sum_{k=0}^n E_{i_k}^*T_{i_{k-1}}$.

Below results can be interpreted as cat-and-mouse games where the cat moves according to $\mathbf P$ and the cat moves according to $\mathbf P^*$.

_Cat-and-mouse game 1_ Both animals are placed at the same state chosen according to $\pi$. The mouse moves a step and stop, meanwhile the cat moves until it finds the mouse which takes $M$ steps. If $|I|=n$, $EM=n-1$.

_proof_ Since the mouse jumps as reversed chain, one can imagine the cat jumps one more step after he caught the mouse, under which case he should jump to the starting point. This gives $EM=E_\pi T^+-1$. Notice $E_\pi T^+=\sum_i \pi_i E_i T_i^+=\sum_i \pi_i\pi_i^{-1}=n$.

_Cat-and-mouse game 2_ 