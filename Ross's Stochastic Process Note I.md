This is note for Ross's Stochastic Process.

Basic notions are skipped, and we hit the road now.

#### 1.9 Stochastic Process

**Definition** A **stochastic process** (abbr. s.p.) $X=\{X(t),t\in T \}$ is a collection of r.v.'s, where $T$ is an index set. $t$ is often interpreted as time. If $T$ is countable, $X$ is **discrete-time** and if $T$ is a continuum, $X$ is **continuous-time**.

Any realization of $X$ is called a sample path.

$X$ is said to have **independent increments** if for all $t_0<...<t_n$, $X(t_1)-X(t_0),...,X(t_n)-X_(t_{n-1})$ are independent; have 

**stationary increments** if for fixed $s$, for all $t$ $X(t+s)-X(t)$ has the same distribution.

**Example 1.9 (A)** consider a random walk on $\mathbb Z/(m+1)\mathbb Z$, with $X_0=0$, and $P(X_{n+1}=i\pm 1|X_n=i)=1/2$, we claim that, when all points are visited, the distribution of the last point visited is uniform on $\{1,...,m\}$.

<font color='red'>_proof_</font> To arrive at $i\ne 0$, we must have visited $i-1$ or $i+1$. Let $A$ be the event that $X$ visits $i-1$ before $i+1$ and $B$ the opposite thing. $A$ and $B$ are disjoint and $P(A)+P(B)=1$. Condition on $A$, $X$ may visit $i$ or $i+1$ first. If $X$ visits $i$ before $i+1$, then since $i+1$ haven't been visited, the last to be visited can't be $i$. If $X$ visits $i+1$ before $i$, then it must visits all points except $i$. So conditioning on $A$, the event that $i$ is the last to be visited is the event that $i$ is visited before $i+1$.

Consider the event "$i$ is visited before $i+1$". Put these points on a line with order $i,i-1,...,i+1$. This is "gambler's ruin" problem, and the result is that, starting from $i-1$, that it is absorbed at $i+1$ has probability $1/m$. But here we doesn't care about the exactly probability, so we denote it $p$. $p$ is irrelevant to $i$.

The case for $B$ is identical, with the order inversed. So $P(\text{the last one is i})=pP(A)+pP(B)=p$. So the distribution is uniform, so $pm=1$, $p=1/m$. 

Interestingly we can use this model to solve the "gambler ruin" problem. We have shown, if he starts from 0 and win/lose 1 with the same probability, then $P(\text{-n before +1})=\frac{1}{n+1}$, or we say $P(\text{+1 before -n})=\frac{n}{n+1}$. Moreover, 
$$
P(\text{+2 before -n})=P(\text{+2 before -n}|\text{+1 before -n})\frac{n}{n+1}=P(\text{+1 before -n-1})\frac{n}{n+1}=\frac{n}{n+2}
$$
similarly by induction we have $P(\text{+k before -n})=\frac{n}{n+k}$.

**(B)** Now suppose $P(X_{n+1}=i+1|X_n=i)=p$ and $P(X_{n+1}=i-1|X_n=i)=1-p$. we claim if $p>1/2$, $P(\text{the last to be visited is i})$ is increasing.

<font color='red'>_proof_</font> The proof is similar. Condition on $A$, that we visit $i$ last have probability $p'$, and condition on $B$ the probability is not $p'$, we say it $q'$. Notice $p',q'$ are irrelevant to $i$ and $p'<q'$ since $p>1/2$ encourages to move left. 

Now we have $P(\text{i is last state})=p'P(A)+q'(1-P(A))=(p'-q')P(A)+q'$. Notice $P(A)$ is decreasing: if one visit $i-1$ before $i+1$, it must have visited $0,...,i-1$ and not visited $i$, so it must visit $i-2$ before $i$. So $P(\text{i-1 before i+1})<P(\text{i-2 before i})$.

**(C)** Generalize this model: consider a graph with central vertex labelled $0$, from which $r_0$ rays emanate. Each ray is a line with $n_r$ nodes, with one endpoint $0$ and another endpoint called leaf $i_r$ if it's on $r$ th ray. Consider a simple random walk starting from $0$, we consider the distribution of the first leaf to be visited, say $L$. 

<img src="C:\Users\m1500\Desktop\Durrent\images\a star graph.png" style="zoom:60%;" />

<font color='red'>_proof_</font> Condition on the first ray to be visited, $R$. If $j$ is the first ray to be visited, by **(A)** it visit $i_r$ before $0$ with probability $1/n_r$, and if it return to $0$ first the process is refreshed, so 
$$
\begin{aligned}
P(L=i)&=\sum_{r=1}^{r_0}\frac{1}{r_0}P(L=i|R=r)
\\P(L=i|R=i)&=1/n_i+(1-1/n_i)P(L=i)
\\P(L=i|R=k)&=(1-1/n_k)P(L=i), r\ne k
\\\Rightarrow\ r_0P(L=i)&=1/n_i+\sum_r (1-1/n_r)P(L=i)
\\\Rightarrow\ P(L=i)&=\frac{1/n_i}{\sum_r 1/n_r}
\end{aligned}
$$

### Chapter 2 The Poisson Process

#### 2.1 The Poisson Process

**Definition** A s.p. $\{N(t),t\ge 0\}$ is said to be a **counting process** if $N(t)$ denotes the total number of events that have occurred up to time $t$. It satisfies: (i) $N(t)\in Z_{\ge 0}$ (ii) $N(t)$ is nondecreasing (iii) $N(t)-N(s)$ is the number of events occurred during $(s,t]$. 

One of the most important types of counting process is the Poisson process:

**Definition 2.1.1** The counting process $N(t)$ is said to be a **Poisson process having rate $\lambda$** (abbr. $P_\lambda(t)$) where $\lambda\in\mathbb R_+$, if

(i) $N(0)=0$ (ii) $N(t)$ has independent increments (iii) $\forall s,t>0$, $N(t+s)-N(s)\sim P(\lambda t)$.

**Definition 2.1.2 Equivalent definition** ... if 

(i) $N(0)=0$ (ii) $N(t)$ has stationary and independent increments (iii) $P(N(h)=1)=\lambda h+o(h)$ (iv) $P(N(h)\ge 2)=o(h)$.

**Theorem 2.1.1** **Definition 2.1.1** and **Definition 2.1.2** are equivalent.

<font color='red'>_proof of Theorem 2.1.1_</font> 

$\Leftarrow$ Let $P_n(t)=P(N(t)=n)$. It suffices to show (iii) holds.

- We can derive $P_0(t)$ by 
  $$
  \begin{array}{@{}l@{}}
  \begin{array}{@{}r@{}l@{}}
  P_0(t+h)
  &{}=P(N(t+h)=0)=P(N(t)=0,N(t+h)-N(t)=0)\\
  &{}=P_0(t)P_0(h)=P_0(t)(1-\lambda h-o(h))
  \end{array}\\
  \Rightarrow \frac{P_0(t+h)-P_0(t)}{h}
  =-\lambda P_0(t)+o(1)\\
  \Rightarrow P_0'(t)=-\lambda P_0(t)
  \Rightarrow P_0(t)=e^{-\lambda t}
  \end{array}
  $$

- Similarly for $P_n(t)$​, by induction on $n$,
  $$
  \begin{array}{@{}l@{}}
  \begin{aligned}
  P_n(t+h)
  &=P_n(t)P_0(h)+P_{n-1}(t)P_1(h)
    +P_n(t+h)P(N(t+h)-N(t)\ge 2)\\
  &=P_n(t)(1-\lambda h-o(h))
    +P_{n-1}(t)(\lambda h+o(h))+o(h)
  \end{aligned}\\[0.5em]
  \begin{aligned}
  \Rightarrow \frac{P_n(t+h)-P_n(t)}{h}
  &=-\lambda P_n(t)+\lambda P_{n-1}(t)+o(1)\\
  &=-\lambda P_n(t)
    +\lambda \frac{(\lambda t)^{n-1}}{(n-1)!}e^{-\lambda t}+o(1)
  \end{aligned}\\[0.5em]
  \Rightarrow P_n(t)=\frac{(\lambda t)^n}{n!}e^{-\lambda t}
  \end{array}
  $$

$\Rightarrow$ It suffices to show (iii) holds.
$$
\begin{aligned}
P(N(h)=1)&=\lambda h e^{-\lambda h}=\lambda h+o(h)
\\P(N(h)\ge 2)&=1-e^{-\lambda h}-\lambda h e^{-\lambda h}\le\lambda^2h^2=o(h)
\end{aligned}
$$
*See PTE for intuition: this comes from the Poisson approximation of binomial distribution.*

#### 2.2 Interarrival and waiting time distributions

**Definition** The **sequence of interarrival times**, $(X_n)$, is defined by: $X_1$ is the time of the first occurrence and $X_{n}$ is the time between $(n-1)$st occurrence and $n$th occurrence.

Now we determine the distribution of $X_i$.

- $P(X_1>t)=P(N(t)=0)=e^{-\lambda t}$, so $X_1\sim Exp(\lambda)$.
- $P(X_2>t|X_1=s)=P(N(t+s)-N(s)=0)=e^{-\lambda (t)}$, so $P(X_2>t)=e^{-\lambda t}$, i.e., $X_2\sim Exp(\lambda)$ and $X_2$ is independent with $X_1$.
- Continue this process, we can get

**Proposition 2.2.1** $X_i$ are i.i.d. $\sim Exp(\lambda)$.

_Remark_ The stationary and independent increments makes $N(t+s)=_d N(t)\forall s$, so the interarrival times are memoryless.

**Definition** The **waiting time** until $n$th event is the time when $n$th occurs, i.e., $X_1+...+X_n$. Denote this by $S_n$.

The distribution can be attained by:

- $\varphi_{S_n}=(\varphi_{X_1}(t))^n=[\lambda/(it-\lambda)]^n$, so  $S_n\sim Gamma(n,\lambda)$, with density $f_{S_n}=\lambda e^{-\lambda t}\frac{(\lambda t)^{n-1}}{(n-1)!}$.

-  $P(S_n\le t)=P(N(t)\ge n)=\sum_{j=n}^\infty e^{-\lambda t}\frac{(\lambda t)^j}{j!}$, and differentiate w.r.t. $t$, we have the same result.
- Notice $P(t<S_n<t+dt)=P(N(t)=n-1)P(N(dt)\ge 1)=\frac{(\lambda t)^{n-1}}{(n-1)!}e^{-\lambda t}\lambda dt+o(dt)$.

**Equivalent definition of Poisson distribution** Let $X_i$ be i.i.d. $\sim Exp(\lambda)$, and $S_n=\sum_{i=1}^{n} X_i$, then the resulting counting process is $P_\lambda(t)$.

### 2.3 Conditional distribution of the arrival times

Conditioning on $N(t)=1$, we wonder the distribution of $X_1$. 

_Intuition_ With the independent and stationary increments, each interval in $[0,t]$ of equal length should contain the event with the same probability, i.e., $X_1$ should be uniform. Verification is direct,
$$
P(X_1<s|N(t)=1)=\frac{P(N(s)=1,N(t)-N(s)=0)}{P(N(t)=1)}=\lambda s e^{-\lambda s}e^{-\lambda (t-s)}/\lambda te^{-\lambda t}=s/t
$$
To generalize this, we introduce a notion.

**Definition** Let $Y_1,...,Y_n$ be r.v.'s, we say $Y_{(1)},...,Y_{(n)}$ are the order statistics corresponding to $Y_1,...,Y_n$ if $Y_{(k)}$ is the $k$th smallest value among $Y_i$. 

If $Y_i$ are i.i.d. with density $f$, we know $f(y_1,...,y_n)=n!f(y_1)...f(y_n)$, if $y_i$ are increasing.

If $Y_i$ are i.i.d. $\sim U(0,t)$, we know $f(y_1,...,y_n)=n! t^{-n}$.

**Theorem 2.3.1** Let $N(t)$ be a Poisson process, with $S_n$ the waiting time. Let $Y_1,...,Y_n$ be i.i.d. $\sim U(0,t)$. Then $(S_1,...,S_n)=_d (Y_{(1)},...,Y_{(n)})$.

<font color='red'>_proof of Theorem 2.3.1_</font> 
$$
f_{(S_1,...,S_n)|N(t)=n}(t_1,...,t_n) = \frac{(\prod_{m=1}^n \lambda e^{-\lambda(t_m-t_{m-1})}) e^{-\lambda (t-t_n)}}{P(N(t)=n)}=\frac{n!}{t^n}
$$
_Intuition_ If we just record the time of the occurrence of events, each of them is uniformly distributed and independent, so the times of $n$ occurrence are uniform on $[0,t]^n$ (unordered).

**Example 2.3 (A)** Suppose travelers arrive at a train depot $\sim P_\lambda(t)$. If the train departs at time $t$, we want to compute the expected sum of waiting times for the train, i.e. $E[\sum_{i=1}^{N(t)} (t-S_i)]$. 

Condition on $N(t)$, we have 
$$
E[\sum_{i=1}^{N(t)}(t-S_i)|N(t)]=tN(t)-E[\sum_{i=1}^{N(t)}S_i|N(t)]=tN(t)-E[\sum_{i=1}^{N(t)}U_{(i)}]=tN(t)-E[\sum_{i=1}^{N(t)}U_i]=tN(t)-1/2 tN(t)=1/2 tN(t)
$$
So $E[\sum_{i=1}^{N(t)} (t-S_i)]=E[E[\sum_{i=1}^{N(t)}(t-S_i)|N(t)]]=\frac{t}{2} E[N(t)]=\frac{\lambda t^2}{2}$.

By **Theorem 2.3.1**, we can consider the following process: Let $N(t)$ be a Poisson process, and $P(x)$ a function takes value on $[0,1]$. If an event occurs at time s, it will be type-I with prob. $P(s)$ and type-II with prob. $1-P(s)$ independently. Let $N_1(t)$ be the counting process of type-I and $N_2(t)$ be the counting process of type-II, we have:

**Proposition 2.3.2** For fixed $t$, $N_1(t)$ and $N_2(t)$ are independent Poisson r.v.'s with means $\lambda tp$ and $\lambda t(1-p)$ respectively, where $p=\frac{1}{t}\int_0^t P(s)ds$. 

_Remark_ $N_i(t)$ isn't a Poisson process in general, since $p$ may vary. However, if $p$ is a constant, i.e., irrelevant to $t$, They are Poisson processes. We will discuss this in the "compound Poisson process".

<font color='red'>_proof of Proposition 2.3.2_</font> We compute the joint distribution of $N_1(t)$ and $N_2(t)$. First, 
$$
P(N_1(t)=m,N_2(t)=n)=P(N_1(t)=m,N_2(t)=n|N(t)=m+n)P(N(t)=m+n)
$$
Conditioning on $N(t)$, there are $N(t)$ events occur on $[0,t]$ independently. Pick one event, it become type-I with prob. $p=\int_0^t P(s)f_{U}(s)ds$, where $U\sim U(0,t)$. So $p=t^{-1}\int_0^t P(s)ds$. This leads to
$$
P(N_1(t)=m,N_2(t)=n|N(t)=m+n)=\binom{m+n}{m}p^n(1-p)^m
$$
And finally we have 
$$
P(N_1(t)=m,N_2(t)=n)=\binom{m+n}{n}p^n(1-p)^m \frac{(\lambda t)^{m+n}}{(m+n)!}e^{-\lambda t}=\frac{(\lambda tp)^n}{n!}e^{-\lambda tp}\frac{(\lambda t(1-p))^m}{m!}e^{-\lambda t(1-p)}
$$
So $N_i(t)$ are independent Poisson distribution with means $\lambda tp$ and $\lambda t(1-p)$.

_Remark_ The proof can be easily generalized to any fixed number of types.

**Example 2.3 (B) The infinite server Poisson queue** Suppose that customers arrive at a service station $\sim P_\lambda(t)$. Upon arrival the customer is immediately served by one of an infinite number of possible servers, and the service time are assumed to be independent with a common distribution $G$.

For a fixed $t$, our interest lies on the joint distribution of the number of customers that have completed their service and the number of customers that are in service.

To compute this, we can use **Proposition 2.3.2**. We mark those who have completed their service at time $t$ type-I and those who are in service type-II. In this case, $P(s)$ is the prob. of a customer who arrives at time $t$ and leave before time $t$, whence $P(s)=G(t-s)$. So $N_1(t)$ is a Poisson with mean $\lambda tp$, $N_2(t)$ is a Poisson with mean $\lambda t(1-p)$, where $p=t^{-1}\int_0^s G(s)ds$, and they are independent.

**Example 2.3(c)** Suppose that a device is subject to shocks $\sim P_\lambda(t)$. The $i$th shock gives rise to damage $D_i$, where $D_i$ i.i.d. and independent with the process. 

The damage has the following property: (i) it will decrease exponentially in time, i.e., if a shock has initial damage $D$, then a time $t$ later its damage is $De^{-\alpha t}$. (ii) the damage are additive. This results that $D(t)=\sum_{i=1}^{N(t)} D_i e^{-\alpha(t-S_i)}$.

Now we calculate $E[D(t)]$. Also by conditioning on $N(t)$​,
$$
\begin{aligned}
E[D(t)\mid N(t)]
&= E\left[\sum_{i=1}^{N(t)} D_i e^{-\alpha (t-S_i)} \mid N(t)\right] \\
&= E[D]\, E\left[\sum_{i=1}^{N(t)} e^{-\alpha(t-S_i)}\mid N(t)\right]
   \text{ by independence of } D_i \\
&= e^{-\alpha t} E[D] E\left[\sum_{i=1}^{N(t)} e^{\alpha U_{(i)}}\mid N(t)\right]
   \text{ by Theorem 2.3.1} \\
&= e^{-\alpha t} E[D]\sum_{i=1}^{N(t)} E\left[e^{\alpha U_i}\right] \\
&= e^{-\alpha t} E[D]N(t)\frac{e^{\alpha t}-1}{\alpha t} \\
E[D(t)]&=E[E[D(t)\mid N(t)]]=E[D]\lambda \frac{1-e^{-\alpha t}}{\alpha}
\end{aligned}
$$
Another derivation is to segment the period into $[ih,(i+1)h], i=0,...,[t/h]$, and gather the damages occurred during these intervals, i.e., let $X_i=\sum_{ih\le S_k\le (i+1)h} e^{-\alpha (t-S_k)}$. So $D(t)=\sum_{i=0}^{[t/h]} X_i$. 

$E[D(t)]=\sum_{i=1}^{[t/h]}E[X_i]$, and condition on $X_i$, we know when $h$ is small, we need only to consider $X_i=1$. We denote the occurrence time of this single event by $L_i$, then we have 
$$
E[D(t)]=\sum_{i=0}^{[t/h]}\lambda h E[De^{-\alpha(t-L_i)}]+o(h)=\lambda E[D]\sum_{i=0}^{[t/h]}hE[e^{-\alpha(t-L_i)}]+o(1)\to \lambda E[D] \int_0^t e^{-\alpha (t-s)}ds
$$
This idea comes from the fact that Poisson distribution is an approximation of binomial distribution in the sense that when $h$ is sufficiently small, $P(\lambda t)\approx\sum_{i=0}^{[t/h]} B(1, \lambda h)$.

#### 2.3.1 The M/G/1 Busy period

Consider M/G/1 queue, in which customers arrive $\sim P_\lambda(t)$, and there is only one desk. Upon arrival, they either enter the service if free or wait in the queue. The successive service times are i.i.d. $\sim G$, and independent with the arrival. We investigate the distribution of the length of a busy period, i.e., the whole period keeping serving people. 

Suppose a busy period starts at some time and mark this by 0. Let $S_k$ denote the time until $k$ additional customers have arrived, and $Y_i$ the service time. Now we can give a formal definition: the busy period will last time $t$  and consist of $n$ service iff 

(i) $S_k\le Y_1+...+Y_k,k=1,...,n-1$.

(ii) $Y_1+...+Y_n=t$

(iii) There are $n-1$ arrivals in $(0,t)$. (along with $t=0$, $n$ customers are served.)

Denote the busy period $(T,M)$ where $T$ is the length and $M$ is the number of customers. Let $f_{T,M}(t,m)=\partial_t P(T\le t, M=m)$, we have 
$$
\begin{aligned}
f_{T,M}(t,m)&=\partial_t P(\sum_{i=1}^{M} Y_i\le t, M=m,S_k\le\sum_{i=1}^{k} Y_i\ \forall k\le M-1)
\\&=P(S_k\le\sum_{i=1}^{k} Y_i,\ \forall k\le m-1\mid M=m,\sum_{i=1}^{m} Y_i=t)\partial_t P(\sum_{i=1}^{m} Y_i\le t,M=m)
\\\partial_t P(\sum_{i=1}^{m} Y_i\le t,M=m)&=e^{-\lambda t}\frac{(\lambda t)^{m-1}}{(m-1)!}dG^{*m}(t) \text{ by independence of }Y_i\text{ and }M
\end{aligned}
$$
and again by **Theorem 2.3.1**, suppose $\tau_i$ are **ordered** $m-1$ r.v.'s $\sim U(0,t)$,
$$
\\P(S_k\le\sum_{i=1}^{k} Y_i,\ \forall k\le m-1\mid M=m,\sum_{i=1}^{m} Y_i=t)=P(\tau_k\le \sum_{i=1}^{k} Y_i\ \forall k\le m-1\mid \sum_{i=1}^{m}Y_i=t)
$$
To calculate these, we need a series of lemmas.

**Lemma 2.3.3** If $Y_i$ are i.i.d. and nonnegative, then $E[\sum_{i=1}^{k} Y_i\mid \sum_{i=1}^{n} Y_i=y]=\frac{k}{n} y$.

<font color='red'>_proof of Lemma 2.3.3_</font> For any $|S|\subset \{1,...,n \}$ and $|S|=k$, we know $(Y_i)_{i\in S}=_d (Y_i)_{i=1}^k$, assuming the first vector has increasing index. So we have:
$$
\binom{n}{k}E[\sum_{i=1}^{k} Y_i\mid \sum_{i=1}^{n} Y_i=y]=\binom{n-1}{k-1}E[\sum_{i=1}^{n} Y_i\mid \sum_{i=1}^{n} Y_i=y]=\binom{n-1}{k-1}y
$$
which proves the result.

**Lemma 2.3.4** Let $\tau_i$ denote the **ordered** values from $n$ r.v.'s i.i.d. $\sim U(0,t)$, $Y_i$ i.i.d. nonnegative r.v.'s independent of $\tau_i$, then 
$$
P(\sum_{i=1}^{k}Y_i\le\tau_k\ \forall k\le n|\sum_{i=1}^{n} Y_i=y)=\left\{\begin{aligned}&1-y/t&0<y<t\\&0&\text{otherwise}\end{aligned}\right.:=(1-y/t)_+
$$
<font color='red'>_proof of Lemma 2.3.4_</font> Use induction on $n$. 

- when $n=1$, $LHS=P(y\le \tau_1)=RHS$.

- if this holds for $1,...,n-1$, for $n$, suppose $y<t$, since it's trivial when $y>t$, the prob. is 0.
  $$
  \begin{aligned}
  &P(\sum_{i=1}^{k}Y_i\le\tau_k\ \forall k\le n|\sum_{i=1}^{n}Y_i=y)
  \\&=\int P(\sum_{i=1}^{k} Y_i\le \tau_k\ \forall k\le n-1,y\le\tau_n\mid \sum_{i=1}^{n} Y_i=y, \sum_{i=1}^{n-1}Y_i=s,\tau_n=r)dP(\sum_{i=1}^{n-1}Y_i\le s\mid \sum_{i=1}^{n} Y_i=y)dP(\tau_n\le r)
  \\&=\int 1_{y\le r}P(\sum_{i=1}^{k} Y_i\le\tau_k\ \forall k\le n-1|\sum_{i=1}^{n-1}Y_i=s,\tau_n=r)dP(\sum_{i=1}^{n-1} Y_i\le s\mid \sum_{i=1}^{n} Y_i=y)dP(\tau_n\le r)
  \\&=\int 1_{y\le r} (1-s/r)_+d(r/t)^ndP(\sum_{i=1}^{n-1}Y_i\le s\mid\sum_{i=1}^{n} Y_i=y)
  \\&=\int1_{y\le r}[\int (1-s/r)_+dP(\sum_{i=1}^{n-1}Y_i\le s|\sum_{i=1}^{n} Y_i=y)]d(r/t)^n
  \\&=\int1_{y\le r}(1-\frac{n-1}{rn}y)d(r/t)^n
  \\&=t^{-n}\int_{[y,t]}nr^{n-1}-y(n-1)r^{n-2}dr=1-t/y
  \end{aligned}
  $$

> [!IMPORTANT]
>
> The result is surprisingly simple. It comes from the ballot problem.
>
> **Strict ballot problem** Suppose candidate A receives $a$ votes and candidate B receive $b$ votes, with $a>b$, and all vote orderings (totally $\binom{a+b}{a}$) are equally likely. If we denote the event that A is always ahead of B by $A_{a,b}$, we have $P(A_{a,b})=\frac{a-b}{a+b})$.
>
> <font color='red'>_proof_</font> We can derive the formular for $P(A_{a,b})$ by conditioning on the last vote,
> $$
> P(A_{a,b})=P(A_{a-1,b})\frac{a}{a+b}+P(A_{a,b-1})\frac{b}{a+b}
> $$
> This is because: now that $a>b$, A must be ahead at the last vote. So A keeps ahead $\Leftrightarrow$ A keeps ahead before the last vote.
>
> The boundary conditions are $P(A_{a,a})=0$, and $P(A_{2,1})=1/3$. Use induction on $a+b$, we can conclude $P(A_{a,b})=\frac{a-b}{a+b}$.
>
> **Weak version** under the same settings (but we allow $a\ge b$) , let $B_{a,b}$ be the event that A is never behind B, we have $P(B_{a,b})=\frac{a-b+1}{a+1}$.
>
> <font color='red'>_proof_</font> By conditioning on the last vote, the formular is exactly that of the strict problem. When $a>b$, the reason is the same. When $a=b$, notice $B_{a,a}$ holds only when the last vote is $B$, since otherwise before the last vote $B$ must go ahead. In this case, $P(B_{a-1,a})=0$, so it holds, too.
>
> Given boundary condition $P(A_{a-1,a})=0$ and $P(A_{1,1})=1/2$, use induction on $a+b$.
>
> (Above will not be applied below)
>
> **Cycle lemma** This is cyclic ballot problem. Let $(x_1,..,x_n)$ be a tuple where $x_i\in\{0,1\}$, and $\sum_{i=1}^{n} x_i=r$. Among all its cycle shifts, i.e., $(x_1,...,x_n)(x_2,...,x_n,x_1),...,(x_n,x_1,...,x_{n-1})$, $r$ of them satisfies: the sum of first $k$ terms are positive for all $k$.
>
> <font color='red'>_proof_</font> The condition happens iff the first term is 1.
>
> Return to the theorem. First, let $M$ denote the number of points that fall into $(0,y)$, we know $M\sim B(n,y/t)$.
>
> Condition on $S_n=y$ and $M=m$, then split $(0,y)$ into $n$ random intervals of lengths $Y_1,...,Y_n$. Since $Y_i$ are i.i.d., these intervals are **exchangeable**, so invariant under cyclic shift. Let $a_i$ be the number of uniform points falling in the $i$th interval, we have $\sum_{i=1}^{n} a_i=m$. The condition $\sum_{i=1}^{k} Y_i<\tau_k$ is just $\sum_{i=1}^{k} a_i\le k-1$.
>
> Rewrite this to use the cyclic lemma: let $x_i=1-a_i$, then the conditions become: $\sum_{i=1}^{n} x_i=n-m$ and $\sum_{i=1}^{k} x_i\ge 1$ for all $k$. This happens with probability $(n-m)/n$.
>
> The final probability is given by $E\frac{n-m}{n}=1-y/t$.

**Lemma 2.3.5** Let $\tau_i$ denote the **ordered** values from $n-1$ r.v.'s i.i.d. $\sim U(0,t)$, $Y_i$ i.i.d. nonnegative r.v.'s independent of $\tau_i$, then $P(\sum_{i=1}^{k} Y_i<\tau_k\forall k\le n-1|\sum_{i=1}^{n} Y_i=t)=1/n$.

<font color='red'>_proof of Lemma 2.3.5_</font>
$$
LHS=\int P(\sum_{i=1}^{k}Y_i<\tau_k\forall k\le n-1\mid \sum_{i=1}^{n-1}Y_i=s)dP(\sum_{i=1}^{n-1}Y_i\le s\mid \sum_{i=1}^{n}Y_i=t)=\int (1-s/t)_+dP(\sum_{i=1}^{n-1}Y_i\le s\mid \sum_{i=1}^{n}Y_i=t)=1/n
$$
Combine these lemmas, we return to compute.

First we transform the form of the lemma to apply them. Notice if $Z_i$ are i.i.d. $\sim U(0,t)$, then $(Z_1,...,Z_n)=_d(t-Z_1,...,t-Z_n)$, so $(Z_{(1)},...,Z_{(n)})=_d (t-Z_{(n)},...,t-Z_{(1)})$. By this,
$$
\begin{aligned}
&P(\tau_k\le \sum_{i=1}^{k} Y_i\ \forall k\le m-1\mid \sum_{i=1}^{n}Y_i=t)\\&=P(t-\tau_{n-k}\le \sum_{i=1}^{k}Y_i\forall k\le m-1\mid \sum_{i=1}^{n}Y_i=t)=P(t-\tau_{n-k}\le t-\sum_{i=k+1}^{n}Y_i\forall k\le n-1\mid \sum_{i=1}^{n} Y_i=t)\\&=P(\tau_{n-k}\ge \sum_{i=k+1}^{n}Y_i\forall k\le n-1\mid \sum_{i=1}^{n} Y_i=t)=P(\tau_{n-k}\ge\sum_{i=1}^{n-k}Y_i\forall k\le n-1\mid \sum_{i=1}^{n} Y_i=t)\\&=P(\sum_{i=1}^{k}Y_i\le \tau_k\forall k\le n-1\mid \sum_{i=1}^{n} Y_i=t)=1/n
\end{aligned}
$$
So $f_{T,M}(t,m)=e^{-\lambda t}\frac{(\lambda t)^{m-1}}{m!}dG_m(t)$, and $f_T(t)=\sum_{m=1}^\infty f_{T,M}(t,m)$.

### 2.4 Nonhomogeneous Poisson process

"Nonhomogeneous" means the rate can vary w.r.t $t$.

**Definition** The counting process $N(t)$ is said to be a **nonstationary** or **nonhomogeneous** Poisson process with intensity function $\lambda(t)$ if 

(i) $N(0)=0$ 

(ii) $N(t)$ has independent increments 

(iii) $P(N(t+h)-N(t))\ge 2=o(h)$

(iv) $P(N(t+h)-N(t)=1)=\lambda(t)h+o(h)$.

**Proposition** Let $m(t)=\int_0^t \lambda(s) ds$, $N(t+s)-N(t)\sim P(m(t+s)-m(t))$.

The proof is similar as that in the case $\lambda$ is constant.

_Remark_ Since we drop the assumption of stationary increments, we can assign more probabilities at certain time.

When $\lambda(t)$ is bdd and $\lambda(t)<\lambda$, we can attain a nonhomogeneous Poisson process by running a $P_\lambda(t)$, and keep the event that happen at time $t$ with prob. $\lambda(t)/t$, independently of the process. This can be verified through the definition directly. This gives us an insight into **Proposition 2.3.2**, or we can use that proposition to prove this.

**Example 2.4(A) Record values** Let $X_i$ i.i.d. with hazard rate function $\lambda(t)$. We say that a record occur at time $n$ if $X_n>\max(X_1,...,X_{n-1})$, where $X_0=0$. If a record occurs at time $n$, then $X_n$ is called a record value. Let $N(t)$ denote the number of record values $\le t$, i.e., the counting process of events that happens at $x$ if the record value is $x$. Now we claim $N(t)$ is a nonhomogeneous Poisson process with intensity $\lambda(t)$. 

_Remark_ The "real time" is index $n$. $t$ is the level.

> [!NOTE]
>
> Consider a cts r.v. $X$ with c.d.f. $F$ and density $f$. The **failure** or **hazard** rate function is defined by: $\lambda(t)=f(t)/(1-F(t))$. To understand this, think of $X$ as a lifetime and suppose now $X$ has survived for $t$. Then it dies in the next $dt$ with prob. 
> $$
> P(X\in(t+dt)|X>t)=\frac{P(X\in(t,t+dt),X>t)}{P(X>t)}\approx\frac{f(t)}{1-F(t)}dt
> $$
> so $\lambda(t)$ is the intensity that a $t$-year-old item will fail.
>
> _Remark_ If $X\sim Exp(\lambda)$, we can verify $X$ has $\lambda(t)=\lambda$. This implies the "memoryless property".
>
> _Remark_ The inverse of the last remark is also true, since $\lambda(t)$ determines the distribution of $X$ uniquely. This is just an ODE.

- $N(0)=0$ by definition.
- $N(t)$ has independent increments: suppose $0<t_1<...<t_n$, then $N(t_n)-N(t_{n-1})$ is independent of $N(t_i)-N(t_{i-1}),i<n$, since we need only to care about those values $>t$.
- notice $N(t+h)-N(t)=1$ iff the first record greater than $t$ is less than $t+h$. If the first is $X_n$,  we have $P(X_n\in (t,t+h)|X_n>t)=\lambda(t) h+o(h)$ from the definition of $\lambda(t)$. Since RHS is irrelevant to $t$, $P(N(t+h)-N(t)=1)=\lambda(t)h+o(h)$.
- notice $N(t+h)-N(t)=0$ iff the first record greater than $t$ is greater than $t+h$, and if the first is $X_n$ we have $P(X_n>t+h|X_n>t)=1-P(X_n\in (t,t+h)|X_n>t)=1-\lambda(t)h+o(h)$. 

so $N(t)$ is a Poisson with intense $\lambda(t)$.

**Example 2.4(B) M/G/$\infty$ queue** Suppose service desk is infinite, customers arrive $\sim P_\lambda (t)$, and service time has c.d.f. $G$, then the output process, i.e., the counting process of customers whoever completed their service by time $t$, is a nonhomogeneous Poisson process with intensity $\lambda(t)=\lambda G(t)$. Denote this by $N(t)$.

- $N(0)=0$ by definition.

- independent increments: By **Proposition 2.3.2** (remark), since the service times are independent of the arrival, pick disjoint time intervals, for any $t$, the event occurs at this time has probabilities to leave in those time intervals or other time (different types) that are functions depending only on $t$. So the departures inside those intervals have independent Poisson laws.

- Along this idea, it suffices to verify $N(t+s)-N(t)\sim P(\lambda \int_s^{s+t} G(y)dy)$. Denote $p(y)$ to be the probability for an event that occurred at time $t$ to leave during $[t,t+s]$, then 
  $$
  p(y)=\left\{\begin{aligned}&G(s+t-y)-G(s-y)&y<s\\&G(s+t-y)&s<y<s+t\\&0&y>s+t\end{aligned}\right.
  $$
  Consider by time $s+t$ the number of departure, it's Poisson with mean $\lambda\int_0^{s+t} P(y)dy=\lambda \int_s^{s+t} G(y)dy$. Use this, we can verify the definition directly.

_Remark_ $\lambda(t)\to\lambda$ as $t\rightarrow\infty$, so $N(t)$ is nearly $P_\lambda(t)$ when $t$ is large.

### 2.5 Compound Poisson random variables and processes

**Definition** Let $X_i$ be i.i.d. with c.d.f. $F$, $N\sim P(\lambda)$ independent of $X_i$, and $W=\sum_{i=1}^{N} X_i$. $W$ is said to be a **compound Poisson r.v.** with Poisson parameter $\lambda$ and component distribution $F$.

**Proposition** The moment generating function of $W$, $\psi_W(t)=\exp(\lambda (\psi_X(t)-1))$.

<font color='red'>_proof_</font> 
$$
Ee^{tW}=E[E[e^{tW}\mid N]]=E[E[\prod_{i=1}^N e^{tX_i}\mid N]]=E[\psi_X^N]=\sum_{i=0}^\infty \psi_X(t)^i\frac{\lambda^i}{i!}e^{-\lambda}=\exp(\lambda(\psi_X-1))
$$
**Corollary** $EW=\lambda EX$, $var(W)=\lambda EX^2$.

**Example 2.5 (A)** Compound Poisson process often arises in this way: Suppose $N(t)\sim P_\alpha (t)$, and if the event occurs at time $s$, its contribution is a r.v. with c.d.f. $F_s$ (To treat rigorously, suppose $F_s(x)=F(s,x)$ is measurable), which is independent of the past. Then by time $t$, the contribution $W=\sum_{i=1}^{N(t)} X_i$. 

$X_i$ are neither independent nor identically distributed, since the distribution depends on time: for example, consider $F_s(x)=1_{x\ge s}$, then if $X_i$ occurs at time $s$, $X_i=s$ a.s., so $X_1<X_2<...$ a.s., but actually $X_i\sim Gamma(i,\alpha)$.

However, $W$ is a compound Poisson process, with parameter $\lambda=\alpha t$ and $F(x)=t^{-1}\int_0^t F_s(x) ds$.

<font color='red'>_proof_</font> Condition on $N(t)$, the time of each occurrence is uniform on $(0,t)$, so conditionally there are $N(t)$ r.v. i.i.d. with distribution function $F(x)=\int_0^t F_s(x)f_U(s)ds=t^{-1}\int_0^t F_s(x)ds$. So $W$ is exactly a compound Poisson r.v..



Return to the primary definition. When $F$ takes value on a finite discrete set, wlog $P(X_i=j)=p_j, 1\le j\le n$, we have $W=\sum_{i=1}^{n} jN_j$, where $N_j\sim P(\lambda p_j)$ by elementary calculations. by this we can verify the formular for $EW$ and $var(W)$.

#### 2.5.1 A compound Poisson identity

**Proposition 2.5.2** Under the settings for a compound Poisson r.v., let $X$ be a r.v. with c.d.f. $F$ and independent of $W$, then for any function $h(x)$, $E[Wh(W)]=\lambda E[Xh(W+X)]$.

<font color='red'>_proof of Proposition 2.5.2_</font> 
$$
\begin{aligned}
E[Wh(W)]&=\sum_{n=1}^\infty E[Wh(W)|N=n]e^{-\lambda}\frac{\lambda^n}{n!}
\\&=\sum_{n=1}^\infty e^{-\lambda}\frac{\lambda^n}{n!}E[\sum_{i=1}^{n} X_ih(\sum_{j=1}^{n}X_j)]
\\&=\sum_{n=1}^\infty e^{-\lambda}\frac{\lambda^n}{n!}\sum_{i=1}^{n}E[X_ih(\sum_{j=1}^{n} X_j)]
\\&=\sum_{n=1}^\infty e^{-\lambda}\frac{\lambda^n}{n!}nE[X_nh(\sum_{j=1}^{n} X_j)]\text{ since }X_i\text{ are i.i.d.}
\\&=\sum_{n=1}^\infty e^{-\lambda}\frac{\lambda^n}{(n-1)!}\int E[X_n h(\sum_{j=1}^{n} X_i)\mid X_n=x]dF(x)
\\&=\sum_{n=1}^\infty e^{-\lambda}\frac{\lambda^n}{(n-1)!}\int E[xh(\sum_{j=1}^{n-1}X_i+x)]dF(x)
\\&=\lambda\int [\sum_{n=1}^\infty e^{-\lambda}\frac{\lambda^{n-1}}{(n-1)!}E[xh(\sum_{j=1}^{n-1}X_i+x)]]dF(x)\text{ by Fubini}
\\&=\lambda \int E[xh(W+x)]dF(x)=\lambda E[Xh(W+X)]\text{ by Fubini}
\end{aligned}
$$
**Corollary 2.5.3** If $X$ has c.d.f. $F$, then $E[W_n]=\lambda \sum_{j=0}^{n-1}\binom{n-1}{j} E[W^j]W[X^{n-j}]$.

<font color='red'>_proof of Corollary 2.5.3_</font> Pick $h(x)=x^{n-1}$, we have 
$$
E[W^n]=\lambda E[X(X+W)^{n-1}]=\lambda\sum_{j=0}^{n-1}\binom{n-1}{j} E[W^j]E[X^{n-j}]\text{by independence}
$$
By this, we can use induction to get every moment of $W$.

**Corollary 2.5.4** If $X$ is $Z_{>0}$-valued, let $\alpha_j=P(X=j)$ and $P_j=P(W=j)$, we have $P_0=e^{-\lambda}$ and $P_n=\frac{\lambda}{n}\sum_{j=1}^{n} j\alpha_j P_{n-j}$.

<font color='red'>_proof of Corollary 2.5.4_</font> $P_0=e^{-\lambda}$ is trivial. For $P_n$, pick $h(x)=\frac{1}{n} 1_{n}(x)$, so $Wh(W)=1_{W=n}$, and 
$$
P(W=n)=\lambda E[Xh(W+X)]=\lambda\sum_j E[Xh(W+X)|X=j]\alpha_j=\lambda \sum_j \frac{j}{n}P_{n-j}\alpha_j
$$

#### 2.5.2 Compound Poisson process

**Definition** A s.p. $(X(t))$ is said to be a **compound Poisson process** if it can be represented by $X(t)=\sum_{i=1}^{N(t)} X_i$, where $N(t)$ is a Poisson process, $X_i$ are i.i.d. and independent of $N(t)$. In this case, for every $t$, $X(t)$ is a compound Poisson r.v..

### 2.6 Conditional Poisson processes

**Definition** Let $\Lambda$ be a positive r.v. with c.d.f. $G$, $N(t)$ a counting process s.t. conditioning on $\Lambda=\lambda$, $N(t)\sim P_\lambda(t)$. Then $(N(t))$ is called a conditional Poisson process. 

In this case, $P(N(t+s)-N(s)=n)=\int_0^\infty e^{-\lambda t}\frac{(\lambda t)^n}{n!}dG(\lambda)$, i.e., $N(t)$ has stationary increments. But it doesn't have independent increments: suppose $a<b<c<d$, $P(N(d)-N(c)=m,N(b)-N(a)=n)=\int_0^\infty e^{-\lambda(d-c)}\frac{(\lambda (d-c))^m}{m!}e^{-\lambda(b-a)}\frac{(\lambda (b-a))^n}{n!}dG(\lambda)$,which isn't separable in general. So it isn't a Poisson process in general.

We can, by Bayes Formular, determine the distribution of $\Lambda$ given $N(t)$. It's given by 
$$
P(\Lambda\le x|N(t)=n)=\frac{\int_0^x P(N(t)=n\mid \Lambda= x)dG(\lambda)}{\int_0^\infty P(N(t)=n\mid\Lambda=\lambda)dG(\lambda)}
$$

***

Below are exercises.
