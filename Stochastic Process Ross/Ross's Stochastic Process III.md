## Chapter 4 Markov Chain

### 4.1 Introduction and Examples

**Definition** A stochastic process $X_n$ is $\mathbb Z_{\ge 0}$-valued, satisfying $P(X_{n+1}=j\mid X_n=i_n,...,X_0=i_0)=p_{ij}$, is called a **Markov chain**. The process satisfies that, the conditional distribution of $X_{n+1}$ given $X_0,...,X_n$ only depends on $X_n$, which is called **Markovian property**. $p_{ij}$ is the probability that the process will make a transition into state $j$ when in state $i$. The probabilities satisfies $p_{ij}\ge 0\forall i,j$ and $\sum_{j=0}^\infty p_{ij}=1\forall i$. Let $P=(p_{ij})$.

**Example 4.1(A) The M/G/1 queue** Denote the length of queue $X(t)$, notice $X(t)$ is not Markov, since given $\mathcal F(s)_{s\le t}$, to make the prediction, we need to consider the arrival (by memoryless property, this doesn't depend on the past, so it makes no difference) and how long the current person has been serviced (this is not memoryless).

Define $X_n$ to be the length of queue when the $n$th person leaves, $n\ge 1$, then $X_n$ is Markov. To see this, let $Y_n$ denote the number of persons that enter the system during the service time of $n$th person, we have 
$$
X_{n+1}=\left\{\begin{aligned}&X_n-1+Y_n,&X_n>0\\&Y_n,&X_n=0\end{aligned}\right.
$$
Notice $Y_n$ is independent of $X_1,...,X_{n-1}$, so $X_n$ is indeed Markov. The transition probability is given by 
$$
\begin{aligned}
p_{0,j}&=\int_0^\infty e^{-\lambda x}\frac{(\lambda x)^j}{j!}dG(x)
\\p_{i,j}&=\int_0^\infty e^{-\lambda x}\frac{(\lambda x)^{j-i+1}}{(j-i+1)!}dG(x),\ j\ge i-1,i\ge 1
\\p_{ij}&=0,\text{otherwise}
\end{aligned}
$$
**Example 4.1(B) The G/M/1 queue** Suppose the service time is $Exp(\mu)$. Let $X_n$ be the length of queue by the $n$th arrival (including the new), $X_n$ is Markov since the service time is memoryless. Notice as long as the queue is not empty, between two arrival, the customers leave as a Poisson process. But when the queue is empty. So the transition probability is given by
$$
\begin{aligned}
p_{i,i+1-j}&=\int_0^t \frac{(\mu t)^j}{j!}e^{-\mu t}dG(t),\ j=0,...,i-1
\\p_{i,1}&=\int_0^t\sum_{j=i}^\infty \frac{(\mu t)^j}{j!}e^{-\mu t}dG(t)
\end{aligned}
$$
**Example 4.1(c) General random walk** Let $X_i$ be i.i.d., with $P(X_i=j)=a_j,j=-1,0,1$. Then $S_n$ is Markov with $P_{ij}=a_{j-i},|i-j|\le 1; 0,$otherwise.

**Example 4.1(D) Absolute value of SRW** when $a_1=1-a_{-1}=p\in(0,1)$, the random walk is said to be simple. Surprisingly $|S_n|$ is Markov. The proof is as follows:

**Proposition 4.1.1** If $S_n$ is a SRW, then $P(S_n=i\mid|S_n|=i,...,|S_1|=i_1)=p^i/(p^i+q^i)$.

<font color='red'>_proof of Proposition 4.1.1_</font> Define $j$ to be the last visit time to $0$. Then $S_j=0$. Now it suffices to look at $S_{j+1},...,S_{j+n}$. Since there are only two cases that differ up to sign, $S_n=i$ or $S_n=-i$, whose probability is respectively $p^{(n-j)/2+i/2}q^{(n-j)/2-i/2}:=p_1$ and $q^{(n-j)/2+i/2}p^{(n-j)/2-i/2}:=p_2$, the probability we concerns is exactly $p_1/(p_1+p_2)=p^i/(p^i+q^i)$.

In this case, we have
$$
P(|S_{n+1}|=i+1\mid |S_n|=i,...,|S_1|=i_0)=P(S_{n+1}=i+1\mid S_n=i)\frac{p^i}{p^i+q^i}+P(S_{n+1}=-i-1\mid S_n=-i)\frac{q^i}{p^i+q^i}=\frac{p^{i+1}+q^{i+1}}{p^i+q^i}
$$
So the transition probability is given by 
$$
p_{i,i+1}=\frac{p^{i+1}+q^{i+1}}{p^i+q^i}=1-p_{i,i-1},i>0; p_{0,1}=1,i=1
$$

### 4.2 Chapman-Kolmogorov Equations and classification of states

Now introduce some notions.

The **$n$-step transition probability** is defined by $p_{i,j}^n=P(X_{n+m}=j\mid X_m=i)$. The **Chapman-Kolmogorov equation** is $p_{ij}^{n+m}=\sum_{k=0}^\infty p_{ik}^np_{kj}^m$, which is attained by conditioning on $X_n$. If we let $P^{(n)}=(p_{ij}^n)$, indeed $P^{(n)}=P^n$ by this equation.

state $j$ is **accessible** from $i$ if $p_{i,j}^n>0\exists n$, and state $j$ and $i$ are **communicate** if they are accessible to each other. We write $i\leftrightarrow j$ for this.

**Proposition** Communication is an equivalence relation.

By this, we can divide the states into classes. The chain is **irreducible** if there is only one class. 

State $i$ is said to have **period** $d$ if $d=\gcd(n:p_{ii}^n\ne 0)$. If $d=1$, the state is said to be **aperiodic**. Denote the period of $i$ by $d(i)$. Actually, $d(i)$ is a class property:

**Proposition 4.2.2** If $i\leftrightarrow j$, then $d(i)=d(j)$.

<font color='red'>_proof of Proposition 4.2.2_</font> Since $i\leftrightarrow j$, pick $p_{ij}^m,p_{ji}^n\ne 0$, then $p_{ii}^{n+m}\ge p_{ij}^mp_{ji}^n>0$ and $p_{ii}^{n+d(j)+m}\ge p_{ij}^mp_{jj}^{d(j)}p_{ji}^m>0$. So $d(i)\mid n+m,n+d(j)+m$, so $d(i)\mid d(j)$. Meanwhile $d(j)\mid d(i)$, so they are equal.

Let $f_{ij}^n$ denote the probability that starting from $i$, the first time to visit $j$ is the $n$th step. Let $f_{ij}=\sum_{n=1}^\infty f_{ij}^n$, then $f_{ij}$ denotes the probability that starting from $i$, the chain ever visited to $j$. If $i\ne j$, $f_{ij}>0$ iff $j$ is accessible from $i$. If $i=j$, we say $i$ is recurrent if $f_{ii}=1$ and is **transient** otherwise.

**Proposition 4.2.3** state $j$ is recurrent iff $\sum_{n=1}^\infty p_{jj}^n=\infty$.

<font color='red'>_proof of Proposition 4.2.3_</font> Notice if $j$ is recurrent, then the chain must return to $i$ , and at this moment it restarts. So it will return infinitely many times a.s.. On the other hand, if $j$ is transient, then the number of return follows $G(f_{jj})$, which has finite mean. So $j$ is recurrent iff the number of returns has infinite mean. 

Let $1_n$ denotes the indicator function of the event that the chain visits $j$ at the $n$th step, then the number of visits $N$ has 
$$
EN=E\sum_{n=1}^\infty 1_n=\sum_{n=1}^\infty E1_n=\sum_{n=1}^\infty p_{jj}
$$
which completes our proof. 

_Corollary_ If the Markov chain has finite states, then there must be a recurrent state.

**Corollary 4.2.4** If $i$ is recurrent and $i\leftrightarrow j$, then $j$ is recurrent.

<font color='red'>_proof of Corollary 4.2.4_</font> Since $i\leftrightarrow j$, pick $p_{ij}^m>0,p_{ji}^n>0$. So by **Proposition 4.2.3**
$$
\sum_{s=1}^\infty p_{jj}^{m+n+s}\ge \sum_{s=1}^\infty p_{ji}^np_{ii}^sp_{ij}^m=\infty
$$
**Example 4.2(A) SRW** Now we consider the transience and recurrence of states for a SRW. Since all states communicates, they will be all recurrent/transient. So let's consider $f_{00}$, and notice its period is 2,
$$
f_{00}=\sum_{n=1}^\infty p_{00}^{2n}=\sum_{n=1}^\infty \binom{2n}{n} p^n(1-p)^n
$$
when $n$ is large, by Stirling's formular the summands $\sim (4p(1-p))^n/\sqrt{\pi n}$. So the series converges when $p\ne 1/2$ and diverges when $p=1/2$. This corresponds that, when $p=1/2$ SRW is recurrent and otherwise transient.

Moreover, for a symmetric SRW in d dimension, when $d=1,2$ all states are transient and when $d>2$ all states are transient.

**Corollary 4.2.5** If $i\leftrightarrow j$ and $j$ is recurrent, then $f_{ij}=1$.

<font color='red'>_proof of Corollary 4.2.5_</font> Since $i\leftrightarrow j$ and $j$ is recurrent, $i$ is recurrent. If $f_{ij}<1$, then a.s. after the chain visits $i$ for some time the chain never visits $j$. But $j$ is also recurrent, which leads to a contradiction.

### 4.3 Limit Theorems

Let $N(t)$ denote the number of visits to $j$ by time $t$, $t\in\mathbb Z_{>0}$. If $j$ is recurrent, let the chain starts from $j$, $N(t)$ is a renewal process with interarrival distribution ${f_{jj}^n}$. If $i\leftrightarrow j$, then starts the chain from $i$, $N(t)$ is a delayed renewal process, whose initial distribution is $f_{ij}^n$. In this way, we can apply limit theorems for renewal process for Markov chain.

Let $\mu_{jj}$ be the expected interarrival time. Then $\mu_{jj}=\sum_{n=1}^\infty nf_{jj}^n$ when $j$ is recurrent. When $j$ is transient, then $F(\infty)<1$, so $\mu_{jj}=\infty$.

**Theorem 4.3.1** If $i\leftrightarrow j$, then 

(i) Starting from $i$, w.p.1 $N(t)/t\to 1/\mu_{jj}$.

(ii) $\lim_{n \to \infty} \sum_{k=1}^{n} p_{ij}^k/n=1/\mu_{jj}$.

(iii) If $j$ is aperiodic, $\lim_{n \to \infty} p_{ij}^n=1/\mu_{jj}$

(iv) If $j$ is periodic, $\lim_{n \to \infty} p_{jj}^{nd}=d/\mu_{jj}$.

<font color='red'>_proof of Theorem 4.3.1_</font> Just notice two facts: (i) $EN(n)=\sum_{i=1}^{n} p_{ij}^n$ (ii) The process has lattice distribution.

**Definition** If state $j$ is recurrent, we say it's **positive recurrent** if $\mu_{jj}<\infty$ and **null recurrent** if $\mu_{jj}=\infty$. By **Theorem 4.3.1**, if we define $\pi_j=\lim_{n \to \infty} p_{jj}^{nd(i)}$, then $\pi_j>0$ iff $j$ is positive recurrent. 

**Proposition 4.3.2** Positive/null recurrence is a class property. 

<font color='red'>_proof of Proposition 4.3.2_</font> If $i\leftrightarrow j$ and $i$ is null recurrent, and we can pick $p_{ij}^n>0,p_{ji}^m>0$. So $p_{ii}^{n+s+m}\ge p_{ij}^np_{jj}^sp_{ji}^m$. Since $LHS\to 0$, we have $p_{jj}^s\to 0$. So $j$ is recurrent. 

**Definition** a positive recurrent, aperiodic state is called **ergodic**.

**Definition** A probability distribution $P_j$ is said to be stationary for a Markov chain if $P_j=\sum_{i=0}^\infty P_ip_{ij}$. The name follows from the fact that, if $X_0$ has law $P_j$, then $X_n$ also has law $P_j$ for all $n$. And by Markov property, the chain has stationary increments.

**Theorem 4.3.3** An irreducible aperiodic Markov chain belongs to one of the two following classes:

(i) All states are null recurrent/transient. In this case, $p_{ij}^n\to 0\forall i,j$, and there is no stationary distribution.

(ii) All states are positive recurrent. In this case, $\pi_j=\lim_{n \to \infty} p_{ij}^n>0$ is the unique stationary distribution.

<font color='red'>_proof of Theorem 4.3.3_</font>

First prove (ii). 

- $\pi_j$ is a probability measure, i.e., $\sum_{j=0}^\infty \pi_j= 1$. To prove this, notice $\sum_{j=0}^{M}p_{ij}^n\le 1$. Push $n$ to limit, then push $M$ to limit, we have $\sum_{j=0}^\infty \pi_j\le 1$. Equality holds, but we shall prove later.

- $\pi_j$ is stationary. Since $p_{ij}^{n+1}\ge\sum_{k=0}^{M}  p_{ik}^np_{kj}$, push $n$ to limit, then push $M$ to limit, we have $\pi_{j}\ge \sum_{k=0}^\infty \pi_k p_{kj}$. Equality must hold for all $j$, since otherwise we have 
  $$
  \sum_{j=0}^\infty \pi_j>\sum_{j=0}^\infty\sum_{k=0}^\infty\pi_k p_{kj}=_{\text{Fubini}}\sum_{k=0}^\infty\sum_{j=0}^\infty\pi_k p_{kj}=\sum_{k=0}^\infty \pi_k
  $$
  which is impossible.

- Now $P_j:=\pi_j/\sum_{k=0}^\infty \pi_k$ is exactly a stationary distribution, so existence hold. Now assume $P_j$ to be an arbitrary stationary distribution, and set $X_0\sim P_j$, we have 
  $$
  P_j=P(X_n=j)=\sum_{i=0}^\infty p_{ij}^n P_i\ge \sum_{i=0}^{M}p_{ij}^n P_i\to_{n\to\infty}\sum_{i=0}^{M}\pi_j P_i\to_{M\to\infty}\sum_{i=0}^\infty \pi_j P_i
  $$
  i.e., $P_j\ge \sum_{i=0}^\infty \pi_j P_i=\pi_j$. On the other hand,
  $$
  P_j=\sum_{i=0}^\infty p_{ij}^n P_i\le \sum_{i=0}^{M} p_{ij}^n P_i+\sum_{i=M+1}^\infty P_i\to \sum_{i=0}^{M} \pi_j P_i+\sum_{i=M+1}^\infty P_i
  $$
  Since $M$ is arbitrary and $\sum P_i<\infty$, let $M\to\infty$, we have the inverse inequality. So $P_j=\pi_j$. So $\pi_j$ is indeed a probability measure, and it's unique.

For (i), notice if $P_j$ is a stationary distribution, then $P_j\le \sum_{i=0}^\infty \pi_j P_j+\sum_{i=M+1}^\infty P_i$ also holds, but $\pi_j=0$ indicates $P_j\le \sum_{i=M+1}^\infty P_i$. Let $M\to\infty$, $P_j=0$. So there isn't a stationary distribution. 

_Intuition_ For (ii), we can start from the case that $X_i$ has finite states. Suppose $X_0$ has distribution $P_j$, let $v=(P_0,...,P_n)^T$, then if $P^nv$ converges, we have $\lim_{n \to \infty} P^nv=P\lim_{n \to \infty} P^nv$, so $\lim_{n \to \infty} P^n v$ the limit distribution is a stationary distribution. 

_Remark_ When $X_i$ is periodic, there is still a unique probability measure $\pi_j$ s.t. $\pi_j=\sum_i \pi_i p_{ij}$. But since $\lim_{n \to \infty} p_{ij}^n$ may not exist, it's no more the "limit distribution". Instead, it's the long-run proportion of time the chain is at state $j$.

<font color='red'>_proof_</font> Suppose the chain starts at $0$. Let $\tau$ be the return time, then $E\tau<\infty$.

Let $Y_j=\sum_{n=0}^{\tau -1}1_{X_n=j}$. Then by renewal-reward theorem, $\pi_j=EY_j/E\tau$.

- $\sum_j \pi_j=\sum_j EY_j/E\tau=1$.
- $EY_j=p_{ij}EY_i$.

To attain the stationary distributions, we can solve the equations directly:

**Example 4.3(A) Limiting Probabilities for the Embedded M/G/1 queue** Consider the embedded Markov chain defined in **Example 4.1(A)**. Let $a_j=\int_0^\infty e^{-\lambda x}\frac{(\lambda x)^j}{j!} dG(x)$, then the transition probability is given by $p_{0j}=a_j;p_{ij}=a_{j-i+1}\forall i>0,j\ge i-1; p_{ij}=0,j<i-1$. 

Let $\rho=\sum_j ja_j$ the mean arrival during a service time. We have $\rho=\lambda ES$ where $S$ is the service time. Now we prove this chain is positive recurrent when $\rho<1$.

To prove this, we solve the equation $\pi_j=\sum_i \pi_i p_{ij}$:

Define $\pi(s)=\sum_{j=0}^\infty \pi_j s^j$ and $A(s)=\sum_{j=0}^\infty a_j s^j$. So 
$$
\begin{aligned}
\pi(s)&=\sum_{j=0}^\infty \pi_js^j=\sum_{j=0}^\infty (\pi_0a_j+\sum_{i=1}^{j+1}\pi_ia_{j-i+1})s^j
\\&=\pi_0A(s)+\sum_{i=1}^\infty\sum_{j=0}^\infty\pi_ia_{j-i+1}s^j
\\&=\pi_0 A(s)+(\pi(s)-\pi_0)A(s)/s
\\\Rightarrow\pi(s)&=\frac{(s-1)\pi_0 A(s)}{s-A(s)}
\end{aligned}
$$
Notice $A(1)=1, A'(1)=\rho$, so by L 'hospital rule, $\pi(1)=\pi_0/(1-\rho)$. So the solution exists iff $\rho<1$, and $\pi_0=1-\rho$, $\pi_j$ can be solved from $\pi(s)=(s-1)(1-\rho)A(s)/(s-A(s))$.

**Example 4.3(B) Limiting probabilities form the Embedded G/M/1 queue** Consider the embedded Markov chain defined in **Example 4.1(B)**. The technique is also to solve the equation, but for this problem it guesses the form is like $\pi_k=c\beta^k$. 

**Example 4.3(c) The age of a renewal process** Consider a renewal process whose interarrival time has law $P_j$ (lattice). Let $X_n$ be the age of current cycle, then $X_n$ is indeed a Markov chain. The transition probability $p_{i1}=P(X_n=1\mid X_{n-1}=i)=P_i/\sum_{j=i}^\infty P_j$ and $p_{i,i+1}=1-p_{i,1}$. The stationary distribution, by solving the equations, is given by $\pi_i=P(X\ge i)/EX$. Notice this corresponds to the age distribution of the renewal process.

Also, we can reason about the initial distribution directly:

**Example 4.3(D)** Suppose there is a population. In each time cycle, everyone dies with probability $p$ independently, and there are new members $\sim P(\lambda)$.Denote $X_n$ to be the number of members, $X_n$ is a Markov chain. 

To determine the stationary distribution, guess $X_0\sim P(\mu)$. Then $X_1\sim P((1-p)\mu+\lambda)$. To make it stationary, $\mu=(1-p)\mu+\lambda$, i.e., $\mu=\lambda/p$.

**Example 4.3(E) The Gibbs Sampler** Let $p(x_1,...,x_n)$ be the joint probability mass function of $(X_1,...,X_n)$. Commonly it's difficult to sample a random vector, but easy to sample some $X_i$ given $X_{j},j\ne i$ with the conditional distribution. Gibbs sampler applies this idea and it works as follows:

- Sample $X^0=(x_1^0,...,x_n^0)$ where $P(X=X^0)>0$.
- Fix $X_2,...,X_n$, sample $X_i$ and update its value. Continue this process until $X_n$ is updated, and say the new vector $X^1$.
- Continue this process to get $X^2,...$.

Now claim the stationary distribution is $p$. It's easy to verify each intermediate r.v. has distribution $p$ during the generation of $X^1$. Hence when the chain is aperiodic and irreducible, the limit distribution is exactly $p$.

**CLT for visits to 0** Suppose $X_n$ is a irreducible, positive recurrent Markov chain with stationary distribution $\pi$. Let $N$ denote the number of transitions between successive visits to state $0$. By the CLT for renewal process, the visits to $0$ by time $n$ approximately $\sim \mathcal N(n/EN,nvar N/[EN]^3)$ Now let's determine $EN^2$. 

Regard visits to 0 as renewals, we get a renewal process. Now reward the process its excess at any time. Then $ER=E[ER\mid N]=EN+N-1+...+1=\frac{1}{2}(EN^2+EN)$. By renewal reward theorem, $ER/EN$ is exactly the long-run reward rate.

Meanwhile, we can calculate the reward rate in another way. denote $T_i$ to be the time from $i$ to the first new visit to $0$. The reward by time $n$ is just $\sum_{i=1}^{n} T_i$, so $\sum_{i=1}^{n} T_i/n\to ER/EN$. Shift our view from the time to the state, then if we denote $\mu_{i0}$ to be the mean transitions from $i$ to $0$, then the long-run transitions from the current state to $0$ are $\sum_i \pi_i \mu_{i0}$. $\mu_{i0}$ can be solved from linear equations $\mu_{i0}=1+\sum_j \mu_{j0}p_{ij}$.

So, $\frac{1}{2} (\frac{EN^2}{EN}+1)=\sum_i \pi_i\mu_{i0}$.

**Example 4.3(F)** Consider a two-state Markov chain with $p_{00}=\alpha=1-p_{01}$, and $p_{10}=\beta=1-p_{11}$. Then $\pi_0=\beta/(1-\alpha+\beta)=1-\pi_1$, $\mu_{00}=1/\pi_0, \mu_{10}=1/\beta$. By above argument we have $varN=(1-\beta+\alpha\beta-\alpha^2)/\beta^2$. So the visits to $0$ is nearly normal with mean $n\pi_0$ and variance $n\pi_0^3 varN$. When $\alpha=\beta=1/2$, $N\sim \mathcal N(n/2, n/4)$.

### 4.4 Transitions among classes, the Gambler's ruin problem and mean times in transient states.

**Proposition 4.4.1 Closeness of recurrent class** Let $R$ be a recurrent class of states. If $i\in R$ but $j\notin R$, then $p_{ij}=0$.

<font color='red'>_proof of Proposition 4.4.1_</font> Notice if $p_{ij}>0$, then $p_{ji}^n=0\forall n$ since $i\nleftrightarrow j$. In this case, $i$ can jump to $j$, but can never return after that. This contradicts the recurrence of $i$.

**Proposition 4.4.2** Let $T$ be the set of all transient states, $j\in R$ a recurrent class. Then $f_{ij}=\sum_{k\in T}p_{ik}f_{kj}+\sum_{k\in R} p_{ik}$.

proof by conditioning on the first step.

**Example 4.4(A) The gambler's ruin problem** _Setting_ Suppose a gambler wins or loses $1$ unit per play with probability $p,1-p$ independently. Denote the fortune by time $n$ by $X_n$, then $X_n$ is a Markov chain. Suppose he stops at $X_n=0$ or $X_n=N$, then the transition probability is given by $p_{00}=p_{NN}=1$, and $p_{i,i+1}=p=1-p_{i,i-1}$. Now we wonder the probability it stops at $N$ starting from $i$.

First, the states can be divided into 3 classes, $\{0\},\{N\},\{1,...,N-1\}$, with the first two recurrent and the third transient. Since the transient states will be visited for finite times and there are finite transient states, it will finally stops at $0$ or $N$.

Now denote $f_{i}=f_{iN}$, we have $f_{i}=p f_{i+1}+qf_{i-1}$. the boundary condition is $f_0=0,f_N=1$. Solving this, we get 
$$
f_i = 
\begin{cases} 
\dfrac{1 - (q/p)^i}{1 - (q/p)^N} & \text{if } p \neq \frac{1}{2}\\
\dfrac{i}{N} & \text{if } p = \frac{1}{2}
\end{cases}
$$

- If we pushes $N\to \infty$, then 
  $$
  f_i \rightarrow
  \begin{cases} 
  1 - (q/p)^i & \text{if } p > \frac{1}{2} \\
  0 & \text{if } p \leq \frac{1}{2}
  \end{cases}
  $$
  So if his strategy is to stop only when $X=0$, when $p>1/2$, with positive probability the fortune converges to infinity, and when $p\le 1/2$, w.p.1 he stops at $0$.

- Consider the number of bets $B$ and $m_i:=E^iB$. Since $B$ is a stopping time, by Wald's equation, 
  $$
  E^i \sum_{j=1}^{B} X_j=E^i BEX_i=(2p-1) E^iB
  $$
  But $E^i \sum_{j=1}^{B} X_j =f_i(N-i)+(1-f_i)(-i)=f_i N-i$, so $E^i B=\frac{f_i N-i}{2p-1}$. when $p=1/2$, take limit.

Now consider a finite Markov chain with states $\{1,...,t\}:=T$ transient, then pick $Q=(p_{ij})_{i,j\le t}$. Notice $Q$ denotes the transition probability from transient state to transient state, and at least some sum of row $<1$, otherwise $Q$ is a transition matrix for $T$, but a finite-state Markov chain must have a recurrent state. 

Let $m_{ij}$ to be visits to $j$ with $X_0=i$, where $i,j\in T$. Conditioning on the first step we have $m_{ij}=\delta_{ij}+\sum_{k=1}^t p_{ik}m_{kj}$ (If it jumps out of $T$, it will never return). Then if we denote $M=(m_{ij})_{i,j\le t}$, we have $M=I+QM$, i.e., $M=(I-Q)^{-1}$. 

Since $m_{ij}=f_{ij}m_{jj}$, $f_{ij}$ can also be determined by $M$.

_Proposition_ $(I-Q)^{-1}$ exists. 

<font color='red'>_proof_</font> To prove this, it suffices to show $1$ is not an eigenvalue. Since $Q>0$ and the sum of each row $\in(0,1]$, by Perron-Frobenius theorem, the eigenvalue of maximal module is a real number in $(0,1]$, with an eigenvector $v>0$. If the inverse doesn't exist, $1$ must be an eigenvalue, and $v=vQ$. But sum up coordinates of $v$, since we have argued the sum of rows of $T$ are not all equal to $1$, $\sum_i (vQ)_i<\sum_i v_i$. However $v>0$. This is a contradiction.

### 4.5 Branching Process

_Setting_ Consider the Markov chain $X_n$ defined by the following manner: Imagine a population  with every individual producing offspring $\sim P_j$ independently. $X_0$ is the initial scale of the population and $X_n$ is the number of $n$th offspring.

Since the individuals are independently producing offspring, it suffices to start from $X_0=1$ to get many results. 

- Suppose $X_0=1$, then $EX_n=\mu EX_{n-1}=...=\mu^n$, where $\mu=\sum_j jP_j$.

- Now consider $\pi_0$ to be the probability that the population ever dies out with $X_0=1$. By conditioning on the first generation, we have 
  $$
  \pi_0=\sum_{j=0}^\infty P(\text{dies out}\mid X_1=j)P_j=\sum_{j=0}^\infty \pi_0^j P_j
  $$
  since if a population of $n$ individuals ever dies out, $n$ families starting from some individual must all die out and these events are independent.

**Theorem 4.5.1** Suppose $p_0>0$ and $p_0+p_1<1$ (to exclude trivial case) Then $\pi_0$ is the smallest positive number satisfying $\pi_0=\sum_{j=0}^\infty \pi_0^j P_j$. Moreover, $\pi_0=1$ iff $\mu\le 1$.

<font color='red'>_proof of Theorem 4.5.1_</font>

- Notice $\pi_0=1$ is a solution.

- Now we prove $\pi_0$ should be the smallest such root. Pick $\pi$ a root. We prove by induction that $\pi\ge P(X_n=0)$, by
  $$
  P(X_{n+1}=0)=\sum_j P(X_{n+1}=0\mid X_n=j)P_j \le \sum_j \pi P_j=\pi
  $$
  And actually $\lim_{n \to \infty} P(X_n=0)=\pi_0$. So $\pi>\pi_0$. This indicates that $\pi_0$ should be smallest root.

- When $\mu\le 1$, consider $\varphi(s)=\sum_{j=0}^\infty P_j s^j$. Notice $\varphi(s),\varphi'(s),\varphi''(s)>0\forall s\in[0,1]$, and $\varphi'(1)=\mu$. So if $\mu\le 1$, $(s-\varphi(s))'\ge 0$, and $1-\varphi(1)=0$. This implies $1$ is the unique root. If $\mu<1$, $0-\varphi(0)<0$, and $(s-\varphi(s))'\mid_{s=1}=1-\mu<0$, $1-\varphi(1)=0$, this implies there is another root in $(0,1)$. remark: since $\varphi$ is strictly convex, the equation has at most 2 roots.

### 4.6 Applications of Markov chain

#### 4.6.1 A Markov chain model of Algorithmic efficiency

Consider such Markov chain: $p_{ii}=1$, $p_{ij}=\frac{1}{i-1}\forall j<i$. Then this chain always moves toward $1$, which is interpreted the "best state" here.

- Let $T_i$ be the number of transitions from $i$ to $1$. Then $ET_i=1+\frac{1}{i-1}\sum_{j=1}^{i-1} ET_j, ET_1=0$, which gives $ET_i=\sum_{j=1}^{i-1}\frac{1}{j}$.

- To obtain some more description of $T_N$, we use $T_N=\sum_{j=1}^{N-1} 1_j$, where $1_j$ is the indicator function of the event the process has ever entered state $j$. (This identity holds since the chain visits each state for only one time.)

- **Lemma 4.6.1** $1_j$ are independent, with $P(1_j=1)=1/j$.

  <font color='red'>_proof of Lemma 4.6.1_</font> Let $i=\min\{i>j: 1_i=1\}$, we have 
  $$
  P(1_j=1\mid 1_{j+1},...,1_N)=\frac{1/(i-1)}{j/(i-1)}=1/j
  $$
  since in this condition $i$ is known, and the state $i$ can only jumps to $1,...,j$.

- **Proposition 4.6.2** (i) $ET_N=\sum_{j=1}^{N-1} 1/j$ (ii) $varT_N=\sum_{j=1}^{N-1}1/j(1-1/j)$ (iii) $T_N$ is approximately Poisson with mean $\log N$

  <font color='red'>_proof of Proposition 4.6.2_</font> (i) and (ii) follows from **Lemma 4.6.2**, and (iii) holds by weak law of small numbers.

#### 4.6.2 An application to runs

_Setting_ Consider a sequence $(x_k)$ that takes values on $\mathbb Z_{>0}$. A run is a longest increasing segment. For instance, $\mid 3,5,8\mid 2,4\mid 3\mid 1$ consists of $4$ runs. 

Now let $X_i$ i.i.d. $\sim U(0,1)$, and consider the distribution of the length of successive runs. Denote the length of $n$th run by $L_n$. First, we can conclude easily:

- $P(L_1\ge m)=(m!)^{-1}$. (order statistic problem)
- If $X_1=x$, $P(L\ge m\mid x)=(1-x)^{m-1}/(m-1)!$.

By this, to find the distribution of $L_n$, let's discuss $I_n$, the initial value of $n$th run. Obviously $I_n$ is a Markov chain. To determine the transition density, consider 
$$
P(I_{n+1}\in (y,y+dy)\mid I_n=x)=\sum_{m=1}^\infty P(I_{n+1}\in (y,y+dy),L_n=m\mid I_n=x)
$$
when $y$ is small, $I_{n+1}\in (y,y+dy),L_n=m\mid I_n=x$ means $I_{n+1}\in (y,y+dy)$, and some value in the $n$th run exceeds $y$. So
$$
RHS=\sum_{m=1}^\infty \frac{(1-x)^{m-1}}{(m-1)!}P(\max{X_i}>y\mid X_i>x)\ dy
$$
where 
$$
P(\max X_i>y\mid X_i>x)=\left\{\begin{aligned} &1,&y\le x\\&1-\frac{(y-x)^{m-1}}{(1-x)^{m-1}},&y>x\end{aligned}\right.
$$
which gives 
$$
RHS=\left\{\begin{aligned}&e^{1-x}&y\le x\\&e^{1-x}-e^{y-x}&y>x\end{aligned}\right.
$$
Now we care about the limit distribution of $I_n$. 

_Intuition_ $I_n<y$  means $X_k>y\mid X_k<X_{k-1}$ (suppose $I_n=X_k$), and since $X_{k-1}\sim U(0,1)$ when there's no condition, the probability is $P(X_1>y\mid X_1<X_2)=(1-y)^2$. So $\pi_y=2(1-y)$ seems to be the limit distribution.

_Input_ The limit distribution is also the stationary distribution in this case.

<font color='red'>_proof_</font> verify $\pi(x)=\int \pi(y)p(x\mid y)dy$.

Immediately we get the limit distribution of $L_n$, 
$$
\lim_{n \to \infty} P(L_n\ge m)=\int_0^1 \frac{(1-x)^{m-1}}{(m-1)!}2(1-x)dx=\frac{2}{(m+1)(m-1)!}
$$
and $EL_n\to\sum_{m=1}^\infty P(L_n\ge m)=2$.

#### 4.6.3 List Ordering rules-Optimality of the transposition rule

_Setting_ Consider a stack with elements $e_1,...,e_n$, and they will be visited with probability $P_j$. The goal is to minimize the carrying cost. Since a stack is FIFO, if $P_j$ is known, the optimal placing is to place them from top to end by decreasing order of $P_j$. Now assume $P_j$ is unknown, and we are only allowed to rearrange the elements by its present state.

To simplify the problem, assume $P_1=p$ and $P_2=...=P_n=(1-p)/(n-1):=q$. Then we can track a Markov chain with $n$ states instead of $n!$.

TBC

### 4.7 Time-reversible Markov chain

**Definition** An irreducible positive recurrent Markov chain is **stationary** if the initial state follows the stationary distribution. We say it's in **steady state**.

_Remark_ For an ergodic chain, we can assume the chain starts when $t=-\infty$, which is often useful.

Consider a stationary Markov chain, and we trace the sequence of states going backward in time, $(X_n,X_{n-1},...)$ starting from $n$.

**Proposition** The reverse chain is also Markov.

<font color='red'>_proof_</font> 

1. $P(X_m=j\mid X_{m+1}=i,X_{m+2},...)=P(X_m=j\mid X_{m+1}=i)$, since if we look at the chain forward, $X_{m+2},...$ are independent of $X_m$.

2. Its transition probability is given by
   $$
   p_{ij}^*=P(X_n=j\mid X_{n+1}=i)=P(X_{n+1}=i\mid X_n=j)P(X_n=j)/P(X_{n+1}=i)=p_{ji}\pi(j)/\pi(i)
   $$

**Definition** If $p_{ij}^*=p_{ij}$, i.e., $\pi_ip_{ij}=\pi_jp_{ji}\forall i,j$, the chain is said to be **time reversible**. 

_Remark_ Since $\pi_i$ is the long-time proportion of visits of $i$, $\pi_ip_{ij}$ is the long-time proportion of transitions from $i$ to $j$. So the chain is time-reversible if the long-run proportion of transition from $i$ to $j$ equals to that from $j$ to $i$. 

_Remark_ If we can find the solution for $x_i>0,x_ip_{ij}=x_jp_{ji},\sum_ix_i=1$, then the chain is reversible and $(x_i)$ is exactly the stationary distribution, since $\sum_i x_ip_{ij}=\sum_i x_jp_{ji}=x_j$. Since $\pi$ is unique, it follows that $\pi_i=x_i$.

**Example 4.7(A) An ergodic random walk** Suppose an ergodic chain satisfies $p_{i,i+1}+p_{i,i-1}=1$, then it's time-reversible. The argue follows from the first remark: Notice the chain moves one unit on axis per step. If the chain moves $k$ times from $i$ to $j$ and $k'$ times from $j$ to $i$, $|k-k'|\le 1$. So the long-run proportion must be equal.

Now we consider a special Markov chain: Given a graph $G(V,E)$, we put weight $w_{ij}$ on the edge $(i,j)$. $w_{ij}=0$ if $i\nleftrightarrow j$. Consider a Markov chain with transition probability $p_{ij}=w_{ij}/\sum_k w_{ik}$. then $X_n$ tracking this process is called **a random walk on an edge weighted graph**.

**Proposition 4.7.1** If $|V|<\infty$, and $X_n$ is irreducible, then it's time reversible w.r.t. $\pi_i=\sum_k w_{ik}/\sum_j\sum_k w_{jk}$

<font color='red'>_proof of Proposition 4.7.1_</font> Solve equations,
$$
\pi_i p_{ij}=\pi_j p_{ji}\Rightarrow \pi_i w_{ij}/\sum_k w_{ik}=\pi_j w_{ji}/\sum_k w_{jk}\Rightarrow \pi_i/\sum_k w_{ik}=\pi_j/\sum_k w_{jk}
$$
yields $\pi_i=\sum_k w_{ik}/\sum_j\sum_k w_{jk}$.

**Example 4.7(c)** consider a star graph consisting of $r$ rays, each of which consists of $n$ vertices. Its transition probabilities are given by: at the center, it moves to every neighbor with equal probability; at a leaf node, it moves to its neighbor with probability 1; at a node on some ray, it moves towards the leaf with probability $p$ and towards the venter $1-p$. We wonder the expected transitions that it takes to visit all vertices and then return to 0.

_Solution_ Weight the graph in this manner:

<img src="C:\Users\m1500\Desktop\Durrent\images\star_graph.png" style="zoom:70%;" />

with $\sum_i\sum_j w_{ij}=2r(1-w^n)/(1-w)$.

This gives $\pi_0=r/\sum_i\sum_j w_{ij}=(1-w)/2(1-w^n)$, and $\mu_{00}=1/\pi_0=2(1-w^n)/(1-w)$.

There are two ways to calculate.

Consider visit to $0$ as renewal, we get a renewal process. Let $X_j$ be the steps in $j$th cycle, then $EX_j=\mu_{00}$. Let $N$ be the stopping time of visiting $i$th leaf node.

- By Wald's equation, $\mu:=E\sum_{j=1}^N X_j=\mu_{00} EN$.
- $N$ follows a geometry distribution, and the probability of success is given by $\frac{1}{r} \frac{1-1/w}{1-1/w^n}$, since it has $1/r$ probability to enter the $i$th ray and that it visits the leaf before the center is a gambler-ruin problem.

We have determined the mean steps to visit a certain leaf and then return to $0$. Now we use this to compute the expected steps to visit all nodes and then return to 0, say $ET$.

(i) _On book_ We can decompose $T=T_1+T_2+...+T_r$, where $T_i$ is the extra time needed after leaves $1,...,i-1$ are done (i.e., visited the leaf and return to 0), until leaves $1,...,i$ are done. If $i$ is visited before $i-1$, $T_i=0$. Then $ET=ET_1+...+ET_r$. 

Consider $ET_i$ respectively. $ET_1$ is exactly the time needed to visit leaf $1$, so $ET_1=\mu$. $ET_2$ is the extra time needed after leaves $1$ are done until $1,2$ are done. If $1$ is visited before $2$, then the extra time is just the time from $0$ needed to visit $2$ whose mean is $\mu$, but if $2$ is visited before $1$, then the extra time is $0$. This gives 
$$
ET_2=P(1\text{ ahead of }2)\mu+P(2\text{ ahead of }1)0=\mu/2
$$
 by symmetry. Generalize this argument, we can see for $T_i$, if $i$ is not the last to be visited in $1,...,i$, $T_i=0$, otherwise $T_i$ is the time needed from $0$ to $i$, whose mean is $\mu$. Again by symmetry, $ET_i=\mu/i$. So $ET=\mu(1+...+1/r)$.

(ii) _More direct_ Recall coupon's collector problem,

> [!NOTE]
>
> **Coupon-collector problem** Suppose there are $r$ different coupon types. Each time you get a coupon, it is equally likely to be any one of the $r$ types. How many coupons do you expect to collect before you have all $r$ types?
>
> _Solution_ denote the time by $T$, and the time to collect $i$th new coupon by $T_i$, then $T=T_1+...+T_r$. Foe each $T_i$, since $i-1$ coupons have been collected, so it follows a geometry distribution with $p=(r-i+1)/r$, hence $ET_i=r/(r-i+1)$. Since $ET=ET_1+...+ET_r$, we have $ET=r\sum_{i=1}^{r}1/i$.

Apply here now. Define $N$ to be the stopping time that it has visited a leaf and return to 0. By Wald's equation, $\mu':=E\sum_{j=1}^{N} X_j=\mu_{00} EN$. Similarly, $EN=(1-1/w^n)/(1-1/w)$, since from $0$ the chain must move to some neighbor, and as it enter some ray, the problem is gambler's ruin. Since each time the chain returns to 0 it choose one ray uniformly, so in this sense it's a coupon's collector problem, with $1$ replaced by $\mu'$. So the expected steps are $\mu'\sum_{i=1}^{r} r/i$. Since $\mu=r\mu'$, the two result is equal.

Now we return to the discussion for an equivalent condition of "reversible". 

**Theorem 4.7.2** A stationary Markov chain is time reversible iff for all $i,i_1,...,i_k$, we have $p_{ii_1}p_{i_1i_2}...p_{i_ki}=p_{ii_k}p_{i_ki_{k-1}}...p_{i_1i}$, i.e., the probability of a loop equals that of its inverse.

_Intuition_ if it's time reversible, we must be able to solve $x_ip_{ij}=x_jp_{ji}$, $x_kp_{kj}=x_jp_{jk}$, and $x_ip_{ik}=x_kp_{ki}$. This forces that $p_{ij}p_{jk}p_{ki}=p_{ji}p_{kj}p_{ik}$. Meanwhile, if the condition holds, we can see the long-run proportions of the loop and its inverse are equal, which corresponds the case that the chain is reversible.

<font color='red'>_proof of Theorem 4.7.2_</font> $\Rightarrow$ just solve equations.

$\Leftarrow$ Pick $i,j$ fixed, we have $p_{ii_1}...p_{i_kj}p_{ji}=p_{ij}p_{ji_k}...p_{i_1i}$. Sum up w.r.t. $i_1,...,i_k$, we have $p_{ij}^{k+1}p_{ji}=p_{ji}^{k+1}p_{ij}$. Since $\pi_i=\lim_{n \to \infty}\sum_{k=1}^{n} p_{ji}^k/n$, we have $\pi_j p_{ji}=\pi_ip_{ij}$.

_Remark_ When the chain is ergodic, irreducible, and of finite state, then it suffices to verify $p_{ij}p_{jk}p_{ki}=p_{ik}p_{kj}p_{ji}$, since we can decompose $i\to i_1\to i_2...\to_1$ into $i\to i_1\to i_2\to i\to i_2\to i_3\to i...\to i_{n}\to i$.

**Example 4.7(D) A list problem** This is an example for **Theorem 4.7.2**. Suppose we have $1,...,n$ placed in some order, $P_j$ is the probability for $j$ to be picked. When someone is picked, it moves one step closer to the head (if it's the head, it doesn't move). The orders construct a Markov chain with state $n!$, for from $i_1....i_n$ to $i_1...i_n$, every element must moves forward and backward for equal steps, which should have equal probability. 

Moreover, we can verify $\pi(i_1,...,i_n)=Cp_{i_1}^np_{i_2}^{n-1}...p_{i_n}$ is a stationary distribution, where $C$ is a normalization constant. 

**Theorem 4.7.3** Suppose $(X_n)$ is irreducible. If given $p_{ij}$, one can solve $\pi_ip_{ij}=\pi_jp_{ji}^*$, with $\sum_i\pi_i=1$ and $p_{ji}^*$ some transition probability, then $\pi_i$ is a stationary distribution and $p_{ij}^*$ is the transition probability for reversed Markov chain.

<font color='red'>_proof of Theorem 4.7.3_</font> Stationarity comes from the identity $\sum_i \pi_i p_{ij}=\sum_i \pi_jp_{ji}^*=\pi_j$. 

Now we have $X_n$ i.i.d.$\sim \pi$, and $X_i,X_j$ are independent if $|i-j|>1$. So if we see the chain reversely, we can observe the same phenomenon. So the reversed chain has stationary distribution $\pi$. Since 
$$
\begin{aligned}
P(X_n=i,X_{n+1}=j)&=P(X_{n+1}=j\mid X_n=i)P(X_n=i)=p_{ij}\pi_i
\\&=P(X_n=i\mid X_{n+1}=j)P(X_{n+1}=j)=p'_{ji}\pi_j
\end{aligned}
$$
where $p_{ji}'$ denotes the transition probability for reversed chain. So $p_{ji}'=p_{ji}^*$.

By this, we can obtain both the stationary distribution and the reversed transition probability.

**Example 4.7(E)** Reconsider **Example 4.3(C)**: Suppose $X_n$ is a Markov chain. If we regard visits to 0 as renewals, and the interarrival time has distribution $P_j$, then the age $A_n$ is a Markov chain, whose transition probability is given by $p_{i1}=P_i/\sum_{j=i}^\infty P_j=1-p_{i,i+1}$.

Now consider the reversed chain. The chain increases by 1 or decrease to 0 each step, so its inverse chain decreases by 1 or increase to some number after touching 0 each step, which behaves like the excess. Now we verify this.

The transition for excess chain is given by $p_{i,i-1}^*=1\forall i>1$, and $p_{1,i}=P_i$. By this, we can solve $\pi_i=\pi_1\sum_{j=i}^\infty P_j$, which gives $\pi_i=\sum_{j=i}^\infty P_j/\mu$. So the reversed chain is exactly excess, and the limit distribution is also that of age.

### 4.8 Semi-Markov Process

**Definition** $Z(t)$ with state space $S$ is called **semi-Markov process**, if it shifts its states as a Markov chain, but the waiting time is a r.v. with distribution $F_{ij}$ when it's shifting from state $i$ to state $j$.

_Remark_ $Z(t)$ isn't Markovian in general, since at time $t$, the future may depend on the past, since it's determined not only by the current state, but by the time spent in this state. For a Markov chain, $F_{ij}$ has point mass at $1$, which is a special case. 

_Remark_ The time spent in state $i$, has distribution $H_i$ given by $H_i(t)=\sum_{j=1}^\infty p_{ij} F_{ij}(t)$. Denote its mean $\mu_i=\int_0^\infty xdH_i(x)$.

**Definition** If we denote $X_n$ to be the $n$th state it visits, $X_n$ is a Markov chain, which is called **embedded Markov chain**. $Z(t)$ is **irreducible** if $X_n$ is. 

**Proposition 4.8.1** Suppose $Z(t)$ is irreducible. Regard visits to $i$ as renewals and denote the interarrival time $T_{ii}$. Suppose $T_{ii}$ has nonlattice distribution and finite mean $\mu_{ii}$. Then $P_i=\lim_{t \to \infty} P(Z(t)=i\mid Z(0)=j)=\mu_i/\mu_{ii}$, independent of the initial state.

<font color='red'>_proof of Proposition 4.8.1_</font> First, if we regard visits to $i$ as renewals, it's exactly a renewal process. Say the process is on when $Z(t)=j$. By theorems for alternating renewal process we complete our proof.

_Corollary_ the long-run proportion of time in state $i$ is also $\mu_i/\mu_{ii}$.

**Theorem 4.8.3** Suppose further $X_n$ is positive recurrent, then $P_i=\pi_i\mu_i/\sum_j \pi_j\mu_j$.

_Intuition_ $\pi_i$ is long-run proportion for $X_n$ to stay in state $i$ and $\mu_i$ is the mean waiting time for state $i$. So $\pi_i\mu_i$ is the long-run time interval to stay at time $i$.

<font color='red'>_proof of Theorem 4.8.3_</font> 

Set $Y_i(j)$ to be the amount of time spent in state $i$ during the $j$th visit to that state, and $N_i(m)$ to be the number of visits to state $i$ in the first $m$ transitions, $P_{i,m}$ to be the proportion of time in state $i$ during the first $m$ transitions, we have 
$$
\begin{aligned}
P_{i,m}&=\frac{\sum_{k=1}^{N_i(m)}Y_i(k)}{\sum_{s\in S}\sum_{k=1}^{N_s(m)} Y_s(k)}
\\&=\frac{\sum_{k=1}^{N_i(m)}Y_i(k)}{N_i(m)}\bigg/\sum_{s\in S}\frac{\sum_{k=1}^{N_s(m)} Y_s(k)}{N_s(m)}\frac{N_s(m)}{N_i(m)}
\\&\to \mu_i /\sum_{s\in S}\mu_s \frac{\pi_s}{\pi_i}
\end{aligned}
$$
**Theorem 4.8.4** Let $Y(t)$ denotes the time from t to the next transition and $S(t)$ the next state to transit. If $Z(t)$ is irreducible and nonlattice, then
$$
\lim_{t \to \infty} P(Z(t)=i,Y(t)>x, S(t)=j\mid Z(0))=\mu_{ii}^{-1}p_{ij}\int_x^\infty \bar{F}_{ij}(y)dy
$$
<font color='red'>_proof of Theorem 4.8.4_</font> Consider visits to $0$ as renewal, and say the process is on when $Z(t)=i, Y(t)>x, S(t)=j$.

Summing up w.r.t. $j$, we have

_Corollary_ $\lim_{t \to \infty} P(Z(t)=i,Y(t)>x\mid Z(0)=k)=\int_x^\infty \bar{H}_i (y)/\mu_{ii}$.

_Corollary_ $\lim_{t \to \infty} P(Z(t)=i,Y(t)>x)=P_i \bar{H}_{i,e}(x)$, where $H_{i,e}$ is the equilibrium distribution of $H_i$. This corresponds to our intuition.

***

4.7 For SRW in 1d, denote $N_n$ the number of returns to 0. Then $EN_n=O(\sqrt{n})$.

_proof_
$$
\begin{aligned}
EN_{2n}&=\sum_{i=1}^{n} P(S_{2i}=0)=\sum_{i=1}^{n} \binom{2i}{i}2^{-2i}=(2n+1)\binom{2n}{n}2^{-2n}-1
\end{aligned}
$$
by noticing, if we let $a_i=\binom {2i}{i} 2^{-2i}$, then $a_{i-1}=\frac{2i}{2i-1}a_i$, i.e., $a_i=(2i+1)a_i-(2i-1)a_{i-1}$. Then use telescoping.

By stirling's formular, $EN_{2n}\approx (2n+1)/\sqrt{\pi n}-1=O(\sqrt{n})$.

_Remark_ So the returning time $T\approx n/\sqrt{n}\to\infty$. To argue this rigorously, solve $\pi_i=(\pi_{i-1}+\pi_{i+1})/2$ and find no solution satisfying $\sum_i \pi_i=1$.

4.11 If $f_{ii},f_{jj}<1$, we have 

(a) $\sum_{n=1}^\infty p_{ij}^n<\infty$: suppose $p_{ij}^k>0$, since $j$ is recurrent, we have $\sum_{n=1}^\infty p_{ij}^n\le p_{ij}^k\sum_{n=1}^\infty p_{jj}^n<\infty$.

(b) $f_{ij}=\sum_{n=1}^\infty p_{ij}^n/(1+\sum_{n=1}^\infty p_{jj}^n)$: We have identity $p_{ij}^n=\sum_{k=1}^{n} f_{ij}^n p_{jj}^{n-m}$. 

4.22 Let $T_i$ denote the number of plays in a gambler's problem that the fortune starts from $i$ and ends at $0$ or $N$. Compute $ET_i$.

_Solution_ By moving one step forward, $ET_0=ET_N=0$ and $ET_i=1+pET_{i+1}+(1-p)ET_{i-1}$. The solution is
$$
ET_k=\left\{\begin{aligned}&\frac{1}{1-2p}[k-N\frac{1-(q/p)^k}{1-(q/p)^N}]&p\ne 1/2\\&k(N-k)&p=1/2\end{aligned}\right.
$$
4.27 Consider a particle that moves along a set of $m+1$ nodes, labelled $0,1,...,m$, with $p_{i,i+1}=p=1-p_{i,i-1}$, where $m+1=0$. If the chain starts at $0$, find the probability to visit $i$ for the last. 

_Solution_ Before node $i$ is hit, the other $m$ nodes form a line $i+1,...,m,0,1,...,i-1$, where $0$ is $(m-i+1)$st. To visit $0$, the particle must visit $i-1$ or $i+1$. This is a gambler's ruin. After visiting two endpoints, wlog it has visited $i-1$, To visit all nodes except $i$, consider the line $i,i+1,...,i-1$, now for the nodes it must visits $i-1$ before $i$. This results in another gambler's ruin. 

Denote $P_x(T_a^i<T_b^i)$ to be the probability of starting from $x$, the $i$th ($i$=1,2) gambler's ruin hits a before $b$. For simplicity let $r=q/p$. So 
$$
\begin{aligned}
P_i&=P_0(T_{i+1}^1<T_{i-1}^1)P_{i+1}(T_{i-1}^2<T_i^2)+P_0(T_{i-1}^1<T_{i+1}^1)P_{i-1}(T_{i+1}^2<T_i^2)
\\&=[1-\frac{1-r^{m-i}}{1-r^{m-1}}]\frac{1-r}{1-r^m}+\frac{1-r^{m-i}}{1-r^{m-1}}[1-\frac{1-r^{m-1}}{1-r^m}]
\\&=\frac{r^{m-i}}{1+r+...+r^{m-1}}
\end{aligned}
$$
Especially, as we noted, when $r=1$, $P_i\equiv 1/m$.

4.33 The branching process $X_n$ has the property: $X_n\to 0$ or $X_n\to\infty$.

_proof_ Suppose $\mu>1$, since when $\mu\le 1$, w.p.1 the extinction happens. Notice despite $\mu>1$, the extinction is still likely to happen. Denote the extinction probability by $q<1$, then when $X_n=k$, the probability that it finally dies out is $q^k$ and that it finally survives is $1-q^k$.

Suppose $X_n$ doesn't converge to 0 nor $\infty$. Then there is some $K$ s.t. $1\le X_n\le K$ i.o.. If the process has visited $r$ times of $1,...,K$, the probability that it finally survives is less than $(1-q^K)^r$, since each time it visits $0,...,K$, it dies out with probability at least $q^K$ . When $r\to\infty$, we see it finally dies out, which is a contradiction. 



