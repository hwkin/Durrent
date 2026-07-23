This is note on _Reversible Markov Chains and Random Walks on Graphs_ 

## Chapter 2 General Markov chains

### 2.1 Notation and reminders of fundamental results

_Setting_ The Markov chain is discrete-time and has finite state space.

_Notations_ $I=\{i,j,k\}$ state space. $\mathbf P=(p_{ij})$ transition matrix for discrete Markov chain. $p_{ij}^{(t)}=P(X_t=j\mid X_0=i),t\in Z_{>0}$ t-step transition probability, where $\mathbf P^{(t)}=\mathbf P^t$. 

$P_i$ and $E_i$ indicate that $X(0)=i$, similarly $P_\rho$ and $E_\rho$ indicate that $X(0)\sim\rho$. 

$T_i=\min\{t\ge 0: X_t=i \}$ the first hitting time. $T_i^+=\min\{t>0: X_t=i\}$ satisfies that when $X(0)\ne i$, $T_i^+=T_i$, and otherwise $T_i^+$ is the first return time. $T_A=\min\{t\ge 0: X_t\in A\}$.

#### 2.1.1 Stationary distribution and asymptotics

Assume the chain is irreducible.

**Theorem 2.0** There exists a unique stationary distribution $\pi$, i.e., a distribution satisfying the _balanced equations_ $\pi_j=\sum_i \pi_i p_{ij}\forall j$.

_Remark_ If $X_0\sim\pi$. then $X_t\sim\pi\forall t$. Such chain is called the _stationary chain_.

**Theorem 2.1 The ergodic theorem** Let $N_i(t)$ be the number of visits to state $i$ by time $t$ (_Remark: t is excluded_), then for any initial distribution, $t^{-1}N_i(t)\to \pi_i$ a.s..

_Remark_ This illustrates that space average=spatial average.

**Theorem 2.2 The convergence theorem** For any initial distribution, if the chain is aperiodic, we have $P(X_t=j)\to_{t\to\infty}\pi_j\forall j$.

#### 2.1.2 continuous-time chains

_Notations_ $q_{ij},j\ne i$ transition times. Define $q_i=\sum_j q_{ij}$ and let $q_{ii}=-q_i$. $Q=(q_{ij})$. $P_i(X_t=j):=Q_{ij}^{(t)}$, where $\mathbf Q^{(t)}=\exp(\mathbf Q t)$. $T_i^+=\min\{t\ge T_{I\backslash i}: X_t=i\}$.

**Modification of Theorem 2.0**  The _balanced equations_ are $\sum_i \pi_i q_{ij}=0\forall j$.

**Modification of Theorem 2.1** $N_i(T):=\int_0^t 1_{X_s=i}ds$.

**Modification of Theorem 2.2** No assumption on aperiodicity is needed.

**Forward equations** $\frac{d}{dt} P(X_t=j)=\sum_i P(X_t=i)q_{ij}$. In matrix form, $\frac{d}{dt} \mathbf Q^{(t)}=\mathbf Q\mathbf Q^{(t)}$.

**Continuation** for a discrete Markov chain, replace the fixed holding time $1$ by $Exp(1)$. under this, many quantities are unchanged, including $\pi$ and $E_i T_A$.

### 2.2 Identities for mean hitting times and occupation times

#### 2.2.1 Occupation measures and stopping times

**Proposition 2.3** Let $S$ be a stopping time with $X_S=i$ (notice $S$ is not necessarily the first returning time) $E_i\# \text{visits to j before } S=\pi_j E_iS$.

_proof 1_ Since the chain is Markov, we can consider the chain as a renewal process with interarrival time $S$. Suppose the process is rewarded $1$ when it visits $j$, then by reward-renewal theorem, the long-run reward rate equals the expected reward rate in a cycle. This yields
$$
\pi_j=\lim_{t \to \infty} \frac{N_j(t)}{t}=\frac{E_i\# \text{visits to j before } S}{ES}
$$
_proof 2_ We can prove a generalized equation.

**Proposition 2.4** Let $\theta$ be a distribution on $I$ with $X_0\sim\theta$, and let $S$ be a stopping time s.t. $X_S=_d X_0$ (Notice $S$ isn't necessarily the first time) , then $E_\theta\#\text{visits to j before }S=\pi_j E_\theta S$.

_proof_ Let $\rho_j=E_\theta\# \text{visits to j before } S$, then we have $\sum_j \rho_j p_{jk}=\rho_k\forall k$:
$$
\begin{aligned}
\rho_k&=\sum_{t=0}^\infty P_\theta (X_t=k,S>t)
\\&=\sum_{t=0}^\infty P_\theta (X_{t+1}=k,S>t)\text{ because } P_\theta(X_S=k)=P_\theta (X_0=k)
\\&=\sum_{t=0}^\infty\sum_j P_\theta (X_t=j,S>t,X_{t+1}=k)
\\&=\sum_{t=0}^\infty\sum_j P_\theta (X_t=j,S>t)p_{jk}
\\&=\sum_j \rho_j p_{jk}
\end{aligned}
$$
Then by the uniqueness of stationary distribution and $\sum_j \rho_j=E_\theta S$, we attain the conclusion.

#### 2.2.2 Mean hitting time and related formulas

By applying **Proposition 2.3** with particular choice of $j$ and $S$, we have 

**Lemma 2.5** $E_iT_i^+=1/\pi_i$

**Lemma 2.6** $E_i\#\text{visits to j before }T_i^+=\pi_j/\pi_i$

**Lemma 2.7** $E_j\#\text{visits to j before }T_i=\pi_j (E_j T_i+E_i T_j)$, $j\ne i$.

**Corollary 2.8** $P_i(T_j<T_i^+)=[\pi_i (E_i T_j+E_jT_i)]^{-1}$, $j\ne i$.

**Lemma 2.9** $E_i\#\text{visits to j before }T_l=\pi_j (E_i T_l+E_lT_j-E_iT_j)$, $i\ne l$.

**Corollary 2.10** $P_i (T_j<T_l)=(E_i T_l+E_l T_j-E_i T_j)/(E_j T_l+E_l T_j)$.

**Lemma 2.11 Mean hitting time formula** $\pi_i E_\pi T_i=Z_{ii}$

**Lemma 2.12 Mean hitting time formula** $\pi_j E_i T_j=Z_{jj}-Z_{ij}$.

**Corollary 2.13** $\sum_j \pi_j E_i T_j=\sum_j Z_{jj}$, $\forall i$.

**Corollary 2.14 The random target lemma** $\sum_j \pi_j E_i T_j$ doesn't depend on $i$.

**Lemma 2.15** $E_\pi \#\text{visits to j before }T_i=\frac{\pi_j}{\pi_i}Z_{ii}-Z_{ij}$.

> $Z_{ij}=\sum_{t=0}^\infty p_{ij}^{(t)}-\pi_j$. When the chain is periodic, we use Cesaro limit to avoid divergence. Notice $\sum_j Z_{ij}=0\forall i$. $\mathbf Z=(Z_{ij})$ is called _fundamental matrix_.

_proof_ 

For **Lemma 2.5 and 2.6**, pick $S=T_i^+$.

For **Lemma 2.7**, Let $S$ be the first return to $i$ after first visit to $j$. Then $E_j\#\text{visits to j before }T_i=E_i\#\text{visits to j before }S$ by definition. and $ES=E_i T_j+E_j T_i$. 

For **Corollary 2.8**, starting from $i$, number of visits to $i$ without hitting $j$ has a geometric distribution with successful probability $P(T_j<T_i^+)$. So $P(T_j<T_i^+)^{-1}=E_i\#\text{visits to i before }T_j=\pi_i (E_iT_j+E_jT_i)$.

For **Lemma 2.9**, let $S$ be the first return to $i$ after the first visit to $j$ after the first visit to state $l$, we have $E_i \#\text{visits to j before }S=E_i\#\text{visits to j before }T_l+E_j\#\text{visits to j before }T_i$. Meanwhile, $ES=E_i T_l+E_l T_j+E_j T_i$.

For **Corollary 2.10**, notice $E_i\#\text{visits to j before }T_l=P_i(T_j<T_l)E_j\#\text{visits to j before } T_l$.

For **Lemma 2.11**, to make $\pi$ occur, let $S$ be the first return to $i$ after $t_0$, we have $E_i\#\text{visits to i before }S=\sum_{t=0}^{t_0-1}p_{ii}^{(t)}$ and $ES=t_0+E_{\rho}T_i$ where $X_{t_0}\sim\rho$ with $X_0=i$ . This gives 
$$
\sum_{t=0}^{t_0-1}p_{ii}^{(t)}=\pi_i(t_0+E_\rho T_i)\Rightarrow \sum_{t=0}^{t_0-1}(p_{ii}^{(t)}-\pi_i)=\pi_iE_\rho T_i
$$
push $t_0\to\infty$ and we will get $Z_{ii}=\pi_i E_\pi T_i$. 

For **Lemma 2.12**, we also exploit $\pi$. Let $S$ be the first return to $i$ after moving for $t_0$ after hitting $k$ first, we have $E_i\#\text{visits to i before }S=E_i\#\text{visits to i before }T_k+\sum_{t=0}^{t_0-1}p_{ki}^{(t)}$ and $ES=ET_k+t_0+E_\rho T_i$, where $X_{t_0}\sim\rho$ with $X_0=k$. This gves
$$
\begin{aligned}
&E_i\#\text{visits to i before }T_k+\sum_{t=0}^{t_0-1}p_{ki}^{(t)}=\pi_i(E_iT_k+t_0+E_\rho T_i)\\
\Rightarrow& \pi_i(E_i T_k+E_k T_i)+\sum_{t=0}^{t_0-1}p_{ki}^{(t)}=\pi_i(E_i T_k+t_0+E_\rho T_i)\\
\Rightarrow &\sum_{t=0}^{t_0-1}(p_{ki}^{(t)}-\pi_i)=\pi_i(E_\rho T_i-E_i T_k)
\end{aligned}
$$
push $t_0\to\infty$ and we have $Z_{ki}=\pi_i(E_\pi T_i-E_i T_k)$. Then use **Lemma 2.11** we have $\pi_i E_i T_k=Z_{ii}-Z_{ki}$.

**Corollary 2.13 and 2.14** are trivial.

For **Lemma 2.15**, let $S$ be the first visit of $i$ after $t_0$, then $E_i\#\text{visits to j before }S=\sum_{t=0}^{t_0-1} p_{ij}^{(t)}+E_\rho \#\text{visits to j before }T_i$ and $ES=t_0+E_\rho T_i$ where $X(t_0)\sim\rho$ with $X(0)=i$. This gives 
$$
\sum_{t=0}^{t_0-1} p_{ij}^{(t)}+E_\rho \#\text{visits to j before }T_i=\pi_j(t_0+E_\rho T_i)\Rightarrow\sum_{t=0}^{t_0-1} (p_{ij}^{(t)}-\pi_j)+E_\rho \#\text{visits to j before }T_i=\pi_j E\rho T_i
$$
push $t_0\to\infty$.

_Remark_ A formal derivation of mean hitting time formula is (which doesn't make sense)
$$
\begin{aligned}
&\sum_{t=0}^\infty (1_{X_t=j}-\pi_j)=\sum_{t=0}^{T_j-1}(1_{X_t=j}-\pi_j)+\sum_{t=T_j-1}^\infty(1_{X_t=j}-\pi_j)\\
\Rightarrow&E\sum_{t=0}^\infty (1_{X_t=j}-\pi_j)=E\sum_{t=0}^{T_j-1}(1_{X_t=j}-\pi_j)+E\sum_{t=T_j-1}^\infty(1_{X_t=j}-\pi_j)\\
\Rightarrow& Z_{ij}=-\pi_j E_i T_j+Z_{jj}
\end{aligned}
$$

#### 2.2.3 Continuous-time versions

For cts-time cases, $Z_{ij}=\int_0^\infty (P_i(X_t=j)-\pi_j)dt$, and $\#\text{visits to j}$ should be replaced by the amount of time spent in $j$. This gives

**Modification of Proposition 2.3** Let $S$ be a stopping time with $X_S=i$ (notice $S$ is not necessarily the first returning time), $E_i\text{amount of time spent at j before } S=\pi_j E_iS$.

**Modification of Lemma 2.5** $E_i T_i^+=1/(q_i \pi_i)$.

_proof_ $E_i\text{amount of time spent at j before } T_i^+=1/q_i$.

**Modification of Lemma 2.6** $E_i\text{amount of time spent in j before }T_i^+=\pi_j/(q_i \pi_i)$.

**Modification of Lemma 2.7** $E_j\text{amount of time spent in j before }T_i=\pi_j (E_j T_i+E_i T_j)$, $j\ne i$.

_proof_ Let S be the first return to $i$ after hitting $j$, then $E_i\text{amount of time spent at j before } S=E_j\text{amount of time spent at j before } T_i$ and $ES=E_i T_j+E_j T_i$.

**Modification of Corollary 2.8** $P_i(T_j<T_i^+)=(q_i \pi_i (E_i T_j+E_j T_i))^{-1}$.

_proof_ 
$$
E_i\text{amount of time spent in j before }T_i^+=P_i(T_j<T_i^+)E_j\text{amount of time spent in j before }T_i
$$

### 2.3 Variances of sums

In discrete time, consider $N_i(t)=\#\text{visits to state i before time }t$. 

- The expectation is given by
  $$
  E_\pi N_i(t)=E_\pi\sum_{s=0}^{t-1}1_{X(s)=i}=t\pi_i
  $$

- The variation is given by
  $$
  \begin{aligned}
  var_\pi N_i(t)&=E_\pi \bigg(\sum_{s=0}^{t-1}1_{X(s)=i}-\pi(i)\bigg)^2\\&=\sum_{r=0}^{t-1}\sum_{s=0}^{t-1}(P_\pi(X_r=i,X_s=i)-\pi_i^2)\\&=2\sum_{0\le r< s\le t-1}(P_\pi(X_r=i,X_s=i)-\pi_i^2)+\sum_{0\le r\le t-1}(P_\pi (X_r=i)-\pi_i^2)\\
  &=2\pi_i\sum_{u=1}^{t-1} (t-u)(p_{ii}^{(u)}-\pi_i)\ +t(\pi_i-\pi_i^2),u=|s-r|\\&=\pi_i\bigg(\sum_{u=0}^{t-1}2(t-u)(p_{ii}^{(u)}-\pi_i)-t(1-\pi_i) \bigg)
  \end{aligned}
  $$
  By the technique from analysis we have 
  $$
  \frac{var_\pi N_i(t)}{t}\to \pi_i(2Z_{ii}-1+\pi_i)
  $$

- Generalize this, pick $f,g\in \mathbf R^I$ s.t. $E_\pi f(X_0)=E_\pi g(X_0)=0$, and define $S_t^f=\sum_{s=0}^{t-1} f(X_s)$,

  $$
  E_\pi S_t^fS_t^g=\sum_i\sum_j f(i)g(j)\sum_{r=0}^{t-  1}\sum_{s=0}^{t-1}(P_\pi(X_r=i,X_s=j)-\pi_i\pi_j)
  $$

By similar estimation, $\frac{E_\pi S_t^fS_t^g}{t}\to f\Gamma g$, where $\Gamma_{ij}=\pi_i Z_{ij}+\pi_jZ_{ji}+\pi_i\pi_j-\pi_i\delta_{ij}$ and $(f\Gamma g)_{ij}=f(i)\Gamma_{ij}g(j)$.

In continuous time, 

- The variance is 
  $$
  \begin{aligned}
  var_\pi N_i(t)&=\int_0^t\int_0^t P_\pi (X_r=i,X_s=i)-\pi_i^2drds\\&=\int_0^t\int_0^t \pi_i p_{ii}^{(|t-s|)}-\pi_i^2drds
  \end{aligned}
  $$
  So $\frac{var_\pi N_i(t)}{t}\to 2\pi_i Z_{ii}$.

- Similarly $\Gamma_{ij}=\pi_i Z_{ij}+\pi_jZ_{ji}$, which simplifies the result.

**Theorem 2.17** For centered $f$, $t^{-1/2}S_t^f\to_d \mathcal N(0,f\Gamma f)$.

### 2.4 Two metrics on distributions

#### 2.4.1 Variance distance 

**Definition** the variance distance $\|\theta_1-\theta_2\|_v=\max_{A\subset I}|\theta_1(A)-\theta_2(A)|$.

**Lemma 2.19** The identity holds:
$$
\frac{1}{2}\sum_i |\theta_1(i)-\theta_2(i)|=\sum_i(\theta_1(i)-\theta_2(i))^+=\sum_i(\theta_1(i)-\theta_2(i))^-=1-\sum_i\min(\theta_1(i),\theta_2(i)=\max_{A\subset I}|\theta_1(A)-\theta_2(A)|=\min_{V_1\sim \theta_1,V_2\sim \theta_2} P(V_1\ne V_2)
$$
**Application** For Markov chain, we may use $d_i(t)=\|\rho_{i,t}-\pi\|$, where $\rho_{i,t}$ is the distribution of $X_t$ given $X_0=i$ and $\pi$ is the limit distribution. let $d(t):=\max_i d_i(t)$ be the worst case difference. Let $\bar d(t)=\max_{ij}\|\rho_{i,t}-\rho_{j,t}\|$. 

**Lemma 2.20** 

(a) **Submultiplicativity property** $\bar d(s+t)\le \bar d(s)\bar d(t)$

(b) $d(s+t)\le 2d(s)d(t)$

(c) $d(t)\le \bar d(t)\le 2d(t)$

(d) $d(t),\bar d(t)$ is decreasing functions.

**Corollary 2.21** Suppose there exists a probability measure $\mu$, $\delta\in \mathbf R_+$ and $t>0$ s.t. $p_{ij}^{(t)}\ge\delta \mu_j\forall i,j$. Then $d(s)\le (1-\delta)^{[s/t]},s\ge 0$.

_proof_ The hypothesis implies $\bar d(t)\le 1-\delta$. Use **Lemma 2.20** (a) and (c).

**Proposition** $\mu\to\|\theta-\mu\|_v$ is a convex functional for distribution $\mu$ where $\theta$ is fixed. As a corollary, for any distribution $\mu$ on $I$, we have $\|\mu-\pi\|_v\le d(0)$.

#### 2.4.2 $L^2$ distance

**Definition** Pick a fixed distribution $\pi$, which may often be the stationary distribution. For $f\in \mathbf R^I$, its $L^2$ norm is $\|f\|_2:=\sqrt{\sum_i \pi_i f^2(i)}=\sqrt{E_\pi f(X)^2}$, where $X\sim\pi$. For a signed measure $\nu$, its $L^2$ norm is $\|\nu\|_2:=\sqrt{\sum_i \nu_i^2/\pi_i}$, which is exactly the $L^2$ norm of $\nu/\pi$. For distribution $\theta,\mu$, the $L^2$ distance is just $\|\theta-\mu\|_2$. In particular, $\|\theta-\pi\|_2=\sqrt{\sum_i \theta_i^2/\pi_i-1}$.

_Remark_ If $X_t\sim \theta_t$ and the stationary distribution is exactly $\pi$, $\|\theta_t-\pi_t\|_2$ is also a decreasing function.

**Definition** Under the same setting, for $f\in \mathbf R^I$, its $L^1$ norm is $\|f\|_1=\sum_i \pi_i |f(i)|$ and $\|\nu\|_1=\sum_i |\nu_i|$. By Cauchy-Schwarz formular, $\|\cdot\|_1\le\|\cdot\|_2$. 

_Remark_ $\|\theta_1-\theta_2\|_1=2\|\theta_1-\theta_2\|_v$.

#### 2.4.3 Exponential tails of hitting times

<font color="red">_Principle_</font> Because the state space is finite, many quantities converging to 0 as $t\to\infty$ must converge exponentially fast by iterating over worst-case initial states. 

_Example_ The submultiplicative property of $\bar d(t)$.

_Example_ The first hitting time of $A\subset S$, $T_A$. Let $t_A^*=\max_i E_i T_A$. We have 
$$
P_\mu(T_A>ms\mid T_A>(m-1)s)=P_\theta (T_A>s)\le\max_i P_i (T_A>s)\le_\text{Markov inequality} t_A^*/s
$$
where $\mu$ is initial distribution, $\theta$ is the distribution of $X_{(m-1)s}$. By induction, this yields $P_\mu(T_A>ms)\le (t_A^*/s)^m$,or $P_\mu(T_A>t)\le(t_A^*/s)^{[t/s]}$, i.e., exponentially decreasing. 

For cts-time case, a good choice of $s$ is $s=et_A^*$, which gives $\sup_\mu P_\mu(T_A>t)\le\exp(-[\frac{t}{et_A^*}])$.

### 2.5 Distributional identities

#### 2.5.1 Stationary consequences

**Lemma 2.23** For $t\in \mathbf N$, $P_\pi(T_A=t-1)=P_\pi(T_A^+=t)=\pi(A)P_{\pi_A}(T_A^+\ge t)$ where $\pi_A(i)=\pi_i/\pi(A),i\in A$.

_Remark_ This links the return time of $A$ to the hitting time of $A$ when the chain is stationary.

_proof_ For the first identity, since the chain is stationary, $(X_0,...,X_{t-1})=_d (X_1,...,X_t)$, so
$$
P_\pi(T_A=t-1)=P_\pi(X_0\notin A,...,X_{t-2}\notin A,X_{t-1}\in A)=P_\pi(X_1\notin A,...,X_{t-1}\notin A,X_t\in A)=P_\pi(T_A^+=t)
$$
For the second identity, similarly
$$
\begin{aligned}
P_\pi(T_A^+=t)&=P(X_1\notin A,...,X_{t-1}\notin A,X_t\in A)\\&=P(X_1,...,X_{t-1}\notin A)-P(X_1,...,X_t\notin A)\\&=P(X_1,...,X_{t-1}\notin A)-P(X_0,...,X_{t-1}\notin A)\\&=P(X_0\in A,X_1,...,X_{t-1}\notin A)\\&=\pi(A)P_{\pi_A}(T_A^+\ge t)
\end{aligned}
$$
Sum up w.r.t. $t$., we have

**Corollary Kac's formular** $\pi(A)E_{\pi_A}T_A^+=1$.

_Remark_ A special case is just **Lemma 2.5**: $E_i T_i^+=1/\pi_i$.

Multiple $t$ on both side and sum up w.r.t. $t$, we have $1+E_\pi T_A=\pi(A)\frac{1}{2}(E_{\pi_A}T_A^++E_{\pi_A}(T_A^+)^2)$. This gives $var_{\pi_A}(T_A^+)=\frac{2E_\pi T_A+1}{\pi(A)}-\frac{1}{\pi^2(A)}$.

**Analogue in cts-time of Lemma 2.23** $P_\pi(T_A\in(t,t+dt))=Q(A,A^c)P_{\rho_A}(T_A>t)dt,t>0$, where $Q(A,A^c)=\sum_{i\in A}\sum_{j\in A^c}q_{ij}$ and $\rho_A(j)=\sum_{i\in A}q_{ij}/Q(A,A^c)$.

**Analogue in cts-time of Kac's formular** $Q(A,A^c)E_{\rho_A}T_A=\pi(A^c)$.

#### 2.5.2 A generating function identity

**Lemma 2.25** Define $G_{ij}(z)=\sum_{t\ge 0}P_i(X_t=j)z^t$ and $F_{ij}(z)=\sum_{t\ge 0}P_i(T_j=t)z^t$. Then $F_{ij}=G_{ij}/G_{jj}$.

_Remark_ This links the distribution of #visits to $j$ to that of $T_j$. Analogue in cts-time is Laplace transform.

_Analysis proof_ Conditioning on $T_j$,
$$
\begin{aligned}
p_{ij}^{(t)}&=\sum_{l=0}^t P_i(T_j=l)p_{jj}^{(t-l)}\\ \Rightarrow G_{ij}(z)=\sum_{t\ge 0}p_{ij}^{(t)}z^t&=\sum_{t\ge 0}\sum_{l=0}^t P_i(T_j=l)p_{jj}^{(t-l)}z^t=\sum_{l\ge 0}\sum_{t\ge l}P_i(T_j=l)z^l p_{jj}^{(t-l)}z^{t-l}=F_{ij}(z)G_{jj}(t)
\end{aligned}
$$
_Probability proof_ Let $\zeta\sim Geom(1-z)$ independent of the chain. Then 
$$
G_{ij}(z)=\sum_{t\ge 0}P_i(X_t=j)P(\zeta>t)=E_i\#\text{visits to j before }\zeta=P_i(T_j<\zeta)E_j\#\text{visits to j before }\zeta=F_{ij}(z)G_{jj}(z)
$$
Notice $E_iT_j=\frac{d}{dz} F_{ij}(z)\mid_{z=1}$. This gives another derivation of mean hitting time.

_proof_ Notice $G_{ij}(z)=Z_{ij}(z)+\frac{\pi_j}{1-z}$, where $Z_{ij}(z)=\sum_{t\ge 0}(p_{ij}^{(t)}-\pi_j)z^t$. This gives 
$$
F_{ij}(z)=\frac{Z_{ij}(z)+\frac{\pi_j}{1-z}}{Z_{jj}(z)+\frac{\pi_j}{1-z}}=1+(1-z)\frac{Z_{ij}-Z_{jj}}{(1-z)Z_{jj}(z)+\pi_j}
$$
Then differentiate both side and let $z=1$.

#### 2.5.3 Distribution and continuization

As we have mentioned, the continuization $\hat X_t$ of discrete-time Markov chain $X$ is to replace the fixed holding times to independent $Exp(1)$ holding times. In this way, if $N_t\sim P_1(t)$, $\hat X_t=_d X_{N(t)}$, and $\hat T_A=S_{T_A}$. This gives:

- $P_i(\hat X_t=j)=\sum_{s=0}^\infty \frac{t^s}{s!}e^{-t}P_i(X_s=j)$.

- $E[\hat T_A\mid T_A]=T_A$ and $var[\hat T_A\mid T_A]=T_A$, since $Exp(1)$ has mean and variance $1$.

  From _conditional variance formula_ $var Z=Evar(Z\mid Y)+varE(Z\mid Y)$ we have $var\hat T_A=ET_A+var T_A$.

### 2.6 Matthews' method for cover times

Consider the _cover time_ $C=\max_jT_j$, i.e., the time required to visit every state. 

**Theorem 2.26 Matthews** For $|I|=n$,

(i) $\max_v E_v C\le h_{n-1} \max_{i,j}E_i T_j$  (ii) $\min_v E_v X\ge h_{n-1}\min_{i\ne j}E_i T_j$,

where $h_{n-1}=\sum_{m=1}^{n-1}m^{-1}$.

_proof_ Let $J_1,...,J_n$ be a uniform random ordering of states independent of the chain. Let $C_m=\max_{i\le m}T_{J_i}$ be the time required to visit $J_1,...,J_m$ and $L_m$ is the state amongst $J_1,...,J_m$ hit last. Consider whether $J_m$ is visited before $J_{m-1}$, we have an identity
$$
E_v[C_m-C_{m-1}\mid J_1,...,J_m;X_t,t\le C_{m-1}]=E_{L_{m-1}}T_{J_m}\ 1_{L_m=J_m}
$$
For lower bound, take expectation, by symmetry of $J_m$, we have
$$
E_vC_m-C_{m-1}\ge\min_{i\ne j} E_i T_j\ E 1_{L_m=J_m}=\min_{i\ne j} E_i T_j\  m^{-1}
$$
and 
$$
E_v C_1\ge 0P(J_1=v)+\min_{i\ne j}E_i T_j\ P(J_1\ne v)=\min_{i\ne j}E_i T_j(1-1/n)
$$
sum them up and we attain the lower bound. Upper bound can be attained in the same way.

### 2.7 New chain from the old

For a chain $X_t$ on $I$, the goal is to construct a chain on $A\subset I$.

#### 2.7.1 The chain watched only on $A$

This is the chain $Y_t$ defined by $S_0=T_A$, $S_n=\min\{t>S_{n-1}: X_t\in A \}$, and $Y_n=X_{S_n}$. The chain has state space $A$ and transition matrix $\bar P_A(i,j)=P_i(X_{T_A}=j)$. By ergodic theorem the stationary distribution is $\pi_A:=\pi_i/\sum_j \pi_j$ where $i\in A$.

#### 2.7.2 The chain restricted to $A$

This is the chain $Y_n$ with transition matrix $\hat P_A(i,j)=P(i,j),i,j\in A,i\ne j$ and $\hat P_A(i,i)=1-\sum_{j\in A, j\ne i}P(i,j),i\in A$. In general the chain has little connection with $X_t$ and the stationary distribution isn't $\pi_A$. But when the chain is reversible the stationary distribution is exactly $\pi_A$.

#### 2.7.3 The collapsed chain

Pick $A\subset I$ and collapse $A^c$ into a new state $a$, i.e., the state space for new chain is $A\cup \{a\}$. The transition matrix is given by 
$$
\begin{align*}
p_{ij}^{*} &= p_{ij},\; i,j \in A \\
p_{ia}^{*} &= \sum_{k\in A^{c}} p_{ik},\; i \in A \\
p_{ai}^{*} &= \frac{1}{\pi(A^{c})}\sum_{k\in A^{c}} \pi_{k}p_{ki},\; i \in A \\
p_{aa}^{*} &= \frac{1}{\pi(A^{c})}\sum_{k\in A^{c}}\sum_{l\in A^{c}} \pi_{k}p_{kl}.
\end{align*}
$$
which has stationary distribution $\pi^*$ given by $\pi_i^*=\pi_i,i\in A;\pi_a^*=\pi(A^c)$. 

_Collapsing principle_ $X_{t\wedge T_{A^c}}=_d Y_{t\wedge T_a}$. So to prove a result which involves the behavior of the chain only up to time $T_{A^c}$, we may assume $A^c$ is a singleton. 

_Remark_ But as $X_t$ hits $A^c$, the behavior will be different from $Y_t$. Actually, if one collapse $A^c$ into a state, $X_t$ may not be Markov.

_Remark_ The constructions give different processes. The chain watched only on $A$ "rebounds at a random place dependent on the hitting place", the chain restricted to $A$ "rebounds off the boundary of $A^c$ where the boundary is hit" and the collapsed chain "exits $A^c$ at a random place independent of the hitting place".

### 2.8 Miscellaneous methods

#### 2.8.1 Martingale methods

The goal is to find martingales and apply optional stopping theorem.

**Lemma 2.27** Let $P:\mathbf R^I\to \mathbf R^I$ be an operator with $(Pu)(i)=\sum_j p_{ij}u(j)$. Then for $A\subset I$ nonempty and $f\in \mathbf R^A$, the solution to Dirichlet problem $\begin{cases}(P-I)u=0,&\text{on} A^c\\u=f,&\text{on} A\end{cases}$ exists and is unique. The function satisfying $Pu=u$ is called **harmonic**.

_proof_ If $u$ is a solution, then notice $M_t=f(X_{T_A\wedge t})$ is a martingale. This yields $f(i)=E_iM_0=E_i M_{T_A}=E_i f(X_{T_A})$. This gives both existence and uniqueness.

**Corollary 2.28** If $h$ is harmonic on $I$, then $h$ is constant.

_proof_ Pick $x\in I$ and fix $h(x)=c$. Notice $h\equiv c$ is a solution to the Dirichlet problem with BC $h(x)=c$, and it's unique. 

**Lemma 2.29 The random target lemma** $\sum_j E_i T_j \pi_j$ doesn't depend on $i$. 

_Remark_ We have computed that the sum equals $\sum_j Z_{jj}$ which is independent of $i$.

_proof_ Let $g_j(i)=E_i T_j$. By conditioning on the first step we have 
$$
g_j(i)=1_{i\ne j}+1_{i\ne j}\sum_k p_{ik}g_j(k)
$$
Let $h(i)=\sum_j \pi_j g_j(i)$, we have 
$$
\begin{aligned}
h(i)&=\sum_j \pi_j(1_{i\ne j}+1_{i\ne j}\sum_k p_{ik}g_j(k))\\&=1-\pi_i+\sum_{j,k}\pi_jp_{ik}g_j(k)1_{i\ne j}=1-\pi_i+\sum_k p_{ik}(h(k)-\pi_i g_i(k))\\&=\sum_k p_{ik} h(k)+1-\pi_i-\pi_i\sum_k p_{ik} g_i(k)=\sum_k p_{ik}h(k)+1-\pi_i-\pi_i(E_iT_i^+-1)\\&=\sum_k p_{ik}h(k)
\end{aligned}
$$
So $h(i)$ is harmonic on $I$, so it doesn't depend on $i$.

**Lemma 2.30** For any stopping time $S$ and any state $i,j,k$, let $N(j;t)$ denote the number of visits to $j$ before $t$ and $N(j,k;t)$ denote the number of transition from $j$ to $k$ before $t$, then $E_iN(j,k;S)=p_{jk}E_iN(j;S)$.

_Remark_ One can prove this by direct computation.

_proof_ Notice $N(j,k;t)-p_{jk}N(j;t)$ is a martingale. By optional stopping theorem the identity holds.

**Lemma 2.31** Consider hitting time equation $\begin{cases}u=1+Pu&\text{on }A^c\\u=0&\text{on }A\end{cases}$ whose solution is $E_iT_A$. If $h$ is a super-solution, i.e., $\begin{cases}h\ge1+Ph&\text{on }A^c\\h\ge0&\text{on }A\end{cases}$, then $E_iT_A\le h(i)$.

_proof_ Let $M_{t}=t+h(X_t)$, the hypothesis implies $M_t$ is a supermartingale. By optional stopping theorem, $h(i)=E_i M_0\ge E_i M_{T_A}\ge ET_A$. 

#### 2.8.2 A comparison argument

The goal is to obtain inequalities for a "hard" chain by compare that with an "easy" chain.

**Lemma 2.32** Let $X_t$ be a discrete-time chain with $I=\{0,...,n\}$ such that $p_{ij}=0,j>i$. Write $m(i)=i-E_iX_1$ and suppose $0<m(1)\le m(2)...\le m(n)$. Then $E_nT_0\le\sum_{j=1}^{n} m(j)^{-1}$.

_proof_ Write $h(i)=\sum_{j=1}^{i} m(j)^{-1}$, and extend $h$ to $[0,n]$ by linear interpolation. Then $h$ is concave. So we have 
$$
Ph(i)=E_ih(X_1)\le h(E_iX_1)=h(i-m(i))\le h(i)-h'(i)m(i)=h(i)-1
$$
By **Lemma 2.31**, $h(i)\le E_i T_0$. 

_Idea_ The proof looks confusing. Actually we are comparing this with a cts-time chain. 

Let $Y_t$ be a cts-time pure-death chain with rates $q_{i,i-1}=m(i)$. Then $E_i T_0=\sum_{j=1}^{i} m(j)^{-1}$. 

For a cts-time chain $Z_t$, define $\mathcal L(f)(i)=\lim_{t\downarrow 0}\frac{E_i f(Z_t)-f(i)}{t}=\sum_j q_{ij}f(j)$ to be the **generator** operator, which is the instantaneous expected rate of change of $f$ defined on $Z_t$. In this case, $\mathcal L h(i)=-1$. 

For $X_t$, the decreasing rate of $h$ in one step is $E_i h(i)-h(X_1)\ge 1$. So the mean time $E_nT_0^X\le E_n T_0^Y$. 

#### 2.8.3 Wald equations

**Lemma 2.33** 

(a) Let $0=Y_0\le Y_1\le...$ be such that $E[Y_{i+1}-Y_i\mid Y_j,j\le i]\le c,i\ge 0$ for constant $c$. Then for any stopping time $T$, $EY_T\le cET$.

(b) **Wald's equation for martingales** $\le c$ can be replaced by $=c$.

(c) **Wald's equation** Especially $Y_n=\sum_{i=1}^{n} \xi_i$ for i.i.d. nonnegative $\xi_i$ then $EY_T=E\xi_i ET$.

_proof_ (a) Notice $Y_i-ci$ is a supermartingale. So $E[Y_T-cT]\le EY_0=0$ by optional stopping theorem. (b) Now $Y_i=ci$ is a martingale. (c) Corollary from (b).



