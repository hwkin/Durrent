## Chapter 3 Central Limit Theorems

### 3.1 The De Moivre-Laplace theorem

Let $X_i,X_2,...$ be i.i.d. with $P(X_1=1)=P(X_1=-1)=1/2$ and let $S_n=X_1+...+X_n$, then we know $P(S_{2n} = 2k) = \binom{2n}{n + k} 2^{-2n}$. By Stirling Formular,
$$
\binom{2n}{n + k} 2^{-2n}\sim\big(1-\frac{k^2}{n^2}\big)^{-n}\big(1+\frac{k}{n}\big)^{-k}\big(1-\frac{k}{n}\big)^k\big(\pi n\big)^{-1/2}\big(1+\frac{k}{n}\big)^{-1/2}\big(1-\frac{k}{n}\big)^{-1/2}
$$
introduce a lemma,

**Lemma 3.1.1** If $c_j\to 0$, $a_j\to\infty$, $a_jc_j\to\lambda$, then $(1+c_j)^{a_j}\to e^\lambda$.

Then we can see if $2k=x\sqrt{2n}$, we have 
$$
\big(1-\frac{k^2}{n^2}\big)^{-n}\big(1+\frac{k}{n}\big)^{-k}\big(1-\frac{k}{n}\big)^k\sim e^{x^2/2}\cdot e^{-x^2/2}\cdot e^{-x^2/2}
$$
and $(1+k/n)^{-1/2}(1-k/n)^{-1/2}\to 1$ as $n\to\infty$. Combine these, we have 

**Theorem 3.1.2** If $2k/\sqrt{2n}\to x$, then $P(S_{2n}=2k)\sim(\pi n)^{-1/2}e^{-x^2/2}$.

Next let's estimate $P(a\sqrt{2n}\leq b\sqrt{2n})$.
$$
P(a\sqrt{2n}\leq b\sqrt{2n})=\sum_{m\in[a\sqrt{2n},b\sqrt{2n}]\cap 2\mathbb Z}P(S_{2n}=m)\approx \sum_{x\in[a,b]\cap(2\mathbb Z/\sqrt{2n})}(2\pi)^{-1/2}e^{-x^2/2}(2/n)^{1/2}\approx\int_a^b (2\pi)^{-1/2}e^{-x^2/2}dx
$$
Formalize this and pass even numbers to all integers, we have

**Theorem 3.1.3 The De Moivre-Laplace Theorem** If $a<b$ then as $m\to\infty$, $P(a\leq S_m/\sqrt{m}\leq b)\to\int_a^b (2\pi)^{-1/2}e^{-x^2/2}dx$.

_Remark_ This is a special case of CLT.

### 3.2 Weak Convergence

**Definition** A sequence of distribution functions is said to **converge weakly** to a limit $F$ if $F_n(y)\to F(y)$ for all $y$ that are continuity points of $F$. Say a sequence of r.v. s $X_n$ **converge weakly** or **converge in distribution** to a limit $X_\infty$ if their distribution functions $F_n(x)$ converges weakly to $F$.

#### 3.2.1 Examples

**Example 3.2.1** Let $X_1,X_2,...$ be i.i.d. with $P(X_i=1)=P(X_i=-1)=1/2$, then by De Moivre-Laplace, $F_n(y)\to\int_{-\infty}^y (2\pi)^{-1/2}e^{-x^2/2}dx$.

**Example 3.2.2** Let $X_1,X_2,...$ be i.i.d. with distribution $F$. The Glivenko-Cantelli theorem (will be presented later) implies that for almost every $\omega$, $F_n(y)=n^{-1}\sum_{m=1}^n 1_{X_m(\omega)\leq y}\to F(y)$ for all $y$. This is, the distribution of $S_n/n$ converges to $F$.

These converges hold for every $y$.

**Example 3.2.3** Let $X$ has distribution $F$, then $X+1/n$ has distribution $F(x-1/n)$, so as $n\to\infty$, $F_n(x)\to F(x-)$, and $F$ is right-cts. So convergence only occurs at continuity points.

**Example 2.3.4 Waiting for rare events** Let $X_p\sim G(p)$, then $P(pX_p>x)\to e^{-x}$ for all $x\geq 0$ as $p\to 0$, i.e., $pX_p\to_d Exp(1)$.

**Example 3.2.5 Birthday problem** LEt $X_1,X_2,...$ be independent and uniformly distributed on $\{1,...,N\}$, and let $T_N=\min\{n: X_n=X_m\text{ for some }m<n \}$, then $P(T_N>n)=\prod_{m=2}^n (1-\frac{m-1}{N})$. Moreover, $P(T_N/N^{1/2}>x)\to e^{-x^2/2}$ for all $x\ge 0$.

Before the next example, we need a simple result called **Scheffe's Theorem**. Suppose we have probability densities $f_n$ and $f_n\to f_\infty$ pointwise. Then for all Borel sets $B$, 
$$
\bigg|\int_B f_n(x)-\int_B f_\infty (x)\bigg|\leq \int|f_n-f_\infty|=2\int(f_\infty-f_n)^+dx\to 0
$$
by DCT. So the **total variation norm** $\|\mu_n-\mu_\infty\|\equiv \sup_B |\mu_n(B)-\mu_\infty (N)|\to 0$. Take $B=(-\infty,x]$ we can get weak convergence. 

But the norm converging to 0 is not necessary for weak convergence. If $X_n=1/n$, $X_0=0$, then $X_n\to_d X_0$ but $\|X_n-X_0\|\equiv 1$.

**Example 3.2.6 Central order statistic** Put $(2n+1)$ points at random in $(0,1)$. Let $V_{n+1}$ be the $(n+1)$th largest point. It's easy to see that

**Lemma 3.2.7** $V_{n+1}$ has density function $f_{V_{n+1}}(x)=(2n+1)\binom{2n}{n}x^n(1-x)^n$.

Let $Y_n=2\sqrt{2n}(V_{n+1}-1/2)$, then 
$$
f_{Y_n}(y)=(2n+1)\binom{2n}{n}\big(\frac{1}{2}+\frac{y}{2\sqrt{2n}}\big)^n\big(\frac{1}{2}-\frac{y}{2\sqrt{2n}}\big)^n\frac{1}{2\sqrt{2n}}\to (2\pi)^{-1/2}e^{-y^2/2}
$$
By Scheffe's theorem we have $Y_n\to_d \mathcal N (0,1)$.

#### 3.2.2 Theory

**Theorem 3.2.8** If $F_n\to F_\infty$ weakly, then there are r.v.s $Y_n$ with distribution $F_n$ s.t. $Y_n\to Y_\infty$ a.s..

<font color='red'>_proof of Theorem 3.2.8_</font> The idea is to use the generalized inverse. Actually, it suffices to show $F_n^{-1}\to_d F^{-1}$. To see this, we first identify the "exceptional points". Let $a_x=\sup\{y: F(y)<x \}$, $b_x=\inf\{y:F(y)>x \}$, and $\Omega_0=\{x:a_x=b_x\}$, i.e., those values where $F$ isn't constant around. On these points $F^{-1}$ is cts. $\Omega-\Omega_0$ is countable, since $(a_x,b_x)$ are disjoint intervals including rationals. 

For $x\in \Omega_0$, $F(y)<x$ for $y<F^{-1}(x)$ and $F(z)>x$ for $z>F^{-1}(x)$. Now we prove $F_n^{-1}\to F^{-1}$ on $\Omega_0$.

- $\liminf_{n\rightarrow\infty} F_n^{-1}(x)\ge F^{-1}(x)$.

  Let $y<F^{-1}(x)$, and F is cts on $y$. Then $F(y)<x$. For sufficient large $n$, $F_n(y)<x$. So $F_n^{-1}(x)\geq y$. Since $y$ is arbitrary, the limit is true.

- $\limsup_{n\rightarrow\infty} F_n^{-1}(x)\leq F^{-1}(x)$ 

  The procedure is the same. 

In this way, let $\Omega=(0,1)$ with default configuration, and $Y_n=F^{-1}(U)$, then $Y_n\to Y$ a.s..

Apply this, we can get an equivalent definition of weak convergence that make sense in any topological space. The essence is that, weak convergence doesn't care about the underlying event field, it only concerns the distribution function. So carry this to a.s. convergence, we can deal more flexibly.

**Theorem 3.2.9** $X_n\to_d X_\infty$ iff for every bounded cts function g, we have $Eg(X_n)\to Eg(X_\infty)$.

<font color='red'>_proof of Theorem 3.2.9_</font> Let $Y_n=_d X_n$ s.t. $Y_n\to Y_\infty$ a.s.. Since g is bounded cts, by Bounded Convergence Theorem, we have $Eg(X_n)=Eg(Y_n)\to Eg(Y_\infty)=Eg(X_\infty)$.

To prove the converse, pick a family of test functions to verify pointwise convergence of distributions. Let 
$$
g_{x,\epsilon}(y)=\left\{\begin{aligned}&1&y\leq x\\&0&y\geq x+\epsilon\\&\text{linear}&x\leq y\leq x+\epsilon\end{aligned}\right.
$$
So we have
$$
\limsup_{n\rightarrow\infty} P(X_n\leq x)\le \limsup_{n\rightarrow\infty} Eg_{x,\epsilon}(X_n)=Eg_{x,\epsilon}(X_\infty)\leq P(X_\infty\leq x+\epsilon)
$$
And the inverse,
$$
\liminf_{n\rightarrow\infty} P(X_n\leq x)\ge \liminf_{n\rightarrow\infty} Eg_{x-\epsilon,\epsilon}(X_n)=Eg_{x-\epsilon,\epsilon}(X_\infty)\ge P(X_\infty\leq x-\epsilon)
$$
Let $\epsilon\to 0$, if $x$ is a cts point of $X_\infty$, we know $\lim_{n \to \infty} F_n(x)\to F_\infty (x)$.

> [!Note]
>
> In functional analysis, in a normed linear space $X$, for $x_n,x\in X$, we say $x_n$ converges/converges in norm/converges strongly if $\|x_n-x\|\to 0$, and $x_n$ converges weakly if $\forall f\in X^*$, $\lim_{n \to \infty} f(x_n)=f(x)$.

The next is a trivial but useful generalization of **Theorem 3.2.9**. 

**Theorem 3.2.10 Continuous mapping theorem** Let $g$ be a measurable function and $D_g$ is the set of discontinuous points. If $X_n\to_d X_\infty$, and $P(X_\infty\in D_g)=0$, then $g(X_n)\to_d g(X)$. If in addition $g$ is bounded, then $Eg(X_n)\to Eg(X_\infty)$.

<font color='red'>_proof of Theorem 3.2.10_</font> Let $Y_n=_d X_n$ with $Y_n\to Y_\infty$ a.s.. If $f$ is cts, $D_{f\circ g}\subset D_g$, so $P(Y_\infty\in D_{f\circ g})=0$. This follows that $f(g(Y_n))\to f(g(Y_\infty))$ a.s.. If $f$ is bounded, by BCT we have $Ef(g(Y_n))\to Ef(g(Y_\infty))$. This indicates $g(Y_n)\to_d g(Y_\infty)$.

If $g$ is bounded, then $f(x)=x$ is bounded, so $Eg(X_n)\to Eg(X_\infty)$.

The next result provides a number of useful alternative definitions of weak convergence.

**Theorem 3.2.11** TFAE:

(i) $X_n\to_d X$

(ii) $\forall G$ open, $\liminf_{n\rightarrow\infty} P(X_n\in G)\ge P(X_\infty\in G)$.

(iii) $\forall K$ closed, $\limsup_{n\rightarrow\infty} P(X_n\in K)\le P(X_\infty\in K)$.

(iv) $\forall A\in \mathcal B$ with $P(X_\infty\in\partial A)=0$, $\lim_{n \to \infty} P(X_n\in A)=P(X_\infty \in A)$.

<font color='red'>_proof of Theorem 3.2.11_</font> 

(i)$\Rightarrow$ (ii): Let $Y_n=_d X_n$ and $Y_n\to Y_\infty$ a.s., then since $G$ is open, $\liminf_{n\rightarrow\infty} 1_G(Y_n)\geq 1_G (Y_\infty )$.By Fatou's lemma, 
$$
\liminf_{n\rightarrow\infty} P(Y_n\in G)=\liminf_{n\rightarrow\infty}E1_G(Y_n)\geq E\liminf_{n\rightarrow\infty} 1_G(Y_n)\geq E1_G(Y_\infty )=P(Y_\infty \in G)
$$
(ii)$\Leftrightarrow$ (iii) since $A$ is open$\Leftrightarrow$ $A^c$ is closed

(ii),(iii) $\Rightarrow$ (iv) We have $P(X_\infty\in \bar{A})=P(X_\infty \in A)=P(X_\infty \in A^o)$. Take limits by (ii),(iii) and we can reach the conclusion.

(iv)$\Rightarrow$(i): Let $A=(-\infty ,x]$ where $x$ is a cts point of $X_\infty$.

**Theorem 3.2.12 Helly's selection theorem** For every sequence $F_n$ of distribution functions, there is a subsequence $F_{n(k)}$ and a right cts nondecreasing function $F$ s.t. $\lim_{k \to \infty} F_{n(k)}(y)=F(y)$ at all cts points $y$ of $F$.

_Remark_ The limit may be not a distribution function. For example, let $a+b+c=1$, $F_n(x)=a 1_{x\geq n}+b 1_{x\geq -n}+c G(x)$, where $G$ is a distribution function. Notice $F_n(x)\to F(x)=b+cG(x)$, with $F(-\infty )=b$ and $F(+\infty )=b+c=1-a$, i.e., some mass escapes to infinity. Tis type of convergence is sometimes called **vague convergence**.

<font color='red'>_proof of Theorem 3.2.12_</font> The first step is a diagonal argument. Let $q_1,q_2,...$ be an enumeration of the rationals. Since for each $k$, $F_m(q_k)\in [0,1]$ for all $m$, let $m_0(j)=j$, $m_k(j)$ is the subsequence of $m_{k-1}(j)$ such that $F_{m_k}(q_k)$ converges. Let $n(k)=m_k(k)$ the diagonal sequence, then $F_{n(k)}$ converges on every rational number, say the limit function is $G$. From $G$, we construct $F(x)=\inf\{G(q), q\in \mathbb Q , q>x \}$ which is right cts and since $G$ is nondecreasing, we can show $F_{n(k)}\to F$ on every cts point. 

**Theorem 3.2.13** Every subsequential limit is the distribution function of a probability measure iff the sequence $F_n$ is tight, i.e., for all $\epsilon$ there is am $M_\epsilon$ s.t. $\limsup_{n\rightarrow\infty} 1-F_n(M_\epsilon )+F_n(-M_\epsilon )\leq \epsilon$.

_Remark_ This condition is to uniformly control the tail of distribution so that it is small enough.

<font color='red'>_proof of Theorem 3.2.13_</font> 

- If the sequence is tight, and $F_{n(k)}\to_v F$, pick $\epsilon$ and let $r<-M_\epsilon$, $s>M_\epsilon$ be the continuity points of $F$. Since $F_n(r)\to F(r)$ and $F_n(s)\to F(s)$, we have 
  $$
  1-F(s)+F(r)=\lim_{k \to \infty} 1-F_{n(k)}(s)+F_{n(k)}(r)\leq \limsup_{k\rightarrow\infty}1-F_{n(k)}(M_\epsilon)+F_{n(k)}(-M_\epsilon)\leq \epsilon
  $$
  So $\limsup_{x\rightarrow\infty} 1-F(x)+F(-x)\leq \epsilon$. Since $\epsilon$ is arbitrary, $F$ is a distribution function.

- If the sequence is not tight, we can pick $\epsilon>0$, $n(k)\uparrow\infty$, $1-F_{n(k)}(k)+F_{n(k)}(-k)\geq \epsilon$. Extract a subsequence $F_{n(k_j)}\to_v F$. Similar estimation shows that $1-F(+\infty)+F(-\infty)\geq \epsilon$. So $F$ is not the distribution function of a prob. measure.

**Theorem 3.2.14** If there is a $\varphi>0$ s.t. $\varphi(x)\to \infty$ as $|x|\rightarrow\infty$, and $C=\sup_n \int \varphi(x)dF_n(x)<\infty$, then $F_n$ is tight. 

_Remark_ This is often a useful sufficient condition.

<font color='red'>_proof of Theorem 3.2.14_</font> $C\geq (1-F_n(M)+F_n(-M))\inf_{|x|>M}\varphi(x)$.

Actually, weak convergence can be induced by metric, so we have

**Theorem 3.2.15** If each subsequence of $X_n$ has a further subsequence that converges to $X$ weakly then $X_n$ converges to $X$ weakly.

**Exercise 3.2.1** Give an example of r.v. $X_n$ with densities $f_n$ s.t. $X_n\to_d U(0,1)$ but $f_n$ doesn't converges to 1 for any $x\in[0,1]$.

<font color='red'>_proof of Exercise 3.2.1_</font> Actually this follows from a fact that $f_n\to f$ pointwise (or even uniform convergence) doesn't imply $f_n'\to f'$ pointwise. Consider 
$$
f_{n,k}(x)=\left\{\begin{aligned}&nx&x\in[k/n^2,(k+1)/n^2]\\&-(x-1/n)+1/n^2&x\in[(k+1)/n^2,(k+2)/n^2]\end{aligned}\right.
$$
Consider distribution functions $1_{(0,1)}+f_{2,0},1_{(0,1)}+f_{2,1},1_{(0,1)}+f_{2,2},,1_{(0,1)}+f_{3,0},...,1_{(0,1)}+f_{3,7},...$ Notice since $f_{n,k}\rightrightarrows 0$, and $f_{n,k}'\geq -1$, so these are well defined distributions, converging to $1_{(0,1)}$, and its derivative at any point oscillates to infinity.

**Exercise 3.2.2 Converge to maxima** Let $X_1,X_2,...$ i.i.d. $\sim F$, $M_n=\max_{m\leq n}X_m$ the maximal value. Then $P(M_n\leq x)=F(x)^n$.

(i) If $F(x)=1-x^{-\alpha},x\ge 1;0,\text{ otherwise}$, then $P(M_n/n^{1/\alpha}\leq y)\to\exp(-y^{-\alpha})$.

(ii) If $F(x)=1-|x|^\beta,-1\le x\le 0$, then for $y<0$, $P(n^{1/\beta}M_n\le y)\to\exp(-|y|^\beta)$.

(iii) If $F(x)=1-e^{-x},x\geq 0$, then for $y\in \mathbb R$, $P(M_n-\log n\leq y)\to\exp(-e^{-y})$. (Gumbel distribution).

**Exercise 3.2.4 Fatou's lemma** Let $g\ge 0$ be cts, then for $X_n\to_d X_\infty$ we have $\liminf_{n\rightarrow\infty} Eg(X_n)\ge Eg(X_\infty)$.

<font color='red'>_proof of Exercise 3.2.4_</font> Let $Y_n=_d X_n$ and $Y_n\to Y_\infty$ a.s., then
$$
\liminf_{n\rightarrow\infty} Eg(X_n)=\liminf_{n\rightarrow\infty}Eg(Y_n)\geq E\liminf_{n\rightarrow\infty} g(Y_n)=Eg(Y_\infty)
$$
**Exercise 3.2.5 Integration to limit** Suppose g,h are cts with $g(x)>0$, $|h|/g\to 0$ as $|x|\to\infty$. If $F_n\to_w F$ and $\int gdF_n\leq C<\infty$ for all n, then $\int hdF_n\to \int hdF$.

<font color='red'>_proof of Excerise 3.2.5_</font> 

First $\int gdF\leq C$, since $C\ge \int g\wedge M dF_n\to \int g\wedge MdF$, and push $M\to\infty$.

Next control $\int hdF_n$. $\forall\epsilon$, pick $R$ s.t. $|h|\le \epsilon g$ for all $|x|>R$, then 
$$
|\int hdF_n-\int hdF|\leq|\int_{(-R,R)} h(dF_n-dF)|+\int_{\mathbb R \backslash(-R,R)} \epsilon g(dF_n+dF)
$$
so its limit $\le 2C\epsilon$. Since $\epsilon$ is arbitrary, we've finished our proof.

**Exercise 3.2.6 The Levy Metric** on distribution: $\rho(F,G)=\inf\{\epsilon:F(x-\epsilon)-\epsilon\le G(x)\le F(x+\epsilon)+\epsilon\forall x \}$ defines a metric on the space of distributions and $\rho(F_n,F)\to 0$ iff $F_n\to_w F$.

**Exercise 3.2.7 The Ky Fan Metric** on r.v.s: $\alpha(X,Y)=\inf\{\epsilon>0: P(|X-Y|>\epsilon)\le \epsilon \}$ defines a metric and $\rho(F_X,F_Y)\le \alpha(X,Y)$. 

_Remark_ If $X_n\to_p X$, then $\alpha(X_n,X)\to 0$, $\rho(F_{X_n},F_X)\to 0$, i.e., convergence in prob. $\Rightarrow$ weak convergence. And there are obviously examples that $\rho(F_{X_n},F_X)\to 0$ but $\alpha(X,Y)\nrightarrow 0$, for example, $X_n\to_d X$ but they are independent.

**Exercise 3.2.8** Actually the metric we defined for convergence in prob, $\beta(X,Y)=E\frac{|X-Y|}{1+|X-Y|}$, are equivalent, since we have: $\alpha^2/(1+\alpha)\leq\beta\leq \alpha+(1-\alpha)\alpha(1+\alpha)$. So both of these metric could induce convergence in probability.

**Exercise 3.2.9** If $F_n\to_d F$ and $F$ is cts, then $\sup_x |F_n(x)-F(x)|\to 0$.

_Remark_ This indicates when $F$ is cts, weak convergence is actually uniform convergence.

<font color='red'>_proof of Exercise 3.2.9_</font> The result for this phenomenon is that distribution functions are monotonic.

$\forall \epsilon$, since $F$ is a distribution function, $\exists M$ s.t. $F(-M),1-F(M)<\epsilon$. On $[-M,M]$, $F$ is cts, so uniformly cts, pick $\delta$ s.t. $\forall x,y\in[-M,M],|x-y|<\delta,$ we have $|F(x)-F(y)|<\epsilon$. 

Fix points $-M=x_1<x_2<...<x_m=M$ s.t. $|x_{i+1}-x_i|<\delta$. Since $F_n\to_w F$, $\exists N$ s.t. $\forall n>N, 1\le i\le m$, $|F_n(x_i)-F(x_i)|<\epsilon$. So for any $x\in \mathbb R$, 

(i) If $x>M$, $|F(x)-F_n(x)|\leq |1-F(x)|+|1-F_n(x)|\leq \epsilon+2\epsilon=3\epsilon$.

(ii) If $x_i<x<x_{i+1}$, $|F(x)-F_n(x)|\leq |F(x)-F(x_i)|+|F(x_i)-F_n(x_i)|+|F_n(x_i)-F_n(x)|\leq 3\epsilon$.

(iii) If $x<-M$, $|F(x)-F_n(x)|<3\epsilon$ as in (i).

So $|F(x)-F_n(x)|<3\epsilon$ for all $n>N$. This indicates $F_n\rightrightarrows F$.

**Exercise 3.2.10** $F$ can be approximated by step functions, more precisely, there is a sequence of distributions of the form $\sum_{m=1}^n a_{n,m}1_{[x_{n,m},+\infty)}$ converges to $F$ weakly.

**Exercise 3.2.11** When $X_n$ take values on integers, $X_n\to_dX_\infty$ iff $P(X_n=m)\to P(X=m)$ for all $m\in \mathbb Z$.

**Exercise 3.2.12** If $X_n\to_p X$ then $X_n\to_d X$, but the inverse doesn't hold. This have been shown in **Exercise 3.2.8**. However, if $X_n\to_d c$ for some $c\in\mathbb R$, we have $X_n\to_p c$.

<font color='red'>_proof of Exercise 3.2.12_</font> 
$$
P(|X_n-c|<\epsilon)=P(c-\epsilon<X_n<c+\epsilon)\leq F_n(c+\epsilon)-F_n(c-\epsilon)\to F(c+\epsilon)-F(c-\epsilon)=1
$$
So $P(|X_n-c|\ge \epsilon)\to 0$.

**Exercise 3.2.13 Converging together lemma** If $X_n\to_d X$ and $Y_n\to_d c$ where $c\in\mathbb R$, we have $X_n+Y_n\to_d X+c$.

<font color='red'>_proof of Exercise 3.2.13_</font> 
$$
\begin{aligned}
P(X_n+Y_n\le t)&=P(|Y_n-c|<\delta,X_n+Y_n\le t)+P(|Y_n-c|\ge \delta, X_n+Y_n\le t)\le P(X_n\le t-c+\delta)+P(|Y_n-c|\ge \delta)
\\&\ge P(X_n\le t-c-\delta,|Y_n-c|<\delta)\ge P(X_n\le t-c-\delta)-P(|Y_n-c|>\delta)
\end{aligned}
$$
Since $Y_n\to_p c$, we can get
$$
\limsup_{n\rightarrow\infty} F_{X_n+Y_n}(t)-F_{X_n+c}(t+\delta)\le 0
\\\liminf_{n\rightarrow\infty} F_{X_n+Y_n}(t)-F_{X_n+c}(t-\delta)\ge 0
$$
Since $F_{X_n+c}\to_w F_{X+c}$ and $\delta$ is arbitrary, we can get $X_n+Y_n\to_d X+c$.

As a corollary, if $X_n\to_d X$ and $Z_n-X_n\to_d 0$, then $Z_n\to_d X$.

**Exercise 3.2.14** If $X_n\to_d X$ and $Y_n\ge 0$, $Y_n\to_d c$, where $c\in \mathbb R_+$, then $X_nY_n\to cX$.

<font color='red'>_proof of Exercise 3.2.14_</font> Similar procedure as **Exercise 3.2.13**.

_Remark_ These two results are called **Slutsky's theorem**. 

A more general form is: if $X_n\to_d X$ and $Y_n\to_d c$, then $(X_n,Y_n)\to_d (X,c)$. 

<font color='red'>_proof_</font> Let $f:\mathbb R^2\to\mathbb R$ be bounded cts function. It suffices to show $Ef(X_n,Y_n)\to Ef(X,c)$.

Write
$$
|Ef(X_n,Y_n)-Ef(X,c)|\le |Ef(X_n,Y_n)-Ef(X_n,c)|+|Ef(X_n,c)-Ef(X,c)|
$$
The second term goes to 0 since $f(\cdot,c)$ is a bounded cts function on $\mathbb R$.

For the first term, since $X_n\to_d X$, $(X_n)$ is tight. So $\forall\eta,\exists M>0,P(|X_n|>M)<\eta$ for all large $n$. Meanwhile, $\forall\delta>0,P(|Y_n-c|>\delta)\to 0$. Since $f$ is bounded, say $|f|\le B$.

On $[-M,M]\times[c-1,c+1]$, $f$ is uniformly cts, so for $\epsilon>0$, when n is large,
$$
|Ef(X_n,Y_n)-Ef(X_n,c)|\le \epsilon+2BP(|X_n|>M\text{ or }|Y_n-c|>1)\to \epsilon
$$
This implies convergence holds.

Use functions $f(x,y)=x+y, g(x,y)=xy$, we can directly get above two results.

_Remark_ If $X_n\to_d X$ and $Y_n\to Y$ a.s., we cannot get $X_n+Y_n\to_d X+Y$ in general. For example, let $Y_1=Y_n=Y_\infty\sim B(1,1/2)$ and $Y_i=X_i,Y_\infty=1-X_\infty$, then $X_n\to_d X_\infty$ and $Y_n\to Y_\infty$ a.s., but $X_i+Y_i\sim 2B(1,1/2)$, $X_\infty+Y_\infty=1$.

**Exercise 3.2.15** As an application, show that if $X_n=(X_n^1,...,X_n^n)$ is uniformly distributed over $\sqrt{n}\mathbb S$, then $X_1\to_d \mathcal N(0,1)$.

<font color='red'>_proof of Exercise 3.2.15_</font> Actually, let $Y_n\sim\mathcal N(0,1)$, then $(Y_i(n/\sum_{i=1}^{n}Y_i^2)^{1/2})_{i=1}^n$ is uniform on $\sqrt{n}\mathbb S$. Notice $\sum_{i=1}^{n}Y_i^2/n\to 1$ a.s., so by Slutsky theorem, $Y_1(n/\sum_{i=1}^{n}Y_i^2)^{1/2}\to_d \mathcal N(0,1)$.

### 3.3 Characteristic Functions

#### 3.3.1 Definition, inverse Formular

**Definition** If $X$ is a r.v., we define its **characteristic function (ch.f.)** by $\varphi(t)=Ee^{itX}=E\cos tX+iE\sin tX$.

**Theorem 3.3.1** All ch.f. have the following properties:

(i) $\varphi(0)=1$

(ii) $\varphi(-t)=\overline{\varphi(t)}$

(iii) $|\varphi(t)|=|Ee^{itX}|\le E|e^{itX}|=1$

(iv) $|\varphi(t+h)-\varphi(t)|\le E|e^{ihX}-1|$, so $\varphi(t)$ is uniformly cts on $\mathbb R$.

(v) $Ee^{it(aX+b)}=e^{itb}\varphi(at)$

**Theorem 3.2.2** If $X_1$ and $X_2$ are independent, having ch.f. $\varphi_1,\varphi_2$, then $X_1+X_2$ has ch.f. $\varphi_1\varphi_2$.

**Example 3.3.3 Coin flips** If $P(X=1)=P(X=-1)=1/2$ then $\varphi(t)=\cos t$.

**Example 3.3.4 Poisson distribution** If $X\sim Poisson(\lambda)$, then $\varphi(t)=\exp(\lambda(e^{it}-1))$.

**Example 3.3.5 Normal distribution** If $X\sim \mathcal N(0,1)$, then $\varphi(t)=\exp(-t^2/2)$. If $X\sim \mathcal N(0,1)$, then $\varphi(t)=\exp(i\mu t-\frac{1}{2}\sigma^2t^2)$.

**Example 3.3.6 Uniform distribution on $(a,b)$** $\varphi(t)=\frac{e^{itb}-e^{ita}}{it(b-a)}$. Especially, if $a+b=0$, $\varphi(t)=\sin tb/tb$.

**Example 3.3.7 Triangular distribution** If $X$ has density $1-|x|$, where $x\in(-1,1)$, then $\varphi(t)=2(1-\cos t)/t^2$. Actually, if $X$ and $Y$ are independent and uniform on $(-1/2,1/2)$, $X+Y$ has triangular distribution.

**Example 3.3.8 Exponential distribution** If $X\sim Exp(1)$, then $\varphi(t)=\frac{1}{1-it}$.

**Lemma 3.3.9** If $F_1,...,F_n$ have ch.f. $\varphi_1,...,\varphi_n$, and $\lambda_i\ge 0$ with $\lambda_1+...+\lambda_n=1$, then $\sum_{i=1}^{n} \lambda_i F_i$ has ch.f. $\sum_{i=1}^{n} \lambda_i\varphi_i$.

<font color='red'>_proof of Lemma 3.3.9_</font> Just use $\int fd(\mu+\nu)=\int fd\mu+\int fd\nu$.

**Example 3.3.10 Bilateral exponential** If $X$ has density $\frac{1}{2}e^{-|x|},x\in\mathbb R$, then $\varphi(t)=1/(1+t^2)$. This results from $F_X$ can be written as $1/2 F_Y+1/2 F_{-Y}$, $Y\sim Exp(1)$.

**Theorem 3.3.11 The inversion formular** Let $\varphi(t)=\int e^{itx}\mu(dx)$ where $\mu$ is a prob. measure. If $a<b$ then
$$
\lim_{T\to\infty}(2\pi)^{-1}\int_{-T}^T\frac{e^{-ita}-e^{-itb}}{it}\varphi(t)dt=\mu(a,b)+\frac{1}{2}\mu(\{a,b\})
$$
_Remark_ The existence of limit is part of the conclusion. If $\mu=\delta_0$ the point mass at $0$, $\varphi(t)\equiv 1$. In this case, if $a=-1$ and $b=1$, the integrand is $2\sin t/t$ which is not absolutely integrable, but the limit does exist, which is 1.

_Remark_ This theorem indicates that the ch.f. can determine the distribution uniquely.

<font color='red'>_proof of Theorem 3.3.11_</font> 

First, we can calculate
$$
\begin{aligned}
I_T&=\int_{-T}^T\frac{e^{-ita}-e^{-itb}}{it}\varphi(t)dt=\int_{-T}^T\int\frac{e^{-ita}-e^{-itb}}{it}e^{itx}\mu(dx)dt
\\&=_{(Fubini)}\int\int_{-T}^T \frac{e^{-ita}-e^{-itb}}{it}e^{itx}dt\mu(dx)
\\&=\int\bigg\{\int_{-T}^T \frac{\sin(t(x-a))}{t}dt-\int_{-T}^T \frac{\sin(t(x-b))}{t}dt\bigg\}d\mu(x)
\end{aligned}
$$
Since (i) $|{e^{-ita}-e^{-itb}}/{it}|=|\int_a^b e^{-ity}dy|\le b-a$ is bounded; (ii) $\cos t=\cos -t$, so its integration on $[-T,T]$ is $0$.

Now introduce $R(\theta,T)=\int_{-T}^T(\sin\theta t)/tdt$, we have
$$
R(\theta,T)=\int_{-T}^T\frac{\sin \theta t}{t}dt=2\text{sgn}(\theta)\int_0^{|\theta|T}\frac{\sin t}{t}dt\to\text{sgn}(\theta)\pi
$$
So the integrand inside bracket has limit 
$$
\left\{\begin{aligned}&2\pi&a<x<b\\&\pi&x=a,b\\&0&x<a,x>b\end{aligned} \right.
$$
Actually $|R(\theta,T)|\le 2\sup_x|\int_0^x \sin t/t dt|$, which is actually finite despite the integrand is not integrable.

So $\lim_{T \to \infty}(2\pi)^{-1}I_T=\mu(a,b)+1/2\mu(\{a\})+1/2\mu(\{b\})$.

By the inverse formular we have:

**Corollary 3.3.12** If $\varphi$ is real-valued then $X=_d -X$, since they have the same ch.f..

**Corollary 3.3.13** If $X_1\sim\mathcal N(0,\sigma_1^2),X_2\sim\mathcal N(0,\sigma_2^2)$ are independent then $X_1+X_2\sim\mathcal N(0,\sigma_1^2+\sigma_2^2)$, since they have the same ch.f..

When $\phi$ is integrable, the inversion formular can be simpler, but this only happens when the underlying measure is nice.

**Theorem 3.3.14** If $\varphi\in L^1$, then $\mu$ has bounded cts density $f(y)=(2\pi)^{-1}\int e^{ity}\varphi(t)dt$.

Since by above formular
$$
\mu(a,b)+\frac{1}{2}\mu(\{a,b\})=\frac{1}{2\pi}\int_\mathbb R \frac{e^{-ita}-e^{-itb}}{it}\varphi(t)dt\le \frac{(b-a)}{2\pi}\int_\mathbb R |\varphi(t)|dt
$$
Let $b\to a$, we can find $\mu$ doesn't have point masses. So we can calculate
$$
\begin{aligned}
\mu(x,x+h)&=\frac{1}{2\pi}\int\frac{e^{-itx}-e^{-it(x+h)}}{it}\varphi(t)dt
\\&=\frac{1}{2\pi}\int(\int_x^{x+h}e^{-ity}dy)\varphi(t)dt
\\&=\int_x^{x+h}\big(\frac{1}{2\pi}\int e^{-ity}\varphi(t)dt\big)dy
\end{aligned}
$$
So $\mu$ has density $f(y)=(2\pi)^{-1}\int e^{ity}\varphi(t)dt$. The continuity of $f$ is by DCT.

Apply the inverse formular to some of known ch.f. we can get new ch.f..

**Example 3.3.15 Polya's distribution** Recall if $X$ has density $(1-|x|)^+$, the ch.f. of $X$ is $\varphi(t)=2(1-\cos t)/t^2$. Apply inverse formular of density, we have 
$$
(1-|x|)^+=\frac{1}{2\pi}\int e^{itx} \frac{2(1-\cos t)}{t^2}dt=\int e^{itx}\frac{1-\cos t}{\pi t^2}dt
$$
This indicates that $(1-|x|)^+$ is ch.f. of the distribution whose density is $\frac{1-\cos t}{\pi t^2}$.

**Example 3.3.16 Cauchy distribution** Recall if $X$ has density $\frac{1}{2}e^{-|x|}$, its ch.f. is $\frac{1}{1+t^2}$. Apply inverse formular and we have 
$$
\frac{1}{2}e^{-|x|}=\frac{1}{2\pi} \int e^{itx}\frac{1}{1+t^2}dx
$$
So Cauchy distribution with density$\frac{1}{\pi(1+x^2)}$ has ch.f. $e^{-|x|}$.

_Remark_ From this we know if $X_1,X_2,...$ i.i.d. has Cauchy distribution, then $\frac{1}{n}(X_1+...+X_n)=_d X_1$.

**Exercise 3.3.2** (i) As in the proof of **Theorem 3.3.11**, we know 
$$
\mu(\{a\})=\lim_{T \to \infty}\frac{1}{2T}\int_{-T}^T e^{-ita}\varphi(t)dt
$$
(ii) If $P(X\in h\mathbb Z)=1$ for some $h>0$, we know its ch.f. satisfies $\varphi(t)=\varphi(t+2\pi/h)$,i.e., has period $2\pi/h$. Then by (i) we know 
$$
P(X=x)=\frac{h}{2\pi}\int_{-\pi/h}^{\pi/h}e^{-itx}\varphi(t)dt
$$
for $x\in h\mathbb Z$. (iii) This also holds under a transition by a constant.

**Exercise 3.3.3** Integrate $a$ in **Exercise 3.3.2** (i) w.r.t. $\mu$, we have 
$$
\lim_{T \to \infty} \frac{1}{2T}\int_{-T}^T |\varphi(t)|^2dt=\sum_x \mu(\{x\})^2
$$
If $X$ and $Y$ are independent and have the same law $\mu$, $RHS=P(X=Y)$.

_Remark_ This indicates if $|\varphi|\to 0$ as $t\to\infty$, $RHS=0$, i.e., $\mu$ doesn't have point masses. Actually the converse is false.

As a usage of inverse formular,

**Exercise 3.3.5** If $X_1,X_2,...$ i.i.d.$\sim U(-1,1)$, then for $n\ge 2$, $S_n$ has density $f(x)=\frac{1}{\pi}\int_0^\infty (\sin t/t)^n\cos tx dx$. 

<font color='red'>_proof of Exercise 3.3.5_</font> $S_n$ has ch.f. $(\sin t/t)^n$. By inverse formular, the density is given by
$$
f(x)=\frac{1}{2\pi}\int e^{-itx}\varphi(t)dt=\frac{1}{2\pi}\int e^{-itx}\big(\frac{\sin t}{t}\big)^ndy=\int\frac{1}{2\pi}(\sin t/t)^n\cos tx dt
$$
And by symmetry we can reach the conclusion.

#### 3.3.2 Weak Convergence

Now let's relate the convergence of ch.f. to weak convergence.

**Theorem 3.3.17 Continuity theorem** Let $\mu_n,1\le n\le\infty$ be prob. measures with ch.f. $\varphi_n$. 

(i) If $\mu_n\to_d \mu_\infty$ then $\varphi_n(t)\to \varphi_\infty(t)\forall t$ 

(ii) If $\varphi_n(t)\to \varphi(t)$ pointwise, with $\varphi$ is cts at 0, then $\mu_n$ is tight and converges weakly to the measure $\mu$ with ch.f. $\varphi$.

_Remark_ Continuity of the limit at $0$ is needed in (ii). Consider this example: Let $\mu_n\sim\mathcal N(0,n)$, then $\varphi_n(t)=\exp(-nt^2/2)\to 0$ for all $t\ne 0$, and $\varphi_n(0)=1$ for all $n$. Notice in this case the measure doesn't converge weakly since $\mu_n((-\infty,x])\to 1/2$ for all $x$.

<font color='red'>_proof of Theorem 3.3.17_</font> 

(i) If $\mu_n\to_d\mu_\infty$, since $e^{itx}$ is bounded cts function, we have $Ee^{itX_n}\to Ee^{itX}$ for all $t$.

(ii) 

- First we prove tightness. Do some calculations,
  $$
  \int_{-u}^u1-e^{itx}dt=2u-\int_{-u}^u(\cos tx+i\sin tx)dt=2u-\frac{2\sin ux}{x}
  $$
  Divide by $u$ and integrate $x$ w.r.t. $\mu_n$,
  $$
  u^{-1}\int_{-u}^u1-\varphi_n(t)dt=2\int (1-\frac{\sin ux}{ux})\mu_n(dx)
  $$
  Actually from $RHS$ we can get the tail prob.: 
  $$
  2\int(1-\frac{\sin ux}{ux})\mu_n(dx)\ge 2\int_{|x|\ge 2/u}1-1/|ux|\mu_n(dx)\ge \mu_n((-\infty,2/u)\cup(2/u,+\infty))
  $$
  Since $\varphi(t)\to 1$ as $t\to 0$, (here we use the continuity) we have $u^{-1}\int_{-u}^u(1-\varphi(t))dt\to 0$ as $u\to 0$. And $\varphi_n(t)\to \varphi(t)$, By BCT for any $\epsilon$ when $n$ is large and $u$ is small,
  $$
  2\epsilon\ge u^{-1}\int_{-u}^u(1-\varphi_n(t))dt\ge \mu_n((-\infty,-2/u)\cup(2/u,\infty))
  $$
  So $\mu_n$ is tight.

- By tightness and Helly's selection theorem, there is a subsequence of $\mu_n$, say $\mu_{n(k)}$, converging to $\mu$. This $\mu$ is actually the limit of the whole sequence. By (i), we know $\varphi_{n(k)}\to \varphi_\mu$, and $\varphi_n$ is pointwise convergent to $\varphi$, so $\varphi_n\to \varphi=\varphi_\mu$. By the inverse formular, we know this indicates $\mu_n\to_d\mu$, and $\varphi_\mu=\varphi$.