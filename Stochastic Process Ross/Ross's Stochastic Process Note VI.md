## Chapter 7 Random Walks

**Definition** Let $X_i\in L^1$ i.i.d., and $S_0=0,S_n=\sum_{i=1}^{n} X_i$. The process $S_n$ is called a **random walk**. If $P(X_i=1)=1-P(X_i=-1)=p$, we call it **simple random walk**.

### 7.1 Duality in random walks

> [!important]
>
> **Duality Principle** $(X_1,...,X_n)=_d (X_n,...,X_1)$. 

This is immediate since $X_i$ are i.i.d.. We will illustrate this by some propositions.

**Proposition 7.1.1** If $EX>0$, let $N=\min\{n: S_n>0 \}$, we have $EN<\infty$.

<font color='red'>_proof of Proposition 7.1.1_</font>
$$
\begin{aligned}
EN&=\sum_{n=0}^\infty P(N>n)\\&=\sum_{n=0}^\infty P(X_1\le 0, X_1+X_2\le 0,...,X_1+...+X_n\le 0)\\&=\sum_{n=0}^\infty P(X_n\le 0,X_n+X_{n-1}\le 0,...,X_n+...+X_1\le 0)\\&=\sum_{n=0}^\infty P(S_n\le S_{n-1},S_n\le S_{n-2},...,S_n\le 0)
\end{aligned}
$$
So now we consider the event $S_n\le S_{n-1},S_n\le S_{n-2},...,S_n\le 0$, i.e., $S_n$ hits the lowest.  Conditioned on the last hitting lowest, the time until next hitting lowest is the hitting time of $(-\infty,0]$ for a new RW $\tilde S_n=_d S_n$. So the hitting lowest can be a renewal.

So 
$$
EN=\sum_{n=0}^\infty P(\text{renewal occurs at time }n)=1+E\text{\#renewals}
$$
By SLLN, $S_n\to+\infty$ a.s., so #renewals is finite a.s.. But for a renewal process with interarrival time distribution $F$, either $F(\infty)=1$ and #renewals$=\infty$, or $F(\infty)<1$ and #renewals$\sim G(1-F(\infty))$, with $E\#\text{renewals}<\infty$. So $EN<\infty$.

**Proposition 7.1.2** Let $R_n=|\{S_1,...,S_n \}|$. Then $\lim_{n \to \infty} \frac{ER_n}{n}=P(S_n\ne 0\forall n>0)$.

<font color='red'>_proof of Proposition 7.1.2_</font> Let $1_k=1_{S_k\ne S_j,\forall j<k}$, i.e., the RW visits a new position, and $T$ be the returning time to $0$.
$$
\begin{aligned}
R_n&=1+\sum_{k=1}^{n} 1_k\\
ER_n&=1+\sum_{k=1}^{n} P(1_k=1)\\
&=1+\sum_{k=1}^{n} P(S_k\ne S_{k-1},...,S_k\ne S_1,S_k\ne 0)\\
&=1+\sum_{k=1}^{n} P(X_k\ne 0, X_k+X_{k-1}\ne 0,..., X_k+...+X_1\ne 0)\\
&=1+\sum_{k=1}^{n} P(S_1\ne 0,..., S_n\ne 0)\\
&=\sum_{k=0}^{n} P(T>k)\\
\frac{ER_n}{n}&=\frac{\sum_{k=0}^{n} P(T>k)}{n}\to_\text{Stolz}P(T=\infty)
\end{aligned}
$$
and $T=\infty$ is exactly the event that $S_n\ne 0\forall n>0$.

**Example 7.1(A) SRW** 

- Let $p=1/2$, then the RW is recurrent and thus $P(S_n\ne 0\forall n>0)=0$. So $ER_n/n\to 0$.

- Let $p>1/2$, let $\alpha=P(S_n=0\exists n>0\mid X_1=1)$, and by **Theorem 7.1.1** $P(S_n=0\exists n>0\mid X_1=-1)=1$. 

  - So conditioned on $S_1$, $P(S_n=0\exists n>0)=\alpha p+1-p$. 

  - Meanwhile, conditioned on $X_2$, Since 
    $$
    P(S_n=0\exists n>0\mid S_2=2)=P(S_n=1\exists n>2\mid S_2=2)P(S_n=0\exists n>k\mid S_k=1)=\alpha^2
    $$
    Conditioned on $X_2$, we have $\alpha=\alpha^2 p+1-p$.

  - Since $\alpha<1$ by transience, $\alpha=(1-p)/p$ and $P(S_n\ne 0\forall n>0)=2p-1$. This gives $ER_n/n\to 2p-1$.

**Proposition 7.1.3** If $S_n$ is SRW, Let $Y_k$ be the  number of visits to state $k$ before returning to $0$ . Then $EY_k=1\forall k$.

<font color='red'>_proof of Proposition 7.1.3_</font> Suppose $k>0$
$$
\begin{aligned}
EY_k&=\sum_{n=1}^\infty P(S_n=k,S_1,...,S_{k-1}\ne 0)
\\&=\sum_{n=1}^\infty P(S_n=k,S_1,...,S_{k-1}>0)
\\&=\sum_{n=1}^\infty P(X_n>0,X_n+X_{n-1}>0,...,X_n+...+X_2>0,S_n=k)
\\&=\sum_{n=1}^\infty P(S_n=k,S_n>S_{n-1},...,S_n>S_1)
\\&=\sum_{n=1}^\infty P(n \text{ is the first time to visit }k)
\\&=P(S_n=k\exists n)
\end{aligned}
$$
Since $S_n$ is recurrent, $EY_k=1$.

##### Application to G/G/1 queueing model

**Definition** A $G/G/1$ queueing model is a single-server model where customers arrive as a renewal process with interarrival distribution $F$ and service distribution $G$. 

**Proposition 7.1.4** Let interarrival times be $X_i$, service times be $Y_i$, and the waiting time for $n$th customer be $D_n$. Then for $c>0$, $P(D_{n+1}\ge c)=P(S_k>c\exists k\le n)$, i.e., $S_i$ crosses $c$ by time $n$, where $S_j=\sum_{i=1}^{j} Y_i-X_{i+1}$.

<font color='red'>_proof of Proposition 7.1.4_</font> In this case, every customer spends $D_n+Y_n$. Then $D_{n+1}= \begin{cases} D_n + Y_n - X_{n+1} & \text{if } D_n + Y_n \ge X_{n+1} \\ 0 & \text{if } D_n + Y_n < X_{n+1}, \end{cases}$. Let $U_n=Y_n-X_{n+1}$, we have $D_{n+1}=\max\{0,D_n+U_n \}$. One can iterate this, and finally we have $D_{n+1}=\max\{0,U_n,U_n+U_{n-1},...,U_n+...+U_1 \}=_d \max\{0,S_1,...,S_n \}$.

_Remark_ Notice $D_{n}$ is nondecreasing, so is $P(D_n\ge c)$, so $\lim_{n \to \infty} P(D_n\ge c)$ exists, say $P(D_\infty \ge c)$, and $P(D_\infty\ge c)=P(S_j\text{ ever crosses }c)$. So if $EU=EY-EX>0$, by SLLN we know $P(D_\infty\ge c)=1$. This is true when $EU=0$. Only when $EU<0$ can $D_\infty$ not degenerate. 

**Proposition 7.1.5 Spltzer's identity** Let $M_n=\max(0,S_1,...,S_n)$, we have $EM_n=\sum_{k=1}^{n} \frac{1}{k} ES_k^+$.

<font color='red'>_proof of Proposition 7.1.5_</font> 

First, split by whether $S_n>0$, we have 
$$
M_n=1_{S_n>0}M_n+1_{S_n\le 0} M_n
$$
For the first term,
$$
1_{S_n>0}M_n=1_{S_n>0}\max(S_1,...,S_n)=1_{S_n>0} X_1+1_{S_n>0}\max(S_1-X_1,...,S_n-X_1)
$$
Since $(X_1,...,X_n)=_d(X_n,X_1,...,X_{n-1})$, we have 
$$
E1_{S_n>0}M_n=E1_{S_n>0}X_1+E1_{S_n>0}\max(S_1-X_1,...,S_n-X_1)=E1_{S_n>0}X_1+E1_{S_n>0}M_{n-1}
$$
Also, since $(X_i,S_n)$ has the same distribution for all $i$, we have
$$
E[S_n1_{S_n>0}]=nEX_11_{S_n>0}\Rightarrow EX_11_{S_n>0}=\frac{1}{n}ES_n^+
$$
So we can get
$$
EM_n1_{S_n>0}=EM_{n-1}1_{S_n>0}+\frac{1}{n}ES_n^+
$$
For the second term, when $S_n<0$, $M_n=M_{n-1}$, whence
$$
EM_n=EM_{n-1}1_{S_n>0}+\frac{1}{n} ES_n^++EM_{n-1}1_{S_n<0}=EM_{n-1}+\frac{1}{n} ES_n^+
$$
iterate this and we reach the conclusion.

_Application on G/G/1 queue model_ $ED_{n+1}=EM_n=\sum_{k=1}^{n} \frac{1}{k}ES_k^+$.

### 7.2 Some remarks concerning exchangeable random variables

For duality principle, it's sufficient to assume $X_i$ are **exchangeable**, i.e., for any $\sigma\in S_n$, $(X_i)_{i=1}^n=_d (X_{\sigma(i)})_{i=1}^n$. For infinite r.v.'s, they are **exchangeable** iff all finite subsets of r.v.'s are.

**Example 7.2(A)** Suppose balls are randomly selected without replacement from a urn consisting of $n$ balls of which $k$ are white. If we let $X_i=1_\text{ith selection is white}$, we will find $X_1,...,X_n$ are exchangeable but not independent.

As an application, we have 

**Proposition 7.2.1** If $f$ and $g$ are both increasing, then $cov(f(X),g(X))\ge 0$.

<font color='red'>_proof of Proposition 7.2.1_</font> First for $X_1,X_2$ exchangeable, we have 
$$
(f(x_1)-f(x_2))(g(x_1)-g(x_2))\ge 0\forall x_1,x_2\Rightarrow E[(f(X_1)-f(X_2))(g(X_1)-g(X_2))]\ge 0
$$
By exchangeability, $Ef(X_1)g(X_1)=Ef(X_2)g(X_2)$ and $Ef(X_1)g(X_2)=Ef(X_2)g(X_1)$. Now pick $X_1,X_2$ i.i.d., we can reach the conclusion.

**Example 7.2(B)** Let $\Lambda\sim G$, and conditioned that $\Lambda=\lambda$, $X_i$ are i.i.d. $\sim F_\lambda$. Then they are exchangeable since $P(X_1\le x_1,...,X_n\le x_n)=\int \prod_{i=1}^{n} F_\lambda(x_i)dG(\lambda)$, but not independent.

interestingly, this example has an inverse.

**Theorem 7.2.2 De Finetti's theorem** If $X_i\in\{0,1\}$ are exchangeable, then there is a distribution $G$ on $[0,1]$ s.t. $\forall 0\le k\le n$, $P(S_n=k)=\int_0^1 \lambda^k(1-\lambda)^{n-k} dG(\lambda)$, i.e., there is $\Lambda\sim G$, and conditioned that $\Lambda=\lambda$, $X_i$ are i.i.d. $\sim B(1,\lambda)$.

### 7.3 Using martingales to analyze random walks

**Theorem 7.3.1** Suppose $X_i\in \mathbb Z\cap [-M,M],M<\infty$. Then $S_n$ is recurrent Markov chain iff $EX=0$.

<font color='red'>_proof of Theorem 7.3.1_</font> when $EX\ne 0$, $S_n$ must be transient. So it suffices to show $EX=0$ indicates recurrence. Notice when $EX=0$, $S_n$ is a martingale. 

Suppose $S_0=i,i\ge 0$. Let $A=\{-M,...,-1 \}$ and $A_j=\{j,j+1,...,j+M \},j>0$. Let $N=\min\{n: S_n\in A\cup A_j\}$, then $N$ is a stopping time, so $ES_N=ES_0=i$. But 
$$
ES_N=E[S_N\mid S_N\in A]P(S_N\in A)+E[S_N\mid S_N\in A_j]P(S_N\in A_j)\ge -MP(S_N\in A)+j(1-P(S_N\in A))
$$
i.e., 
$$
P(S_N\in A)\ge \frac {j-i}{j+M}
$$
so $P(S_n\in A\exists n)\ge P(S_N\in A)\ge\frac{j-i}{j+M}$. Since $j$ is arbitrary, push $j\to\infty$, we have $P(S_n\in A\exists n)=1$. Similarly let $B=\{1,2,...,M\}$, then for $S_0<0$, $P(S_n\in B\exists n)=1$. Together we have $P(S_n\in A\cup B\exists n)=1$ for any $S_0$. This have shown that $S_n$ is recurrent.

_Remark_ This argument is canonical. First, we should unearth martingale lying under the process and use optional stopping theorem. Second, we should define appropriate stopping time, for instance, in above theorem, if we define $N=\min\{n:S_n\in A \}$, it may be a random time. But if we define $N=\min\{n: S_n\in A\cup A_j \}$, $N<\infty$ a.s., then we can push $j\to\infty$ to remove another boundary.

_Remark_ Since by Wald's equation $ES_N=EXEN$, we know $EN=\infty$ and the chain is null recurrent.

**Example** Suppose $EX\ne 0$. Fix $A,B>0$, we wonder $P_A=P(S_n\ge A\text{ before }\le -B)$.

> [!Note]
>
> To be rigorous, we must prove the following:
>
> **Proposition** If $EX\ne0$ or $EX=0$ and $X$ isn't degenerated, then for $A,B>0$, let $N=\min\{n: S_n\ge A\text { or }S_n\le -B \}$, then $N<\infty$ a.s..
>
> _proof_ If $EX>0$, then $\exists\epsilon,P(X\ge\epsilon)>0$. Also, if $EX=0$ and $X$ is not degenerated, $\exists \epsilon,P(X\ge\epsilon)>0$. Then pick $k$ s.t. $k\epsilon>A+B$. Now if $S_0\in [-B,A]$, the probability of escaping is at least $p^k$. So we have
> $$
> P(N>mk)\le (1-p^k)^m
> $$
> which indicates
> $$
> EN=\sum_{n\ge 0} P(N>n)\le k\sum_{m\ge 0}P(N>mk)\le k\sum_{n\ge 0}(1-p^k)^m<\infty
> $$
> So $N<\infty$ a.s.. The same holds for $EX<0$.

The technique is also to construct a martingale. Suppose we can find $\theta$ s.t. $Ee^{\theta X}=1$. Then $Z_n:=e^{\theta S_n}$ is a martingale. Consider the stopping time $N:=\min\{n: S_n\le -B\text{ or }S_n\ge A \}$. By optional stopping theorem, $Ee^{\theta S_N}=1$. So
$$
1=E[e^{\theta S_N}\mid S_N\ge A]P_A+E[e^{\theta S_N}\mid S_N\le -B](1-P_A)\approx e^{\theta A}P_A+e^{-\theta B}(1-P_A)
$$
whence $P_A=\frac{1-e^{-\theta B}}{e^{\theta A}-e^{-\theta B}}$. From this, $ES_N\approx AP_A-B(1-P_A)$. by Wald's equation one can get $EN$.

**Example 7.3(A) The Gambler's ruin problem** In this case, $P(X_i=1)=1-P(X_i=-1)=p$. When $A,B$ are integers, $\approx$ can be replaced by $=$. Pick $\theta =\ln q/p$, $Z_n:=e^{\theta S_n}$ is a martingale and $P_A=\frac{(q/p)^B-1}{(q/p)^{A+B}-1}$, $EN=\frac{AP_A-B(1-P_A)}{2p-1}$.

Suppose $EX<0$. For $P(S_n\ge A\exists n)$, notice $1\ge e^{\theta A}P_A\Rightarrow P_A\le e^{-\theta A}$, since $B$ is arbitrary, push $B\to\infty$ and we can get $P(S_n\ge A\exists n)\le (p/q)^A$.

### 7.4 Applications to G/G/1 queues and ruin problems

#### 7.4.1 The G/G/1 queue

**Theorem 7.4.1** If $EU<0$, $P(D_\infty\ge A)\le e^{-\theta A}$ where $Ee^{\theta U}$. 

<font color='red'>_proof of Theorem 7.4.1_</font> We have shown $P(D_\infty\ge A)=P(S_n\ge A\exists n)$ where $S_n=\sum_{i=1}^{n} U_i$. This follows directly from above discussion.

In addition, when $Y_i\sim Exp(\mu)$, we can get the exact result. Consider 
$$
1=E[e^{\theta S_N}\mid S_N\ge A]P(S_n\ge A\text{ before }\le -B)+E[e^{\theta S_N}\mid S_N\le -B]P(S_n\le -B\text{ before }\ge A)
$$
Notice 
$$
\begin{aligned}
E[e^{\theta S_N}\mid S_N\ge A]&=E[E[e^{\theta S_n}\mid S_n\ge A,N=n, Y_n-S_n=c]\mid S_N\ge A]
\\&=E[E[e^{\theta (Y_n-c)}\mid Y_n\ge A+c,N=n,Y_n-S_n=c]\mid S_N\ge A]
\\&=E[E[e^{\theta (A+\tilde Y)}\mid N=n,Y_n-S_n=c]\mid S_N\ge A]
\\&=E[e^{\theta(A+\tilde Y)}]=\frac{\mu}{\mu-\theta}e^{\theta A}
\end{aligned}
$$
where $\tilde Y\sim Exp(\mu)$ is independent of anything else. The key is the memoryless property of exponential distribution. 

Push $B\to\infty$, we have $1=\frac{\mu}{\mu-\theta} e^{\theta A}P(S_n\ge A\exists n)$, so $P(D_\infty\ge A)=\frac{\mu-\theta}{\mu}e^{-\theta A}$, and $P(D_\infty=0)=\theta/\mu$.

#### 7.4.2 A ruin problem

_Setting_ Consider an insurance company receives money at rate $c$ per unit time and receive claims according to a renewal process with interarrival times $X_i$ whose values are $Y_i$ independent of $X_i$. Consider $p=P(A+ct-\sum_{i=1}^{N(t)} Y_i<0\exists t>0)$, i.e., the probability that the company go bankrupt. When $EY\ge cEX$, the company must be bankrupt (consider the corresponding reward process). So we assume $EY<cEX$.

Since the bankrupt will happen immediately some claim occurs, we can write $p=P(A+c\sum_{i=1}^{n} X_i-\sum_{i=1}^{n} Y_i<0\exists n)$. Then the problem becomes: pick $U_i=Y_i-cX_i$ with $EU_i<0$, $S_n=\sum_{i=1}^{n} U_i$, we wonder $p=P(S_n>A\exists n>0)=P(D_\infty>A)$, where $D_\infty$ is the limiting delay in a G/G/1 queue with interarrival times $cX_i$ and service times $Y_i$. We have 

**Theorem 7.4.2** 

(i) $p(A)\le e^{-\theta A}$ where $Ee^{\theta (Y-cX)}=1$

(ii) If $Y_i\sim Exp(\mu)$, $p(A)=\frac{\mu-\theta}{\mu}e^{-\theta A}$

(iii) If $X_i\sim Exp(\lambda)$, $p(0)=\lambda EY/c$.

<font color='red'>_proof of Theorem 7.4.2_</font> (i) and (ii) can be proved as in **Theorem 7.4.1**. 

For (iii), we can consider a M/G/1 queue with arrival rate $\lambda/c$ and service time $Y_i$. Then $p(0)$ is just the limiting probability that a new customer finds the queue nonempty. Since the arrivals $\sim P_\lambda (t)$, it's also the limiting probability that the system is nonempty. We have shown this is $\lambda/c\times EY$.

***

7.3 For SRW compute the expected number of visits to state $k$.

_Solution_ Denote the number of visits to state $0$ by $N$. We have 
$$
EN=\sum_{n=0}^\infty p_{00}^{2n}=\sum_{n=0}^\infty\binom{2n}{n}p^n(1-p)^n
$$
By Stirling formula, $\binom{2n}{n}p^n(1-p)^n\sim \frac{[4p(1-p)]^n}{\sqrt{\pi n}}$. 

- When $p=1/2$, the chain is null-recurrent since $EN=\infty$ and there is no stationary distribution.
- When $p\ne 1/2$, the chain is transient since $EN<\infty$. 

If $p>1/2$, since $S_n\to\infty$ a.s., for $k\ge 0$, the chain visits $k$ a.s., so the expected visit times are all $EN$. For $k<0$, since the chain visit $k$ with probability $p_k<1$, the expected visit times are $p_k EN$.

To get $p_k$, notice $Z_n:=(q/p)^{S_n}$ is a martingale, let $N=\min\{ n: S_n=k\text{ or }M \}$ where $M>0$, $N$ is a stopping time, so by optional stopping theorem, 
$$
1=EZ_0=EZ_N=(q/p)^k P(S_N=k)+(q/p)^M P(S_N=M)
$$
Since $q/p<1$, push $M\to\infty$ then we have $P(S_n=k\exists n)=(p/q)^k<1$.

