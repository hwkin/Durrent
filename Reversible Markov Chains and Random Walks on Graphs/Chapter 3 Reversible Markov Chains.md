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

_Property_ $\pi_i Z_{ij}=\pi_jZ_{ji}^*$.

**Lemma 3.2 The cyclic tour property** For states $i_0,i_1,...,i_m$ of a reversible chain, $\sum_{k=0}^n E_{i_k}T_{i_{k+1}}=\sum_{k=0}^n E_{i_k}T_{i_{k-1}}$. Actually, for general chain we have $\sum_{k=0}^n E_{i_k}T_{i_{k+1}}=\sum_{k=0}^n E_{i_k}^*T_{i_{k-1}}$.

Below results can be interpreted as cat-and-mouse games where the cat moves according to $\mathbf P$ and the cat moves according to $\mathbf P^*$.

<font color="blue">_Cat-and-mouse game 1_</font> Both animals are placed at the same state chosen according to $\pi$. The mouse moves a step and stop, meanwhile the cat moves until it finds the mouse which takes $M$ steps. If $|I|=n$, $EM=n-1$.

_proof_ Since the mouse jumps as reversed chain, one can imagine the cat jumps one more step after he caught the mouse, under which case he should jump to the starting point. This gives $EM=E_\pi T^+-1$. Notice $E_\pi T^+=\sum_i \pi_i E_i T_i^+=\sum_i \pi_i\pi_i^{-1}=n$.

<font color="blue">_Cat-and-mouse game 2_</font> Initially cat is placed at $x$ and mouse is placed at $y$. The player sees their position and decides which to move one step (not necessarily in turn), and he stops until the cat and mouse meet, which takes $M$ steps. We wonder $E_{(x,y)}M$. 

_Example_ One may think $E_{(x,y)}M$ depends on the strategy and the distance. However, consider the example of asymmetric random walk on $\mathbb Z/n\mathbb Z$, with $p_{n,n+1}=2/3,p_{n,n-1}=1/3$. In this case, the moment they move $n$th step (with cat $m$ steps and mouse $n-m$ steps) , the distance (clockwise along the circle) doesn't depend on the strategy but only on $n$, since one can imagine the cat starts from $x$, moves $m$ steps, moves to the position of mouse, and moves $n-m$ steps according to the reverse of the action of mouse, then it should arrive at $y$. So $M$ doesn't depend on the strategy but only on the distance.

In general, $E_{(x,y)}M$ does depend on strategy, but the effect of strategy can be bounded in terms of a measure of non-symmetry of the chain.

**Proposition 3.3** Regardless of the strategy, $\min_z E_\pi T_z\le E_{(x,y)}M-(E_x T_y-E_\pi T_y)\le\max_z E_\pi T_z$, where hitting times $T$ refer to the $\mathbf P$-chain.

> _proof_ Consider the functions $f(x,y)=E_xT_y-E_\pi T_y$ and $f^*(y,x)=E_y^*T_x-E_\pi^* T_x$. 
>
> On the one hand, by mean hitting formular, $f(x,y)=-Z_{xy}/\pi_y$ and $f^*(y,x)=-Z^*_{yx}/\pi_x$. Since we have known $\pi_x Z_{xy}=\pi_y Z_{yx}^*$, we have $f(x,y)=f^*(y,x)$.
>
> On the other hand, by conditioning on the first step, (1)$f(x,y)=1+\sum_z p_{xz}f(z,y)$ and $f^*(y,x)=1+\sum_z p_{yz}^*f^*(z,x)$. This gives (2)$f(x,y)=1+\sum_z p_{yz}^*f(x,z)$.
>
> Let $(\hat X_t,\hat Y_t)$ be the positions of cat and mouse after $t$ moves according to some strategy. Consider $W_t=t+f(\hat X_t,\hat Y_t)$. By (1) and (2), one can verify $W_t$ is a martingale. By optional stopping theorem, $E_{(x,y)}W_0=E_{(x,y)}W_M$, i.e., $f(x,y)=E_{(x,y)}M+E_{(x,y)}f(\hat X_M,\hat Y_M)$. Since $\hat X_M=\hat Y_M$ and $f(z,z)=-E_\pi T_z$, we can get the result.
>
> _Remark_ If the chain is symmetry, one can get $E_{(x,y)}M=E_x T_y$. If the chain is reversible (but not necessarily symmetry) $x_0=\arg \min_z E_\pi T_z$ and $y_0=\arg\max_z E_\pi T_z$,since $E_\pi T_{x_0}+E_{x_0}T_{y_0}=E_\pi T_{y_0}+E_{y_0}T_{x_0}$, we have $E_{y_0}T_{x_0}\le E_{(x_0,y_0)}M\le E_{x_0}T_{y_0}$. The bound can be attained by fixing one animal at his initial state (when $f(\hat X_M,\hat Y_M)$ can take the minimal and maximal). In general the bound may not be attained.

#### 3.1.2 Entry-wise ordered transition matrices

> [!Tip] 
>
> _Recall_ Pick $f\in \mathbf R^I$ s.t. $E_\pi f(X_0)=0$, and define $S_t^f=\sum_{s=0}^{t-1} f(X_s)$,we have $\sigma^2(\mathbf P,f):=\lim_{t \to \infty} \frac{var S_t^f}{t}=f\Gamma f$, where $\Gamma_{ij}=\pi_i Z_{ij}+\pi_jZ_{ji}+\pi_i\pi_j-\pi_i\delta_{ij}$.

**Lemma 3.4 Peskun's Lemma** Let $\mathbf P^{(1)}$ and $\mathbf P^{(2)}$ be transition matrices of two reversible chains with identical stationary distribution which satisfies $p_{ij}^{(1)}\le p_{ij}^{(2)}\forall j\ne i$. For all $f$ with $E_\pi f(X_0)=0$, $\sigma^2(\mathbf P^{(1)},f)\ge\sigma^2(\mathbf P^{(2)},f)$.

### 3.2 Reversible chains and weighted graphs

_Convention_ A _graph_ has finite vertex-set $\mathcal V$ and edge-set $\mathcal E$, is connected and undirected, has no multiple edges and has no self-loops. In a _weighted graph_, each edge $(v,w)$ has a weight $w_{v,x}=w_{x,v}\in\mathbb R_+$ and self-loops are allowed. $w_v=\sum_x w_{vx}$ and $w=\sum_v w_v$.

**Definition** A discrete-time **random walk on a weight graph** is a Markov chain with state space $\mathcal V$ and transition matrix $p_{vx}=w_{vx}/w_v,x\ne v$. On a unweighted graph, set $w_{vx}=1\forall v,x$, i.e., $p_{vx}=1/d_v$ if $(v,x)$ is an edge and $0$ otherwise, where $d_v$ is the degree of $v$.

_Property_ This chain is <font color=red>reversible</font> with $\pi_v=w_v/w$ since $\pi_v p_{vx}=\pi_x p_{xv}=w_{vx}/w$. For unweighted graph, $\pi_v=d_v/2|\mathcal E|$. If the graph is regular (i.e., the degree of graphs are identical), the stationary distribution is uniform. 

This chain is irreducible since the graph is connected. 

Conversely, an irreducible and reversible graph can also be embedded into a graph by setting $\mathcal V=I$ and $w_{xv}=\pi_x p_{xv}$.

In continuous time, one can associate a random walk with a graph by 

(a) set $q_{vx}=w_{vx}/w_v$, which is the continuization of the discrete-time chain and thus has the same stationary distribution and mean hitting times. (mainly used) 

_Remark_ If we set $w_{xv}=\pi_x q_{xv}$, the resulting graph cannot determine the chain completely, since we can specify $\pi_i$ independently and solve for $q$'s. It's not the case for discrete-time chain since $\sum_v p_{xv}=1$ but $\sum_v q_{xv}$ is arbitrary. 

(b) $q_{vx}=w_{vx}$, which is called the _fluid model_, which has uniform stationary distribution.

**Lemma 3.5** For random walk on an n-vertex graph, $E_vT_v^+=w/w_v=2|\mathcal E|/d_v=n$ for weighted, unweighted, and unweighted regular graph respectively.

**Example 3.6 chess moves**

_Setting_ Start a knight at a corner square of an otherwise-empty chessboard. Move the knight at random, by choosing uniformly from the legal knight-moves at each step. What is the mean number of moves until the knight returns to the starting square?

_Solution_ Consider squares as vertices and all legal paths as edges, the knight is performing a random walk on a unweighted graph, with $E_v T_v^+=2|\mathcal E|/d_v=|\mathcal E|$. And $|\mathcal E|=168$.

**Lemma 3.7** Given an edge $(v,x)$ and define $U=\min_t\{X_t=v,X_{t-1}=x \}$ then $E_v U=w/w_{vx}=2|\mathcal E|$ for weighted and unweighted graph respectively. 

> _proof_ Consider $(X_{t-1},X_t)$ which is a Markov chain whose state space is $\vec{\mathcal E}$. One can verify $\rho(v,x)=w_{vx}/w$ is the stationary distribution (Notice this chain is not reversible! Verify balanced equation).

**Corollary 3.8 The edge-commute inequality** For an edge $(v,x)$, $E_v T_x+E_xT_v\le w/w_{vx},2|\mathcal E|$ for weighted and unweighted graph.

> _proof_ It suffices to show $E_v T_x+E_x T_v\le E_v U$. Let $T_x^v,T_v^x,T_U^v$ denote these times. Suppose the chain starts from $v$. From $T_x^v$ on, $T_v^x$ denote the first time when the chain hits $x$ and $T_U^v-T_x^v$ denote the first time when the chain hits $v$ through path $(x,v)$. The chain hits $v$ either through $(x,v)$ or from some other paths, so $T_v^x\le T_U^v-T_x^v$. Take expectations.

**Lemma 3.9** If $|\mathcal V|=n$, $\sum_{e=(v,x)\in \mathcal E} w_e(E_v T_x+E_x T_v)=w(n-1)$.

> _proof_ 
> $$
> LHS=\frac{1}{2}\sum_v\sum_xw_{vx}(E_vT_x+E_xT_v)=\sum_v\sum_x w_{vx}E_xT_v=\sum_v\sum_x w\pi_vp_{vx}E_xT_v=\sum_v w\pi_v(E_vT_v^+-1)=w(n-1)
> $$
>

#### 3.2.1 The fluid model

_Setting_ Imagine there are finite number of identical buckets which can hold unit quantity of fluid. Tubes connect these buckets through their bottoms, which consists of a graph. If bucket $i$ and $j$ with amount of fluid $p_i>p_j$ are connected by a tube with parameter $w_{ij}$, the flow rate from $i$ to $j$ through this tube is $w_{ij}(p_i-p_j)$. Denote the quantity of fluid in bucket $i$ at time $t$ by $p_i(t)$, we have 
$$
\frac{d}{dt}p_{j}(t)=\sum_{i\ne j}w_{ji}(p_j(t)-p_i(t))
$$
which is exactly **forward equations** for a cts-time chain with $q_{ij}=w_{ij}$. 

Intuitionally, $\lim_{t \to \infty}p_j(t)$ will be identical for all $j$, which agrees with the fact that the fluid model has uniform stationary distribution. 

### 3.3 Electrical networks

#### 3.3.1 Flows

**Definition** 

- A **flow** $\mathbf f=(f_{ij})$ on a graph satisfies: if $(i,j)\in\mathcal E$, $f_{ij}=-f_{ji}$, otherwise $f_{ij}=f_{ji}=0$. $f_{(i)}=\sum_{j\ne i}f_{ij}$ is the flow out of $i$. By symmetry, $\sum_i f_{(i)}=0$. 

- Given $A,B\subset\mathcal V,A\cap B=\emptyset$, a **unit flow from B to A** is a flow satisfying $\sum_{i\in B}f_{(i)}=1$ and $f_{(j)}=0\forall j\notin A\cup B$.

From a Markov chain $X$, we can define a special flow as follows: Given $A\subset\mathcal V$ and $v_0\notin A$, define $f^{v_0\to A}$ by $f_{ij}=E_{v_0}\sum_{t=1}^{T_A}(1_{X_{t-1}=i,X_t=j}-1_{X_{t-1}=j,X_t=i})$. 

1. $f_{ij}$ is the mean number of transitions $i\to j$ minus the mean number of transitions from $j\to i$ for the chain starting at $v_0$ and running until hitting $A$. 

2. This is a unit flow from $v_0$ to $A$, since
   $$
   f_{(i)}=\sum_{j\ne i}f_{ij}=E_{v_0}\sum_{t=1}^{T_A}\sum_{j\ne i}(1_{X_{t-1}=i,X_t=j}-1_{X_{t-1}=j,X_t=i})=E_{v_0}\sum_{t=1}^{T_A}1_{X_{t-1}=i}-1_{X_t=i}=E_{v_0}1_{X_0=i}-1_{X_{T_A}=i}
   $$

#### 3.3.2 The analogy

**Motivation** Given a weighted graph, consider it as an electrical network, where a wire linking $v$ and $x$ has conductance $w_{vx}$. Fix $v_0\in \mathcal V,A\subset\mathcal V,v_0\notin A$, apply voltage $1$ at $v_0$ and voltage $0$ at $A$ (ground $A$), and denote $g$ to be the voltage. By Ohm's law, $I_{vx}=(g(v)-g(x))w_{vx}$. So $I$ is a flow. By Kirchhoff's node law, $I_{(v)}=0\forall v\notin\{v_0\}\cup A$. 

**Definition** A **electrical network** is a weighted graph with a function $g$ and flow $I$ representing voltage and current respectively, satisfying $I_{vx}=(g(v)-g(x))w_{vx}$, $I_{(v)}=0\forall v\notin \{v_0\}\cup A$, and normalization condition $g(v_0)=1,g\mid_A=0$.

From two laws, $g$ satisfies the Dirichlet problem $\begin{cases}g(v)=\sum_x p_{vx} g(x),v\notin \{v_0\}\cup A\\g(v_0)=1,g(x)=0\forall x\in A\end{cases}$, so $g$ is uniquely determined. 

**Proposition 3.10** (a) $g(v)=P_v(T_{v_0}<T_A)$ (b) $I_{vx}=f_{vx}/r$, where $\mathbf f=\mathbf f^{v_0\to A}$ and $r=(w_{v_0}P_{v_0}(T_A<T_{v_0}^+))^{-1}$.

> _proof_ (a) The unique solution to the Dirichlet problem is $g(v)=E_v g(X_{T_A\cup\{v_0\}})=P_v(T_{v_0}<T_A)$.
>
> (b) To prove $f_{vx}/r=(g(v)-g(x))w_{vx}$, we just compute via mean hitting times. First, since the chain stops at $A$, one can collapse $A$ into a singleton $a$. For ease of notation let $N_t(x)$ be the number of visits to $a$ before time $t$,
> $$
> \begin{aligned}
> f_{vx}&=E_{v_0}N_{T_a}(v)p_{vx}-E_{v_0}N_{T_a}(x)p_{xv}\\&=_\text{Lemma 2.9}\pi_v(E_{v_0}T_a+E_a T_v-E_{v_0}T_v)p_{vx}-\pi_x(E_{v_0}T_a+E_a T_x-E_{v_0}T_x)p_{xv}\\&=\frac{w_{vx}}{w}[E_a T_v-E_aT_x+E_{v_0}T_x-E_{v_0}T_v]
> \end{aligned}
> $$
> Meanwhile,
> $$
> \begin{aligned}g(v)&=P_v(T_{v_0}<T_a)=\frac{E_vT_a+E_aT_{v_0}-E_vT_{v_0}}{E_{v_0}T_a+E_a T_{v_0}}\\\Rightarrow r(g(v)-g(x))w_{vx}&=r\frac{E_vT_a-E_xT_a-E_vT_{v_0}+E_xT_{v_0}}{E_{v_0}T_a+E_aT_{v_0}}w_{vx}
> \end{aligned}
> $$
> By cyclic tour property,
> $$
> E_aT_v+E_vT_{v_0}+E_{v_0}T_x+E_xT_a=E_aT_x+E_xT_{v_0}+E_{v_0}T_v+E_vT_a
> $$
> which gives
> $$
> \begin{aligned}
> r(g(v)-g(x))w_{vx}&=r\frac{wf_{vx}/w_{vx}}w_{vx}{E_{v_0}T_a+E_aT_{v_0}}\\&=\frac{wf_{vx}/w_{vx}}{w_{v_0}P_{v_0}(T_a<T_{v_0}^+)}\pi_{v_0}P_{v_0}P(T_a<T_{v_0}^+)w_{vx}\\&=f_{vx}
> \end{aligned}
> $$
> For $I_{(v)}=0\forall v\notin A\cup\{v_0\}$, notice this follows from the definition of $\mathbf f$.
>
> _Remark_ Notice $I_{(v_0)}=1/r=g(v_0)/r$. So here $r$ is the _effective resistance between $v_0$ and $A$_, i.e., we regard the whole network as effectively a single conductor from $v_0$ o $A$, whose resistance is $r$.

#### 3.3.3 Mean commute times

**Corollary 3.11 commute interpretation of resistance** Given two vertices $v,a$ in a weighted graph, the effective resistance $r_{va}$ is related to the mean commute time between $v$ and $a$, i.e., $E_vT_a+E_aT_v$, by $E_vT_a+E_aT_v=wr_{va}$.

_Remark_ If $a$ and $v$ are subsets of $\mathcal V$ this may be false.

_Remark_ When $(v,a)\in\mathcal E$, since $r_{va}\le w_{va}^{-1}$, this implies **Corollary 3.8**.

> [!Note]
>
> The operations on electric network, i.e., cutting an edge or decreasing an edge's conductance can increase an effective resistance, while shorting two vertices or increasing an edge's conductance can decrease an effective resistance, which can be used to bound the mean commute times in complex networks, e.g., infinite vertces.

#### 3.3.4 Foster's theorem

**Corollary 3.12 Foster's theorem** In a weighted $n$-vertex graph, let $r_e$ be the effective resistance between the ends of an edge $e$, then $\sum_e r_e w_e=n-1$.

_Remark_ This is the rephrase of **Lemma 3.9** in the view of commute interpretation of resistance.

==From now on, all chains are finite state, irreducible and reversible.==

### 3.4 The spectral representation

Let $\mathbf\Pi=\text{diag}(\pi_i)$. Let $s_{ij}=\pi_i^{1/2}p_{ij}\pi_j^{-1/2}$,i.e., $\mathbf S=\sqrt{\mathbf\Pi}\mathbf P\sqrt{\mathbf\Pi}^{-1}$, then $\mathbf S$ is symmetric. 

- Spectrum decomposition gives $\mathbf S=\mathbf U\mathbf \Lambda\mathbf U^T$ where $\mathbf U\in O(n)$ and $\mathbf \Lambda=\text{diag}(\lambda_n)$ with $1=\lambda_1>\lambda_2\ge...\ge \lambda_n\ge -1$ (Perron Frobenius theorem), moreover $\mathbf P=\sqrt{\mathbf\Pi}^{-1}\mathbf U\mathbf \Lambda\mathbf U^T\sqrt{\mathbf\Pi}$. 
- The right eigenvector of $\lambda_i$ of $\mathbf S$ is $(u_{ji})_{j=1}^n$, of $\mathbf P$ is $(u_{ji}\pi_j^{-1/2})_{j=1}^n$; the left eigenvector of $\lambda_i$ of $\mathbf S$ is the same and of $\mathbf P$ is $(u_{ji}\pi_j^{1/2})_{j=1}^n$.
- $\lambda=1$ corresponds the eigenvector $\mathbf u_1=(\sqrt{\pi_i})_{i=1}^n$. Uniqueness of the stationary distribution also implies $\lambda_2<1$.

In cts-time case, $\mathbf P$ is replaced by $-\mathbf Q$. The eigenvalues satisfy $0=\lambda_1<\lambda_2\le...\le\lambda_n$.

For matrix powers, $\mathbf S^{t}=\mathbf U\mathbf \Lambda^t\mathbf U^T$ and $\mathbf P^t=\sqrt{\mathbf\Pi}^{-1}\mathbf U\mathbf \Lambda^t\mathbf U^T\sqrt{\mathbf\Pi}$.

- **Spectral representation formula** $p_{ij}^{(t)}=\pi_i^{-1/2}\pi_j^{1/2}\sum_{m=1}^n u_{im}\lambda_m^t u_{jm}$.

  **Analogue in cts time** $p_{ij}^{(t)}=\pi_i^{-1/2}\pi_j^{1/2}\sum_{m=1}^n \exp(-\lambda_m t)u_{im}u_{jm}$.

- For a special case, we can consider a continuization of a discrete-time chain $Y_t=X_{N(t)}$ where $N(t)\sim P_1(t)$, we have 
  $$
  P_i(Y_t=j)=\pi_i^{-1/2}\pi_j^{1/2}\sum_{m=1}^n u_{im}u_{jm}\sum_{\nu=0}^\infty\lambda_m^\nu\frac{e^{-t}t^\nu}{\nu!}=\pi_i^{-1/2}\pi_j^{1/2}\sum_{m=1}^n u_{im}u_{jm}e^{-(1-\lambda_m)t}
  $$
  whence we find the orthonormal matrices are identical, and the eigenvalues $\tilde\lambda_m=1-\lambda_m$.

- For cts-time, we have 
  $$
  P_i(Y_t=j)=\pi_j+\pi_i^{-1/2}\pi_j^{1/2}\sum_{m=2}^nu_{im}u_{jm}e^{-\lambda_m t}\Rightarrow P_i(Y_t=j)-\pi_j=Ce^{-\lambda_2 t}+o(e^{-\lambda_2 t})
  $$
  So $\lambda_2$ can be interpreted as the asymptotic rate of convergence to stationary distribution.  By this, consider the **relaxation time** defined by $\tau_2=\lambda_2^{-1}$ for cts-time chain or $(1-\lambda_2)^{-1}$ for discrete-time chain.

- For cts-time, we have 
  $$
  \begin{aligned}
  p_{ij}^{(t)}-\pi_j&=\pi_i^{-1/2}\pi_j^{1/2}\sum_{m\ge 2}u_{im}u_{jm}\exp(-\lambda_m t)\Rightarrow Z_{ij}=\int_0^\infty p_{ij}^{(t)}-\pi_j dt=\pi_i^{-1/2}\pi_j^{1/2}\sum_{m\ge 2}u_{im}u_{jm}\lambda_m^{-1}\\
  p_{ii}^{(t)}-\pi_i&=\sum_{m\ge 2}u_{im}^2\exp(-\lambda_m t)\Rightarrow Z_{ii}=\int_0^\infty p_{ii}^{(t)}-\pi_i dt=\sum_{m\ge 2}u_{im}^2\lambda_m^{-1}
  \end{aligned}
  $$
  i.e., $\mathbf Z=\sqrt{\mathbf\Pi}^{-1}\mathbf U\mathbf \Lambda'\mathbf U^T\sqrt{\mathbf \Pi}$, where $\mathbf \Lambda'=\text{diag}(0,\lambda_2^{-1},...,\lambda_n^{-1})$.

  Moreover $\sum_i Z_{ii}=\sum_{m\ge 2}\lambda_m^{-1}$. This gives

**Proposition 3.13 The eigentime identity** For each $i$, in cts-time $\sum_j \pi_j E_i T_j=\sum_{m\ge 2}\lambda_m^{-1}$. In discrete time $\sum_j \pi_j E_i T_j=\sum_{m\ge 2}(1-\lambda_m)^{-1}$. 

#### 3.4.1 Mean hitting times and reversible chains

For reversible chains, many identities can be simplified.

**Corollary 3.14** $E_\pi T_j-E_\pi T_i=E_i T_j-E_j T_i$.

_Remark_ Define an ordering $i\preceq j$ iff $E_\pi T_i\le E_\pi T_j$, then $E_iT_j\ge E_j T_i$ iff $i\preceq j$.

_Remark_ **Corollary 3.14** doesn't imply $\arg\max_{i,j}E_iT_j=\arg\min_i E_\pi T_i,\arg\max_j E_\pi T_j$.

**Lemma 3.15** $\max_{ij}E_i T_j\le 2\max_k E_\pi T_k$.

> _proof_ $\sqrt{\Pi}\mathbf Z\sqrt{\Pi}^{-1}=\mathbf U\mathbf \Lambda'\mathbf U^T$ is positive-semidefinite. For $\mathbf A$ positive-semidefinite, $A_{ij}^2\le A_{ii}A_{jj}$. This gives $(Z_{ij}/\pi_j)^2\le (Z_{ii}/\pi_i)(Z_{jj}/\pi_j)$. Then by mean hitting time formula,
> $$
> E_i T_j=\frac{Z_{jj}}{\pi_j}-\frac{Z_{ij}}{\pi_j}\le2\max_k \frac{Z_{kk}}{\pi_k}=2\max_k E_\pi T_k
> $$
>

### 3.5 Complete monotonicity

One advantage of working in continuous time is to exploit complete monotonicity properties.

**Definition** If $f:\mathbb R_+\to \mathbb R_+$ satisfies that there is a measure $\mu\ge 0$ on $\mathbb R_+$ s.t. $f(t)=\int_{\mathbb R_+}e^{-\theta t}\mu(d\theta)$ is called **completely monotone**. Equivalently, $f$ is the Laplace transform of some nonnegative r.v..

Our application will use only the special case of finite sum, i.e., $f(t)=\sum_m a_m e^{-\theta_m t}$ where $a_m>0,\theta_m\ge 0$.

_Property_ $f'\le 0$ and $f''\ge 0$, which shows $f$ is convex. Moreover, $(\ln f)'\le 0$ and $(\ln f)''\ge 0$, along with $f(0)=0$, one can conclude $\ln f$ is super-additive, i.e., $f$ is super-multiplicative. 

_Remark_ If $f$ is CM, so is $-f'$ and $\bar F(t)=\int_t^\infty f(s)ds$.

**Definition** A probability distribution $\nu$ on $\mathbb R_+$ is called CM if its tail distribution function $\bar F(t)=\nu(t,\infty)$ is CM, or equivalently its density is CM.

_Remark_ In more probabilistic language, $\nu$ is CM iff there are independent r.v.'s $\xi\sim Exp(1)$ and $\lambda>0$ s.t. $\xi/\Lambda\sim \nu$.

**Definition** The **spectral gap** $\lambda\ge 0$ of CM function $f$ can be defined by $\lambda=\inf\{t>0:\mu[0,t]>0\}$. In discrete case, $\lambda=\min \theta_m$. For a distribution, $\lambda=\text{ess}\inf\Lambda$, which is exactly the spectral gap of $\bar F$.

_Remark_ The spectral gap controls the behavior of $f$ at $\infty$. 

CM functions can be bounded in terms of $f(0)$ and $f(\infty)$, i.e., 

**Lemma 3.16** Let $f$ be CM with $0<f(0)<\infty$. Then $\exp(\frac{f'(0)t}{f(0)})\le\frac{f(t)}{f(0)}\le\frac{\bar F(t)}{\bar F(0)}\le\exp(-\lambda t)$. When $\bar F(0)=\infty$, $\bar F(\infty)=\infty$ and $\lambda=0$, so it also holds.

> _proof_ WLOG $f(0)=1$, and write $f(t)=Ee^{-\Theta t}$ where $\Theta\sim\mu$.
>
> Consider $f'(t)=-E(\Theta e^{-\Theta t})$. Since $\theta\to e^{-\theta t}$ is decreasing, $\Theta$ and $e^{-\Theta t}$ are negatively correlated, which says $E(\Theta e^{-\Theta t})\le E\Theta Ee^{-\Theta t}$, i.e., $-f'(t)\le -f'(0)f(t)$, or $(\log f(t))'\ge f'(0)$. This gives the leftmost inequality.
>
> Consider $\bar F(t)=E(\Theta^{-1}e^{-\Theta t})\ge E\Theta^{-1}Ee^{-\Theta t}=\bar F(0)f(t)$, which gives the middle inequality.
>
> Consider $f(t)=\int_0^\infty e^{-\theta t}\mu(d\theta)=e^{-\lambda t}\int_\lambda^\infty e^{-\theta (t-\lambda)}\mu(d\theta)\le e^{-\lambda t}$. Since $\bar F$ has the same spectral gap as $f$, the rightmost inequality also holds.

**Application to reversible Markov chain** By spectrum representation, $p_{ii}^{(t)}-\pi_i$ is CM. 

More generally, for $g\in \mathbf R^I$, $\rho(t)=E[g(X_t)g(X_0)]$​ is CM for stationary chain, since 
$$
\rho(t)=\sum_{i=1}^n \pi_i g(i)\sum_{k=1}^n p_{ik}^{(t)}g(k)=\sum_{i=1}^n \pi_i g(i)\sum_{k=1}^n \pi_i^{-1/2}\pi_j^{1/2}\sum_{m=1}^nu_{im}u_{jm}\exp(-\lambda_m t)g(k)=\sum_{m=1}^n(\sum_i \pi_i^{1/2}g(i)u_{im})^2\exp(-\lambda_m t)
$$
Pick $g=1_A$, $P(X_t\in A\mid X_0\in A)$ is CM for stationary chain. 

#### 3.5.1 Lower bounds on mean hitting times

**Lemma 3.17** For any state $i$ in a cts-time chain, $\frac{(1-\pi_i)^2}{q_i\pi_i}\le E_\pi T_i\le \frac{\tau_2(1-\pi_i)}{\pi_i}$, where $q_i=\sum_{j\ne i}q_{ij}$ is the exit rate and $\tau_2=\lambda_2^{-1}$ is the relaxation time.

From continuization the lemma holds in discrete time, replacing $q_i$ by $1-p_{ii}$.

> _proof_ Since $f(t):=p_{ii}^{(t)}-\pi_i$ is CM, from **Lemma 3.16**,
> $$
> \exp(\frac{-q_it}{1-\pi_i})\le\frac{f(t)}{1-\pi_i}\le\exp(-\lambda_2 t)
> $$
> Since $E_\pi T_i=\pi_i^{-1}Z_{ii}=\pi_i^{-1}\int_0^\infty f(t)dt$, integrate the inequality and we have the result.

**Proposition 3.18** For a discrete-time chain on $n$ states, 

(a)$\sum_j \pi_j E_\pi T_j\ge (n-1)^2/n$

(b) $\max_{i,j}E_i T_j+E_j T_i\ge 2(n-1)$

(c) $\max_{i,j} E_i T_j\ge n-1$

(d) $\tau_2\ge (n-1)/n$.

equality holds when the graph is complete.

> _proof_ Work on continuized chain, where $q_i=1-p_{ii}<1$. 
>
> (a) By **Lemma 3.17** and Cauchy's inequality,
> $$
> \sum_j \pi_j E_\pi T_j\ge\sum_j (1-\pi_j)^2/q_j\ge \sum_j (1-\pi_j)^2=n-2+\sum_j \pi_j^2\ge n-2+1/n=(n-1)^2/n
> $$
> (b) This is proved via contradiction. Suppose $E_iT_j+E_jT_i<2(n-1)\forall i,j$.
>
> Let $\tau_0=\sum_j \pi_j E_k T_j$, which doesn't depend on $k$ by random target lemma. Then 
> $$
> \begin{aligned}
> &\sum_{j\ne i}\frac{\pi_j}{1-\pi_i}(E_i T_j+E_j T_i)=\frac{\tau_0+E_\pi T_i}{1-\pi_i}<\sum_{j\ne i}\frac{\pi_j}{1-\pi_i}2(n-1)=2(n-1)\\\Rightarrow&2\tau_0=\sum_i \pi_i(\tau_0+E_\pi T_i)<\sum_i 2(n-1)\pi_i(1-\pi_i)=2(n-1)(1-\sum_i \pi_i^2)=\frac{2(n-1)^2}{n}
> \end{aligned}
> $$
> which contradicts (a). 
>
> (c) This follows from (b).
>
> (d) By **Lemma 3.17**, $\tau_2\ge \pi_i E_\pi T_i/(1-\pi_i)$. This gives 
> $$
> \tau_2(n-1)=\sum_i \tau_2 (1-\pi_i)\ge\sum_i\pi_i E_\pi T_i\ge (n-1)^2/n
> $$
> which is (d).

**Corollary 3.19** $\text{var}_i T_i^+\ge (1-\pi_i)(1-2\pi_i)/\pi_i^2$.

> _proof_ 
> $$
> \text{var}_i T_i^+=\frac{2E_\pi T_i+1}{\pi_i}-\frac{1}{\pi_i^2}\ge \frac{2(1-\pi_i)^2/(1-p_{ii})+\pi_i-1}{\pi_i^2}\ge\frac{(1-2\pi_i)(1-\pi_i)}{\pi_i^2}
> $$
>

#### 3.5.2 Smoothness of convergence

**Lemma 3.20** 

(a) $\sum_j p_{ij}^2(t)/\pi_j=p_{ii}(2t)/\pi_i$

(b) $|\frac{p_{ik}(t+s)}{\pi_k}-1|\le\sqrt{(\frac{p_{ii}(2t)}{\pi_i}-1)(\frac{p_{kk}(2s)}{\pi_k}-1)}$.

(c) $\frac{p_{ik}(t+s)}{\pi_k}\le\sqrt{\frac{p_{ii}(2t)}{\pi_i}\frac{p_{kk}(2s)}{\pi_k}}$.

(d) $\max_{i,k}\frac{p_{ik}(2t)}{\pi_k}\le\max_{i}\frac{p_{ii}(2t)}{\pi_i}$.

> _proof_ 
>
> (a) 
> $$
> \sum_j \frac{p_{ij}^2(t)}{\pi_j}=\sum_j p_{ij}(t)\frac{p_{ji}(t)}{\pi_i}=\frac{p_{ii}(2t)}{\pi_i}
> $$
> (b) First we have 
> $$
> \begin{aligned}
> \bigg|\frac{p_{ik}(t+s)}{\pi_k}-1\bigg|&=\bigg|\sum_j \frac{p_{ij}(t)p_{jk}(s)}{\pi_k}-1 \bigg|=\bigg|\sum_j \frac{p_{ij}(t)p_{kj}(s)}{\pi_j}-1 \bigg|\text{ by reversibility}\\&=\bigg| \sum_j \pi_j\frac{p_{ij}(t)-\pi_j}{\pi_j}\frac{p_{kj}(t)-\pi_j}{\pi_j} \bigg|\le\sum_j \pi_j\bigg| \frac{p_{ij}(t)-\pi_j}{\pi_j} \bigg|\bigg| \frac{p_{kj}(t)-\pi_j}{\pi_j} \bigg|\\
> \bigg| \frac{p_{ii}(2t)}{\pi_i}-1 \bigg|&=\sum_j\frac{(p_{ij}(t)-\pi_j)^2}{\pi_j}\end{aligned}
> $$
> Then by Cauchy inequality,
> $$
> \begin{aligned}
> \\\Rightarrow (\frac{p_{ii}(2t)}{\pi_i}-1)(\frac{p_{kk}(2s)}{\pi_k}-1)&=\sum_j\frac{(p_{ij}(t)-\pi_j)^2}{\pi_j}\sum_j\frac{(p_{kj}(s)-\pi_j)^2}{\pi_j}\\&\ge(\sum_j\frac{|(p_{ij}(t)-\pi_j)(p_{kj}(s)-\pi_j)|}{\pi_j}  )^2 \\&=(\bigg|\frac{p_{ik}(t+s)}{\pi_k}-1\bigg|)^2
> \end{aligned}
> $$
> (c) Apply Cauchy inequality.
>
> (d) Corollary from (c)

From (a), if $X_t\sim \theta_t^i$ where $X_0=i$, we have $\|\theta_t^i-\pi\|_2^2=\frac{p_{ii}(2t)}{\pi_i}-1$. 

- $\|\theta_t^i-\pi\|_2$ decreases w.r.t. $t$ by the spectrum representation of $p_{ii}(t)$.
- The rate of global convergence, $\|\theta_t^i-\pi\|_2$, is controlled by the convergence rate of $p_{ii}(2t)$ to $\pi_i$.

#### 3.5.3 Inequalities for hitting time distributions on subsets

_Warning_ Most of simple identities for mean hitting times on singletons have no simple analogs for that on subsets.

_Exception_ Recall **Kac's formular** $E_{\pi_A}T_A^+=1/\pi(A)$.

But we can attain inequalities for reversible chains. Below are results.

**Definition** The **ergodic exit distribution** $\rho_A$ from $A$ is defined by $\rho_A(j)=\frac{\sum_{i\in A}\pi_i q_{ij}}{Q(A,A^c)}$, where $Q(A,A^c)=\sum_{i\in A}\sum_{k\in A^c}\pi_i q_{ik}$ is the **ergodic flow rate** out of $A$. By stationary $Q(A,A^c)=Q(A^c,A)$.

**Proposition 3.21** For a cts-time chain and fixed $A\subset I$,

(i) If $X_0\sim\pi$ or $X_0\sim \pi_{A^c}$ or $X_0\sim \rho_A$, $T_A$ has CM distribution.

(ii) The distribution of $T_A$ from the three initial distribution is connected by $P_\pi(T_A>t)=\pi(A^c)P_{\pi_{A^c}}(T_A>t)$ and $P_{\pi_{A^c}}(T_A\in(t,t+dt))=\frac{P_{\rho_A}(T_A>t)}{E_{\rho_A}T_A}dt$.

(iii) The spectral gap $\lambda_A$ of $T_A$ is identical for three distribution and $P_{\rho_A}(T_A>t)\le P_{\pi_{A^c}}(T_A>t)=\frac{P_\pi (T_A>t)}{\pi(A^c)}\le\exp(-\lambda_A t)$. In particular, $\frac{\pi(A^c)}{Q(A,A^c)}=E_{\rho_A}T_A\le E_{\pi_{A^c}}T_A=\frac{E_\pi T_A}{\pi(A^c)}\le 1/\lambda_A$

(iv) $E_\pi T_A\le \tau_2 \pi(A^c)/\pi(A)$.

> _proof_ 
>
> (i) First, consider the case when $A$ is a singleton and we prove if $X_0\sim \pi_{I\backslash\{a\}}$, $T_A$ is CM.
>
> Consider the "trapped" process $\tilde X_t$, i.e., $q_{aj}=0\forall j\ne a$, where we have $P_{\pi_{I\backslash\{a\}}}(T_a>t)=P_{\pi_{I\backslash\{a\}}}(\tilde X_t\in I\backslash\{a\})$. Recall that $P(\tilde X_t\in A\mid \tilde X_0\in A)$ is CM, so RHS is CM. Now we make it rigorous. Consider the modified chain $X^\epsilon_t$ where $q_{ij}^\epsilon=q_{ij},i\ne a;q_{aj}^\epsilon=\epsilon q_{aj}$. One can verify the chain is also reversible, with stationary distribution $\pi_i^\epsilon=b_1\pi_i,i\ne a;\pi_a^\epsilon=b_2$. Push $\epsilon\to 0$, we have $P_{\pi_{I\backslash\{a\}}}(X_t^\epsilon\in I\backslash\{a\})\to P_{\pi_{I\backslash\{a\}}}(T_a>t)$. LHS is CM. By the continuity of Laplace transform, RHS is CM. 
>
> By collapsing principle, when $X_0\sim \pi_{A^c}$, $T_A$ is CM. 
>
> (ii) The first is trivial by conditioning on $X_0$. For the second, we have $P_\pi(T_A\in(t,t+dt))=Q(A,A^c)P_{\rho_A}(T_A>t)dt,t>0$ and $Q(A,A^c)/\pi(A^c)=1/E_{\rho_A}T_A$, referring to **Section 2.5.1**.
>
> Return to (i), by (ii), we know when $X_0\sim\pi$ or $\rho_A$, $X_t$ is also CM.
>
> (iii) The first claim follows from (ii) and the spectrum representation. For the first chain of inequality, notice it's just corollary of **Lemma 3.16**. Integrate this, and we can attain the second chain. 
>
> (iv) By **Lemma 3.17** and collapsing principle, $E_\pi T_A\le \tau_2\pi(A^c)/\pi(A)$.

_Remark_ In discrete time, $q_{ij}$ are replaced by $p_{ij}$.

#### 3.5.4 Approximate exponentiality of hitting times

_Motivation_ For $A\subset I$, when $\pi(A)$ is small, the distribution of $T_A$ can be approximated by an exponential distribution with equal mean. Below are two measures for the approximation.

**Proposition 3.22** If $T$ has a CM distribution, $\sup_t|P(T>t)-e^{-t/ET}|\le \frac{ET^2}{2(ET)^2}-1$.

**Proposition 3.23** For $A\subset I$, $\sup_t|P_\pi (T_A>t)-\exp(-t/E_\pi T_A)|\le \tau_2/E_\pi T_A$.

### 3.6 Extremal characterizations of eigenvalues

#### 3.6.1 The Dirichlet formalism

**Definition** A reversible chain has an associated **Dirichlet form** $\mathcal E$ defined as follows: In discrete time, for $g\in \mathbf R^I$, $\mathcal E(g,g)=\frac{1}{2}\sum_i\sum_{j\ne i}\pi_i p_{ij}(g(j)-g(i))^2$. In continuous time $p_{ij}$ is replaced by $q_{ij}$. 

- In discrete time,
  $$
  \mathcal E(g,g)=\frac{1}{2}E_\pi(g(X_1)-g(X_0))^2=E_\pi[g(X_0)(g(X_0)-g(X_1))]
  $$
  
- In continuous time
  $$
  \mathcal E=\lim_{t \to 0}t^{-1}\frac{1}{2}E_\pi (g(X_t)-g(X_0))^2=\lim_{t \to 0}t^{-1}E_\pi[g(X_0)(g(X_t)-g(X_0))]=-\sum_i\sum_j \pi_i g(i) q_{ij} g(j)
  $$

- For RW on weighted graph, 
  $$
  \mathcal E(g,g)=\frac{1}{2}\sum_i\sum_{j\ne i}\frac{w_{ij}}{w}(g(j)-g(i))^2
  $$

**Lemma 3.24** If $X_t\sim \rho(t)$, let $f_j(t)=\rho_j(t)/\pi_j$, one have $\frac{d}{dt}\|\rho(t)-\pi\|_2^2=-2\mathcal E(f(t),f(t))$.

> _proof_ First, $\|\rho(t)-\pi\|_2^2=\sum_j \pi_j^{-1}\rho_j^2(t)-1$. By forward equations $\rho_j'(t)=\sum_i \rho_i(t) q_{ij}$, we have 
> $$
> \frac{d}{dt}\|\rho(t)-\pi\|_2^2=\sum_j \pi_j^{-1}2\rho_j(t)\sum_i \rho_i(t)q_{ij}=\sum_i\sum_j 2f_j(t)f_i(t)\pi_i q_{ij}= -2\mathcal E(f(t),f(t))
> $$

#### 3.6.2 Summary of extremal characterizations

**Extremal characterization of relaxation time** the relaxation time is $\tau_2=\sup\{\|g\|_2^2/\mathcal E(g,g): \sum_i \pi_i g(i)=0 \}$.

**Extremal characterization of quasi-stationary mean hitting time** The quasi-stationary mean exit time is $E_{\alpha_A} T_A=\sup\{\|g\|_2^2/\mathcal E(g,g):g\ge 0, g\mid_A=0 \}$

**Extremal characterization of mean commute times** For $i\ne j$, $E_iT_j+E_jT_i=\sup\{1/\mathcal E(g,g):0\le g\le 1,g(i)=1,g(j)=0 \}$.

#### 3.6.3 The extremal characterization of relaxation time

**Rayleigh-Ritz extremal characterization of eigenvalues** For $S$ a self-adjoint matrix under $<\cdot,\cdot>$ with eigenvalues $\mu_1\ge \mu_2\ge...$, $\mu_1=\sup_\mathbf x\frac{\langle\mathbf x,S\mathbf x\rangle}{\langle\mathbf x,\mathbf x\rangle}$, with supremum taken by the eigenvalue of $\mu_1$, and $\mu_2=\sup_{\langle\mathbf y,\mathbf x\rangle=0 }\frac{\langle\mathbf y,S\mathbf y\rangle}{\langle\mathbf y,\mathbf y\rangle}$, with supremum taken by the eigenvalue of $\mu_2$. 

**Application to Dirichlet form** Take $\langle\mathbf x,\mathbf y\rangle=\mathbf x^T\Pi\mathbf y$, where $\Pi=\text{diag}(\pi_i)$. Notice under this inner product, $P$ is self-adjoint when the chain is reversible. Moreover, the Rayleigh quotient $\frac{\langle\mathbf x,P\mathbf x\rangle}{\langle\mathbf x,\mathbf x\rangle}=1-\frac{\mathcal E(\mathbf x,\mathbf x)}{\|\mathbf x\|_2^2}$. 

_Proof of Extremal characterization of relaxation time_ Since $\lambda_1$ corresponds the right eigenvector $\mathbf 1$,  $\tau_2=1/(1-\lambda_2)=\sup_{\langle\mathbf x,\mathbf 1\rangle=0}\frac{\langle\mathbf x,\mathbf x\rangle}{\langle\mathbf x,P\mathbf x\rangle}$.

**Discussion on $g$** (In cts-time) Suppose $g$ is the function attaining the supremum and $\|g\|_2=1$, then $g$ should be the right eigenvector of $\lambda_2$. Consider its corresponding left eigenvector $\theta$ given by $\theta_i=\pi_i g(i)$ (Assume $\lambda_2$ has multiplicity 1), which is a signed measure.

Since $\theta Q=\lambda_2 \theta$, as it evolve, $\theta(t)=\theta e^{-Q_t}=\theta e^{-\lambda_2 t}=\theta e^{-t/\tau_2}$. For any signed measure $\nu$ with $\sum_i \nu_i=0$, notice $\nu\perp \mathbf1$, so consider $V=\mathbf R^{|I|}/\langle\mathbf 1\rangle$, $\nu\in V$, and we have $\nu(t)\approx ce^{-t/\tau_2}\theta$, where $c\theta$ is the projection on $\langle\theta\rangle$, $c=\sum_i \nu_i g(i)$.. In this sense, $\theta$ is the signed measure which relaxes to $0$ most slowly. 

For a probability measure $\rho$, apply these to $\rho-\pi$, we have $\rho(t)-\pi\approx ce^{-t/\tau_2}\theta$. If $\rho(i)=1$, $\rho(t)-\pi\approx g(i) e^{-t/\tau_2}\theta$. So $\theta$ can be regarded as the asymptotic normalized difference between the true distribution at time $t$ and the stationary distribution. $g_0$ can be regarded as the asymptotic normalized size of deviation from stationarity, as a function of the starting state.

#### 3.6.4 Simple applications

**Estimation on the convergence rate**

**Lemma 3.26 $L^2$ contraction lemma** For a cts-time chain $X_t$, if $X_t\sim \rho(t)$, then $\|\rho(t)-\pi\|_2\le e^{-t/\tau_2}\|\rho(0)-\pi\|_2$.

> _proof_ This is a Gronwall-type inequality. Let $f_j(t)=\rho_j(t)/\pi_j$, by **Lemma 3.24** and the extremal characterization of $\tau_2$ (notice $\langle f(t)-1,1\rangle=0$)
> $$
> \frac{d}{dt}\|\rho(t)-\pi\|_2^2=-2\mathcal E(f(t),f(t))=-2\mathcal E(f(t)-\vec1,f(t)-\vec1)\le-2\frac{\|f(t)-\vec1\|_2^2}{\tau_2}=\frac{-2}{\tau_2}\|\rho(t)-\pi\|_2^2
> $$
> Integrate this and we have $\|\rho(t)-\pi\|_2^2\le e^{-2t/\tau_2}\|\rho(0)-\pi\|_2^2$.

Alternatively, **Lemma 3.26** follows by observing that $\|\rho(t)-\pi\|_2^2$ is CM with spectral gap at least $2\lambda_2=2/\tau_2$.

> _proof_ 
>
> From the spectrum representation, one have 
> $$
> \rho_j(t)-\pi_j=\sum_i \rho_i(0)(p_{ij}^{(t)}-\pi_j)=\sum_i \rho_i(0)[\pi_i^{-1/2}\pi_j^{1/2}\sum_{m\ge 2}u_{im}u_{jm}\exp(-\lambda_m t)]
> $$
> By computation, let $g(i)=\rho_i(0)/\pi_i$, we have 
> $$
> \|\rho(t)-\pi\|_2^2=\sum_{m\ge 2}(\sum_i \pi_i^{1/2}g(i) u_{im})^2\exp(-\lambda_m t)
> $$

**Compare relaxation times of different chains on the same state space**

**Corollary 3.27** Given a chain with relaxation time $\tau_2$, let $\tau_2^A$ be the relaxation time of the chain with subset $A$ collapsed to a singleton $a$, then $\tau_2^A\le \tau_2$.

> _proof_ A function $g$ on the states of the collapsed chain can be extended to function $\tilde g$ on the original chain by setting $\tilde g(x)=g(a),x\in A$. 
>
> - $\sum_i \pi_i g(i)$ $\sum_i \pi_i g(i)=\sum_i \tilde\pi_i \tilde g(i)$ since $\tilde\pi_a=\sum_{i\in A} \pi_i$. For the same reason, $\|g\|_2^2=\|\tilde g\|_2^2$.
>
> -  $\mathcal E(g,g)$​ is also unchanged, since 
>   $$
>   \mathcal E(\tilde g,\tilde g)=-\sum_{i,j} \tilde\pi_i \tilde q_{ij}\tilde g(i)\tilde g(j)=-\sum_{i\in A^c,j\in A^c} \pi_i q_{ij}g(i)g(j)-\sum_{i\in A^c}\pi_i q_{ia}g(i)g(a)-\sum_{j\in A^c}\pi_aq_{ai} g(a)g(j)-\pi_aq_{aa}g(a)^2=-\sum_{i,j}\pi_i q_{ij}g(i)g(j)=-\mathcal E(g,g)
>   $$
>   from the definition of collapsed chain.
>
> By **Extremal characterization of relaxation time**, such $g$ attaining the supremum on collapsed chain has an extension $\tilde g$ that can be a test function for in the extremal characterization of $\tau_2$. So $\tau_2^A\le \tau_2$.

**Corollary 3.28** Let $\tau_2$ be the relaxation time for a "fluid model" cts-time chain on a graph weighted by $(w_e)$ and $\tau_2^*$ corresponds to $(w_e^*)$. If $w_e^*\ge w_e\forall e$, then $\tau_2^*\le \tau_2$.

> _proof_ Since $\mathcal E^*(g,g)\ge\mathcal E(g,g)$, by **extremal characterization of relaxation time** one can attain this.

**Lemma 3.29 The direct comparison lemma** Let $(w_e)$ and $(w_e^*)$ be edge-weights on a graph without self-edges, $(w_i),(w_i^*)$ be vertex-weights, $\tau_2,\tau_2^*$​ be relaxation times for associated RWs. Then
$$
\frac{\min_e(w_e/w_e^*)}{\max_i (w_i/w_i^*)}\le\frac{\tau_2}{\tau_2^*}\le \frac{\max_i (w_i/w_i^*)}{\min_e (w_e/w_e^*)}
$$

> _proof_ 
>
> For any $g$, on the one hand, $w^*\mathcal E^*(g,g)\ge w\mathcal E(g,g)\min_e (w_e^*/w_e)$. On the other hand, $w^*\|g\|_2^{*2}\le w\|g\|_2^2\max_i (w_i^*/w_i)$. 
>
> Now consider $\sum_i \pi_i^*g(i)=0$. Denote $b=\sum_i \pi_i g(i)$, one have 
> $$
> \frac{\|g\|_2^{*2}}{\mathcal E^*(g,g)}\le^1\frac{\|g-b\|_2^{*2}}{\mathcal E^*(g-b,g-b)}\le^2\frac{\|g-b\|_2^2}{\mathcal E(g-b,g-b)}\frac{\max_i (w_i^*/w_i)}{\min_e (w_e^*/w_e)}
> $$
> $^1$: $\|g\|_2^{*2}=\|g-b\|_2^{*2}+b^2$ by computation. $\mathcal E^*(g,g)=\mathcal E^*(g-b,g-b)$ by definition.
>
> $^2$: From above inequalities.
>
> Take supremum of LHS one have $\tau_2^*\le \tau_2\frac{\max_i (w_i^*/w_i)}{\min_e (w_e^*/w_e)}$. For the other side just reverse the roles of $w_e$ and $w_e^*$.

_Remark_ Sometimes $\tau_2$ are very sensitive to apparently small changes in the chain. 

> _Example_ Consider RW on an unweighted graph. If we add extra edges of small proportion, $\tau_2$ will change fast.
>
> _Fact_ For a complete graph, $\mathbf P$ has eigenvalue $1$ (single) and $-1/(n-1)$ ($n-1$ multiple). So $\tau_2=1-1/n$.
>
> **Example 3.30** Given two complete graphs with $n$ vertices $1,2,....,n$ and $1',2',...,n'$. If one join $1$ and $1'$, then $w=2[2\times\frac{n(n-1)}{2}+1]$ and $\tau_2\sim n^2/2$. If one join $i$ and $i'$ for all $i$, then $w=2[2\times\frac{n(n-1)}{2}+n]$ and $\tau_2\sim n/2$. Notice as $n$ increase, the proportion of added edges are both infinitesimal, but the relaxation time increases in different rate. Intuitively, in the former graph the walker is less likely to transfer to another graph than the latter. 
>
> **Example 3.31** Given a complete graph on $n$ vertices. Take $k=o(n^{1/2})$ new vertices and attach each to distinct vertices of the original complete graph. Then $w=n(n-1)+2k$ and $\tau_2$ is bounded. But if these $k$ vertices make up a complete graph, $w=n(n-1)+2k+k(k-1)$ but $\tau_2\sim k$. 

When $w_i=w_i^*$, comparison arguments are most effective. By embedding the reversible chain to the graph, we have

**Lemma 3.32 The direct comparison lemma** For transition matrices $\mathbf P$ and $\mathbf P^*$ with the same stationary distribution $\pi$, if $p_{ij}\ge \delta p_{ij}^*\forall j\ne i$, we have $\tau_2\le \delta^{-1}\tau_2^*$. 

#### 3.6.5 Quasi-stationary

**Definition** Given $A\subset I$, let $\mathbf P^A$ denote the restriction of $\mathbf P$ on $A^c$. Suppose $\mathbf P^A$ is irreducible, by Perron-Frobenius theorem there is a unique $\lambda_A\in(0,1)$ single, with left eigenvector $\alpha$ a distribution. Extend $\alpha$ to $\alpha_A$ by setting $\alpha_A\mid_A=0$ (Not necessarily left eigenvector of $\mathbf P$)  $\alpha_A$ is called **quasi-stationary distribution**. 

Moreover, $P_{\alpha_A}(X_n=j\mid T_A>n)=\alpha_A(j),j\in A^c$, since conditioned on $T_A>n$ the walker is walking on the restricted chain, where $\alpha_A$ is the stationary distribution. Meanwhile, $P_{\alpha_A}(X_n=j,T_A>n)=\alpha_A(\mathbf P^A)^n=\lambda_A^n \alpha_A$. These yields $P(T_A>n)=\lambda_A^n$. So $T_A\sim Geom(\lambda_A)$ and $E_{\alpha_A}T_A=1/(1-\lambda_A)$. $E_{\alpha_A}T_A$ is called the **quasi-stationary mean exit time**.

Similarly for cts-time chain, let $\mathbf Q^A$ be the restriction of $\mathbf Q$ on $A^c$. Suppose $\mathbf Q^A$ is irreducible, define similarly $\alpha_A$ and $E_{\alpha_A}T_A$. Here $T_A\sim Exp(\lambda_A)$, so $E_{\alpha_A}T_A=\lambda_A^{-1}$. Notice they are unchanged under continuization. 



