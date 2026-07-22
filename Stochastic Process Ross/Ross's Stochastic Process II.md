## Chapter 3 Renewal Theory

### 3.1 Introduction and Preliminaries

Renewal process is the result of generalizing the i.i.d. exponential waiting time of Poisson process to i.i.d. waiting time with arbitrary distribution.

**Definition** Let $X_i$ i.i.d. nonnegative with distribution $F$ (suppose $P(X_i=0)<1$), which shall be interpreted as interarrival times. Let $S_n=\sum_{i=1}^{n} X_i$ be the time of $n$th occurrence. Let $N(t)=\sup \{n:S_n\le t \}$ be the counting process. Then $N(t)$ is called **renewal process**.

_Remark_ (i) $\mu:=EX_i\in (0,\infty]$ by assumptions. (ii) $N(t)<\infty\forall t$, since by SLLN we have $S_n/n\to \mu>0$ a.s., so $S_n<t$ can only occur finite times.

### 3.2 Distribution of $N(t)$.

Denote the $n$-fold convolution of $F$ by $F_n$.

To attain the distribution of $N(t)$, notice $N(t)\ge n\Leftrightarrow S_n\le t$, so $P(N(t)=n)=P(N(t)\ge n)-P(N(t)\ge n-1)=F_n(t)-F_{n-1}(t)$.

Let $m(t)=E[N(t)]$. $m(t)$ is called **renewal function**, much of renewal theory is concerned with determining its properties.

**Proposition 3.2.1** $m(t)=\sum_{n=1}^\infty F_n(t)$.

<font color='red'>_proof of Proposition 3.2.1_</font> Let $1_n$ be the indicator function of $S_n\in [0,t]$, then $N(t)=\sum_{n=1}^\infty 1_n$. So we have by Fubini theorem,
$$
m(t)=E[N(t)]=E\sum_{n=1}^\infty 1_n=\sum_{n=1}^\infty E1_n=\sum_{n=1}^\infty F_n(t)
$$
**Proposition 3.2.2** $m(t)<\infty\ \forall 0\le t<\infty$.

<font color='red'>_proof of Proposition 3.2.2_</font> Pick $\alpha$ s.t. $P(X_i\ge \alpha)>0$, and truncate $X_i$ to $\bar{X_i}=\alpha 1_{X_n\ge \alpha}$. Since $X_i\ge \bar{X_i}$, $N(t)\le \bar{N}(t)$.

Now the process runs as follows: The renewal only happens at $t=n\alpha$, and at this point it behaves as a geometry law with successful probability $P(X_i\ge \alpha)$. As it succeeds, it jumps to the next time point $(n+1)\alpha$. Since geometry distribution has finite expectation $1/P(X_n\ge \alpha)$, and on $[0,t]$ there is at most $[t/\alpha]$ timestamps, so $E\bar{N}(t)<\infty$. So $EN(t)<\infty$. Moreover, its $r$ moment, $EN(t)^r<\infty\ \forall t>0,r>0$.

### 3.3 Some limit theorems

Since $m(t)=EN(t)<\infty\ \forall t$, we have $N(t)<\infty$ a.s.. As for $N(\infty)$, we notice 
$$
P(N(\infty)<\infty)=P(X_n=\infty\exists n)=P(\bigcup_{n=1}^\infty\{X_n=\infty\})\le \sum_{n=1}^\infty P(X_n=\infty)=0
$$
We are interested in the rate at which $N(t)$ goes to infinity. Intuitively, $N(t)/t\to 1/\mu$, if we interpret $N(t)/t$ as the "frequency" and $\mu$ as the "period". In this sense, $1/\mu$ is called **rate** of the renewal process. To make it precise, consider $S_{N(t)}$ to be the last occurrence by time $t$, and $S_{N(t)+1}$ to be the first occurrence after $t$. Intuitionally , $t-S_{N(t)},S_{N(t)+1}-t$ will not affect the limit. Now we prove this formally,

**Proposition 3.3.1 SLLN for renewal process** w.p.1, $N(t)/t\to 1/\mu$, as $t\rightarrow\infty$.

<font color='red'>_proof of Proposition 3.3.1_</font> We have $\frac{S_{N(t)}}{N(t)}\le \frac{t}{N(t)}\le \frac{S_{N(t)+1}}{N(t)}$. Since $N(t)\to\infty$ a.s., (i) $S_{N(t)}/N(t)\to \mu$ a.s. by SLLN (ii) $(N(t)+1)/N(t)\to 1$ a.s.. This indicates $t/N(t)\to\mu$ a.s..

**Example 3.3(A)** Suppose there are infinite coins, each of which has own probability $p$ of landing heads, where $p\sim U(0,1)$ independently. Suppose we are flipping coins sequentially, at any time either flipping a new coin or one that had previously used. Find a strategy to maximize the long-run proportion of heads.

_Solution_ Our strategy is as follows: flip a coin until it turns out a tail, then pick a new coin and abandon the used. Now we prove the proportion tends to 1.

Let $N(n)$ denote the number of tails at first $n$ flips. The long-run proportion is just $\lim_{n \to \infty} \frac{n-N(n)}{n}$. Now it suffices to show $N(n)/n\to 0$.

Notice $N(n)$ is indeed a renewal process, with $X_i\sim G(1-p)$ conditioned on $p$. So 
$$
EX_i=E[E[X_i\mid p]]=\int_0^1 \frac{1}{1-p}dp=\infty
$$
which indicates $N(n)/n\to 0$ a.s..

However, we cannot derive $m(t)/t\to\infty$, since Fatou's Lemma is an inequality. This is indeed true, and we will prove later.

#### 3.3.1 Wald's Equation

Let $X_i$ be a sequence of i.i.d. r.v.'s.

**Definition** An $Z_{\ge 0}$-valued r.v. $N$ is said to be a **stopping time** for the sequence of $X_1,X_2,...$ if the event $\{N=n \}$ is independent of $X_{n+1},...$, i.e., it's determined only by the knowledge before $n$. We can interpret $N$ as the number observed before stopping, and when observed $X_1,...,X_n$, we can know whether to stop at $n$.

**Example 3.3(B)** Suppose $X_n$ i.i.d. $\sim B(1,1/2)$. Let $N=\min\{n: \sum_{i=1}^{n} X_i=10\}$, $N$ is a stopping time. We can consider this as keeping flipping a fair cion until $10$ heads.

**Example 3.3(C)** Suppose $X_n$ i.i.d. with $P(X_n=\pm 1)=1/2$, and $N=\min\{n: \sum_{i=1}^{n} X_i=1 \}$. then $N$ is a stopping time. We can consider this as a stopping time for a gambler who on each play is equally likely to win or lose 1 unit and who decides to stop the first time he is ahead.

**Theorem 3.3.2 Wald's equation** Let $X_i$ be i.i.d. with $EX_i<\infty$, $N$ is a stopping time w.r.t. $X_i$ and $EN<\infty$. Then $E[\sum_{ i=1}^{N}X_i]=ENEX_i$.

<font color='red'>_proof of Theorem 3.3.2_</font> Let $1_n=1_{N\ge n}$, we have $\sum_{n=1}^{N} X_n=\sum_{n=1}^\infty X_n1_n$. Notice $\{N\ge n\}$ is determined by $X_1,...,X_{n-1}$ ,since it happens iff $N\ne i$ for $1\le i\le n-1$. This implies $X_n$ and $1_n$ are independent. (in contrast, $\{N=n\}$ is determined by $X_1,...,X_n$) So we can compute
$$
E[\sum_{i=1}^{N} X_i]=E[\sum_{n=1}^\infty X_n1_n]=_{\text{Fubini}}\sum_{n=1}^\infty E[X_n1_n]=\sum_{n=1}^\infty EX_n E1_n=EX_i\sum_{n=1}^\infty E1_n=EX_iEN
$$

#### 3.3.2 Back to renewal theory

**Theorem 3.3.4 The elementary renewal theorem** $m(t)/t\to 1/\mu$ as $t\rightarrow\infty$.

<font color='red'>_proof of Theorem 3.3.4_</font> 

- Consider the stopping time $N(t)+1$, the first arrival after $t$. This is a stopping time, since $N(t)+1=n\Leftrightarrow X_1+...+X_{n-1}\le t, X_1+...+X_n\ge t$ which can be determined by $\sigma(X_1,...,X_n)$. So by Wald's equation, $E[S_{N(t)+1}]=\mu(m(t)+1)$.
- Suppose $\mu<\infty$. Since $S_{N(t)+1}>t$, we have $\mu(m(t)+1))>t$, i.e., $\liminf_{t\rightarrow\infty} m(t)/t\ge1/\mu$.
- For the other direction, truncate $X_n$ by letting $\bar{X}_n=X_n\wedge M$, and run a new renewal process with $\bar{X_n}$. $\bar{S_n},\bar{N}(t)$ is defined in the same way. Now we can control $\bar{S}_{N(t)+1}\le t+M$, and take expectation $\bar{\mu}(\bar{m}(t)+1)\le t+M$. So we have $\limsup_{t\rightarrow\infty} \bar{m}(t)/t\le 1/\bar{\mu}$. Since $N(t)\le \bar{N}(t)$, $m(t)\le \bar{m}(t)$, i.e., $\limsup_{t\rightarrow\infty} m(t)/t\le 1/\bar{\mu}$. Since $M$ is arbitrary, let $M\to\infty$, $RHS=1/\mu$.
- As for $\mu=\infty$, $1/\bar{\mu}\to 0$.

**Theorem 3.3.5 CLT for renewal process** Suppose $EX_i=\mu$ and $var X_i=\sigma^2$, then $(N(t)-t/\mu)/(\sigma\sqrt{t/\mu^3})\to_d \mathcal N(0,1)$.

_Intuition_ $N(t)\approx t/\mu$, and $S_n\approx n\mu+\sigma\sqrt{n} Z$, where $Z\sim \mathcal N(0,1)$. So $t\approx N(t)\mu+\sigma\sqrt{t/\mu}Z$.

<font color='red'>_proof of Theorem 3.3.5_</font> The calculation follows from intuition that we need to convert $N(t)$ to $S_n$ for a more precise estimation:
$$
\begin{aligned}
P(\frac{N(t)-t/\mu}{\sigma\sqrt{t/\mu^3}}<y)&=P(N(t)<r(t))\text{ ,where }r(t)=y\sigma\sqrt{t/\mu^3}+t/\mu
\\&=P(S_{[r(t)]+1}>t)
\\&=P(\frac{S_{[r(t)+1]}-[r(t)+1]\mu}{\sigma\sqrt{[r(t)+1]}}>\frac{t-[r(t)+1]\mu}{\sigma\sqrt{[r(t)+1]}})
\\&\to P(Z>-y)=P(Z<y)
\end{aligned}
$$
by CLT.

_Remark_ The theorem shows $N(t)$ is asymptotically $\mathcal N(t/\mu,t\sigma^2/\mu^3)$.

### 3.4 The key renewal theorem and applications

To state the Blackwell's renewal theorem, we need a notion:

**Definition** A $\mathbb R_+$-valued r.v. $X$ is said to be **lattice** if there exists $d\ge 0$ s.t. $\sum_{n=0}^\infty P(X=nd)=1$, i.e., takes value on a lattice. The largest $d$ having this property is said to be the **period** of $X$. If $X$ is a lattice with distribution $F$, we say $F$ is lattice, too.

**Theorem 3.4.1 Blackwell's Theorem** 

(i) If $F$ is not lattice, then $m(t+a)-m(t)\to a/\mu$ as $t\rightarrow\infty$.

(ii) If $F$ is a lattice with period $d$, then $E[\#\{\text{renewals at }nd\}]\to d/\mu$.

_Intuition_ (i) When $F$ is not a lattice, Intuitively $E[N(t+a)-N(t)]$ should tends to a limit, say $g(a)$. $g(a)$ must be increasing and $g(a+b)=g(a)+g(b)$ by definition, so $g(x)=cx$ by Cauchy equation. To identify $c$, let $x_i=m(i)-m(i-1)$, then $\lim_{i \to \infty} x_i=c$. By Stolz theorem, $\sum_{i=1}^{n} x_i/n\to c$. By elementary renewal theorem, $c=1/\mu$.

(ii) When $F$ is lattice, then the limit in (i) doesn't exist since $S_n$ only takes value on $nd$. So we consider renewals on $nd$, and if the limit exists, by elementary renewal theorem and Stolz theorem, it should be $d/\mu$. Moreover, if $X_i>0$, i.e., only one renewal happens at $nd\ \forall n$, we have $\lim_{n \to \infty}P(\text{renewal at }nd)=d/\mu$.

To state the key renewal theorem, we need a notion:

**Definition** Let $h:\mathbb R_+\to \mathbb R$. Denote its Darboux upper and lower sum w.r.t. the segmentation $[na,(n+1)a]\forall n\in Z_+$ by $M_a$ and $M^a$. If $M_a,M^a<\infty$ and $\lim_{a \to 0}aM_a=\lim_{a \to 0}aM^a$, $h$ is called **directly Riemann integrable**. In other words, it has finite total variation.

A useful sufficient condition for $h$ to be directly Riemann integrable is that $h$ is nonnegative, nonincreasing and integrable on $\mathbb R_+$.

**Theorem Key renewal theorem** Suppose $F$ is not lattice, $h$ is directly Riemann integrable, then $\lim_{t \to \infty} \int_0^t h(t-x)dm(x)=\frac{1}{\mu}\int_0^\infty h(t)dt$. Notice w.r.t. $F$, $m(x)=\sum_{n=1}^\infty F_n(x)$ and $\mu=\int_0^\infty (1-F(t))dt$.

_Remark_ By key renewal theorem, we can compute the limit of $g(t)$, some probability or expectation at time $t$ by first conditioning on the time of last renewal prior to $t$. This can yield an equation of the form 
$$
g(t)=h(t)+\int_0^t h(t-x)dm(x)
$$
_Remark_ We can derive Blackwell's theorem from Key renewal theorem: Let $h(t)=1_{[0,a]}(t)$, when $t$ is large, $g(t)=m(t)-m(t-a)$. By renewal theorem, the limit is $\int_0^\infty h(t)dt/a=\mu/a$.

To illustrate this, we consider $S_{N(t)}$. Its distribution is given by 

**Lemma 3.4.3** $P(S_{N(t)}\le s)=\bar{F}(t)+\int_0^s \bar{F}(t-y)dm(y)$, where $\bar{F}=1-F$.

<font color='red'>_proof of Lemma 3.4.3_</font> 
$$
\begin{aligned}
P(S_{N(t)}\le s)&=\sum_{n=0}^\infty P(S_{N(t)}\le s, N(t)=n)=\sum_{n=0}^\infty P(S_n\le s, S_{n+1}> t)\\&=\bar{F}(t)+\sum_{n=1}^\infty P(S_n\le s, S_{n+1}>t)
\\&=\bar{F}(t)+\sum_{n=1}^\infty \int_0^\infty P(S_n\le s, S_{n+1}>t\mid S_n=y)dF_n(y)
\\&=\bar{F}(t)+\sum_{n=1}^\infty \int_0^s P(S_{n+1}-S_n> t-y)dF_n(y)
\\&=\bar{F}(t)+\int_0^s \bar{F}(t-y)dm(y)
\end{aligned}
$$
_Remark_ $P(S_{N(t)}=0) =\bar{F}(t)$, and $dF_{S_{N(t)}}(y)=\bar{F}(t-y)dm(y)$.

Intuitively, we can argue that $dm(y)=P(\text{renewal occurs in }(y,y+dy))$. So $dF_{S_{N(t)}}(y)=P(\text{renewal in }(y,y+dy),\text{ next arrival}>t-y)=dm(y)\bar{F}(t-y)$.

#### 3.4.1 Alternating renewal processes

_Setting_ Consider a system with two states, on and off. Initially it's on, and remains for $Z_1$, goes off and remains for $Y_1$, and repeat this process. Suppose $(Z_i,Y_i)$ are i.i.d. (So $Z_i$ are i.i.d., so are $Y_i$), but $Z_i$ and $Y_i$ can be dependent. Denote the distribution of $Z_i,Y_i,Z_i+Y_i$ by $H,G,F$, and denote the event is on at $t$ by $A_t$. We have:

**Theorem 3.4.4** If $E[Z_n+Y_n]<\infty$, and $F$ is nonlattice, then $\lim_{t \to \infty} P(A_t)=\frac{EZ_n}{EZ_n+EY_n}$.

<font color='red'>_proof of Theorem 3.4.4_</font> Think of switching on as renewal, and condition on $S_{N(t)}$, 
$$
\begin{aligned}
P(A_t)&=P(A_t\mid S_{N(t)}=0)P(S_{N(t)}=0)+\int_0^\infty P(A_t\mid S_{N(t)}=y)dF_{S_{N(t)}}(y)\\
P(A_t\mid S_{N(t)}=0)&=P(Z_1>t\mid Z_1+Y_1>t)=\bar{H}(t)/\bar{F}(t)\\
P(A_t\mid S_{N(t)}=y)&=P(Z>t-y\mid Z+Y>t-y)=\bar{H}(t-y)/\bar{F}(t-y),y<t\\
\Rightarrow P(A_t)&=\bar{H}(t)+\int_0^t \bar{H}(t-y)dm(y)\\
&\to 0+\frac{\int_0^\infty \bar{H}(t)dt}{\mu}=\frac{EZ}{EZ+EY}
\end{aligned}
$$
_Remark_ Similarly, if the initial state is off, $P(\bar{A}_t)\to EY/(EY+EZ)$. Meanwhile, by the theorem, if the initial state is on, $P(\bar{A}_t)=1-P(A_t)\to EY/(EY+EZ)$. This fact implies the initial state makes no difference in the limit.

_Application_ Consider a renewal process. Let $Y(t)=S_{N(t)+1}-t$ be the **residual life at $t$**, $A(t)=t-S_{N(t)}$ be the **age at $t$**. We can interpret this by thinking of renewal as replacing a failed component. Now we wonder the asymptotic distribution of $A(t)$:

**Proposition 3.4.5** If the interarrival time is nonlattice and $\mu<\infty$, then $\lim_{t \to \infty} P(Y(t)\le x)=\lim_{t \to \infty} P(A(t)\le x)=\mu^{-1}\int_0^x \bar{F}(y)dy$.

<font color='red'>_proof of Proposition 3.4.5_</font> 

The strategy is to build an alternating renewal process. Fix an $x$, We say it's on when $A(t)\le x$, and it's off when $A(t)> x$. Then if $F$ is nonlattice we have by **Theorem 3.4.4**:
$$
\lim_{t \to \infty} P(A(t)\le x)=E[\min (X,x)]/EX=\frac{\int_0^x \bar{F}(y)dy}{\mu}
$$
Similarly, for a renewal process we say it's on when $Y(t)\le x$ and off when $Y(t)>x$. The asymptotic distribution of $Y(t)$ is given by 
$$
\lim_{t \to \infty} P(Y(t)\le x)=E[\min (X,x)]/EX=\frac{\int_0^x \bar{F}(y)dy}{\mu}
$$
_Remark_ $Y(t)$ and $A(t)$ has identical distribution, which is not so surprising. This symmetry has been implied in the proof: imagine we run a two-side renewal process, then in two direction we can see identical renewal process, and age in one direction is residual life in another direction.

_Remark_ $Y(t)$ and $A(t)$ are not independent.

Now we turn to the distribution of the whole lifetime, $Y(t)=S_{N(t)+1}-S_{N(t)}=A(t)+Y(t)$.  First, we have an interesting fact:

**Proposition Inspection paradox** $P(X_{N(t)+1}>x)\ge \bar{F}(x)$.

<font color='red'>_proof_</font> 
$$
\begin{aligned}
P(X_{N(t)+1}>x)&=\sum_{n=0}^\infty P(X_{N(t)+1}>x\mid N(t)=n)P(N(t)=n)
\\&=\sum_{n=0}^\infty P(X_{n+1}>x\mid X_{n+1}>t-S_{n})P(N(t)=n)
\\&=\sum_{n=0}^\infty\frac{P(X_{n+1}>x)}{P(X_{n+1}>t-S_n)}P(N(t)=n)
\\&\ge \sum_{n=0}^\infty P(X>x)P(N(t)=n)=P(X>x)
\end{aligned}
$$
_Remark_ Take expectation, we have $EX_{N(t)+1}\ge \mu$. This is to say, if you are in a renewal process, it's more likely that the renewal interval you are in is longer than an ordinary renewal interval. The reason is that, a longer interval is more likely to fetch some point $t$. 

We can claim, an interval of length $y$ is $y$ times more likely to contain $t$ than an interval of length 1. In this case, denote the density of $X_{N(t)+1}$ by $g$, we have approximately $g(y)dy=d (yF(y)/\mu)$. Actually, this is true.

_Correction_ Ross uses alternating renewal argument, which is incorrect. If we mark the intervals with length $>x$ on and $<x$ off, then whole cycle contains at least 2 renewal intervals. Actually, the distribution of length of "on" and"off" states also change.

**Proposition** $\lim_{t \to \infty} P(X_{N(t)+1}>x)=\int_x^\infty ydF(y)/\mu$.

<font color='red'>_proof_</font> Use the primary renewal equation argument, 
$$
\begin{aligned}
P(X_{N(t)+1}>x)&=P(X_{N(t)+1}>x, S_{N(t)}=0)+\int_0^t P(X_{N(t)+1}>x\mid S_{N(t)}=y)dF_{S_{N(t)}}(y)
\\&=P(X_1>\max\{x,t\})+\int_0^t P(X_i>\max\{x,t-y\}\mid X_i>t-y)\bar{F}(t-y)dm(y)
\\&\to \mu^{-1}\int_0^\infty P(X_i>\max\{x,y\})dy=\mu^{-1} \int_x^\infty ydF(y)
\end{aligned}
$$
**Example 3.4(A)** Suppose customers arrive at a store to buy some kind of commodity. The amount desired by customers are $Y_i$ i.i.d. $\sim G$. The store uses the following $(s,S)$ ordering policy: if the inventory level is below $s$ after serving a customer, an order is placed to bring t up to $S$ immediately. Let $X(t)$ denote the inventory level at time $t$, now we wonder it's asymptotic distribution. Fix $s<x<S$.

- Construct an alternating renewal process. Since we are investigating the asymptotic behavior, WLOG let $X(0)=S$. Set it on when $X(t)\ge x$ and off otherwise. At the beginning and the end of a cycle, $X(t)=S$, so it's a renewal process. So
  $$
  \lim_{t \to \infty}P(X(t)>x)=\frac{E[\text{amount of time the inventory}\ge x\text{ in a cycle}]}{E[\text{ time of a cycle}]}
  $$

- Let $N_x=\min\{n: Y_1+...+Y_n>S-x\}$ to be the first renewal when the inventory falls below $x$.Then $N_s$ is the renewal starting the new cycle. So
  $$
  \lim_{t \to \infty} P(X(t)>x)=\frac{E[\sum_{i=1}^{N_x} Y_i]}{E[\sum_{i=1}^{N_s}Y_i]}=\frac{EN_x}{EN_s}
  $$

- Consider the renewal process $Y_i$. $N_x-1$ is the number of renewals before $S-x$, so $E[N_x-1]=m_G(S-x)$. So 
  $$
  \lim_{t \to \infty}P(X(t)>x)=\frac{m_G(S-x)+1}{m_G(S-s)+1}
  $$

#### 3.4.2 Limiting mean excess and the expansion of $m(t)$

**Proposition 3.4.6** If $F$ is nonlattice, $EX_i^2<\infty$, then $E[Y(t)]\to E[X_i^2]/2\mu$.

<font color='red'>_proof of Proposition 3.4.6_</font> Take expectation for the renewal equation of $Y(t)$, we have 
$$
\begin{aligned}
EY(t)&=E[Y(t)\mid S_{N(t)}=0]\bar{F}(t)+\int_0^t E[Y(t)\mid S_{N(t)}=y]\bar{F}(t-y)dm(y)
\\&=E[X-t\mid X>t]\bar{F}(t)+\int_0^t E[X-(t-y)\mid X>t-y]\bar{F}(t-y)dm(y)
\\E[X-t\mid X>t]&=\int_t^\infty (s-t)dF(s)/\bar{F}(t) 
\\\Rightarrow EY(t)&\to \mu^{-1}\int_0^\infty E[X-t\mid X>t]\bar{F}(t)dt
\\&=\mu^{-1}\int_0^\infty \int_t^\infty (s-t)dF(s)dt=\mu^{-1}\int_0^\infty\int_0^s (s-t)dtdF(s)
\\&=\mu^{-1}\int_0^\infty \frac{s^2}{2}dF(s)=\frac{EX^2}{2\mu}
\end{aligned}
$$
(i) $E[X-t\mid X>t]\bar{F}(t)\to 0$ as $t\to\infty$: By Schwarz inequality
$$
\int_t^\infty (s-t)^2 dF(s)\int_t^\infty dF(s)\ge [\int_t^\infty (s-t)dF(s)]^2
$$
and the second moment is finite.

(ii) $E[X-t\mid X>t]\bar{F}(t)$ is directly Riemann integrable: differentiate it w.r.t. $t$, it's negative.

**Corollary 3.4.7** If $EX^2<\infty$ and $F$ is nonlattice, then $m(t)-t/\mu\to EX^2/1\mu^2-1$.

<font color='red'>_proof of Corollary 3.4.7_</font> Since $S_{N(t)+1}=t+Y(t)$, $ES_{N(t)+1}\to t+EX^2/2\mu$. But $ES_{N(t)+1}=\mu [m(t)+1]$ by Wald's equality. 

#### 3.4.3 Age-dependent branching processes

_Setting_ Suppose that an organism at the end of its life produce random numbers of offspring with law $P(X=j)=p_j$. The lifetime of everyone is i.i.d. $\sim F$, and the number of offspring of everyone is independent of anything else. Denote the alive individuals at $t$ by $X(t)$. $X(t)$ is called **age-dependent branching process**. We are concerning the asymptotic behavior of $M(t):=E[X(t)]$, where we assume $m:=\sum_{j=1}^\infty jp_j>1$.

**Theorem 3.4.8** If $X_0=1,m>1$, and $F$ is nonlattice, then 
$$
e^{-\alpha t}M(t)\to\frac{m-1}{m^2 \alpha EXe^{-\alpha X}},t\to\infty
$$
where $\alpha$ is chosen s.t. $Ee^{-\alpha X}=1/m$.

<font color='red'>_proof of Theorem 3.4.8_</font> By conditioning on $T_1$,
$$
\begin{aligned}
M(t)&=\int_0^\infty E[X(t)\mid T_1=s]dF(s)
\\&=\int_0^t mM(t-s)dF(s)+\int_t^\infty 1dF(s)=\bar{F}(t)+m\int_0^t M(t-s)dF(s)
\end{aligned}
$$
To make this a renewal equation (to absorb m) , introduce $G(s)=m\int_0^s e^{-\alpha y}dF(y)$ which is a distribution, and replace $F$ by $G$ by 
$$
e^{-\alpha t}M(t)=e^{-\alpha t}\bar{F}(t)+\int_0^t e^{-\alpha (t-s)}M(t-s)\ me^{-\alpha s}dF(s)=e^{-\alpha t}\bar{F}(t)+\int_0^t e^{-\alpha (t-s)}M(t-s)dG(s)
$$
Let $f(t)=e^{-\alpha t}M(t)$ and $h(t)=e^{-\alpha t}\bar{F}(t)$, we have $f=h+f*G$.  By induction, $f=h+h*m_G$. $h$ is decreasing and $h(\infty)=0$, so it's Riemann integrable, and by renewal theorem,
$$
f(t)\to \mu_G^{-1}\int_0^\infty h(t)dt=\frac{\int_0^\infty e^{-\alpha t}\bar{F}(t)dt}{\int_0^\infty xdG(x)}=\frac{\alpha^{-1}(1-\int_0^\infty e^{-\alpha t}dF(t))}{\int_0^\infty xme^{-\alpha x}dF(x)}=\frac{1-1/m}{\alpha m EXe^{-\alpha X}}
$$

### 3.5 Delayed Renewal Processes

**Definition** Let $X_i,i\ge 2$ be i.i.d. $\mathbb R_+$-valued, $\sim F$, and $X_1$ be independent of $X_i,i\ge 2$, $\sim G$. Let $S_0=0,S_n=\sum_{i=1}^{n} X_i$, $N_D(t)=\sup\{n: S_n\le t\}$, then $N_D$ is a **delayed renewal process**.

Consider those properties of interest:

-  $P(N_D(t)=n)=P(S_n\le t)-P(S_{n+1}\le t)=G*F_{n-1}-G*F_n$.
- $E[N_D(t)]=\sum_{n=0}^\infty P(S_n\le t)=\sum_{n=1}^\infty G*F_{n-1}(s)$.
- w.p.1., $N_D(t)/t\to 1/\mu$
- $m_D(t)/t\to1/\mu$
- If $F$ is nonlattice, $m_D(t+a)-m_D(t)\to a/\mu$.
- If $F$ and $G$ are lattice with period $d$, $E[\#\text{renewals at }nd]\to d/\mu$.
- If $F$ is nonlattice and $h$ is directly Riemann integrable, then $\int_0^t h(t-x)dm_D(x)\to\mu^{-1} \int_0^\infty h(t)dt$.

**Example 3.5 (A)** Consider $X_i$ i.i.d. are discrete. Call a finite sequence $(x_1,...,x_k)$ a pattern, and say it occur at $n$ if $X_n=x_k,...,X_{n-k+1}=x_1$. Denote the number of occurrence of the pattern by $n$ by $N(n)$. 

Notice $N(n)$ is a delayed renewal process, since the occurrence after the first one can draw support from the former pattern, i.e., $T_1$ is the time for occurrence and $T_i,\ge 2$ are time for repetition, where $T_i$ are interarrival times. It's a ordinary renewal process iff $(x_1,...,x_i)$ and $(x_{n-i+1},...,x_n)$ are different pattern for all $i<n$. If the condition doesn't hold, say the longest such subsequence head-tail.

The rate at which the pattern occurs is given by
$$
\frac{N(n)}{n}\to_{a.s.}\frac{1}{\mu}=\lim_{n \to \infty} E[\#\text{renewals at }n]=\prod_{i=1}^k P(X=x_k)
$$
Now we consider a concrete case. Suppose $P(X_n=1)=p,P(X_n=0)=1-p:=q$, and the pattern is $0101$. Then $ET_i=p^{-2}q^{-2}$. Now we wonder $ET_1$.

Observe the pattern. If the pattern has occurred, to make it occur again, the "helpful" pattern is $01$, which encourages $0101|01$ occurs. So $ET_i$ can be regarded as the mean waiting time from pattern $01$ to $0101$, i.e., $ET_{1,0101}=ET_{1,01}+p^{-2}q^{-2}$. Notice the pattern $01$ induces an ordinary renewal process, so $ET_{1,01}=p^{-1}q^{-1}$ by the above derivation. So $ET_{1,0101}=p^{-1}q^{-1}+p^{-2}q^{-2}$.

From this we can conclude, for a pattern $(x_i)$, if the head-tail is empty, $ET_{1,(x_i)}=ET_{n,(x_i)}=\prod_{i=1}^k P(X=x_i)$. If it's not empty, denote by $(y_k)$, $ET_{1,(x_i)}=ET_{1,(y_k)}+ET_{n,(x_i)}$. And by induction we can get the final result. So
$$
\begin{aligned}
ET_{1,0100100}&=ET_{1,0100}+p^{-2}q^{-5}=ET_{1,0}+p^{-1}q^{-3}+p^{-5}q^{-2}=p^{-1}+p^{-1}q^{-3}+p^{-5}q^{-2}
\\ET_{1,1*n}&=p^{-n}+ET_{1,1*(n-1)}=p^{-n}+...+p^{-1}
\end{aligned}
$$
In this setting, we consider the probability that the pattern $A$ occurs ahead of $B$. For example, $A=1010$ and $B=0100$. Denote $N_{B|A}$ to be the time of occurrence of $B$ starting from the occurrence of $A$, $N_{A}=T_{1,A}$ . 

Notice $EN_{0100|1010}=EN_{0100|010}$. Meanwhile, $EN_{0100}=EN_{010}+EN_{0100|010}$, since $010$ is necessary for $0100$. By calculation, $EN_{0100}=q^{-1}+q^{-3}p^{-1}$, $EN_{010}=q^{-1}+q^{-2}p^{-1}$. So $EN_{B|A}=q^{-3}p^{-1}-q^{-2}p^{-1}$. Also $EN_{A|B}=E[N_A]=p^{-2}q^{-2}+p^{-1}q^{-1}$.

Now let $P_A$ be the probability that $A$ occurs before $B$, let $M=\min\{N_A,N_B\}$, we have 
$$
EN_A=EM+E[N_A-M]=EM+EN_{A|B}(1-P_A)
$$
similarly $EN_B=EM+EN_{B|A}P_A$. By this, we can solve $P_A=[EN_B+EN_{A|B}-EN_A]/[EN_{B|A}+EN_{A|B}]$, and $EM=EN_B-EN_{B|A}P_A$.

when $p=1/2$, we have $EN_A=20,EN_B=18,P_A=9/14,EM=90/7$. Notice although $EN_A>EN_B$, $P_A>1/2$. 

**Example 3.5(B)** _Setting_ Consider this process: A system consists of $n$ independent components, each of which runs a alternating renewal process $(X_n^i,Y_n^i)_{n>0}$, where $X_n^i$ i.i.d.$\sim Exp(\lambda_i)$, $Y_n^i$ i.i.d. $\sim Exp(\mu_i)$, respectively representing on and off. Suppose the system is parallel, say it's functional if at least one of the components are working, nonfunctional if non of them are working. Let $N(t)$ denote the times the system is nonfunctional. 

This process is a delayed renewal process, since it starts from the state that all components are working, and renewal happens when all components break down.

Now we wonder $\mu$. The strategy is to apply Blackwell's theorem. Consider the probability of breakdown in $(t,t+h)$. On each component, the probability of breakdown we have 
$$
\lim_{t \to \infty}P(\text{breakdown at }(t,t+h))=\lim_{t \to \infty} P(\text{on at t})P(\text{last time<}h\mid\text{on at }t)=\frac{\lambda_i}{\lambda_i+\mu_i}(1-e^{-h/\lambda_i})=\frac{h}{\lambda_i+\mu_i}+o(h)
$$
by the memoryless property of exponential distribution.

As for the whole system, when $t\gg h$, in $(t,t+h)$ we only need to consider this case: one will break down, and others have already broken down (since other cases is $o(h)$), i.e., 
$$
\lim_{t \to \infty} P(\text{breakdown at }(t,t+h))=\sum_{i=1}^{n} \frac{1}{\lambda_i+\mu_i}\prod_{j\ne i}\frac{\mu_j}{\lambda_j+\mu_j}\ h+o(h)
$$
By Blackwell's renewal theorem, $\mu=(\prod_{j=1}^n \frac{\mu_i}{\mu_i+\mu_j}\sum_{i=1}^{n} \mu_i^{-1})^{-1}$.

Once the system breaks down, the broken time follows $Exp(\sum_{i=1}^{n} \mu_i^{-1})$. So the mean broken time is $(\sum_{i=1}^{n} \mu_i^{-1})^{-1}$. The mean functional time is the difference of the two mean.

**Example 3.5(c)** Consider two coins, which land on tails with probability $p_1,p_2$ (unknown). Now we construct a strategy to continually flip the coins a.t. the long-run proportion of tails is $\min(p_1,p_2)$.

_Strategy_ Start by flipping coin 1 until a tail occurs, at which point switch to coin 2 and flip it until a tail occurs. Say that cycle 1 ends at this point. Now flip coin 1 until two tails in a row occur, and then switch and do the same with coin 2. Say that cycle 2 ends at this point. In general, when cycle n ends, return to coin 1 and flip it until n + 1 tails in a row occur and then flip coin 2 until this occurs, which ends cycle n + 1.

_proof_ 

- Let $p=\max(p_1,p_2),\alpha p=\min(p_1,p_2)$, where $\alpha<1$. Call the coin with tail probability $p$ the bad coin, $\alpha p$ the good one. In the cycle $m$, let $B_m$ be the flips of bad coin and $G_m$ the flips of good coin. 

- **Lemma** For $\epsilon>0$, $P(B_m\ge \epsilon G_m i.o.)=0$.

  <font color='red'>_proof_</font> 
  $$
  P(G_m\le B_m/\epsilon)=E[P(G_m\le B_m/\epsilon\mid B_m)]=E[\sum_{i=1}^{B_m/\epsilon} P(G_m=i\mid B_m)]\le E[\sum_{i=1}^{B_m/\epsilon}(\alpha p)^m]=\epsilon^{-1} ((\alpha p) ^m EB_m)
  $$
  $P(G_m=i\mid B_m)=P(G_m=i)\le (\alpha p)^m$, since in the $m$th cycle there must be $m$ tails of good coins regardless of any condition.

  Recall **Example 3.5(A)**, $EB_m=\sum_{i=1}^{m} p^{-i}=\frac{(1/p)^m-1}{1-p}$.

  So 
  $$
  \sum_{m=1}^\infty P(G_m\le B_m/\epsilon)=\epsilon^{-1}\sum_{m=1}^\infty \frac{1-p^m}{1-p}\alpha^m<\infty
  $$
  By Borel-Cantelli lemma, $P(B_m\ge \epsilon G_mi.o.)=0$.

- The lemma shows that $B_m/(B_m+G_m)\ge \epsilon/(1+\epsilon)$ can only happens for finitely many times. So the long-run proportion of flips of bad coins is $0$. Now since almost we only use the good coin, by SLLN, the proportion of tails is $\alpha p$.

_Correction_ We don't need to assume which coin is flipped first.



As proved before, $P(S_{N(t)}\le s)=\bar{G}(t)+\int_0^s \bar{F}(t-y)dm_D(y)$, and the limit is $\mu^{-1}\int_0^\infty \bar{F}(y)dy$. The limit distribution of residual life, $F_e(x)=\int_0^x \bar{F}(y)dy/\mu$, is called **equilibrium distribution** of $F$. The delayed distribution with $G=F_e$ is called **equilibrium renewal process**. This process arises naturally: suppose someone starting to observe the renewal process at time $t$. As $t\to\infty$, it's nearly an equilibrium renewal process. This process has some interesting properties, e.g., it has stationary increments, while in general ordinary renewal process doesn't enjoy this property.

**Theorem 3.5.2** For the equilibrium renewal process, 

(i) $m_D(t)=t/\mu$

(ii) $P(Y_D(t)\le x)=F_e(x)$

(iii) $N_D$ has stationary increments.

<font color='red'>_proof of Theorem 3.5.2_</font>

(i) By Laplace transformation $\mathcal L(F)(s)=\int e^{-st}dF(t)$, we have $\mathcal L(m_D)(s)=\sum_{n=1}^\infty \mathcal L(G)(s)\mathcal L(F_{n-1})(s)=\frac{\mathcal L(G)(s)}{1-\mathcal L(F)(s)}$, and $\mathcal L(F_e)(s)=\frac{1-\mathcal L(F)(s)}{\mu s}$. Since $G=F_e$, $\mathcal L(m_D)(s)=(\mu s)^{-1}$, whose inverse is $t/\mu$. By uniqueness, $m_D(t)=t/\mu$.

(ii) Similarly 
$$
P(Y_D(t)>x)=\bar{G}(t+x)+\int_0^t \bar{F}(t+x-s)dm_D(s)
$$
Let $G=F_e$, 
$$
P(Y_D(t)>x)=\bar{F}_e(t+x)+\int_0^t \bar{F}(t+x-s)ds/\mu=\bar{F}_e(t+x)+F_e(t+x)-F_e(x)=1-F_e(x)
$$
(iii) $\forall s,t$, $N_D(t+s)-N_D(s)$ is the process one starts to observe the renewal process at time $t$. By (ii), The distribution of $X_1$ is exactly $F_e$. So $N_D(t+s)-N_D(s)=_d N_D(t)$.

### 3.6 Renewal Reward Process

_Setting_ Consider a renewal process $N(t)$ with interarrival times $X_n$ i.i.d.$\sim F$, and each renewal brings a reward $R_n$, which are i.i.d. but can depend on $X_n$, or formally, $(X_n,R_n)$ are i.i.d.. Let $R(t)=\sum_{i=1}^{N(t)} R_n$ be the total reward earned by time $t$. 

**Theorem 3.6.1** If $ER,EX<\infty$, we have 

(i) w.p.1, $R(t)/t\to ER/EX$

(ii) $ER(t)/t\to ER/EX$.

<font color='red'>_proof of Theorem 3.6.1_</font>

(i) By SLLN and SLLN of renewal process, we have $\frac{R(t)}{t}=\frac{\sum_{i=1}^{N(t)}R_n}{N(t)}\frac{N(t)}{t}\to ER/EX$.

(ii) _Correction_ $N(t)+1$ is not a stopping time for $R_n$. It's a stopping time for $(X_n,R_n)$.

Use Wald's equation, 
$$
ER(t)=E\sum_{i=1}^{N(t)} R_i=E\sum_{i=1}^{N(t)+1} R_i-ER_{N(t)+1}=(m(t)+1)ER-E[R_{N(t)+1}]
$$
So $ER(t)/t=(m(t)+1)/t\ ER-ER_{N(t)+1}/t$. By elementary renewal theorem, $(m(t)+1)/t\to 1/EX$. Now it suffices to show $ER_{N(t)+1}/t\to 0$. 

Notice we cannot assume $ER_{N(t)+1}=ER$ since $R_n$ may depends on $X_n$, and $X_{N(t)+1}$ may be longer than normal (inspection paradox), so they can be different.

Prove this by truncation. For any $A>0$, 
$$
R_{N(t)+1}\le A+R_{N(t)+1}1_{R_{N(t)+1}>A}\Rightarrow ER_{N(t)+1}\le A+ER_{N(t)+1}1_{R_{N(t)+1}>A}
$$
Consider the expectation of $Y=R_n1_{R_n>A}$, we have 
$$
\begin{aligned}
EY_{N(t)+1}&=\sum_{n=1}^\infty EY_n1_{N(t)+1=n}\le \sum_{n=1}^\infty EY_n1_{N(t)+1\ge n}\\&=\sum_{n=1}^\infty EY_nE1_{N(t)+1\ge n}=EY_nEN(t)+1=EY(m(t)+1)
\end{aligned}
$$
The subtle point is, $Y_n$ is independent of $\{N(t)+1\ge n\}$ but maybe not independent of $\{N(t)+1=n\}$.

In this way, 
$$
ER_{N(t)+1}/t\le A/t+EY(m(t)+1)/t\to EY/EX
$$
But since $A$ is arbitrary and $ER<\infty$, $ER_{N(t)+1}/t\to 0$, which completes our proof. 

_Remark_ The "reward" can be given at the end of the cycle or gradually during the cycle. Under both cases the theorem hold, since $\sum_{n=1}^{N(t)}R_n\le R(t)+\sum_{n=1}^{N(t)} R_n+R_{N(t)+1}$.

**Example 3.6(A) Alternating renewal process** Suppose we earn at a rate of one per unit time when the system is on. Then $R(t)$ is the total on time by $t$. By **Theorem 3.6.1**, $R(t)/t\to EX/(EX+EY)$ w.p.1. This is, the long-run probability of the system is on is exactly the long-run proportion of the on time.

**Example 3.6(B) Average age and excess** Let $A(t)$ denote the age at $t$ of a renewal process, now we compute $\lim_{t \to \infty} \int_0^t A(s)ds/t$. Reward the process at rate $A(t)$, we have w.p.1,
$$
\frac{\int_0^t A(s)ds}{t}\to \frac{E\int_0^X sds}{EX}=\frac{EX^2}{2EX}
$$
For $Y(t)$, similarly, reward at rate $Y(t)$, w.p.1,
$$
\frac{\int_0^t Y(s)ds}{t}\to\frac{E\int_0^X (X-t)dt}{EX}=\frac{EX^2}{2EX}
$$
Since $X_{N(t)+1}=A(t)+Y(t)$, 
$$
\frac{\int_0^t X_{N(s)+1}ds}{t}\to \frac{EX^2}{EX}\ge EX
$$
**Example 3.6 (c)** _Setting_ Suppose travelers arrive at a train depot as a renewal process with mean interarrival time $\mu$, and whenever there are $N$ travelers waiting at the depot a train leaves. When there is $n$ travelers, it costs at rate $nc$, and when a train leaves it costs $K$. Now we are interested in the mean cost.

In this setting, we have $E[\text{length of a cycle}]=N\mu$, and $E[\text{cost of a cycle}]=EcX_1+...+(N-1)cX_{N-1}+K=\frac{c\mu N(N-1)}{2}+K$. The ratio is the limit mean cost.

#### 3.6.1 A queueing application

_Setting_ Customers arrive as a renewal process with interarrival time $X_i$. There is only one desktop, and the service time for each customer is $Y_i$ which are i.i.d..$X_i,Y_j$ are independent. Assume $EY<EX<\infty$. Suppose the first customer arrives at time $0$, and let $n(t)$ denote the number of people in the system at $t$. 

Let $L=\lim_{t \to \infty} \int_0^t n(s)ds/t$. To investigate this, we think of the renewal as the beginning of a busy period (notice this truly leads to a renewal process), and reward the process at rate $n(s)$. So 
$$
L=\frac{E[\text{reward during a cycle}]}{E[\text{time of a cycle}]}=\frac{E\int_0^T n(s)ds}{ET}
$$
Let $W_i$ denote the amount of the time the $i$th customer spends in the system (including service time and queueing time), and $W=\lim_{n \to \infty} \sum_{i=1}^{n} W_i/n$. To investigate this, we abandon time and only investigate the number of people in the queue. This is also a renewal process if we think of the state the system is free as a renewal. Reward the process $W_i$ as $i$th people left, we have $W=E[\sum_{i=1}^{N}W_i]/[EN]$ where $N$ denotes the cycle time of the renewal process.

$L$ the average queue length and $W$ the average time cost of everyone has the following interesting relation:

**Theorem 3.6.2** Let $\lambda=1/EX$ denotes the arrival rate, then $L=\lambda W$. 

<font color='red'>_proof of Theorem 3.6.2_</font> 

- Notice $T=\sum_{i=1}^{N} X_i$. Notice $N$ is a stopping time of $(X_i,Y_i)$. So by Wald's equation, $ET=EN/\lambda$.

- $$
  L=\frac{E\int_0^T n(s)ds}{ET}=\lambda\frac{E\int_0^T n(s)ds}{EN}=\lambda W\frac{E[\int_0^T n(s)ds]}{E[\sum_{i=1}^{N} W_i]}
  $$

- Indeed $\int_0^T n(s)ds=\sum_{i=1}^{N} W_i$. One can convince himself by noticing this is two slicing of the same amount.

_Remark_ Indeed, the theorem is true as long as the queueing model restarts itself probabilistically and $ET<\infty$ from our proof. Consider the case of multiple desktop, let the renewal takes place when every desktop is empty. If $EY<kEX$, $ET$ will be finite, and the theorem holds.

### 3.7 Regenerative processes

**Definition** If the s.p. $X_t$ satisfies: $\exists S>0$ a r.v., $X_{t+S}=_d X_t$, then $X_t$ is called **regenerative process**. 

From the definition, the restart time, usually called **regeneration time**, is infinitely many. Denote them by $S_1,...$. Then $S_1,...$ constitutes the time of a renewal process, i.e., $N(t):=\max\{n: S_n\le t\}$ is a renewal process. Denote the interarrival time for the renewal process by $T_i$,we have 

**Theorem 3.7.1** If $X$ is $\mathbb Z_+$-valued, then 
$$
P_j:=\lim_{t \to \infty} P(X(t)=j)=\frac{E[\text{amount of time in state j during a cycle}]}{ET_i}
$$
<font color='red'>_proof of Theorem 3.7.1_</font> Conditioning on the last renewal before $t$,
$$
\begin{aligned}
P(X(t)=j)&=P(X(t)=j\mid S_{N(t)}=0)\bar{F}(t)+\int_0^t P(X(t)=j\mid S_{N(t)}=s)\bar{F}(t-s)dm(s)
\\&=P(X(t)=j, S_1>t)+\int_0^t P(X(t-s)=j,S_1>t-s)dm(s)
\\&\to \int_0^\infty P(X(t)=j,S_1>t)dt/ES_1
\end{aligned}
$$
And $\int_0^\infty P(X(t)=j,S_1>t)dt$ is exactly the amount of time in state $j$ in a cycle.

**Proposition 3.6.2** Under the same setting, 
$$
\lim_{t \to \infty}\frac{\text{amount of time in j by t}}{t}=\frac{E[\text{time in j during a cycle}]}{ES_1}
$$
<font color='red'>_proof of Proposition 3.6.2_</font> Reward the process at rate 1 when it is at state $j$. Then this follows directly from **Theorem 3.6.1**.

_Remark_ limit probability=long-time proportion=E time at some state in a cycle /E cycle length

#### 3.7.1 The symmetric random walk and the arc sine laws

_Setting_ Let $Y_i$ i.i.d. with $P(Y_i=\pm 1)=1/2$, and $Z_0=0,Z_n=\sum_{i=1}^{n} Y_i$. The process $Z_n$ is called symmetric random walk process.

$Z_n$ induces a regenerative process $X_n=sgn Z_n$, which regenerates whenever $X_n=0$. 

- Let $u_n=P(Z_{2n}=0)=\binom{2n}{n} 2^{-2n}$. Notice $u_n=\frac{2n-1}{2n}u_{n-1}$.  We can conclude the distribution of the interarrival time by conclusions from ballot's problem,
  $$
  P(Z_1,Z_2,...,Z_{2n-1}\ne 0,Z_{2n}=0)=u_n\frac{n-(n-1)}{n+(n-1)}=\frac{u_n}{2n-1}
  $$
  
- Also we can conclude the probability it doesn't hit $0$ before $2n$,

  **Lemma 3.7.3** $P(Z_1,...,Z_{2n}\ne 0)=u_n$

  <font color='red'>_proof of Lemma 3.7.3_</font> Since $LHS=1-\sum_{i=1}^{n}\frac{u_i}{2n-1}$, by induction it holds.

- By Stirling's formular, $u_n\sim(n\pi)^{-1/2}$. So w.p.1, the SRW returns to 0.

- The distribution of the last visit to 0 by $2n$ is given by 

  **Proposition 3.7.4** For $k< n$, $P(Z_{2k}=0,Z_i\ne0\forall 2k+1\le i\le n)=u_ku_{n-k}$ 

Now we illustrate the SRW by connecting $Z_k,Z_{k+1}$ by straight line, then its path is cts.

**Theorem 3.7.5** Let $E_{k,n}$ denote the event that by time $2n$, SRW is positive for $2k$ time units and negative for $2n-2k$ time units, and $b_{k,n}=P(E_{k,n})$, we have $b_{k,n}=u_ku_{n-k}$.

<font color='red'>_proof of Theorem 3.7.5_</font> Use induction on $n$. 

- When $n=1$, $b_{1,1}=b_{0,1}=1/2$ since it's determined by the first step to move upward or downward. Meanwhile $u_0=1, u_1=1/2$. So for this case it holds.

- Assume $b_{k,m}=u_ku_{m-k}$ holds for all $k\le m<n$. 

  - First we prove $b_{n,n}=u_n$. Conditioning on the first visit to 0, we have 
    $$
    \begin{aligned}
    b_{n,n}&=\frac{1}{2}\sum_{r=1}^{n} b_{n-r,n-r}P(T=2r)+\frac{1}{2}P(T>2n)
    \\&=\frac{1}{2}\sum_{r=1}^{n} u_{n-r}P(T=2r)+\frac{1}{2}P(T>2n)\text{ induction hypothesis} 
    \\&=\frac{1}{2}\sum_{r=1}^{n} P(Z_{2n-2r}=0)P(T=2r)+\frac{1}{2}P(T>2n)
    \\&=\frac{1}{2}\sum_{r=1}^{n} P(Z_{2n}=0\mid T=2r)P(T=2r)+\frac{1}{2}P(T>2n)\text{ (restart) }
    \\&=\frac{1}{2}P(Z_{2n}=0)+\frac{1}{2}P(T>2n) \text{ since }T<2n
    \\&=u_n
    \end{aligned}
    $$

  - Next we consider common $k$, we have 
    $$
    \begin{aligned}
    b_{k,n}&=\sum_{r=1}^{n} P(E_{k,n}\mid T=2r)P(T=2r)
    \\&=\sum_{r=1}^{n} b_{k-r,n-r}\frac{1}{2}P(T=2r)+\sum_{r=1}^{n} b_{k,n-r}\frac{1}{2} P(T=2r)
    \\&=\sum_{r=1}^{n} u_{k-r}u_{n-k}\frac{1}{2}P(T=2r)+\sum_{r=1}^{n} u_ku_{n-r-k}\frac{1}{2} P(T=2r)
    \\&=u_{n-k}\frac{1}{2} u_k+u_k\frac{1}{2} u_{n-k}=u_ku_{n-k}\text{ from the last case}
    \end{aligned}
    $$
    With the invalid index implying corresponding item is 0.

- In this case it's true for $m=n$. So the theorem holds for all $k\le n$.

By **Theorem 3.7.5**. If we denote $R_n$ to be the time units when it's positive, we have $P(R_n=2k)=u_ku_{n-k}\sim \frac{1}{\pi\sqrt{k(n-k)}}$, which is called the discrete arc sine distribution. So 
$$
P(\frac{R_n}{2n}\le x)\approx \frac{1}{\pi}\int_0^{nx}\frac{1}{\sqrt{y(n-y)}}dy=\frac{1}{\pi}\int_0^x \frac{1}{\sqrt{w(1-w)}}dw=\frac{2}{\pi }\arcsin \sqrt{x}
$$
For instance, $P(R_n/2n\le 1/2)\approx 2/\pi \arcsin \sqrt{2}/2=1/2$.

_Remark_ $R_n/2n$ doesn't converge to some constant, e.g., $1/2$, as we expected. An interesting fact is that, notice that $u_n\to 0$ and that SRW is symmetric implies $P(X_n=1)\to 1/2$, but the  proportion $R_n/2n$ doesn't converge to some constant. The reason is that $ET=\infty$, since 
$$
ET\ge\sum_{n=1}^\infty P(T\ge 2n)=\sum_{n=1}^\infty u_n
$$
where $u_n=O(n^{-1/2})$.

_Remark_ **Proposition 3.7.4** says $P(\text{no zeros between }2nx\text{ and }2n)=1-\sum_{k=nx}^n u_ku_{n-k}$, which is approximately $2/\pi\arcsin\sqrt{x}$.

### 3.8 Stationary point process

**Definition** A **stationary point process** is a counting process with stationary increments. One example is equilibrium renewal process.

**Theorem 3.8.1** If $N(t)$ is a nontrivial stationary point process, we have $\lim_{t \to 0} \frac{P(N(t)>0)}{t}:=\lambda>0$.

<font color='red'>_proof of Theorem 3.8.1_</font> Let $f(t)=P(N(t)>0)$. we have 
$$
f(s+t)=P(N(t+s)-N(t)>0\text{ or }N(t)>0)\le f(s)+f(t)
$$
i.e., $f$ is concave, and $f(0)=0$. So $f'(0)$ makes sense.

**Example 3.8(A)** For equilibrium renewal process, $P(N(t)>0)=F_e(t)=\int_0^t \bar{F}(y)dy/\mu$. By L-Hospital rule $\lambda=\mu^{-1}$.

Notice $EN(t+s)=EN(t)+EN(s)$ and is increasing, by Cauchy equation, there is $c$ s.t. $EN(t)=ct$. Generally, 
$$
c=\sum_{n=1}^\infty\frac{nP(N(t)=n)}{t}\ge \sum_{i=1}^{n}\frac{P(N(t)=n)}{t}=\frac{P(N(t)>0)}{t}\to\lambda
$$
When $c=\lambda$ holds? First, let's introduce a notion: A stationary point process is said to be **regular** or **orderly** if $P(N(t)\ge 2)=o(t)$. This implies the probability that two events occur simultaneously with probability 0.

**Theorem Korolyook's theorem** If $N(t)$ is regular, $\lambda=c$.

The proof refers to Ross.

_Remark_ If the increments are independent, it's Poisson process.

***

3.4 $m(t)=F(t)+\int_0^t m(t-x)dF(x)$

<font color='red'>_proof_</font> conditioning on $X_1$, we have 
$$
m(t)=\int_0^t [m(t-x)+1]dF(x)=F(t)+\int_0^t m(t-x)dF(x)
$$
3.5 $m(t)$ uniquely determines $F(t)$.

<font color='red'>_proof_</font> denote Laplace transform $\hat{f}$, we have $\hat{m}(t)=\frac{\hat{F}(t)}{1-\hat{F}(t)}$. By the uniqueness of Laplace transform, $m(t)$ determines $F(t)$.

3.6 Let $N(t)$ be a renewal process, and suppose that conditioning on $N(t)=n$, $S_1,...,S_n$ is distributed as the order statistics of $U_i\sim U(0,t)$. Prove $N(t)$ is a Poisson process.

<font color='red'>_proof_</font> When $s<t$, $E[N(s)\mid N(t)]=N(t)s/t$, so $EN(s)=EN(t)s/t$. This implies $m(t)=ct$ for some $t$. Since $m(t)$ uniquely determines $F$, so $F$ is exponential with rate $1/c$. 

3.7 If $F$ is the uniform distribution on $(0,1)$, then $m(t)=e^t-1$.

<font color='red'>_proof_</font> solve 3.4, $m(t)=t+\int_0^t m(x)dx$, the solution is $m(t)=e^t-1$. 

_Corollary_ If $X_i$ i.i.d. $\sim U(0,1)$, then the expected number of $X$ to sum up until $>t$ is $e^t$.

3.11 (simplified) Let $X_i$ i.i.d., and $P(X_i=2)=P(X_i=4)=P(X=8)=1/3$, $N$ is a stopping time so that $N=n$ when $X_n=2,X_i\ne 2\forall i<n$.

By Wald's equation, $ET=ENEX$. $EX=14/3$ by calculation, and $N\sim G(1/3)$, so $EN=3$ and $ET=14$.

Another derivation is somewhat complicated, but can help us better understand Wald's equation: 
$$
ET=E[E[T\mid N]]=E[E[\sum_{i=1}^{N} X_i\mid N]]=E[(N-1)\frac{4+8}{2}+2]=14
$$
Notice conditioning on the stopping time forces the distribution of $X_i$ to change.

3.15 Let $A(t),Y(t)$ denotes the age and excess,

(a) 
$$
P(Y(t)>x\mid A(t)=s)=P(X>x+s\mid X>s)=\bar{F}(x+s)/\bar{F}(s)
$$
(b) 
$$
P(Y(t)>x\mid A(t+x/2)=s)=\left\{\begin{aligned}&0,&s\le x/2\\&\bar{F}(s+x/2)/\bar{F}(s-x/2),&s>x/2\end{aligned}\right.
$$
(d) 
$$
P(Y(t)>x,A(t)>y)=\int_0^{t-y} P(Y(t)>x\mid S_{N(t)}=s)\bar{F}(t-s)dm(s)=\int_0^{t-y} \frac{\bar{F}(x+t-s)}{\bar{F}(t-s)}\bar{F}(t-s)dm(s)=\int_0^{t-y}\bar{F}(x+t-s)dm(s)
$$
3.16 Consider an interesting renewal process, where the interarrival times has Gamma distribution with parameters $(n,\lambda)$, $n\in\mathbb Z$.

By Proposition 3.4.6, $\lim_{t \to \infty} EY(t)\to EX^2/2EX=(n+1)/2\lambda$.

On the other hand, Gamma distribution is exactly the sum of $n$ exponential distribution. Denote $I(t)$ so that at time $t$, the process is in the $I(t)$th exponential distribution of a cycle, we have 
$$
\lim_{t \to \infty} EY(t)=\lim_{t \to \infty} \sum_{i=1}^{n}E[Y(t)\mid I(t)=i]P(I(t)=i)
$$
Conditioning on $I(t)=i$, $Y(t)$ is the sum of $(n-i)$ complete exponential waiting time intervals and the current exponential interval, by memoryless property, it's the sum of $(n-i+1)$ exponential waiting time intervals. So $E[Y(t)\mid I(t)=i]=\lambda^{-1}(n-i+1)$. And by rewarding the process at rate 1 when $I(t)=i$, we have $\lim_{t \to \infty} P(I(t)=i)=1/n$. Combine these argument, we can get the same result.

3.17 Conditioning on $X_1$, we often get the renewal-type equation, whose form is $g(t)=h(t)+\int_0^t g(t-x)dF(x)$. Its solution is given by $g(t)=h(t)+\int_0^t h(t-x)dm(x)$ by Laplace transform. By key renewal theory, its limit is given by $\lim_{t \to \infty} g(t)=\mu^{-1} \int_0^\infty h(t)dt$ whenever $h$ is directly Riemann integrable.

3.21 Suppose a gambler will win or lose $1$ unit with probability $p$ and $1-p$ respectively in each epoch. He will quit for the first time he wins $k$ consecutive bets. At the moment she quits, find expected winnings $EW$ and expected epoch of wins $EK$. 

<font color='red'>_proof_</font> Let $X_i$ i.i.d. with $P(X_i=1)=p,P(X_i=-1)=1-p$. Let $N$ denote the time when $k$ consecutive wins occur. $N$ is a stopping time, so by Wald's equation,
$$
EW=E\sum_{i=1}^{N} X_i=EX_iEN=(2p-1)EN
$$
Consider this as coin flip, we have $EN=p^{-k}+...+p^{-1}$.

For $EK$, suppose the number of total epochs is $M$, we have $W=2K-N$, so $EK=EN+EW/2=pEN$. 

3.27 For a renewal reward process, we have $\lim_{t \to \infty} E[R_{N(t)+1}]=E[R_1X_1]/EX_1$.

<font color='red'>_proof_</font> Write renewal equation,
$$
\begin{aligned}
E[R_{N(t)+1}]&=\int_0^t E[R_i\mid X_i>t-s] dF_{S_n}(s)
\\&=\int_0^t \int_0^\infty P(R_i>r\mid X_i>t-s)dr\bar{F}(t-s)dm(s)
\\&=\int_0^t\int_0^\infty P(R_i>r,X_i>t-s)drdm(s)
\\&\to\int_0^\infty \int_0^\infty P(R_i>r,X_i>x)drdx/\mu
\end{aligned}
$$
The limit is just $EXR/EX$, since 
$$
\begin{aligned}
\\RHS&=\int_0^\infty\int_0^\infty \int_x^\infty P(R_i>r\mid X_i=y)dF(y)dx/\mu dr
\\&=\int_0^\infty\int_0^\infty\int_0^yP(R_i>r\mid X_i=y)dx/\mu dF(y)dr
\\&=\int_0^\infty\int_0^\infty yP(R_i>r\mid X_i=y)dF(y)dr/\mu
\\&=\int_0^\infty\int_0^\infty P(R_iX_i>r\mid X_i=y)dF(y)dr/\mu
\\&=\int_0^\infty P(X_iR_i>r)dr/\mu=EX_iR_i/\mu
\end{aligned}
$$
3.32 Consider a M/G/1 queue, with arrival rate $\lambda$ and mean service time $\mu_G$, then we have 

(a) The proportion of time the system is busy is $1-\lambda\mu_G$, since as $t$ large, there is approximately $\lambda t$ arrival, with service time $\lambda t\mu_G$ in total.

(b) the expected length of a busy period can be derived by an alternating renewal process: say the busy periods $X_i$ and free periods $Y_i$, we have $\lambda\mu_G=EX/EX+EY$. Since the process is Poisson, $X\sim Exp(\lambda)$, with $EX=1/\lambda$, so $EY=\mu_G/(1-\lambda\mu_G)$.

(c) The expected number of customers served in a busy period can be derived from Wald's equation: $EY=\mu_G EN$, so $EN=1/(1-\lambda\mu_G)$.

