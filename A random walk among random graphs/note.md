This note mainly consists of remarks among chapters.

#### 1.1 Basic on graphs

_proof of Lemma 1.2 König's lemma_ 

(i)$\Rightarrow$(ii) Pick $S$ to be the set of all finite self-avoiding paths. Construct a tree from $S$ by setting the root to be an empty path and setting $\gamma_2$ to be the child of $\gamma_1$ if $\gamma_2=\gamma_1+v$ with $v\in V$. Notice $|S|=\infty$ since at least every vertex corresponds to a path in $S$. Meanwhile, the tree is locally finite since $\mathfrak g$ is. So the tree must be of infinite depth, from which we can pick a infinite path.

(ii)$\Rightarrow$(iii) Truncate the path.

(iii)$\Rightarrow$(i) This has already shown that the connected component of $v_0$ is infinite.

#### 1.4 Two graphs

_proof of theorem 1.5_ 

To make it simpler, let $L_n$ be the set of vertices of level $n$. To compute, we need to consider the vertex where the path $v_0\leftrightarrow x$ and $v_0\leftrightarrow y$ split. Denote this vertex by $x\wedge y$
$$
\begin{aligned}
&\sum_{x,y\in L_n}P(v_0\leftrightarrow x,v_0\leftrightarrow y)\\=&\sum_{x,y\in L_n} P(v_0\leftrightarrow x\wedge y, x\wedge y\leftrightarrow x,x\wedge y\leftrightarrow y)\\=&2\sum_{i=0}^{n-1} 2^i (2^{n-i-1})^2p^i p^{n-i} p^{n-i}+2^n p^n\\=&(2p)^n (1+p+...+2^{n-1} p^n)
\end{aligned}
$$

#### 2.2 Walks with finite mean and the law of large numbers

_proof of theorem 2.4_

For n large, $\lim_{n \to \infty}\sum_{i=0}^n P(|S_i|\le \epsilon i)/n=\lim_{n \to \infty} P(|S_n|/n\le \epsilon)=1$, so for large $n$ the inequality holds.

_Solution to exercise 2.1_ 

Let $X_n\sim \mu$, then $EX_n=0,E|X_n|=\infty, EX_n^2=\infty$. 

First, $kP(X_n\ge k)=k\sum_{i=k}^\infty (i^2\log i)^{-1}=O((\log k)^{-1})\to 0$. By truncation argument, $S_n/n\to 0$ in probability. 

Next, let $A_n=\{|X_n|>n \}$. If $S_n/n\to 0$ a.s., one have $X_n/n=S_n/n-S_{n-1}/(n-1)\times (n-1)/n\to 0$ a.s., i.e., $A_n$ happens for finite times. But $P(A_n)=O((k\log k)^{-1})$ which is not summable. By the second Borel Cantelli lemma and the independence of $A_n$, $|X_n|/n>1$ i.o., which leads to contradiction.

This example shows that, though $S_n/n\to_p 0$, maybe $X_n\notin L^1$.

_Solution to exercise 2.3_ ==To be solved==

_Solution to exercise 2.5_ 

(i) Let $S_n=n$ and $S'_n=-n$.

(ii) Suppose $S_n$ is transient. In this case, $\hat\mu(t),\hat\mu'(t)\in [-1,1]$ and $(1-\hat\mu(t))^{-1},(1-\hat\mu'(t))^{-1}$ are integrable. We have 
$$
0\le\frac{1}{1-\hat\mu(t)\hat\mu'(t)}=\frac{1+\hat\mu(t)\hat\mu'(t)}{1-\hat\mu(t)^2\hat\mu'(t)^2}\le\frac{2}{1-\hat\mu(t)^2\hat\mu'(t)^2}\le \frac{2}{1-\hat\mu(t)^2}
$$
Notice $(1-\hat\mu(t)^2)$ is integrable since $S_{2n}$ is symmetric transient random walk, $\frac{1}{1-\hat\mu(t)\hat\mu'(t)}$ is also integrable. 

(iii) Let $S_n$ has Cauchy increments with shift 1, i.e., $\hat\mu(\xi)=e^{-|\xi|+i\xi}$, and $S_n'=-n$. Then $S_n$ is recurrent, since $\Re(1-e^{-|\xi|+i\xi})^{-1}=O(1/2|\xi|)$ near 0, which is not integrable. $S_n'$ is trivially transient. But $S_n+S_n'$ is recurrent, since the increments has ch.f. $e^{-|\xi|}$, and $(1-e^{-|\xi|})^{-1}$ is not integrable. 

(iv) from (iii).

_Solution to exercise 3.1_
$$
\begin{aligned}
P(S_{T_{\mathbb Z>0}}=k)&=\sum_n P(S_1\le 0,...,S_{n-1}\le 0, S_n=k)
\\&=^1\sum_n P(S_n-S_{n-1}\le 0,..., S_n-S_0=k)
\\&=\sum_n P(S_1\ge k,..., S_{n-1}\ge k, S_n=k)
\\&=\sum_{n}\sum_{i\ge k}\mu_i P(S_2,...,S_{n-1}\ge k, S_n=k\mid S_1=i)
\\&=^2\sum_n \sum_{i\ge k}\mu_i P(S_1,...,S_{n-2}\ge k-i, S_{n-1}=k-i)
\\&=^3\sum_{i\ge k}\mu_i \sum_n P(S_1,...,S_{n-2}\ge k-i,S_{n-1}=k-i)
\\&=^4\sum_{i\ge k}\mu_i E\text{ the number of visits to }k-i\text{ before visiting }k-i-1\\&=^5\sum_{i\ge k}\mu_i \mu_{-1}^{-1}
\end{aligned}
$$
1: duality

2: The process has stationary increments

3: Fubini

4: The walk is skip-free

5: The increments has mean 0, so the walk is recurrent, so it must visit $k-i$. So its visiting times have geometric law with success probability $\mu_{-1}$ (As long as it doesn't go downward, it will finally return). 

#### 3.1.2 A proof of the law of large numbers

_From Lemma 3.3 to SLLN_ 

Suppose $EX_i=0$. Pick $\epsilon$. Then $\sup_{n\ge 0}(S_n-n\epsilon)<\infty$ a.s., whence $\sup_{n\ge 0}S_n/n-\epsilon\le 0$ a.s.. Similarly $\inf_{n\ge 0}S_n/n+\epsilon\ge 0$ a.s.. Let $\epsilon$ small enough, one can obtain SLLN.

#### 3.2 Cycle lemma

_Solution to exercise 3.2_ 

Pick a path $s$ where $k$ is the first time to take the maximum. Notice $s^{k}$ corresponds to a path whose hitting time of $1$ is $n$ and before $n$ the path is below the axis. So WLOG let $s$ be the path where $n$ is the first time to take the maximum. Notice now $s^{l}$ corresponds to a path where $n-l$ is the first time to take the maximum. Under this symmetry, one can directly conclude that $K_n$ is uniform. 

#### 3.2.3 Simple symmetric random walk

_Remark_ The arc-sine law for BM is: arc-sine distribution has c.d.f. $F(x)=\frac{2}{\pi} \arcsin \sqrt{x}$, then

(i) $A:=\int_0^1 \mathbb 1_{B_t>0}dt\sim\text{Arcsine}(0,1)$

(ii) $L:=\sup\{t\le 1: B_t=0 \}\sim \text{Arcsine}(0,1)$

(iii) $T_{\max}:=\arg\max_{0\le t\le 1}B_t\sim \text{Arcsine}(0,1)$

_proof of Proposition 3.6_ 

For the first line of identity, $K_n=k$ can be split into two independent events from the independence of increments: In the first $k$ step, $S_k$ is the first to reach the maximum; in the last $n-k$ step, $S_m-S_k\le 0$. 

By duality lemma, the first event has probability
$$
P(S_k\ge S_1,...,S_{k-1})=P(S_1,...,S_k>0)=P(S_1>0, T_0^+>k)
$$
Since $S_n-S_k=_d S_{n-k}$, one have 
$$
P(S_{k+1},...,S_n\le S_k)=P(S_1,...,S_{n-k}\le 0)=P(T_1>n-k)=P(T_{-1}>n-k)
$$
the last identity comes from the symmetry of RW.

For the second line of inequality, 
$$
P(T_0^+>k, S_1>0)=\frac{1}{2}P(T_0^+>k\mid S_1>0)=\frac{1}{2}P(T_{-1}>k-1)
$$
(no symmetry is involved)

#### 3.3.1 Ballot theorem 

_proof of lemma 3.7_
$$
\begin{aligned}
P(S_i>0,\forall 1\le i\le n, S_n=k)&=P(X_1>0,X_1+X_2>0,...,X_1+...+X_{n-1}>0, X_1+...+X_n=k)\\&=P(X_n>0,X_n+X_{n-1}>0,...,X_n+...+X_2>0,X_n+...+X_1=k)\\&=P(T_k(S)=n)\\&=P(T_{-k}(-S)=n)
\end{aligned}
$$
_proof of proposition 3.10_ 

Conditioned on $S_1$ and notice $T_{<0}=T_{-1}$, 
$$
\begin{aligned}
P(T_{<0}<\infty)&=\sum_{n=-1}^\infty P(S_1=n)P(\bigcap_{i=0}^n\{\theta_{i+1}-\theta_i<\infty \})\\&=\sum_{n=-1}^\infty \mu_n P(T_{<0}<\infty)^{n+1}
\end{aligned}
$$
_Solution to exercise 3.4_ 

Since $S$ is a skip-free descending RW and drifts towards $+\infty$, $P(T_{-1}<\infty)
