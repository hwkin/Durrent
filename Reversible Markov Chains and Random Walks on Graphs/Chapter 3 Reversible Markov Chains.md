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

_proof_ Consider the functions $f(x,y)=E_xT_y-E_\pi T_y$ and $f^*(y,x)=E_y^*T_x-E_\pi^* T_x$. 

On the one hand, by mean hitting formular, $f(x,y)=-Z_{xy}/\pi_y$ and $f^*(y,x)=-Z^*_{yx}/\pi_x$. Since we have known $\pi_x Z_{xy}=\pi_y Z_{yx}^*$, we have $f(x,y)=f^*(y,x)$.

On the other hand, by conditioning on the first step, (1)$f(x,y)=1+\sum_z p_{xz}f(z,y)$ and $f^*(y,x)=1+\sum_z p_{yz}^*f^*(z,x)$. This gives (2)$f(x,y)=1+\sum_z p_{yz}^*f(x,z)$.

Let $(\hat X_t,\hat Y_t)$ be the positions of cat and mouse after $t$ moves according to some strategy. Consider $W_t=t+f(\hat X_t,\hat Y_t)$. By (1) and (2), one can verify $W_t$ is a martingale. By optional stopping theorem, $E_{(x,y)}W_0=E_{(x,y)}W_M$, i.e., $f(x,y)=E_{(x,y)}M+E_{(x,y)}f(\hat X_M,\hat Y_M)$. Since $\hat X_M=\hat Y_M$ and $f(z,z)=-E_\pi T_z$, we can get the result.

_Remark_ If the chain is symmetry, one can get $E_{(x,y)}M=E_x T_y$. If the chain is reversible (but not necessarily symmetry) $x_0=\arg \min_z E_\pi T_z$ and $y_0=\arg\max_z E_\pi T_z$,since $E_\pi T_{x_0}+E_{x_0}T_{y_0}=E_\pi T_{y_0}+E_{y_0}T_{x_0}$, we have $E_{y_0}T_{x_0}\le E_{(x_0,y_0)}M\le E_{x_0}T_{y_0}$. The bound can be attained by fixing one animal at his initial state (when $f(\hat X_M,\hat Y_M)$ can take the minimal and maximal). In general the bound may not be attained.

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

_proof_ Consider $(X_{t-1},X_t)$ which is a Markov chain whose state space is $\vec{\mathcal E}$. One can verify $\rho(v,x)=w_{vx}/w$ is the stationary distribution (Notice this chain is not reversible! Verify balanced equation).

**Corollary 3.8 The edge-commute inequality** For an edge $(v,x)$, $E_v T_x+E_xT_v\le w/w_{vx},2|\mathcal E|$ for weighted and unweighted graph.

_proof_ It suffices to show $E_v T_x+E_x T_v\le E_v U$. Let $T_x^v,T_v^x,T_U^v$ denote these times. Suppose the chain starts from $v$. From $T_x^v$ on, $T_v^x$ denote the first time when the chain hits $x$ and $T_U^v-T_x^v$ denote the first time when the chain hits $v$ through path $(x,v)$. The chain hits $v$ either through $(x,v)$ or from some other paths, so $T_v^x\le T_U^v-T_x^v$. Take expectations.

**Lemma 3.9** If $|\mathcal V|=n$, $\sum_{e=(v,x)\in \mathcal E} w_e(E_v T_x+E_x T_v)=w(n-1)$.

_proof_ 
$$
LHS=\frac{1}{2}\sum_v\sum_xw_{vx}(E_vT_x+E_xT_v)=\sum_v\sum_x w_{vx}E_xT_v=\sum_v\sum_x w\pi_vp_{vx}E_xT_v=\sum_v w\pi_v(E_vT_v^+-1)=w(n-1)
$$

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

_proof_ (a) The unique solution to the Dirichlet problem is $g(v)=E_v g(X_{T_A\cup\{v_0\}})=P_v(T_{v_0}<T_A)$.

(b) To prove $f_{vx}/r=(g(v)-g(x))w_{vx}$, we just compute via mean hitting times. First, since the chain stops at $A$, one can collapse $A$ into a singleton $a$. For ease of notation let $N_t(x)$ be the number of visits to $a$ before time $t$,
$$
\begin{aligned}
f_{vx}&=E_{v_0}N_{T_a}(v)p_{vx}-E_{v_0}N_{T_a}(x)p_{xv}\\&=_\text{Lemma 2.9}\pi_v(E_{v_0}T_a+E_a T_v-E_{v_0}T_v)p_{vx}-\pi_x(E_{v_0}T_a+E_a T_x-E_{v_0}T_x)p_{xv}\\&=\frac{w_{vx}}{w}[E_a T_v-E_aT_x+E_{v_0}T_x-E_{v_0}T_v]
\end{aligned}
$$
Meanwhile,
$$
\begin{aligned}g(v)&=P_v(T_{v_0}<T_a)=\frac{E_vT_a+E_aT_{v_0}-E_vT_{v_0}}{E_{v_0}T_a+E_a T_{v_0}}\\\Rightarrow r(g(v)-g(x))w_{vx}&=r\frac{E_vT_a-E_xT_a-E_vT_{v_0}+E_xT_{v_0}}{E_{v_0}T_a+E_aT_{v_0}}w_{vx}
\end{aligned}
$$
By cyclic tour property,
$$
E_aT_v+E_vT_{v_0}+E_{v_0}T_x+E_xT_a=E_aT_x+E_xT_{v_0}+E_{v_0}T_v+E_vT_a
$$
which gives
$$
\begin{aligned}
r(g(v)-g(x))w_{vx}&=r\frac{wf_{vx}/w_{vx}}w_{vx}{E_{v_0}T_a+E_aT_{v_0}}\\&=\frac{wf_{vx}/w_{vx}}{w_{v_0}P_{v_0}(T_a<T_{v_0}^+)}\pi_{v_0}P_{v_0}P(T_a<T_{v_0}^+)w_{vx}\\&=f_{vx}
\end{aligned}
$$
For $I_{(v)}=0\forall v\notin A\cup\{v_0\}$, notice this follows from the definition of $\mathbf f$.

_Remark_ Notice $I_{(v_0)}=1/r=g(v_0)/r$. So here $r$ is the _effective resistance between $v_0$ and $A$_, i.e., we regard the whole network as effectively a single conductor from $v_0$ o $A$, whose resistance is $r$.

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

Let $s_{ij}=\pi_i^{1/2}p_{ij}\pi_j^{-1/2}$,i.e., $\mathbf S=\text{diag}(\sqrt{\pi_i})\mathbf P\text{diag}(\sqrt{\pi_i})^{-1}$, then $\mathbf S$ is symmetric. Spectrum decomposition gives $\mathbf S=\mathbf U\mathbf \Lambda\mathbf U^T$ where $\mathbf U\in O(n)$ and $\mathbf \Lambda=\text{diag}(\lambda_n)$ with $1=\lambda_1>\lambda_2\ge...\ge \lambda_n\ge -1$ (Perron Frobenius theorem), moreover $\mathbf P=(\text{diag}(\sqrt{\pi_i})^{-1}U)\mathbf \Lambda(\text{diag}(\sqrt{\pi_i})^{-1}U)^{-1}$. $\lambda=1$ corresponds the eigenvector $