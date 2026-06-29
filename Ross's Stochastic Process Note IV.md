## Chapter 5 Continuous-time Markov chains

### 5.2 Continuous-time Markov Chains

**Definition** $X(t)$ with $\mathcal S=\mathbb N$ is a **continuous-time Markov chain** if $\forall s,t\ge 0,i,j\in \mathcal S$, we have $P(X(t+s)=j\mid X(s)=i,X(u)=u,0\le u<s)=P(X(t+s)=j\mid X(s)=i)$, i.e., conditioned on $s$, the future process $X(t),t>s$ is independent of the past $X(u),0\le u<s$.

_Remark_ We assume that $P(X(t+s)=j\mid X(s)=i)$ is independent of $s$, i.e., $X(t)$ is stationary.

Denote the waiting time between some two transitions by $\tau$, by Markovian property we have $P(\tau>s+t\mid \tau>s)=P(\tau>t)$, so $\tau$ is exponentially distributed. 

By this, we can see the chain in this way: as it enters state $i$, it waits for $T\sim Exp(\nu_i)$ ($0\le \nu_i<\infty$) and transits to state $j$ with $p_{ij}$.($\sum_{j\ne i}p_{ij}=1$). Waiting times are independent of each other.

_Remark_ A continuous-time Markov chain is said to be **regular** if w.p.1. the number of transitions in any finite length of time is finite. We assume the chains are regular. But the chain can be nonregular. Let $p_{i,i+1}=1$ and $v_i=i^2$, then since $\sum_i 1/i^2<\infty$, with positive probability the chain can transit for infinite times in finite time.

**Definition** Call $q_{ij}=\nu_ip_{ij}$ the **transition rate** from $i$ to $j$, since it's the rate at which the process transits into $j$ from $i$. Meanwhile, let $p_{ij}(t)=P(X(t+s)=j\mid X(s)=i)$, and $p_{ij}'(t)$ be the corresponding density.

### 5.3 Birth and Death Processes

**Definition** A cts-time Markov chain with states $\mathcal S=\mathbb N$, with $q_{ij}=0\ \forall|i-j|>1$ is called a **birth and death process**. Consider the states as the scale of some population, then if the state increases by $1$, we say a birth occurs and if the state decreases by $1$ we say a death occurs. 

We can consider the chain in the following way: whenever there are $i$ people, a birth will occur in $T\sim Exp(\lambda_i)$ and a death will occur in $T'\sim Exp(\mu_i)$ independently, with $\lambda_i=q_{i,i+1}$ (**birth rates**) and $\mu_i=q_{i,i-1}$ (**death rates**). The reason is that $T\wedge T'\sim Exp(\lambda_i+\mu_i)$ and $P(T<T')=\lambda_i/(\lambda_i+\mu_i)=p_{i,i+1}$.

**Example 5.3(A) Two Birth and Death Processes** 

(i) M/M/s queue. Suppose there are $s$ service desks and customers arrive $\sim P_\lambda(t)$ and the service time are i.i.d. $\sim Exp(\mu)$. Let $X(t)$ denote the number of people in the system, $X(t)$ is a birth and death process with $\lambda_n=\lambda$ and $\mu_n=(n\wedge s)\mu$.

(ii) Linear growth model with immigration: $\mu_n=n\mu$ and $\lambda_n=n\lambda+\theta$. $\theta$ represents immigration.

**Definition** A birth and death process is said to be a **pure birth process** if $\mu_n=0\forall n$.

_Example_ Poisson process is pure. 

_Example_ Consider a population where there is no death and everyone gives birth independently $\sim Exp(\lambda)$, then the number of population is also pure with $\lambda_n=n\lambda$, which is called a **Yule process**.

> [!IMPORTANT]
>
> Consider a Yule process with $X(0)=1$, and $T_i$ be the waiting times from state $i$ to $i+1$. Then $T_i$ are independent and $T_i\sim Exp(i\lambda)$. 
>
> 1. The distribution of $S_n=T_1+...+T_n$ can be determined by induction:
>    $$
>    \begin{aligned}
>    P(S_1<t)&=1-e^{-\lambda t}\\
>    P(S_2<t)&=\int_0^t (1-e^{-2\lambda(t-s)})\lambda e^{-\lambda s}ds=(1-e^{-\lambda t})^2 \\
>    \text{when } P(S_n<t)&=(1-e^{-\lambda t})^n\text{:}\\
>    P(S_{n+1}<t)&=\int_0^t P(S_{n+1}<t\mid S_n=s)dF_{S_n}(t)\\
>    &=\int_0^t(1-e^{-(n+1)\lambda(t-s)})d(1-e^{\lambda s})^n
>    \\&=(1-e^{\lambda t})^{n+1}
>    \end{aligned}
>    $$
>    So $p_{1j}(t)=(1-e^{-\lambda t})^{j-1}-(1-e^{-\lambda t})^j=e^{-\lambda t}(1-e^{-\lambda t})^{j-1}$, $X(t)\sim G(e^{-\lambda t})$. Moreover, if $X(0)=i$, $X(t)$ is the sum of $i$ geometric r.v.'s, i.e., negative binomial distribution.
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

**Example 5.3(B)** Consider a Yule process with $X(0)=1$, and let $A(t)=a_0+t+\sum_{i=1}^{X(t)-1}(t-S_i)$ be the sum of ages of all individuals, where $a_0$ is the age of the first individual at $t=0$. Conditioned on $X(t)$,
$$
E[A(t)\mid X(t)=n+1]=a_0+t+n\int_0^t (t-s)\frac{\lambda e^{-\lambda (t-s)}}{1-e^{-\lambda t}}ds=a_0+t+n\frac{1-e^{-\lambda t}-\lambda te^{-\lambda t}}{\lambda(1-e^{-\lambda t})}
$$
So 
$$
E[A(t)]=E[E[A(t)\mid X(t)=n+1]]=a_0+t+(e^{\lambda t}-1)\frac{1-e^{-\lambda t}-\lambda te^{-\lambda t}}{\lambda(1-e^{-\lambda t})}=a_0+\lambda^{-1}(e^{\lambda t}-1)
$$
Or use $A(t)=a_0+\int_0^t X(s)ds$ and take expectation.

**Example 5.3(c) A simple epidemic model** 

_Setting_ Consider a population of $m$ individuals. At time $0$, one is infected. In any time interval $h$, any given infected person will cause any given susceptible to be infected with probability $\alpha h+o(h)$. As one is infected, it's infected forever. 

Let $X(t)$ denote the number of infected individuals in the population at time $t$. $X(t)$ is a pure birth process, with $\lambda_n=((m-n)\vee 0)n\alpha$. Let $T$ be the time until the total population is infected, i.e., $T=\sum_{i=1}^{m-1} T_i$. $T_i\sim Exp(\lambda_i)$ are independent, so $ET=\sum_{i=1}^{m-1} \frac{1}{\alpha i(m-i)}$ and $var(T)=\sum_{i=1}^{m-1}\frac{1}{(\alpha i(m-i))^2}$.

### 5.4 The Kolmogorov Differential Equations

> **Lemma 5.4.1** (i)$p_{ii}(t)=1-\nu_i t+o(t)$ (ii) $p_{ij}(t)=q_{ij}t+o(t)$.
>
> <font color='red'>_proof of Lemma 5.4.1_</font> 
>
> (i) The probability of two or more jumps is infinitesimal. 
>
> Let $N(t)$ be the number of jumps during $[0,t]$ given $X(0)=i$ and $T_1$ be the first holding time, then $T_1\sim Exp(\nu_i)$. Let $K$ be the state entered at the first jump, so that $P(K=k)=p_{ik}$. Then 
> $$
> P^i(N(t)\ge 2)=\sum_{k\ne i}\int_0^t \nu_i e^{-\nu_i s}p_{ik}(1-e^{-\nu_k(t-s)})ds=\sum_{k\ne i}t\int_0^1\nu_i e^{-\nu_i ut}p_{ik}(1-e^{-\nu_k(1-u)t})
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
_Remark_ They are called **backward equations** since in computing the distribution of state at time $t+h$, we conditioned on the state back at time $h$.

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
\\\Rightarrow EX(t+h)&=EX(t)+(\lambda p-\mu)X(t)h+o(h)
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

Recall theorems for semi-Markov process, we have: if the corresponding discrete Markov chain is positive-recurrent with invariant distribution $\pi$,  
$$
p_j:=\lim_{t \to \infty} p_{ij}(t)=\frac{\pi_j/\nu_j}{\sum_i \pi_i/\nu_i}
$$
Since $\pi_j$ is the unique solution to $\pi_j=\sum_i \pi_i p_{ij},\sum_j \pi_j=1$, $p_j$ is the unique solution to $p_j=\sum_i p_i q_{ij},\sum_{j} p_j=1$. This gives us ways to compute this. 

Another method for computing this is worth mentioning: Consider forward equations $p_{ij}'(t)=\sum_{k\ne j}q_{kj}p_{ik}(t)-\nu_j p_{ij}(t)$. Suppose $\lim_{t \to \infty} p_{ij}(t)$ exists, $p_{ij}'(t)\to 0$, then $\sum_{k\ne j} q_{kj}p_k=\nu_j p_j$.

_Remark_ According to properties of semi-Markov process, $p_j$ is also the long-run proportion of the chain staying at state $i$.

_Remark_ If the initial distribution is $p_j$, the chain is stationary, i.e., $\sum_i p_i p_{ij}(t)=p_j\forall t$.

_proof_ by DCT,
$$
\sum_i p_ip_{ij}(t)=\sum_i \lim_{s \to \infty}p_{ki}(s)p_{ij}(t)=\lim_{s \to \infty}\sum_i p_{ki}(s)p_{ij}(t)=\lim_{s \to \infty} p_{kj}(s+t)=p_j
$$
_Remark_ Like what we have done for reversed Markov chain, this has a nice interpretation:

In interval $(0,t)$, transitions into j and transitions out of $j$ differ at most $1$. So in the long run the rate at which transitions into state $j$ occur must equal the rate at which transitions out of state $j$ occur. The former is $\sum_{i\ne j} p_i q_{ij}$, and the latter is $p_j\nu_j$. By this, the equations are also called "balance equations".

**Example Limiting probabilities for a birth and death process** 
$$
\begin{aligned}
\lambda_0p_0&=\mu_1p_1\\
(\lambda_n+\mu_n)p_n&=\mu_{n+1}p_{n+1}+\lambda_{n-1}p_{n-1}\Rightarrow \lambda_n p_n=\mu_{n+1}p_{n+1}+\lambda_{n-1}p_{n-1}-\mu_np_n\\
\Rightarrow \lambda_np_n&=\mu_{n+1}p_{n+1}\\
\Rightarrow p_n&=\frac{\lambda_{n-1}...\lambda_0}{}
\end{aligned}
$$
