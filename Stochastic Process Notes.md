Stochastic Process Notes 

1. ### Martingales

   1. **conditional expectation** 

      **conditional expectation in $L^2$**: Given $(\Omega,\mathcal{F},\mathbb{P})$, $\mathcal{G}$ be the sub-$\sigma$-algebra of $\mathcal{F}$. If $X\in\mathcal{G}$, then $X\in\mathcal{F}$,which indicates an inclusion $L^2(\mathcal{G},\mathbb{P})\hookrightarrow L^2(\mathcal{F},\mathbb{P})$, actually this is a isometry. In particular, $L^2(\mathcal{G},\mathbb{P})$ is a closed subspace of $L_2(\mathcal{F},\mathbb{P})$, and we can consider the orthogonal projection $\Pi_\mathcal{G}$. 

      Given $X\in L^2(\mathcal{F},\mathbb{P})$, $\Pi_\mathcal{G}(X)$ is called the **conditional expectation** of $X$ given $\mathcal{G}$.

      For instance, if $\mathcal{G}=\mathcal{F}$, $\Pi_\mathcal{G}(X)=X$ since we know all information. If $\mathcal{G}=\sigma\{\emptyset\}$, $\Pi_\mathcal{G}(X)=\mathbb{E}(X)$ since we know no information.

      _Note_: By Cauchy-Schwarz inequality, $L^2(\mathbb{P})\subset L^1(\mathbb{P})$ (Since the measure of whole space is 1) .

       ***Definition*** (global) Let $X\in L^1(\mathbb{P})$, a conditional expectation of X given $\mathcal{G}$ is a $\mathcal{G}$-measurable random variable $Y$ such that $\mathbb{E}[\mathbb{1}_A X]=\mathbb{E}[\mathbb{1}_A Y]\ \forall A \in \mathcal{G}$, such $Y$ is called a **version** of $\mathbb{E}[X|\mathcal{G}]$. (unique up to a.s. equal)

      Link with previous approach: If $X\in L^2(\mathbb{P})$, $X=\Pi_{\mathcal{G}}(X)+Z$, with Z in the orthogonal completion of $L^2(\mathcal{G},\mathbb{P})$. For all $A\in\mathcal{G}$, $\mathbb{1}_A\in L^2(\mathcal{G},\mathbb{P})$, hence 
      $$
      \mathbb{E}[X\mathbb{1}_A]=\mathbb{E}[\Pi_\mathcal{G}(X)\mathbb{1}_A]+\mathbb{E}[Z\mathbb{1}_A]=\mathbb{E}[\Pi_\mathcal{G}(X)\mathbb{1}_A]
      $$
      since $\langle Z,\mathbb{1}_A\rangle=0$. So $\Pi_\mathcal{G}$ is a version of $\mathbb{E}[X|\mathcal{G}]$ 

      **Lemma** Let $Y$ be a version of $\mathbb{E}[X|\mathcal{G}]$, then $\mathbb{E}|Y|\leq\mathbb E |X|$, in particular $Y\in L^1(\mathbb P)$.

      <font color='red'>_proof_</font> 
      $$
      \mathbb E |Y| = \mathbb E [Y\mathbb 1_{\{Y>0\}}]-\mathbb E[Y\mathbb 1_{\{Y\leq 0\}}] = \mathbb E [X\mathbb 1_{\{Y>0\}}]-\mathbb E[X\mathbb 1_{\{Y\leq 0\}}]\\\leq\mathbb E [|X|\mathbb 1_{\{Y>0\}}]+\mathbb E[|X|\mathbb 1_{\{Y\leq 0\}}]=\mathbb E |X|
      $$
      **Uniqueness** 

      <font color='red'>_proof_</font> Let $Y_1,Y_2$ be two version. Let $\varepsilon>0$, 
      $$
      \varepsilon\mathbb P(Y_1-Y_2)\leq\varepsilon\mathbb E [(Y_1-Y_2)\mathbb 1_{Y_1-Y_2\geq\varepsilon}]=\mathbb E [(X_1-X_2)\mathbb 1_{Y_1-Y_2\geq\varepsilon}]=0
      $$
      So $\mathbb P (Y_1-Y_2\geq\varepsilon)=0$, by symmetry $\mathbb P (|Y_1-Y_2|\geq\varepsilon)=0$, so $Y_1=Y_2$ a.s.

      **Existence** 

      <font color='red'>_proof_</font> 

      Case: $L^2(\mathbb P) $ is dense in $L^1(\mathbb P)$ (the most common case). 

      In this case, for all $X\in L^2(\mathbb P)$, $\Pi_\mathcal G(X)$ is the unique version. Now let $X\in L^1(\mathbb P)$ and $(X_n)\in L^2(\mathbb P)$, s.t. $X_n\rightarrow X$ in $ L^1$, so from the present lemma,
      $$
      \mathbb E|\mathbb E[X_n|\mathcal G]-\mathbb E[X_m|\mathcal G]|\leq \mathbb E|\mathbb E[X_n-X_m|\mathcal G]|\leq \mathbb E|X_n-X_m|
      $$
      Since $X_n$ converges in $ L^1$, $\mathbb E[X_n|\mathcal G]$ is also Cauchy, so it converges in $ L^1$ to some variable, say $Y$. $Y$ is $\mathcal G$-measurable as a limit and it's easy to verify it's surely a version.

      Case: density is not assumed. Suppose $X\geq 0$

      ***Definition*** We say a measure $\mathbb Q$ is **absolutely continuous** w.r.t. $\mathbb P$ if $\mathbb P (A)=0$ imply $\mathbb P (B) =0$.

      **Theorem (Radon Nikodym)** If $\mathbb Q \ll \mathbb P$, there exists a measurable function $Z$ s.t. $\int_A Z d\mathbb P = \mathbb Q (A) \ \forall\ A\in\mathcal F$, usually we write $Z=\frac{d\mathbb Q}{d\mathbb P}$.

      For all $A\in\mathcal G$, define $\mathbb Q (A)=\int_A X d\mathbb P$,

      *claim*: $\mathbb Q$ is a measure. 

      Indeed, give a countable family of disjoint sets $\{A_n\}$, 
      $$
      \mathbb Q(\cup_{n=1}^N A_n)=\sum_{n=0}^N \int_{A_n} X d\mathbb P=\sum_{n=0}^N \mathbb Q (A_n)\rightarrow \sum_{n=0}^\infty \mathbb Q (A_n)
      $$
      By DCT, $LHS\rightarrow Q(\cup_{n=0}^\infty A_n)$. Meanwhile, $\mathbb Q\ll\mathbb P$.

      By **Radon-Nikodym theorem**, there exists a version $\frac{d\mathbb Q}{d \mathbb P}$.

      In general case, write $X=X_+-X_-$.

   2. Properties of conditional expectation.

      **Theorem** Let $X,Y\in L^1(\mathbb P)$

      (i) $\mathbb E[aX+Y|\mathcal G]=a\mathbb E[X|\mathcal G]+\mathbb E[Y|\mathcal G]$ 

      (ii) If $X\leq Y$ then $\mathbb E [X|\mathcal G]\leq\mathbb E [Y|\mathcal G]$ 

      <font color='red'>_proof_</font> (i) Verify directly by test sets.

      (ii) From (i) it suffices to show if $X\leq 0$, then $\mathbb E [X|\mathcal G]\leq 0$ a.s. The technique is similar to the proof of uniqueness.

      **Theorem ** Suppose $\mathcal G_1\subset\mathcal G_2\subset F$, then 
      $$
      \mathbb E[\mathbb E[X|\mathcal G_1]|\mathcal G_2]=\mathbb E[\mathbb X|\mathcal G_1]=\mathbb E[\mathbb E[X|\mathcal G_2]|\mathcal G_1]
      $$
      <font color='red'>_proof_</font> All random variables are $\mathcal G_1$ measurable, so verify using test sets.

      **Theorem** (Taking out what's known) Let $X,Y\in L^1(\mathbb{P})$ with $XY\in L^1(\mathbb P)$ and $X$ is $\mathcal G$-measurable, then $\mathbb E[XY|\mathcal G]=X\mathbb E[Y|\mathcal G]$ 

      <font color='red'>_proof_</font> First suppose X is an indicator function and verify, then for finite linear combination of indicator functions it holds, and take limit.

      **Theorem** Suppose $X_n\downarrow 0$ a.s., then $\mathbb E [X_n|\mathcal G]\rightarrow 0$ a.s.

      <font color='red'>_proof_</font> since LHS is nondecreasing, it has a limit, say Y. Use DCT to verify.

      **Theorem Conditional Jensen inequality** Let $\varphi:\mathbb R\rightarrow\mathbb R$ convex, and suppose $X,\varphi(X)\in L^1$, then $\varphi(\mathbb E[X|\mathcal G])\leq \mathbb E[\varphi(X)|\mathcal G]$.

      **Corollary** $\|\mathbb E[X|\mathcal G]\|_p\leq\|X\|_p$.

2. ### Continuous martingale

   1. deterministic preliminaries

      1.  Finite variation

         ***Definition*** Let $f:\mathbb R\rightarrow \mathbb R$, continuous. For $n\in\mathbb N$, $T>0$, $V_n(T)=\sum_{k=0}^{2^n-1} |f((k+1)2^{-n}T)-f(k2^{-n}T)|$ then $V(T)=\lim_{n\rightarrow\infty}V_n(T)$ exists for all $T$ and is non-decreasing. If the limit is finite, we say that $f$ has **finite variation**.

         $V(T)$ is a continuous and non-decreasing function.

         **Lemma** $f$ has finite variation $\Leftrightarrow$ f is the difference of two continuous non-decreasing functions.

         <font color='red'>_proof_</font> $\Leftarrow$ verify. $\Rightarrow$ $f=1/2(f+V)+1/2(f-V)$ 

         _Remark_ By Lebesgue's theorem, every increasing function is differentiable a.e., and this gives an 1-1 map: Probability measure $\mu$ on $[0,1]$ to homeomorphisms of $[0,1]$ $f$ such that $f(t)=\mu([0,t])$. So by the previous lemma, we can integrate functions against the differential of finite variation functions.

      2. Quadratic variation

         ***Definition*** Let $f\in C^0(R_+)$, define for $n\in\mathbb N$ and $T>0$, $[f]_t^n=\sum_{k=0}^{2^n-1} (f((k+1)2^{-n}T)-f(k2^{-n}T))^2$. $[f]_t=\lim [f]_t^n$. If the limit exists, we call it the **quadratic variation** of $f$ in $[0,t]$

         _Remark_ Finite variation functions have 0 quadratic function.

   2. Continuous time martingales

      Given $(\Omega,\mathcal F,\mathbb P)$.

      ***Definition*** A **filtration** is a family $(\mathcal F_t)_{t\geq 0}$ of sub-$\sigma$-algebras of $\mathcal F$ s.t. $\mathcal F_s\subset\mathcal F_t$ if $s<t$.We say $(\mathcal F_t)$ satisfy the **usual condition** if: (i) $\mathcal F_t$ contains all P-null sets (ii) $\mathcal F_t$ is right-continuous.

      ***Definition*** A **process** is a measurable map $X:\Omega\times\mathbb R_+\rightarrow\mathbb R$. A process is **adapted** with $(\mathcal F_t)_{t\geq 0}$ if $X_t=X( ,t)$ is $\mathcal F_t$ measurable for all $t$.

      ***Definition*** The **previsible** $\sigma$-algebra $\mathcal P$ is the $\sigma$-algebra generated by the sets $E\times[s,t)$ for $E\in\mathcal F_s$ and $t>s$. A process is **previsible** if it's $\mathcal P$-measurable. In particular, continuous adapted process are previsible. Here continuous means for every $\omega$, $X_t(\omega)$ is a continuous map of $t$.

      Given any process X we can define a filtration $\mathcal F_t=\sigma((X_s)_{0\leq s\leq t})$.

      ***Definition*** A **continuous $(\mathcal F_t)$-martingale** is a continuous adapted, integrable process $X$ s.t. $\mathbb E [X_t|\mathcal F_s]=X_s$ for all $t\geq s$. It's a sub/super-martingale if $\geq$ /$\leq$.

      Let $(t_n)_{n\in\mathbb N}$ s.t. $t_n\uparrow\infty$, then $(X_{t_n})$ is a discrete time $(\mathcal F_{t_n})$-martingale.

      ***Definition*** A **stopping time** is a random variable $T:\Omega\rightarrow\mathbb R_+$, s.t. $\{T\leq t\}\in \mathcal F_t$ for all $t\geq 0$. If X is a martingale, so is $X_t^T:=X_{t\wedge T}$. 

      **Theorem Optional Stopping** TFAE:

      (i) $X$ is a martingale

      (ii) $X^T$ is a martingale

      (iii) For all bounded stopping times $T$, $\mathbb E X_T=\mathbb E X_0$.

      ***Definition*** A **continuous local martingale** is a continuous adapted process s.t. $\exist (T_n)_{n\in\mathbb N}$ stopping time with $T_n\rightarrow\infty$ a.s. and $X^{T_n}$ is a martingale for all $n\geq 1$. In this case, we say $(T_n)$ **reduces** $X$. (there are local martingales which aren't martingales.)

      **Lemma** If $X$ is a local martingale and for all $t$ it's nonnegative, then $X$ is a supermartingale.

      <font color='red'>_proof_</font> Pick any reducing sequence. By conditional Fatou's lemma, $\forall\ t\geq s\geq 0$, 
      $$
      \mathbb E [X_t|\mathcal F_s]=\mathbb E[\liminf_{n\rightarrow\infty}X_t^{T_n}|\mathcal F_s]\leq \liminf_{n\rightarrow\infty}\mathbb E[X_t^{T_n}|\mathcal F_s]=\liminf_{n\rightarrow\infty} X_s^{T_n}=X_s
      $$
      **Corollary** Every bounded local martingale is a true martingale.

      **Corollary** Given any local martingale $X$, $T_n=\inf\{t\geq 0,|X_t|\geq n\}$ is a reducing sequence.

   3. $L^2$ theory

      **Theorem** Let $X$ be a continuous martingale
      $$
      \lambda^p\mathbb P(|X_t|\geq \lambda)\leq\sup_{t\geq 0} \mathbb E[|X_t|^p]\ \forall p\geq1
      \\(\mathbb E \sup_{t\geq 0} |X_t|^p)^{1/p}\leq \frac{p}{p-1}\sup_{t\geq 0} \mathbb E [|X_t|^p]\ \forall\ p\geq1
      $$
      And $X_t\rightarrow X$ for some $X$ in $L^p$.
      
      _Warning_ For $p=1$, need extent requirement $\lim_{\lambda\rightarrow\infty}\sup_{t\geq 0} \mathbb E[|X_k|\mathbb 1_{|X_t|\geq\lambda}]<\infty$, i.e., uniformly integrable.
      
      Now our goal is to put a Hilbert space structure on $L^2$-bounded martingales:
      
      Let $\mathcal H$ be the set of all continuous martingale such that $\mathbb E [\sup_{t\geq 0}|X_t|^2]<\infty$, endowed with the Euclidean norm $\mathbb E [X_\infty^2]$. This is a norm more than a seminorm: 
      
      if $\mathbb E [X_\infty^2]=0$, then for all $t>0$, $\mathbb E X_t^2 \leq \mathbb E[\mathbb E[X_\infty^2|\mathcal F_t]] = 0$.
      
      **Lemma** If $X$ is a martingale and is not constant, then $X$ has infinite total variation.
      
      <font color='red'>_proof_</font> Observe that for a martingale $M$,  for all partitions $0=t_0<t_1<...<t_n=t$, suppose $M_0=0 a.s.$
      $$
      \begin{aligned}
      \mathbb E[M_t^2]&=\mathbb E [(\sum_{k=0}^{n-1} M_{t_{k+1}}-M_{t_k})^2]
      \\&=\sum_{k=0}^{n-1} \mathbb E (M_{t_{k+1}}-M_{t_k})^2+2\sum_{k=0}^{n-1}\mathbb E[(M_{t_{k+1}}-M_{t_k})\sum_{j=k+1}^{n-1}(M_{t_{j+1}}-M_{t_j})]
      \\&=\sum_{k=0}^{n-1} \mathbb E (M_{t_{k+1}}-M_{t_k})^2
      \end{aligned}
      $$
      since we notice: 
      $$
      \mathbb E[(M_{t_{k+1}}-M_{t_k})(M_{t_{j+1}}-M_{t_j})]=\mathbb E [(M_{t_{k+1}}-M_{t_k})\mathbb E (M_{t_{j+1}}-M_{t_j}|\mathcal F_{t_k})]=0
      $$
      This is quite tricky and useful. After this, 
      $$
      RHS\leq\mathbb E [\sup_{0\leq k\leq n-1} |M_{t_{k+1}}-M_{t_k}|\sum_{k=0}|M_{t_{k+1}}-M_{t_k}|]
      $$
      Since LHS is positive and $M_t$ is continuous, it must have infinite variation.
      
      On the other hand, if a martingale has finite variation, it must be a constant.
      
      **Theorem** $\mathcal H$ is a Hilbert space.
      
      <font color='red'>_proof_</font> The last thing to prove is that $\mathcal H$ is complete.
      
      We introduce another norm $\left\lvert\!\left\lvert\!\left\lvert X \right\rvert\!\right\rvert\!\right\rvert=\mathbb E [\sup |X_t|^2]$ 
      
      Clearly $\|X_\infty^2\|\leq \left\lvert\!\left\lvert\!\left\lvert X \right\rvert\!\right\rvert\!\right\rvert$  and $\left\lvert\!\left\lvert\!\left\lvert X \right\rvert\!\right\rvert\!\right\rvert\leq 2\|X_\infty^2\|$. So they are equivalent. Now we prove the space is complete under this norm.
      
      Pick a Cauchy sequence $(X^n)$ in $\mathcal H$, then extract a subseries which converges fast enough and get a continuous process $X$, and verify it is a martingale.
      
      **Theorem** Let $M$ be a continuous local martingale, then $M$ has finite quadratic variation, denoted by $[M]$. Moreover, $[M]$ is the unique increasing, adapted process such that $M^2-[M]$ is a continuous local martingale (up to a constant) .
      
      _Remark_ The prod variation gives a way to reparametrize $M_t$,i.e., define $N_t=M_{\phi(t)}$ then $\phi(t)$ is the unique time s.t. $[M]_{\phi(t)}=t$.
      
      <font color='red'>_proof_</font> 
      
      Uniqueness: If if we are given two increasing adapted process $A,B$ s.t. $M^2-A,M^2-B$ are local martingale, then $A-B$ is also a local martingale. But it's of finite variation, so it's a constant.
      
      Existence: the idea is to discretize and put to the limits using $L^2$ inequalities. 
      
      The detail is left to other references. 
      
      
      
      The property of finite quadratic variation function: 
      
      Intuitively, if $f$ is of nonzero and finite quadratic variation, $f(t+\varepsilon)-f(t)\approx\sqrt{\varepsilon}\gg\varepsilon$, which implies have wild conditions.
      
      Recall $(\xi_n)~\mathcal N(0,1)$, i.i.d., Then $S_n/n\rightarrow 0$ a.s. by SLLN, and $S_n/\sqrt{n}=_d \mathcal N(0,1)$. So if we fix $n$ and let $f(k/n)=\sum_{j=0}^k \frac{\xi_j}{\sqrt{n}}$, the variation of f in $[k/n,(k+1)/n]$ is typically of order $1/\sqrt{n}$ .

3. ### Markov chain 

   Given $(\Omega,\mathcal F,\mathbb P)$ and $(S,\mathcal S)$ measurable space where $\mathcal S$ is finitely generated.

   ***Definition*** A **Markov chain** is a process $X:\Omega\times\mathbb N\rightarrow S$ s.t. $\mathbb P(X_{n+1}\in A|\sigma(X_1,...,X_n))=\mathbb P(X_{n+1}\in A|\sigma(X_n))$.

   ***Definition*** A **transition probability** is a map $p:S\times\mathcal S\rightarrow R_+$ s.t.

   (i) a.e. $x\in S$, $p(x,)$ is a probability on $(S,\mathcal S)$ 

   (ii) For all $A\in\mathcal S$, $x\rightarrow p(x,A)$ is measurable.

   _Note_ Given a transition probability $p$, we can define

   (i) A new measure $\mu p$ by $(\mu p)(B)=\int_S p(x,B)\mu(dx)$.

   (ii) an operator $P$ on the space of bounded measurable function by $Pf(x):=\int f(y)p(x,dy)$. This operator has norm 1,and satisfies $\int_\mathbb R f(y)(\mu p)(dy)=\int _S Pf(x) \mu(dx)$.

   (iii) We can also think of a transition probability as an operator$P^*$ on the space of probability measure on $(S,\mathcal S)$: for all bounded measurable function $f$, $P^*\mu(f)=\int f P^*\mu=\int Pf \mu$ 

   **Example** Simple random walk: Let $S=\mathbb Z$ with usual $\sigma$-algebra and $p(n,n+1)=p(n,n-1)=1/2$, $p(n,m)=0$ if $n=m$ or $|n-m|>1$.

   More generally, given a transition probability $p$ and a probability measure $\mu$, we can define a family of probability measure $P_n$ on $S^n$ by $P_n(A_0\times\cdots\times A_n)=\int_{A_0\times\cdots\times A_n } d\mu(x_0)p(x_0,dx_1)\cdots p(x_{n-1},dx_n)$ . By Kolmogorov's extension theorem, $(P_n)$ extends to a probability measure on $S^{\mathbb N}$

   **Claim** This defines a Markov chain with state space $S$.

   Suppose S is a discrete set,
   $$
   \mathbb P(X_0=x_0,...,X_n=x_n)=p(x_0,x_1)...p(x_{n-1},x_n)
   $$
    On the other hand, 
   $$
   LHS=\mathbb P(X_n=x_n|X_{n-1}=x_{n-1},...,X_0=x_0)\mathbb P(X_{n-1}=x_{n-1},...,X_0=x_0)
   $$
   whence
   $$
   p(x_{n-1},x_n)=\mathbb P(X_n=x_n|X_{n-1}=x_{n-1},...,X_0=x_0)
   $$
   independent of the values of the process up to time $n-2$, which is a Markov chain.

   **Definition** A **stopping time** is a measurable, $\mathbb N$-valued function $N$ s.t. $\{N=n\}$ is $\mathcal F$-measurable.

   **Theorem Strong Markov Property** Let $N$ be an a.s. finite stopping time. $\mathcal F_N$ is the $\sigma$-algebra generated by $\{N\leq n\}\cap \mathcal F_n$, then $\mathbb P(X_{N+1}\in A|\mathcal F_N)=\mathbb P(X_{N+1}\in A| X_N)\ \forall\ A\in\mathcal S$.

   <font color='red'>_proof_</font> 
   $$
   \begin{aligned}
   LHS&=\sum_k \mathbb P(X_{N+1}\in A,N=k|\mathcal F_N)\mathbb P(N=k)
   \\&=\sum_k \mathbb P(X_{N+1}\in A|X_k)\mathbb P(N=k)
   \\&=\mathbb P(X_{N+1}\in A|X_N)
   \end{aligned}
   $$
   **Definition** **Important stopping times** Let $A\in\mathcal S$. Define $T_A^0=0$, $T_A^{k+1}:=\inf\{n>T_A^k\ s.t. X_n\in A\}$ 

   **Lemma** Let $y\in S$. $\mathbb P_x (T_y^k<\infty)=\mathbb P_x(T_y^1<\infty)\mathbb P_y(T_y^1<\infty)^{k-1}$ ($\mathbb P_x$ means initial probability distribution $\mu$ is $\delta_x$, more clearly, $\mathbb P_x(A)=\mathbb P(A|X_0=x))$ 

   <font color='red'>_proof_</font> 
   $$
   \mathbb P_x(T_y^k<\infty)=\mathbb P_x(T_y^k<\infty|T_y^{k-1}<\infty)\mathbb P_x(T_y^{k-1}<\infty)=\mathbb P_y(T_y^1<\infty)\mathbb P_x(T_y^{k-1}<\infty)
   $$
   Since we can regard this as restart Markov chain at $k-1$. By induction the proof is complete.

   **Theorem Reflection principle for SRW** Let $(\xi_n)_{n\in\mathbb N}$ be i.i.d. $\mathbb R$-valued random variables, and $S_n=\sum_{k=1}^n \xi_k$, then $\mathbb P(\sup_{1\leq k\leq n} S_k\geq a)\leq 2\mathbb P(S_n\geq a)$ 

   <font color='red'>_proof_</font> Define 
   $$
   \tilde \xi_k=\left\{\begin{array}{rcl}\xi_k \ &if&\ k\leq T:=\min\{n:S_n\geq a\}\\-\xi_k \ &if&\ k>T\end{array}\right.
   $$
   i.e., the new process is defined so that when the primary process hit a, it turn back.

   Then the process $(\tilde{S_n})=_d (S_n)$ by symmetry of $\xi$. 

   So $\{T\leq n\}\subset\{S_n\geq a\}\sqcup\{\tilde S_n\geq a\}$, and take probability.

   Here is a plot:

   <img src="C:\Users\m1500\Desktop\Durrent\images\reflection_principle_simple.png" style="zoom: 15%;" />

4. Recurrence and Transience

   Given a discrete state space $S$.

   ***Definition*** A state $y\in S$ is **recurrent** if $\mathbb P_y(T_y<\infty)=1$ where $T_y=\min\{n>0:X_n=y\}$, **transient** otherwise.

   In other words, If $y$ is recurrent, $\mathbb P(X_n$ visits $y$ i.o.$)=1$.

   Let $N(y)=\sum_{n=0}^\infty \mathbb 1_{X_n=y}$ be the number of visits to $y$. 

   **Theorem** $\mathbb E[N(y)]=\infty \Leftrightarrow y$ is recurrent. 

   If $y$ is recurrent, $\mathbb E[N(y)]=\sum_n \mathbb 1_{X_n=y}=\infty$.

   If $y$ is transcient,
   $$
   \mathbb E[N(y)]=\mathbb E\sum_{n=1}^\infty \mathbb 1_{N(y)\geq n}=\sum_n \mathbb P_x(T_y^n<\infty)=\frac{\mathbb P_x(T_y^1<\infty)}{1-\mathbb P_y(T_y^1<\infty)}<\infty
   $$
   **Theorem** If $x$ is recurrent and $\mathbb P_x(T_y<\infty)>0$, then $y$ is recurrent.

   <font color='red'>_proof_</font> Since $\mathbb P_x(T_y<\infty)>0$, we can pick a finite path $\gamma$ from $x$ to $y$ occuring with positive possibility.

   So $\mathbb P_x(T_x=\infty)\geq \mathbb P_x(\gamma)\mathbb P_y(T_x=\infty)$, and since $LHS=0$, so $\mathbb P_y(T_x=\infty)=0$.

   This implies we can find another finite path $\gamma'$ from $y$ to $x$ occuring with positive probability.

   define $p^n(x,y)$ to be the possibility that $x$ moves to $y$ in $n$ steps, then $p^{L+n+K}(y,y)\geq \mathbb P(\gamma')p^n(x,x)\mathbb P(\gamma)$, where $\gamma'$ is of length L and $\gamma$ is of length K. 

   So $\sum_{n=0}^\infty p^{L+n+K}(y,y)\geq \mathbb P(\gamma')\sum_{n=0}^\infty p^n(x,x) \mathbb P(\gamma)=\infty$ since $x$ is recurrent and the series is just $\mathbb E[N(x)]$.

   So $\mathbb E[N(y)]=\infty$, $y$ is recurrent.

   **Definition** Say a subset $C\subset S$ is **closed** if  for all $x\in C$ and $\mathbb P_x(T_y<\infty)>0$, $y\in C$. Say a subset $D\in S$ is **irreducible** if $\forall\ x,y,\mathbb P_x(T_y<\infty)>0$.

   **Theorem** Suppose $C$ is finite and closed then it contains a recurrent state. 

   <font color='red'>_proof_</font> Since $\sum_{y\in C}\mathbb E[N(y)]=\infty$ and $|C|<\infty$, there is some $y$ such that $\mathbb E[N(y)]=\infty$, so $y$ is recurrent.

   **Theorem** Let $R$ be the set of all recurrent states, then $R$ is the union of all irreducible closed components.

   <font color='red'>_proof_</font> If we interduce relation $x\sim y$ if $\mathbb P_x(T_y<\infty)>0$, by definition of recurrence and above theorem, it's a equivalent relation, so each equivalent class is closed and irreducible. Moreover, given $x\in R$, the equivalent class of $x$ is $\{y:\mathbb P_x(T_y<\infty)>0\}$.

   Example

    <img src="C:\Users\m1500\Desktop\Durrent\images\markov_classes.png" style="zoom:50%;" />

   **Recurrence of random walk**

   We now study random walk on $\mathbb R^d$, $d\geq 1$. Let $(X_n)_{n\in\mathbb N}$ be i.i.d. random variables on $\mathbb R^d$ of arbitrary distribution, and $S_n=\sum_{k=0}^n X_k$.

   ***Definition*** say $x\in \mathbb R^d$ is a **recurrent value** if $\forall\varepsilon>0, \mathbb P(\|S_n-x\|<\varepsilon\ i.o.)=1$. say $x\in \mathbb R^d$ is a **possible value** if $\forall\varepsilon>0,\exist n\geq 1, \mathbb P(\|S_n-x\|<\varepsilon)>0$.

   Let $U\subset\mathbb R^d$ be the set of recurrent values.

   **Theorem** $U$ is either empty or a closed subgroup of $(\mathbb R^d,+)$. In the second case, $U$ coincides with the set of possible values.

   _Remark_ For common Markov chains, the two sets may not coincide.

   <font color='red'>_proof_</font> suppose $U\neq \emptyset$.

   (i) To prove $U$ is closed, we prove $U^c$ is open. Let $x\in U^c$ and by definition $\exist\varepsilon>0$, $(S_n)$ visits $\mathbb B(x,\varepsilon)$ finite times with positive probability. Then $\forall y\in \mathbb B(x,\varepsilon/2)$, $(S_n)$ visits $\mathbb B(y,\varepsilon/2)$ finite times with positive possibility, so it's open.

   (ii) To prove $U$ is a group, pick $x\in U$. Let $\varepsilon>0$ and $T$ be the first visit time of $\mathbb B(x,\varepsilon)$, so $T<\infty$ a.s.. Now consider $(S_{T+n}-S_T)_{n\geq 0}$ conditionally on $T$, which has the same distribution with $(S_n)$, so $0\in U$.Adapting the argument and we can see addition, inverse are both closed operation.

   (iii) Due to spatial homogeneity, if $S_n$ can visit $x$, then it can visit it infinitely times since $0\in U$, and after hitting it just moves like considering $x$ as the origin.

   We now turn to **simple random walk** in $\mathbb R^d$ defined by $p(x,x\pm e_k)=1/2d\ \forall 1\leq k\leq d$ and $p(x,y)=0$ otherwise. The sequence of stopping times is defined by $\xi_k=0, \xi_k=\min\{n>\xi_{k-1}: S_n=0\}$,i.e., the kth time hitting 0.

   **Lemma** TFAE:

   (i) $\mathbb P(\xi_1<\infty)=1$

   (ii) $\mathbb P(S_n=0\ i.o.)=1$

   (iii) $\sum_{m=0}^\infty \mathbb P(S_m=0)=\infty$ 

   <font color='red'>_proof_</font> 

   (i)$\Leftrightarrow$(ii): $\mathbb P(S_n=0\ i.o.)=\mathbb P(\bigcap_{n=1}^\infty \{\xi_k<\infty)\}=\lim_{k\rightarrow\infty}\mathbb P(\xi_k<\infty)=\lim_{k\rightarrow\infty} \mathbb P(\xi_1<\infty)^k$ by strong Markov property.

   (ii)$\Leftrightarrow$(iii): LHS in (iii) is just the expectation of return times. Use theorem:

   > **Theorem** $\mathbb E[N(y)]=\infty \Leftrightarrow y$ is recurrent. 

   **Theorem** SRW is recurrent for $d\leq 2$ and transient for $d\geq 3$.

   <font color='red'>_proof_</font> Actually, we just need to show the case for $d=2$ and $d=3$.

   (i) d=2: First to observe $\mathbb P(S_{2m+1}=0)=0$. To come back to 0 after 2n steps we must make as many up/down and as many left/right steps.
   $$
   \mathbb P(S_{2n}=0)=4^{-2n}\sum_{k=0}^n C_{2n}^{2k}C_{2k}^kC_{2n-2k}^{n-k}=4^{-2n}(C_{2n}^n)^2\sim\frac{1}{\pi n}
   $$
   since $\sum_n \mathbb P(S_{2n}=0)=\infty$, $S_m=0$ i.o..

   (ii) d=3: 
   $$
   \mathbb P(S_{2n}=0)=6^{-2n}\sum_{k=0}^n\sum_{j=0}^{n-k}C_{2n}^{2k}C_{2n-2k}^{2j}C_{2k}^kC_{2j}^jC_{2n-2k-2j}^{n-k-j}=6^{-2n}C_{2n}^n\sum_{k=0}^n\sum_{j=0}^{n-k}(\frac{n!}{k!j!(n-k-j)!})^2\\\leq 6^{-2n}C_{2n}^n\max_{k,j}\frac{n!}{k!j!(n-k-j)!}\sum_{k=0}^n\sum_{j=0}^{n-k}\frac{n!}{k!j!(n-k-j)!}\lesssim cn^{-3/2}
   $$
   since $\sum_n \mathbb P(S_{2n}=0)<\infty$, $(S_m)$ is transient.

   Now we return to random walk on $\mathbb R^d$.

   **Theorem** Let $\epsilon>0$ be fixed, 

   (i) If $\sum_{n=0}^\infty \mathbb P(\|S_n\|<\epsilon)<\infty$, then it's transient.

   (ii) If $\sum_{n=0}^\infty \mathbb P(\|S_n\|<\epsilon)=\infty$, then it's recurrent.

   <font color='red'>_proof_</font> (i) This follows from Borel-Cantelli lemma directly.

   (ii) This result needs two lemmas: First, there is some epsilon such that $S_n$ returns the ball i.o.; Second, if there is one such epsilon then it holds for any epsilon. This is a powerful result.

   **Lemma 1** If $\sum_{n=0}^\infty \mathbb P(\|S_n\|<\epsilon)=\infty$, then $\mathbb P(\|S_n\|<2\epsilon\ i.o.)=1$.

   <font color='red'>_proof_</font> We are slightly expanding the ball. To prove this, we consider what can happen if $\|S_n\|>2\epsilon$ and how it relates with the transience of random walk.

   For $m,k\in\mathbb N$, consider the event $A_{m,k}=\{\|S_n\|<\epsilon\}\cap\{\|S_{m+n}\|\geq \epsilon, n\geq k-1\}$, i.e., $S_n$ stays in the ball and after $k$ steps it escape and never turn back.

   First, we can see for a fixed $k$, if $A_{m_1,k},A_{m_2,k}$ both occur, then $|m_1-m_2|<k$.

   Next, we estimate:
   $$
   k\geq \sum_{m=0}^\infty\mathbb P(A_{m,k})\geq \sum_{m=0}^\infty\mathbb P(\|S_m\|<\epsilon, \|S_n-S_m\|\geq2\epsilon, n\geq m+k-1)
   $$
   By Markov chain property, we can make a copy independent of $S_n-S_m$ and independent of $S_n$, $\tilde S_n$:
   $$
   RHS=\sum_{m=0}^\infty\mathbb P(\|S_m\|<\epsilon)\sum_{n=k-1}^\infty\mathbb P(\|\tilde{S_n}\|\geq 2\epsilon)=\mathbb P(\|\tilde{S_n}\|\geq 2\epsilon, n\geq k-1)\sum_{m=0}^\infty\mathbb P(\|S_m\|<\epsilon)
   $$
   But the infinite summary diverges, so $\mathbb P(\|S_n\|\geq 2\epsilon\ \forall n\geq k-1)=0$. This implies $\|S_n\|<2\epsilon$ i.o. since k is arbitrary.

   **Lemma 2** Let $m\geq 2$, then $\sum_{n=0}^\infty \mathbb P(\|S_n\|<m\epsilon)\leq (2m)^d\sum_{n=0}^\infty \mathbb P(\|S_n\|<\epsilon)$. The norm is infinite norm in $\mathbb R^d$.

   <font color='red'>_proof_</font> Given $x\in \mathbb B(0,m\epsilon)$. 

   First we segment $\mathbb B(0,\epsilon)$ into some pieces: Let $\Lambda_\epsilon:=\epsilon \mathbb Z^d\cap[-m\epsilon,m\epsilon)^d$, then we have covering $\mathbb B(0,m\epsilon)\subset \cup_{x\in\Lambda_\epsilon}(x+[0,\epsilon)^d)$ . So
   $$
   \sum_{n=0}^\infty\mathbb P(\|S_n\|<m\epsilon)\leq \sum_{n=0}^\infty\sum_{x\in\Lambda_\epsilon} \mathbb P(S_n\in x+[0,\epsilon)^d)
   $$
   Given $x\in \Lambda_\epsilon$, let $T_x$ be the hitting time of $S_n$ to $x+[0,\epsilon)^d$. Then
   $$
   \begin{aligned}
   \sum_{n=0}^\infty\mathbb P(S_n\in x+[0,\epsilon)^d)=&\sum_{n=0}^\infty\sum_{l=0}^\infty\mathbb P(S_n\in x+[0,\epsilon)^d, T_x=l)\\=&\sum_{l=0}^\infty\sum_{n=0}^\infty\mathbb P(\|S_{n+l}-S_l\|<\epsilon, T_x=l)\\=&\sum_{n=0}^\infty\mathbb P(\|S_n\|<\epsilon)
   \end{aligned}
   $$
   And $\#\Lambda_\epsilon=(2m)^d$, so the proof is complete.

   This indicates when we consider smaller ball, the sum of probability is still infinite. 

   Finally by definition, the proof is complete.

   **Theorem Random walk in $\mathbb R^2$** If $\frac{S_n}{\sqrt{n}}\rightarrow_d \mathcal N(0,\sigma^2)$ where $\infty>\sigma>0$, then the random walk is recurrent.

   _Recall_ If $\mu$ is a measure defined on $\mathbb R^d$, its characteristic function is function $\hat{\mu}$ defined by $\hat{\mu}(t)=\int_{\mathbb R^d} e^{itx}d\mu(x)$, i.e., the Fourier transformation.

   Note $\hat{\mu}(0)=\int_{\mathbb R^d}\mu(x)$ is the total measure, for probability measure this is 1. 

   **Theorem** Let $\delta>0$, then $(S_n)$ is recurrent iff $\sup_{\delta<1}\int_{(-\delta,\delta)^d} \Re \frac{1}{1-\hat{\mu}(y)}dy=\infty$, where $\hat{\mu}(y)$ is the characteristic function of $\xi$ and $S_n=\xi_1+...+\xi_n$.

   _Remark_ $\frac{1}{1-\hat{\mu}}$ diverges as $y\rightarrow 0$ since $\hat{\mu}(0)=1$. So for the integral to be infinite, the integrand should blow up at least as $y^{-\alpha}$ for $\alpha>d$ as $y\rightarrow 0$. Commonly, if characteristic function is nearly $\exp(-|t|^\alpha)$, then it is approximately $1-|t|^\alpha$.

5. Invariant measures

   _Recall_ a transition probability $p$ defines an operator $P^*$ on the space of measure on state space. Now we are interested in the fixed points $P^*\mu=\mu$.

   If the law of Markov chains converge weakly as $n\rightarrow\infty$, then it must be a fixed point of $P^*$.

   For discrete state spaces, $P^*\mu=\mu$ is just $\forall y\in S, \sum_x \mu(x)p(x,y)=\mu(y)$.

   **Example simple random walk on $\mathbb Z/n\mathbb Z$** $p([l],[l\pm 1])=1/2$ and 0 otherwise.

   Check that the uniform measure $\Pi([l])=1/N$ is invariant.

   As $n\rightarrow\infty$, this Markov chain "looks like" SRW on $\mathbb Z$ and setting $\mu_k=1$ defines an invariant measure with infinite mass. (notice this is not a probability measure!)

   <img src="C:\Users\m1500\Desktop\Durrent\images\simple random walk on znz.png" style="zoom:25%;" /> 

   A variation of this: 2-circle: Once we reach one cycle, we stayed there forever. Both the uniform measure on the first and second circle are invariant (not pass the bridge), so there is no uniqueness in this case.

   ![](C:\Users\m1500\Desktop\Durrent\images\2-cycle invariant.png)

   In general, if we have several irreducible components, we many have an invariant distribution in each component and any convex combination is also invariant(among different component). This is why most would be stated for irreducible chains.

   **Theorem** Let $\mu$ be an invariant measure (not necessarily a prob. measure) and let $n\in \mathbb N$ and define $Y_n=X_{n-m}$, $0\leq m\leq n$ with $(X_n)$ having initial distribution $\mu$. Then $Y_n$ is a Markov chain with dual transition $q(x,y)=p(y,x)\frac{\mu(y)}{\mu(x)}$

   _Remark_ We are reversing the Markov chain.

   <font color='red'>_proof_</font> We apply the definition, 
   $$
   \mathbb P(Y_{m+1}=y|Y_n=x)=\mathbb P(X_{n-m-1=y}|X_m=x)=\mathbb P(X_{n-m}=x|X_{n-m-1}=y)\frac{\mathbb P(X_{n-m-1}=y)}{\mathbb P(X_{n-m}=x)}\\=\mathbb P(X_1=x|X_0=y)\frac{\mu(y)}{\mu(x)}=p(y,x)\frac{\mu(y)}{\mu(x)}
   $$
   ***Definition*** we say $\mu$ is reversible if $q=p$. 

   If $\mu$ is reversible, then $\mu(x)p(x,y)=\mu(y)p(y,x)$. This equation is called **detailed balance**. In general it can be hard to check.

   Now we consider the **Existence** of invariant measure.

   _Intuitively_, when we run the Markov chain, the fraction of time spent at each point x should give a/the stationary measure. More precisely, the limit of $\mathbb E\sum_{n=0}^{N-1} 1_{X_n=m}/N$.

   **Theorem** Let $x$ be recurrent and $X$ be irreducible. Let $T_x$ be the hitting time of $x$. Define $\mu_x(y)=\mathbb E_x[\sum_{n=0}^{T_x-1}1_{X_n=y}]=\sum_{n=0}^\infty\mathbb P_x(X_n=y,T_x>n)$, then $\mu$ is an invariant measure.

   <font color='red'>_proof_</font> 

   Note $\mu_x(x)=\sum_{n=0}^\infty \mathbb P_x(X_n=x, T_x>n)=\mathbb P_x(X_0=x)=1$ by the definition of hitting time.

   Now we check the definition of stationary: let $z\in S$, then
   $$
   \sum_{y\in S} \mu_n(y)p(y,z)=\sum_y\sum_{n=0}^\infty\mathbb P_x(X_n=y,T_x>n)p(y,z)=\sum_{n=0}^\infty \mathbb P_x(X_{n+1}=z, T_x>n)\\=\left\{\begin{aligned}&\sum_{n=0}^\infty\mathbb P_x(X_n=z, T_x>n)&if\ z\neq x\\&\sum_{n=0}^\infty \mathbb P_x(T_x=n+1)=1=\mu_x(x)&if\ z=x\end{aligned}\right.
   $$
   some details: the change from $\mathbb P_x(X_{n+1}=z, T_x>n)$ to $\mathbb P_x(X_{n}=z, T_x>n)$ since (i) when $n=0$, the second is 0; when $n\neq 0$, since $X_{n+1}=z$ and $T_x>n$, $T_x>n+1$, so it's reasonable.

   Actually, we should argue that $\mu_x(y)<\infty$: Since $\mu_x p=\mu_x$, then for all $n\geq 1$, $\mu_x p^n=\mu_x$, and $\mu_x(x)=1$. Recall that $x$ is recurrent, and $X$ is irreducible implies there is a path from $x$ to $y$ and from $y$ to $x$ both of positive prob., so there is some $p^n(y,x)>0$, and since $\mu_x(y)p^n(y,x)\leq\mu_x(x)$, $\mu_x(y)$ must be finite.

   Now we consider **Uniqueness**.

   **Theorem** Suppose p is irreducible and all states are recurrent. Then the stationary measure is unique up to constant multiples.

   <font color='red'>_proof_</font> Let $\nu$ be a stationary measure. Assume wlog $\mu(a)=1$, where $a\in S$ is a fixed state. We want to show that $\nu=\mu_a$. 

   For any $z\in S$ and $n\in\mathbb N$, 
   $$
   \nu(z)=\sum_y\nu(y)p(y,z)=\nu(a)p(a,z)+\sum_{y\neq a}\nu(y)p(y,z)\\=\nu(a)p(a,z)+\sum_{y\neq a}\nu(a)p(a,y)p(y,z)+\sum_{x\neq a}\sum_{y\neq a}\nu(x)p(x,y)p(y,z)\\=\nu(a)\mathbb P_a(X_1=z)+\nu(a)\mathbb P_a(X_1\neq a, X_2=z)+\mathbb P_\nu (X_0\neq a, X_1\neq a, X_2=z)
   $$
   Continue this process, we get
   $$
   \nu(z)=\nu(a)\sum_{m=1}^n\mathbb P_a(X_k\neq a, 1\leq k<m, X_m=z)+\mathbb P_\nu (X_j\neq a, 0\leq j<n, X_n=z)
   $$
   Let n tends to infinity, we have $\nu(z)\geq \nu(a)\mu_a(z)$, since the first sum has each entry the prob. of $X_m=z, T_a>m$ and the second term $\geq 0$.

   So to claim the equation holds, we want $\mathbb P_\nu (X_j\neq a, 0\leq j<n)\rightarrow 0$. But $\nu$ can be an infinite measure, so this may not work.

   We turn to a little tricky way. Consider
   $$
   \nu(a)=\sum_x\nu(x)p^n(x,a)\geq \nu(a)\sum_x\mu_a(x)p^n(x,a)=\nu(a)\mu_a(a)=\nu(a)
   $$
   since $\nu$ is stationary. And the equality must hold. whenever $p^n(x,a)>0$ for some $n,x$. Since $X$ is irreducible, such $n,x$ must exist, so our proof is complete.

   In summary, for an irreducible Markov chain with one state recurrent, there is a unique stationary measure by construction.

   We should be careful that, until now we are discussing "measure" not a probability measure. The measure of the whole space can be infinite. So now we turn to the problem: When is a stationary measure a prob. measure?

   (i) If $Z_a=\sum_{z\in S} \mu_a(z)<\infty$, then $\pi(z)=\frac{\mu_a(z)}{Z_a}$ is a stationary **distribution**.

   (ii) Otherwise, since the uniqueness tells us that those stationary measures are multiples of $\mu_a$, so there can't be a stationary distribution. 

   **Theorem** If there is a stationary distribution $\pi$ then all states $y$ s.t. $\pi(y)>0$ are recurrent.

   <font color='red'>_proof_</font> Using that $\pi$ is invariant under $p^n$ for all n, $\sum_{x}\sum_{n\in \mathbb N}\pi(x)p^n(x,y)=\sum_{n\in\mathbb N}\pi(y)=\infty$. 

   On the other hand, $\sum_{n=1}^\infty p^n(x,y)=\frac{\mathbb P_x(T_y<\infty)}{1-\mathbb P_y(T_y<\infty)}$.

   So $\infty=\sum_x \pi(x)\frac{\mathbb P_x(T_y<\infty)}{1-\mathbb P_y(T_y<\infty)}\leq \frac{1}{1-\mathbb P_y(y)}$, since $\sum_x \pi(x)=1$ and $\mathbb P_x(T_y<\infty)\leq 1$.

   So $\mathbb P_y(T_y<\infty)=1$, and our proof is complete.

   Next, we find an expression for the stationary distribution.

   **Theorem** If $p$ is irreducible with stationary distribution $\pi$, then then $\pi(x)=\frac{1}{\mathbb E_x(T_x)}\forall x\in S$

   _Remark_ For recurrent states, $\mathbb P_x(T_x<\infty)=1$ but we may have $\mathbb E_x(T_x)=\infty$. This theorem says that, the stationary measure $\mu_x$ can be normalized to a stationary distribution iff $\mathbb E_x(T_x)<\infty$.

   <font color='red'>_proof_</font> define $\pi(x)=\frac{\mu_x(x)}{\sum_{z\in S}\mu_x(z)}$, then
   $$
   \sum_{y\in S}\mu_x(y)=\sum_{y\in S}\sum_{n=0}^\infty \mathbb P_x(X_n=y, T_x>n)=\sum_{n=0}^\infty \mathbb P_x(T_x>n)=\mathbb E_x(T_x)
   $$
   So $\pi(x)=\frac{1}{\mathbb E_x(T_x)}$.

   ***Definition*** We say that $x$ is **positive recurrent** if $\mathbb E_x(T_x)<\infty$ and **null recurrent** otherwise.

   **Theorem** If $S$ is irreducible, then TFAE:

   (i) Some $x\in S$ is positive recurrent.

   (ii) There exists a stationary distribution.

   (iii) All states are positive recurrent.

   <font color='red'>_proof_</font> (ii)$\Rightarrow$(iii)$\Rightarrow$(i) is trivial. For (i)$\Rightarrow$(ii), it's just above theorem. Define $\pi(y)=\frac{\mu_x(y)}{\sum_{z\in S}\mu_x(z)}=\frac{\mu_x(y)}{\mathbb E_x T_x}$.

   **Example M/G/1 queue** We have one desk where client are being serviced.

   (i) Service time has distribution $F$ which is arbitrary and $(T_n)$ i.i.d. representing all serving times.

   (ii) Client arrives as a Poisson point process with parameter $\lambda>0$.

   > [!NOTE]
   >
   > Poisson point process: Conditionally on $T_1$, there are $Possion(\lambda T)$ clients awaiting in the interval $[0,T_n]$. 

   $$
   \mathbb P(\text{k new arrivals in }[0,T])=\int_0^T \mathbb P(\text{ k new arrivals in }[0,t])dF(t)=\int_0^T e^{-\lambda t}\frac{(\lambda t)^k}{k!}dF(t):=a_k
   $$

   If $X_n:=$ \# customs when $n$th client enters service, then $X_n$ is a Markov chain transition:

   (i) $p(0,0)=a_0+a_1$ (ii) $p(n,n+k-1)=a_k$.

   Let $\mu=\sum_{k=0}^\infty ka_k$ be the average number of clients in time $T$.

   Intuitively, the chain has a drift of value $\mu-1$ (arrive $\mu$, leave 1). So we are expecting it's transient for $\mu>1$ and recurrent for $\mu\leq 1$. (for $\mu=1$, we know that RW in $1D$ is recurrent)

   (i) We can compare $X_n$ with RW $S_n=X_0+\sum_{j=1}^n \xi_j$ with $\xi_j$ i.i.d. and $\mathbb P(\xi_1=j-1)=a_j\forall j\geq 0$. So $\mathbb E\xi=\mu -1$.

   Notice $S_n$ and $X_n$ coincide up to hitting time of 0. After this, we always have $S_n\geq X_n$ since $S_n$ can come to negative axis.

   On the other hand, $S_n-(\mu-1)n$ is a martingale. So $X_n$ is a super-martingale when $\mu>1$.So it's transient.

   (ii) When $\mu=1$, 0 is recurrent. We show this by **optional stopping theorem**.

   For all $x\in\mathbb N$, $M\in\mathbb N$​
   $$
   x=\mathbb E_x[X_{T_0\wedge T_M}]=\mathbb E_x[X_{T_0\wedge T_M}|T_0<T_M]\mathbb P(T_0<T_m)+\mathbb E_x[X_{T_0\wedge T_M}|T_0>T_M]\mathbb P_x(T_0>T_M)=M\mathbb P_x(T_0>T_M)
   $$
   Push M to infinity, we can conclude $\mathbb P_x(T_0>\infty)=0$

   (iii) Now we consider strong recurrence for $\mu\leq 1$. 

   1. Observe that $\mathbb E_x(T_{x-1})$ is independent of $x$ (since before hitting 0, we can always consider this as a RW), So $\mathbb E_x(T_0)=\mathbb E_x(T_{x-1})+\mathbb E_{x-1}(T_{x-2})+...+\mathbb E_1(T_0)=x\mathbb E_1(T_0)$. 

   2. When $\mu<1$, $\mathbb E[X_{n+1}-X_n|X_n=x]=\mu-1<0$.

      Stopping at $T_0\wedge n:=\tau_n$, we have
      $$
      \mathbb E_1[X_{\tau_n}]=\mathbb E_1[X_0+\sum_{m=0}^{\tau_n-1}X_{m+1}-X_m]=1+\mathbb E_1\sum_{m=0}^{\tau_n-1}(X_{m+1}-X_m)=1+\mathbb E_1[\tau_n-1](\mu-1)\geq 0
      $$
       so $\mathbb E_1[T_0\wedge n]\leq \frac{1}{1-\mu}$. Let n tend to infinity, we can conclude $\mathbb E_1[T_0]$ is bounded.

   3. On the other hand,

   $$
   \mathbb E_1(T_0)=\sum_{k=0}^\infty a_k\mathbb E_1[T_0|X_1=k]=a_0+\sum_{k=1}^\infty a_k\mathbb E_k[1+T_0]=1+\sum_{k=1}^\infty a_k k\mathbb E_1[T_0]=1+\mu\mathbb E_1[T_0]
   $$

   So $\mathbb E_1[T_0]=\frac{1}{1-\mu}$ when $\mu<1$, infinite when $\mu=1$.

   4. Now consider returning to 0,
      $$
      \mathbb E_0[T_0]=(a_0+a_n)\cdot 1+\sum_{k=2}^\infty a_k\mathbb E_{k-1}[1+T_0]=1+\mathbb E_1[T_0]\sum_{k=2}^\infty(k-1)a_k=\frac{a_0}{1-\mu}
      $$
      

      So when $\mu<1$, it's positive recurrent and when $\mu=1$, it's null recurrent.

6. Asymptotic behavior 

   _Note_ If y is transient, then $p^n(x,y)\rightarrow 0$ as $n\rightarrow\infty$. So we only get interested for recurrent state.

   **Theorem** Let $y$ be recurrent, then $\forall x\in S$, as $n\rightarrow\infty$, $\frac{N_n(y)}{n}\rightarrow \frac{1_{\{T_y<\infty\}}}{\mathbb E_y(T_y)}$ ($\mathbb P_x$ a.s.), where $N_n(y)=\sum_{m=1}^n 1_{\{X_n=y\}}$.

   <font color='red'>_proof_</font> Set $\tau_0=0, \tau_{k+1}=\inf \{n>\tau_k:X_n=y\}$. Then r.v. $(\tau_{k+1}-\tau_k)_{k\geq 1}$ are i.i.d. and $\frac{\tau_k}{k}\rightarrow \mathbb E_y[T_y]$ by SLLN. For each n, there is a unique $k_n\in \mathbb N$ such that $\tau_{k_n}\leq n<\tau_{k_{n+1}}$. So we have $\frac{k_n}{\tau_{k_n}}\leq \frac{N_n(y){n}}\leq \frac{k_n+1}{\tau_{k_n}}$. Since both side converges to $\frac{1}{\mathbb E_y[T_y]}$, we get our conclusion. (If $\tau_n=\infty$, the limit is 0.)

   **Example SRW on $\mathbb Z/N\mathbb Z, N\geq 2$** (Periodicity) In this loop, we can come back to $[0]$ after $2n$ steps, and I can also come back to 0 after a whole loop. 

   i) If N is even, always come back after *even* number of steps

   ii) If N is odd, can come back after *odd* numbers ($\geq N$) as well.

   Return times are the "positive ideal" generated by smallest periods. 

   In general, $I_x=\{n\in \mathbb N\ s.t.\ p^n(x,x)>0\}$. In this example, $d_x=\gcd(I_x)=2, \ if\ 2|N; 1\ if \ 2\nmid N$.

   **Theorem** if $p$ is irreducible and aperiodic with stationary distribution $\pi$, then for all $x$, $p^n(x,\cdot)\rightarrow \pi$ weakly. 

   Now we prove this for discrete state space. In this case, it just says $\forall x,y,p^n(x,y)\rightarrow\pi(y)$.

   _Remark_ For every $x,y\in S$, $p^n(x,y)$ is bounded, so we can extract a convergent subsequence. Since the space is countable, we can find a subsequence converging simultaneously for all $x,y$ by a diagonal argument. So we would have be done if we could prove every subsequential limit is $\pi$. Notice this is not true in general, so we need aperiodicity and irreducibility. To overcome the issue, we are going to use an approach based on **coupling**.

   > [!IMPORTANT]
   >
   > ***Definition*** A **coupling** between two prob. measure p,q on S is a prob. measure on S such that the first (resp. the second) marginal is equal to p(resp. q)
   >
   > **Example**  
   >
   > (i) $p\otimes q$, where $p$ and $q$ are independent.
   >
   > (ii) If $X\sim p$ , then $(X,X)$ is a coupling between p and p.
   >
   > (iii) Suppose you have a die with numbers for {1,2,3,4,5,6}, and you color faces {1,2,3} in black, {4,5,6} in white, then the pair (number, color) is a coupling between a uniform measure on {1,...,6} and {0,1} but not independent. 
   >
   > A natural distance measure when we do coupling is the total variation: $\|\mu-\nu\|_{TV}=\sup_{A\in\mathcal S} |\mu(A)-\nu(A)|=\frac{1}{2}\sum_{x\in S}|\mu(x)-\nu(x)|$. The coefficient 1/2 is to avoid counting twice.
   >
   > If $\mathbb P$ is a coupling with sample $(X,Y)$,  $A\in\mathcal S$, then
   > $$
   > \begin{aligned}
   > |\mathbb P(X\in A)-\mathbb P(Y\in A)|&\leq |\mathbb P(X\in A, X=Y)-\mathbb P(Y\in A, X=Y)|+|\mathbb P(X\in A,X\neq Y)-\mathbb P(Y\in A, X\neq Y)
   > \\&\leq \mathbb P(X\neq Y)
   > \end{aligned}
   > $$

   <font color='red'>_proof_</font> 

   To prove the theorem, we will couple $p^n(x,\cdot)$ with $\pi$ in the following way:

   * Run $X_n$ started from $x$(fixed).
   * Independently, run $Y_n$ started from the stationary distribution.
   * Let $T=\inf \{n\geq 0|X_n=Y_n\}$. For $n\geq T$, set $X_n=Y_n$, evolving through $p$.

   Clearly this is a coupling of the Markov chain with itself, where $X_n$ has law $p^n(x,\cdot)$ and $Y_n$ has law $\pi$ by stationary. We say that the coupling is **successful** if $T<\infty$.

   By the coupling inequality, $\|p^n(x,\cdot)-\pi\|_{TV}\leq \mathbb P(X_n\neq Y_n)=\mathbb P(T>n)$. So it suffices to show $\mathbb P(T>n)\rightarrow 0$.

   1. Before time T, $(X_n, Y_n)$ evolves as the independent product chain on $S\times S$ with transition prob. $\tilde p((x_1,y_1),(x_2,y_2))=p(x_1,x_2)p(y_1,y_2)$. Let $\Delta=\{(z,z):z\in S\}$ be the diagonal, we want to show the product chain hits $\Delta$ a.s.

   2. We want to show $\tilde p$ is irreducible. This depends on:

      **Lemma** 

      (i) If $\mathbb P_x(T_y<\infty)$, then $d_x=d_y$ 

      (ii) If $d_x=1$, then $p^m(x,x)>0$ for all large enough $m$.

      where $d_x$ is the period of state $x$.

      since $p$ is irreducible and aperiodic, then for any $x,y\in S$, $p^m(x,y)>0$ for large enough $m$. Then by the definition of $\tilde p$, $\tilde p^m((x_1,y_1),(x_2,y_2))>0$ for large enough m. So it's irreducible.

   3. Obviously $\pi\otimes\pi$ is stationary for $\tilde p$. This implies every state is positive recurrent by above theorem. So the hitting time of $\Delta$ is finite a.s., i.e., $\mathbb P(T>n)\rightarrow 0$.

   Proof is complete.

   > Digression: Markov process in continuous time
   >
   > Let E be a compact Polish space with Borel $\sigma$-algebra $\mathcal E$. Let $\mathcal C_0(E)=\{f:E\rightarrow \mathbb R: f\text{ is continuous and }f(x)\rightarrow 0\text{ at infinity.}\}$
   >
   > A Feller semigroup is a family $(T_k)_{k\geq 0}$ of bounded operators on $\mathcal C_0(E)$ such that
   >
   > (i) $T_t\geq 0\ \forall t\geq 0$, i.e., $T_tf\geq 0\ \forall t\geq 0$. And $T_t 1=1$ (This is not necessary, but convenient for dealing with prob. measure)
   >
   > (ii) $T_{t+s}=T_t\circ T_s\ \forall t,s\geq 0$ (semigroup property).
   >
   > (iii) $\|T_t f-f\|_{\mathcal C_0 (E)}\rightarrow 0\ \text{ when }t\rightarrow 0\ \forall f\in \mathcal C_0(E)$.
   >
   > The infinitesimal generator is the operator $(A,D(A))$ where $D(A)=\{f\in \mathcal C_0(E), \frac{1}{t} (T_t f-f)\text{ converges uniformly as }t\rightarrow 0\}$, and A is given by $Af={\lim_{t\rightarrow 0}\frac{1}{t}(T_t f-f)}$ for $f\in D(A)$. 
   >
   > Formally, we then have $T_t=e^{tA}$
   >
   > We can construct a transition prob. from a Feller semigroup.
   >
   > **Theorem Riesz-Markov-Kakutani representation theorem** Let E be a compact Hausdorff space and $\Lambda$ be a positive linear form on $\mathcal C_0(E)$, i.e., $\Lambda (f)\geq 0\ \forall f\geq 0$, such that $\Lambda (1)=1$. Then there must be a unique Borel prob. measure $\mu$ on $E$ such that $\Lambda(f)=\int_E fd\mu$ for all $f\in \mathcal C_0(E)$. 
   >
   > And, $\mu$ is outer regular: $\mu(A)=\inf\{\mu(O): O\text{ open }, A\subset O\}$;
   >
   > $\mu$ is inner regular: $\mu(A)=\sup\{\mu(K): K\text{ compact },K\subset A\}$
   >
   > _Note_: There is a version for locally compact spaces.
   >
   > Return to Feller semigroup. Given $(T_t)_{t\geq 0}$ Feller, and let $x\in E$, $f\rightarrow (T_tf)(x)$ is a positive linear form with $T_t 1=1$, so there exists a unique $\mu_x^t$ prob. measure s.t. $T_t f(x)=\int f(y)d\mu_x^t(y)$. Then set $p_t(x,dy)=\mu_x^t(dy)$, $p_t$ is a transition prob.
   >
   > Question: Is there a Markov process associated to $(p_t)_{t\geq 0}$? Actually this is well-developed theory, under some conditions the construction is available.
   >
   > **Example** consider $p_t(x,dy)=e^{-\frac{(x-y)^2}{2t}}\frac{dy}{\sqrt{2\pi t^2}}$ on $\mathbb R$. Because the Gaussian distribution is stable, this is indeed a transition prob.. 
   >
   > Take $X_t i.i.d.\sim\mathcal N(0,1)$​, 
   > $$
   > T_{t+s}f(x)=\mathbb E f(x+\sqrt{t+s}X)=\mathbb Ef(x+\sqrt t X_s+\sqrt t X_t)=T_t\circ T_s
   > $$
   > where $f\in \mathcal C_0(\mathbb R), x\in \mathbb R$. 
   >
   > What is the infinitesimal generator? 
   > $$
   > T_tf(x)=\mathbb E[f(x+\sqrt t X)]=f(x)+\frac{t^2}{2}f''(x)+o(t^2)
   > $$
   > by DCT and $\mathbb E[X^2]=1$. So the infinitesimal generator is $\frac{1}{2} \frac{d^2}{dx^2}$ with domain $\mathcal C_0(\mathbb R)$.
   >
   > _Note_ The semigroup property depends only on the stability of Gaussian. Cauchy distribution also defines a "Cauchy process"

7. Ergodic theorems

   > [!TIP]
   >
   > Here are some preliminaries about ergodicity from PTE.
   >
   > ***Definition*** $X_0,X_1,...$ is said to be a **stationary sequence** if for every $k$, the shifted sequence $(X_{k+n})_{n\geq 0}$ has the same distribution with $(X_n)_{n\geq 0}$.
   >
   > ***Examples*** 
   >
   > (i) $X_i$ are i.i.d.
   >
   > (ii) $X_n$ is a Markov chain with transition prob. $p(x,A)$ and stationary distribution $\pi$. Then if $X_0$ has distribution $\pi$, $X_i$ is a stationary sequence.

   In general, we want to prove results of form "time average converges to spatial average". 

   E.g., if $(X_n)$ stationary sequence. $f:\Omega\rightarrow\mathbb R$, then $\frac{1}{n}\sum_{k=0}^{n-1} f(X_k)\rightarrow\int fd\pi$ a.s..

   ***Definition*** A measurable function $\phi:\Omega\rightarrow\Omega$ is **measure preserving** if $\mathbb P_*\varphi=\mathbb P$,.i.e., $\mathbb P(\varphi^{-1}(A))=\mathbb P(A)\forall A\in\mathcal F$. 

   **Example** (From PTE) Let $\phi$ be a measure preserving function, and let $\phi^0=id, \phi^1(\omega)=\omega, \phi^n(\omega)=\phi\circ\phi^{n-1}(\omega)$, then $(X_n)$ defined by $X_n(\omega)=X(\phi^n(\omega))$ is a stationary sequence when $X\in\mathcal F$, since let $B\in\mathcal R^{n+1}$ and $A=\{\omega: (X_0(\omega),...,X_n(\omega))\in B\}$, we have
   $$
   \mathbb P((X_k,...,X_{k+n})\in B)=\mathbb P(\phi^k\omega\in A)=\mathbb P(\omega\in A)=\mathbb P((X_0,...,X_n)\in B)
   $$
   Actually, reversely for any stationary sequence, we can directly get $\phi$: 

   First Kolmogorov's extension theorem allows us to construct a measure $\mathbb P$ on $(S^\mathbb N, \mathcal S^\mathbb N)$, then the sequence $X_n(\omega)=\omega_n$ has the same distribution as $X_{n+k}(\omega)=\omega_{n+k}$, then let $\phi$ be the shift operator, $\phi(\omega_0,...)=(\omega_1,...)$ and $X(\omega)=\omega_0$. 

   The setting of ergodic theorems are just given by this example: We are given $(\Omega,\mathcal F, \mathbb P)$, and a map $\phi$ preserve $\mathbb P$, and $X_n(\omega)=X(\phi^n(\omega))$.

   ***Definition*** A set $A\in\mathcal F$ is **invariant** if $\varphi^{-1}(A)=A$ up to $\mathbb P$-null sets.

   It's easy to check that the collection $\mathcal I$ of $\varphi$-invariant sets is a sub-$\sigma$-algebra of $\mathcal F$.

   ***Definition*** Say $\varphi$ is **ergodic** if $\mathcal I$ is trivial, i.e., for every $A\in\mathcal I$, $\mathbb P(A)\in\{0,1\}$. 

   If $\phi$ is not ergodic, the space can be split into two sets $A$ and $A^c$, each having positive measure. So $\phi(A)=A$ and $\phi(A^c)=A^c$. In words, $\phi$ is not irreducible. In this sense, ergodicity is a generalization of irreducibility.

   > [!NOTE]
   >
   > **Theorem Kolmogorov's 0-1 law** If $X_i$ i.i.d., $A\in\mathcal T:=\cap_{n=1}^\infty \sigma(X_n,X_{n+1},...)$, then $\mathbb P(A)=0,1$.
   >
   > **Theorem Levy's 0-1 law** If $\mathcal F_n$ is a filtration, $A\in\mathcal F_\infty$, then $\lim_{n\rightarrow\infty} \mathbb P(A|\mathcal F_n)=1_A$ a.s..

   **Example i.i.d. sequence** (From PTE) If $\Omega=\mathbb R^\mathbb N$, $\phi$ is the shift operator, then an invariant set $A$ has $\{omega:\omega\in A\}=\{\omega:\phi\omega \in A \}\in \sigma(X_1,...)$, so $A\in\cap_{n=1}^\infty\sigma(X_n,X_{n+1},...)=\mathcal T$, the tail $\sigma$-alg. By Kolmogorov's 0-1 law, $\mathbb P(A)=0\ or\ 1$.

   **Example Markov chains ** (From PTE) Suppose the state space $S$ is countable and stationary distribution has $\pi(x)>0\ \forall x\in S$, when all states are recurrent. Then we can write $S=\cup R_i$, where $R_i$ are disjoint irreducible closed sets. If $X_0\in R_i$, then $X_n\in R_i$ a.s., so $\{\omega: X_0(\omega)\in R_i\}\in\mathcal I$. This indicates not irreducible $\Rightarrow$ not ergodic.

   On the other hand, if $A\in\mathcal I$, then $1_A\circ \theta_n=1_A$, where $\theta$ is shift operator. So if let $\mathcal F_n=\sigma(X_0,...,X_n)$, 
   $$
   \mathbb E_\pi(1_A|\mathcal F_n)=\mathbb E_\pi (1_A\circ\theta_n|\mathcal F_n)=\mathbb E_{X_n}1_A
   $$
   by strong Markov property. Now $LHS\rightarrow 1_A$ by Levy's 0-1 law. Meanwhile, when $X_n$ is irreducible, for any $y\in S$, $RHS=\mathbb E_y1_A$ i.o., so actually $\mathbb P_\pi (A)=0\ or\ 1$. So irreducible $\Rightarrow$ ergodic.

   Notice $\mathcal I$, the invariant sets and $\mathcal T$, the tail events, aren't always the same, for example, when the chain is periodic. 

   **Example** $\mathbb S=\{z\in\mathbb C: |z|=1\}$ with $\sigma$-algebra of uniform measure. Given $\theta\in\mathbb R$, $R_\theta (z)=ze^{i\theta\pi}$ is measure preserving.

   For $z\in\mathbb S$, $O_z:=\{R_\theta^n(z): n\geq 0\}$ orbit of $z$. 

   When $\theta\in\mathbb Q$, $O_z$ is finite, hence for all $\epsilon>0$, $A_\epsilon:=\cup_{0\leq\alpha<\epsilon}O_{e^{i\alpha}}$ is invariant. We can pick $\epsilon$ small enough s.t. $A_\epsilon\neq \mathbb S$, so $\mathcal I$ is nontrivial.

   When $\theta\notin \mathbb Q$, $O_z$ is dense, so any open interval interacts $O_z$, so $\mathcal I$ is trivial.

   ***Another proof from PTE*** consider on $[0,1)$, take $A\in \mathcal I$, and use Fourier expansion: $1_A=\sum_k c_k e^{i2\pi kx}$ in $L^2$​ convergence. Since the coefficient is unique, 
   $$
   1_A\circ R_\theta=\sum_k (c_ke^{2\pi ik\theta})e^{2\pi ikx}
   $$
   when $\theta$ is rational, only finite terms of $c_k$ need to be 0; otherwise every term should be 0, which indicates $1_A=0$ a.e.

   Usually, ergodic system get arbitrary close to any point in the state space. (i.e., the orbits are dense.)

   **Theorem Ergodic theorem** If $\varphi$ is measure preserving, and $X\in L^1(\mathbb P)$, then 
   $$
   \frac{1}{n}\sum_{k=0}^{n-1}X(\varphi^k\omega)\rightarrow\mathbb E[X|\mathcal I]
   $$
   a.s. and in $ L^1$.

   In particular, the limit is just constant $\mathbb EX$ if $\mathcal I$ is trivial.

   We rely on the following propositions.

   **Proposition Maximal inequality for positive operators** Let $U:L^1\rightarrow L^1$ be the positive operator, and let $F_N:=\max\{f_n,1\leq n\leq N\}$, where $f_n=\sum_{k=0}^{n-1} U^k f$, then $\int_{F_N>0}fd\mathbb P\geq 0$.

   We will apply this proposition to $U_\varphi$, where $U_\varphi f(\omega)=f(\varphi(\omega))$. Obviously $U\geq 0$ and $\int |Uf|d\mathbb P=\int|f(\varphi(\omega))|d\mathbb P=\int |f(\omega)|d\mathbb P$, so $\|U\|=1$.

   <font color='red'>_proof of Maximal Inequality for positive operators_</font> 

   For $0\leq n\leq N$, we have $UF_N^++f\geq Uf_n+f=f_{n+1}$. Since this hold for those $n$, $UF_N^++f\geq \max_{1\leq k\leq N}\{f_k\}=F_N$ So on $\{F_N>0\}$, $UF_N^++f\geq F_N^+$, and since $U$ is positive $UF_N^+\geq 0$, we have 
   $$
   \int_{F_N>0}fd\mathbb P\geq \int_{F_N>0}F_N^+-UF_N^+d\mathbb P\geq \int F_N^+-UF_N^+d\mathbb P=\|F_N^+\|_1-\|UF_N^+\|_1\geq 0
   $$
   <font color='red'>_proof of Ergodic theorem_</font> 

   First we prove convergence a.s.

   Assume WLOG that $\mathbb E [X|\mathcal I]=0$. Let $S_n=\sum_{k=0}^{n-1} X(\phi^k \omega)$, we want to prove $\frac{1}{n} S_n\rightarrow 0$.

   Let $\epsilon>0$ , $\bar X=\limsup_{n\rightarrow\infty}\frac{S_n}{n}$, and $D_\epsilon=\{\bar X>\epsilon\}$. Since $\bar X(\phi\omega)=\bar X(\omega)$, $D_\epsilon\in\mathcal I$. 

   Introduce $X^*=(X-\epsilon)1_{D_\epsilon}$, then $S_n^*=\sum_{k=0}^{n-1} X^*(\phi^k)$, $M_k^*=\max\{0,S_1^*,...,S_n^*\}$, $F_n=\{M_n^*>0\}$, $F=\cup F_n$. Then $\frac{S_n^*}{n}=(\frac{S_n}{n}-\epsilon)1_{D_\epsilon}$ and $F=\{\sup_{n} \frac{S_n^*}{n}>0\}$, so actually $F$ is just $D_\epsilon$.

   Apply the proposition for $f=X^*$, we have $\int_{F_n}X^*d\mathbb P\geq 0$. Take n to infinity, we have $\int_{D_\epsilon} X^* d\mathbb P\geq 0$.

   It follows that $0\leq \int_{D_\epsilon} X^*d\mathbb P=\int_{D_\epsilon}Xd\mathbb P-\epsilon\mathbb P(D_\epsilon)$. But $\int_{D_\epsilon} Xd\mathbb P=\mathbb E[\mathbb E[X|\mathbb I];D_\epsilon]=0$, so $\mathbb P(D_\epsilon)=0$. That is, $\bar X<\epsilon$ a.s.. Since $\epsilon$ is arbitrary, $\bar X\leq 0$. The same arguments indicate $\bar X\geq 0$. SO $\bar X=0$ a.s..

   Next we prove convergence in $ L^1$. Pick $\epsilon>0,M>1$
   $$
   \mathbb E|\frac{1}{n}\sum_{k=0}^{n-1}X(\phi^k)|\leq \mathbb E|\frac{1}{n}\sum_{k=0}^{n-1}X(\phi^k)1_{|X(\phi^k)|\leq M}|+\mathbb E|\frac{1}{n}\sum_{k=0}^{n-1}X(\phi^k)1_{|X(\phi^k)|> M}|
   $$
   The first converges to 0 by convergence a.s. and DCT, so take $n_0$ s.t. $\forall n>n_0$ the first term  $\leq\epsilon/2$. For the second term, it $\leq \mathbb E X1_{X\geq M}$. Since $X\in L^1$, we cam take M s.t. it $\leq \epsilon/2$. So $LHS<\epsilon$ for large enough $n$. So it converges in $ L^1$.

   **Example** (from PTE) For i.i.d. sequence, since $\mathcal I$ is trivial, the theorem says $\frac{1}{n}\sum_{m=0}^{n-1} X_m\rightarrow \mathbb E X_0$ a.s. and in $ L^1$. This is just SLLN.

   **Example** (from PTE) For a irreducible Markov chain on a countable state space $X_n$ with stationary distribution $\pi$, let f be a function with $\sum_x |f(x)|\pi(x)\leq\infty$, then since $\mathcal I$ is trivial, $\frac{1}{n} \sum_{m=0}^{n-1} f(X_m)\rightarrow\sum_x f(x)\pi(x)$ a.s. and in $ L^1$.

   **Recurrence**

   We will study the recurrence properties of stationary sequences. The settings are as before.

   Consider random walk on $\mathbb R^d$. let $S_n=X_1+...+X_n$ and $A=\{S_n\neq 0, \forall n\geq 1\}$, $R_n=\#\{S_1,...,S_n\}$. we wonder how often does $S_n$ come back to 0 and how much space does it visit.

   **Theorem** $\frac{R_n}{n}\rightarrow \mathbb E[1_A|\mathcal I]$.

   _Remark_ when $\mathcal I$ is trivial, $\frac{R_n}{n}\rightarrow \mathbb P(A)$.

   <font color='red'>_proof_</font> we have $R_n\geq \sum_{m=1}^n 1_A(\phi^m\omega)$, since $\phi^m\omega\in A$ iff $S_n(\phi^m\omega)\neq 0 \forall k\geq 1$, but $S_n(\phi^m\omega)=S_{n+k}-S_k$, so actually RHS is $|\{m: 1\leq m\leq n, S_l\neq S_m\forall l>m\}|$. 

   Use ergodic theorem, $\liminf_{n\rightarrow\infty} R_n/n\geq \mathbb E(1_A|\mathcal I)$.

   To prove the opposite, Let $A_k=\{S_1\neq 0,...,S_k \neq 0\}$. Then $R_n\leq k+\sum_{m=1}^{n-k} 1_{A_k}(\phi^m\omega)$, since RHS is $k+|\{m:1\leq m\leq n-k, S_l\neq S_m \forall m\leq l\leq m+k \}|$.

   Use ergodic theorem, $\limsup_{n\rightarrow\infty}R_n/n\leq \mathbb E(1_{A_k}|\mathcal I)$. Since as $k\uparrow\infty$, $A_k\downarrow A$, MCT for conditional expectation gives $\mathbb E(1_{A_k}|\mathcal I)\downarrow \mathbb E(1_A|\mathcal I)$. The proof is complete.

   **Theorem** Let $(X_i)$ be a stationary sequence taking values in $Z$ and $X_i\in L^1$. Let $A=\{S_1\neq 0, S_2\neq 0,... \}$.

   (i) If $\mathbb E(X_1|\mathcal I)=0$ then $\mathbb P(A)=0$. 

   (ii) if $\mathbb P(A)=0$, then $\mathbb P(S_n=0 i.o.)=1$. 

   (mean zero implies recurrence.)

   <font color='red'>_proof_</font> (i) If $\mathbb E(X_1|\mathcal I)=0$ then the ergodic theorem implies $S_n/n\rightarrow 0$ a.s..

   Now for any $K$, 
   $$
   \limsup_{n\rightarrow\infty}(\max_{1\leq k\leq n}|S_k|/n)=\limsup_{n\rightarrow\infty}(\max_{K\leq k\leq n}|S_k|/n)\leq (\max_{k\geq K}|S_k|/k)
   $$
   Since as $K\uparrow\infty$, $RHS\downarrow 0$, we have $\lim_{n\rightarrow\infty}\max_{1\leq k\leq n}|S_k|/n=0$.

   Since $X_n\in \mathbb Z$, $R_n\leq 1+2\max_{1\leq k\leq n}|S_k|$, so $R_n/n\rightarrow 0$. a.s., so $\mathbb E[1_A|\mathcal I]=0$, so $\mathbb P(A)=0$.

   (ii) Let $F_j=\{S_i\neq 0\ \forall 1\leq i<j, S_j=0 \}$ and $G_{j,k}=\{S_{j+i}-S_j\neq 0\ \forall 1\leq i<k, S_{j+k}-S_j=0 \}$. Notice $F_k$ are disjoint and since $\mathbb P(A)=0$, $\sum \mathbb P(F_k)=1$. Moreover, stationarity implies $\mathbb P(G_{j,k})=\mathbb P(F_k)$, and for fixed $j$, $G_{j,k}$ are disjoint, so actually $\cup_k G_{j,k}=\Omega$ a.s..

   It follows that $\sum_k \mathbb P(F_j\cap G_{j,k})=\mathbb P(F_j)$ and $\sum_{j,k} \mathbb P(F_j\cap G_{j,k})=1$. Notice $F_j\cap G_{j,k}$implies $S_j=S_{j+k}=0$, i.e., $\mathbb P(S_n=0 \text{ for at least 2 times})=1$. 

   Introduce $G_{j,k_1,...,k_l}$ in the similar fashion, we can conclude $\mathbb P(S_n=0\text{ for at least }l\text{ times})=1$, so the proof is complete.

   **Theorem** (From PTE) If $(X_i)$ is a stationary sequence, $A\in\mathcal S$, $\mathbb P(X_n\in A \text{ at least once})=1$, then under $\mathbb P(\cdot |X_0\in A)$, $t_n=T_n-T_{n-1}$ is a stationary sequence with $\mathbb E(T_1|X_0\in A)=1/\mathbb P(X_0\in A)$.  $T_n$ is $n$th visit time to $A$.

   _Remark_ For a Markov chain defined on countable state space with a stationary distribution, we pick $A=\{x\}$, the theorem just says $\mathbb E_xT_x=1/\pi (x)$. This theorem drops Markov assumption and extend it to an arbitrary set $A$.

   <font color='red'>_proof_</font> (i) $t_i$ is stationary under the conditional measure: Actually it suffices to show $\mathbb P(t_1=m,t_2=n|X_0\in A)=\mathbb P(t_2=m,t_3=n|X_0\in A)$, then use similar argument for  any finite-dim case.

   Our first step is to extend $(X_n)_{n\geq 0}$ to $(X_n)_{n\in\mathbb Z}$ using shift operator. Then let $C_k=\{X_{-1}\notin A,...,X_{-k+1}\notin A, X_{-k}\in A\}$, we have $(\cup_{k=1}^K C_k)^c=\{X_k\notin A\ \forall -K\leq k\leq -1 \}$, and $\mathbb P(RHS)=\mathbb P(X_k\notin A\forall 1\leq k\leq K)$. Let $K\rightarrow\infty$, since $X_n$ must visit $A$ a.s., the prob. at right hand tends to 0, so $\mathbb P(\cup_{k=1}^\infty C_k)=1$. And 
   $$
   \mathbb P(t_2=m,t_3=n, X_0\in A)=\sum_{l=1}^\infty \mathbb P(X_0\in A, t_1=l, t_2=m, t_3=n)
   \\=\sum_{l=1}^\infty \mathbb P(C_l,X_0\in A, t_1=m, t_2=n)=\mathbb P(X_0\in A, t_1=m, t_2=n)
   $$
   i.e., move visit time (0,l,l+m,l+m+n) to (-l,0,m,m+n).

   (ii) compute
   $$
   \mathbb E(t_1|X_0\in A)=\sum_{k=1}^\infty\mathbb P(t_1\geq k|X_0\in A)=\mathbb P(X_0\in A)^{-1}\sum_{k=1}^\infty \mathbb P(t_1\geq k,X_0\in A)
   \\=\mathbb P(X_0\in A)^{-1}\sum_{k=1}^\infty \mathbb P(C_k)=1/\mathbb P(X_0\in A)
   $$
   **Example Random permutations and integer partitions** Let $n\in \mathbb N^*$, a partition of $n$ is a nonincreasing sequence $(\lambda_1,...,\lambda_l)$ s.t. $\sum \lambda_i=n$. In this case, we say $\lambda$ partitions $n$ and has length $l$. This can be represented by a Young diagram. A Young tableau is a filling of Young diagram by number $1,2,...,n$ s.t. rows and columns increase. Let $f_\lambda$ be the number of Young tableau with shape $\lambda$, i.e., ways to fill in Young diagram. 
   
   > [!NOTE]
   >
   > **Robinson–Schensted correspondence** $S_n\leftrightarrow \{(P,Q):\text{P and Q are two standard Young tableau with same shape}\}$.
   >
   > To explain this, we introduce RSK algorithm for inserting a number into a Young tableau:
   >
   > Suppose S is a Young tableau, to insert $x$ into $S$, operate as follows:
   >
   > 1. start from the first row.
   > 2. In the current row, find the minimal $y$ which is larger than $x$.
   > 3. If found, replace $y$ by $x$, and insert $y$ to the next row.
   > 4. If not found, place $x$ to the end of this row and exit.
   >
   > It's easy to examine this algorithm preserves a Young tableau.
   >
   > Moreover, if we create another tableau simultaneously by filling n at the place where a new box is created, then this also gives a Young tableau, since we only add boxes at the end of a row. 
   >
   > For a permutation $\sigma\in S_n$, we say $\sigma(1)\sigma(2)...\sigma(n)$ is a word. Insert this word into a Young tableau by RSK algorithm, we have P the insertion and Q the recording. So $S_n\rightarrow (P,Q)$ is well-defined. Meanwhile, this procedure can be reversed. So the map is a bijection. 
   
   The **Plancherel measure** is the pushforward of the uniform measure on $S_n$ to the set of partitions of n, given by $\mathbb P(\lambda)=\frac{1}{Z} f_\lambda^2$, with $Z=\sum_{\lambda \text{ partitions of n }} f_\lambda^2=|S_n|=n!$ by the bijection. 