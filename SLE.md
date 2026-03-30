### Class 1 Stochastic Analysis

***Definition*** $\{H_t\}_{t\geq 0}$ is a stochastic process, we say $\{H_t\}$ is **adapted** if $H_t\in\mathcal F_t$, is **continuous** if the map $t\rightarrow H_t$ is continuous a.s., is **bounded** if $\exists \ N<\infty, |H_t|<N\ \forall\ t$, is a **local martingale** if there exists a sequence of stopping time $\tau_j\uparrow\infty$ s.t.$H_{t\wedge\tau_j}$ is a martingale $\forall j$. We denote adapted cts process by $\mathcal I$ and continuous martingale by $\mathcal M$.

Now we begin our step to define a stochastic integration.

1. Integration of simple process w.r.t. BM (Brownian Motion)

   ***Definition*** a **Brownian Motion** $(B_t)_{t\geq 0}$ is a stationary independent process satisfies $B_t\sim \mathcal N(0,t)$.

   ***Definition*** $H$ is called a simple process if $H_t=\sum_{j=1}^n c_j1_{[t_{j-1},t_j)}$ where $0\leq t_0<...<t_n$, and $c_j$ is a bounded random variable $\in\mathcal F_{t_{j-1}}$.  

   <font color='red'> **Define**</font> when $n=1$ the integral 
   $$
   Z_t=\int_0^t H_s dB_s=\left\{\begin{align}&0,&t<t_0\\&c_1(B_t-B_{t_0}),&t_0\leq t<t_1\\&c_1(B_{t_1}-B_{t_0}),&t>t_1\end{align}\right.
   $$
   when $n>1$ the integral is the linear combination of cases for $n=1$. This is well-defined.

   Notice the Brownian motion is adapted to the filtration, and the simple process is predictable (since it is slightly in advance)

   **Property** (i) linear in the integrand: $\int_0^t (H_s+K_s)dB_s=\int H_sdB_s +\int_0^t K_sdB_s$

   (ii) quadratic variation property

   ***Definition*** **quadratic variation** $\langle Z\rangle_t=\int_0^t H_s^2 ds$.

   **Theorem Itô's Isometry for simple process** $E[\langle Z\rangle_t]=EZ_t^2$.

   <font color='red'>_proof_</font> 
   $$
   \begin{aligned}
   &Z_t=\int_0^t H_sdB_s=\sum_{j=1}^nc_j\Delta W_j
   \\&EZ_t^2=E(\sum_{j=1}^nc_j\Delta W_j)^2=\sum _{j=1}^nE(c_j^2\Delta W_j^2)+2\sum_{i\neq j}E(c_i c_j\Delta W_i\Delta W_j)
   \end{aligned}
   $$
   For the crossing terms,
   $$
   E(c_ic_j\Delta W_i\Delta W_j)=EE(c_ic_j\Delta W_i\Delta W_j|\mathcal F_{t_j})=E[c_ic_j\Delta W_i\ E\Delta (W_j|\mathcal F_{t_j})]=0
   $$
   For the square terms,
   $$
   Ec_j^2\Delta W_j^2=Ec_j^2 \Delta t_j
   $$
   Sum up,
   $$
   E Z_t^2=\sum_{j=1}^n Ec_j^2\Delta t_j=\int_0^t E(H_s^2)ds
   $$
   **Theorem** If $H_s$ is square integrable (always true for simple process), $Z_t$ is a square integrable martingale and $Z_t^2-\langle Z\rangle_t\in \mathcal M$.

   <font color='red'>_proof_</font> 

   Let's evaluate this at two specific times on our grid: $s = t_m$ and $t = t_k$, where $m < k$ (so $s < t$). 
   Therefore $Z_s = \sum_{i=1}^{m} c_i \Delta W_i$ and $Z_t = \sum_{i=1}^{k} c_i \Delta W_i$

   Notice that we can split $Z_t$ into the past and the future: $Z_t = Z_s + \sum_{i=m}^{k-1} c_i \Delta W_i$

   (i) Prove $Z_t$ is a Square-Integrable Martingale. It's square-integrable by Ito's Isometry, now verify it's a martingale.
   $$
   E[Z_t \mid \mathcal{F}_s] = E [ Z_s + \sum_{i=m}^{k-1} c_i \Delta W_i | \ \mathcal{F}_s]=Z_s + \sum_{i=m}^{k-1} E [ c_i \Delta W_i \mid \mathcal{F}_s ]
   $$
   Now we look at the sum. For any index $i \ge m$, the time $t_i \ge s$. We use the Tower Property to condition on $\mathcal{F}_{t_i}$:
   $$
   E [ c_i \Delta W_i \mid \mathcal{F}_s ] = E \Big[ E [ c_i \Delta W_i \mid \mathcal{F}_{t_i} ] \ \Big| \ \mathcal{F}_s \Big]=E\Big[ c_i \cdot E[\Delta W_i|\mathcal F_{t_i}]\Big|\mathcal F_s\Big] =  0
   $$
   So $E[Z_t \mid \mathcal F_s] = Z_s $ 

   (ii) Prove $Z_t^2 - \langle Z \rangle_t$ is a Martingale

   We need to show that $ E[Z_t^2 - \langle Z \rangle_t \mid \mathcal{F}_s] = Z_s^2 - \langle Z \rangle_s $.
   By rearranging terms, this is mathematically equivalent to proving: $ E[Z_t^2 - Z_s^2 \mid \mathcal{F}_s] = E[\langle Z \rangle_t - \langle Z \rangle_s \mid \mathcal{F}_s] $

   LHS: Since $ Z_t^2 = \Big( Z_s + (Z_t - Z_s) \Big)^2 = Z_s^2 + 2Z_s(Z_t - Z_s) + (Z_t - Z_s)^2 $

   Now, subtract $Z_s^2$ from both sides, and take the conditional expectation given $\mathcal{F}_s$:
   $$ E[Z_t^2 - Z_s^2 \mid \mathcal{F}_s] = E \Big[ 2Z_s(Z_t - Z_s) + (Z_t - Z_s)^2 \mid \mathcal{F}_s \Big] $$

   Let's break this into two pieces:
   1.  The Middle Term: $2Z_s$ is $\mathcal{F}_s$-measurable, so pull it out: $2Z_s E[Z_t - Z_s \mid \mathcal{F}_s]$. Because $Z_t$ is a martingale  $E[Z_t \mid \mathcal{F}_s] = Z_s$, which means $E[Z_t - Z_s \mid \mathcal{F}_s] = 0$. The middle term completely vanishes.
   2.  The Last Term: As proved in Ito's isometry, it's RHS.

   ***Equiv. Definition of quadratic variation*** Let $(\Pi_n)_{n=1}^{K_n}$ be a partition on time such that $\|\Pi_n\|\rightarrow 0$. then $\lim\sum_{j=1}^{K_n}(Z_{t_j}-Z_{t_{j-1}})^2=\langle Z\rangle _t$ in $L^2$.

   <font color='red'>_proof_</font> suffice to consider the case for $H_t=1_{[0,t]}$.

   Let $Q_n=\sum_{j=1}^{K_n} [(B_{t_j}-B_{t_{j-1}})^2-(t_j-t_{j-1})]$, then $Q_n=\sum_{j=1}^{K_n} (t_j-t_{j-1})[(\frac{B_{t_j}-B_{t_{j-1}}}{\sqrt{t_j-t_{j-1}}})^2-1]$

   So $EQ_n^2=\sum_{j=1}^{K_n}(t_j-t_{j-1})^2E(\mathcal N(0,1)^2-1)^2\leq \|\Pi_n\|tE(\mathcal N(0,1)^2-1)^2\rightarrow 0$.

   If the sequence of partition$\|\Pi_n\|$ is chosen such that $\sum_n \|\Pi_n\|<\infty$, then we have $P(Q_n>\epsilon)\leq \epsilon^{-2}EQ_n^2$ and by Borel-Cantelli lemma, $Q_n<\epsilon$ a.s., i.e. $Q_n\rightarrow 0$ a.s.

   

2. Integration of bounded $\mathcal I$ w.r.t. BM

   Let $H_t$ be a bounded (uniformly w.r.t. time) cts. Boundedness is used for applying DCT.

   Step 1: On discretized timestamps

   Let $\mathcal D:=\{\frac{j}{2^n}, i,n\in \mathbb Z_{\geq 0}\}$ dyadic rational (dense in $\mathbb R$)

   For $t\in\mathcal D$ <font color='red'> **define**</font> $Z_t=\int_0^t H_sdB_s:=\lim_{n\rightarrow\infty}\sum_{j=1}^{K_n} H_{t_{j-1}}(B_{t_j}-B_{t_{j-1}})$, the limit is in prob. (Notice here we use left endpoint to correspond the "prevision" of $H_t$. If we use right endpoint, we get very different interval.)

   To prove the limit exists in probability,

   ***Definition*** $Osc(H,\delta):=\sup\{|H_s-H_r|:0\leq s,r\leq t,|s-r|<\delta\}$, then since $H$ is cts, $Osc(H,\delta)\rightarrow 0$ as $\delta\rightarrow 0$.

   Let $H^{(n)}$ be a simple process defined by $H_s^{(n)}=H_{t_{j-1}}, t_{j-1}\leq s<t_j$ and $Z_t^{(n)}=\int_0^t H_S^{(n)} dBs$.

   Notice $|H_s-H_s^{(n)}|\leq Osc(H,\|\Pi_n\|):=O_n\rightarrow 0$.

   _Claim_: ${Z_t^{(n)}}$ is a Cauchy sequence in $L^2$.

   <font color='red'>_proof_</font> $E(Z_t^{(n)}-Z_t^{(m)})^2=\int_0^t (H_s^{(n)}-H_s^{(m)})^2ds\leq tE(O_n+O_m)^2\rightarrow 0$

   So it is converges in $L^2$ by completeness, so it converges in prob, so it's well-defined. 

   **Theorem Ito's isometry for bounded cts process** $E[Z_t^2]=\int_0^t E[H_s^2]ds$

   <font color='red'>_proof_</font> 
   $$
   E[Z_t^2]=\lim_{n\rightarrow\infty}E[(Z_t^{(n)})^2]=\lim_{n\rightarrow\infty}\int_0^tE[(H_s^{(n)})^2]ds=\int_0^t E[H_s^2]ds
   $$
   Notice DCT is used for the last inequality.

   Similarly, **quadratic variation** $\langle Z\rangle_t=\int_0^t H_s^2 ds$. 

   Notice $Z_t^2-\langle Z\rangle_t=\lim_{n\rightarrow\infty} (Z_t^{(n)})^2-\langle Z^{(n)}\rangle_t$ converges in $L^1$, and it's a martingale.

   

   Step 2: push the limit to any time

   To define the integral at any time, we need a stronger convergence at those dyadic numbers. Using a diagonalization argument we can pick a subsequence of $\|\Pi_n\|$, such that the convergence for any dyadic number is a.s..

   **Lemma** Suppose $H$ is a bounded cts process. Then for each dyadic number t, $s\rightarrow Z_s$ is a uniformly continuous function on $D\cap [0,t]$.

   <font color='red'>_proof_</font> 

   >  Doob's maximal inequality: If $M_s$ is any square integrable martingale, then 
   > $$
   > P\{\sup\{|M_s-M_0|:0\leq s\leq t\}\geq \epsilon\}\leq \epsilon^{-2}E[M_t^2]
   > $$

   Use Doob's maximal inequality on $Z_s-Z_s^{(n)}$,
   $$
   P\{\sup\{|Z_s-Z_s^{(n)}|:0\leq s\leq t,s\in\mathcal D\}\geq \epsilon\}\leq \epsilon^{-2}E[(Z_t-Z_t^{(n)})^2]\rightarrow 0
   $$
   By taking a subsequence such that $\sum E[(Z_t-Z_t^{(n)})^2]<\infty$ and using Borel-Cantelli lemma, $Z_s$ is a uniform limit of $Z_s^{(n)}$ a.s.. Since $Z_s^{(n)}$ is continuous on s,  so is $Z_s$.

   Now by continuity, we can <font color='red'> **define**</font> the integration at any time by taking limits. 

   Moreover, if $\Pi_n$ is a sequence of partitions then there is a sequence such that for all $s\leq t$,$\int_0^sH_rdB_r=\lim_{n\rightarrow\infty}\sum_{t_j\leq s} H_{t_{j-1}}[B_{t_j}-B_{t_{j-1}}]$.

   For quad. var., $\lim_{n\rightarrow\infty}\sum_{j=1}^{K_n}[Z_{t_j}-Z_{t_{j-1}}]^2=\langle Z\rangle_t=\int_0^t H_s^2 ds$ in prob. also holds.

   

3. Integration of $\mathcal I$ w.r.t. BM

   Let 
   $$
   \phi_N(x)=\left\{\begin{aligned}&-N,&x\leq -N\\&x,&-N\leq x\leq N\\&N,&x\geq N\end{aligned}\right.
   $$
   Let $Z_{t,N}=\int_0^t \phi_N(H_s)dB_s$ and <font color='red'> **define**</font> $Z_t=\lim_{N\rightarrow\infty} Z_{t,N}$.

   Also, the sum definition corresponds: $Z_t=\lim_{n\rightarrow\infty} \sum_{j=1}^{K_n} H_{t_{j-1}}[B_{t_j}-B_{t_{j-1}}]$ in prob.

   As before, $\langle Z\rangle_t=\int_0^t H_s^2ds=\lim_{n\rightarrow\infty}\sum_{j=1}^{K_n}[Z_{t_j}-Z_{t_{j-1}}]^2$ with the limit in prob.

   

4. Integration of $\mathcal I$ w.r.t. local martingale.

   **Proposition** if $H\in\mathcal I$, then $Z_t$ and $Z_t^2-\langle Z\rangle_t$ are local martingales. Moreover, if $H$ is square integrable, then $Z_t\in\mathcal M^2$ and $Z_t^2-\langle Z\rangle_t\in \mathcal  M$.

   <font color='red'>_proof_</font> Let stopping times to be $\tau_N:=\inf\{s:|H_s|\geq N\}$, then $Z_{t\wedge\tau_N}=Z_{t\wedge\tau_N,N}$. Also, $\tau_N\uparrow\infty$. By definition it's a local martingale.

   If $H_t,K_t\in\mathcal I$ and $Z_t=\int_0^t H_sdB_s$, we <font color='red'> **define**</font> $\int_0^t K_sdZ_s=\int_0^t K_sH_sdB_s$. It can also be approximated in prob. by piecewise approximation.

   _Remark_ cts local martingale+ Brownian filtration $\Leftrightarrow$ stochastic process w.r.t. BM

   

5. Covariance process $(Z,Y)_t$

   ***Definition*** If $Z_t=\int_0^t H_sdB_s$ and $Y_t=\int_0^t K_sdB_s$, the **covariance process** is defined by $\langle Z,Y\rangle_t=\int_0^t H_sK_sds$.

   Under this definition, $\langle Z\rangle_t=\langle Z,Z\rangle_t$ and $4\langle Z,Y\rangle_t=\langle Z+Y\rangle_t-\langle Z-Y\rangle_t$ which implies $\langle Z,Y\rangle_t$ is a local martingale.

   > The sum of local martingales is also a local martingale.
   >
   > proof: If X is a local martingale with stopping time $t$ and Y is a local martingale with stopping time $s$ then the stopping time of X+Y is $\tau_n=\min\{s_n,t_n\}$.

   Similarly, $\lim_{n\rightarrow\infty}\sum_{j=1}^{K_n} (Z_{t_j}-Z_{t_{j-1}})(Y_{t_j}-Y_{t_{j-1}})=\langle Z,Y\rangle_t$ in prob.

   Moreover, $Z_tY_t-\langle Z,Y\rangle_t=\int_0^t Z_sdY_s+\int_0^t Y_sdZ_s$.

   Differentiate both side, we can arrive at **Integration by part formular**

   

6. Ito's formular

   Suppose $h(t,x)$ is a collection of random variables indexed by $(t,x)$, and call it **adapted cts function** if (i) $h(t,x)$ is continuous on $\mathbb R_+\times\mathbb R$ (ii) for each $x\in\mathbb Q$, $h(t,x)\in\mathcal I$.

   Let $\mathcal A$ be the set of adapted cts functions and let $\mathcal A_{1,2}$ be the set of $h(t,x)$ where $\dot{h},h',h''$ exists (dot implies derivation against t and prime implies against s)

   **Theorem Ito's formular** Suppose $H\in\mathcal I$ and $Z_t=\int_0^t H_sdB_s$, $h\in\mathcal A_{1,2}$, then
   $$
   h(t,Z_t)-h(0,Z_0)=\int_0^t h'(s,Z_s)H_sdB_s+\int_0^t[\dot{h}(s,Z_s)+\frac{1}{2}h''(s,Z_s)H_s^2]ds
   $$
   Differentiation form is 
   $$
   dh(t,Z_t)=\dot{h}dt+h'H_tdB_t+\frac{1}{2}h''H_t^2dt
   \\dh(t,Z_t)=\dot{h}dt+h'dZ_t+\frac{1}{2}h''(dZ_t)^2
   $$

7. Integration of $\mathcal I$ w.r.t. semi-martingale

   Let$\vec{B_t}=(B_t^1,...,B_t^d)$ be a d-dim Brownian motion.

   > A stochastic process $X_t$ is a semi-martingale if it can be written as $X_t=X_0+M_t+A_t$, where $X_0$ is the start, $M_t$ is a local martingale (as a noise) and a process of finite variation (as a trend).

   Let $Z_t=R_t+\int_0^t \vec{H_s}\cdot\vec{dB_s}:=R_t+\sum_{i=1}^d \int_0^tH_s^jdB_s^j$, where $R_t$ is a B.V. adapted process. $\langle Z\rangle _t$ is defined to be $\int_0^t \sum_{j=1}^d (H_s^j)^2 ds$.

   ***Definition*** $\int_0^t J_sdZ_s:=\int_0^t J_sdR_s+\sum_{j=1}^d\int_0^t J_sH_s^jdB_s^j$.

   **Theorem Ito's formular for semi-martingale** if $Z^1,...,Z^m$ are semi-martingales and $h\in\mathcal A_{1,2}$, then
   $$
   h(t,\vec{Z_t})-h(0,\vec{Z_0})=\int_0^t\dot{h}(s,\vec{Z_s})ds+\sum_{i=1}^m\int_0^th_i(s,\vec{Z_s})dZ_s^i+\frac{1}{2}\sum_{1\leq i\leq m,1\leq l\leq m}\int_0^t h_{il}(s,\vec{Z_s})d\langle Z^i,Z^l\rangle_s
   $$

8. Applications of Ito's formular

   (i) Exponential martingale: $Z_t=\int_0^t\vec{H_t}\cdot d\vec{B_t}$ is a local martingale. 

   Let $Y_t=e^{Z_t}$, then 
   $$
   dY_t=e^{Z_t}dZ_t+\frac{1}{2} e^{Z_t}(dZ_t)^2=e^{Z_t}dZ_t+\frac{1}{2} e^{Z_t}|\vec{H_t}|^2dt
   $$
   Let $M_t=e^{Z_t-\frac{1}{2}\langle Z\rangle _t}$, then
   $$
   dM_t=M_td(Z_t-\frac{1}{2}\langle Z\rangle_t)+\frac{1}{2} M_t d(Z_t-\frac{1}{2}\langle Z\rangle_t)^2=M_tdZ_t
   $$
   If the term w.r.t. $dt$ is not 0, the process get a trend with time to increase or decrease. So $Y_t$ is a submartingale and $M_t$ is a martingale.

   (ii) Bessel Process: Let $\vec{B_t}$ be a standard d-dim BM, and $\vec{B_0}\neq 0$. Let $f(x)=|x|$, then $\nabla f=\frac{x}{|x|}$ and $\Delta f=\frac{d-1}{|x|}$. By Ito's formular,
   $$
   d|\vec{B_t}|=\frac{\vec{B_t}}{|\vec{B_t}|}d\vec{B_t}+\frac{1}{2}\frac{d-1}{|\vec{B_t}|}dt
   $$
   It satisfies the SDE: $dY_t=\frac{a}{Y_t}dt+d\tilde{B_t}$ where $a=\frac{d-1}{2}$, and $\tilde B_t$ is a standard Brownian motion (Notice on above equation, $\int_0^T\frac{\vec{B_t}}{|\vec{B_t}|}d\vec{B_t}$ has quadratic variation $t$, so it's Brownian). $Y_t$ is called a Bessel-d process.

   _attachment_ a chart:

   |        | d$B_t$ | dt   |
   | ------ | ------ | ---- |
   | d$B_t$ | dt     | 0    |
   | dt     | 0      | 0    |

   _Remark_ As above we have seen the integration of adapted cts process is always a local martingale. Is the inverse true?
   
   **Theorem Martingale representation theorem** Suppose $M_t$ is an $\mathcal F_t$-martingale (w.r.t. $\mathbb P$) and $M_t\in L^2(\mathbb P)$ for all $t\geq 0$. Then there exists a unique stochastic progress $g(s,\omega)$ such that $g$ is measurable, adapted, square integrable process and 
   $$
   M_t(\omega)=\mathbb E[M_0]+\int_0^t g(s,\omega)dB_s,\text{a.s. for all }t\geq 0
   $$

### Class 2 Stochastic calculus, Bessel process and Overview of SLE

1. time change of martingales

   Fluctuation is determined by its parameterization, e.g., (the realization of) $B(t)$ and $B(2t)$ have different fluctuation. However, for $B(2t)$, if the time run in a rate of $t'=\frac{1}{2}t$, then it recovers to a standard BM. Actually, (local) martingales have its "intrinsic clock", while under this clock, the (local) martingale run in the same way as $B(t)$.

   **Proposition** Suppose $\lim_{t\rightarrow\infty}\langle Z\rangle_t=\lim_{t\rightarrow\infty}\int_0^t H_s^2ds=\infty$, and $\tau_r=\inf\{t:\langle Z\rangle_t=r\}$. Let $W_r=Z_{\tau_r}$, then $W_r$ is a SBM w.r.t. $\mathcal F_{t_r}$.

   <font color='red'>_proof_</font> It suffices to show that for every $r_0<r$, that the distribution of $W_r-W_{r_0}$ conditioned on $\mathcal F_{\tau_{r_0}}$ is normal, mean 0 and variance $r-r_0$, and it's independent increment process.

   To examine it's a normal distribution, we use characteristic function: Let $M_t=e^{iyZ_t+\frac{y^2}{2}\langle Z\rangle_t}$, then 
   $$
   dM_t=M_t(iydZ_t+\frac{y^2}{2}d\langle Z\rangle_t)+\frac{1}{2}M_t(iydZ_t+\frac{y^2}{2}d\langle Z\rangle_t)^2=iyM_tdZ_t
   $$
   (Use Ito's formular and the "multiplication table")

   So $M_t$ is a local martingale. By Optional stopping theorem, use the stopping time $\tau$, we have $\mathbb E e^{iyZ_{\tau_r}+\frac{y^2}{2}r}=\mathbb E M_t=\mathbb EM_0=1$, so $Z_{\tau_r}$ has char. function $e^{-\frac{y^2}{2}r}$, it's of mean 0 and variance r. After slight arguments, we can complete the proof.

2. Girsanov's transformation

   The aim is to construct a good measure to deal better with drift.

   Suppose $K_s\in b\mathcal I$ and $|K_s|\leq N\ \forall s$, and $X_t=B_t-\int_0^t K_r dr$. I want to construct a measure, where $X_t$ is a martingale on it.

   The construction is as follows: 

   Let $M_t=\exp\{\int_0^t K_sdB_s-\frac{1}{2}\int_0^t K_s^2ds\}$. Since it's a local martingale (by Ito's formular; as above), and $0\leq M_t\leq e^{NB_t}$, so it's uniformly integrable on every bounded interval. So it's a positive martingale. 

   Let $M_t=\frac{d\mathbb Q_t}{d\mathbb P}$, and $\mathbb E_{\mathbb Q_t}$ be the expectation w.r.t. $\mathbb Q_t$, then for every $\mathcal F_t$-measurable $Y$, we have $\mathbb E_{\mathbb Q_t}[Y]=\mathbb E[Y M_t]$. Moreover, if $s<t$ and $Y$ is $\mathcal F_s$-measurable, we have $\mathbb E[Y M_t]=\mathbb E[\mathbb E[Y M_t|\mathcal F_s]]=\mathbb E[Y \mathbb E[M_t|\mathcal F_s]]=\mathbb E[Y M_s]$. So $\mathbb Q_t\mid_{\mathcal F_s}=\mathbb Q_s $, we can extend it to $\mathbb Q$ such that for all $t$, $\mathbb Q\mid_{\mathcal F_t}=\mathbb Q_t$.

   Or from another perspective, since $M_t$ is a positive martingale, it must converge to $M_\infty$. Define $M_\infty=\frac{d\mathbb Q}{d\mathbb P}$.
   
   **Proposition** $X_t$ is a martingale w.r.t. $(\mathbb Q,\mathcal F)$.
   
   <font color='red'>_proof_</font> It suffices to show $\mathbb E_{\mathbb Q}(X_t\mid \mathcal F_s)=X_s$. By definition, it suffices to show for all $A\in\mathcal F_s$, $\mathbb E_\mathbb Q X_t1_A=\mathbb E_\mathbb Q X_s1_A$, i.e., $\mathbb EX_t1_AM_t=\mathbb EX_s1_AM_s$. To prove this, we prove $X_tM_t$ is a martingale.
   
   By the formular of changing of variable, $dX_tM_t=X_tdM_t+M_tdX_t+d\langle X,M\rangle_t=...dB_t$, we can verify $X_tM_t$ is a martingale.
   
   For n-dim case, let $Z_t=\sum_{j=1}^d\int_0^t H_s^jdB_s^j$ , $M_t=\exp\{Z_t-\langle Z\rangle_t/2\}$, and $X_t=Z_t-\int_0^t M_r^{-1}d\langle Z\rangle_r$.
   
   **Example** Suppose $B_0=x>0$, let $M_t=B_t$ and let $T=\inf\{t:B_t=0\}$. Then for $0\leq t<T$, $dM_t=dB_t$ and hence $K_t=1/B_t$. 
   
   Let $\mathbb Q_t$ be such that $\frac{d\mathbb Q_t}{\mathbb P}=x^{-1}M_{t\wedge T}$. The process $\tilde{B}_s=B_s-\int_0^s\frac{1}{B_r}dr$, $0\leq s\leq t$ is a standard Brownian motion w.r.t. $\mathbb Q_t$. In other form, $dB_s=\frac{1}{B_s}ds+d\tilde{B}_s$. This is the Bessel equation for $d=3$.
