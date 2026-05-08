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

As applications, 

**Exercise 3.3.7** Suppose $X_n\sim\mathcal N(0,\sigma_n^2)\to_d X$, then $\sigma_n^2\to \sigma^2\in[0,+\infty)$.

<font color='red'>_proof of Exercise 3.3.7_</font> $\varphi_n(t)=\exp(-1/2\ \sigma_n^2t^2)$. If $X_n\to_d X$, $\varphi_n(1)$ must converge, so $\sigma_n^2$ converges, say the limit $\sigma^2$. It must be nonnegative.

It's easy to verify $\varphi_n(t)\to\exp(-1/2 \sigma^2t^2)$ pointwise, and since the limit is cts at 0, we know $X$ has ch.f. $\exp(-1/2\sigma^2t^2)$, so $X\sim\mathcal N(0,\sigma^2)$.

Moreover, if $X_n\sim\mathcal N(\mu_n,\sigma_n^2)\to_d X$, we can prove similarly $\mu_n\to\mu$ and $\sigma_n^2\to\sigma^2$, and $X\sim\mathcal N(\mu,\sigma^2)$.

**Exercise 3.3.8** If $X_n$ and $Y_n$ are independent, $X_n\to_d X$ and $Y_n\to_d Y$, then $X_n+Y_n\to_d X+Y$.

<font color='red'>_proof of Exercise 3.3.8_</font> Then $\varphi_{X_n}\to \varphi_X$ and $\varphi_{Y_n}\to\varphi_Y$. Since $\varphi$ is bounded, $\varphi_{X_n+Y_n}=\varphi_{X_n}\varphi_{Y_n}\to\varphi_{X}\varphi_{Y}=\varphi_{X+Y}$.

**Exercise 3.3.9** Let $X_1,X_2,...$ be independent and let $S_n=X_1+...+X_n$. If $S_n\to_d S$, then $\varphi_S=\prod \varphi_n$.

**Exercise 3.3.10** Euler's formular says $(\sin t)/t=\prod_{m=1}^\infty \cos(t/2^m)$. Actually this have a probabilistic interpretation. Let $X_n$ be independent with law $P(X_n=1/2^n)=P(X_n=-1/2^n)=1/2$. Then $\sum_{n=1}^\infty X_n=_d U(-1,1)$. Use **Exercise 3.3.9**, since $\varphi_{U(-1,1)}=\sin t/t$ and $\varphi_{X_n}=\cos(t/2^m)$, we can get this result.

#### 3.3.3 Moments and Derivatives

We have shown 
$$
\mu\{x:|x|>2/u\}\le u^{-1} \int_{-u}^u(1-\varphi(t))dt
$$
which indicates the smoothness of ch.f. at 0 is related to the decay of measure at $\infty$.

**Theorem 3.3.18** If $\int |x|^n \mu(dx)<\infty$ then $\varphi\in C^n$ with $\varphi^{(k)}=\int (ix)^k e^{itx}\mu(dx)$.

<font color='red'>_proof of Theorem 3.3.18_</font> Notice $|e^{itx}|\le 1$. Differentiate inside integral signal for $n$ times.

In this case, its Maclaurin expansion is $\varphi(t)=\sum_{m=0}^n \frac{E(itX)^m}{m!}+o(t^n)$. A more precise estimation for the error term is

**Lemma 3.3.19** 
$$
\bigg |e^{ix}-\sum_{m=1}^n \frac{(ix)^m}{m!}\bigg |\le \min\bigg (\frac{|x|^{n+1}}{(n+1)!},\frac{2|x|^n}{n!} \bigg )
$$
<font color='red'>_proof of Lemma 3.3.19_</font> By Taylor expansion with integral error term, 
$$
e^{ix}-\sum_{m=1}^{n}\frac{(ix)^m}{m!}=\frac{1}{n!}\int_0^x i^{n+1}e^{it}(x-t)^n dt
$$
when $x$ is small, we can estimate $|RHS|\le \frac{1}{n!}\frac{|x|^{n+1}}{n+1}$

when $x$ is large, a better estimate can be obtained by 
$$
\frac{i}{n}\int_0^x (x-s)^n e^{is}ds=-\frac{x^n}{n}+\int_0^x (x-s)^{n-1}e^{is}ds=\int_0^x(x-s)^{n-1}(e^{is}-1)ds
$$
And 
$$
\int_0^x |(x-s)^{n-1}(e^{is}-1)|ds\le 2\int_0^x|(x-s)|^{n-1}ds\le \frac{2}{n}|x|^n
$$
So $|RHS|\le \frac{1}{(n-1)!}\frac{2}{n} |x|^n$. Combine these we can reach the conclusion.

By this we have 
$$
\bigg |Ee^{itX}-\sum_{m=1}^{n}E\frac{(itX)^m}{m!}\bigg|\le E\bigg |e^{itX}-\sum_{m=1}^{n}\frac{(itX)^m}{m!}\bigg|\le E\min(|tX|^{n+1},2|tX|^n)
$$
A useful trivial corollary is 

**Theorem 3.3.20** If $E|X|^2<\infty$ then $\varphi(t)=1+itEX-t^2/2\ EX^2+o(t^2)$.

The converse case also holds, i.e., if $\varphi''$ exists, then $EX^2<\infty$.

**Theorem 3.3.21** If $\limsup_{h\downarrow 0}(\varphi(h)+\varphi(-h)-2\varphi(0))/h^2>-\infty$, then $EX^2<\infty$,

<font color='red'>_proof of Theorem 3.3.21_</font> 
$$
\int x^2dF(x)\le 2\liminf_{h\to 0}\int \frac{1-\cos hx}{h^2}dF(x)=\liminf_{h\to 0}-\int\frac{e^{ihx}+e^{-ihx}-2}{h^2}dF(x)=-\limsup_{h\to 0}\frac{\varphi(h)+\varphi(-h)-2\varphi(0)}{h^2}<\infty
$$
gives the desired result. Actually, if $\varphi''$ exists then the limit term is $\varphi''(0)$ by Taylor expansion. However that limit exists cannot assure the second derivative exists, i.e., consider $f$ odd on $\mathbb R$ with $f(x)=\sqrt{x}$ on $R_{\ge 0}$.

**Exercise 3.3.12** Consider $X\sim\mathcal N(0,1)$, with $\varphi(t)=\exp(-t^2/2)=\sum_{m=0}^\infty\frac{1}{m!}(-1)^m\frac{t^{2m}}{2^{m}}$, we can derive $EX^{2n}=(2n-1)!!$.

**Exercise 3.3.13** (i) If $\mu_i$ is tight, then their ch.f.'s are equicontinuous.

<font color='red'>_proof_</font> For all $\epsilon$, since $\mu_i$ is tight, pick $M$ s.t. $\sup_i \mu_i([-M,M]^c)<\epsilon$, then for $|h|M<\epsilon$, 
$$
|Ee^{i(t+h)X_n}-Ee^{itX_n}|\le E|e^{ihX_n}-1|\le 2P(|X_n|>M)+hM\le 3\epsilon
$$
which indicates equicontinuity.

(ii) If $\mu_n\to_d\mu_\infty$, then $\varphi_n\to\varphi_\infty$ on compact sets.

<font color='red'>_proof_</font> Since $\mu_n\to_d\mu_\infty$, $\mu_n$ is tight. So their ch.f. are equicontinuous. Then pick finite points that are dense enough, and pass the convergence on points to all compact set. Or Arzela-Ascoli theorem.

_Remark_ The uniform convergence can only occur on compact sets. For example, consider $\mathcal N(0,1-1/n)\to_d\mathcal N(0,1)$.

**Exercise 3.3.14** Let$X_1,X_2,...$ be i.i.d. with ch.f.$\varphi$, then $S_n/n$ converges to some constant in prob. iff $\varphi'(0)$ exists.

<font color='red'>_proof of Exercise 3.3.14_</font>

$\Leftarrow$ If $\varphi(0)=ia$, then (take $\log$ on the main component)
$$
\varphi_{S_n/n}=\varphi^n(t/n)=\exp(n\log \varphi(t/n))=\exp(iat+o(1/n))\to\exp(iat)
$$
and the limit is cts at 0. This indicates $S_n/n\to_d a$, so $S_n/n\to_p a$.

$\Rightarrow$ Inversely if $S_n\to_p a$ then $\varphi(t/n)^n\to e^{iat}$. To simplify this we assume $a=0$.

By **Exercise 3.3.13**, for any fixed $T>0$ we have $\varphi(t/n)^n\rightrightarrows 1$ on $[0,T]$.

Now we suppose for contradiction $\frac{\varphi(h)-1}{h}\nrightarrow 0$, i.e., $\exists\ h_k\downarrow 0,\epsilon>0$, $|\varphi(h_k)-1|\ge \epsilon h_k$.

Since we have $|1-\varphi(h_k)^m|=|1-\varphi(h_k)||1+\varphi(h_k)+...+\varphi(h_k)^{m-1}|$,and 
$$
|1+\varphi(h_k)+...+\varphi(h_k)^{m-1}|\ge m-\sum |1-\varphi(h_k)^i|\ge m-\sum i|1-\varphi(h_k)|\ge m(1-m\epsilon h_k/2)
$$
so $|1-\varphi(h_k)^m|\ge (m\epsilon h_k)(1-1/2\ m\epsilon h_k)$.

Notice $\varphi(h_k)^m=\varphi(mh_k/m)^m$, so if we pick suitable $m_k$ s.t. $m_kh_k\to \eta<1$, then $m_kh_k$ is bounded, and we have $|1-\varphi(h_k)^{m_k}|\to 0$, but $RHS\to \eta(1-\eta/2)>0$.

So $\varphi'(0)=0$.

(The next two sections are left for later completion)

### 3.4 Central Limit Theorems

#### 3.4.1 i.i.d. Sequences

**Theorem 3.4.1** Let $X_1,X_2,...$ be i.i.d. with $EX_i=\mu,var(X_i)=\sigma^2\in \mathbb R^+$, then $(S_n-n\mu)/\sigma n^{1/2}\to \mathcal N(0,1)$.

<font color='red'>_proof of Theorem 3.4.1_</font> WLOG $\mu=0$, then by **Theorem 3.3.20**, $\varphi(t)=E\exp(itX_1)=1-\frac{\sigma^2 t^2}{2}+o(t^2)$, so we expect $E\exp(itS_n/\sigma n^{1/2})=(1-t^2/2n+o(n^{-1}))^n\to\exp(-t^2/2)$. To make this true for complex numbers, we need to show

**Theorem 3.4.2** if $c_n\to c\in\mathbb C$, then $(1+c_n/n)^n\to c$.

**Lemma 3.4.3** Let $z_1,...,z_n$ and $w_1,...,w_n$ be complex numbers of modulus less than $\theta$, then
$$
\left| \prod_{m=1}^{n} z_m - \prod_{m=1}^{n} w_m \right| \leq \theta^{n-1} \sum_{m=1}^{n} |z_m - w_m|
$$
<font color='red'>_proof of Lemma 3.4.3_</font> Use induction. This is true for $n=1$, and for $n>1$, we have
$$
\left| \prod_{m=1}^{n} z_m - \prod_{m=1}^{n} w_m \right|
\leq \left| z_1 \prod_{m=2}^{n} z_m - z_1 \prod_{m=2}^{n} w_m \right| + \left| z_1 \prod_{m=2}^{n} w_m - w_1 \prod_{m=2}^{n} w_m \right|\leq \theta \left| \prod_{m=2}^{n} z_m - \prod_{m=2}^{n} w_m \right| + \theta^{n-1} |z_1 - w_1|
$$
**Lemma 3.4.4** If $b\in\mathbb C$, $|b|<1$, then $e^b-(1+b)|\le |b|^2$.

<font color='red'>_proof of Lemma 3.4.4_</font> By definition
$$
|e^b-(1+b)|=|b^2/2!+b^3/3!+...|\le|b|^2/2(1+1/2+1/2^2+...)=|b|^2
$$
<font color='red'>_proof of Theorem 3.4.2_</font> Let $z_m=(1+c_m/m)$, $w_n=\exp(c_n/n)$, $\gamma>|c|$. Then when $n$ is large $|c_n|\le\gamma$. So $|z_m|,|w_m|\le e^{\gamma/n}$ Then we have
$$
|(1+c_n/n)^n-e^{c_n}|\le_{3.4.3}(e^{\gamma/n})^{n-1}n|c_n/n|^2\le e^{\gamma}(\gamma^2/n)\to 0
$$
Now let's look at some examples of CLT.

**Example 3.4.6 Coin flips** Let $X_1,X_2,...$ be i.i.d.$\sim B(1,1/2)$. Since $EX_i=1/2$ and $var X_i=1/4$, CLT shows $(S_n-n/2)/\sqrt{n/4}\to_d \mathcal N(0,1)$.

**Example 3.4.7 Normal approximation to the binomial** This is to say if you want to approximate on an integer $n$ using normal distribution you has better estimate on $[n-1/2,n+1/2]$. This is called **histogram correction**.

**Example 3.4.8 Normal approximation to the Poisson** To estimate the limit distribution $P(\lambda)$, we start from integers. Let $X_1,X_2,...$ i.i.d. $\sim P(1)$, we have $S_n\sim P(n)$, and by CLT we have $(S_n-n)/n^{1/2}\to_d\mathcal N(0,1)$. For $\lambda\to\infty$ on real line, let $N_1,N_2,N_3$ be independent Poisson with means $[\lambda],\lambda-[\lambda],[\lambda]+1-\lambda$. If we let $S_{[\lambda]}=N_1$, $Z_\lambda=N_1+N_2$, and $S_{[\lambda]+1}=N_1+N_2+N_3$, then $S_[\lambda]\le Z_\lambda\le S_{[\lambda]+1}$. Use CLT, it follows that $(Z_\lambda-\lambda)/\lambda^{1/2}\to\mathcal N(0,1)$.

**Example 3.4.9 Pairwise independence** For SLLN, pairwise independence is enough, but not for CLT. Let $\xi_1,\xi_2,...$ be i.i.d. with $P(\xi_i=1)=P(\xi_i=-1)=1/2$.

First we notice if $S,T\subset Z_+$ are finite and not identical, we have $\prod_{i\in S}\xi_i$ and $\prod_{j\in T}\xi_j$ have the same law but are independent. 

For $n\in Z_+$, suppose the binary form of $n-1$ has digit $1$ on the set $K_n\subset Z_+$. Then let $X_n=\xi_1\prod_{j\in K_n}\xi_{j+1}$. Now $X_n$ are pairwise independent, and the sum is constructed so that $S_{2^n}=\xi_1(1+\xi_2)...(1+\xi_{n+1})$. If CLT hold, we should have $S_n/{\sqrt{n}}\to_d\mathcal N(0,1)$. But $S_{2^n}$ has law $P(S_{2^n}=\pm 2^n)=2^{-n-1}$, $P(S_{2^n}=0)=1-2^{-n}$.  So CLT doesn't hold.

**Exercise 3.4.2** 

(i) $S_n/\sqrt{n}$ doesn't converge a.s.: Let $X_1,X_2,...$ be i.i.d. with $EX_i=0,EX_i^2<\infty$, then by CLT we know $S_n/\sqrt{n}\to_d\mathcal N(0,1)$, So $P(S_n/\sqrt{n}>x)$ have a positive limit. By Kolmogorov's 0-1 law, $S_n/\sqrt{n}>0$ i.o.. Since $x$ is arbitrary, $\limsup_{n\rightarrow\infty} S_n/\sqrt{n}=\infty$ a.s.. 

(ii) $S_n/\sqrt{n}$ doesn't converge in prob.: Suppose otherwise it converges in prob., then extract a subseries $n(m)=m!$. Since it's induced by topology, the series is Cauchy. However
$$
\frac{S_{(m+1)!}}{\sqrt{(m+1)!}}-\frac{S_{m!}}{\sqrt{m!}}=\frac{S_{(m+1)!}-S_{m!}}{\sqrt{(m+1)!}}-(1-\frac{1}{\sqrt{m+1}})\frac{S_{m!}}{\sqrt{m!}}
$$
By CLT both term converge to $\mathcal N(0,\sigma^2)$ ,so it has distribution $\mathcal N(0,2\sigma^2)$ by independence. This indicates this sequence cannot converge in probability. 

_Remark_ we don't know what the limit will be, so we can only deal with the Cauchy sequence.

**Exercise 3.4.5 Self-normalized sums** Let $X_1,X_2,...$ be i.i.d. with $EX_i=0$ and $EX_i^2=\sigma^2$, then
$$
\sum_{i=1}^{n}X_i\bigg/\bigg(\sum_{i=1}^{n}X_i^2\bigg)^{1/2}=\frac{\sum_{i=1}^{n}X_i}{\sqrt{n}}\bigg/\bigg(\frac{\sum_{i=1}^{n}X_i^2}{n}\bigg)^{1/2}\to_d\mathcal N(0,1)
$$
By Slutsky's theorem.

**Exercise 3.4.6 Random index CLT** Let $X_1,X_2,...$ be i.i.d. with $EX_i=0$ and $EX_i^2=\sigma^2$. If $N_n$ is an integer-valued positive r.v. , $a_n$ is a sequence of integers with $a_n\to\infty$ and $N_n/a_n\to 1$ in prob.. Then $S_{N_n}/\sigma\sqrt{a_n}\to \mathcal N(0,1)$.

<font color='red'>_proof of Exercise 3.4.6_</font> Since we have $S_{a_n}/\sigma\sqrt{a_n}\to_d\mathcal N(0,1)$, we need only to estimate the difference $(S_{N_n}-S_{a_n})/\sigma\sqrt{a_n}$. We have 
$$
P((S_{N_n}-S_{a_n})/\sigma\sqrt{a_n}>\epsilon)\le P(|N_n/a_n-1|\ge \epsilon')+P(\max_{1\le k\le [\epsilon' a_n]}|S_k|>\epsilon\sigma\sqrt{a_n})
$$
The first term goes to 0 and the second term can be bounded by Kolmogorov's maximal inequality:
$$
P(\max_{1\le k\le [\epsilon' a_n]}|S_k|>\epsilon\sigma\sqrt{a_n})\le (\epsilon\sigma\sqrt{a_n})^{-2}P(S_{[\epsilon' a_n]}>\epsilon\sigma\sqrt{a_n})
$$
Take $\epsilon=\epsilon'$, notice $RHS\to 0$ since $a_n\to\infty$ and the prob. is convergent by CLT.

**Exercise 3.4.7 CLT in renewal theory** Let$Y_1,Y_2,...$ be i.i.d. positive r.v. with $EY_i=\mu$ and $var(Y_i)=\sigma^2$. Then we have $(\mu N_t-t)/(\sigma^2t/\mu)^{1/2}\to_d\mathcal N(0,1)$.

<font color='red'>_proof of Exercise 3.4.7_</font> By definition we have $S_{N_t-1}\le t\le S_{N_t}$. Since $N_t/t\to1/\mu$ a.s., we have $(S_{N_t}-\mu N_t)/(\sigma^2 t/\mu)^{1/2}\to_d\mathcal N(0,1)$ as $t\to\infty$.

#### 3.4.2 Triangular Arrays

**Theorem 3.4.10 The Lindeberg-Feller theorem** For each $n$, let $X_{n,m},1\le m\le n$ be independent r.v.'s with mean 0. Suppose

(i)$\sum_{m=1}^{n} EX_{n,m}^2\to\sigma^2>0$

(ii) For all $\epsilon>0$, $\lim_{n \to \infty}\sum_{m=1}^{n} E(|X_{n,m}|^21_{|X_{n,m}|>\epsilon})=0$.

Then $S_n\to_d\mathcal N(0,\sigma^2)$.

_Remark_ This contains case for i.i.d. r.v.'s: suppose $X_1,X_2,...$ are i.i.d. with mean 0 and variance $\sigma^2$,then $E(X_1/n^{1/2})^2+...+(X_n/n^{1/2})=\sigma^2$ and $\sum_{i=1}^{n} E(X_n^2/n\ 1_{|X_n/\sqrt{n}|>\epsilon})=EX_1^21_{|X_1|>\epsilon\sqrt{n}}\to 0$ by DCT.

<font color='red'>_proof of Theorem 3.4.10_</font> Let $\varphi_{n,m}(t)=E\exp(itX_{n,m})$, $\sigma_{n,m}^2=EX_{n,m}^2$, by **Theorem 3.3.17** it suffices wo show that $\prod_{m=1}^n \varphi_{n,m}(t)\to\exp(-t^2\sigma^2/2)$.

Let $z_{m,n}=\varphi_{m,n}(t)$ and $w_{m,n}=(1-t^2\sigma_{n,m}^2/2)$. By above estimation, we have
$$
\begin{aligned}
|z_{n,m}-w_{n,m}|&\le E(|tX_{n,m}|^3\wedge 2|tX_{n,m}|^2)
\\&\le E(|tX_{n,m}|^31_{|X_{n,m}|\le\epsilon})+E(2|tX_{n,m}|^21_{|X_{n,m}}|>\epsilon)
\\&\le \epsilon t^3E(|X_{n,m}|^21_{|X_{n,m}|<\epsilon})+2t^2E(|X_{n,m}|^21_{|X_{n,m}|>\epsilon})
\end{aligned}
$$
So 
$$
\limsup_{n\rightarrow\infty}\sum_{m=1}^{n}|z_{n,m}-w_{n,m}|\le \epsilon t^3\sigma^3
$$
Since $\epsilon$ is arbitrary, it follows that the sequence converges to 0. 

Since we have this, we want to use **Lemma 3.4.3** to show 
$$
\bigg|\prod_{m=1}^n \varphi_{n,m}(t)-\prod_{m=1}^n(1-t^2\sigma_{n,m}^2/2)\bigg|\to 0
$$
verify the necessary condition. $|\varphi_{n,m}|\le 1$, and $\sigma_{n,m}^2\le\epsilon^2+E(|X_{n,m}|^21_{|X_{n,m}|>\epsilon})$. So when $n$ is large enough, since $\epsilon$ is arbitrary, $\sup_m\sigma_{n,m}^2\to 0$. So $|1-t^2\sigma_{n,m}^2/2|<1$. So let $\theta=1$ there, we can know the limit holds.

Let $c_{m,n}=-t^2\sigma_{n,m}^2/2$. By (i), $\sum_{m=1}^{n} c_{m,n}\to -\sigma^2t^2/2$. since $\sup_m\sigma_{n,m}^2\to 0$, we have $\prod_{m=1}^n (1+c_{m,n})\to\exp(-\sigma^2t^2/2)$. The proof is complete. 

**Example 3.4.11 Cycles in a random permutation and record values** Let $Y_1,Y_2,...$ be independent with $P(Y_m=1)=1/m$ and $P(Y_m=0)=1-1/m$. So$EY_m=1/m$ and $var(Y_m)=1/m-1/m^2$. So $ES_n\sim\log n$ and $var (S_n)\sim\log n$. Let $X_{n,m}=(Y_m-1/m)/(\log n)^{1/2}$, then $EX_{n,m}=0$ and $\sum_{m=1}^{n} var X_{n,m}\to 1$. Moreover, $\sum_{m=1}^n E(|X_{n,m}|^21_{|X_{n,m}|>\epsilon})\to 0$, actually it equals to 0 when $\epsilon\sqrt{\log n}>1$.

This indicates $(\log n)^{-1/2}(S_n-\sum_{m=1}^{n} 1/m)\to\mathcal N(0,1)$. Since $|\log n-\sum_{m=1}^n 1/m|\le 1$, we can know $(S_n-\log n)/(\log n)^{1/2}\to \mathcal N(0,1)$.

**Example 3.4.12 The converse of three series theorem** Recall **Theorem 2.5.8**

> [!NOTE]
>
> **Theorem 2.5.8 Kolmogorov's three-series theorem** Let $X_1,X_2,...$ be independent, and let $A>0$, $Y_i=X_i1_{|X_i|\leq A}$. $\sum_{n=1}^\infty X_n$ converges a.s. iff
>
> (i) $\sum_{n=1}^\infty P(|X_n|>A)<\infty$ (ii) $EY_n$ converges (iii)$\sum_{n=1}^\infty var(Y_n)<\infty$

We have proven $\Leftarrow$, now we prove $\Rightarrow$.

<font color='red'>_proof_</font> (i) otherwise since $X_n$ are independent, $|X_n|>A$ i.o., so it cannot converge.

(iii) Suppose otherwise it's infinite. Let $c_n=\sum_{m=1}^{n} var(Y_m)$ and $X_{n,m}=(Y_m-EY_m)/c_n^{1/2}$. We can verify $EX_{m,n}=0$, $\sum_{m=1}^{n} var(X_{m,n})=1$, and $\sum_{m=1}^{n} E(|X_{m,n}|^21_{|X_{m,n}>\epsilon|})\to 0$, since actually when $2A/c_n^{1/2}<\epsilon$ the sum is 0. (So $c_n\to\infty$ is necessary for this). So $S_n\to_d \mathcal N(0,1)$.

Now by (i), we know if $\lim_{n \to \infty}\sum_{m=1}^{n} X_m$ exists then $\lim_{n \to \infty}\sum_{m=1}^{n} Y_m$ exists. Since $c_n\to\infty$, $T_n=(\sum_{m=1}^{n} Y_m)/c_n^{1/2}\to 0$ a.s.. So $S_n-T_n\to_d \mathcal N(0,1)$.But $S_n-T_n$ isn't random.

(ii) If (i) and (iii) hold, then $\lim_{n \to \infty}\sum_{m=1}^{n} Y_m-EY_m$ exists. Since $\sum_{m=1}^{\infty} Y_m$ exists, so does $\lim_{n \to \infty} \sum_{m=1}^{n} EY_m$.

_Remark_ So when the sum of variance is infinite, it's very likely to follow CLT.

**Example 3.4.13 Infinite variance** Suppose $X_1,X_2,...$ are i.i.d. and for $x\ge 1$, $P(X_1>x)=P(X_1<-x)$ and $P(|X_1|>x)=x^{-2}$. This has infinite variance
$$
E|X_1|^2=\int_0^\infty 2xP(|X_1|>x)dx=\infty
$$
but it turns out that when $S_n$ is suitably normalized it converges to a normal distribution. Let $Y_{n,m}=X_m1_{|X_m|\le c_n}$, where $c_n=n^{1/2}\log\log n$. This is chosen large enough so that $\sum_{m=1}^{n} P(Y_{n,m}\ne X_m)\le nP(|X_1|>c_n)\to 0$, and small enough such that the variance is small. Indeed, $EY_{n,m}^2\sim\log n$:

- upper bound:
  $$
  EY_{n,m}^2\le\int_0^{c_n}2yP(|X_1|>y)dy=c+\int_1^{c_n} 2/y dy=c+\log n+2\log\log\log n\sim\log n
  $$

- lower bound:

  Notice $P(|Y_{m,n}|>x)=P(|X_1|>x)-P(|X_1|>c_n)$. When $x\le\sqrt{n}$, $RHS\ge(1-(\log\log n)^{-2})P(|X_1|>x)$. So
  $$
  EY_{n,m}^2\ge (1-(\log\log n)^{-2})\int_1^{\sqrt{n}}2/y dy\sim\log n
  $$

So if we let $S_n'=Y_{n,1}+...+Y_{n,n}$, then $var(S_n')\sim n\log n$. So we apply the Lindeberg-Feller CLT to $X_{m,n}=Y_{m,n}/(n\log n)^{1/2}$. The conditions all hold, so $S_n'/(n\log n)^{1/2}\to_d \mathcal N(0,1)$. So $S_n/(n\log n)^{1/2}\to_d \mathcal N(0,1)$.

**Theorem 3.4.14** Let $X_1,X_2,...$ be i.i.d. and $S_n=X_1+...+X_n$. In order that there exists constants $a_n$ and $b_n>0$ so that $(S_n-a_n)/b_n\to \mathcal N(0,1)$, it's necessary and sufficient that $y^2P(|X_1|>y)/E(|X_1|^21_{|X_1|<y})\to 0$.

In below exercises $X_i$ are independent.

**Exercise 3.4.9** Condition in **Theorem 3.4.10** is not necessary. Consider this example: Suppose $X_m$ are independent with distribution $P(X_m=\pm m)=1/2m^2$ and $P(X_m=\pm 1)=(1-m^{-2})/2$ when $m>1$. 

- $EX_m=0$ and $var(X_m)=2-m^{-2}$. So $var(S_n)/n\to 2$.
- $S_n/\sqrt{n}\to_d\mathcal N(0,1)$. Using ch.f. can be much complicated. So we argue in a more indirect way. Let $Y_m=X_m\wedge 1$, $S_m'=\sum_{m=1}^{n} Y_m$. Then by De Moivre Laplace theorem $S_m'/\sqrt{m}\to_d \mathcal N(0,1)$. And $P(Y_m-X_m\ne 0)=m^{-2}$ is summable. By Borel-Cantelli lemma, $Y_m\ne X_m$ only occurs for finite times. In this case,$(S_m'-S_m)/\sqrt{m}\to 0$ a.s. since $\sqrt{n}\uparrow\infty$. So finally $S_n/\sqrt{n}\to_d \mathcal N(0,1)$ by Slutsky's theorem.
- The problem is, $\sum_{m=1}^{n} E(X_m/\sqrt{n})^21_{|X_{m}/\sqrt{n}|\ge1}\approx \sum_{m=[\sqrt{n}]}^{n}\frac{1}{\sqrt{n}}\approx\sqrt{n}\to\infty$.

**Exercise 3.4.10** If $|X_i|\le M$ and $\sum_{n=1}^{\infty}var(X_n)=\infty$, then $(S_n-ES_n)/\sqrt{var(S_n)}\to_d\mathcal N(0,1)$.

<font color='red'>_proof of Exercise 3.4.10_</font> Since $X_i$ are bounded, the mean is finite, so WLOG assume $EX_i=0$. Consider triangular series $X_{n,m}=X_m/\sqrt{var(S_n)}$. Notice $\sum_{m=1}^{n}EX_{n,m}^2=1$, and for all $\epsilon$, when $\epsilon\sqrt{var(S_n)}>M$, $\sum_{m=1}^{n}EX_{n,m}1_{|X_{n,m}|>\epsilon}=0$. So by **Theorem 3.4.10** the CLT holds.

**Exercise 3.4.11** Suppose $EX_i=0,EX_i^2=1$ and $E|X_i|^{2+\delta}\le C$ for some $0<\delta,C<\infty$. Then $S_n/\sqrt{n}\to_d\mathcal N(0,1)$.

**Exercise 3.4.12 Lyapunov's theorem** Let $\alpha_n=\{var(S_n)\}^{1/2}$. If there is some $\delta>0$ s.t. $\lim_{n \to \infty} \alpha_n^{-(2+\delta)}\sum_{m=1}^{n}E(|X_m-EX_m|^{2+\delta})=0$. Then $(S_n-ES_n)/\alpha_n\to_d\mathcal N(0,1)$.

_Remark_ **Exercise 3.4.11** is a special case.

**Exercise 3.4.13** This is a good example to show different convergence. Let $X_j$ be independent with law $P(X_j=\pm j)=1/2j^\beta$, 0 otherwise. 

(i) when $\beta>1$, Then $P(X_j\ne 0)=1/j^\beta$ is summable, so $X_j=0$ for all $j>K$ for some $K$. So $S_n\to S_\infty$ a.s.

(ii) when $\beta<1$,$S_n/n^{(3-\beta)/2}\to_d c\mathcal N(0,1)$: just verify.

(iii) when $\beta=1$ then $S_n/n\to X$ with $\varphi_X(t)=\exp(-\int_0^1 x^{-1}(1-\cos xt)dx)$:

First, $\varphi_{X_j}=1-\frac{2\sin^2 (jt)/2}{j}$. So $\varphi_{S_n/n}=\prod_{j=1}^n (1-2\frac{\sin^2(jt)/(2n)}{j})$. Take logarithm,
$$
\begin{aligned}
\log\varphi_{S_n/n}&=\sum_{j=1}^{n} \ln(1-2\frac{\sin^2\frac{jt}{2n}}{j})
\\&=\sum_{j=1}^{n} -2\frac{\sin^2\frac{jt}{2n}}{j}+O(\frac{\sin^4\frac{jt}{2n}}{j^2})
\\\sum_{j=1}^{n}\frac{\sin^4\frac{jt}{2n}}{j^2}&\le\sum_{j=1}^{n}\frac{j^4t^4}{16n^4j^2}\le t^4C/n\to 0
\\\sum_{j=1}^{n} -2\frac{\sin^2\frac{jt}{2n}}{j}&=\sum_{j=1}^{n} -2\frac{\sin^2\frac{jt}{2n}}{j/n}\frac{1}{n}\to-2\int_0^1\frac{\sin^2 tx/2}{x}dx
\end{aligned}
$$
