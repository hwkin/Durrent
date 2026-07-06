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

- The corresponding discrete Markov chain for reversed process has transition probability $p_{ij}^*=\frac{\pi_j p_{ij}}{\pi_i}$. Let $q_{ij}^*=\nu_i p_{ij}^*$, we have $p_i q_{ij}^*=p_j q_{ji}$
