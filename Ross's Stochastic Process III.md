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