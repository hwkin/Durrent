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