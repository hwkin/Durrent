### 3.6 Poisson Convergence

#### 3.6.1 The Basic Limit Theorem

The first result is sometimes called "weak law of small numbers" or the "law of rare events". These names derive from the fact that the Poisson appears as the limit of a sum of indicators of events that have small probabilities.

**Theorem 3.6.1** For each $n$ let $X_{n,m},1\le m\le n$ be independent r.v. with $P(X_{n,m}=1)=p_{n,m}$, $P(X_{n,m}=0)=1-p_{n,m}$. Suppose (i) $\sum_{m=1}^{n} p_{n,m}\to\lambda\in\mathbb R_+$ and (ii) $\max_{1\le m\le n}p_{n,m}\to0$, then $S_n\to_d P(\lambda)$.

<font color='red'>_First proof of Theorem 3.6.1_</font> Let $\varphi_{n,m}(t)=E\exp(itX_{n,m})=(1-p_{n,m})+p_{n,m}e^{it}$. So we have $E\exp(itS_n)=\prod_{m=1}^n (1+p_{n,m}(e^{it}-1))$. The target ch.f. is $\varphi=\exp(\sum_{m=1}^{n} p_{n,m}(e^{it}-1))$.

Again we use **Lemma 3.4.3**. $|1+p_{n,m}(e^{it}-1)|=|p_{n,m}e^{it}+(1-p_{n,m})1|<1$ since it lies on the line connecting $e^{it}$ and $1$. $|\exp(p_{m,n}(e^{it}-1))|=\exp(p_{m,n}Re(e^{it}-1))\le 1$. So
$$
\bigg|\exp\bigg(\sum_{m=1}^{n}p_{n,m}(e^{it}-1)\bigg)-\prod_{m=1}^n 1+p_{n,m}(e^{it}-1)\bigg|\le\sum_{m=1}^{n}|\exp(p_{n,m}(e^{it}-1))-1-p_{n,m}(e^{it}-1)|\le\sum_{m=1}^{n} p_{n,m}^2|e^{it}-1|^2\le 4\bigg(\max_{1\le m\le n}p_{n,m}\bigg)\sum_{m=1}^{n} p_{n,m}\to 0
$$
**Example 3.6.2** If there is 400 students in a class, then the number of students have their birthday at a fixed day has approximately Poisson: pick $n=400$ and $p_{n,m}=1/365$. then $\sum_{m=1}^{n} p_{n,m}\to 400/365$ and $\max p_{n,m}\to 0$, so $N\sim P(400/365)$. $P(N=0)\approx e^{-400/365}$.

The second proof will provide information about rate of convergence.

**Definition** The total variation distance of two measures on countable set $S$ is defined by $\|\mu-\nu\|\equiv \frac{1}{2}\sum_z |\mu(z)-\nu(z)|=\sup_{A\subset S}|\mu(A)-\nu(A)|$.

**Lemma 3.6.4** (i) the total variation defines a metric on prob. measures on $\mathbb Z$. (ii) $\|\mu_n-\mu\|\to 0$ iff $\mu_n(x)\to\mu(x)\forall z\in \mathbb Z$, equivalently $\mu_n\to_d \mu$.

**Lemma 3.6.5** If $\mu_1\times \mu_2$ denotes the product measure on $\mathbb Z\times\mathbb Z$ that has $\mu_1\times\mu_2(x,y)=\mu_1(x)\mu_2(y)$, then $\|\mu_1\times\mu_2-\nu_1\times\nu_2\|\le \|\mu_1-\nu_1\|+\|\mu_2-\nu_2\|$.

<font color='red'>_proof of Lemma 3.6.5_</font> 
$$
\begin{aligned}
2\|\mu_1\times\mu_2-\nu_1\times\nu_2\|&=\sum_{x,y}|\mu_1(x)\mu_2(y)-\nu_1(x)\nu_2(y)|\\
&\le \sum_{x,y} \left|\mu_1(x)\mu_2(y)-\nu_1(x)\mu_2(y)\right|
 + \sum_{x,y} \left|\nu_1(x)\mu_2(y)-\nu_1(x)\nu_2(y)\right| \\
&= \sum_y \mu_2(y)\sum_x \left|\mu_1(x)-\nu_1(x)\right|
 + \sum_x \nu_1(x)\sum_y \left|\mu_2(y)-\nu_2(y)\right| \\
&= 2\|\mu_1-\nu_1\| + 2\|\mu_2-\nu_2\|.
\end{aligned}
$$
**Lemma 3.6.6** If $\mu_1*\mu_2$ denotes the convolution of $\mu_1$ and $\mu_2$, i.e., $\mu_1*\mu_2(x)=\sum_{y} \mu_1(x-y)\mu_2(y)$, then $\|\mu_1*\mu_2-\nu_1*\nu_2\|\le \|\mu_1\times\mu_2-\nu_1\times\nu_2\|$.

<font color='red'>_proof of Lemma 3.6.6_</font>
$$
\begin{aligned}
2\|\mu_1 * \mu_2 - \nu_1 * \nu_2\|
&= \sum_x \left| \sum_y \mu_1(x-y)\mu_2(y)
- \sum_y \nu_1(x-y)\nu_2(y) \right| \\
&\le \sum_x \sum_y \left| \mu_1(x-y)\mu_2(y)
- \nu_1(x-y)\nu_2(y) \right| \\
&= 2\|\mu_1 \times \mu_2 - \nu_1 \times \nu_2\|.
\end{aligned}
$$
**Lemma 3.6.7** Let $\mu$ be a measure with $\mu(1)=p,\mu(0)=1-p$, and $\nu$ is a Poisson distribution with mean $p$. Then $\|\mu-\nu\|\le p^2$.
$$
2\|\mu-\nu\|=|\mu(0)-\nu(0)|+|\mu(1)-\nu(1)|+\sum_{n\ge 2}\nu(n)=|1-p-e^{-p}|+|p-pe^{-p}|+1-e^{-p}-pe^{-p}=2p(1-e^{-p})\le 2p^2
$$
<font color='red'>_Second proof of Theorem 3.6.1_</font> Let $\mu_{n,m}$ be the law of $X_{n,m}$. Let $\mu_n$ be the law of $S_n$. Let $\nu_{n,m}\sim P(p_{n,m}),\nu_n\sim P(\sum_{m\le n}p_{n,m}:=\lambda_n),\nu\sim P(\lambda)$. Then $\mu_n=\mu_{n,1}*...*\mu_{n,n}$ and $\nu_n=\nu_{n,1}*...*\nu_{n,n}$. So 
$$
\|\mu_n-\nu_n\|=_{3.6.6}\|\mu_{n,1}\times...\times\mu_{n,n}-\nu_{n,1}\times...\times\nu_{n,n}\|\le_{3.6.5} \sum_{m=1}^{n} \|\mu_{n,m}-\nu_{n,m}\|\le_{3.6.7} 2\sum_{m=1}^{n} p_{n,m}^2
$$
Notice RHS goes to 0. Since $\nu_n\to_d\nu$, the result follows.

**Rate of convergence** When $p_{n,m}=1/n$, we have $\sup_A\{\mu_n(A)-\nu_n(A) \}\le 1/n$.

Compare with binomial probabilities $B(n,1/n)$, say $\nu_n$, 
$$
\begin{aligned}
n(\mu_n(0)-\nu_n(0))&=n((1-1/n)^{n}-e^{-1})\to e^{-1}/2
\\n(\mu_n(1)-\nu_n(1))&=n(C_n^1(1/n)(1-1/n)^{n-1}-e^{-1})\to e^{-1}/2
\\n(\mu_n(2)-\nu_n(2))&=n(C_n^2(1/n)^2(1-1/n)^{n-2}-e^{-1}/2!)\to e^{-1}/4
\end{aligned}
$$
For $k\ge 3$, $\mu_n(k)-\nu_n(k)\le 0$. So $\sup_{A\subset\mathbb Z}|\mu_n(A)-\nu_n(A)|\to 5/4en$. This is a sharper upper bound.

#### 3.6.2 Two Examples with Dependence

**Example 3.6.8 Matching** Let $\pi$ be a random permutation of $\{ 1,2,...,n\}$. Let $X_{n,m}=1$ if $\pi(m)=m$ and 0 otherwise. $S_n=\sum_{m=1}^{n} X_{n,m}$ is the number of fixed points. Now let's check $P(S_n=0)$.

Let $A_{n,m}=\{X_{n,m}=1\}$. By inclusion-exclusion formular,
$$
P(\cup_{m=1}^n A_m)=\sum_m P(A_m)-\sum_{l<m} P(A_lA_m)+\sum_{k\le l\le m}P(A_kA_lA_m)-...=\sum_{i=1}^n(-1)^{i-1}\binom{n}{i}\frac{(n-i)!}{n!}=\sum_{i=1}^{n}\frac{(-1)^{i-1}}{i!}
$$
So $P(S_n=0)=\sum_{m=0}^{n} (-1)^m/m!$. We know $P(S_n=0)\to e^{-1}$. The error is 
$$
|P(S_n=0)-e^{-1}|=|\sum_{m=n+1}^{\infty}\frac{(-1)^m}{m!}|\le \frac{1}{(n+1)!}|\sum_{k=0}^\infty(n+2)^{-k}|=\frac{1}{(n+1)!}\frac{n+2}{n+1}
$$
much faster than $1/n$. As for other probabilities, 
$$
P(S_n=k)=\binom{n}{k}\frac{1}{n(n-1)...(n-k+1)}P(S_{n-k}=0)=\frac{1}{k!}P(S_{n-k}=0)\to e^{-1}/k!
$$
So $S_n\to_d P(1)$.

**Example 3.6.9 Occupancy problem** Suppose that $r$ balls are placed at random into $n$ boxes. From the Poisson approximation to the Binomial that if $n\to\infty$ and $r/n\to c$, then the number of balls in a given box will reach $P(c)$. Now we show for the number of empty boxes, $N$,

**Theorem 3.6.10** If $ne^{-r/n}\to\lambda\in\mathbb R_+$, then $N_n\to_d P(\lambda)$.

_Remark_ To see why this holds, by Poisson approximation we know for a given box, it's empty at prob. $e^{-r/n}$ approximately. If we regard the emptiness as independent events, again by Poisson approximation if $ne^{-r/n}\to\lambda$ then $N_n\to_d P(\lambda)$.

<font color='red'>_proof of Theorem 3.6.10_</font> First we have $P(\text{ boxes }i_1,i_2,...,i_k\text{ are empty })=(1-k/n)^r$.

Let $p_m(r,n)$ be the prob. that $r$ balls are put in $n$ boxes with exactly $m$ boxes empty, we have $p_0(r,n)=\sum_{k=0}^n (-1)^k \binom{n}{k} (1-k/n)^r$ by inclusion-exclusion formular, and $p_m(r,n)=\binom{n}{m} (1-m/n)^r p_0(r,n-m)$.

**Lemma** when $ne^{-r/n}\to\lambda$, $\binom{n}{m}(1-m/n)^r\to \lambda^m/m!$

<font color='red'>_proof_</font> One direction <font color='blue'>_Upper Bound_</font>
$$
\binom{n}{m}(1-m/n)^r\le \frac{n^m}{m!}e^{-mr/n}\to\lambda^m/m!
$$
Another direction: First we notice $\binom{n}{m}(1-\frac{m}{n})^r\ge (1-\frac{m}{n})^{m+r}n^m/m!$. 

To estimate this, first $(1-\frac{m}{n})^m\to 1$. Take logarithm for the rest,
$$
\log (n^m(1-\frac{m}{n})^r)= m\log n-r\log (1-\frac{m}{n})\ge m\log n-rm/n-rm^2/n^2
$$
by noticing $\log(1-t)\ge -t-t^2$. Since $ne^{-r/n}\to\lambda$, we have $r=n\log n-n\log \lambda+o(n)$. This indicates $RHS\ge m\log\lambda+o(1)$. So $\liminf_{n\rightarrow\infty} n^m(1-m/n)^r\ge\lambda^m$.

Combine above results we have proven the result.

Return to our proof. From <font color='blue'>_Upper Bound_</font>, we know $p_0$ is dominated by an absolutely summable series $\sum_{m=1}^{\infty}(2\lambda)^m/m!$ when $n$ is sufficiently large. So by DCT, we know $p_0(r,n)\to\sum_{k=0}^\infty(-1)^k\frac{\lambda^k}{k!}=e^{-\lambda}$, and similarly $p_m(r,n)\to \lambda^m/m!\ e^{-\lambda}$. So $N_n\to_d P(\lambda)$.

**Example 3.6.11 Coupon collector's problem** Let $X_1,X_2,...$ be i.i.d. uniform on $\{1,2,...,n\}$, and $T_n=\inf\{m:\{X_1,...,X_m\}=\{1,2,...,n\} \}$, i.e., the first time to collect all kinds of coupons. This problem is equivalent to the previous one, since $T_n\le m$ iff $m$ balls fill up all $n$ boxes. So
$$
P(T_n/n-\log n\le x)=P(T_n\le n\log n+nx)= p_0([n\log n+nx], n)\to \exp(-e^{-x})
$$
Notice $T_n=X_{n,1}+...+X_{n,n}$, where $X_{n,i}$ are independent with $X_{n,i}\sim G(\frac{n-i+1}{n})$. Let  $Y_{n,i}=(X_{n,i}-EX_{n,i})/n$, we have $\sum_{i=1}^{n} EY_{n,i}^2\to\pi^2/6$, but
$$
\sum_{i=1}^{n} E(Y_{n,i}^21_{|Y_{n,i}|\ge\epsilon})\ge EY_{n,n}^21_{|Y_{n,n}|>\epsilon}\ge \epsilon^2 (1-1/n)^{[(1+\epsilon)n]}\to\epsilon^2e^{-(1+\epsilon)}
$$
So the conditions for Lindeberg-Feller doesn't hold.

### 3.7 Poisson Processes

**Theorem 3.7.1** Let $X_{n,m},1\le m\le n$ be independent $\mathbb Z_{\ge 0}$-valued r.v. with $P(X_{n,m}=1)=p_{n,m}$ and $P(X_{n,m}\ge 2)=\epsilon_{n,m}$. If 

(i) $\sum_{m=1}^{n}p_{n,m}\to\lambda>0$

(ii) $\max_{1\le m\le n}p_{n,m}\to 0$

(iii) $\sum_{m=1}^{n} \epsilon_{n,m}\to 0$.

Then $S_n\to_d P(\lambda)$.

<font color='red'>_proof of Theorem 3.7.1_</font> Use weak law of small numbers. Let $X_{n,m}'=1_{X_{n,m}=1}$, then by **Theorem 3.6.1** we have $S_n'\to_d P(\lambda)$. By (iii), $P(X_{n,m}\ne X_{n,m}')=\epsilon_{n,m}$ indicates $P(S_{n,m}\ne S_{n,m}')\le\sum_{m=1}^{n}\epsilon_{n,m}\to 0$. So $S_{n,m}-S_{n,m}'\to_p 0$. 

**Theorem 3.7.2** Let $N(s,t)$ denote the arrival of somewhere during time $(s,t]$.

(i) If $s_1<t_1<s_2<t_2<...<s_k<t_k$, $N(s_i,t_i)$ and $N(s_j,t_j)$ are independent when $i\ne j$. (independent increments)

(ii) $N(s,t)=_d N(0,t-s)$ (stationary increments)

(iii) $P(N(0,h)=1)=\lambda h+o(h)$

(iv) $P(N(0,h)\ge 2)=o(h)$

Then $N(0,t)$ has law $P(\lambda t)$.

<font color='red'>_proof of Theorem 3.7.2_</font> let $X_{n,m}=N((m-1)t/n,mt/n)$, then by **Theorem 3.7.1** it holds.

**Definition** a family of r.v.'s $N_t$ that satisfies 

(i) if $0=t_0<t_1<...<t_n$, then $N(t_k)-N(t_{k-1})$ are independent (independent increments)

(ii) $N(t)-N(s)\sim P(\lambda(t-s))$ (stationary increments)

is called **Poisson process with rate $\lambda$**. 

Another construction is:

**Proposition** Let $\xi_1,\xi_2,...$ i.i.d. $\sim Exp(\lambda)$, $T_n=\xi_1+...+\xi_n$ and $T_0=0$, $N_t=\sup\{n:T_n\le t \}$. Then $N_t$ is a Poisson process.

<font color='red'>_proof_</font> 

(i) $N_t$ is Poisson: First, $T_n$ has density $f_{T_n}(s)=\frac{\lambda^ns^{n-1}}{(n-1)!}e^{-\lambda s}$, so 
$$
P(N_t=n)=P(T_n\le t<T_{n+1})=\int_0^t f_{T_n}(s)P(\xi_{n+1}>t-s)ds=e^{-\lambda t}\frac{(\lambda t)^n}{n!}
$$
(ii) Increments are independent: 

- First we want to show $T_{(N_t+1)}-t$ is independent of $N_t$ and $=_d \xi_1$:
  $$
  \begin{aligned}
  P(T_{n+1}\ge u|N_t=n)&=\frac{P(T_{n+1}\ge u,N_t=n)}{P(N_t=n)}=\frac{P(T_{n+1}\ge u,T_n\le t)}{P(N_t=n)}
  \\&=\frac{\int_0^t f_{T_n}(s)P(\xi_{n+1}>u+s)ds}{P(N_t=n)}=e^{-\lambda(u-t)}
  \end{aligned}
  $$
  
- Next we define $T_1'=T_{N(t)+1}-t$, $T_k'=T_{N(t)+k}-T_{N(t)+k-1}$ for $k\ge 2$. We have seen $T_1'=_d\xi_1$ and is independent of $N(t)$. For $T_k'$, we observe (actually this is trivial)
  $$
  P(N_t=n,T_k'\ge v_k, k=1,...,K)=P(T_n<t, T_{n+1}>t+v_1,\xi_{n+2}\ge v_2,... \xi_{n+K}\ge v_k)=P(T_n<t,T_{n+1}>t+v_1)\prod_{k=2}^K P(\xi_1\ge v_k)=P(N_t=n)\prod_{k=1}^K P(\xi_1\ge v_k)
  $$
  which indicates they are independent and $T_k'=_d\xi_1$.

- This implies $T_1,T_2,...=_d T_1',T_2',...$. So the increments are independent: 

  Consider vector $(N(t_2)-N(t_1),...,N(t_n)-N(t_{n-1}))$. This is $\sigma(T_k',k\ge 1)$ measurable if we set $t=t_1$, so it's independent of $N(t_1)$. By induction on $n$, we know these increments are independent.

_Remark_ That $T_1'$ is independent of $N_t$ results from the "lack of memory" property of $Exp(\lambda)$, i.e., $P(T>t+s|T>t)=P(T>s)$.

**Exercise 3.7.1** If $P(T>0)=1$ and $P(T>t+s|T>t)=P(T>s)$, we have $T\sim Exp(\lambda)$ for some $\lambda$.

<font color='red'>_proof of Exercise 3.7.1_</font> Then $f(t)=P(T>t)$ satisfies $f(0)=1$ and $f(s+t)=f(s)f(t)$. Moreover $f$ is monotonic, so by Cauchy equation $f(t)=\exp(\lambda t)$ for some $\lambda$.

**Exercise 3.7.2** $S\sim Exp(\lambda), T\sim Exp(\mu)$ are independent, then $S\wedge T\sim Exp(\lambda+\mu)$. Moreover, $P(T\ge S)=\lambda/(\lambda+\mu)$.

_Remark_ The proof is direct. To understand this, consider two pieces of radioactive substance with mass $\lambda$ and $\mu$. The number of particles emitted is a Poisson process with rate $\lambda$ and $\mu$. Then $S$, $T$, $S\wedge T$ are the first times of emit of the first, the second, the whole substance. And since the particle is "uniformly" emitted w.r.t. mass, that the first particle is from the first substance has probability $\lambda/(\lambda+\mu)$.

**Exercise 3.7.3** This can be generalized. Suppose $:T_i\sim Exp(\lambda_i)$, then $V=\min\{T_1,...,T_n \}\sim Exp(\sum_{i=1}^{n} \lambda_i)$. Moreover, $I=\arg \min \{ T_i\}$ has law $P(T=i)=\lambda_i/(\sum_{j=1}^{n}\lambda_j)$.

#### 3.7.1 Compound Poisson Processes

Consider $N_t$ a Poisson process and $Y_i$ i.i.d and independent of $N_t$, let $S(t)=\sum_{i=1}^{N(t)} Y_i$.

**Theorem 3.7.3** Suppose for now $N_t$ is just a $Z_{\ge 0}$-valued, then we have

(i) If $E|Y_i|,EN<\infty$, then $ES=ENEY_i$

(ii) If $EY_i^2,EN^2<\infty$, then $var (S)=EN var(Y_i)+var(N) (EY_i)^2$

(iii) If $N\sim P(\lambda)$, $var(S)=\lambda EY_i^2$.

<font color='red'>_proof of Theorem 3.7.3_</font> (i) 
$$
ES=\sum_{n=0}^\infty E(S|N=n)P(N=n)=\sum_{n=0}^\infty nEY_iP(N=n)=ENEY_i
$$
similarly (2) can be calculated. (iii) is a special case.

#### 3.7.2 Thinning

The goal is to use $Y_i$ to split the Poisson process. Let $N_j(t)=\#\{i\le N(t): Y_i=j\}$. We have

**Theorem 3.7.4** $N_j(t)$ are independent rate $\lambda P(Y_i=j)$ Poisson process.

_Remark_ For now we can regard $Y_i$ as tags.

<font color='red'>_proof of Theorem 3.7.4_</font> First we suppose $P(Y_i=1)=p,P(Y_i=2)=1-p$. Consider $N_1(t), N_2(t)$.

From the independent increment property of Poisson process we have $(N_1(t_i)-N_1(t_{i-1}),N_2(t_i)-N_2(t_{i-1}))$ are independent of each other. Moreover, $X_i=N_i(t+s)-N_i(s)$ are independent of each other, since 
$$
P(X_1=j,X_2=k)=e^{-\lambda t}\frac{(\lambda t)^{j+k}}{(j+k)!}\binom{j+k}{j}p^j(1-p)^{n-j}=e^{-\lambda pt}\frac{(\lambda pt)^j}{j!}e^{-\lambda(1-p)t}\frac{(\lambda(1-p)t)^k}{k!}
$$
So they are independent Poisson with rate $\lambda p$ and $\lambda (1-p)$.

For general cases, the proof is identical.

An easy generalization is

**Theorem 3.7.5** Suppose that in a Poisson process with rate $\lambda$ (which may occur everywhere) we keep a point that lands at $s$ with probability $p(s)$ (vary with position $s$). Then the result is a nonhomogeneous Poisson process with rate $\lambda p(s)$ (i.e., every position $s$ has a Poisson process with rate $\lambda p(s)$).

**Example 3.7.6 Poissonization and the occupancy problem** If we put a Poisson number of balls with mean $r$ in $n$ boxes, and $N_i$ denotes the number of balls in box $i$, then we know $N_i$ i.i.d. $\sim P(r/n)$. This technique is called "Poissonization" since if $r$ is fixed, $N_i$'s are not independent, which hold back direct analysis. 

Now we turn to the number of empty boxes. Suppose the the number of total balls has law $P(s)$ where $s=n\log n-n\log\mu$, then each box receives $N_i\sim P(s/n)$ balls which are independent. Then $P(N_i=0)=e^{-s/n}=\mu/n$. So the number of empty boxes has law $B(n,\mu/n)$, and by weak law of small numbers it converges weakly to $P(\mu)$.

Return to a fixed number of balls, where $r=n\log n-n\log \lambda+o(n)$. To transfer the result back, choose $\mu_2<\lambda<\mu_1$, and define $s_i=n\log n-n\log \mu_i$, then $s_1<r<s_2$. 

We have $P(P(s_1)<r<P(s_2))\to 1$: $r-s_i=O(n)$, but $\sigma P(s_i)=O(\sqrt{n\log n})=o(n)$.

Under $P(s_1),P(s_2)$, the law of empty boxes are $P(\mu_1),P(\mu_2)$. Since $\mu_1,\mu_2$ are arbitrary, the law of empty boxes is $P(\lambda)$, when $ne^{-r/n}\to\lambda$. This proved the pervious result again.

**Example 3.7.7 A Poisson process on a measure space $(S,\mathcal S,\mu)$** This process is a random map $m:\mathcal S\to Z_{\ge 0}$ that if $A_i\in\mathcal S$ are disjoint of finite measure, then $m(A_i)$ are independent r.v.'s with law $P(\mu(A_i))$. The measure $\mu$ is called the **mean measure** since $Em(A_i)=\mu(A_i)$. If $S=\mathbb R_+,\mathcal S=\mathcal B, \mu=\text{Lebesgue measure}$, this corresponds to Poisson process where $m$ is mapped from time.

If $\mu(S)<\infty$, we can construct $m$ by this manner: 

- Normalize $\mu$: define $\nu(A)=\mu(A)/\mu(S)$.
- Pick $N\sim P(\mu(S))$, choose $X_i$ i.i.d. with distribution $\nu$, and let $m(A)=\# \{j\le N: X_j \in A \}$, then $m(A)\sim P(\mu(A))$ by **Theorem 3.7.4**.

This can be extended directly to $\sigma$-finite measure spaces.

#### 3.7.3 Conditioning

**Theorem 3.7.9** Let $T_n$ be the time of $n$th arrival in a rate $\lambda$ Poisson process. Let $U_1,...,U_n$ i.i.d. $\sim U(0,t)$, $V_k^n$ denote the kth smallest number in $\{U_1,...,U_n \}$. Conditioning on $N(t)=n$, $(V_1^n,...,V_n^n)=_d (T_1,...,T_n)$.

<font color='red'>_proof of Theorem 3.7.3_</font>
$$
f_{(T_1,...,T_n)|N(t)=n}(t_1,...,t_n) = \frac{(\prod_{m=1}^n \lambda e^{-\lambda(t_m-t_{m-1})}) e^{-\lambda (t-t_n)}}{P(N(t)=n)}=\frac{n!}{t^n}
$$

$$
f_{(V_1^n,...,V_n^n)}(t_1,...,t_n)=n!(1/t)^n
$$

So they have the same law.

By these, we can derive some results.

**Corollary 3.7.10** If $0<s<t$, then $P(N(s)=m|N(t)=n)=\binom{n}{m}(\frac{s}{t})^m (1-\frac{s}{t})^{n-m}$.

<font color='red'>_proof of Corollary 3.7.10_</font> By Theorem 3.7.9,
$$
P(N(s)=m|N(t)=n)=P(T_m\le s<T_{m+1}|N(t)=n)=P(V_m^n\le s<V_{m+1}^n)=P(\text{m less than t and (n-m) greater than t})=\binom{n}{m}(\frac{s}{t})^m(1-\frac{s}{t})^{n-m}
$$
**Theorem 3.7.11** Let $T_n$ be the time of nth arrival in a rate $\lambda$ Poisson process. Let $U_1,U_2,...,U_n$ i.i.d. $\sim U(0,1)$. Let $V_k^n$ be the kth smallest number in $\{U_1,...,U_n \}$. Then $(V_1^n,...,V_n^n)=_d (T_1/T_{n+1},...,T_n/T_{n+1})$.

<font color='red'>_proof of Theorem 3.7.11_</font> Let's change variables where $v_i=t_i/t_{n+1},1\le i\le n$ and $v_{n+1}=t_{n+1}$. Then
$$
\begin{aligned}
f_{T_1/T_{n+1},...,T_n/T_{n+1},T_{n+1}}(v_1,...,v_{n+1})&=f_{T_1,...,T_{n+1}}(t_1,...,t_{n+1})\frac{\partial(t_1,...,t_{n+1})}{\partial(v_1,...,v_{n+1})}
\\f_{T_1,...,T_{n+1}}(t_1,...,t_{n+1})&=\prod_{m=1}^{n+1}\lambda e^{-\lambda(t_m-t_{m-1})}=\lambda^{n+1}e^{-\lambda t_{n+1}}
\\\frac{\partial(t_1,...,t_{n+1})}{\partial(v_1,...,v_{n+1})}&=v_{n+1}^n
\end{aligned}
$$
So $f_{T_1/T_{n+1},...,T_{n+1}}(v_1,...,v_{n+1})=\lambda^{n+1}v_{n+1}^n e^{-\lambda v_{n+1}}$. Integrate w.r.t. $v_{n+1}$, this is just Gamma function and the integration is $n!$, which is desired.

Now we take $\lambda=1$ and letting $V_0^n=0, V_{n+1}^n=1$.

**Exercise 3.7.6** $nV_k^n\to_d T_k$.

<font color='red'>_proof of Exercise 3.7.6_</font> $V_k^n=_d T_k/T_{n+1}$, and $T_{n+1}/n\to 1$ a.s., then use Slutsky's theorem.

**Exercise 3.7.7** $A_n=n^{-1}\sum_{m=1}^{n} 1_{n(V_i^n-V_{i-1}^n)>x}\to e^{-x}$ in prob.

<font color='red'>_proof of Exercise 3.7.7_</font> Let $\Delta_i^n=V_i^n-V_{i-1}^n$, then $\Delta_i^n=_d \xi_i/T_{n+1}$. Since $\xi_i$ are i.i.d. we know $(\Delta_1^n,...,\Delta_{n+1}^n)$ is uniform on simplex $\{(y_1,...,y_{n+1}):y_i>0,y_1+...+y_{n+1}=1 \}$. This gives marginal distribution $P(\Delta_i^n>a)=(1-a)^n$ (This correspond to a copy of simplex scaled by $(1-a)$). Moreover, $P(\Delta_i^n>a,\Delta_j^n>b)=(1-a)^n (\frac{1-a-b}{1-a})^n=(1-a-b)^n$ when $a,b$ is small enough.

Taking $a=x/n$ we have $p_n:=P(n\Delta_i^n>x)=(1-x/n)^n\to e^{-x}$. Meanwhile, for $i\ne j$, $q_n:=P(n\Delta_i^n>x,n\Delta_j^n>x)=(1-2x/n)^n\to e^{-2x}$.

Calculate
$$
\begin{aligned}
EA_n&=P(n\Delta_i^n>x)=(1-\frac{x}{n})^n\to e^{-x}
\\EA_n^2&=\frac{1}{n^2}E\bigg[\sum_{i=1}^{n} 1_{n\Delta_i^n>x}+\sum_{i\ne j}1_{n\Delta_i^n>x,n\Delta_j^n>x} \bigg]=\frac{np_n+n(n-1)q_n}{n^2}
\\var A_n&=\frac{p_n}{n}+\frac{n-1}{n}q_n-p_n^2\to e^{-2x}-(e^{-x})^2=0
\end{aligned}
$$
Under this precise estimation, we know $A_n\to e^{-x}$ by Markov inequality.

**Exercise 3.7.8** $(n/\log n)\max_{1\le m\le n+1}V_m^n-V_{m-1}^n \to 1$ in prob.

<font color='red'>_proof of Exercise 3.7.8_</font> It suffices to show $(n/\log n)\frac{\max_{1\le m\le n+1}\xi_m}{T_{n+1}}\to 1$. By SLLN we have $n/{T_{n+1}}\to 1$ a.s., now we show $(\max_{1\le m\le n+1}\xi_m)/\log n\to 1$ in prob. Actually we show it converges to $1$ weakly:
$$
P(\max_{1\le m\le n} \xi_m/\log n\le x)=\prod_{i=1}^n P(\xi_i\le x\log n)=(1-n^{-x})^{n+1}\to\left\{\begin{aligned} &1&x>1\\&e^{-1}&x=1\\&0&x<1\end{aligned}\right.
$$
Combine these results we know the convergence hold.

**Exercise 3.7.9** $P(n^2\min_{1\le m\le n}V_m^n-V_{m-1}^n>x)\to e^{-x}$.

<font color='red'>_proof of Exercise 3.7.9_</font> It suffices to show $n^2\frac{\min_{1\le m\le n}\xi_m}{T_{n+1}}\to_d Exp(1)$. Since $n/T_{n+1}\to 1$ a.s., we will show $n\min_{1\le m\le n}\xi_i\to_d Exp(1)$. Actually we have
$$
P(n\min_{1\le m\le n+1}\xi_m\ge x)=\prod_{m=1}^{n+1}e^{-x/n}=e^{-x(1+1/n)}\to e^{-x}
$$

### 3.8 Stable Laws

Let $X_1,X_2,...$ be i.i.d.. By **Theorem 3.4.1**, if $EX_i=\mu$, $var(X_i)=\sigma^2>0$ then $(S_n-n\mu)/n^{1/2}\sigma\to_d \mathcal N(0,1)$. Now we turn to investigate the case $EX_1^2=\infty$ and give necessary and sufficient conditions for the existence of constants $a_n$ and $b_n$ so that $(S_n-b_n)/a_n\to_d Y$ where $Y$ is nondegenerate.

**Example** Suppose $X_i$ has law $P(X_1>x)=P(X_1<-x)=x^{-\alpha}/2$ for $x\ge 1$, where $0<\alpha<2$. We have
$$
1-\varphi(t)=\int_1^\infty (1-e^{itx})\frac{\alpha}{2|x|^{\alpha+1}}dx+\int_{-\infty}^{-1}(1-e^{itx})\frac{\alpha}{2|x|^{\alpha+1}}=\alpha\int_1^\infty \frac{1-\cos (tx)}{x^{\alpha+1}}dx=t^\alpha \alpha\int_t^\infty \frac{1-\cos u}{u^{\alpha+1}}du
$$
Notice $\int_0^\infty \frac{1-\cos u}{u^{\alpha+1}}du<\infty$, so we have $1-\varphi(t)\sim C|t|^\alpha$ as $t\to 0$.

By this, we have
$$
E\exp(it S_n/n^{1/\alpha})=\varphi(t/n^{1/\alpha})^n= (1-(1-\varphi(t/n^{1/\alpha})))^n\to \exp(-C|t|^\alpha)
$$
Let $Y$ be a r.v. with ch.f. RHS, we have $S_n/n^{1/\alpha}\to_d Y$.

**Another derivation** If $0<a<b$ and $an^{1/\alpha}>1$, then $P(an^{1/\alpha}<X_1<bn^{1/\alpha})=\frac{1}{2n} (a^{-\alpha}-b^{-\alpha})$. 

Notice we can apply weak law for small numbers: consider $X_{n,m}=X_m/n^{1/\alpha}$, we have $\sum_{m=1}^{n} P(X_{n,m}\in (a,b))=\frac{a^{-\alpha}-b^{-\alpha}}{2}$, and their maximal value converges to 0. So If we denote the number of $X_{n,m}$ that falls into $(a,b)$ by $N_n(a,b)$, we have $N_n(a,b)\to_d N(a,b)$, where $N(a,b)$ has Poisson law with mean $\frac{a^{-\alpha}-b^{-\alpha}}{2}$.

Generalize this result. For $A\subset \mathbb R-(-\delta,\delta)$ where $\delta>1$, we have $P(X_1/n^{1/\alpha}\in A)=\int_{n^{1/\alpha} A}\frac{\alpha}{2|x|^{\alpha+1}}dx=n^{-1}\int_A\frac{\alpha}{2|x|^{\alpha+1}}dx$. Let $N_n(A)$ be the times $X_{n,m}$ visits $A$, $N_n(A)\to_d N(A)$ where $N(A)$ is a Poisson r.v. with mean $\mu(A)=\int_A \frac{\alpha}{2|x|^{\alpha+1}} dx<\infty$.

This limiting family of r.v. $N(A)$ is called a **Poisson process on $\mathbb R$ with mean measure $\mu$**, which we have already seen before. 

Now we turn to $S_n/n^{1/\alpha}$. Let $I_n(\epsilon)=\{m\le n:|X_{n,m}|>\epsilon n^{1/\alpha} \}$ the indices of "big terms", $\hat{S_n}(\epsilon)=\sum_{m\in I_n(\epsilon)} X_{n,m}$ the sum on big terms and $\bar{S_n}(\epsilon)=S_n-\hat{S_n}(\epsilon)$ the sum on small terms.

First, $\bar{S_n}$ contributes little when $\epsilon$ is small. To see this, notice if we let $\bar{X}_{n,m}(\epsilon)=X_{n,m}1_{|X_{n,m}|\le \epsilon n^{1/\alpha}}$, we have $\bar{S_n}(\epsilon)=\sum_{m=1}^{n} \bar{X}_{n,m}(\epsilon)$. Since law of $X$ is symmetric, $E\bar{X}_{n,m}=0$. By independence $E(\bar{S_n}(\epsilon)^2)=nE\bar{X}_1(\epsilon)^2$, and 
$$
E\bar{X}_1(\epsilon)^2=\int_0^\infty 2yP(|\bar{X}_1(\epsilon)|>y)dy\le\int_0^1 2ydy+\int_1^{\epsilon n^{1/\alpha}}2y\ y^{-\alpha}dy=1+\frac{2}{2-\alpha}(\epsilon^{2-\alpha}n^{2/\alpha-1}-1)\le \frac{2}{2-\alpha}\epsilon^{2-\alpha}n^{2/\alpha-1}
$$
so $E(\bar{S_n}(\epsilon)/n^{1/\alpha})^2\le \frac{2\epsilon^{2-\alpha}}{2-\alpha}$.

Next we compute $\hat{S_n}(\epsilon)/n^{1/\alpha}$. First, we notice $I_n(\epsilon)\sim B(n,\epsilon^{-\alpha}/n)$. Conditioning on $I_n(\epsilon)$, $\hat{S_n}$ is the sum of $I_n(\epsilon)$ independent r.v.'s with distribution $F_n^\epsilon$, given by (symmetric for $x<\epsilon$)
$$
1-F_n^\epsilon(x)=P(X_1/n^{1/\alpha}>x||X_1|/n^{1/\alpha}>\epsilon)=x^{-\alpha}/2\epsilon^{-\alpha}=1-F(x/\epsilon), x\ge \epsilon
$$
which, due to the property of the distribution, $=_d \epsilon X_1$. By this, $F_n^\epsilon$ has ch.f. $\varphi_{X_1}(\epsilon t)$, so the ch.f. of $\hat{S_n}(\epsilon)/n^{1/\alpha}$ is given by 
$$
E\exp(it\hat{S_n}(\epsilon)/n^{1/\alpha})=\sum_{m=0}^n\binom{n}{m}(\epsilon^{-\alpha}/n)^m(1-\epsilon^{-\alpha}/n)^{n-m}\varphi_{X_1}(\epsilon t)^m
$$
still by DCT, control term by 
$$
|\binom{n}{m}(\epsilon^{-\alpha}/n)^m(1-\epsilon^{-\alpha}/n)^{n-m}\varphi_{X_1}(\epsilon t)^m|\le \binom{n}{m}/n^m\le \frac{1}{m!}
$$
which is summable, we can get (by Poisson approximation of binomial distribution)
$$
E\exp(it\hat{S_n}(\epsilon)/n^{1/\alpha})\to\sum_{m=0}^\infty \exp(-\epsilon^{-\alpha})(\epsilon^{-\alpha})^m \varphi_{X_1}(\epsilon t)^m/m!=\exp(-\epsilon^{-\alpha}(1-\varphi(\epsilon t)))
$$
Meanwhile recall $1-\varphi(t)\sim C|t|^\alpha$, we have $\lim_{\epsilon\to 0}\exp(-\epsilon^{-\alpha}(1-\varphi(\epsilon t)))=\exp (-C|t|^\alpha)$.

To reach the same result, we want $\epsilon=0$. The case here is subtle, since we only have pointwise convergence, and we don't know if LHS is cts at 0. The best result we can get (which is enough) is:

**Lemma 3.8.1** If $h_n\to g$ pointwise on $(0,a)$ where $a>0$, and $g$ is cts at 0, we can pick $\epsilon_n\to 0$, where $h_n(\epsilon_n)\to g(0)$.

_Remark_ Construction is direct. 

Apply this to $h_n=LHS$ and $g=RHS$, we know there is a sequence of $\epsilon_n$ s.t. $\hat{S_n}(\epsilon_n)/n^{1/\alpha}\to_d Y$ where $Y$ has ch.f. $\exp(-C|t|^\alpha)$.

Meanwhile, $E(\bar{S_n}(\epsilon_n)/n^{1/\alpha})^2\to 0$, implying $\bar{S_n}(\epsilon_n)/n^{1/\alpha}\to 0$ in prob. By Slutsky's theorem we have $S_n/n^{1/\alpha}\to_d Y$.

We will generalize this result.

**Definition** $L:\mathbb R_+\to \mathbb R_+$ is **slowly varying** if $\lim_{x\to\infty}L(tx)/L(x)=1$ for all $t>0$. $L(t)=\log t$ is slowly varying but $L(t)=t^\epsilon$ is not.

**Theorem 3.8.2** Suppose $X_i$ are i.i.d. with distribution satisfying

(i) $\lim_{x\to\infty}P(X_1>x)/P(|X_1|>x)=\theta\in [0,1]$

(ii) $P(|X_1|>x)=x^{-\alpha}L(x)$, where $\alpha<2$ and $L$ slowly varying. 

Let $S_n=X_1+...+X_n$, $a_n=\inf\{x:P(|X_1|>x)\le n^{-1} \}$, $b_n=nE(X_11_{|X_1|\le a_n})$. 

Then as $n\to\infty$, $(S_n-b_n)/a_n\to_d Y$ where $Y$ has a nondegenerate distribution.

_Remark_ The conditions are also necessary.

<font color='red'>_proof of Theorem 3.8.2_</font> 

The proof is mimicing the proof for that example.

- $nP(|X_1|>a_n)\to 1$.

  By definition of $a_n$, $nP(|X_1|>a_n)\le 1$. For the inverse, by (ii) we have 
  $$
  (1+2\epsilon)^{-\alpha}=\lim_{n \to \infty}\frac{P(|X_1|>(1+2\epsilon)a_n/(1+\epsilon))}{P(|X_1|>a_n/(1+\epsilon))}\le \liminf_{n\rightarrow\infty}\frac{P(|X_1|>a_n)}{1/n}
  $$
  since $\epsilon$ is arbitrary, $nP(|X_1|>a_n)\to 1$ a.s.. This implies $a_n\to\infty$.

- So $nP(X_1>xa_n)\to\theta x^{-\alpha}$ for $x>0$. So $|\{m\le n: X_n>xa_n\}|\to_d P(\theta x^{-\alpha})$. This indicates that $\mathcal X_n=\{X_m/a_m:1\le m\le n \}$ converges to a Poisson process on $(-\infty,\infty)$ with mean measure 
  $$
  \mu(A)=\int_{A\cap\mathbb R_+}\theta \alpha |x|^{-\alpha-1}dx+\int_{A\cap \mathbb R_-}(1-\theta)\alpha|x|^{-\alpha-1}dx
  $$

- Let $I_n(\epsilon)=\{m\le n:|X_m|>\epsilon a_n \}$, $\hat{\mu}(\epsilon)=EX_m1_{\epsilon a_n< |X_m|\le a_n}$, $\hat{S_n}(\epsilon)=\sum_{m\in I_n(\epsilon)} X_m$, $\bar{\mu}(\epsilon)=EX_m1_{|X_m|\le \epsilon a_n}$, $\bar{S_n}(\epsilon)=(S_n-b_n)-(\hat{S_n}(\epsilon)-n\hat{\mu} (\epsilon))=\sum_{m=1}^{n} X_m1_{|X_m|\le \epsilon a_n}-\bar{\mu}(\epsilon)$.

- $\bar{S_n}(\epsilon)$ contributes little: Let $\bar{X}_m(\epsilon)=X_m1_{|X_m|\le \epsilon a_n}$, we have 
  $$
  E(\bar{S_n}(\epsilon)/a_n)^2=n\ var(\bar{X}_1(\epsilon)/a_n)\le nE(\bar{X}_1(\epsilon)/a_n)^2\le n\int_0^\epsilon2yP(|X_1|>ya_n)dy=nP(|X_1|>a_n)\int_0^\epsilon 2y \frac{P(|X_1|>ya_n)}{P(|X_1|>a_n)}dy
  $$
  Take $n\to\infty$, we expect the minit and integral sign commutes. But something subtle is that the ratio of probabilities may be unbounded so we can't use Fatou's Lemma. As (ii) implies, the ratio is of order $y^{-\alpha-\delta}$.

  **Lemma 3.8.3** For any $\delta>0$, there is $C$ so that $\forall t\ge t_0$ and $y\le 1$, $P(|X_1|>yt)/P(|X_1|>t)\le Cy^{-\alpha-\delta}$.

  _Remark_ We cannot directly use property (ii) since our result is uniform for $y$. To conquer this, we use a sequence to control them.

  <font color='red'>_proof of Lemma 3.8.3_</font> By (ii), $P(|X_1|>t/2)/P(|X_1|>t)\to 2^\alpha$. So there is some $t_0$ s.t. $\forall t>t_0$, $P(|X_1|>t/2)/P(|X_1|>t)\le 2^{\alpha+\delta}$. Continue until $t/2^m <t_0$, we have $P(|X_1|>t/2^n)/P(|X_1|>t)\le C2^{(\alpha+\delta)n}$ for all $n$, where $C=1/P(|X_1|>t_0)$ (Here we control the tail by C) . Let $1/2^n<y\le 1/2^{n-1}$, we have $P(|X_1|>yt)/P(|X_1|>t)\le C2^{(\alpha+\delta)n}\le C 2^{\alpha+\delta}y^{-\alpha-\delta}$.

  Use the lemma to estimate we have $\limsup_{n\rightarrow\infty} E(\bar{S_n}(\epsilon)/a_n)^2\le 1\cdot \int_0^\epsilon 2yCy^{-\alpha-\delta}dy$. Pick $\delta<2-\alpha$, we know $RHS\to 0$ as $\epsilon\to 0$.

- Compute $\hat{S_n}(\epsilon)$: First $|I_n(\epsilon)|\to_d P(\epsilon^{-\alpha})$. Conditioning on $|I_n(\epsilon)|$, $\hat{S_n}(\epsilon)/a_n$ is the sum of $|I_n(\epsilon)|$ independent r.v. with distribution $F_n^\epsilon$, where 
  $$
  1-F_n^\epsilon(x)=P(X_1/a_n>x||X_1|/a_n>\epsilon)\to \theta x^{-\alpha}/\epsilon^{-\alpha}
  \\F_n^\epsilon(-x)=P(X_1/a_n<-x||X_1|/a_n>\epsilon)\to (1-\theta)|x|^{-\alpha}/\epsilon^{-\alpha}
  $$
  for $x\ge\epsilon$. Let $\psi_n^\epsilon$ be the ch.f. of $F_n^\epsilon$, and $\psi^\epsilon$ be the ch.f. of the limit. As in the proof of the example we have $\varphi_{\hat{S_n}(\epsilon)/a_n}\to\exp(-\epsilon^{-\alpha}(1-\psi^\epsilon(t)))$. After some estimation on integrals, we have (and combine the last point) $(S_n-b_n)/a_n$ has nondegenerate ch.f..

(The left is for later completion)

### 3.10 Limit Theorems in $\mathbb R^d$ 

We begin by considering weak convergence in a general metric space $(S,\rho)$. We say $X_n\to_d X_\infty$ iff $Ef(X_n)\to Ef(X_\infty)$ for all bounded cts $f$. We will develop some equivalent definitions of weak convergence. 

**Theorem 3.10.1** TFAE:

(i) $Ef(X_n)\to Ef(X_\infty)$ for all bounded cts $f$.

(ii) $Ef(X_n)\to Ef(X_\infty)$ for all bounded Lipstichz cts $f$.

(iii) For all closed sets $K$, $\limsup_{n\rightarrow\infty} P(X_n\in K)\le P(X_\infty \in K)$.

(iv) For all open sets $G$, $\liminf_{n\rightarrow\infty} P(X_n\in G)\ge P(X_\infty\in G)$.

(v) For all sets $A$ with $P(X_\infty\in\partial A)=0$, $\lim_{n \to \infty} P(X_n\in A)=P(X_\infty\in A)$.

(vi) Let $D_f$ be the set of discontinuities of $f$. For all bounded functions $f$ with $P(X_\infty\in D_f)=0$, we have $Ef(X_n)\to Ef(X_\infty)$.

<font color='red'>_proof of Theorem 3.10.1_</font> 

(i)$\Rightarrow$(ii) is trivial.

(ii)$\Rightarrow$ (iii) Let $f_j(x)=(1-j\rho(x,K))^+$. $f_j$ is Lipstichz cts and takes value on $[0,1]$, and $f_j\downarrow 1_K$. So $\limsup_{n\rightarrow\infty} P(X_n\in K)\le \lim_{n \to \infty} Ef_j(X_n)=Ef_j(X_\infty)$. Let $j$ go to infty, by BCT the limit is $P(X_\infty\in K)$.

_Remark_ Before we use Fatou's Lemma to prove this, but now we cannot. This is because we can find $Y_i=_d X_i$ and $Y_i\to Y_\infty$ a.s. for $d=1$ case. This is also true in any complete separable metric space but the construction is messy.

(iii)$\Leftrightarrow$ (iv) is trivial.

(iii),(iv)$\Rightarrow$ (v) consider $A^o$ and $\bar{A}$.

(v)$\Rightarrow$ (vi) Suppose $|f|\le K$. Since $\{\alpha: P(f(X_\infty)=\alpha)>0\}$ is countable, we can find $\alpha_0<-K<\alpha_1<...<a_{l-1}<K<\alpha_l$ s.t. $P(f(X_\infty)=\alpha_i)=0\forall i$, $\alpha_i-\alpha_{i-1}<\epsilon$. Let $A_i=f^{-1}((\alpha_{i-1},\alpha_i])$. Then $\partial A_i\subset f^{-1}(\{\alpha_{i-1},\alpha_i \})\cup D_f$. So $P(f(X_\infty)\in\partial A_i)=0$. So $\sum_{i=1}^{l}\alpha_iP(X_n\in A_i)\to\sum_{i=1}^{l} \alpha_i P(X_\infty\in A_i)$. Since $0\le \sum_{i=1}^{l} \alpha_i P(X_n\in A_i)-Ef(X_n)\le\epsilon$ and $\epsilon$ is arbitrary, $Ef(X_n)\to Ef(X_\infty)$.

(vi)$\Rightarrow$ (i) is trivial.

Return to $\mathbb R^d$. Let $X=(X_1,...,X_d)$ be a random vector. 

**Definition** The **distribution function** of $X$ is defined by $F(x)=P(X\le x)$, where $X\le x$ means $X_i\le x_i\forall i$. It satisfies:

(i) Nondecreasing, i.e., $x\le y\Rightarrow F(x)\le F(y)$.

(ii) $\lim_{x \to \infty} F(x)=1$, and $\lim_{x_i \to -\infty} F(x)=0$.

(iii) Right cts, i.e., $\lim_{y\downarrow x} F(y)=F(x)$.

(iv) $\Delta_A F\ge 0$ for all rectangles $A$. Recall the definition of a prob. measure in multi-dim case.

If $F_n$ and $F$ are distribution functions on $\mathbb R^d$, we say $F_n\to_w F$ if $F_n(x)\to F(x)$ at all cts points of $F$.

**Example** This example is to show there is "enough points" to make the definition sensible.

Consider the distribution function of $(0,Y)$ where $Y\sim U(0,1)$:
$$
F(x,y)=\left\{\begin{aligned}&1&\text{if }x\ge 0, y\ge 1\\&y&\text{if }x\ge 0, 0\le y<1\\&0&\text{otherwise}\end{aligned}\right.
$$
its discontinuities are $\{0\}\times R_+$, but it doesn't have any point mass, which is different from the case in $d=1$.

Let's dive deeper. Observe $\lim_{x_n\uparrow x}F(x)-F(x_n)=P(X\le x)-P(X<x)$. For $d=1$, $RHS=P(X=x)$. But for $d=2$, actually $RHS=P(X\in (-(\infty,x_1]\times \{x_2\}\cup \{x_1\}\times (-\infty,x_2])$. For higher $d$, let $H_c^i=\{x:x_i=c\}$ be a hyperplane. Notice for different $c$ $H_c^i$ are disjoint, so at most countable of them carry positive probability. 

Let $D^i=\{c:P(X\in H_c^i)>0 \}$. If $x\notin D^i\forall i$, $F$ must be cts at $x$, since in this case $P(X\le x)=P(X<x)$ (but not vise versa) . So the discontinuities of $F$ are at most countable.

**Theorem 3.10.2** Let $X_i$ has distribution $F_i$. Then $F_i\to_w F$ iff $X_i\to_d X$ in the metric space.

<font color='red'>_proof of Theorem 3.10.2_</font> 

$\Rightarrow$ We prove **Theorem 3.10.1** (iv) holds. Since we are approximating an open set, we only need to show the converge holds for enough rectangles. We say a rectangle $A$ is good if its vertices doesn't lie in any $D^i$. Then at those vertices $F$ is cts, and we can show $P(X_n\in A)\to P(X\in A)$. $A$'s are many enough by our observation.

$\Leftarrow$ Use **Theorem 3.10.1** (v). If $F$ is cts at $x$, we have $P(X\le x)=P(X<x)$, so let $A=(-\infty,x_1]\times...\times (-\infty,x_d]$ we know $P(X\in\partial A)=0$, so $F_n(x)=P(X_n\in A)\to P(X\in A)=F(x)$.

Tightness can also be generalized. We say a sequence of prob. measure $\mu_n$ is tight if $\forall \epsilon,\exists M:\mu_n([-M,M]^d)\ge 1-\epsilon$.

**Theorem 3.10.3** If $\mu_n$ is tight, then there is a weakly convergent subsequence.

Proof is similar with 1d case.

**Definition** the **ch.f.** of $(X_1,...,X_d)$ is $\varphi(t)=E\exp(it\cdot X)$.

**Theorem 3.10.4 Inversion formular** If $A=[a_1,b_1]\times ...\times [a_d,b_d]$ with $\mu(\partial A)=0$ we have $\mu(A)=\lim_{T \to \infty} (2\pi)^{-d}\int_{[-T,T]^d}\prod_{j=1}^d \psi_j (t_j)\varphi(t)dt$, where $\psi_j(s)=(\exp(-isa_j)-\exp(-isb_j))/is$.

<font color='red'>_proof of Theorem 3.10.4_</font> Fubini theorem and BCT.

**Theorem 3.10.5 Convergence theorem** Let$X_n$ be random vectors with ch.f. $\varphi_n$. Then $X_n\to_d X_\infty$ iff $\varphi_n(t)\to\varphi_\infty (t)$.

Proof is similar with 1d case. Moreover, if $\varphi_n(t)$ converges to some function which is cts at $0$, then the limit is the ch.f. of some random vector and is the weak limit.

**Theorem 3.10.6 Cramer-Wold device** If $\forall\theta\in\mathbb R^d$, $\theta\cdot X_n\to_d \theta\cdot X_\infty$, we have $X_n\to _d X_\infty$.

<font color='red'>_proof of Theorem 3.10.6_</font> if $\theta\cdot X_n\to_d\theta\cdot X_\infty$, we have $E\exp(i\theta\cdot X_n)\to E\exp(i\theta\cdot X_\infty)$.

**Theorem 3.10.7 the central limit theorem in $\mathbb R^d$** Let $X-i$ be i.i.d. random vectors with $EX_n=\mu$ and finite covariance $\Gamma_{ij}=E((X_{n,i}-\mu_i)(X_{n,j}-\mu_j))$, then $(S_n-n\mu)/n^{1/2}\to_d \mathcal N(0,\Gamma)$.

<font color='red'>_proof of Theorem 3.10.7_</font> WLOG $\mu=0$. $\forall \theta\in \mathbb R^d$, we have $\theta\cdot X_n$ is a r.v. with mean 0 and variance 
$$
E(\sum_i \theta_i X_{n,i})^2=\sum_i\sum_j E(\theta_i \theta_j X_{n,i}X_{n,j})=\sum_i\sum_j \theta_i \theta_j \Gamma _{ij}
$$
using CLT in 1d and **Theorem 3.10.6**.

**Example 3.10.8 Simple random walk on $\mathbb Z^d$** Let $X_i$ be i.i.d. with $P(X_n=e_i)=P(X_n=-e_i)=1/2d$. $Cov X=\frac{1}{2d} I$. So $S_n/\sqrt{n}\to_d \mathcal N(0,\Gamma)$.

**Example 3.10.9** Let $X_i$ be i.i.d. with $P(X_i=e_i)=1/6$ for $i=1,...,6$. Then $EX_{n,i}=1/6$ and $EX_{n,i}X_{n,j}=0$ for $i\ne j$. So $\Gamma_{i,i}=5/36,\Gamma_{i,j}=-1/36$, and the limiting distribution is concentrated on $\{x:\sum_i x_i=0 \}$.

**multivariate normal distribution** write $\Gamma=U^t V U$ where $U^t$ is orthogonal and $V$ is diagonal, and $W=\sqrt{V}$. Let $A=WU$, $Y=(X_1,...,X_n)$ where $X_i$ i.i.d. $\sim\mathcal N(0,1)$, then $YA$ has law $\mathcal N(0,\Gamma)$.

**Exercise 3.10.6** r.v.'s $X_1,...,X_k$ are independent iff $\varphi_{X_1,...,X_k}(t)=\prod_{j=1}^k \varphi_{X_j}(t_j)$.

<font color='red'>_proof of Exercise 3.10.6_</font> $\Leftarrow$ We can pick $Y_i=_d X_i$ that are independent. So $(Y_i)$ has ch.f. $\varphi_{X_1,...,X_k}$, so $(Y_i)=_d (X_i)$. Check $X_i$ are independent by definition.

$\Rightarrow$ $E\exp(it\cdot X)=E\prod_i \exp(it_iX_i)=\prod_i E\exp(it_i X_i)$.
