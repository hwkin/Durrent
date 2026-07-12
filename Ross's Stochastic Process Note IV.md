## Chapter 5 Continuous-time Markov chains

### 5.2 Continuous-time Markov Chains

**Definition** $X(t)$ with $\mathcal S=\mathbb N$ is a **continuous-time Markov chain** if $\forall s,t\ge 0,i,j\in \mathcal S$, we have $P(X(t+s)=j\mid X(s)=i,X(u)=u,0\le u<s)=P(X(t+s)=j\mid X(s)=i)$, i.e., conditioned on $s$, the future process $X(t),t>s$ is independent of the past $X(u),0\le u<s$.

_Remark_ We assume that $P(X(t+s)=j\mid X(s)=i)$ is independent of $s$, i.e., $X(t)$ is stationary.

Denote the waiting time between some two transitions by $\tau$, by Markovian property we have $P(\tau>s+t\mid \tau>s)=P(\tau>t)$, so $\tau$ is exponentially distributed. 

By this, we have <font color='red'>Perspective 1</font> for cts-time Markov chain: as it enters state $i$, it waits for $T\sim Exp(\nu_i)$ ($0\le \nu_i<\infty$) and transits to state $j$ with $p_{ij}$.($\sum_{j\ne i}p_{ij}=1$). Waiting times are independent of each other, and transitions are also independent.

**Definition** Call $q_{ij}=\nu_ip_{ij}$ the **transition rate** from $i$ to $j$, since it's the rate at which the process transits into $j$ from $i$. Meanwhile, let $p_{ij}(t)=P(X(t+s)=j\mid X(s)=i)$, and $p_{ij}'(t)$ be the derivative of $p_{ij}(t)$, which can be seen as the rate of transition from state $i$ to $j$.

By this, we have <font color='red'>Perspective 2</font> for cts-time Markov chain: as it enters state $i$, there are clocks corresponding to states except $i$, with independent holding times $T_j\sim Exp(q_{ij})$. The chain transits to the state whose clock is the first to go off. This is because $\min_{j\ne i}T_j\sim Exp(\nu_i)$ and $P(T_k\le T_j,j\ne i,k)=p_{ij}$.

### 5.3 Birth and Death Processes

**Definition** A cts-time Markov chain with states $\mathcal S=\mathbb N$, with $q_{ij}=0\ \forall|i-j|>1$ is called a **birth and death process**. Consider the states as the scale of some population, then if the state increases by $1$, we say a birth occurs and if the state decreases by $1$ we say a death occurs. 

By <font color='red'>Perspective 2</font>, whenever there are $i$ people, a birth will occur in $T\sim Exp(\lambda_i)$ and a death will occur in $T'\sim Exp(\mu_i)$ independently, with $\lambda_i=q_{i,i+1}$ (**birth rates**) and $\mu_i=q_{i,i-1}$ (**death rates**). 

**Example 5.3(A) Two Birth and Death Processes** 

(i) M/M/s queue. Suppose there are $s$ service desks and customers arrive $\sim P_\lambda(t)$ and the service time are i.i.d. $\sim Exp(\mu)$. Let $X(t)$ denote the number of people in the system, $X(t)$ is a birth and death process with $\lambda_n=\lambda$ and $\mu_n=(n\wedge s)\mu$.

(ii) Linear growth model with immigration: $\mu_n=n\mu$ and $\lambda_n=n\lambda+\theta$. $\theta$ represents immigration.

**Definition** A birth and death process is said to be a **pure birth process** if $\mu_n=0\forall n$.

_Example_ Poisson process is pure. 

_Example_ Consider a population where there is no death and everyone gives birth independently $\sim Exp(\lambda)$, then the number of population is also pure with $\lambda_n=n\lambda$, which is called a **Yule process**.

> [!Note]
>
> Consider a Yule process with $X(0)=1$, and $T_i$ be the waiting times from state $i$ to $i+1$. Then $T_i$ are independent and $T_i\sim Exp(i\lambda)$. 
>
> 1. The distribution of $S_n=T_1+...+T_n$ can be determined by induction on $n$ and direct computation. The result is: $P(S_n<t)=(1-e^{-\lambda t})^n$.
>    
>    Or more elegantly, consider $n$ clocks, each with holding time $T\sim Exp(\lambda)$ independent of each other. Let $R_i$ be the time of the $i$th ring. Then $R_i\sim Exp((n+1-i)\lambda)$, and by the memoryless property $R_i$ are independent. On the one hand, $\sum_{i=1}^n T_i=_d \sum_{i=1}^{n} R_i$; on the other hand, $P(S_n<t)=P(\sum_{i=1}^{n} R_i<t)=(1-e^{-\lambda t})^n$ by independence of clocks.
>    
>    So $p_{1j}(t)=(1-e^{-\lambda t})^{j-1}-(1-e^{-\lambda t})^j=e^{-\lambda t}(1-e^{-\lambda t})^{j-1}$, $X(t)\sim G(e^{-\lambda t})$. 
>    
>    Moreover, if $X(0)=i$, $X(t)$ is the sum of $i$ geometric r.v.'s, i.e., negative binomial distribution.
>    
> 2. Conditioned on $X(t)=n+1$, the distribution of $S_1,...,S_n$ is given by 
>    $$
>    \begin{aligned}
>    &p(S_1=s_1,S_2=s_2,...,S_n=s_n\mid X(t)=n+1)\\
>    &=\frac{p(T_1=s_1,...,T_n=s_n-s_{n-1},T_{n+1}>t-s_n)}{P(X(t)=n+1)}\\
>    &=\frac{\lambda e^{-\lambda s_1}\cdot2\lambda e^{-2\lambda(s_2-s_1)}\cdot...\cdot n\lambda e^{-n\lambda(s_n-s_{n-1}) }\cdot e^{-(n+1)\lambda(t-s_n)}}{(1-e^{-\lambda t})^ne^{-\lambda t}}\\
>    &=\frac{n!\lambda^n}{(1-e^{-\lambda t})^n}\prod_{i=1}^n e^{-\lambda (t-s_i)}
>    \end{aligned}
>    $$
>    (Notice this is not rigorous: it should be density)
>
>    Let 
>    $$
>    f(x)=\left\{\begin{aligned}&\frac{\lambda e^{-\lambda(t-x)}}{1-e^{-\lambda t}},&0\le x\le t\\&0&\text{otherwise} \end{aligned}\right.
>    $$
>    we have 
>    $$
>    f_{S_1,...,S_n\mid X(t)=n+1}(s_1,...,s_n)=n!\prod_{i=1}^n f(s_i)
>    $$
>    i.e., the conditional distribution is the order statistics of $X_,...,X_n$ i.i.d. with density $f$.
>    
>    Also, consider $n$ clocks, then conditioning on $X(t)=n+1$ is equivalent to conditioning on the case that all clocks go off. Then the density of the holding time for each clock is exactly $f$. So $S_1,...,S_n$ is an order statistic.

**Example 5.3(B)** Consider a Yule process with $X(0)=1$, and let $A(t)=a_0+t+\sum_{i=1}^{X(t)-1}(t-S_i)$ be the sum of ages of all individuals, where $a_0$ is the age of the first individual at $t=0$. Conditioned on $X(t)$,
$$
E[A(t)\mid X(t)=n+1]=a_0+t+n\int_0^t (t-s)\frac{\lambda e^{-\lambda (t-s)}}{1-e^{-\lambda t}}ds=a_0+t+n\frac{1-e^{-\lambda t}-\lambda te^{-\lambda t}}{\lambda(1-e^{-\lambda t})}
$$
So 
$$
E[A(t)]=E[E[A(t)\mid X(t)=n+1]]=a_0+t+(e^{\lambda t}-1)\frac{1-e^{-\lambda t}-\lambda te^{-\lambda t}}{\lambda(1-e^{-\lambda t})}=a_0+\lambda^{-1}(e^{\lambda t}-1)
$$
Or use $A(t)=a_0+\int_0^t X(s)ds$ and take expectation (Fubini).

**Example 5.3(c) A simple epidemic model** 

_Setting_ Consider a population of $m$ individuals. At time $0$, one is infected. In any time interval $h$, any given infected person will cause any given susceptible to be infected with probability $\alpha h+o(h)$. As one is infected, it's infected forever. 

Let $X(t)$ denote the number of infected individuals in the population at time $t$. $X(t)$ is a pure birth process, with $\lambda_n=(m-n)n\alpha$. Let $T$ be the time until the total population is infected, i.e., $T=\sum_{i=1}^{m-1} T_i$. $T_i\sim Exp(\lambda_i)$ are independent, so $ET=\sum_{i=1}^{m-1} \frac{1}{\alpha i(m-i)}$ and $var(T)=\sum_{i=1}^{m-1}\frac{1}{(\alpha i(m-i))^2}$.

### 5.4 The Kolmogorov Differential Equations

> **Lemma 5.4.1** (i)$p_{ii}(t)=1-\nu_i t+o(t)$ (ii) $p_{ij}(t)=q_{ij}t+o(t)$.
>
> <font color='red'>_proof of Lemma 5.4.1_</font> 
>
> (i) The probability of two or more jumps is infinitesimal. 
>
> Let $N(t)$ be the number of jumps during $[0,t]$ given $X(0)=i$ and $T_1$ be the first holding time, then $T_1\sim Exp(\nu_i)$. Let $K$ be the state entered at the first jump, so that $P(K=k)=p_{ik}$. Then 
> $$
> P^i(N(t)\ge 2)=\sum_{k\ne i}\int_0^t \nu_i e^{-\nu_i s}p_{ik}(1-e^{-\nu_k(t-s)})ds=\sum_{k\ne i}t\int_0^1\nu_i e^{-\nu_i ut}p_{ik}(1-e^{-\nu_k(1-u)t})du
> $$
> Since $0\le\sum_{k\ne i}\nu_i e^{-\nu_i ut}p_{ik}(1-e^{-\nu_k(1-u)t})\le \sum_k \nu_ip_{ik}\nu_kt$, by Fubini and DCT, push $t\to 0$, we have $P^i(N(t)\ge 2)/t\to 0$.
>
> (ii) $p_{ii}(t)=e^{-\nu_i t}+o(t)=1-\nu_i t+o(t)$, since if it jumps it must jumps for two steps.
>
> (iii) $p_{ij}(t)=(1-e^{-\nu_i t})p_{ij}+o(t)=q_{ij}(t)+o(t)$
>
> **Lemma 5.4.2** For $s,t$, $p_{ij}(t+s)=\sum_{k=0}^\infty p_{ik}(t)p_{kj}(s)$
>
> This is just the continuous version of Chapman-Kolmogorov equations.

**Theorem 5.4.3 Kolmogorov's Backward Equations** For all $i,j$ and $t\ge 0$,
$$
p_{ij}'(t)=\sum_{k\ne i}q_{ik}p_{kj}(t)-\nu_i p_{ij}(t)
$$
<font color='red'>_proof of Theorem 5.4.3_</font> By **Lemma 5.4.2**,
$$
\begin{aligned}
&p_{ij}(t+h)=\sum_k p_{ik}(h)p_{kj}(t)\\\Rightarrow& p_{ij}(t+h)-p_{ij}(t)=\sum_{k\ne i}p_{ik}(h)p_{kj}(t)-(1-p_{ii}(h))p_{ij}(t)\\\Rightarrow&\lim_{h \to 0}\frac{p_{ij}(t+h)-p_{ij}(t)}{h}=\lim_{h \to 0}\sum_{k\ne i}\frac{p_{ik}(h)}{h}p_{kj}(t)-\nu_i p_{ij}(t)
\end{aligned}
$$
Now it suffices to justify the interchange of limit and summation: Notice
$$
\sum_{k\ne i}\frac{p_{ik}(h)}{h}p_{kj}(t)\le \sum_{k\ne i}\frac{p_{ik}(h)}{h}=\frac{1-p_{ii}(h)}{h}\le 2\nu_i
$$
when $h$ is small. By DCT, 
$$
\lim_{h\to 0}\sum_{k\ne i}\frac{p_{ik}(h)}{h}p_{kj}(t)=\sum_{k\ne i}\lim_{h\to 0}\frac{p_{ik}(h)}{h}p_{kj}(t)=\sum_{k\ne i}q_{ik}p_{kj}(t)
$$
In contrast, we have 

**Theorem 5.4.4 Kolmogorov's Forward Equations** Under suitable regularity conditions,
$$
p_{ij}'(t)=\sum_{k\ne i}q_{kj}p_{ik}(t)-\nu_jp_{ij}(t)
$$
<font color='red'>_proof of Theorem 5.4.4_</font> Similarly,
$$
\frac{p_{ij}(t+h)-p_{ij}(t)}{h}=\frac{\sum_k p_{ik}(t)p_{kj}(h)-p_{ij}(t)}{h}=\sum_{k\ne j}p_{ik}(t)\frac{p_{kj}(h)}{h}-\frac{1-p_{jj}(h)}{h}p_{ij}(t)
$$
Notice $\sum_{k\ne j}p_{ik}(t)\frac{p_{kj}(h)}{h}$ may not be dominated by an integrable function in general, since the limits $\lim_{h\to 0}\frac{p_{kj}(h)}{h}$ are not uniform. But in many models DCT can hold.

_Remark_ The difference comes from the moment that the state shifts. For the backward equations, transition happens at $0$ and for the forward equations transition happens at $t$. 

**Example 5.4(A)** Consider a two-state cts Markov chain that $\nu_0=\lambda,\nu_1=\mu,p_{ij}=\delta_{ij}$.Then the forward equations yield
$$
p_{00}'(t)=\mu p_{01}(t)-\lambda p_{00}(t)=-(\lambda+\mu)p_{00}(t)+\mu
$$
along with $p_{00}(0)=1$, whence $p_{00}(t)=\frac{\mu}{\mu+\lambda}+\frac{\lambda}{\mu+\lambda}e^{-(\lambda+\mu)t}$.

**Example 5.4(B)** The Kolmogorov forward equations for the birth and death process are 
$$
\begin{aligned}
p_{i0}'(t)&=\mu_1 p_{i1}(t)-\lambda_0 p_{i0}(t)\\
p_{ij}'(t)&=\lambda_{j-1}p_{i,j-1}(t)+\mu_{j+1}p_{i,j+1}(t)-(\lambda_j+\mu_j)p_{ij}(t),j\ne 0
\end{aligned}
$$
**Example 5.4(C)** For a pure birth process, the forward equations reduce to 
$$
\begin{aligned}
p_{ii}'(t)&=-\lambda_i p_{ii}(t)
\\p_{ij}'(t)&=\lambda_{j-1}p_{i,j-1}(t)-\lambda_j p_{ij}(t),j> i
\end{aligned}
$$
along with $p_{ii}(0)=1$, whence $p_{ii}(t)=e^{-\lambda_i t}$. Indeed this is direct: since the process is pure, $p_{ii}(t)$ is the probability that during $[0,t]$ there is no birth. Also, along with $p_{ij}(0)=0,j\ne i$, $p_{ij}(t)=\lambda_{j-1}e^{-\lambda_j t}\int_0^t e^{\lambda_j s}p_{i,j-1}(s)ds$.

**Example 5.4(D)** 

_Setting_ Consider a population of males and females. Each female gives birth $\sim Exp(\lambda)$ independently, with each birth a female with probability $p$ independently. Females die $\sim Exp(\mu)$ and males die $\sim Exp(\nu)$. Let $X(t)$ be the number of females and $Y(t)$ of males at time $t$, then $(X(t),Y(t))$ is a cts-time Markov chain with infinitesimal rates:
$$
q((n,m),(n+1,m))=n\lambda p,\ q((n,m)(n,m+1))=n\lambda(1-p),\\ q((n,m)(n-1,m))=n\mu,\ q((n,m)(n,m-1))=m\nu
$$
Now $X(0)=i$ and $Y(0)=j$.

(a) Consider $EX(t)$. Notice $X(t)$ is itself a Markov chain, we have 
$$
\begin{aligned}
E[X(t+h)\mid X(t)]&=X(t)+(\lambda p-\mu)X(t) h+o(h)
\\\Rightarrow EX(t+h)&=EX(t)+(\lambda p-\mu)EX(t)h+o(h)
\\\Rightarrow \frac{d}{dt}EX(t)&=(\lambda p-\mu)X(t)
\\\Rightarrow EX(t)&=ie^{(\lambda p-\mu)t}
\end{aligned}
$$
(b) Consider $EY(t)$. Notice $Y(t)$ itself isn't Markov, its information comes from $X(s), Y(s),s<t$.
$$
\begin{aligned}
E[Y(t+h)\mid X(t),Y(t)]&=Y(t)+\lambda(1-p)X(t)h-\nu Y(t)h+o(h) 
\\\Rightarrow E[Y(t+h)\mid X(t)]&=E[Y(t)\mid X(t)]+\lambda(1-p)X(t)h-\nu E[Y(t)\mid X(t)]h+o(h)
\\\Rightarrow EY(t+h)&=EY(t)+\lambda(1-p)EX(t)h-\nu EY(t)h+o(h)
\\\Rightarrow\frac{d}{dt}EY(t)&=\lambda(1-p)ie^{(\lambda p-\mu)t}-\nu EY(t)
\\\Rightarrow EY(t)&=\frac{i\lambda (1-p)}{\lambda p+\nu-\mu}e^{(\lambda p-\mu)t}+\bigg(j-\frac{i\lambda(1-p)}{\lambda p+\nu-\mu}\bigg)e^{-\nu t}
\end{aligned}
$$
(c) Consider $E[X(t)^2]$. Similarly
$$
\begin{aligned}
E[X(t+h)^2\mid X(t)^2]&=\lambda pX(t)h[X(t)+1]^2+\mu X(t)h[X(t)-1]^2+(1-\lambda pX(t)h-\mu X(t)h)X(t)^2
\\&=X(t)^2+2(\lambda p-\mu)hX(t)^2+(\lambda p+\mu)hX(t)+o(h)
\\\Rightarrow E[X(t+h)^2]&=E[X(t)^2]+2(\lambda p-\mu)hE[X(t)^2]+(\lambda p+\mu)hEX(t)+o(h)
\\\Rightarrow \frac{d}{dt}E[X(t)^2]&=2(\lambda p-\mu)E[X(t)^2]+(\lambda p+\mu)ie^{(\lambda p-\mu)t}
\\\Rightarrow E[X(t)^2]&= \frac{i(\mu + \lambda p)}{\mu - \lambda p} e^{(\lambda p - \mu)t} + \left[ i^{2} - \frac{i(\mu + \lambda p)}{\mu - \lambda p} \right] e^{2(\lambda p - \mu)t}.
\end{aligned}
$$
(d) Consider $Cov(X(t),Y(t))$. The technique is identical. One just notice that 
$$
X(t+h)Y(t+h)=
\begin{cases}
(X(t)+1)Y(t) & \text{with prob. } \lambda p X(t)h + o(h) \\
X(t)(Y(t)+1) & \text{with prob. } \lambda(1-p)X(t)h + o(h) \\
(X(t)-1)Y(t) & \text{with prob. } \mu X(t)h + o(h) \\
X(t)(Y(t)-1) & \text{with prob. } \nu Y(t)h + o(h) \\
X(t)Y(t) & \text{with prob. } 1 - \text{the above}
\end{cases}
$$

### 5.5 Limiting probabilities

Recall theorems for semi-Markov process, if the corresponding discrete Markov chain is positive-recurrent with invariant distribution $\pi$,  
$$
p_j:=\lim_{t \to \infty} p_{ij}(t)=\frac{\pi_j/\nu_j}{\sum_i \pi_i/\nu_i}
$$
- Since $\pi_j$ is the unique solution to $\pi_j=\sum_i \pi_i p_{ij},\sum_j \pi_j=1$, $p_j$ is the unique solution to $p_j=\sum_i p_i q_{ij},\sum_{j} p_j=1$. This gives us ways to compute this. 

- Another method for computing this is worth mentioning: Consider forward equations $p_{ij}'(t)=\sum_{k\ne j}q_{kj}p_{ik}(t)-\nu_j p_{ij}(t)$. Suppose $\lim_{t \to \infty} p_{ij}(t)$ exists, $p_{ij}'(t)\to 0$, then $\sum_{k\ne j} q_{kj}p_k=\nu_j p_j$.

_Remarks_ 

- According to properties of semi-Markov process, $p_j$ is also the long-run proportion of the time when the chain stays at state $i$.

- If the initial distribution is $p_j$, the chain is stationary, i.e., $\sum_i p_i p_{ij}(t)=p_j\forall t$.

  _proof_ by DCT,
  $$
  \sum_i p_ip_{ij}(t)=\sum_i \lim_{s \to \infty}p_{ki}(s)p_{ij}(t)=\lim_{s \to \infty}\sum_i p_{ki}(s)p_{ij}(t)=\lim_{s \to \infty} p_{kj}(s+t)=p_j
  $$
- Like what we have done for reversed Markov chain, this has a nice interpretation: In interval $(0,t)$, transitions into j and transitions out of $j$ differ at most $1$. So in the long run the rate at which transitions into state $j$ occur must equal the rate at which transitions out of state $j$ occur. The former is $\sum_{i\ne j} p_i q_{ij}$, and the latter is $p_j\nu_j$. So we attain again that
  $$
  \sum_{i\ne j} p_i q_{ij}=p_j \nu_j
  $$
  By this, the equations are also called "balance equations".

**Limiting probabilities for a birth and death process** Consider the rate at which the chain leaves or enters some state, we have 

| State | Rate Process Leaves    | Rate Process Enters                     |
| ----- | ---------------------- | --------------------------------------- |
| 0     | $\lambda_0p_0$         | $\mu_1 p_1$                             |
| n     | $(\lambda_n+\mu_n)p_n$ | $\mu_{n+1}p_{n+1}+\lambda_{n-1}p_{n-1}$ |

They should be equal. Solve this we have $p_0=\big[1+\sum_{n=1}^\infty\frac{\lambda_0...\lambda_{n-1}}{\mu_1...\mu_n} \big]^{-1}$,$p_n=\frac{\lambda_{n-1}...\lambda_0}{\mu_n...\mu_1}p_0$. So when $\sum_{n=1}^\infty\frac{\lambda_0...\lambda_{n-1}}{\mu_1...\mu_n}$ exists, the limiting probabilities also exist.

**Example 5.5(A) The M/M/1 queue** with $\lambda_n=\lambda$ and $\mu_n=\mu$, we have $p_n=(\lambda/\mu)^n(1-\lambda/\mu)$ when $\lambda<\mu$. Intuitively, if $\lambda>\mu$, the queue will be infinitely long, and if $\lambda=\mu$ the chain behaves like a SRW, which is null recurrent.

**Example 5.5(B)** 

_Setting_ There are $M$ machine, each of which will break down in $Exp(\lambda)$. There is a repairman, who fixes a machine for $Exp(\mu)$. The state $n$ is the number of down machine. 

This is a birth and death process, with $\mu_n=\mu$ and $\lambda_n=(M-n)\lambda$ ($n\le M$). This gives $p_0=\big[1+\sum_{n=1}^{M} (\frac{\lambda}{\mu})^n\frac{M!}{(M-n)!} \big]^{-1}$ and $p_n$, whence we know the mean of down machines in the long run.

Moreover, for the long-run probability that some machine is running, we have 
$$
P(\text{machine is running})=\sum_{n=0}^M P(\text{machine is running}\mid\text{n not working})p_n=\sum_{n=0}^M \frac{M-n}{M}p_n
$$
**Visits to a fixed state** Suppose the chain is positive-recurrent and irreducible. Consider state $0$, by **CLT for renewal process** we have when $t\gg 1$, $\#\text{number of visits}\approx \mathcal N (t/ET_{00},t\ var[T_{00}]/E^3[T_{00}])$, where $T_{00}$ is the time between successive visits to $0$. 

- View this as an alternating renewal process, we have $ET_{00}\ p_0=ET_0=1/\nu_0$, where $T_0$ is the holding time of $0$.
- View this as an reward renewal process, with reward rate at $t$ equal to the time from $t$ to the next visit to $0$. Then the average reward rate is $\frac{ET_{00}^2}{2ET_{00}}$. On the other hand, in the long-run proportion, the average reward rate can be also expressed as $\sum_i p_i ET_{i0}$. $ET_{i0}$ can be solved via $ET_{i0}=1/\nu_i+\sum_{j\ne 0}p_{ij}ET_{j0}$.
- Upon having $ET_{00}$ and $ET_{00}^2$, we can determine the asymptotic distribution of the number of visits.

### 5.6 Time Reversibility

Consider a chain starting from $-\infty$, which is stationary. Now consider it going backwards in time,

- Conditioned on $X(t)$, $X(r),r<t$ and $X(s),s>t$ are independent for all $r,s$. So the reversed process is also Markov.

- If the holding time of $i$ has law $Exp(\nu_i)$, then for the reversed chain, the holding time has the same law: 
  $$
  P(X(r)=i\forall r\in[t-s,t]\mid X(t)=i)=\frac{P(X(r)=i\forall r\in [t-s,t])}{P(X(t)=i)}=\frac{P(X(r)=i\forall r\in[t-s,t]\mid X(t-s)=i)P(X(t-s)=i)}{P(X(t)=i)}=P(X(r)=i\forall r\in[t-s,t]\mid X(t-s)=i)
  $$
  Since $P(X(t-s)=i)=P(X(t)=i)=p_i$.

- The corresponding discrete Markov chain for reversed process has transition probability $p_{ij}^*=\frac{\pi_j p_{ij}}{\pi_i}$. Let $q_{ij}^*=\nu_i p_{ij}^*$, we have $p_i q_{ij}^*=p_j q_{ji}$.

  _Intuition_ Since $p_i$ is the long-run proportion of time when the chain stays at state $i$, it's also that of the reversed chain, therefore $p_i$ is also the stationary distribution for reversed chain. (Or more rigorously, verify the balanced equation.) So $p_j q_{ji}$ is the long-run rate at which the chain transits from $j$ to $i$, and $p_i q_{ij}^*$ is the long-run rate at which the reversed chain transits from $i$ to $j$. They should be equal.

**Definition** The stationary cts-time Markov chain is **time reversible** if the reversed process$=_d$ the original process, i.e., $q_{ij}^*=q_{ij}$. It's equivalent to $p_i q_{ij}=p_j q_{ji}$. 

**Proposition 5.6.1** An ergodic birth and death is time reversible in steady state.

<font color='red'>_proof of Proposition 5.6.1_</font> Since in state $i$ the chain only moves to $i-1$ or $i+1$, so the rate at which the chain transits from $i$ to $i+1$ is equal to that from $i+1$ to $i$.

**Corollary 5.6.2** For a $M/M/s$ queue where customers arrive $\sim P_{\lambda }(t)$ and service time $\sim Exp(\mu)$, if $\lambda<s\mu$, then the output process of customers departing is, in steady state, a Poisson process with rate $\lambda$.

<font color='red'>_proof of Corollary 5.6.2_</font> For the forward process, those $+1$ transitions constitute a Poisson process. Since the $M/M/s$ queue is time-reversible, the $+1$ transitions of reversed chain also constitute a Poisson process with rate $\lambda$, which corresponds $-1$ transitions of original chain.

**Proposition** If one can find $x_j>0$ satisfies $\sum_j x_j=1$ and $x_i q_{ij}=x_j q_{ji}$, then the chain is time reversible, and $x_i$ are just the stationary distribution.

<font color='red'>_proof_</font> 
$$
\sum_{j\ne i}x_j q_{ji}=\sum_{j\ne i}x_i q_{ij}=x_i \nu_i
$$
So balanced equations hold, whence $x_i$ are stationary distribution.

**Proposition 5.6.3** A time-reversible chain with limiting probabilities $p_j$, $j\in \mathcal S$, that is truncated to the set $A\subset \mathcal S$, i.e., $q_{ij}$ is set to $0$ for all $i\in\mathcal S,j\notin \mathcal S$, and remains irreducible is also time reversible and has limiting probabilities $p_j^A=p_j/\sum_{j\in A} p_j, j\in A$.

<font color='red'>_proof of Proposition 5.6.3_</font> $p_i^A q_{ij}=p_j^A q_{ji}$ also holds for $i,j\in A$.

**Example 5.6(A)** Consider a $M/M/1$ queue with capacity $N$. This is a truncated $M/M/1$ queue, so it's also time-reversible, and the limiting probabilities is given by $p_j=\frac{(\lambda/\mu)^j}{\sum_{i=0}^N (\lambda/\mu)^i}$.

#### 5.6.1 Tandem Queues

_Setting_ Consider a 2-server system in which customers enter the first service $\sim P_\lambda (t)$, after being serviced the customers enter the second service. The service time has law $Exp(\nu_i),i=1,2$, and each time only one customer is serviced at one desk.

First, we have concluded the output of the first service, also the entrance of the second, follows $P_{\lambda}(t)$. So the second service is also a $M/M/1$ queue. Now we wonder more results.

**Lemma 5.6.3** In an ergodic $M/M/1$ queue in steady state, 

(i) The number of customers presently in the system is independent of the sequence of the past departure times.

(ii) The waiting time spent in the system (waiting+service) by a customer is independent of the departure process prior to his departure.

<font color='red'>_proof of Lemma 5.6.3_</font> 

(i) For a $M/M/1$ queue, the arrivals $\sim P_\lambda (t)$, so the future arrivals are independent of the present state. Then see the reverse process, by reversibility the departures of original process, also the arrivals of reversed process, $\sim P_\lambda (t)$. So the past departures are independent of the present state.

(ii) Denote $T_1$ and $T_2$ to be the time one enters and exits the queue. Since the queue is FIFO and arrivals$\sim P_\lambda(t)$, $T_2-T_1$ is independent of arrival process after $T_1$. Then reverse the chain. 

_Remark_ past departure $\leftrightarrow$ future arrival.

**Theorem 5.6.4** For the ergodic tandem queue in steady state, denote $X_1(t),X_2(t)$ to be the number of customers in the first and second service, we have

(i) $X_1(t),X_2(t)$ are independent, with $P(X_1(t)=n,X_2(t)=m)=(\lambda/\mu_1)^n (1-\lambda/\mu_1)(\lambda/\mu_2)^m(1-\lambda/\mu_2)$.

(ii) the waiting time of a customer at service $1$ is independent of that at service $2$.

<font color='red'>_proof of Theorem 5.6.4_</font>  

(i) Independence: By **Lemma 5.6.3(i)**, $X_1(t)$ is independent of the sequence of the departure process prior to time $t$, which determines $X_2(t)$.

Probabilities: $P(X_1(t)=n)=(\lambda/\mu_1)^n(1-\lambda/\mu_1)$ since the chain is stationary; since the arrivals of service $2$ $\sim P_\lambda (t)$, $P(X_2(t)=m)=(\lambda/\mu_2)^m(1-\lambda/\mu_2)$. 

(ii) By **Lemma 5.6.3(ii)**, the waiting time of a customer at service $1$ is independent of the departure process prior to his departure at $1$, which in conjunction with service time at service $2$ determines the waiting time at $2$.

_Remark_ For a fixed customer, the waiting time in two services are independent, but the waiting time in two queues are not independent in general. 

> _Counterexample_ Suppose $\lambda\ll\mu_1=\mu_2$, then almost all customers have zero wait in queue at both services. However given that the wait in queue $1$ is positive, the wait in queue $2$ is also positive with high probability: Suppose customer $A$ has positive waiting time, then there is a customer ahead of him, say $B$. The moment $B$ enters the second queue,$A$ enters the service 1. Even if $B$ enters the service 2 immediately, that the service time of $B$ is longer than that of $A$ has probability $1/2$ since $\mu_1=\mu_2$. So $A$ waits for positive time in 2 has probability $\ge1/2$. This indicates the waiting time in queue may be dependent.

#### 5.6.2 A Stochastic Population Model

_Setting_ Suppose that mutant individuals enter a population $\sim P_\lambda (t)$, and upon arrival every mutant becomes an ancestor of a family. All individuals independently give birth $\sim Exp(\nu)$ and die $\sim Exp(\mu)$ ($\nu<\mu$).

_Notation_ Let $N_j(t)$ denote the number of families at time $t$ that consists of exactly $j$ members, $j\ge 0$, and $\underline{N}(t)=(N_1(t),N_2(t),...)$, then $\underline{N}(t)$ is a cts-time Markov chain. its state is denoted by $\underline n=(n_1,n_2,...)$. Let $B_j\underline n=(n_1,...,n_{j-1},n_j-1,n_{j+1}+1,...),j\ge 1$, $B_0\underline n=(n_1+1,n_2,...)$ and $D_j\underline n=(n_1,n_2,...,n_{j-1}+1,n_j-1,n_{j+1})$ and $D_1\underline n=(n_1-1,n_2,...)$. Then $B_0\underline n$ represents the join of a new mutant, $B_j\underline n$ represents a birth and $D_j\underline n$ represents a death.

The transition rate is given by $q(\underline n,B_0\underline n)=\lambda$, $q(\underline n,B_j\underline n)=jn_j \nu$ and $q(\underline n,D_j \underline n)=jn_j\mu$.

> [!Tip]
>
> Recall the compound Poisson process: If individuals occur $\sim P_\lambda (t)$, and for each individual occur at time $s$, it will be independently marked as type $k$ with probability $p_k(s)$, where $\sum_k p_k(s)=1\forall t$. Then at time $t$, the number of individuals of type $k$ $\sim P(t\lambda p_k)$, where $p_k=\frac{\int_0^t p_k(t)dt}{t}$.

See this as a compound Poisson process by marking every mutant as type $k$ if the family will have $k$ members at time $t$. This is reasonable since the reproduction and death of every family is independent of each other. So $N_j(t)\sim P(\lambda\int_0^t p_j(s;t)ds)$.

**Theorem 5.6.5 Limiting Probabilities** The cts-time Markov chain $N(t)$ is in steady state time-reversible with limiting probabilities $P(\underline n)=\prod_{i=1}^\infty e^{-\alpha_i}\frac{\alpha_i^{n_i}}{n_i !}$, where $\alpha_i=\frac{\lambda}{i\nu}(\frac{\nu}{\mu})^i$. In other words, $N_j(t)\to_d P(\alpha_j)$.

<font color='red'>_proof of Theorem 5.6.5_</font> 

Similarly to that of birth and death process, the chain is also time-reversible in steady state. Meanwhile, the limit distribution of $N_j(t)$ is Poisson, so $p(\underline n)=\prod_{i=1}^\infty e^{-\alpha_i}\frac{\alpha_i^{n_i}}{n_i !}$.

Now solve $p(\underline n)q(\underline n, B_0\underline n)=p(B_0\underline n)q(B_0\underline n,\underline n)$, we have $\alpha_1=\lambda/\mu$; solve $p(\underline n)q(\underline n,B_j\underline n)=p(B_j \underline n)q(B_j \underline n, \underline n)$, we have $\alpha_{j+1}=\alpha_j \frac{\nu}{\mu}\frac{j}{j+1}$. By this we have $\alpha_j=\frac{\lambda}{j\nu}(\frac{\nu}{\mu})^i$. Actually, we can also conclude the time-reversibility of the chain from here.

**Corollary** For a fixed family, let $T_i$ be the amount of time that the family has $i$ members, then $ET_i=(\nu/\mu)^i/(i\nu)$.

<font color='red'>_proof_</font> Actually this corollary arises from the meaning of $p_j(s):=\lim_{t \to \infty} p_j(s;t)$. From **Theorem 5.6.5** We know that $\lambda\int_0^\infty p_j(s)ds=\alpha_j$. Notice if we let $A(s)$ to be the event that after $s$ from the origination the family has $j$ members, we have 
$$
\int_0^\infty p_j(s)ds=\lim_{t \to \infty} \int_0^t p_j(s;t)ds=\lim_{t \to \infty}\int_0^t E 1_{A(s)}ds=_\text{Fubini}\lim_{t \to \infty}E\int_0^t 1_{A(s)}ds=_\text{DCT}E\int_0^\infty 1_{A(s)}ds=ET_j
$$
**The Oldest family** Consider now the population model in steady state and suppose that the present state is $\underline n^*$. We would like to determine the probability that a given family of size $i$ is the oldest family in the population. 

By time reversibility, this probability is equal to the probability that the given family will be the last surviving family among present families. But from the state spaces, we can't determine the extinction for a **given** family. So now we need to construct a new state space.

- For technical reason (one cannot uniformly choose one from infinite objects) , truncate the state space s.t. $\sum_i n_i\le M$, where $M\ge \sum_i n_i^*$. The resulting chain is also time reversible with limit probabilities scaled by $C>0$. This means whenever there are $M$ families, mutants are not allowed to join.
- To keep track of a given family, label them by $1,...,M$, and a new family will be uniformly assigned an unused label. Let $s_i$ to be the number of members in family $i$, then $\underline s=(s_1,...,s_M)$ makes up of a state space. $\underline n(\underline s)$ is defined as above.

**Proposition 5.6.6** The chain with states $\underline s=(s_1,...,s_M)$ is time reversible and has stationary probabilities given by 
$$
p(\underline s)=\frac{(M-\sum_i n_i)!\prod_{i=1}^\infty n_i!}{M!}C\prod_{i=1}^\infty e^{-\alpha_i}\frac{\alpha_i^{n_i}}{n_i!}
$$
_Intuition_ 
$$
p(\underline s)=p(\underline n)p(\underline s\mid\underline n)=p(\underline s\mid \underline n)C\prod_{i=1}^\infty e^{-\alpha_i}\frac{\alpha_i^{n_i}}{n_i!}
$$
Since the labels are random, indeed $p(\underline s\mid \underline n)=\binom{M}{n_1,...,n_k,...,M-\sum_i n_i}^{-1}$.

<font color='red'>_proof_</font> Verify equations.

**Corollary 5.6.7** If in steady state, there are $n_i$ families of size $i$, then the probability that a given family of size $i$ is the oldest family in the population is $i/\sum_j n_j$.

<font color='red'>_proof of Corollary 5.6.7_</font> By time reversibility, equivalently we can consider the probability that from the current state on, the given family survives the longest. By symmetry it's just $i/\sum_j n_j$. Let $M\to\infty$.

### 5.7 Applications of the reversed chain to queueing theory

**Theorem 5.7.1** Consider an irreducible cts-time Markov chain with transition rates $q_{ij}$. If we can find $q_{ij}^*$ and $p_i$ s.t. $\sum_i p_i=1$, $p_i q_{ij}=p_j q_{ji}^*$, and $\sum_{j\ne i} q_{ij}=\sum_{j\ne i} q_{ij}^*$, then $q_{ij}^*$ are transition rates for the reversed chain and $p_i$ are the limiting probabilities for both chains.

_Remark_ This is very useful when we can guess $p_i$ and $q_{ij}^*$. We need only to verify those equations.

#### 5.7.1 Network of Queues

_Setting_ There are $k$ desks, and for each desk customers enter the queue from outside $\sim P_{r_i}(t)$. Service time $\sim Exp(\mu_i)$. After being serviced, the customer will join the queue of $j$th desk with probability $p_{ij}$ and leave with probability $1-\sum_{j\ne i} p_{ij}$. Let $X_i$ be the length of queue in front of desk $i$.

Let $\lambda_i$ to be the total arrival rate of desk $i$, we can solve that from $\lambda_i=r_i+\sum_{j\ne i}\lambda_j p_{ji}$.

Now we consider the limiting probabilities. Inspired by that of tandem queue, we can claim:

**Theorem 5.7.2** Assuming that $\lambda_i<\mu_i$ for all $i$, in steady state, $X_i$ are independent, and the limiting probabilities are given by $p(n_1,...,n_k)=\prod_{i=1}^k (\lambda_i/\mu_i)^{n_i}(1-\lambda_i/\mu_i)$.

_Intuition_ 

- From that of tandem queue, we can expect $X_i$ are independent and $p(n_1,...,n_k)=p_1(n_1)...p_k(n_k)$.

- In steady state, the entrance rate equals the departure rate, so for the reversed process the total arrival rate is also $\lambda_i$ for desk $i$. Consider the transition from $i$ to $j$, we have $\lambda_j p_{ji}=\lambda_i \bar{p}_{ij}$, where $\bar{p}_{ij}$ are reversed correspondence of $p_{ij}$.

- The departure rates of the original and reversed process are equal since the service time are equal. 

  Notice here is something subtle: $\lambda_i$ is the long-run departure rate of the process, while $\mu_i$ is the instantaneous departure rate of the process. The difference lies in that the queue may be idle. So the relation is $\lambda_i=\mu_i P(X_i>0)$ in steady state.

- The arrivals from outside correspond to departure. 

<font color='red'>_proof of Theorem 5.7.2_</font> Actually we will justify our intuitions.

The core is to apply **Theorem 5.7.1**. Let $\mathcal S=\{(n_1,...,n_k) \}$.

By our conjecture, now we verify:

- $\underline n=(n_1,...,n_j...,n_k)$ and $\underline n'=(n_1,...n_j+1,...,n_k)$: $\underline n\to\underline n'$ is caused by outside arrival, and the inverse is caused by a departure. This commands:
  $$
  p(\underline n) r_j=p(\underline n')\mu_j(1-\sum_{k\ne j}\bar p_{jk})
  $$
  By independence, we have
  $$
  p_j(n_j)r_j=p_j(n_j+1)\mu_j (1-\sum_{k\ne j}\frac{\lambda_k p_{kj}}{\lambda_j})=p_j(n_j+1)\mu_jr_j/\lambda_j
  $$
  which gives that $p_j(n)=(\lambda_j/\mu_j)^n(1-\lambda_j/\mu_j)$.

- $\underline n=(n_1,...,n_i,...,n_j,...,n_k)$ and $\underline n'=(n_1,...,n_i-1,...,n_j+1,...,n_k)$: $\underline n\to\underline n'$ and the inverse are both caused by shifting between queues, so we should have 
  $$
  \begin{aligned}
  &p(\underline n)\mu_ip_{ij}=p(\underline n')\mu_j\bar p_{ji}
  \\\Leftarrow&p_i(n_i)p_j(n_j)\mu_ip_{ij}=p_i(n_i-1)p_j(n_j+1)\mu_j\frac{\lambda_i p_{ij}}{\lambda_j}
  \\\Leftarrow&(\lambda_i/\mu_i)\mu_i=(\lambda_j/\mu_j)\mu_j (\lambda_i/\lambda_j)
  \end{aligned}
  $$
  which is right.

- $\underline n=(n_1,...,n_j,...,n_k)$ and $\underline n'=(n_1,...,n_j-1,...,n_k)$: Similar to case 1, it suffices to justify 
  $$
  p(\underline n)\mu_j (1-\sum_{k\ne j}p_{jk})=p(\underline n')\bar r_j 
  $$
  where $\bar r_j=\lambda_j-\sum_{k\ne j}\lambda_k\bar p_{kj}$. This also holds.

By these, we have found solutions for equations in **Theorem 5.7.1**. So the limiting probabilities are $p(\underline n)=\prod_k p_k(n_k)=\prod_k (\lambda_k/\mu_k)^{n_k}(1-\lambda_k/\mu_k)$, and the inverse transition rates are given above. The form of $p(\underline n)$ indicates $X_i$ are independent.

Moreover, from the third case, we can conclude the departure of desk $j$ $\sim P_{\bar r_j}(t)$.

**Corollary 5.7.3** Customers leave the system from desk $j$ $\sim P_{\bar r_j}(t)$.

_Remark_ (i) For desk $i$, its limiting distribution is the same as that of $M/M/1$ queue. But in contrast to the fact that $M/M/1$ queue requires Poisson arrival, the arrival of desk $i$ may not be Poisson. This can happen when a customer can visit a service more than once. 

_Counterexample_ Suppose $r_k$ is much smaller than others, $\mu_k$ is much larger than others and with high probability the customer will return. Then after a customer arrive, he will finish the service and return fast with high probability. This implies that a short period after an arrival it's highly likely to occur another arrival while during the period there isn't an arrival around, it's not so likely to occur an arrival. So the increments are not independent, so it can't be Poisson. 

(ii) One can generalize the results for $M/M/k$ queue.

#### 5.7.2 The Erlang Loss Formula

_Setting_ Queueing loss model: customers arrive at $k$ desks $\sim P_\lambda(t)$. If a customer find all desks busy, he will leave. The service time has distribution $G$, density $g$, hazard rate function $\lambda(t)$, and mean $\mu$.

For this setting, let states to be the ordered service time of current customers, i.e., if there are $n$ customers who have been serviced for $x_1\le...\le x_n$ time units, the state is $(x_1,...,x_n)$. This process is Markov with continuum state space, which can also be dealt by reverse process.

The following theorem is the main result of this section.

**Theorem 5.7.4 Erlang Loss formular** The limiting distribution of the number of customers in the system is given by 
$$
P(n\text{ in the system})=\frac{\frac{(\lambda\mu)^n}{n!}}{\sum_{i=0}^{n}\frac{(\lambda\mu)^i}{i!}}
$$
And conditioned on the case that there is $n$ customers in the system, the ages/residual times are i.i.d. $\sim G_e$.

> [!Tip]
>
> Recall: for a renewal process with interarrival distribution $G$, the long-run distribution of age/residual life is $G_e(x)=\mu^{-1}\int_0^x \bar G(s)ds$, and density is $\mu^{-1}\bar{G}(s)$.

_Intuition_ As we have done before, we can guess that the reverse process is also a $k$-server loss system (since there are at most $k$ customers) , with service time distribution $G$, and arrivals $\sim P_\lambda(t)$ (since in steady state, entrance rate=departure rate. _Notice: The departure includes those who finished their service and those who found all desk occupied._). The state represents the residual service time of present customers.

Also, conditioned on the number of customers, the ages should be i.i.d., and the distribution should be equilibrium distribution.

<font color='red'>_proof of Theorem 5.7.4_</font> Apply **Theorem 5.7.1**.

- Let $\underline x=(x_1,...,x_n)$ and $e_i(\underline x)=(x_1,...,x_{i-1},x_{i+1},...,x_n)$. $\underline x\to e_i(\underline x)$ represents that a customer who has been serviced for $x_i$ exits, so the intensity is $\lambda(x_i)$. $e_i(\underline x)\to \underline x$ represents that a customer enters and will be serviced for $x_i$, so the intensity is $\lambda g(x_i)$. These give:
  $$
  p(\underline x)\lambda(x_i)=p(e_i(\underline x))\lambda g(x_i)
  $$

  - Let $P(\emptyset)$ be the limiting probability that the system is idle. Let $i=1,...,n$, we have 
    $$
    p(\underline x)=\prod_{i=1}^n \lambda \bar G(x_i)\ P(\emptyset)
    $$

  - Integrate over $\underline x$ of length $n$, we have 
    $$
    P(n\text{ in the system})=\int_{x_1\le ...\le x_n}P(\emptyset)\prod_{i=1}^n \lambda \bar G(x_i)dx_1...dx_n=P(\emptyset)\frac{(\lambda \mu)^n}{n!}
    $$

  - Summing over $n$, we have 
    $$
    1=P(\emptyset)+\sum_{n=1}^k P(\emptyset)\frac{(\lambda\mu)^n}{n!}
    $$
    which yields $P(\emptyset)=(\sum_{n=0}^k \frac{(\lambda\mu)^n}{n!})^{-1}$. This gives the result of the theorem.

  - Conditioned on the number of customers, we have 
    $$
    p(\underline x\mid n\text{ in the system})=\frac{p(\underline x)}{P(n\text{ in the system})}=n!\prod_{i=1}^n \frac{\bar G(x_i)}{\mu}
    $$
    So the unordered service times are i.i.d. $\sim G_e$.

- Another case to be verify involves $\underline x=(x_1,...,x_n)$ and $(0,\underline x)=(0,x_1,...,x_n)$. $\underline x\to(0,\underline x)$ represents that one customer arrives, whence has intensity $\lambda$, and the inverse represents that one customer leaves, whence has intensity $1$. So
  $$
  p(\underline x)\lambda=p(0,\underline x)
  $$
  which holds since $\bar G(0)=1$.

**Corollary 5.7.5** The departure process is $P_\lambda (t)$.

#### 5.7.3 The M/G/1 Shared Processor system

_Setting_ Customer arrives $\sim P_\lambda (t)$ with work i.i.d. with distribution $G$. Different from the common $M/G/1$ queue where the desk serves one customer once, for a $M/G/1$ shared queue, if there are $n$ customers in the queue, the desk can serve them simultaneously at rate $1/n$ for each customer. Let $\lambda(t)$ be the hazard rate function of $G$, and $\mu$ be the mean.

Also, let states to be the ordered amounts of work already performed of customers presently in the system, $p(\underline x)$ to be the limiting density of state $\underline x$, and $P(\emptyset)$ to be the limiting probability of idle system.

The main result of this section is:

**Theorem 5.7.6** For the processor sharing model, the number of customers in the system has distribution 
$$
P(n\text{ in the system})=(\lambda\mu)^n(1-\lambda\mu)
$$
And conditioned that there are $n$ customers in the system, the completed or residual workloads are i.i.d. $\sim G_e$. The departure process is $P_\lambda(t)$.

_Intuition_ The reversed process should also be a processor sharing model with arrival rate $\lambda$ and work distribution $G$. The states are ordered residual workload.

<font color='red'>_proof of Theorem 5.7.6_</font>

Apply **Theorem 5.7.1**.

- Consider $\underline x$ and $e_i(\underline x)$. $\underline x\to e_i(\underline x)$ represents that one customer who has been serviced for $x_i$ leaves, whence has intensity $\lambda(x_i)/n$. $e_i(x)\to x$ represents that one customer who will be serviced for $x_i$ enters, whence has intensity $\lambda g(x_i)$. So we have 
  $$
  p(\underline x)\frac{\lambda(x_i)}{n}=p(e_i(\underline x))\lambda g(x_i)
  $$

  - Similarly, let $i=1,...,n$, we have $p(\underline x)=n!\lambda^n P(\emptyset)\prod_{i=1}^n \bar G(x_i)$.

    Integrate w.r.t $\underline x$, we have 
    $$
    P(n\text{ in the system})=\int_{x_1\le...\le x_n} n!\lambda^nP(\emptyset)\prod_{i=1}^n \bar{G}(x_i)=\lambda^nP(\emptyset)\mu^n
    $$

  - Summing over $n$, we have 
    $$
    1=P(\emptyset)+\sum_{n=1}^\infty \lambda^nP(\emptyset)\mu^n
    $$
    which yields $P(\emptyset)=1-\lambda\mu$.

  - Conditioned that $n$ people are in the system, we have 
    $$
    p(\underline x\mid n\text{ in the system})=\frac{p(\underline x)}{P(n\text{ in the system})}=n!\prod_{i=1}^n \mu^{-1}\bar G(x_i)
    $$
    so the unordered amounts of work has distribution $G_e$.

- Consider $\underline x$ and $(0,\underline x)$. $\underline x\to(0,\underline x)$ represents that a customer enters, whence has intensity $\lambda$. Meanwhile, the inverse represents that a customer leaves, since the work of every customer is proceed at rate $1/(n+1)$, it has intensity $1/(n+1)$. So 
  $$
  p(\underline x)\lambda=p(0,\underline x)\frac{1}{n+1}
  $$
  which holds.

_Remark_ 

(i) the average number of customers in the system $L$ is 
$$
L=\sum_{i=0}^\infty n(\lambda\mu)^n(1-\lambda\mu)=\frac{\lambda\mu}{1-\lambda\mu}
$$
By **Theorem 3.6.2**, the average time a customer spent in the system $W$ is 
$$
W=\frac{L}{\lambda}=\frac{\mu}{1-\lambda\mu}
$$
which depends only on the mean of $G$. 

This is surprising. Consider if $G_1$ is point mass of $1$ and $G_2\sim Exp(1)$, the mean of $G_1$ and $G_2$ are both $1$, but the residual workloads have distribution $G_{1e}\sim U(0,1)$ and $G_{2e}\sim Exp(1)$ respectively, whose means are $1/2,1$. But the average time a customer spent are equal.

(ii) For a fixed customer, conditioned on his workload $y$, we wonder the mean time spent in the system, say $W'$.

Pick $\epsilon$ and consider the customers with workload between $y$ and $y+\epsilon$, for convenience say they are special. Let $L'$ be the average number of special customers in the system, $\lambda'$ be their arrival rate, and $W'$ be their average time spent in the system.

1. The density of the total workload of someone present in the system is given by 
   $$
   f(w)=\int_0^wf(w\mid \text{has done }x)dG_e(x)=\int_0^w \frac{g(w)}{\bar G(x)}\frac{\bar{G}(x)}{\mu}dx=\frac{wg(w)}{\mu}
   $$
   This is indeed the long-run distribution of total life for a renewal process with interarrival distribution $G$. 

   So $L'=Lf(w)\epsilon+o(\epsilon)$.

2. $\lambda'=\lambda g(y)\epsilon+o(\epsilon)$.

3. $L'=W'\lambda'$, so $W'=y/(1-\lambda\mu)$. 

This can be checked by $W=\int W'(y) dG(y)=\mu/(1-\lambda\mu)$.

### 5.8 Uniformization

Consider a cts-time Markov chain with $\nu_i\equiv \nu$. Let $N(t)$ denote the number of transitions by time $t$, then $N(t)\sim P_\nu(t)$, and 
$$
\begin{aligned}
p_{ij}(t)&=P(X(t)=j\mid X(0)=i)
\\&=\sum_{n=0}^\infty P(X(t)=j\mid X(0)=i,N(t)=n)P(N(t)=n\mid X(0)=i)
\\&=\sum_{n=0}^\infty p_{ij}^n e^{-\nu t}\frac{(\nu t)^n}{n!}
\end{aligned}
$$
where $p_{ij}^n$ is that of corresponding discrete Markov chain. $P(X(t)=j\mid X(0)=i,N(t)=n)=p_{ij}^n$ holds because the condition $\nu_i\equiv\nu$ gives no information about transition states. This allows one to simplify a cts-time Markov chain to a discrete Markov chain.

To apply this idea into a common cts-time Markov chain, we can lengthen the waiting time by allowing the chain to transit from one state to itself. To be precise, pick $\nu\ge\nu_i\forall i$, and consider a chain with $\nu_i^*\equiv \nu$, and $p_{ij}^*=\left\{\begin{aligned}&1-\nu_i/\nu&j=i\\&\nu_ip_{ij}/\nu&j\ne i\end{aligned}\right.$. This chain has the same distribution as the primary chain. This technique is called "uniformization". 

By this, $p_{ij}(t)=\sum_{n=0}^\infty p_{ij}^{*n}e^{-\nu t}\frac{(\nu t)^n}{n!}$.

**Example 5.8(A)** Consider a chain with $\mathcal S=\{0,1\}$, $p_{01}=p_{10}=1$, $\nu_0=\lambda,\nu_1=\mu$. Now we can uniformize this: Set $\nu=\lambda+\mu$, $\nu_1=\nu_2=\nu$, and transition matrix $P=\begin{bmatrix}\mu/(\lambda+\mu) & \lambda/(\lambda+\mu) \\\mu/(\lambda+\mu) & \lambda/(\lambda+\mu)\end{bmatrix}$. Notice $P^n=P\forall n\ge 1$, so we have 
$$
\begin{aligned}
p_{00}(t)&=\sum_{n=0}^\infty p_{00}^n e^{-(\lambda+\mu)t}\frac{[(\lambda+\mu)t]^n}{n!}=\frac{\mu}{\lambda+\mu}+\frac{\lambda}{\lambda+\mu}e^{-(\lambda+\mu)t}\\
p_{11}(t)&=\sum_{n=0}^\infty p_{11}^ne^{-(\lambda+\mu)t}\frac{[(\lambda+\mu)t]^n}{n!}=\frac{\lambda}{\lambda+\mu}+\frac{\mu}{\lambda+\mu}e^{-(\lambda+\mu)t}
\end{aligned}
$$
Consider $S_i(t)=\int_0^t 1_{X(s)=i}ds$, the total time up to $t$ the chain stays at state $i$. $S_i(t)$ is called the **occupation time process for state $i$**.

- The mean time in state $0$ is given by
  $$
  E[S_0(t)\mid X(0)=0]=E\int_0^t 1_{X^0(s)=0}ds=_\text{Fubini}\int_0^t E1_{X^0(s)=0}ds=\int_0^t p_{00}(s)ds=\frac{\mu}{\lambda+\mu}t+\frac{\lambda}{(\lambda+\mu)^2}[1-e^{-(\lambda+\mu)t}]
  $$

- The distribution is given by:
  $$
  P(S_0(t)\le s)=\sum_{n=0}^\infty e^{-(\lambda+\mu)t}\frac{[(\lambda+\mu)t]^n}{n!}P(S_0(t)\le s\mid N(t)=n)
  $$

  - $P(S_0(t)\le s\mid N(t)=0)=0\forall s< t$ since conditioned that $N(t)=0$, $S_0(t)=t$.

  - When $N(t)\ge 1$, conditioned that $N(t)=n$, the transition moments are order statistics of $n$ independent $U(0,t)$. Meanwhile, the first interval must be in state $0$ and for other time intervals, the chain stays at state $0$ with probability $\mu/(\lambda+\mu)$ independently. 

    By these, the number of intervals of state $0$ is $1+B(n,\mu/(\lambda+\mu))$. Conditioned that $1+k$ intervals are picked, by the symmetry we can move these intervals into the first $k$ intervals, i.e., assume we choose the first $1+k$ intervals. This yields:
    $$
    \begin{aligned}
    P(S_0(t)\le s\mid N(t)=n)&=\sum_{k=0}^n P(S_0(t)\le s\mid N(t)=n,k+1\text{ is picked})P(k\text{ is picked among the last }n)
    \\&=\sum_{k=0}^n P(S_0(t)\le s\mid N(t)=n,\text{the first }k+1\text{ is picked})P(k\text{ is picked among the last }n)
    \\&=\sum_{k=0}^n \bigg(\sum_{i=k+1}^n \binom{n}{i}\bigg(\frac{s}{t}\bigg)^i\bigg(1-\frac{s}{t}\bigg)^{n-i} \bigg)\binom{n}{k}\bigg( \frac{\mu}{\lambda+\mu}\bigg)^k\bigg(\frac{\lambda}{\lambda+\mu}\bigg)^{n-k}
    \end{aligned}
    $$
  
  Meanwhile, $P(S_0(t)=t\mid X(0)=0)=e^{-\lambda t}$.

***

Exercises

5.7 Consider a Yule process with $X(0)=1$. Everyone born in time $s$ will be robust with probability $P(s)$. Compute the distribution of number of robust individuals born in $(0,t)$, say $R(t)$.

_Solution_ Conditioned on birth in $(0,t)$, say $B(t)$, we have 
$$
\begin{aligned}
P(R(t)=k)&=\sum_{n=k}^\infty P(R(t)=k\mid B(t)=n)P(B(t)=n)
\\P(B(t)=n)&=(1-e^{-\lambda t})^{n-1}e^{-\lambda t}
\\P(R(t)=k\mid B(t)=n)&=\int_{[0,t]^n}\binom{n}{k}P(s_1)...P(s_k)(1-P(s_{k+1}))...(1-P(s_n))f(s_1)...f(s_n)ds_1...ds_n\\
&=\binom{n}{k}a^k(1-a)^{n-k},\text{ where } a:=\int_0^t  f(s)P(s)ds
\\\Rightarrow P(R(t)=k)&=\sum_{n=k}^\infty \binom{n}{k} a^k (1-a)^{n-k}(1-e^{-\lambda t})^{n-1}e^{-\lambda t}=\frac{a^k(1-e^{-\lambda t})^{k-1}e^{-\lambda t}}{(1-(1-a)(1-e^{-\lambda t}))^{k+1}}
\end{aligned}
$$
5.10 $p(t)=p_{00}(t)$ is cts.

(a) 
$$
\lim_{t\to 0}\frac{1-p(t)}{t}=\nu_0
$$
since in infinitesimal time, the chain can only jump at most once.

(b) 
$$
p(t)p(s)\le p(t+s)\le 1-p(s)+p(s)p(t)
$$
when one consider $X(s)=0$ or not.

(c) by (b) we have
$$
|p(s+t)-p(s)|\le 1-p(t)
$$
Let $t\to 0$, we can conclude $p(s)$ is cts. 

5.17 Given $A\subset S$, consider $T^i(t)$, the amount of time during $[0,t]$ when the chain stays in $A$. with $X(0)=i$. Let $Y_i$ i.i.d. $\sim Exp(\lambda^{-1})$, which are independent of $X(t)$. Set $t_i(n)=E[T^i(Y_1+...+Y_n)]$.

(a) Derive a set of linear equations for $t_i(1),i\ge 0$.

_Solution_ Let $1_A(i)=1_{i\in A}$, and $S_1$ be the holding time of state $i$. Conditioned on $S_1$, we have 
$$
\begin{aligned}
t_i(1)&=E[T^i(Y_1)]\\&=E[T^i(Y_1)\mid Y_1>S_1]P(Y_1>S_1)+E[T^i(Y_1)\mid Y_1<S_1]P(Y_1<S_1)\\
&=^1(E[T^i(S_1)\mid Y_1>S_1]+\sum_{j\ne i}p_{ij}E[T^j(\tilde Y_1)])P(Y_1>S_1)+E[T^i(Y_1)\mid Y_1<S_1]P(Y_1<S_1)\\
&=ET^i(S_1\wedge Y_1)+\sum_{j\ne i}p_{ij}E[T^j(\tilde Y_1)]P(Y_1>S_1)\\
&=ES_1\wedge Y_1\ 1_A(i)+\sum_{j\ne i}p_{ij}t_j(1) \frac{\nu_i}{\nu_i+\lambda^{-1}}\\
&=^2\frac{1_A(i)}{\lambda^{-1}+\nu_i}+\sum_{j\ne i}\frac{q_{ij}}{\nu_i+\lambda^{-1}}t_j(1)\\
\Rightarrow 1_A(i)&=(\lambda^{-1}+\nu_i)t_i(1)-\sum_{j\ne i}q_{ij}t_j(1)
\end{aligned}
$$

1. By the memoryless property of exponential distribution, conditioned that $Y_1>S_1$, the distribution of $Y_1-S_1$ is $Exp(\lambda)$, so let $\tilde Y_1$ be an independent r.v. $\sim Exp(\lambda)$.
2. $ES_1\wedge Y_1=(\lambda^{-1}+\nu_i)^{-1}$.

(b) Derive a set of linear equations for $t_i(n),i\ge 0$.

_Solution_ 
$$
\begin{aligned}
t_i(n)&=E[T^i(Y_1+...+Y_n)]\\
=&E[T^i(Y_1+...+Y_n)\mid Y_1>S_1]P(Y_1>S_1)+E[T^i(Y_1+...+Y_n)\mid Y_1<S_1]P(Y_1<S_1)\\
=&E[T^i(S_1)\mid Y_1>S_1]P(Y_1>S_1)+\sum_{j\ne i}p_{ij}E[T^j(\tilde Y_1+Y_2+...+Y_n)]P(Y_1>S_1)\\
&+E[T^i(Y_1)\mid Y_1<S_1]P(Y_1<S_1)+E[T^i(Y_2+...+Y_n)]P(Y_1<S_1)\\
=&\frac{1_A(i)}{\nu_i+\lambda^{-1}}+\sum_{j\ne i}\frac{p_{ij}}{\nu_1+\lambda^{-1}}t_j(n)+\frac{\lambda^{-1}}{\lambda^{-1}+\nu_i}t_i(n-1)
\end{aligned}
$$
By these one can derive $t_i(n)$.

(c) When $n$ is large, the best $\lambda$ s.t. $t_i(n)$ is a good approximation of $E[T_i(t)]$.

_Solution_ when $n$ is large, pick $\lambda=n/t$, let $S_n=T_1+...+T_n$. Notice $Ee^{isS_n}=(\frac{ist}{n}-1)^{-n}\to e^{ist}$, whence we have $S_n\to_d X$ where $P(X=t)=1$.

5.18  Consider a cts-time Markov chain with $X(0)=0$. Let $A$ denote a set of states without $0$, and set $T=\min\{t>0: X(t)\in A \}$. Suppose $T<\infty$ a.s.. Let $q_i=\sum_{j\in A}q_{ij}$. Let $H=\int_0^T q_{X(t)}dt$ which is called the random hazard.

(a) Find the hazard rate function, $\lim_{h \to 0} P(s<H<s+h\mid H>s)/h$.

_Solution_ Conditioned that $H>s$, consider $\tau$ s.t. $\int_0^\tau q_{X(t)}dt=s$, we have 
$$
\lim_{h \to 0}P(s<H<s+h\mid H>s)/h=Eq_{X(\tau)}
$$
5.19 Consider a cts-time Markov chain with stationary probabilities $p_i$. Let $T$ denote the first time that the chain has been on state $0$ for $t$ consecutive time units. Find $E^0T$.

_Solution_ From equations
$$
\begin{aligned}
E^0T&=tP(S_1>t)+E^0[T\mid S_1<t]P(S_1<t)
\\&=te^{-\nu_0 t}+\sum_{j\ne 0} p_{0j}(E^j T+\nu_0^{-1}-\frac{te^{-\nu_0 t}}{1-e^{-\nu_0 t}})(1-e^{-\nu_0 t})
\\&=\nu_0^{-1}(1-e^{-\nu_0 t})+\sum_{j\ne 0}p_{0j}E^j T(1-e^{-\nu_0 t})
\\\nu_0 E^0 T&=1-e^{-\nu_0 t}+\sum_{j\ne 0}q_{0j}E^jT(1-e^{-\nu_0 t})
\\E^iT&=\nu_i^{-1} +\sum_{j\ne i}p_{ij} E^jT
\\\nu_i E^i T&=1+\sum_{j\ne i}q_{ij} E^j T
\end{aligned}
$$
5.24 Consider two independent $M/M/1$ queue with respective parameters $\lambda_i,\mu_i$ where $\lambda_i<\mu_i$. Suppose they share the same service room whose capacity is $N$. Compute the limiting probability that $(X_1(t),X_2(t))=(m,n)$.

_Sketch of solution_

- If $X_1(t)$, $X_2(t)$ are independent time reversible cts-time Markov chain, so is $(X_1(t),X_2(t))$. After limiting to $\mathcal S=\{(m,n):m+n\le N \}$, it's still a cts-time time reversible Markov chain.
- $q((m,n),(m+1,n))=\lambda_1,q((m,n)(m-1,n))=\mu_1$, so is $X_2$. Then it's easy to compute the limiting probabilities.

5.30 Consider an $M/M/\infty$ queue with desks marked $1,2,3,...$. On arrival, each customer will choose the idle desk with smallest number.

(a) Find the fraction of time that channel $n$ is busy. 

_Solution_ 

_Notations_ The arrival rate is $\lambda$, mean service time is $\mu$.

- If we set the state to be $(i_1,...,i_n)$ where $i_k=1$ when desk $k$ is occupied and $i_k=0$ otherwise, actually we will obtain a cts-time Markov chain which describe a lost $M/M/n$ queue where the customers choose the idle desk with smallest number. For this finite-state Markov chain, we can compute the limit distribution.

  Notice if we set the state space to be this, the chain is **not reversible**.

- Now we set the state to be the number of occupied desk in the first $n$ desks, i.e., $|\underline x|$, we attain a $M/M/n$​ lost queue. By **Erlang's loss formula**, we have 
  $$
  P((1,...,1))=\frac{(\lambda\mu)^n/n!}{\sum_{i=0}^n (\lambda\mu)^i/i!}:=p_n
  $$
  This yields $P((1,...,1,0))=p_{n-1}-p_n$.

  Consider the state (in fact a set of states) "desk $n$ is busy", whose last state can only be $(1,...,1,0)$, so by balanced equation about desk $n$,
  $$
  P((1,...,1,0))\lambda=P(\text{desk n is busy})/\mu
  $$
  So the probability is $\lambda\mu(p_{n-1}-p_n)$.

(b) Find the overflow rate from $n$ to $n+1$,i.e., the arrivals that find the first $n$ occupied, and the corresponding overflow process.

_Solution_ the overflow rate is just $p_n\lambda$, i.e., after the first $n$ desks occupied, a new arrival makes  the first $n+1$ arrival. Notice the overflow process is of course a renewal process, but not necessarily Poisson, since overflows tend to happen in cluster, i.e., upon one overflow, the first $n$ desks are still busy, so another overflow tends to happen soon.

5.34 Consider an ergodic cts-time Markov chain, with transition rates $q_{ij}$ and stationary distribution $p_j$. Let $B\subset S$, and $G:=B^c$. Suppose the chain is in steady state.

(a) $P(X(t)=i\mid X(t)\in B)=p_i/\sum_{j\in B}p_j$.

(b) 
$$
\begin{aligned}
&P(X(t)=i\mid X(t)\in B,X(t^-)\in G)\\
=&\frac{P(X(t)=i,X(t^-)\in G)}{P(X(t)\in B, X(t^-)\in G)}=\frac{\sum_{j\in G}p_j q_{ji}}{\sum_{j\in G}\sum_{k\in B}p_jq_{jk}}
\end{aligned}
$$
(c) For $i\in B$, let $T_i$ denote the time until the process enters $G$ given that the chain starts from state $i$. Let $\tilde F_i(s)=Ee^{-sT_i}$. Then conditioning on the first state to transit,
$$
\begin{aligned}
\tilde F_i(s)&=E[e^{-sT_i}\mid \text{transits into }G]P(\text{transits into }G)+E[e^{-sT_i}\mid \text{transits into }B]P(\text{transits into }B)
\\&=s\nu_i^{-1}\sum_{j\in G}p_{ij}+\sum_{j \in B,j\ne i}(s\nu_i^{-1}+\tilde F_j(s))p_{ij}
\\&=s\nu_i^{-1}+\sum_{j\in B,j\ne i}\tilde F_j(s)p_{ij}
\\\Rightarrow\tilde F_i(s)&=\frac{\nu_i}{\nu_i+s}[\sum_{j\in B}\tilde F_j(s)p_{ij}+\sum_{j\in G}p_{ij}]
\end{aligned}
$$
(d) in steady state, the transitions between two states should be at the same rate, so 
$$
\sum_{i\in G}\sum_{j\in B} p_i q_{ij}=\sum_{i\in B}\sum_{j\in G}p_i q_{ij}
$$
(e) From (c) and (d) we have 
$$
\begin{aligned}
(\nu_i+s)\tilde F_i(s)&=\sum_{j\in B}\tilde F_j(s)\nu_i p_{ij}+\sum_{j\in G}\nu_i p_{ij}\\
\sum_{i\in B}(\nu_i+s)\tilde F_i(s)p_i&=\sum_{i\in B}\sum_{j\in B}\tilde F_j(s)\nu_i p_{ij}p_i+\sum_{i\in B}\sum_{j\in G}\nu_i p_{ij}p_i
\\s\sum_{i\in B}p_i \tilde F_i(s)+\sum_{i\in B}\tilde F_i(s)p_i \nu_i &=\sum_{i\in B}\sum_{j\in B}\tilde F_j(s)q_{ij}p_i+\sum_{i\in G}\sum_{j\in B}p_i q_{ij}\\
s\sum_{i\in B}p_i \tilde F_i(s)&=\sum_{i\in G}\sum_{j\in B}p_i q_{ij}(1-\tilde F_j(s))
\end{aligned}
$$
(f) Given that the process has just entered $B$ from $G$, let $T_\nu$ denote the time until it leaves $B$. Then 
$$
Ee^{-sT_\nu}=\sum_{i\in B}\frac{\sum_{j\in G}p_j q_{ji}}{\sum_{j\in G}\sum_{k\in B}p_jq_{jk}}\tilde F_i(s)
$$
(g) From (e) we have 
$$
\begin{aligned}
&\sum_{j\in G}\sum_{k\in B} p_j q_{jk}Ee^{-sT_\nu}=\sum_{i\in B}\sum_{j\in G}p_j q_{ji}\tilde F_i(s)=\sum_{i\in B}\sum_{j\in G}p_j q_{ji}-s\sum_{i\in B}p_i \tilde F_i(s)
\\\Rightarrow &\sum_{i\in B}\sum_{j\in G}p_j q_{ji}(1-Ee^{-sT_\nu})=s\sum_{i\in B}p_i \tilde F_i(s)
\\\Rightarrow &\frac{\sum_{i\in B}\sum_{j\in G}p_j q_{ji}(1-Ee^{-sT_\nu})}{s}=\sum_{i\in B}p_i \tilde F_i(s)
\end{aligned}
$$
let $s\to 0$, we have by DCT,
$$
\sum_{i\in B}\sum_{j\in G} p_j q_{ji} ET_\nu=\sum_{i\in B}p_i
$$
(h) Given that the chain falls into $B$, let $T_x$ be the time until it leaves $B$, then 
$$
\begin{aligned}
Ee^{-sT_x}&=\sum_{i\in B}\tilde F_i(s)\frac{p_i}{\sum_{j\in B}p_j}=\frac{1-Ee^{-sT_\nu}}{sET_\nu }
\end{aligned}
$$
(i) By Laplace inverse transform, 

> [!Tip]
> $$
> \bigg(\frac{1-\hat f(s)}{s} \bigg)^\vee=1-\int_0^t f(u)du
> $$

$$
P(T_x\le t)=\int_0^t\frac{P(T_\nu>s)}{ET_\nu}ds
$$

(j) then we have 
$$
P(T_x>t)=\int_t^\infty \frac{P(T_\nu>s)}{ET_\nu}ds
$$
integrate w.r.t. $t$ we have 
$$
ET_x=\frac{ET_\nu^2}{2ET_\nu}\ge\frac{ET_\nu}{2}
$$
_Remark_ If we consider a visit to $B$ as a renewal, $T_\nu$ is the interarrival time and $T_x$ is the residual time/age. By this, (g) has a good interpretation : transition rate into $B$= probability of staying in $B$/mean length of one stay in $B$. This is just the SLLN for renewal theorem, since transition rate into $B$ is just the transition rate (there are only two states), and RHS=1/mean length of an interarrival time.

_Remark_ Notice that if we collapse a subset of state into a state, the resulting process is **not Markov** in general.

5.35 Consider a renewal process whose interarrival distribution $F$ is given by $\bar F(x)=pe^{-\lambda_1 x}+qe^{-\lambda_2 x}$, where $q=1-p$. Compute $EN(t)$.

_Solution_ This has a nice interpretation: Imagine at each renewal, a coin that lands heads with $p$, will be flipped, and if it's a head the next interarrival is $Exp(\lambda_1)$ and otherwise $Exp(\lambda_2)$. Let $R(t)$ be the type of interarrival at time $t$. Then $R(t)$ is a cts-time Markov chain in steady state
