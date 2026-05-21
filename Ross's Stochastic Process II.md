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